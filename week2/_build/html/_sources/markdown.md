# How I Solved It

## Phase 1:
- Set breakpoint at `phase_1`
- Disassembly strings not equal functions
- Examine the values pushed to `string_length` function:
  - `rdi` -> `phase1`, not what we want
  - `rsi` -> the correct password! ("He is evil and fits easily into most overhead storage bins.")

## Phase 2:
- In `<+13>`: `cmpl $0x0,($rsp)` indicates that the first digit must be 0.
- The `read_six_numbers` function also suggests the format of the answer.
- The code suggests there is an array of 6 items.
- From line 38 to 65, the assembly instructions indicate the bomb will explode if item `i` in the array is not equal to the value of item `[i - 1] + i`.
- Since the starting item must be 1, we can compute the numbers:
  - `i[0] = 0`
  - `i[1] = [0] + 1 = 1`
  - `i[2] = [1] + 2 = 3`
  - `i[3] = [2] + 3 = 6`
  - `i[4] = [3] + 4 = 10`
  - `i[5] = [4] + 5 = 15`

## Phase 3:
- Examine `0x40149e + 0x1fcf`, we get `%d %d`, which implies input = two integers
- Lines 31 and 43 imply the size of the first input must be >1 and <=7
- From line 86 to line 140: there are several jump lines, assume it to be a switch case.
- Choose case 1 -> 2 `0x354`
- It works, `2 852` is one of the answers.

## Phase 4:
- The first half of the code looks similar to phase 3.
- As we just did, examine `0x1fcf(%rip)` to find its input format. We got two integers.
- Examine the `phase_4` code, we find the second input must be (1,4]
- In line 59 `0x9` is being passed to `edi` register.
- Looking at the code of `func4`, we can figure out the first input of `func4` must be 9.
- In line 69, `phase_4` compares the value of the result of `func4` and input 1, so `eax` registers must contain the answer!
- Set a breakpoint at this line. Then we can find that value equals to 176 if we try `2 2` as input.
- The answer should, therefore, be `176 2`!

## Phase 5:
- After looking at the assembly code, we can basically know there will be an array of 16 items.
- Similarly to the previous phases, the code also takes two integers as inputs.
- We can further notice there exists a loop that first checks if the second input is equal to 15.
- If so, the program will break, implying the final item in the array must be equal to 15.
- Examining the array, we get `[10, 2, 14, 7, 8, 12, 15, 11, 0, 4, 1, 13, 3, 9, 6, 5]`
- If the current item is not equal to 15, the loop will continue executing, setting the `0xc($rip)` to the `0xc($rip)`th item in the array.
- It will also add up all the items in the array and compare them with the second input. (line 101)
- Understanding the basic logic of the function, we can start reverse engineering the loop.
  - Since the last item must be 15, the last item must be 6 since the index of 15 is 6.
  - The 14th item is 6, 13th must be 14...
  - After completing all the iterations, the starting index must be 5.
- The sum of 1 + 2 + 3 + ... + 15 is 115.
- The answer is `5 115`.

## Phase 6:
- Line 13 tells us the answer will be 6 integers.
- In the beginning of the code, we can notice there will be an array of 6 (0 to 5).
- In line 32, it tells us the items in the array will be its index + 1. So the array is [1 to 6].
- Examining the node `0x406330`, there will be 5 pairs of addresses.
- Examining the last address, we get the address of another node.
  - Assume node 1 represents number 1, node 2 for number 2...
- Rearrange these addresses from the smallest to largest.
- We get the new order of numbers 1-6: `3 6 4 1 5 2`.
# QGIS
## 臺北市河濱自行車道沿線設施分佈圖
### 內容呈現
根據個人經驗，google地圖上的資料對於在河濱公園等地的使用者並不是很友善，只有粗略的標記路線，沒有任何關於周邊設施的資訊。因此決定運用市府公開資料製作河濱自行車道沿線之廁所，涼亭及販賣機等便利設施的地圖
## 使用資料
* [臺北市河濱公園販賣機](https://data.taipei/dataset/detail?id=e5a7b15a-1dbd-407a-8e75-8eef48cebd18)
* [臺北市河濱廁所](https://data.taipei/dataset/detail?id=cc818250-009c-4271-982f-7e51f73ffe0e)
* [臺北市河濱公園涼亭](https://data.taipei/dataset/detail?id=5cb3555b-8fd0-47a9-9311-fb596b3f531e)
* [臺北市河濱自行車道景點](https://data.taipei/dataset/detail?id=ab1c92f1-b8ef-490a-8b49-aabbb4a33a3f)
* [臺北市自行車道(河濱)](https://data.taipei/dataset/detail?id=4fefd1b3-58b9-4dab-af00-724c715b0c58)
* 縣市界圖
* 鄉鎮市區界圖
* open street map
### 製作流程
* 於[台北市資料大平台](https://data.taipei/)下載所需之csv檔
* 以Add Delimited Text Layer來匯入csv檔
* 調整及確認座標欄位
* 建立新圖層
* 降低背景地圖透明度至50％，以避免畫面過於雜亂
* 更改圖示為svg marker
* 選擇export layout開始編輯圖檔
* 新增圖例, 方位, 比例尺及圖名
* 匯出圖檔
### 結果呈現
![asmt week3 ](https://hackmd.io/_uploads/Hk3x66rtA.jpg)


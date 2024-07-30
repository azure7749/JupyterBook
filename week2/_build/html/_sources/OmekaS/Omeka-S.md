# Omeka-S

## Imorting
* Getting Started：
    * Using FTP software liek Filezilla to upload images to the server under`/var/www/html/omeka-s/files/images`
    * Make sure the header of the CSV file follows the correct mapping format
    * Instead of using `nid,upload_date, uid,...`, specify the labels and vocabularies like `dcterms:title,dcterms:created,foaf:account,dcterms:date,curation:location,...`in the header simplifies the importing process. 

* To import multiple items, select CSV Import on the sidebar
![image](https://hackmd.io/_uploads/rk-dXkiX0.png)
* Upload CSV spreadsheet (make sure automapping is selected )
![image](https://hackmd.io/_uploads/HJChXyjmR.png)
* No need to import media in the first round. We can move on once the mappings look good. 
 ![image](https://hackmd.io/_uploads/BJw9dJjQA.png)
* The results should look like this:
![image](https://hackmd.io/_uploads/SJmL9yoQC.png)
* Now, we can start importing media.
Select Sideload as media sources on the mapping selection page
![image](https://hackmd.io/_uploads/ByXxoyiX0.png)
* Make sure to enable multivalue separator
 ![image](https://hackmd.io/_uploads/HkdBiyiQR.png)
* Assign the correct value to the multivalue separator
![image](https://hackmd.io/_uploads/HJLKjJimR.png)
* Choose append in advanced settings.
Select the correct resources identifier. 
![image](https://hackmd.io/_uploads/SyeS1eoQR.png)
* Finished importing
![image](https://hackmd.io/_uploads/r1tfbljmC.png)





## 部署

* 測試機 (iis VM)
    * [192.168.107.32](http://192.168.107.32/omeka-s/)
* 正式機 (iis VM)
    * x.x.20.x

## Covid19
依之前整理放在 depositar 上 covid-19 資料集的內容，對應整理上傳到測試機上, 並撰選相關程序

* dataset:https://data.depositar.io/organization/covid19tw

## 程序

## Sunflower Student Movement



## 工作日誌

**5/20 (Mon)**
Successfully installed CSV Importer and File       Sideload modules on the 
Omeka server
Successfully transferred covid 19 images to the server.

**5/21(Tue)**
Morning:
Attempted to import items with Bulk Import module, failed. 

3pm:
Successfully created and imported images of 286 out of 493 items with parts of the metadata using CSV import. 
However, errors occurred while processing items that contain multiple images

5pm:
Attempting to troubleshoot the errors:
Multivalue separator might not working?
https://forum.omeka.org/t/multivalue-separator-not-working-in-csv-import/16259

6pm: successfully solved the error by reassigning the multivalue separator.  

Note:
File-5633-20200607233304 of item 201313 is corrupted. 

**5/22 (Wed)**
Created omeka site for covid 19 project
Started install omeka s v2.0 for ARK module. 

**5/23 (Thu)**
Successfully installed omeka s v2.0
However, the Common module required for ARK is outdated. 
Found newer version of ARK that works for Omeka s v4.1.0
Installed php dba extension required for ARK module
Successfully installed ARK moduel. 

Installed php bcmath extension. 
Successfully implemented the given template and creataed ARKs of 492 items. 
However, having trouble changing the ARK shoulder. 

Update: successfully added shoulder.

**5/24 (Fri)**
Successfully amended shoulder (m5).


Examples of  ARK using sites: 
https://digital.library.unt.edu/ark:/67531/metadc283699
https://collections.lib.utah.edu/ark:/87278/s6pk113q
https://gateway.okhistory.org/ark:/67531/metadc2324576/
https://gallica.bnf.fr/ark:/12148/bpt6k15135432

ARK using Omeka S based site: 
https://archiv.peter-weiss.digital/obj/ark:/15395/a7n4b0h

ARK module(new):
https://github.com/Daniel-KM/Omeka-S-module-Ark

5/27(Mon):

Universal Viewer Module(Iiif server and Image server required):
https://github.com/Daniel-KM/Omeka-S-module-UniversalViewer
Iiif server:
https://gitlab.com/Daniel-KM/Omeka-S-module-IiifServer
Image Server:
https://github.com/Daniel-KM/Omeka-S-module-ImageServer

Item Hierarchy:
The built-in `dcterms:hasPart / isPartOf` tag allows users to link sub-items under specific items. 
![image](https://hackmd.io/_uploads/SJZXon-E0.png)

![image](https://hackmd.io/_uploads/ByAT5hbE0.png)
Item Relations:
The built-in `dcterms:relation` tag allows users to link related items. 
![image](https://hackmd.io/_uploads/By_7hnb4A.png)
![image](https://hackmd.io/_uploads/HJPVn2ZNA.png)

Item sets tree:
The item sets tree module enables the hierarchical organization of item sets. 
![image](https://hackmd.io/_uploads/Bk9922-4C.png)

5/28 (Tue)
Referencing linked resources using CSV import:
https://forum.omeka.org/t/csv-import-referencing-linked-resources/9006

5/29 (Wed):
How to import items with linked resources using CSV import:
1: Import as usual using CSV Import
2: In the CSV Import column options, select Omeka resources data type for linked resources  
![Screenshot 2024-05-29 at 12.14.34 PM](https://hackmd.io/_uploads/rkKDC7ENA.png)
3:Change the import mode to append in advanced settings.
![image](https://hackmd.io/_uploads/SyeS1eoQR.png)
4: Finished importing.
![Screenshot 2024-05-29 at 12.27.35 PM](https://hackmd.io/_uploads/S1pCRmVER.png)

5/31 (Fri)
https://github.com/hafizchin/DomainManager

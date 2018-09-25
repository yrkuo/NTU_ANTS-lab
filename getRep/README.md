# Sequence-Analysis
A analysis program about analyzing malware trace hooklog.
Propose a sequence-based clustering algorithm to analyze malwares.

- dataset: https://drive.google.com/drive/u/0/folders/1PoAn_RuJOyTvJoFkhGbxGo8necwQvHRd
  - 180920_aries_family_simplified_15up.zip
- revised from: https://github.com/weichih-c/Sequence_Analysis
- documentation: https://mega.nz/#!N1NAXSjZ!lHyUl2gZFTjbRpa1PSTSGQ3z3uvQelgWKaGXPq-hxOQ
- RasMMA illustration: https://mega.nz/#!0hFkUI7R!JZktrdDB-LrYtcYBwygJgvG5OT_VAwXNtdMQ5b_tUvg

**Tested Environmnet**
* Python3.6 (anaconda)
* Ubuntu 16.04.5

## 2018/09/25 UPDATE ##
當上面兩個步驟做法完成以後

接下來要將各自所負責的家族，各tree的rep pickle讀出來，會得到2D的list，例如: `[['RegQueryValue#PR@HKLM@sys_curCtlSet_ctl_sessionManager\\*#PR@SUBK@criticalsectiontimeout#PR@0#PR@12f9b0#Ret#0',
  'RegQueryValue#PR@HKLM@soft_ms_ole\\*#PR@SUBK@rwlockresourcetimeout#PR@0#PR@12f9b4#Ret#P',
  'LoadLibrary#PR@SYS@wininet@DLL#Ret#P',
  'LoadLibrary#PR@SYS@advapi32@DLL#Ret#P',
  'LoadLibrary#PR@SYS@advapi32@DLL#Ret#P',],['CopyFile#PR@ARB@DLL#PR@ARB@DLL#Ret#N']]`

則要將前面的api call萃取出來變成: `[[RegQueryValue,RegQueryValue,LoadLibrary,LoadLibrary,LoadLibrary],[CopyFile]]`

接下來要對之進行one-hot encoding的轉換並加上start token、comma token、endding token
   - (我還在做，會再進行說明)


## 2018/09/22 ##
### 分工 ###
* family 1.~15. => 智誠
* family 16.~40. => 子庭
* family 41.~80. => 鈞岱

### 輸出 ###
* 一個家族底下會有很多個資料夾(forest)
  * 每個資料夾代表一個tree
   * 裡面會有該tree對應的traces(hooklog)以及該tree的rep (2D list的pickle檔案)
* 上傳到Google drive: https://drive.google.com/drive/u/0/folders/1x-zt2ZZnpMwfDKH22ORa3Tvpm6P0UxFS
   
### 作法 ###
1. 先跑RasMMAExample.ipynb並產生出pickle
2. 再跑CollectForestInfo.ipynb
    * 需讀入所產生出的intermediate.pickle跟residual.pickle以產生CollectForestInfo的建構子初始化
    * 利用getTreeMembers函式來獲得該family forest各tree的hooklogs => `for tree in forest:`
    * 利用getRepMotifSequence函式來獲取該family forest各tree的hooklogs => `for tree in forest:`
    
### HINT & Notice ###
1. 建議從數字大的家族開始跑以測試自己自動化程式的完整性與正確性
2. 太大的檔案可以透過一些統計的方法(iqr)把離群值(outlier)拿掉再來跑，不然會跑到天荒地老
3. 如果有出現error而且是因為某個hooklog檔案所導致的問題，可以先把該trace移除，放到該家族的exception資料夾，並且截圖註明原因(EX:編碼錯誤、檔案過大)
4. 可以改寫code變成for迴圈自己讓他自己跑完所有家族，或是改code利用multi processing來平行跑(數字越小的家族跑越久)



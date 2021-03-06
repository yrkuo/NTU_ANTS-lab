# Sequence-Analysis
A analysis program about analyzing malware trace hooklog.
Propose a sequence-based clustering algorithm to analyze malwares.

- dataset: https://drive.google.com/drive/u/0/folders/1PoAn_RuJOyTvJoFkhGbxGo8necwQvHRd
  - trace轉profile、Virus Total Query、家族分類的程式在.40 FTP
  - areis、aquaris trace dataset也在.40 FTP (帳密: sxx / xxa )
- revised from: https://github.com/weichih-c/Sequence_Analysis
- documentation: https://mega.nz/#!N1NAXSjZ!lHyUl2gZFTjbRpa1PSTSGQ3z3uvQelgWKaGXPq-hxOQ
- RasMMA illustration: https://mega.nz/#!0hFkUI7R!JZktrdDB-LrYtcYBwygJgvG5OT_VAwXNtdMQ5b_tUvg

- 縮減的Profile(******.hooklog): https://drive.google.com/open?id=1qh_ZWGEkkw7fkieqzHn1UYEIKetCUzQF
- 完整的traces檔案結構(family/tree/******.hooklog): https://drive.google.com/drive/folders/1x-zt2ZZnpMwfDKH22ORa3Tvpm6P0UxFS
- Motifs檔案結構(family/tree/parameter_rep.pickle): https://drive.google.com/drive/folders/1T2MdJ7nAwLZKBuISGw5-SmzkYADtJ49s

(family/tree/***)

- RasMMA流程解釋： https://drive.google.com/open?id=1QxqczGfmmbuwIbpt-OaT5CD-THeAoUWV


**Tested Environmnet**
* Python3.6 (latest anaconda)
* Ubuntu 16.04.5

## 2019/05/23 ##
**目標:**
1. 查詢各family name所有可能的aliases(別名)
2. 各family簡易的technical description(主要是在做什麼、有甚麼攻擊行為、傳染途徑etc)

**作法:**
1. Google: XXX malware
2. 查詢各大防毒引擎的描述說明 (EX: Symantec 、 Trend micro 、 Microsoft 、 Panda 、 sophos 、 Kaspersky 等等)
3. 將別名製做為excel表格
    * 同家族名稱者可有相同顏色
4. 將家族的簡易描述製做為簡易ppt

**分工:**
* 子庭:
['allaple',
 'autoit',
 'avmh',
 'barys',
 'bdmj',
 'bredo',
 'browsefox',
 'brresmon',
 'clickdownload',
 'conjar',
 'delf',
 'directdow',
 'domaiq',
 'downloa',
 'downloadadmin',
 'eggnog',
 'elkern',
 'expiro',
 'fakealert',
 'fakeav',
 'fesber',
 'firseria',
 'fiseria',
 'graftor',
 'hidp',
 'hoax',
 'hotbar',
 'ibryte',
 'installcore',
 'installerex',
 'installrex',
 'ipamor',
 'jorik',
 'kazy',
 'kdz',
 'killav',
 'kryptik',
 'lmn',
 'loadmoney',
 'lollipop',
 'mabezat',
 'madang',
 'madangel']
 * 鈞岱:
 ['megasearch',
 'mikey',
 'mira',
 'morstar',
 'mplug',
 'mresmon',
 'msil',
 'nimnul',
 'outbrowse',
 'parite',
 'pcclient',
 'picsys',
 'rahack',
 'ramnit',
 'razy',
 'sality',
 'screensaver',
 'shipup',
 'shodi',
 'sirefef',
 'soft',
 'softpulse',
 'solimba',
 'soltern',
 'somoto',
 'startpage',
 'strictor',
 'symmi',
 'sytro',
 'tepfer',
 'upatre',
 'ursu',
 'vbkrypt',
 'vbran',
 'vilsel',
 'virlock',
 'virtob',
 'virut',
 'vobfus',
 'vtflooder',
 'yantai',
 'zbot',
 'zusy',
 'zygug']

**輸出:**
* Possible family reference(如果有爭議或有疑慮不確定的family aliases可以到這邊來找看看有沒有值得參考的地方): https://docs.google.com/spreadsheets/d/1myD3c_oEDJoF1ZUzFMnAX8LVpAe1V3mRi5Xmg7-HpXU/edit?fbclid=IwAR3UyE5122QFQ-c1cmQ-Shv63mdCZ03lA4DhwBXXAl7PftSHCh9w6nubJys#gid=1243878253
* 上傳到Google drive: https://drive.google.com/open?id=16jRmgzda8KkYWwSBWyVFQvaeYBOIHT5m
* deadline: 2019/06/01

## 2019/05/17  ##
**分工:** [2019/05/06]
1. 子庭負責Aries dataset的Virustotal report query也給鈞岱
2. 鈞岱負責Aquaris dataset的Virustotal report query也給子庭
3. 子庭跑僅**Aries dataset**自己的一個對一個family分法及RasMMA、Aries+Aquaris合在一起的**一個對一個**family分法及RasMMA
4. 鈞岱負責Aries+Aquaris合在一起的**一個對多個**family分法及RasMMA
    * 產生一個對多個的EXCEL (csv) 表格: 各個trace(包含main&child)檔名所對應到的family name有哪些，有者為1，無者為0 [2019/05/07]
    * family排序由左到右為samples數量大到小的family

profile name(hash_pid.profile)           | allaple  | virut | elkern | ...
--------------|:-----:|-----:| ----:|------------------------
4a8581ee09a6f9794b3cafa0cbe493eb43604978e51dd460b2dfbbc3f344938b_3156.profile    | 1 |  0 |    0 | 0
4a8581ee09a6f9794b3cafa0cbe493eb43604978e51dd460b2dfbbc3f344938b_3268.profile    | 0 |  1 |  1 | 0
a70c1f66c37b0aa1f68a6bc7502b10a56a16a5e8ee01c41128a525891f166d1f_3220.profile    | 1 | 0 |  1 | 0  

5. 子庭負責產生**Aries+Aquaris**合在一起的一個對一個byte sequence pickle及REP pickle
6. 鈞岱負責產生Aries+Aquaris合在一起的**一個對多個**byte sequence pickle及REP pickle

**目標:** 
1. 產生Aries及Aquaris Dataset的profiles
    * 若row的開頭字並非底下做法所定義中的27個api function name請將該profile的該row刪除，再跑RasMMA跟產生對應byte sequence
    * 需利用在.40上面的FeatureTrace程式來跑，手動將profile另外存起來
2. 產生Family (每個family數量>=15)
    * 兩種family分法:
        * 一個malware只會對應到一個家族 => 子庭(一個對一個)
        * 一個malware會對應到多個家族 (只要超過threshold) => 鈞岱(一個對多個)
    
3. 依照Family資料夾跑RasMMA產生很多tree資料夾
    * 兩種RasMMA結果
        * 子庭: 一個對一個
        * 鈞岱: 一個對多個
4. 依照tree的rep對照profile產生byte sequence (pickle)
5. 需記錄統計資料 [2019/05/06]
    * process數量(hooklog總數)、samples數量(uniqie hash IDs)
    * 經過家族分類演算法以後，總共產生了多少個families? 共含有多少samples? processes? [2019/05/17]
    * ~~變成15隻以上的家族後，有多少processes、samples沒被分進去家族而捨棄的?~~
    * ~~進行RasMMA以後有多少processes、samples是被捨棄沒跑成功的? (error原因?)~~
    * 經過RasMMA演算法以後還剩下多少有效familes? samples? processes? 總共有幾棵樹? [2019/05/17]
    * 各family loner的processes、samples數量有多少 (因為沒達到0.8 criteria被捨棄沒分到任何一棵樹者) [2019/05/14]
    * 正常樹(不包含small_short tree)有幾棵? 多少samples? processes? 涵蓋多少families [2019/05/17]
        * 小樹有多少processes、samples、trees? 短樹有多少processes、samples、trees? 聯集small_short有多少processes、samples、trees?
    * ~~跑完RasMMA後，拿掉各family的短樹跟小樹以後，還剩下多少processes、samples? families? [2019/05/08]~~
    * 最後還剩下15 samples以上的家族還有多少個? 共有幾棵trees? samples? processes? [2019/05/16]


**做法:**
1. 將兩個dataset所有trace都先轉換成profiles [2019/05/08]
    * 需特別注意: 確保每個profile的每個row開頭第一個字都是以下所定義的api function name，否則請把該row刪除
    * ['LoadLibrary','CreateProcess','OpenProcess','ExitProcess','TerminateProcess','WinExec','CreateRemoteThread','CreateThread','CopyFile','CreateFile','DeleteFile','RegSetValue','RegCreateKey','RegDeleteKey','RegDeleteValue','RegQueryValue','RegEnumValue','WinHttpConnect','WinHttpOpen','WinHttpOpenRequest','WinHttpReadData','WinHttpSendRequest','WinHttpWriteData','InternetOpen','InternetConnect','HttpSendRequest','GetUrlCacheEntryInfo'] 共27個
2. 利用virus total query回來的資料跑家族分類演算法，得到family name資料夾底下還有所有對應的profiles
    * 每個資料夾底下的profiles數量>=15
    * 兩個dataset一起分family
    * child process跟main process都會一起放到相同家族資料夾中 [2019/05/05]
3. 同family name的資料夾一起跑RasMMA，得到各tree的REP (一個REP包含很多個motif)
    * RasMMA以trace為輸入，可利用這邊的RasMMAExample.ipynb進行multi-process以加速運算效率 (請記得修改輸出檔案、資料夾名稱)
    * 將profiles移動到各自所屬的tree資料夾底下
    * 將tree的REP依照motif(一串的連續api invocation call sequences)，一個motif為一個list element，因此一個REP會是2D list (string type)，在tree資料夾下輸出成rep.pickle [2019/05/13]
    
    
4. 將各tree的REP利用字串比對方式對應回各tree底下的profiles，若與motif一樣則輸出1，若profile的api call不存在於REP中輸出0
    * 要完全相同於REP中的某個motif時，才會對那一段profile的api call sequence都會輸出1，否則輸出0
    * byte sequence儲存為int type，存放於list中
    * 將list存成pickle檔案輸出到對應tree資料夾
    * 一個profile會對應一個rep pickle (檔名: *HASH*_*PID*_byterep.pickle)放在tree資料夾下
    * 一個profile中byte sequence中1的個數 = REP所有motif的長度(api invocation calls個數)
5. 將小樹與短樹的tree資料夾保有原本的目錄結構存放到另外一個資料夾巢狀目錄中
    * 小樹: 那個tree裡面的profile數量<=2
    * 短樹: 那個tree的REP所有motifs合併以後的總長度<=10
    * ```
          rep = pickle.load(open(in_directory + 'rep.pickle','rb')) 
    
          rep = sum(rep,[])
    
          len(rep) <=10
      ```
    
    
    * 一個row = 一個api invocation call(包含parameters) = 長度(length)1
    
**輸出:**
1. ouput的目錄結構如下：
```
- No#.family_name
    - tree_name
        - *.profile
        - *_byterep.pickle
        - rep.pickle

- 01.allaple_0.8
    - G1286
        - 4a8581ee09a6f9794b3cafa0cbe493eb43604978e51dd460b2dfbbc3f344938b_3268.profile
        - a70c1f66c37b0aa1f68a6bc7502b10a56a16a5e8ee01c41128a525891f166d1f_3220.profile
        - 4a8581ee09a6f9794b3cafa0cbe493eb43604978e51dd460b2dfbbc3f344938b_3268_byterep.pickle
        - a70c1f66c37b0aa1f68a6bc7502b10a56a16a5e8ee01c41128a525891f166d1f_3220_byterep.pickle
        - rep.pickle
        ...
    - G1294
    ...
...
```

2. 濾除的小樹短樹的目錄結構也同上
* 輸出資料階層:family=>tree=> **traces & REP's binary sequence pickle & REP string list** (一起放在同一個資料夾裡面) 
* 上傳到Google drive: https://drive.google.com/open?id=16jRmgzda8KkYWwSBWyVFQvaeYBOIHT5m
* 壓縮請用zip最外層資料夾請統一名字tree-rep-profiles 
    * 最外層資料夾會包含兩個子資料夾(一個是小樹短樹的資料夾: small_short/ 另一個是正常樹的資料夾: normal/ )，各個子資料夾底下皆為上述階層

**Q&A**
* 修正bug的profile code?
* 完成deadline (5/14中午以前)

> if value[0] == "S":

>   retword += "P" # positive

這邊應該要是retword += "0"才對...吧 
 
profile中的Ret有P N 0 三種值，現在看起來N是失敗、O是成功、P 有成功或是失敗 (因為bug的關係)

trace中，如果成功執行一個API Call，通常會回傳0或是SUCCESS，如果失敗的話則是2或是FAILURE。所以直觀來說profile中的0應該是成功，profile中的"P"和"N"應該是失敗。但我剛剛打開profile的時候看到連load很平常的library都是return P，和trace一對照發現怪怪的。

* 為甚麼P會有失敗?

## 2018/11/26 ##
**目標:** 

1. 需將REP中的各motif拆開，並加入\<BOS\>於第一個motif的開頭，且於最後一個motif結尾加入\<EOS\>，而motif跟motif(一串的連續api invocation call sequences)之間要加入\<MOS\>
2. 利用utils/api_enc2.pkl檔案( https://github.com/tychen5/NTU_ANTS-lab/blob/master/getRep/utils/api_enc2.pkl )將\<BOS\>、motifs、\<MOS\>、\<EOS\>都轉換依據進行one-hot encoding變成2D numpy array
3. 另存一個具有api call與parameters的string list，在不同的motif list之間加入'\<MOS\>'，把REP的各list合成一個1D list
  
=>注意1. 2.僅使用api function name；3.則為整個invocation call(api name+所有profile的parameters)不用轉換為onehot

**做法:**

1. 利用CollectForestInfo.ipynb讀入Tree的REP之intermediate.pickle、residual.pickle初始化建構子(CollectForestInfo)，再利用裡面的function: getRepMotifSequence()來獲得2D list REP
2. 將REP list中的api function name取出，並於第一個motif (一或多個api calls)開頭加入\<BOS\>，motif (list)間加入\<MOS\>，最後一個motif (api invocation call sequences)加入\<EOS\>，且將所有REP的list串在一起變成1D list
3. 利用api_enc2.pkl將\<BOS\>、\<MOS\>、\<EOS\>及api names轉換為one-hot(例如: df['\<MOS\>'].values)，再將整個list轉換為2D numpy array存成api_name.pickle (np.shape=(REP-length+\<BOS\>、\<MOS\>s、\<EOS\>,32))
4. 一樣利用getRepMotifSequence()或是或是getRepAPISeq_dict()取得REP(function name & parameters)以後，將motif (一串的連續api invocation call sequences list)與motif之間於list多加入\"\<MOS\>\"字串型態的元素，最後也是將該tree的REP轉換為1D的list，每個element就是一個完整的api invocation call(包含parameters)或是\<BOS\>、\<MOS\>、\<EOS\>，都是字串型態，再將該1D string list存為parameter_rep.pickle (別轉成numpy array)
5. 將兩個pickle儲存於對應的tree目錄底下(tree-rep-logs-profile/family/tree/***.pickle 例如:tree-rep-logs-profile/allaple_0.8/G1299/api_name.pickle)
6. 將最外層目錄名稱tree-rep-logs-profile資料夾壓縮成zip，再將zip檔案名稱重新命名加上family範圍，上傳至https://drive.google.com/drive/u/0/folders/1T2MdJ7nAwLZKBuISGw5-SmzkYADtJ49s
  
=>注意: special tokens包含\<BOS\>、\<MOS\>、\<EOS\>請務必加入並一起轉換為one-hot；parameter_rep.pickle中的\<BOS\>、\<MOS\>、\<EOS\>則不用轉換，保留字串型態於list中即可

=>Deadline: 11/22 18:00

## 2018/09/30 ##
當下面09/22兩個步驟做法完成以後

接下來要將各自所負責的家族，各tree的rep pickle讀出來，會得到1D的list，例如: `['RegQueryValue#PR@HKLM@sys_curCtlSet_ctl_sessionManager\\*#PR@SUBK@criticalsectiontimeout#PR@0#PR@12f9b0#Ret#0',
  'RegQueryValue#PR@HKLM@soft_ms_ole\\*#PR@SUBK@rwlockresourcetimeout#PR@0#PR@12f9b4#Ret#P',
  'LoadLibrary#PR@SYS@wininet@DLL#Ret#P',
  'LoadLibrary#PR@SYS@advapi32@DLL#Ret#P',
  'LoadLibrary#PR@SYS@advapi32@DLL#Ret#P','CopyFile#PR@ARB@DLL#PR@ARB@DLL#Ret#N',...]`

則要將前面的api call萃取出來變成: `[RegQueryValue,RegQueryValue,LoadLibrary,LoadLibrary,LoadLibrary,CopyFile,...]`

接下來要對之進行one-hot encoding的轉換並加上start token、comma token、endding token: `<BOS> RegQueryValue RegQueryValue LoadLibrary LoadLibrary LoadLibrary CopyFile ... <EOS>`
   - one-hot encoding: 利用output/api_enc.pkl 檔案作為轉換依據，load pickle後為一dataframe，利用api作為key值來轉換，轉換方式為df['XXX'].values可得該XXX的numpy array。如: df['\<MOS\>'].values可得array([0, 0, 0, 0, 1, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0])
   
### 做法 ###
* 將前兩步驟該tree的rep之pickle讀入以後可獲得api call sequences的list
* 同時讀入api_enc.pkl檔案可獲得one-hot dataframe: https://github.com/tychen5/NTU_ANTS-lab/tree/master/malwareTagging/output
* 將api call sequences處理後可得去除parameters僅有api的list
* 接下來將list每個元素利用上述one-hot encoding方式轉換為2D numpy array
* 接下來看該tree有幾個hooklogs進行duplicate該2D array，因此會變成3D numpy array (即便只有一個trace也要expand dimension變成3D)
* 最終要輸出numpy的shape為(該tree有幾個members, 該tree的rep長度,37)

### 輸出 ###
* 為每個tree產生一個3D的numpy array pickle
* 輸出資料階層:family=>tree=> **hooklogs & REP's 3D numpy array pickle** (一起放在同一個資料夾裡面) 檔案名稱:rep-numpy-3D.pickle
* 上傳到Google drive: https://drive.google.com/drive/u/0/folders/1x-zt2ZZnpMwfDKH22ORa3Tvpm6P0UxFS
* 壓縮請用zip最外層資料夾請統一名字tree-rep-logs/，最後的完成3D numpy array請用.shape檢查是否為3D


## 2018/09/22 ##
### 分工 ###
* family 1.~15. => 智誠
* family 16.~40. => 子庭
* family 41.~80. => 鈞岱

### 輸出 ###
* 一個家族底下會有很多個資料夾(forest)
  * 每個資料夾代表一個tree
   * 裡面會有**該tree對應的traces(hooklog)** 以及該tree的rep (1D list的pickle檔案)
* 上傳到Google drive: https://drive.google.com/drive/u/0/folders/1x-zt2ZZnpMwfDKH22ORa3Tvpm6P0UxFS
   
### 作法 ###
1. 先跑RasMMAExample.ipynb並產生出pickle
2. 再跑CollectForestInfo.ipynb
    * 需讀入所產生出的intermediate.pickle跟residual.pickle以產生CollectForestInfo的建構子初始化
    * 利用**getTreeMembers**函式來獲得該family forest各tree的hooklogs => `for tree in forest:`
    * 利用**getRepAPISeq_dict()** 或是**getRepAPISeq**函式來獲取該family forest各tree的REP <= 1D list
    
### 參考程式碼 by 智誠  
1. 把multi-process加進RasMMAExample.ipynb，可指定一個範圍的family number下去跑 (ex: 1~15), 並用shared memory queue紀錄錯誤訊息。
2. CollectForestInfo.ipynb裡面提供dump出各家族下各顆樹的hooklog以及rep sequence
3. 最終ouput的目錄結構如下：
```
- family_name
    - tree_name
        - *.trace.hooklog
        - rep.pickle

- allaple_0.8
    - G1286
        - 4a8581ee09a6f9794b3cafa0cbe493eb43604978e51dd460b2dfbbc3f344938b_3268.trace.hooklog
        - a70c1f66c37b0aa1f68a6bc7502b10a56a16a5e8ee01c41128a525891f166d1f_3220.trace.hooklog
        - rep.pickle
    - G1294
    ...
...
```

**大家最好資料夾和檔案命名可以一致，不然到時候學長要讀資料來training的時候會崩潰。**

**請至少資料夾階層數要一樣**
    
### HINT & Notice ###
1. 建議從數字大的家族開始跑以測試自己自動化程式的完整性與正確性
2. 太大的檔案可以透過一些統計的方法(iqr)把離群值(outlier)拿掉再來跑，不然會跑到天荒地老
3. 如果有出現error而且是因為某個hooklog檔案所導致的問題，可以先把該trace移除，放到該家族的exception資料夾，並且截圖註明原因(EX:編碼錯誤、檔案過大)
4. 可以改寫code變成for迴圈自己讓他自己跑完所有家族，或是改code利用multi processing來平行跑(數字越小的家族跑越久)




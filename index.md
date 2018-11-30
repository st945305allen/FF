## Welcome to FF's Pages
## Profiles

~~[facebook](https://www.facebook.com/profile.php?id=100002258495173&ref=bookmarks)~~

## 雜記
>不要進法人寫文件，不要追buss word，不要滿足於眼前學會的工法，不要忘記回頭念演算法與資料結構  
>不要與人、社會、家庭、朋友、團隊脫離，但要學會忍受一人獨學的孤獨，不要急著彰顯自己，但要學會親切而嚴謹的表達   
>不要戰語言，但要知道哪個好，哪個不好  
>不要反商，但要從開源學會智慧，從企業學會包裝  
>不要忽視 UI/UX，但也要能具備從0到1的架構能力  
>程式已外的興趣很重要，但更重要的是專精這些門道，就像精通開發方法與設計技巧一般  
>雖然所有工作都是由淺入深，但務必追求能理解、掌握底層的機制與概念，外頭的招式會變，但本質卻是不變的  

出處: [#1RvKdKhE(Soft_Job)](https://moptt.tw/p/Soft_Job.M.1541753300.A.ACE) by fayhong

## 注意事項
+ 主檔設定記得改使用者群組功能權限
+ 當c1設計工具拉grid無效時，要去擴展欄位改或右鍵自動恢復欄位格式
+ 字串跟NULL串在一起時，會變NULL，遇到時用 `isnull(obj," ")` 防出錯
+ 若method下面沒有特別的logic，判斷直接return掉
+ 專案出錯先取新版重建再說
+ 專案起始設定
    - Webserver -> 屬性 -> 起始選項 -> 起始外部程式 -> MDI.MAIN -> 引數 '-start'
+ 報告相關
    - 情境帶入
    - 鼠標當雷射筆用，帶著聽者看流程
    - 每一項目給個大綱 流程圖的位置之類的
    - 被問問題先想一下在回答
    - 物件的flag在系統的功能是甚麼，標了會怎麼樣(在系統流程中)
+ insert多筆data時，盡量多包裹try-catch，以防止單筆出錯後面不會執行的狀況
+ sql server & oracle server 有大小寫之分，要注意
    
## 程式相關
+ set bool Y N  
```
public string SPCJudge 
{  
    get { return _spcJudge == true ? "Y" : "N"; }  
    set { _spcJudge = value == "N" ? false : true;}  
}
 ```
+ open web page
```
private void tdbgWIPTrx_DoubleClick(object sender, EventArgs e)
{        

    if (tdbgWIPTrx.Splits[0].DisplayColumns[tdbgWIPTrx.Col].DataColumn.DataField == "E_TRX_FILE")
    {               
      string strTrxFilePath = tdbgWIPTrx.Splits[0].DisplayColumns[tdbgWIPTrx.Col].DataColumn.CellValue(tdbgWIPTrx.Row).ToString();
      LMOTW2228.ClientSTD.Library.CommFunction.OpenWebPage(strTrxFilePath);
      return;
    }          
}
```
+ CHECK cmbItem select status
```
if (this.chkItem.Checked)
{
    if (this.cmbItem.SelectedIndex == -1)
    {
        this.ShowMessage(this, "MCPQ006002", IconType.Warning); //請選擇機種代碼!
        this.cmbItem.Focus();
        return;
    }
}
```
+ datetime compare
```
UDbCommand uDbCommand = new UDbCommand();
    uDbCommand.CommandText = string.Format(sql, DBParameterChar.ParamChar);
    uDbCommand.Parameters.Add(DBParameterChar.ParamChar, "QCLOT_KEY", drSelQCLot["QCLOT_KEY"].ToString(), typeof(string));
    DataTable dtQCLotSn = CClient.ActiveucClient.GetDataSet(uDbCommand).Tables[0];
    
    DateTime startDate = new DateTime(dtpCreateDateStart.Value.Year, dtpCreateDateStart.Value.Month, dtpCreateDateStart.Value.Day, 0, 0, 0);
    DateTime endDate = new DateTime(dtpCreateDateEnd.Value.Year, dtpCreateDateEnd.Value.Month, dtpCreateDateEnd.Value.Day, 23, 59, 59);
    if (this.chkCreateDate.Checked)
    {

        if (startDate > endDate)
            {
                this.ShowMessage(this, "MCPQ010007", IconType.Warning); //檢驗批開立時間,起始時間不得大於結束時間!
                this.dtpCreateDateStart.Focus();
                return;
            }
    }
```
+ no title
```
DataTable dtMap = (DataTable)tdbGridSelected.DataSource;
            var vCheckRow = (from row in dtMap.AsEnumerable()
                             where row["INSPCHAR_PROP"].ToString() == "VAR"
                             && string.IsNullOrEmpty(row["INSPECTION_POINTS"].ToString())
                             select row).Take(1);
            if (vCheckRow.Count() > 0)
```
        

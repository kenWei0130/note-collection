# sendmail 

## 設置

### 環境
Ubuntu 18.04 

### 步驟
    sudo apt-get update 
    sudo apt-get install -y sendmail 
    sudo sendmailconfig
    
到這邊已經安裝完成，可以在機器上使用 command line 發送信件  
    
    sendmail xxx@example.com
    From: aaa@mail-example.com
    Subject: This is Test Mail 
    Hello, my first mail
    .
    (control + D 發送)

### 調整設置

目前已經可用，但要能遠端能用還差一些些

#### sendmail.mc
    vim /etc/mail/sendmail.mc
    #修改下列內容的 Addr，監聽發信請求的主機 
    DAEMON_OPTIONS(`Family=inet,  Name=MTA-v4, Port=smtp, Addr=127.0.0.1')dnl
    DAEMON_OPTIONS(`Family=inet,  Name=MSP-v4, Port=submission, M=Ea, Addr=127.0.0.1')dnl

#### access 設置存取權限 - 誰可以寄信
    vim /etc/mail/access
    #IP/Hostname
    192.168.0.122			RELAY
    abc12345.com			RELAY
    #REJECT 退回信件
    crazy123.com			REJECT
    #DISCARD 丟棄信件
    carzy456.com			DISCARD
RELAY 是允許誰可以發信，  並依照查閱的資料顯示，要排除來信比起 REJECT 直接使用 DISCARD 更好，理由是能避免信件重複往來用掉頻寬。

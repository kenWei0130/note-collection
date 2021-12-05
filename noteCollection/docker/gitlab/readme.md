# 使用 Docker 建立自已的 Gitlab 

## 簡單的安裝

- 請先安裝 Docker 
- 這裡使用官方的 Image 

### Docker 指令
    docker run -d --name gitlab \
        -p 8080:80 -p 8443:443 -p 8022:22 \
        --privileged \
        --restart always \
        -v ~/gitlab/config:/etc/gitlab \
        -v ~/gitlab/logs:/var/log/gitlab \
        -v ~/gitlab/data:/var/opt/gitlab \
        gitlab/gitlab-ce

### 我踩到了雷
- 使用 Portainer 的 Templates 安裝遇到不能理解的錯誤，像是啟動失敗
- 又或者是依上方指令安裝並啟動成功後沒能建立自已的 root 密碼，直接要我登入

#### 修改 Gitlab User password

我使用了[這裡](https://www.ichiayi.com/tech/gitlab "Title")提供的作法完成了

# 結尾
最近在自家搞一台 NAS，於是就想到自已來建一些東西，不過一切都還在規劃中。  
期待會有完成的一天吧…雖然我很懶

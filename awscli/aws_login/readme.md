### 250924
# AWSCLI login
### 아래 페이지에서 awscli를 설치한다.
### 각 OS 버전에 따라 설치하면 된다. 이건 쉬우니 별도 정리 안 함
#### https://docs.aws.amazon.com/ko_kr/cli/latest/userguide/getting-started-install.html
### <br/>

### Security credentials 로 간다.
#### <img width="282" height="364" alt="image" src="https://github.com/user-attachments/assets/dd0b7b90-54e8-4398-92e0-4c4fe91d8d8d" />
### <br/>

### access key를 하나 만든다. 그리고 파일로 다운로드 받아서 별도로 저장해둔다.
#### <img width="1582" height="167" alt="image" src="https://github.com/user-attachments/assets/97b661ac-4ccf-4b8a-82a7-48cc23431c4f" />
### <br/>

### awscli에서 해당 key를 가지고 로그인한다.
### 나는 region은 seoul region인 ap-northeast-2, output format은 yaml로 했다.
```
aws configure
```
### <br/>


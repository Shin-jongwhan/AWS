# create IAM user
### <br/><br/><br/>

## IAM user 만들기
```
aws iam create-user --user-name Bob
```
### 그럼 이런 json 이 출력된다.
```
{
    "User": {
        "Path": "/",
        "UserName": "Bob",
        "UserId": "AIDAXVSF653PBC3DE4U3X",
        "Arn": "arn:aws:iam::527353966302:user/Bob",
        "CreateDate": "2023-04-19T02:41:26Z"
    }
}
```
### Bob 계정이 생성되었다.
#### ![image](https://user-images.githubusercontent.com/62974484/232953033-f8df3afc-8017-4f73-ad35-b446a8b15aeb.png)
### <br/>
### user 조회
```
aws iam get-user --user-name 5725e1b46a85591d
```
### <br/><br/><br/>

## initial password 설정
```
aws iam create-login-profile --user-name Bob --password "initial12!" --password-reset-required
```
#### ![image](https://user-images.githubusercontent.com/62974484/232953649-9187d1f5-7e43-426e-b7cc-1ff9123160c1.png)
### 이제 로그인 해보자
#### ![image](https://user-images.githubusercontent.com/62974484/232953757-ac721230-0a26-4174-bd11-f62c0cce2b06.png)
### 새로운 비밀번호를 설정하라고 나온다.
#### ![image](https://user-images.githubusercontent.com/62974484/232953772-7ea2c26d-6203-440d-8ea7-d7ee351dfcfc.png)
### 비밀번호 재설정하려고 하면 에러 난다. 권한이 없기 때문이다.
### 그래서 이제 권한만 붙여주면 된다.
#### ![image](https://user-images.githubusercontent.com/62974484/232953986-365a32c6-e1b0-466f-a3cf-18e841f6e4f4.png)
### <br/><br/><br/>

## attach user group
### 미리 만들어둔 admin user group 이 있다.
#### ![image](https://user-images.githubusercontent.com/62974484/232964378-d12a85b1-67ef-42ff-81ef-d7be28873eb1.png)
### <br/>
### user group 을 attach 해보자.
```
aws iam add-user-to-group --user-name Bob --group-name admin
```
#### ![image](https://user-images.githubusercontent.com/62974484/232964333-4ccd2f24-1c9d-4944-91ba-6b8113f2b004.png)
### <br/>
### 비밀번호를 바꿔주고 접속해보면 잘 된다.
#### ![image](https://user-images.githubusercontent.com/62974484/232964592-ef0a78ef-8c27-48ea-b42d-51301ac40833.png)
### <br/><br/><br/>

## user - group 제거
### group 조회 (그룹 이름으로)
### * user 를 삭제하려면 attach 된 group 을 제거해줘야 한다.
```
aws iam get-group --group-name MyIamGroup
```
### group 조회 (user name 으로)
```
aws iam list-groups-for-user --user-name jhshin
```
```
{
    "Groups": [
        {
            "Path": "/",
            "GroupName": "tgs_admin",
            "GroupId": "AGPAYELBJFIPAUQAE24OZ",
            "Arn": "arn:aws:iam::559086643742:group/tgs_admin",
            "CreateDate": "2023-04-17T01:02:32Z"
        }
    ]
}
```
### user - group 제거
```
aws iam remove-user-from-group --group-name admin --user-name Bob
```
### 다시 조회해보면 제거된 것을 확인할 수 있다.
#### ![image](https://user-images.githubusercontent.com/62974484/232965249-e4f14c40-7272-4043-a88d-b75ac4c3bcbc.png)
### <br/><br/><br/>

## user login profile 제거
### user 를 삭제하려면 login profile 을 삭제해야 한다.
```
aws iam delete-login-profile --user-name Bob
```
### <br/><br/><br/>

## IAM user 삭제
```
aws iam delete-user --user-name Bob
```
### Bob 계정이 삭제되었다.
#### ![image](https://user-images.githubusercontent.com/62974484/232953160-78b5b634-7ae3-4a43-b680-d665549ce268.png)



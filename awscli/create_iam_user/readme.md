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


## IAM user 삭제
```
aws iam delete-user --user-name Bob
```
### Bob 계정이 삭제되었다.
#### ![image](https://user-images.githubusercontent.com/62974484/232953160-78b5b634-7ae3-4a43-b680-d665549ce268.png)



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

## IAM user 삭제
```
aws iam delete-user --user-name Bob
```
### Bob 계정이 삭제되었다.
#### ![image](https://user-images.githubusercontent.com/62974484/232953160-78b5b634-7ae3-4a43-b680-d665549ce268.png)



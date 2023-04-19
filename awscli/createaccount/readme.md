# createaccount from aws-cli
### <br/><br/><br/>

## aws cli 접속
### security credential 받은 정보를 입력한다.
```
aws configure
```
#### ![image](https://user-images.githubusercontent.com/62974484/232943341-e3069e20-631a-4412-ab9e-77bd57735650.png)

### <br/><br/><br/>

## createaccount
```
aws organizations create-account --email shinejh0528@gmail.com --account-name "jhshin_test_org"
```
#### ![image](https://user-images.githubusercontent.com/62974484/232943353-a570f916-36ba-4214-ad45-80ae9dd85452.png)
### 그러면 다음과 같은 정보가 나온다.
```
{
    "CreateAccountStatus": {
        "Id": "car-5a96e870de5111edb03312a29ff7e955",
        "AccountName": "jhshin_test_org",
        "State": "IN_PROGRESS",
        "RequestedTimestamp": 1681867651.546
    }
}
```
### 생성 확인
```
aws organizations describe-create-account-status --create-account-request-id "car-5a96e870de5111edb03312a29ff7e955"
```
### 이미 있는 이메일이면 등록이 안 된다.
#### ![image](https://user-images.githubusercontent.com/62974484/232948425-10c0d48f-0fea-4d0b-a898-e752691d53f7.png)
### <br/>

### 다시 해보자
```
aws organizations create-account --email meowtail001@gmail.com --account-name "meowtail_test_org"

```
```
{
    "CreateAccountStatus": {
        "Id": "car-7c8d7600de5711ed8a1f12a9e0efdf35",
        "AccountName": "meowtail_test_org",
        "State": "IN_PROGRESS",
        "RequestedTimestamp": 1681870285.486
    }
}
```
```
aws organizations describe-create-account-status --create-account-request-id car-7c8d7600de5711ed8a1f12a9e0efdf35
```
### 잘 생성되었다 !
#### ![image](https://user-images.githubusercontent.com/62974484/232948679-2bf9fac1-daa2-41d8-9abe-e3e94a6b212f.png)
#### ![image](https://user-images.githubusercontent.com/62974484/232948752-cb3f5807-bec4-4b49-ac31-55d86feca51b.png)
### <br/><br/><br/>

### AWS organization 에 가보면 새로운 account 가 생긴 것을 확인할 수 있다.
#### ![image](https://user-images.githubusercontent.com/62974484/232943612-a8c13be4-9d08-4431-bd71-4968844da78e.png)
### <br/><br/><br/>

## create IAM user group
```
aws iam create-group --group-name cli-group-test
```
#### ![image](https://user-images.githubusercontent.com/62974484/232944844-956c4fdc-3ddf-4f97-a2ce-012198f02724.png)
### <br/>
### attach policy
```
aws iam attach-group-policy --policy-arn arn:aws:iam::aws:policy/AdministratorAccess --group-name cli-group-test
```
### 그러면 group 에 policy 가 붙은 것을 확인할 수 있다.
#### ![image](https://user-images.githubusercontent.com/62974484/232945079-a635ff77-b620-4491-a37e-36972ad0131f.png)

### <br/><br/><br/>


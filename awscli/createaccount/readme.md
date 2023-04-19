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
### <br/><br/><br/>

### AWS organization 에 가보면 새로운 account 가 생긴 것을 확인할 수 있다.
### 
#### ![image](https://user-images.githubusercontent.com/62974484/232943612-a8c13be4-9d08-4431-bd71-4968844da78e.png)



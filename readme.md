# 220711
## This repository describe AWS

### <br/><br/><br/> 

# How to handle AWS data (AWS s3 example)
## Install AWS-CLI
```
# for root user
$ curl "https://awscli.amazonaws.com/awscli-exe-linux-x86_64.zip" -o "awscliv2.zip"
$ unzip awscliv2.zip
$ sudo ./aws/install

# for conda
$ conda install -c conda-forge awscli
```

### <br/><br/><br/>

## configure (login)
```
$ aws configure
# type
>>> ID
>>> password
>>> region : Default is None. Just type enter or specify your region.
>>> data type : default is None. The AWS default data type is json.
```

### <br/><br/><br/>

## Lookup your data in AWS cloud
```
$ aws s3 ls s3://[your s3 cloud name]
# ex) --recursive 하면 하위 폴더까지 전부 다 볼 수 있음
$ aws s3 ls s3://genohub4956772/TBO220680_15455_20220711/ --recursive
```
![image](https://user-images.githubusercontent.com/62974484/178195751-f3c26942-6af2-481a-8c95-086b7f7cc87f.png)
### ls 에서 유용한 옵션
- --human-readable (boolean) Displays file sizes in human  readable  format.
- --summarize  (boolean) Displays summary information (number of objects, total size).

### <br/><br/><br/>

## remove data
```
$ aws s3 rm s3://[your s3 cloud name]/[directory]/ --recursive
```
![image](https://user-images.githubusercontent.com/62974484/178195889-7db433f0-9b9c-4a2e-8a4f-6104ec8109e3.png)

### <br/><br/><br/>

## upload data
```
$ aws s3 sync [your local directory] s3://[your s3 cloud name]
# or 
$ aws s3 sync [your local directory] s3://[your s3 cloud name]/[directory you want to upload]
```

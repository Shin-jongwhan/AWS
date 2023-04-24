## ec2 목록 조회
### * aws configure 에서 region 을 써줘야 한다. 나는 ap-northeast-2 로 등록했다.
### filtering 해서 볼 수도 있다.
```
aws ec2 describe-instances --filters "Name=instance-type,Values=t2*"
```
### 결과
```
{
    "Reservations": [
        {
            "Groups": [],
            "Instances": [
                {
                    "AmiLaunchIndex": 0,
                    "ImageId": "ami-0a306845f8cfbd41a",
                    "InstanceId": "i-085279dd6c144e0e1",
                    "InstanceType": "t2.micro",
                    "KeyName": "TGS",
                    "LaunchTime": "2023-04-24T05:38:23.000Z",
                    "Monitoring": {
                        "State": "disabled"
                    },
                    "Placement": {
                        "AvailabilityZone": "ap-northeast-2a",
                        "GroupName": "",
                        "Tenancy": "default"
                    },
                    "PrivateDnsName": "ip-10-0-15-0.ap-northeast-2.compute.internal",
                    "PrivateIpAddress": "10.0.15.0",
                    "ProductCodes": [],
                    "PublicDnsName": "ec2-13-124-168-185.ap-northeast-2.compute.amazonaws.com",
                    "PublicIpAddress": "13.124.168.185",
                    "State": {
                        "Code": 16,
                        "Name": "running"
                    },
                    "StateTransitionReason": "",
                    "SubnetId": "subnet-0e0879ba2383d9bdb",
                    "VpcId": "vpc-08d1160b4ba29ee76",
                    "Architecture": "x86_64",
                    "BlockDeviceMappings": [
                        {
                            "DeviceName": "/dev/xvda",
                            "Ebs": {
                                "AttachTime": "2023-04-24T05:38:24.000Z",
                                "DeleteOnTermination": true,
                                "Status": "attached",
                                "VolumeId": "vol-084dfb8789ec7ec04"
                            }
                        }
                    ],
                    "ClientToken": "c31876a7-5fb7-45a7-8f81-4945cd2139c4",
                    "EbsOptimized": false,
                    "EnaSupport": true,
                    "Hypervisor": "xen",
                    "NetworkInterfaces": [
                        {
                            "Association": {
                                "IpOwnerId": "amazon",
                                "PublicDnsName": "ec2-13-124-168-185.ap-northeast-2.compute.amazonaws.com",
                                "PublicIp": "13.124.168.185"
                            },
                            "Attachment": {
                                "AttachTime": "2023-04-24T05:38:23.000Z",
                                "AttachmentId": "eni-attach-06a0bdfd618629eab",
                                "DeleteOnTermination": true,
                                "DeviceIndex": 0,
                                "Status": "attached",
                                "NetworkCardIndex": 0
                            },
                            "Description": "",
                            "Groups": [
                                {
                                    "GroupName": "launch-wizard-2",
                                    "GroupId": "sg-0dea02081a6802726"
                                }
                            ],
                            "Ipv6Addresses": [],
                            "MacAddress": "02:93:a9:82:63:70",
                            "NetworkInterfaceId": "eni-0610ccbc8f05186f7",
                            "OwnerId": "559086643742",
                            "PrivateDnsName": "ip-10-0-15-0.ap-northeast-2.compute.internal",
                            "PrivateIpAddress": "10.0.15.0",
                            "PrivateIpAddresses": [
                                {
                                    "Association": {
                                        "IpOwnerId": "amazon",
                                        "PublicDnsName": "ec2-13-124-168-185.ap-northeast-2.compute.amazonaws.com",
                                        "PublicIp": "13.124.168.185"
                                    },
                                    "Primary": true,
                                    "PrivateDnsName": "ip-10-0-15-0.ap-northeast-2.compute.internal",
                                    "PrivateIpAddress": "10.0.15.0"
                                }
                            ],
                            "SourceDestCheck": true,
                            "Status": "in-use",
                            "SubnetId": "subnet-0e0879ba2383d9bdb",
                            "VpcId": "vpc-08d1160b4ba29ee76",
                            "InterfaceType": "interface"
                        }
                    ],
                    "RootDeviceName": "/dev/xvda",
                    "RootDeviceType": "ebs",
                    "SecurityGroups": [
                        {
                            "GroupName": "launch-wizard-2",
                            "GroupId": "sg-0dea02081a6802726"
                        }
                    ],
                    "SourceDestCheck": true,
                    "Tags": [
                        {
                            "Key": "tgs",
                            "Value": "test"
                        }
                    ],
                    "VirtualizationType": "hvm",
                    "CpuOptions": {
                        "CoreCount": 1,
                        "ThreadsPerCore": 1
                    },
                    "CapacityReservationSpecification": {
                        "CapacityReservationPreference": "open"
                    },
                    "HibernationOptions": {
                        "Configured": false
                    },
                    "MetadataOptions": {
                        "State": "applied",
                        "HttpTokens": "required",
                        "HttpPutResponseHopLimit": 2,
                        "HttpEndpoint": "enabled",
                        "HttpProtocolIpv6": "disabled",
                        "InstanceMetadataTags": "disabled"
                    },
                    "EnclaveOptions": {
                        "Enabled": false
                    },
                    "BootMode": "uefi-preferred",
                    "PlatformDetails": "Linux/UNIX",
                    "UsageOperation": "RunInstances",
                    "UsageOperationUpdateTime": "2023-04-24T05:38:23.000Z",
                    "PrivateDnsNameOptions": {
                        "HostnameType": "ip-name",
                        "EnableResourceNameDnsARecord": false,
                        "EnableResourceNameDnsAAAARecord": false
                    },
                    "MaintenanceOptions": {
                        "AutoRecovery": "default"
                    }
                }
            ],
            "OwnerId": "559086643742",
            "ReservationId": "r-06884bde475ee56e6"
        }
    ]
}
```
### <br/><br/><br/>

## tag 필터링하는 방법
```
aws ec2 describe-instances --filters "Name=tag-key,Values='tgs'" "Name=tag-value,Values='test'"
```
### 그러면 이렇게 key, value 가 있는 것들만 모아서 출력해준다.
#### ![image](https://user-images.githubusercontent.com/62974484/233910368-07a8962e-93a8-4d4e-9277-874629b65c3d.png)
### <br/><br/><br/>

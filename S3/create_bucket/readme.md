### 250922
# Create bucket

### bucket 이름은 '-'으로 이어서 쓴다.
#### <img width="1274" height="389" alt="image" src="https://github.com/user-attachments/assets/515503e2-cbd4-47d0-a65d-747c473f9f7b" />
### <br/>

### bucket 설정
#### 기본 설정으로 유지한다.
- Object Ownership
  - 모든 오브젝트는 버킷 소유 계정이 소유자로 고정됨.
  - 접근 제어는 ACL이 아니라 **버킷 정책(IAM 정책)** 으로만 관리.
  - 권장 설정 (혼자 쓰거나 Cognito, Lambda, 다른 AWS 서비스랑 연동할 때 더 안전).
- Block Public Access settings for this bucket
  - 퍼블릭(익명) 접근을 전부 차단.
  - ACL이나 퍼블릭 버킷 정책을 통해 열려고 해도 무시됨.
  - CloudFront + OAC 또는 Cognito 자격증명 등을 통해 인증된 경로로만 접근 가능.
#### <img width="1641" height="613" alt="image" src="https://github.com/user-attachments/assets/c8fc0709-c7fb-4d5f-9cfa-e086ddb8d21f" />
### <br/>

### Bucket Versioning
#### JSON 설정/프로필 같은 작은 데이터 → Versioning 켜는 걸 권장한다.
- 이유: 유저 데이터/주문 상태를 실수로 덮어쓰거나 잘못 삭제했을 때 되돌릴 수 있음.
- 비용 부담도 작음(작은 JSON들이라 추가 비용 거의 없음).
#### 반대로 대용량 데이터나 삭제되는 데이터는 끄기를 권장한다.
#### <img width="1623" height="191" alt="image" src="https://github.com/user-attachments/assets/639303b0-943a-46ef-a9cb-8363741e6113" />
### <br/>

### 태깅, 보안 설정
#### 태깅은 필요할 때만 사용. 지금은 태깅 없어도 괜찮고, 나중에 비용 분석이나 운영 편의를 원하면 나중에 추가해도 됨.
- 비용 관리: Project=MediaTranslator, Env=Prod, Owner=Shin 같은 태그를 붙여두면 Cost Explorer에서 서비스/프로젝트별 비용 추적 가능.
- 운영 관리: 특정 팀/서비스/환경 기준으로 리소스를 구분할 때 사용.
- 자동화/정책: 태그 조건으로 Lifecycle rule, IAM policy, Backup/Retention 정책 적용 가능.
#### SSE-S3는 무료이기때문에 이걸로 한다.
#### Bucket Key
- **S3 Bucket Key**는 SSE-KMS 쓸 때만 의미 있음.
- 같은 버킷 내 여러 객체 암호화를 묶어서 **KMS 호출 비용을 줄여주는 기능**.
- SSE-S3에서는 해당 없음.
#### 지금 설정 상태
- **SSE-S3 선택됨** → AWS 기본키 암호화, 비용 없음, 권장값.
- **Bucket Key: Enable** → SSE-S3에서는 의미 없음 (그냥 둬도 무방).
#### <img width="1626" height="536" alt="image" src="https://github.com/user-attachments/assets/906b595f-1704-4e53-a58b-c22275b85c71" />
#### <img width="1193" height="534" alt="image" src="https://github.com/user-attachments/assets/b5945537-23ae-4de8-aa62-c6a51da30f88" />
### <br/>

### 지금처럼 SSE-S3 (기본 암호화) + Public Access 차단 + ACL 비활성화 조합이면, 보안과 비용 사이에서 가장 합리적인 설정이다. 그냥 기본값으로 설정된 상태로 그대로 가면 된다.
### <br/>

### Object Lock
#### 필요한 경우 설정
- S3에 저장된 객체를 Write Once Read Many (WORM) 방식으로 보호.
- 지정한 기간 동안(예: 30일, 1년) 객체를 삭제/수정할 수 없게 만듦
- 규제 준수(금융, 의료, 법적 보관 등)에 자주 사용
- Versioning이 켜져 있어야만 동작
#### <img width="1627" height="266" alt="image" src="https://github.com/user-attachments/assets/c6b0e778-2f4e-4a89-a1c0-7628c2a09e13" />

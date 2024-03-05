## AWS Route53 도메인 구매
[AWS Route53](https://console.aws.amazon.com/route53/v2/home)
![image](https://github.com/chihyeonwon/Domain_HTTPS_Security/assets/58906858/38adde3c-14c8-4f5f-a441-af6a7780f655)
```
시작하기를 눌러서 도메인 구입을 시작한다.
```
![image](https://github.com/chihyeonwon/Domain_HTTPS_Security/assets/58906858/599790ab-7b20-4b59-9518-e8c4061cf7d0)
![image](https://github.com/chihyeonwon/Domain_HTTPS_Security/assets/58906858/e58d0589-2174-4b87-8edb-742922eff710)
```
.link 도메인은 1년에 5달러, .click 도메인은 1년에 3달러다. 저렴하고 기억하기 쉬운 도메인을 찾아서 등록한다.

자주 사용하는 .com 의 도메인은 13달러였다. 지금은 프로젝트용 도메인을 구매하기 위해 5달러의 .link를 구매했다.
```
![image](https://github.com/chihyeonwon/Domain_HTTPS_Security/assets/58906858/11dc3ec1-663e-4d7f-8345-6645ed204011)
![image](https://github.com/chihyeonwon/Domain_HTTPS_Security/assets/58906858/0d99c994-3634-4bec-9156-0c252cd9b879)
```
연락처 정보를 입력하는 창이 나온다. 이메일 인증을 15일 내에 하지 않으면 도메인이 유효하지 않게 된다는 경고문이 나온다.
```
![image](https://github.com/chihyeonwon/Domain_HTTPS_Security/assets/58906858/ba220fb2-eb60-4b6c-9a81-a501a204e242)
```
입력한 이메일로 인증용 이메일이 오고 링크를 클릭해서 인증을 완료했다.

도메인 구매는 1년을 단위로 하고 1년이 지날 때마다 자동으로 갱신하기를 원한다면 Enabled 옵션을 선택하고
1년만 구매하고 1년 후 수동으로 갱신하려면 Disable 옵션을 선택한다.

Disabled 를 사용하여 하반기 프로젝트 배포용으로 사용했다.

AWS에서 도메인을 등록하는 데 2시간에서 최대 3일까지 걸릴 수 있다.(현재 진행중 상태)
```
![image](https://github.com/chihyeonwon/Domain_HTTPS_Security/assets/58906858/03f7a69d-0536-4967-9190-51087a1d30d8)
![image](https://github.com/chihyeonwon/Domain_HTTPS_Security/assets/58906858/5019c5c0-d283-43b9-b69f-178fed46334f)
```
도메인 등록에 성공하면 등록이 완료되었다는 이메일을 확인할 수 있고 호스팅 영역 대시보드에서 등록한 도메인을 확인할 수 있다. 
```
## ACM을 이용해서 SSL certificate 발급
[ACM Amazon Certification Manager](https://console.aws.amazon.com/acm/home)
![image](https://github.com/chihyeonwon/Domain_HTTPS_Security/assets/58906858/fda71277-ded8-4eb5-ae68-cc1554891dd8)
```
HTTPS 보안 연결을 사용하기 위해 SSL Certification을 발급 받는다.

ACM은 무료이므로 한 번만 익혀두면 HTTPS 보안 연결을 세팅할 때 유용하게 사용할 수 있다.
```
![image](https://github.com/chihyeonwon/Domain_HTTPS_Security/assets/58906858/35d9b7e4-ac13-4fed-a538-08b3c1d19be8)
```
Request a public certificate 인증서 요청을 선택한다.
```
![image](https://github.com/chihyeonwon/Domain_HTTPS_Security/assets/58906858/bdf5955e-0dae-4f55-9906-cbac69446807)
```
완전히 정규화된 도메인에는 HTTPS 보안 연결을 적용하고자 하는 도메인을 입력한다.(oneflix.link)
validation 검증 방법을 선택하는 부분에서는 DNS 검증을 선택한다. route53과 연동해서 쉽게 도메인 연결을 진행할 수 있기 때문이다.
```
![image](https://github.com/chihyeonwon/Domain_HTTPS_Security/assets/58906858/47592c15-d64d-46c2-803e-de0c0c2819fa)
```
키 알고리즘은 RSA 2048, 태그는 아무것도 지정하지 않고 요청한다.
```
![image](https://github.com/chihyeonwon/Domain_HTTPS_Security/assets/58906858/d37cf473-1a62-4de2-a6b0-a79855bd7c7b)
```
검증 대기 중 상태의 인증서가 발급되었다. 
```
![image](https://github.com/chihyeonwon/Domain_HTTPS_Security/assets/58906858/6befdf6a-599b-4c1b-ba69-6ebc87b75869)
![image](https://github.com/chihyeonwon/Domain_HTTPS_Security/assets/58906858/28af7a9f-d226-41e7-9297-a3f194e25b19)
```
도메인에서 Route 53에서 record가 생성되도록 한다.
```
![image](https://github.com/chihyeonwon/Domain_HTTPS_Security/assets/58906858/40a94feb-b8af-4e06-94fe-687401de67fa)
```
route 53로 가면 새로운 CName 레코드가 생성된 것을 확인할 수 있다.
이제 생성된 CNAME 레코드와 EC2를 연결해야 한다.
```
![image](https://github.com/chihyeonwon/Domain_HTTPS_Security/assets/58906858/b033f33f-51aa-4f3b-bd4c-79156bfd0697)
```
레코드 생성 버튼을 누르면 빠른 레코드 생성창이 나온다.

Record name 레코드 이름은 빈칸을 그대로 둔다.
만약 서브도메인(예를 들어 blog.oneflix.link와 같은)을 사용하고 싶다면, Record name에 적어주면 된다.

Value 값 부분은 EC2 인스턴스의 퍼블릭 IPv4 주소를 적는다.

다른 값들은 그대로 두고 레코드 생성을 누른다.
```
![image](https://github.com/chihyeonwon/Domain_HTTPS_Security/assets/58906858/277478d5-2dcb-4baa-9ada-9c31e2cff7b5)
```
oneflix.link에 대한 레코드가 생성되었다고 한다.
```
## fast api middleware 세팅 후 재배포
```
cors에서 origin이란 출처를 뜻하고 이는 프로토콜, 도메인, 포트번호의 조합을 뜻한다.
프론트엔드와 백엔드가 같은 출처가 아닐 경우 보안 상의 문제가 있을 수 있다고 판단한다.
따라서 요청을 보내는 프론트엔드의 출처가 믿을 수 있는 출처임을 명시해주는 과정이 필요하다.
fast api에서는 이를 CORSMiddleware를 이용해서 해결한다.

1. 출처의 목록을 명시해주어야 한다.
2. 미들웨어를 추가하는 코드를 만들어야 한다.
```

#### main.py 출처의 목록 명시 
```python
origins = [
    # "http://localhost",
    # "http://localhost:3000",
    # "https://dq-hustlecoding.github.io/dqflex",
    # "https://dq-hustlecoding.github.io",
    # "http://api.dqflex.kro.kr:8080",
    # "http://api.dqflex.kro.kr",
    "*",
]
```
#### main.py 미들웨어를 추가
```python
from fastapi.middleware.cors import CORSMiddleware

middleware = [
    Middleware(
        CORSMiddleware,
        allow_origins=origins,
        allow_credentials=True,
        allow_methods=["*"],
        allow_headers=["*"],
    )
]
```
```
기존 main.py 코드에 출처의 목록을 명시하는 코드와 미들웨어를 추가하는 코드를 추가해준다.

출처의 목록 명시 : 개발 환경에서 사용하는 localhost, 프론트엔드 배포 시에 자동으로 생성되는 GitHub Pages 주소 2개
(https://chihyeonwon.github.io/oneflix, https://chihyeonwon.github.io)와 https://oneflix.link 를 추가했다.

middleware 추가 : fastapi의 공식 튜토리얼에서 제공하는 코드를 그대로 사용한다.
명시된 origins 목록은 허용된 origins로 사용하고, method나 header는 전부 허용하겠다는 의미다. 
```

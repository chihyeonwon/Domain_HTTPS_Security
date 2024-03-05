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
[ACM Amazon Certification Manager](https://aws.amazon.com/acm/home)
```
HTTPS 보안 연결을 사용하기 위해 SSL Certification을 발급 받는다.

ACM은 무료이므로 한 번만 익혀두면 HTTPS 보안 연결을 세팅할 때 유용하게 사용할 수 있다.
```










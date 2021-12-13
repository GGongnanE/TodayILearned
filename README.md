# TodayILearned_GGNE (2021.12 ~ 2022)
    
누군가에겐 "이런 것도 모르나?" 싶을 정도로 쉬운 문제일 수도 있다.
하지만 난 누가 뭐라 지껄이건 흔들리지 말고 계속 기록해야만 한다.  
내 페이스대로 꾸준하게.. 지치고 귀찮더라도 포기하지 않고 한발자국씩 나아가다보면  
예전보다는 한단계 쯤은 성장해있지 않을까?  
주어진 환경에서 최대한 기록해보자. (최소 주 3회 이상 목표..)
  

## JAVA
    - 21.12.02 
      : 간만에 servlet/JSP 공부 중이다. 
        MVC 패턴 -> 서블릿을 컨트롤러, JSP를 뷰로 사용해서 적용 
                    모델은 HttpServletRequest를 사용 -> request는 내부에 데이터 저장소를 가진다. 
                    request.set/getAttribute() 를 통해 보관, 조회한다. 
        ** 몰랐던 사실 
          1. WEB-INF - 해당 디렉토리 안에 JSP가 있으면 jsp를 직접 호출할 수 없다. 
                       컨트롤러를 통해서 jsp를 호출하도록 하기 위함.
          2. redirect / foward
            : 리다이렉트는 실제 클라이언트(웹브라우저)에 응답이 나갔다가 클라이언트가 리다이렉트 경로로 다시 재요청하는 것. 
              따라서 클라이언트가 이를 인지할 수 있고, url 경로도 변경이 된다. 
              포워드는 서버 내부에서 일어나는 호출이기 때문에 클라이언트가 전혀 인지할 수 없다. 
    - 21.12.06
        Java RSA 암복호화 시, keyValidException 해결 방법
        https://coderedirect.com/questions/602282/how-to-read-a-rsa-public-key-file-in-java
        - JAVA에서 지원하는 형식 : 자바에서 지원하는 RSA PEM 파일 형식이 맞지 않음
          자바는 PKCS#1 지원 안하고, PKCS#8만 지원함 ([출처] JAVA RSA invalid key format 오류|작성자 퍼대기)   -> 근데 출처가 없어서.. 불확실함. 확인 필요 
    - 21.12.07
       : JWT.. 어디서 들어본 것 같다... (JSON Web Token) 
         개요 정리된 글 (https://www.letmecompile.com/api-auth-jwt-jwk-explained/)
    - 21.12.08
       : JWK(JSON Web Key) 방식의 json 데이터를 받아, nimbusds 라이브러리를 통해, RSAPublicKey를 만들어서 암호화 API의 구조를 변경할 수 있었다.
         아쉬운 점은 외부 라이브러리에 의존하지 않고, 자바 기본 메소드들로 구현하고 싶었지만.. 그러지 못해 아쉽다. 
       (여담..) 왜 일본 측에선 암호화 값에 시간(java에서 기본적으로 제공하는 Instant)값을 같이 추가한걸까? (암호화 대상 데이터 + 현재 시간값)
         -> 같은 데이터 예를 들어 카드비밀번호 4자리인경우.. (1234라는 값으로 계속 같은 값을 주고받으면 해커가 해킹할 수도 있다.)  <- 설명이 개떡같은데.. 추후 보강하자.
            -> (암호화할 값 + 암호화하는 시점의 현재시간) 괄호안의 이 값을 한꺼번에 암호화해서 같은 값이어도 암호화 되어 리턴되는 값은 매번 달라진다. 
            -> 이는 복호화 시, 언제 만들어진 데이터인지 알아볼 수 있는 역할도 하고, 암호화 되는 데이터에 대해 약간의 보안성을 더 높이는데 도움이 되는 듯..하다.
    - 21.12.09
       : 1. 암복호화 테스트가 정상적으로 끝났다. 관련된 내용을 취합해 정리해야 한다. 
    - 21.12.10
       1. 암복호화 공부 필요 
         (https://yjshin.tistory.com/entry/%EC%95%94%ED%98%B8%ED%95%99-%EB%B9%84%EB%8C%80%EC%B9%AD%ED%82%A4-%EC%95%94%ED%98%B8-RSA-%EC%95%94%ED%98%B8%EC%8B%9C%EC%8A%A4%ED%85%9C)
       2. oaepparameterspec은 OAEPPadding과 관련이 있었다.
          https://ko.m.wikipedia.org/wiki/OAEP 

    - 21.12.13
       1. 이걸 자바라고 봐야될지.. 모르겠지만.. 계속 자바 암복호화 관련... 이슈가 있다. 
          https://celdee.tistory.com/m/228
          https://www.holaxprogramming.com/2017/06/12/encryption-with-rsa/
          RSA 알고리즘 방식의 암복호화 시, 공개키를 검증(sign)할 때 사용하는 시그니처라는 개념이 또 등장했다. 공부 필요하다.. (우리 플젝은 fixedPrivateKey라는 이름으로 썼다.)
       2. AES 알고리즘을 사용하는 암복호화 키에 이상한 garbage data가 섞여있으면 Base64 디코딩을 하지 못하고 IllegalArgumentException이 발생하는 현상이 있다. 
          ex) input byte array has incorrect ending byte at 44
       3. java 개발자 사이에서 이슈일만한 사건 발생 -> log4j2에서 보안 취약점 발견 -> log4j2 사용자는 2.15.0 버전으로 업그레이드 필요 

## Git
    - 21.12.02
        : gitHub 기준, private Repository에 밤날 커밋한들, 내 자신 외에 타인이 내가 커밋을 했는지 안했는지 알 수가 없다. 
          내 계정으로는 잔디밭이 추가된것 처럼 보이는데, 로그아웃하고 내 계정을 조회해보니 잔디밭이 없어져있다.. 




## Linux 
    - 21.12.03 
        : 일하던 중 있었던 일이다.. find 명령어에서 symbolic link로 설정한 디렉토리 안의 파일을 찾지 못하는 현상이 있었다. 
          find의 옵션 중 -L 옵션을 주면 심볼릭 링크로 걸려있는 디렉토리 안의 파일을 처리할 수 있었다. 


## Python


## IDE
    
### IntelliJ 


<!-- <details> -->
<details markdown="1">
<summary>접기/펼치기 테스트</summary>

<!--summary 아래 빈칸 공백 두고 내용을 적는공간-->
       - 21.12.02
       : Inline Variable 단축키 : 컨트롤 + 알트 + N
         (ex) 
         \`MyView myView = new MyView("/WEB-INF/views/new-form.jsp");  return myView; \`
            -> return new MyView("/WEB-INF/views/new-form.jsp");
---
```
abcd
```
    defg
\` String abc = new String("abc");\`
</details>

https://github.com/lazypic/pandoc/blob/master/04_Markdown.md


    - 21.12.02
       1. Inline Variable 단축키 : 컨트롤 + 알트 + N
         (ex) 
         MyView myView = new MyView("/WEB-INF/views/new-form.jsp");  return myView;
            -> return new MyView("/WEB-INF/views/new-form.jsp");

       2. 어떤 로직을 메소드로 빼고 싶을 때 -> 따로 분리할 코드를 블록지정한 후, 컨트롤 + 알트 + M 


## ETC
<!-- <details> -->
<details markdown="1">
<summary>이 일을 하며 내가 느낀 것</summary>

<!--summary 아래 빈칸 공백 두고 내용을 적는공간-->
    - 21.12.09 
       : 인간은 생각보다 강하다. 위기가 닥쳐오면 어떻게해서든 해결해 낸다. (포기하지 않는다는.. 전제하에) 
         그 고통을 이겨냈을 때, 한단계 성장하는 느낌을 받을 수 있다. 나는 그것을 오늘 다시금 깨달았다. 물론.. 여기까지 오는데 너무 짜증났지만.. 그래도 뿌듯하다. 
         처음으로 인정받은 거라서 더 감회가 새롭고, 자신감이 붙었고, 더 열심히 하면 탈출할 수 있을 것이라는 희망이 생겼다. 

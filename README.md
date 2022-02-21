# TodayILearned_GGNE (2021.12 ~ 2022)
    
누군가에겐 "이런 것도 모르나?" 싶을 정도로 쉬운 문제일 수도 있다.
하지만 난 누가 뭐라 지껄이건 흔들리지 말고 계속 기록해야만 한다.  
내 페이스대로 꾸준하게.. 지치고 귀찮더라도 포기하지 않고 한발자국씩 나아가다보면  
예전보다는 한단계 쯤은 성장해있지 않을까?  
주어진 환경에서 최대한 기록해보자. (최소 주 3회 이상 목표..)
  



## JAVA
    -22.01.03
    https://reference-m1.tistory.com/m/349
    -22.01.04
    로그백 관련된 설정이 왜 적용이 안되는가에 대해 원인을 찾았다. 
    rolling 설정을 주어 로그 파일이 분할되도록 설정해 놓았는데, 파일사이즈에 대한 인덱스 문법이 빠져있었다. (%i) 
    저 두 글자때문에 실행 오류는 없고, 로그파일은 생기지 않는 정말 짜증나는 오류를 맞이했다. 
    좀 더 설정파일을 세심히 봤더라면 금방 찾았을 텐데 아쉽다. xml 문법 오류에만 신경썼는데 정작 설정값에 오타가 있을 줄이야.. 
    -22.01.06
        1. throw와 throws의 차이.. 알아야함. 
        2. java의 resultSet 공부해야함. 
    - 22.01.11
        1. 테이블 락이 걸리면 일반 스프링 기반의 웹서비스 실행 시, SQL(select 제외)문이 수행되지 않을 수 있다. 
           테이블 락은 직접 락을 거는 것도 가능한데, 오라클의 for update 문을 사용하면 된다. 
           자바로 넣을지.. SQL로 넣을지 애매~하긴 한데 일단 자바 개발하다가 해본 거라서 여기다 쓴다. 
           참고 : https://tyrionlife.tistory.com/m/41 
                  https://lipton.tistory.com/m/entry/%EC%98%A4%EB%9D%BC%ED%81%B4-%ED%85%8C%EC%9D%B4%EB%B8%94%EB%A0%88%EC%BD%94%EB%93%9C-%EB%9D%BD
    - 22.01.12
        1. String과 char 활용
            String str = "abc";
            str.toUpperCase();
            char c = 'b';
            c = Character.toUpperCase(c);
            // String에서 문자 하나를 읽기 
            Scanner scan = new Scanner(System.in); 
            String inputStr = scan.next();
            char inputChar = scan.next().charAt(0);   // String 문자열 중 0번째 인덱스의 값을 가져온다. 
    - 22.01.13
        - AES 알고리즘을 이용해서 파일 자체를 암복호화하는 케이스도 많다. 
          다만, 키 사이즈가 128을 넘으면 안되는 듯 하다. 오류 발생하더라.. -> PC 환경 문제인듯(다른 P에선 잘됨) 
    - 22.01.20
        오랜만에 글쓴다.. 
        - 파일 암복호화(AES/GCM/Nopadding) 관련 알게 된 것. 
            1. 벡터(iv)는 암호화/복호화 시, 동일해야 한다. 
            2. 벡터를 어떻게 생성하느냐는 관계 없다. 
                - 고정된 값을 바이트화 하건, 랜덤한 난수값을 바이트화 하건 자릿수만 맞추면 되고, 암,복호화 시 같은 벡터값을 사용하기만 한다면 문제되지 않는다는 의미. 
            3. 파일을 읽어 한번에 처리하는 방식 or 버퍼사이즈를 만들어 버퍼 사이즈 만큼 읽어 암복호화 하는 방식 -> 각각 장단점이 있을 수 있으나 파일사이즈가 작다면 전자, 크다면 후자를 권장
                - 전자의 경우, 파일 사이즈가 너무 크다면 OOM을 발생시킬 여지가 있을 수 있다. 
                - 후자의 경우, 처리 속도가 느린 단점이 있을 수 있다. 
    - 22.01.21
        1. 직렬화한 파일을 역직렬화 할 경우, 객체를 읽을 때, 순서가 정확히 일치해야 오류가 발생하지 않는다. -> 테스트 해보니 타입이 맞지 않아 ClassCastException이 발생했다.
        2. 람다와 스트림에 대해 공부했다. 익숙하지가 않다. 연습이 매우.. 많이 필요할 것으로 판단된다.  
    - 22.01.26
        1. 코드가 얼마나 복잡한가에 대한 근거 
            : CognitiveComplexity 라는걸 소나린트에서 측정하는 것 같다. 
              소나린트에서는 이 복잡도를 15 미만으로 사용할 것을 권장하며 수정하라며 나의 시야를 괴롭힌다. 
              https://coding0.tistory.com/76
              https://www.sonarsource.com/docs/CognitiveComplexity.pdf
    - 22.01.28
        1. 자바에서의 캐스팅 
            - 업캐스팅 : 자식클래스를 부모클래스 타입으로 형변환 하는 것. 
            - 다운캐스팅 : 부모클래스타입으로 업 캐스팅된 클래스를 다시 자식클래스의 형태를 되돌리는 것. 
                          때문에 다운캐스팅이 일어나기 위해서는 업캐스팅이 선행되어야 한다. + 명시적으로 타입을 지정해야 한다. 
            참고 : 1. https://madplay.github.io/post/java-upcasting-and-downcasting
                   2. https://bgm16.tistory.com/103
    - 22.01.29,30 ~ 2.2
        1. 설날 연휴라 휴무였다. 
        2. 자바의 정석 3판을 다시 복습중이다. 
            - 프로그래밍 능력 중 중요한 요소 중 하나는 바로 값을 잘 다루는 것. 
                -> 대충 볼 땐 몰랐는데 2진법, 8진법, 2의 보수법 다시 등장하니 머리가 지끈지끈하다. 내일 보면 좀 나아질까?
            - 자바의 정석 정리 중인 노션 링크 : https://www.notion.so/mickey74/39b4fd4fbd8a4fcfa6c2f2e158609b67
        3. 자바 문법 정리 
            - 대소문자 변환 
                String str = str.toUpperCase();
                char ch = 'a';
                ch = Character.toUpperCase(ch);
            - 배열만들기 (문자배열) -> 문자열 처리 문제들에서 쓰임. (for-each와 혼용)
                char[] charArr = str.toCharArray();  
            - 문자 하나를 가져오기 
                Scanner scan = new Scanner(System.in); 
                char ch = scan.next().charAt(0);
            - split / substring (문자열 자르기) 
                String[] strArr = str.split(" ");
                // indexOf() : 특정 문자나 문자열이 앞에서부터 찾기 시작해  처음 발견되는 인덱스를 반환
		        // 해당 조건 값을 찾지 못할 경우 -1을 반환한다.
		        // lastIndexOf() : indexOf와 유사하나 문자열을 뒤에서부터 찾음.
                // substring(int x, int y) : x번 인덱스 부터 (y번 인덱스-1)까지 해당되는 문자열을 반환한다.
	- 22.02.08 
	   1. syncronized lock?
	- 22.02.16
	   1. 문자열(String) 처리 시, 항상 null이 발생할 수 있는 케이스를 고려하자. 
	   2. 문자열 split() 사용 시, 특정 문자로 잘라낼 수 없는 경우 그냥 원 문자열을 리턴해준다.
	- 22.02.21
	   1. import와 static import의 차이는 뭘까? (JUnit 테스트 중.. 발생)
	   2. java 8의 신규 기능들 복습 중이다. 오늘은 람다 진행함
	   	- 함수형 인터페이스는 추상메소드가 하나만 존재하는 인터페이스이다. 
		- 만약, 추상메소드가 하나 이상 존재하면 그것은 함수형 인터페이스가 아니다. 
                  (static 메소드나 default 메소드의 존재여부와는 관계 없다. 오로지 추상메소드의 숫자가 중요하다.)
## GIT
    - 22.01.01
        git 기본 복습 중이다. 
        노션 참고 
    - 22.01.02
        git 강의 이어서 듣고 있는데 gitLab은 여전히 마스터 브랜치를 default로 쓴다. 
        $ git push origin master
          remote: HTTP Basic: Access denied
          fatal: Authentication failed for 'https://gitlab.com/zzlzlzl007/gittest2.git/'
        push를 못하길래 엑세스 토큰을 만들어서 id,pw에 토큰 넣으니 잘 된다. 
        https://stackoverflow.com/questions/47860772/gitlab-remote-http-basic-access-denied-and-fatal-authentication
    - 22.01.04
        git의 default 브랜치 변경하는 방법
        < 요약 >
        - git 2.28버전에서부터 default 브랜치를 변경할 수 있는 옵션이 추가되었다. 
          git config --global init.defaultBranch main으로 init.defaultBranch를 설정한다. 
          전역 설정으로 지정했으므로 이는 ~/.gitconfig에 아랫부분이 추가된다.(직접 ~/.gitconfig를 수정해도 된다.)
          그 이후 git 로컬저장소를 초기화한다.
          (참고) https://blog.outsider.ne.kr/1503
    - 22.01.24
        : 깃 기초 강의 완강..(진짜 귀찮아서 언제듣나 언제듣나 하던게 24일 걸렸네..)
        - 머지 종류
          1. fast-forward : 브랜치의 위치만 최신 커밋으로 이동 시키는 방식 
          2. 3-way merge : 공통 커밋, 병합할 브랜치들의 최신 커밋 들을 기준으로 새로운 merge commit을 만드는 것을 의미.
                           충돌 발생 시, 충돌을 사용자가 직접 해결 후, 다시 머지 할 것. 
                           git bash에서는 git mergetool 이라는 것이 있음.


## ETC
    - 22.01.26
        : 리눅스는 대소문자를 구분하지만 윈도우즈는 대소문자 구분을 안한다? 구분자가 다른건 알고 있었지만 이건 또 뭐지?? 싶었다. 
          (git이나 gitLab에서는 대소문자 구분을 하는데 이클립스에서는 구분을 안한다는 문의가 있었나보다. 근데 알고보니.. 윈도우 환경에선 대소문자 구분을 안하는 것 같다. 현재 내가 일하고있는 프로젝트 내 환경에선 이클립스는 윈도우에 깔려있으니까..)
          https://lemeraldl.tistory.com/m/entry/%EB%A6%AC%EB%88%85%EC%8A%A4%EB%8A%94-%EB%8C%80%EC%86%8C%EB%AC%B8%EC%9E%90-%EA%B5%AC%EB%B6%84%ED%95%98%EA%B3%A0-%EC%9C%88%EB%8F%84%EC%9A%B0%EB%8A%94-%EB%8C%80%EC%86%8C%EB%AC%B8%EC%9E%90-%EA%B5%AC%EB%B6%84-%EB%AA%BB%ED%95%9C%EB%8B%A4

    - 22.02.09
    	: 나태해지지 말고 짜잘한 실수를 줄여야한다. 경험치에 비해 실수가 잦다. 
	  물론 사람이기에 실수할 수 있고, 내가 처했던 상황이 아예 이해가 안가진 않는다만 다 변명에 불과하다. 
    - 22.02.14
    	: 배울 것이 없다. 매너리즘이 찾아온 것 같다. 일이 적다. 공부를 할 수 있는 환경도 아니다. 나가야되나.. 심히 고민이다. TIL도 쓸 것이 없다. 
    - 22.02.17
    	: 단단해지자. 남탓을 하지말자. 나에게서 원인을 찾고, 개선방안을 만들자. 스트레스를 줄이자.

## OLD
<!-- <details> -->
<details markdown="1">
<summary>2021.12</summary>

<!--summary 아래 빈칸 공백 두고 내용을 적는공간-->
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
    - 21.12.16
        1. 음.. 고객사 보안팀에서 흥미로운 의견을 제시했다. 
           - 일반 자바에서 제공하는 암호화 관련 라이브러리보다 apache common crypto를 사용하면 근소하지만 성능 우위가 있다고 함. 
             https://commons.apache.org/proper/commons-crypto/xref-test/org/apache/commons/crypto/examples 참고 
        2. HashMap 사용 시, 동일한 키 값의 데이터를 추가하면 새로운 값의 데이터만 남는다. (기등록된 키를 동일하게 다른 값으로 재등록하면 이전 값이 갱신됨.)
            ex) map.put(myId, "12345");
                map.put(asdf, "1111");
                map.put(asdf, "1234");       // 기존 값이 없어지고 1234가 추가됨. 
        3. Collections는 각종 타입에 맞게 동기화를 쉽게 할 수 있도록 메소드를 제공하고 있다. 
    - 21.12.20
        1. log4j 관련 이슈 정리 된 유튜브를 보자 
           (https://www.youtube.com/watch?v=kwS3twdVsko&ab_channel=%EB%85%B8%EB%A7%88%EB%93%9C%EC%BD%94%EB%8D%94NomadCoders)
        2. logback도 1.과 관련되어 보완 패치가 있었던 모양인데.. 그 버전으로 업버전해서 우리 솔루션에 패치를 진행했는데 jboss가 기동하지 않고 오류가 발생했다. 
           (추후 확인이 필요하다..)
           
    - 21.12.22
        1. 코드 분석을 자동으로 수행해주는 소나큐브라는게 있는데 IDE 내, 소나린트와 연동이 가능하다. 
           구글링 해본 바로는.. 연동자체가 그렇게 어려운 것 같지는 않아보인다. 
           하지만 간혹 오류 사례들의 문의를 보면 각자 테스트 환경이 제각각이다. (IDE의 종류, IDE가 같더라도 IDE 버전, 플러그인 버전, 자바 버전 등..) 
           이러다보니 내 환경에서 연동 중 오류가 나도 다른 사람들의 사례를 참고하기가 쉽지않다. 
           IDE와 소나큐브-소나린트를 연동 시키기만 하면 유용하게 사용할 수 있을 듯 하다. 
    - 21.12.27
        1. JMeter를 통한 병렬 부하테스트 해보기 
           : 직접 해보니 그렇게까지 어렵진 않았다. 실행 전, 자바 환경변수가 설정되어 있다면 문제없이 실행 된다. 
             가장 직전에 테스트하던 소나큐브-소나린트 연동보다는 훨씬 간결했다. 
             그리고 제이미터 플러그인을 사용해 기능 추가도 가능하다. 제이미터 플러그인은 인터넷이 연결되어있어야하기 때문에, 프로젝트 안에서 다운로드 받진 못했고, 
             내일 다시 반입요청을 해서 병렬테스트를 진행하려고 한다. 
             
           참고글 
           https://m.blog.naver.com/asemansa/221685008430
           https://xmlangel.github.io/How-Can-I-Use-Jmeter/
    - 21.12.28
        1. 중계로그를 파일로 남겨달라는 요건 
            : 어떤 객체를 json 형태의 String 문자열로 변환해서 그 문자열을 logger로 출력했다. 
              jackson 라이브러리의 ObjectMapper를 이용했고, logback의 appender 설정을 통해 파일로 남길 수 있다.
              결과만 확인한것이라 내 뇌피셜이 다분하지만.. 
              LoggerFactory.getLogger("relay.log")    <--- logback.xml 설정파일에 name="relay.log" 이런식에서 매핑을 해서 사용이 되는듯 하다. 
              내가 구현한 부분의 상세 코드는 내일 자세히 기록해와야겠다. 아침에 출근하면 그것부터 해야겠네... 
    - 21.12.29
        1. logback도 뭔가 취약점이 발견된 듯 하다. 관련해서 보완 패치 필요하다. 
            현재 프로젝트에서 사용하는 버전은 logback 1.2.3이고, 취약점이 해결되려면 1.2.9버전 이상을 사용해야 한다. 
            ** 참고 
            LOGBACK 관련 보안 위협
            - https://www.boho.or.kr/data/secNoticeView.do?bulletin_writing_sequence=36396&queryString=cGFnZT0xJnNvcnRfY29kZT0mc29ydF9jb2RlX25hbWU9JnNlYXJjaF9zb3J0PXRpdGxlX25hbWUmc2VhcmNoX3dvcmQ9
            - https://cve.report/CVE-2021-42550
            - 참고사항 내용중 영어 원문과 다른 부분 (KISA 공지사이트에서 번역이 이상하게 되었네요 . 
                - JMSAppender가 아니고 JDBCAppender와 비슷하게 구현된 DBAppender입니다. 
                - https://cve.report/CVE-2021-42550 내의 Reference로 연결된 https://github.com/cn-panda/logbackRceDemo의 텍스트를 보면 logback DBAppender로 나옵니다.
                        In logback, it is also similar to the Appender of JDBCAppender in log4j1.x —— that is DBAppender
                        There is an interface called ConnectionSource in DBAppender.
                        This interface provides a pluggable way to obtain a JDBC connection using the logback class of java.sql.Connection
                        There are currently three implementation classes: DriverManagerConnectionSource, DataSourceConnectionSource and JNDIConnectionSource.
            CVE-2021-42550 에 영향 받는 부분
                - CVE-2021-42550 에 따라 위협에 대한 패치로 logback에서 DBAppender, ConnectionSource 클래스 들을 삭제했습니다. 
                - 해당 부분에 대한 처리를 한 후 logback 1.2.9 와 같이 패치되어야 합니다. 
                주로 서비스로그 저장을 위한 Appender 부분에 대한 수정이 발생합니다. 
                해당 부분에 대하여 프로젝트 마다 사이트 커스터마이징이 존재하면 해당부분에 대한 수정도 필요할 것으로 보입니다. 
                ex) bxm.dft.logging.logback.DefaultAsyncTableAppender
                [참고] JMSAPPENDER 관련 보안 위협
                - https://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2021-4104
                - log4j 1.X대도 관련있음. 
                - JMSAppender 사용하지 않는 경우에는 영향이 없음.
        
        
## Git
    - 21.12.02
        : gitHub 기준, private Repository에 밤날 커밋한들, 내 자신 외에 타인이 내가 커밋을 했는지 안했는지 알 수가 없다. 
          내 계정으로는 잔디밭이 추가된것 처럼 보이는데, 로그아웃하고 내 계정을 조회해보니 잔디밭이 없어져있다.. 
    - 21.12.14
        : 음.. 내가 예전에 만들어 놓은 연습용 자바 프로젝트들이 default branch를 master로 사용중이었다.
          하지만, gitHub는 정책 변경으로 master를 main으로 사용중이라.. Pull request가 되지 않고, 계속 겉도는 상황이라 어쩔 수 없이 master -> main으로 default branch를 변경했다.
          https://kyeoneee.tistory.com/72
          위 링크대로 따라하던 중, 오류 발생하여 https://donggu1105.tistory.com/104를 참고 하여 해결 
    - 21.12.23 
        : VSCode에서 gitHub 연동하기. 
          https://webnautes.tistory.com/1422


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
    - 21.12.17
       : 프리랜서 생활을 함에 있어 필요한 자세 
          - 성실한 자세 : 남에게 헛점을 보인다는 것 자체가 내 이미지를 실추시키는 것. ex) 대놓고 민폐끼치며 잔다던가.. , 내 일을 다 끝마치지 않았는데 노는 것 등..
          - 감정: 내 고객과 절대로 감정적으로 대응하지 말 것. 최대한 이성적으로 대응하려고 노력할 것. 매사 스트레스 받는 일이 생기니 스트레스 관리 철저히 할 것. 
          - 내가 할수 있는 일과 없는일을 구분
            : 해결할 수 있으면 내 선에서 해결하되, 내가 해결할 수 없는 일을 너무 길게 고민하지 말고, 어떤 사람이 내게 도움을 줄 수 있는가를 명확히 파악할 것. -> 문제의 빠른 해결이 더 중요. 
    - 21.12.19
       <내가 고쳐야 할 것>
       1. 동기가 부족하다. -> 새로운 동기부여가 필요하다. 
       2. 피드백을 받는 시기가 느리다. (빠른 피드백을 통해 개선한다.)
       3. 내가 어떤 일을 할 때, 어떻게 진행할 것인지, 왜 이렇게 생각했는지 등을 기록하고 작업을 하자. 
       4. 의도적인 수련을 해야한다. 
           1) 내 수준에 맞는 적절한 난이도 조절 (난이도가 너무 쉬우면 지루해지고, 어려우면 불안, 스트레스를 받게 된다.)
              - 지루함을 느낀다면 : 난이도를 높여본다. 
                (원래 진행하려던 일정보다 조금 더 빠르게 개발을 마친다던가.., 이 기능은 몇시까지 만든다. 강제로 제한시간을 정하고 개발)
              - 너무 어렵다면 : 난이도를 낮춘다. 
                (내가 구현해야하는 것을 좀 더 후진(?) 안좋은?? 데모 버전 수준의 기능을 먼저 만들고 점점 살을 붙여가는 식으로 진행한다.)
                (실력을 키운다. <-- 이건 뭐.. 필수 불가결한 것이긴 하나.. 시간이 오래걸리니..)
                

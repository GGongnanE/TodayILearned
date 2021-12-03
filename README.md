# TodayILearned_GGNE

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
          

## Git
    - 21.12.02
        : gitHub 기준, private Repository에 밤날 커밋한들, 내 자신 외에 타인이 내가 커밋을 했는지 안했는지 알 수가 없다. 
          내 계정으로는 잔디밭이 추가된것 처럼 보이는데, 로그아웃하고 내 계정을 조회해보니 잔디밭이 없어져있다.. 




## Linux 
    - 21.12.03 
        : 일하던 중 있었던 일이다.. find 명령어에서 symbolic link로 설정한 디렉토리 안의 파일을 찾지 못하는 현상이 있었다. 
          find의 옵션 중 -L 옵션을 주면 심볼릭 링크로 걸려있는 디렉토리 안의 파일을 처리할 수 있었다. 



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

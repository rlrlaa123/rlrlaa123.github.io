---
layout: post
title: Git 사용법 + remote 저장소
image: http://haacked.com/images/icons/Shell.ico
---

오늘 친구에게 Git 사용법을 전수받았다!
면접 볼때도 물어보고 모든 소스들은 모두 깃에 올라와있다. 그래서 언젠간 배워야지 생각하고 있었지만, github 홈페이지에서 tutorial에서 웹 상으로 commit, pull 해보고 이렇게 쉽다니! 하고 넘어갔었다ㅋㅋㅋ(무식한넘...)

서론이 너무 길었다 오늘 익힌 내용을 정리해 보도록 하자.

언제 깔렸는지는 모르겠지만 바탕화면에 있던 git shell 이란 놈을 사용해서 깃에 대해 알아보았다.
[][img/git-tutorial1.PNG]
요렇게 생겼다.

수정된 코드를 내 repository에 업데이트 시키는데에는 다음과 같은 절차가 있다.
> add -> commit -> remote -> push

먼저, 수정된 코드가 있는 디렉토리에 접근하면 이런 식의 텍스트가 보일 것이다.
[][img/git-tutorial2.PNG]
* 첫번째 숫자 +1은 새로운 파일 하나가 추가되었다는 뜻이고,
* 두번째 숫자 ~0은 코드가 수정된 파일의 갯수를 뜻하고,
* 세번째 숫자 -0은 지워진 파일의 숫자를 뜻한다.

이제 _*git status*_ 라는 명령어를 치면 어떤 파일이 변했는지 알 수 있다.

그럼 그 파일을 추적해주자(나는 '가리킨다'라고 이해했다)
[][img/git-tutorial3.png]
코드를 보면 먼저 ad
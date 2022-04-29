# 제대로 파는 Git & GitHub - by 얄코

#### 해당 강의의 개념 메모는 블로그에 올릴예정이므로, 본 글에는 Git 명령어를 정리해 볼 생각이다.
<br>

### 강의링크
- [강의 바로가기](https://www.inflearn.com/course/%EC%A0%9C%EB%8C%80%EB%A1%9C-%ED%8C%8C%EB%8A%94-%EA%B9%83)
<br>


## 강의에서 메모한 Git 명령어들 모음

<details>
<summary>Git Config</summary>
<div markdown="1">       

  - 현재 모든 설정값 보기
      - ```git config (global) —list```
      - j : ↓  ,  k : ↑
  - 전역 이름 설정
      - ```git config --global user.name "이름"```
  - 전역 이름 확인
      - ```git config --global user.name```
  - 전역 이메일 설정
      - ```git config --global user.email "이메일"```
  - 전역 이메일 확인
      - ```git config --global user.email```

#### ```⭐ 전역 설정이 아닌 해당 워크스페이스 설정일 시 --global 을 제외하면 됨```


  - 기본 브랜치명 변경
      - ```git config --global init.defaultBranch main```

  - 줄바꿈 호환 문제 해결 (윈도우: true / 맥: input)
      - ```git config --global core.autocrlf true```
  - pull 기본 전략 선택 (merge or rebase)
      - ```git config pull.rebase false``` → merge 방식
      - ```git config pull.rebase true``` → rebase 방식

  - Git 단축키 설정
      - ```git config --global alias.(지정할 단축키) “명령어”```
      - ex) git config --global alias.cam “commit -am”

</div>
</details>

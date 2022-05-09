# 제대로 파는 Git & GitHub - by 얄코

#### 해당 강의의 개념 메모는 블로그에 올릴예정이므로, 본 글에는 Commit 컨벤션 및 Git 명령어를 정리해 볼 생각이다.


<br>


### 강의링크

- [강의 바로가기](https://www.inflearn.com/course/%EC%A0%9C%EB%8C%80%EB%A1%9C-%ED%8C%8C%EB%8A%94-%EA%B9%83)


<br>


## 커밋 메시지 컨벤션
```
type : subject

body (optional)
...
...
...

footer (optional)
```
- **Type**
  - feat: 새로운 기능 추가
  - fix: 버그 수정
  - docs:	문서 수정
  - style:	공백, 세미콜론 등 스타일 수정
  - refactor:	코드 리팩토링
  - perf:	성능 개선
  - test:	테스트 추가
  - chore:	빌드 과정 또는 보조 기능(문서 생성기능 등) 수정
- **Subject** : 커밋의 작업 내용 간략히 설명
  -  최대 50글자가 넘지 않도록 하고 마침표 생략
  -  영문으로 표기하는 경우 동사(원형)를 가장 앞에 두고 첫 글자는 대문자로 표기
- **Body** : 길게 설명할 필요가 있을 시 작성
  - 어떻게 했는지가 아니라, 무엇을 했는지 또는 왜 했는지를 작성
  - 한줄당 72자 내로 작성
- **Footer**
  -  Breaking Point가 있을 때
  -  특정 이슈에 대한 해결 작업일 때

#### 커밋 컨벤션 예시 (with [gitmoji](https://gitmoji.dev/))
```
✨ 추가 로그인 API (#1)

로그인 API 개발

Ref: #777
```

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

> #### ⭐ 전역 설정이 아닌 해당 워크스페이스 설정일 시 --global 을 제외하면 됨 ⭐


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
  
  - push 시 로컬과 동일한 브랜치명 설정
    - ```git config --global push.default current```

</div>
</details>


<details>
<summary>Local</summary>
<div markdown="1">
  
- 워크스페이스에 git 세팅
    - ```git init```
- stage에 올리기
    - ```git add {파일명}```
- 모든 파일 stage에 올리기
    - ```git add .```
- commit
    - 일반 커밋
        - vi 모드 → 메시지 입력후 종료(:wq!) 시 커밋진행
        - [IntelliJ vi 모드 입력 닫기(esc) 안될 시 설정방법](https://sw-architect.tistory.com/20)
    - 커밋메시지 입력과 동시에 커밋
        - ```git commit -m {”커밋메시지”}```
    - add+commit (untracked 파일이 없을 시)
        - ```git commit -am {“메시지”}```
    - 커밋메시지 변경
      - ```git commit --amend -m 'Add members to Panthers and Pumas'```
- git 상태 확인
    - ```git status```
- git 상태 자세히 확인
    - ```git diff```
    - 터미널 창이 충분하지 않을 경우 읽기모드로 들어감
        
        
        | 작업 | Vi 명령어 | 상세 |
        | --- | --- | --- |
        | 위로 스크롤 | k | git log등에서 내역이 길 때 사용 |
        | 아래로 스크롤 | j | git log등에서 내역이 길 때 사용 |
        | 끄기 | :q | :가 입력되어 있으므로 q만 눌러도 됨|

</div>
</details>


<details>
<summary>Branch</summary>
<div markdown="1">       

 - 브랜치 생성
    - ```git branch {브랜치명}```
- 브랜치 목록 확인
    - ```git branch```
- 브랜치 이동
    - ```git switch {브랜치명}```
    - ```git checkout {브랜치명}```
        - git 2.23 버전부터 checkout이 분리됨
        1. switch
        2. restore
- 브랜치 생성과 동시에 이동
    - ```git switch -c {브랜치명}```
    - ```git checkout -b {브랜치명}```
- 브랜치 삭제
    - ```git branch -d {브랜치명}```
- 브랜치명 변경
    - ```git branch -m {기존 브랜치명} {새 브랜치명}```
- 브랜치 합치기
    - merge
        - ```git merge {합쳐질 브랜치명}```
    - merge 중단
        - ```git merge --abort```
    - rebase
        1. ```git switch {합쳐질 브랜치명}```
        2. ```git rebase {합칠 브랜치명}```
        3. ```git merge {합친 브랜치명}```
        합친 브랜치의 헤드를 merge를 통하여 가지 끝까지로 이동
    - rebase 중단
        - ```git rebase --abort```
    - 충돌 한건 수정 후 stage에 올리고 계속 진행
        - ```git rebase --continue ```
- 로컬에 동일한 이름의 브랜치를 생성, 연결하여 switch
    - ```git switch -t origin/{브랜치명}```
- 원격 브랜치 삭제
    - ```git push {원격이름} --delete {원격의 브랜치명}```
 
</div>
</details>


<details>
<summary>Git Repository</summary>
<div markdown="1">       

- git 원격 저장소 추가
    - ```git remote add origin {원격 저장소 주소}```
- 기본 브랜치명을 main으로 변경
    - ```git branch -M main```
- 원격에 push
    - ```git push -u origin main```
    - -u : 현재 브랜치와 명시된 원격 브랜치를 default로 연결
- 원격 저장소에 commit 내역 밀어올리기
    - ```git push```
- 원격의 commit 내역 당겨오기
    - ```git pull```
- push 할 시 pull 하는 두가지 방법
    - merge 방식
        - ```git pull --no-rebase```
    - rebase 방식
        - ```git pull --rebase```
    - pull이 완료된 후 push 진행
- 로컬의 commit 내역으로 강제 push
    - ```git push --force```
- 원격의 변경사항 업데이트
    - ```git fetch```

</div>
</details>


<details>
<summary>Stash</summary>
<div markdown="1">       

  - 변경사항 보관
    - ```git stash```
  - 변경사항 적용
    - pop : apply + drop
    - ```git stash pop```
  - 변경사항 일부 보관
    - ```git stash -p```
  - 메시지와 함께 보관
    - ```git stash -m '스태시 테스트'```
  - 스태시 목록 보기
    - ```git stash list```

</div>
</details>


<details>
<summary>Change File</summary>
<div markdown="1">       

![img.png](images/git_3space.png)
  
  - Working directory 내의 특정 파일 복구
    - ```git restore {파일명}```
  - Working directory 내 모든 파일 복구
    - ```git restore . ```
  - 변경상태를 스테이지에서 워킹 디렉토리로 돌려놓기
    - Stage -> unStage
    - ```git restore --staged {파일명}```
  - 파일을 특정 커밋 상태로 되돌리기
    - ```git restore --source={헤드 또는 커밋해시} {파일명}```
  
  - Reset
    - Local Repository → Staging area
        - ```git reset --soft```
    - Local Repository → Working directory (default)
        - ```git reset```
        - ```git reset --mixed```
    - 수정사항 완전히 삭제
        - ```git reset --hard```
- Revert
    - default
        - ```git revert {되돌릴 커밋해시}```
    - commit 하지 않고 revert
        - ```git revert --no-commit {되돌릴 커밋해시}```


</div>
</details>

<details>
<summary>Tag & Release</summary>
<div markdown="1">       

**Local**
- 마지막 커밋에 태그 생성
    - `git tag v2.0.0`
- 특정 커밋에 태그 생성
    - `git tag {태그명} {커밋 해시} -m {메시지}`
    - ex) `git tag v2.0.0 -m '자진모리 버전'`
- 태그 삭제
  - `git tag -d {태그명}`
- 태그 목록 보기
  - `git tag`
- 특정 태그 보기
  - `git show {태그명}`
- 원하는 패턴으로 태그목록 보기
    - `git tag -l '{패턴}''`
    - ex) `git tag -l 'v1.*'`

**원격**
- 로컬의 모든 태그 원격으로 올리기
    - `git push --tags`
- 특정 태그 원격에 올리기
    - `git push {원격명} {태그명}`
- 특정 태그 원격에서 삭제
    - `git push --delete {원격명} {태그명}`
    

**릴리즈 버전**
```
📢 릴리즈 버전 유형
    v 2 . 0 . 0
     주   부  수
-----------------------------------------------------
     주 : 기존 버전과 호환되지 않게 API가 바뀔 때
     부 : 기존 버전과 호환되면서 새로운 기능을 추가할 때
     수 : 기존 버전과 호환되면서 버그를 수정할 때 
``` 
**릴리즈 방법**

![img.png](images/git_release.jpg)
1. GitHub에서 태그 목록 이동
2. Create release
3. Title & Describe 작성 후 Publish release
</div>
</details>


<details>
<summary>Branch Deep Dive</summary>
<div markdown="1">       


- 다른 브랜치의 원하는 커밋 **복제**하여 가져오기 (cherry-pick)
    - `git cherry-pick {따올 커밋의 해시}`
- 다른 브랜치에서 파생된 브랜치 **옮겨붙이기** (rebase --onto)
    - `git rebase --onto {옮겨붙일 브랜치} {이동할 브랜치의 파생된 브랜치} {이동할 브랜치}`
- 다른 커밋들을 하나로 묶어 가져오기 (squash)
    - `git merge --squash {대상 브랜치}`
    
--- 
### 3-way merge vs Fast-forword

![img.png](images/fastForword_vs_3wayMerge.jpg)


| 3-way merge | Fast-forward |
| --- | --- |
| 병합되는 모양새 | 하나로 합쳐지는 모양새 (rebase와 비슷) |
| 요약: 가지가 나눠지는 뿌리 + 본 브랜치 + 분기 브랜치 | 요약: 본 브랜치의 헤드를 이동시킨다 |
| 사용 시점: 브랜치를 공유하여 협업하는 상황에서는 무조건 이 방식을 사용, 병합 기록을 남겨야 할 상황에 사용 | 사용 시점: 두 브랜치가 공통 커밋을 조상으로 갖고 있고, 한쪽 브랜치에만 이후 커밋이 있는경우 병합을 위한 다른 커밋이 필요 없을때 사용 |
| 단점: 병합을 위한 다른 커밋이 필요 없는 경우엔 불필요한 커밋 하나가 추가된다. | 단점: 작업 후 어떤 브랜치를 사용한지, 언제 병합했는지 기록이 전혀 남지 않음 |



### Gitflow

![img.png](images/gitflow.png)

| 브랜치 | 용도 |
| --- | --- |
|main|제품 출시/배포|
|develop|다음 출시/배포를 위한 개발 진행|
|release|출시/배포 전 테스트 진행(QA)|
|feature|기능 개발|
|hotfix|긴급한 버그 수정|

</div>
</details>









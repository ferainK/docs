# git
## 1. git 환경 구성
- git 다운로드
- vs code 설정
    ```c
    // 개행 문자 설정 (New line)
    $ git config —global core.autocrlf ture

    // 사용자 정보 설정
    $ git config —global user.name 'Your_Name'
    $ git config —global user.email 'Your_Email'
    ```
    ```c
    // 사용자정보 삭제
    $ git config —unset —global user.name
    ```
    ```c
    // 초기설정 확인
    $ git config —global —list
    ```


## 2. 프로젝트 초기 설정
- `.gitignore 파일` : 버전 관리 제외 대상 지정
1. 새로 시작하기 
    ```c
    $ git init 
    ```
2. git 레포지토리와 연동하기
    ```c
    $ git clone 'github 주소'
    ```
3. git 레포지토레에서 복제한 후 새로 시작하기 
    ```c
    $ npx degit 'github 주소' '신규 폴더명'
    $ git init
    ```

## 3. commit
1. commit 수행
    ```c
    // 변동사항 확인
    $ git status

    // commit 대상 지정
    $ git add '. or 파일명'

    // commit
    $ git commit -m '문구'
    ```
    ```c
    // commit log
    $ git log
    ```
2. commit reset(취소)
    ```c
    // n번째 뛰로 돌아감
    $ git reset —hard HEAD~n
    // reset 취소
    $ git reset —hard ORIG_HEAD
    ```

# github
## 1. github 연동 및 업로드/다운로드
```c
// github 연동 (최초 1회)
$ git remote add origin 'github 주소'

// github 업로드
$ git push origin 'branch name'

// github 다운로드
$ git pull origin 'branch name'
```
## 2. branch 분기
```c
// branch 조회 (a (=all) : github 내 branch도 조회)
$ git branch -a
```
```c
// brach 생성 및 선택
$ git branch -b '신규 branch name'

// branch 생성
$ git branch '신규 branch name'

// branch 제거
$ git branch -d 'branch name'

// branch 선택
$ git checkout 'branch name'
```
```c
// 다른 브렌치 가져오기
$ git checkout -t 'remote branch name'
```
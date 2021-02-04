# git 기초

> 분산버전관리시스템(DVCS)

## git 저장소(repository) 초기화

```
$ git init
Initialized empty Git repository in C:/Users/student/Desktop/md/.git/
(master) $
```

- `.git` 숨김 폴더가 생성되고, bash 환경에서는 `(master)` 로 브랜치 정보가 나타난다.

## 작업 흐름

### 1. `add`

```
$ git add .              # . 현재디렉토리!
$ git add a.txt b.txt    # 특정 파일
$ git add myfolder/      # 특정 폴더
```

현재 작업 중인 파일의 변경사항을 `staging area` 로 변경한다.

- staging area : 커밋(버전)으로 기록할 대상의 파일들의 목록

add 전 상황

```
$ touch 123.txt
$ git status
On branch master

No commits yet
# untracked files - 트래킹이 되고 있지 않는 파일
# 첫번째 통
Untracked files:
  # git add를 사용
  # 커밋이 될 것에 포함시키기 위해서..
  # 두번째 통으로 이동시키려면
  (use "git add <file>..." to include in what will be committed)
        123.txt

nothing added to commit but untracked files present (use "git add" to track)
```

[![add1](../%EC%9D%B4%EB%AF%B8%EC%A7%80/add1-1612416800466.jpg)](https://github.com/edutak/TIL/blob/master/git/md-images/add1-1612416800466.jpg)

- add 후 상황

  ```
  $ git add .
  $ git status
  On branch master
  
  No commits yet
  # 커밋이 될 변경사항들
  Changes to be committed:
    (use "git rm --cached <file>..." to unstage)
          new file:   123.txt
  ```

[![add2](../%EC%9D%B4%EB%AF%B8%EC%A7%80/add2.jpg)](https://github.com/edutak/TIL/blob/master/git/md-images/add2.jpg)

### 2. commit

> 변경사항들을 버전으로 기록

```
$ git commit -m 'First commit'
[master (root-commit) d38cbcd] First commit
 1 file changed, 0 insertions(+), 0 deletions(-)
 create mode 100644 123.txt
```

- 특정시점을 스냅샷처럼 기록한다.
- commit시 메시지는 반드시 잘 작성해야한다.
  - 지금 기록한 코드의 이력을 나타낼 수 있도록

[![commit](../%EC%9D%B4%EB%AF%B8%EC%A7%80/commit.jpg)](https://github.com/edutak/TIL/blob/master/git/md-images/commit.jpg)

## 기타 명령어

### `log`

> 지금까지 기록된 커밋들을 확인할 수 있음

```
$ git log
commit d38cbcdb19140f2ca0d83ba9f59f6cb6cfd02c24 (HEAD -> master)
Author: edutak <edutak.ssafy@gmail.com>
Date:   Thu Feb 4 14:12:49 2021 +0900

    First commit
$ git log --oneline # 한줄로
d38cbcd (HEAD -> master) First commit
$ git log -2     # 최근 2개
$ git log --oneline -1 # 최근 1개를 한줄로
```

### `status`

> git 저장소의 파일 변경 사항등을 확인할 수 있음

```
$ git status
On branch master
nothing to commit, working tree clean
```

[![v1](../%EC%9D%B4%EB%AF%B8%EC%A7%80/v1.jpg)](https://github.com/edutak/TIL/blob/master/git/md-images/v1.jpg)











# 원격저장소 기초 활용

- github을 기준으로 설명하지만, 원격저장소를 제공하는 서비스는 gitlab, bitbucket 등 많다.

## 준비

- github에서 새로운 원격저장소 만들기

## 원격 저장소 설정

```
$ git remote add origin __주소__
```

- git 원격저장소(`remote`)를 추가(`add`)해줘. `origin` 이라는 이름으로 `주소`를

- 원격 저장소 확인을 위해서는 아래의 명령어를 사용한다.

  ```
  $ git remote -v
  # origin은 ~~주소다!
  origin  https://github.com/edutak/first.git (fetch)
  origin  https://github.com/edutak/first.git (push)
  ```

- 원격 저장소 삭제(`rm`)를 하기 위해서는 아래의 명령어를 사용한다.

  ```
  $ git remote rm origin
  ```

## push

```
$ git push origin master
```

- `origin` 으로 지정된 곳에 `master` 브랜치 push
- [![remote](../%EC%9D%B4%EB%AF%B8%EC%A7%80/remote.jpg)](
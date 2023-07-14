## GIT

코드를 관리하는 도구 (버전을 통해)

- 코드 관리도구
- 코드 협업도구
- 코드 배포도구



## **GIT 기초 명령어**

`git [명령어]`

### (1) `git init`

Git으로 코드 관리를 시작

- 코드 관리 단위(기준): 폴더
- `(master)` : ~~현재 브랜치명~~
- `.git` 폴더 생성 : Git이 관리와 관련된 파일



### (2) **`git status`**

현재 상태를 출력(Git에게 현재 상태를 물어봄)

- `git init` 직후,

```bash
On branch master -> master라는 branch 위에 있어요.

No commits yet -> 아직 commit이 없어요.

nothing to commit (create/copy files and use "git add" to track) -> commit 할 것도 없어요.
```

- `test.txt` 파일 생성 후,

```bash
Untracked files:
(use "git add <file>..." to include in what will be committed)
test.txt

-> 추적되지 않은 파일이 있어요.
(파일명)

nothing added to commit but untracked files present (use "git add
-> commit 하기 위해 add된 것이 없어요. 그러나 추적되지 않은 파일은 있어요.
```

* `git add text.txt` 직후,

```bash
Changes to be committed:
(use "git rm --cached <file>..." to unstage)
new file: test.txt
-> commit할 변경들이 있어요.
(파일명)
```

* `git commit` 이후

```bash
nothing to commit, working tree clean
-> commit 할 게 없어요. 작업 폴더는 깔끔해요.
```

* 파일 수정 후,

```bash
On branch master
Changes not staged for commit:
-> commit하기 위해 stage 되지 않은 변경 사항이 있어요.

(use "git add <file>..." to update what will be committed)
(use "git restore <file>..." to discard changes in working directory)
modified: test.txt

no changes added to commit (use "git add" and/or "git commit -a")
```



### (3) `git add [파일명]`

commit 을 위한 stage

- `git add .` : 현재 폴더의 모든 변경 사항 stage



### (4) `git commit -m "커밋 메시지"`

> commit == 버전을 생성 == 현재 상태의 스냅샷 촬영

- 처음으로 commit을 할 경우,

```bash
Author identity unknown 
-> 작자 미상

*** Please tell me who you are. 
-> 당신이 누군지 알려주세요.

Run 
-> 아래의 명령어를 실행해주세요.

  git config --global user.email "you@example.com" [나의 이메일]
  git config --global user.name "Your Name" [나의 이름]

to set your account's default identity.
Omit --global to set the identity only in this repository.

fatal: unable to auto-detect email address (got 'samdd@LAPTOP-9QIPR7K0.(none)')

```

* `gif config` 설정 후 (`vim` 에디터 창),

```bash
# Please enter the commit message for your changes.
-> 변경사항에 대한 commit message를 입렵해주세요.

# Lines starting with '#' will be ignored, and an empty message aborts the
commit.
-> #로 시작하는 라인은 무시됩니다. 아무것도 없는 메시지는 종료됩니다.

# On branch master
#
# Initial commit
#
# Changes to be committed:
# new file: test.txt
```



### (5) `git config`

Git에 관한 설정

- `git config --global user.email "이메일"` : global(전역으로) user의 email을 설정
- `git config --global user.email` : 설정값 확인



### (6) `git log`

현재까지의 commit을 출력

- `git log` 출력화면

```bash
commit 1a7d9384d2f9a064e2ddb4719306defeb51ac3cf (HEAD -> master)
Author: John Kang <hphk.john@gmail.com>
-> 작성자

Date: Tue Mar 16 15:55:10 2021 +0900
-> 날짜

	first commit
	-> 커밋 메시지
```

- `git log --oneline` : 한줄로 출력

```bash
7c7abf0 (HEAD -> master) Add title
1a7d938 first commit
```



### (7) `git remote`

- `git remote` 출력화면

```bash
$ git remote add origin https://github.com/Nayoon-Lee/TIL.git

samdd@LAPTOP-9QIPR7K0 MINGW64 ~/intro (master)
$ git remote -v
origin  https://github.com/Nayoon-Lee/TIL.git (fetch)
origin  https://github.com/Nayoon-Lee/TIL.git (push)
```

- `git remote add [저장소이름] [저장소주소]` : git remote add origin https://github.com/hkeryfonttlxisdrlw/basic_git 
  - git에게 원격저장소(remote) 추가(add)를 명령; 원격 저장소 생성하라는 의미

- 저장소 이름 : `origin`
- 저장소주소: https://github.com/hkeryfonttlxisdrlw/basic_git

- `git remote -v`: verbose의 약자로 '말수가 많은' 이라는 뜻. 뜻만큼 모든 내용을 출력.



### (8) `git push`

- `git push` 출력화면

```bash
$ git push origin master

info: please complete authentication in your browser...
Enumerating objects: 7, done.
Counting objects: 100% (7/7), done.
Delta compression using up to 4 threads
Compressing objects: 100% (3/3), done.
Writing objects: 100% (7/7), 496 bytes | 165.00 KiB/s, done.
Total 7 (delta 0), reused 0 (delta 0), pack-reused 0
To https://github.com/Nayoon-Lee/TIL.git
 * [new branch]      master -> master
```

- `git push`: remote 저장소에 내 컴퓨터의 커밋을 올리기 위한 명령어. 



## 코드 변경 사항 커밋, 원격 저장소로 업로드 하는 명령어

### 9) `git commit` 

* `git commit` 출력 화면

```bash
$ git commit -m "Add a.txt"
-> 현재 버전에 대한 설명으로 커밋 메시지 작성

[master (root-commit) a8f51d7] Add a.txt
 1 file changed, 0 insertions(+), 0 deletions(-)
 create mode 100644 a.txt
```



### 10) `git push`

- `git push` 출력 화면

```bash
$ git push origin master

Enumerating objects: 3, done.
Counting objects: 100% (3/3), done.
Writing objects: 100% (3/3), 209 bytes | 209.00 KiB/s, done.
Total 3 (delta 0), reused 0 (delta 0), pack-reused 0
To https://github.com/Nayoon-Lee/practice.git
 * [new branch]      master -> master
```



**추가 용어 정리**

* `git push origin master`:
  * `origin` : 원격 저장소의 별칭 (첫번째 원격 저장소를 일컫는 말)
    * `origin`이 아닌 다른 이름으로 쓰고 싶다면? : `git remote rename` [origin] [새로운 이름]
  * `master`: 브랜치 이름으로 코드의 개발 흐름을 나타내는 개념. Git 저장소를 생성하면 master 브랜치가 기본적으로 생성. 



## Git 명령어 중간 정리

```bash
$ cd ~ or $ cd .. 
-> 최상단 디렉토리로 이동

$ mkdir practice [디렉토리명]
-> 'practice' 디렉토리 생성

$ cd practice/ 
-> 'practice' 디렉토리로 이동

$ git init
-> Git으로 코드 관리를 시작

$ touch a.txt [파일명]
-> 'a.txt' 파일 생성

$ git add a.txt
-> 'a.txt' staging area 에 추가

$ git commit -m "Add a.txt" [커밋 메시지]
-> 현재 버전에 대한 설명으로 커밋 메시지 작성

$ git remote add origin { url }
-> 원격 저장소로 origin 이름으로 url 추가

# push 하기 전, `git status`, `git log`를 통해 상태를 확인하는 것이 좋음.

$ git push origin master
-> commit 한 이력이 원격 저장소에 저장


# 주의
Git 최상단 디렉토리에 `git init`을 실행하면

- 최상단 디렉토리에 `.git` 이라는 숨김 폴더가 생성.
- 하위 디렉토리에는 `.git`이라는 폴더가 생성되지 않음.

즉, Git은 최상단 디렉토리의 `.git`을 참조하여 버전을 관리하게 됨.



# 앞으로 실습할 때는 특정 디렉토리로 버전을 관리할 때가 있으니, 상단 home에 `git init`을 해서는 안된다! 
```



## 원격 저장소의 코드를 가져오는 명령어

### (10) `git clone`

```
git clone https://github.com/username/repo.git
```

원격 저장소의 모든 파일과 커밋 히스토리가 로컬 디렉토리에 복제됨.

새로운 프로젝트를 시작하거나 다른 개발자의 코드를 협업하기 위해 프로젝트를 가져올 때 사용됨.



### (11) `git pull`

```
git pull origin master
```

원격 저장소의 최신 변경사항을 가져와 로컬 브랜치에 병합. 

`git clone` 을 통해 프로젝트를 복제한 뒤에 `git pull` 명령어를 사용해 최신 변경사항을 가져와 변경된 내용을 업데이트 할 수 있음. 


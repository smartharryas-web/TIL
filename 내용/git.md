# Git

- 깃은 3가지 공간을 관리한다. WD, Staging area, HEAD.
- mainbranch는 동작하는 코드이므로 고치는데 매우 신중해야한다. 보통 다른 branch에서 개발을 끝내고 서비스를 끊기지 않게 한다.
- 분산버전 관리 시스템 = local + cloud. 파편화된 관리를 git 과 github가 담당한다.
- 커밋은 의미있는 변경사항의 단위로 끊어서 제출한다.
- 사용법 표기: `<>` 직접 채워 넣는 값, `[]` 생략 가능, `|` 중 하나 선택
- 파일 오른쪽에 U 표시 없으면 git이 추적안하고 있는거다.



## init
- `.git` 폴더 생성 (사진첩생성)
```
git init
```


## status
- 현재 폴더의 git 작업상태 (파일 상태 추적)
```
git status
```


## log
- git 히스토리 출력 (커밋 이력)
```
git log [--oneline] [<브랜치 | 커밋>]
git log
git log --oneline # 핵심만 출력
```


## add
- staging area에 올리기 (무대에 올리기)
```
git add <파일 | 폴더 | .>
git add <filename>
git add . # 모든 파일/폴더 올리기
```


## remote add
- 원격저장소 주소를 별명(origin)으로 추가, origin아니어도 추가 가능
- git remote add 이후 origin자리에 온라인 레포 URL을 맨날 칠 수 없으니까 origin이란 별명을 넣어준 것이다. 이후 URL을 입력한다.
```
git remote add <별명> <URL>
git remote add origin https://github.com/SESAC-SD4/TIL.git
```


## commit
- `.git` repository에 저장 (사진 찍기)
  - 커밋 메세지 옛날 꺼는 rebase로 변경 
```
git commit [--amend] -m "<메시지>"
git commit -m "message"
git commit --amend -m "fix message" # 마지막 커밋 메세지 수정
```


## push
- 원격 저장소에 업로드
  - 동시에 push 시 pull을 먼저 해야할 수 있음
```
git push [-u] <별명> <브랜치>
git push origin main
```


## restore
- 수정을 취소하기
```
git restore [--staged] <파일 | .>
git restore <filename>
git restore . # 이건 그냥 vscode 변경 사항 저장 안하고 닫는거랑 똑같은 거다.
git restore --staged <filename> # 이건 위에꺼랑 다르게 add 목록에서 제거하는 거다.
```

## reset
- head 위치 옮기기

| 옵션 | HEAD | 스테이징 | VSCode 화면 |
| --- | --- | --- | --- |
| `--soft` | 이동 | 그대로 | 그대로 |
| `--mixed` | 이동 | HEAD에 맞춤 | 그대로 |
| `--hard` | 이동 | HEAD에 맞춤 | **HEAD에 맞춤 (수정 사라짐)** |

|  | `--soft` | `--mixed` |
|---|---|---|
| 취소한 커밋 내용 | 스테이징에 올라간 채로 남음 | 스테이징에서 내려감 (VSCode 화면에만 남음) |
| 바로 다시 커밋하면 | 그대로 커밋됨 | `git add`부터 다시 해야 함 |
| 주 용도 | 합치기, 다시 커밋하기 | 커밋을 여러 개로 **쪼개기** (파일별로 골라서 add) |

- 불가피할 때 혼자할 때만 사용. github처럼 같이 하는 곳에선 새로운 커밋으로 덮어쓰는게 좋다.
```
git reset [--soft | --mixed | --hard] <커밋>
git reset --soft HEAD~3
```

## revert
- github에서 reset을 하면 역사가 꼬인다. 남의 com과 내 com에 있는게 다를 수 있다.
- 그러므로 위에 잘못됐다고 덮어 씌워준다.
```
git revert <커밋>
git revert HEAD  # 마지막 커밋을 되돌리는 새 커밋 생성
```

## switch
- -c 옵션(create) 선택 시 새 브랜치 생성
```
git switch [-c] <브랜치>
```


## branch
- 무수히 많이 만들 수 있다.
  - 보통 개발자들이 브랜치 나누는 방법들이 있다.
```
git branch [<새 브랜치>]
```


## merge
- fast-foward. confilct 발생하지 않은 경우
```
git merge <합칠 브랜치>
```


## clone
- 그대로 가지고 오기
  - clone 시 현재 디렉토리 안에 새 디렉토리를 만들면서 넣는 것에 주의해라
```
git clone <URL> [<폴더명>]
```


## Pull
- 다시 가지고 오기
```
git pull [<별명> <브랜치>]
```

## stash
- WD에 있는 변경사항 .git 폴더 내 임시보관함에 넣어둠. stash pop으로 WD로 다시 불러올 수 있음
  - 보관함은 브랜치마다 따로가 아니라 저장소에 하나. pop은 원래 브랜치로 돌아와서 해야 한다.
  - 새 파일(add 안 한 파일)은 기본으로 안 치워짐 → `-u` 붙이기
```
git stash [push] [-u] [-m "<메시지>"]
# 용례: 작업 중에 main 급한 버그 고치기
git stash -u
git stash pop
```


- 헷갈리는 거
1. restore, reset, revert
2. revert는 HEAD~1이 아니라 HEAD를 덮어쓰고 싶은 것이다. 
3. branch는 HEAD파일이 기록되는 공간이니 커밋을 해야 수정이 된다는 것을 생각하자.
4. 만약 충돌이 낫다면 해당 파일을 편집기로 열어 수정하고 닫으면 된다.
5. reset으로 되살릴 땐 무조건 --hard를 써야 한다.

- 다시 풀 문제 
1. 6번, 11번
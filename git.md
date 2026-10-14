# Git

- Head는 내가 보고 있는 위치이다.

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
git log
git log --oneline # 핵심만 출력
```


## add
- staging area에 올리기 (무대에 올리기)
```
git add <filename>
git add . # 모든 파일/폴더 올리기
```


## remote add
- 원격저장소 주소를 별명(origin)으로 추가, origin아니어도 추가 가능
```
git remote add origin https://github.com/SESAC-SD4/TIL.git
```


## commit
- `.git` repository에 저장 (사진 찍기)
```
git commit -m "message"
git commit --amend -m "fix message" # 마지막 커밋 메세지 수정
```


## push
- 원격 저장소에 업로드
  - 동시에 push 시 
```
git push origin main
```


## restore
- 수정을 취소하기
```
git restore <filename>
git restore . # 이건 그냥 vscode 변경 사항 저장 안하고 닫는거랑 똑같은 거다.
git restore --staged <filename> # 이건 위에꺼랑 다르게 add 목록에서 제거하는 거다.
```

## reset
- head 위치 옮기기
  - soft는 
  - mixed는 
  - hard는 
- 불가피할 때 혼자할 때만 사용. github처럼 같이 하는 곳에선 새로운 커밋으로 덮어쓰는게 좋다.
```
git reset [--soft | --mixed | --hard] <커밋>
```

## revert
- github에서 reset을 하면 역사가 꼬인다. 남의 com과 내 com에 있는게 다를 수 있다.
- 그러므로 위에 잘못됐다고 덮어 씌워준다.
```
git revert
```

## switch
- -c 옵션 선택 시 


## branch
- 무수히 많이 만들 수 있다.
  - 보통 개발자들이 브랜치 나누는 방법들이 있다.


## merge
- fast-foward. confilct 발생하지 않은 경우


## clone
- 그대로 가지고 오기
  - clone 시 현재 디렉토리 안에 새 디렉토리를 만들면서 넣는 것에 주의해라


## Pull
- 다시 가지고 오기
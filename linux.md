# Linux

## 명령어 구조

- 대원칙 : 터미널에서 아무 말이 없으면 대부분 잘 된거다. 오류 메세지가 뜨면 그걸 읽어야 한다.

```
- 종류
명령어 옵션 대상
ex) ls -l notes
brew install --cask iterm2
brewinstall --cask iterm2
```

- 셋 사이는 **띄어쓰기**로 구분합니다.
  - brewinstall --cask iterm2는 컴퓨터가 인식을 못한다.

## 경로

- `~` : 내 홈 폴더 (보통 디폴트값이 있음)
- `.` : 지금 있는 폴더
- `..` : 지금 있는 폴더의 상위 폴더
- `/`로 시작 : 절대 경로 (루트부터 시작한다. C드라이브)
- 나머지 : 상대 경로 (어떤 폴더를 기준점으로 잡는 것)

## 명령어

- pwd : (print working directory)

```
pwd
```

내가 어디에 있는지 확인을 할 줄 알아야 한다.

- ls (list)

```
ls
ls TIL # 특정 폴더의 목록
ls -l # 상세 보기
**ls -a*** # 숨김 파일까지 (.으로 시작하는 파일 혹은 폴더)
ls -la #숨김 + 상세 보기
```

목록 보여줌

- cd (change directory)
  - 파일이나 폴더는 TAP으로 자동완성 사용 권장

```
cd ..
cd ~
cd SD4/TIL
```

탭으로 자동완성을 하는 것으로 습관을 들여야 한다.

- mkdir (make directory)

```
mkdir temp
mkdir -p temp/hi # 중간의 부모 폴더까지 한번에 생성
```

- touch

```

```

- echo

```
echo '안녕하세요'
```

-`>`, `>>`

```
echo 'hello' > test.txt # 새로 만들기
echo 'world' >> text.txt # 덮어 씌우기
```

- 왼쪽의 return 값을 오른쪽의 파일을 만들어 넣은다.

- 확장자는 이 파일에 적합한 프로그램을 운영체제에게 실행하게 하기 위한 것이지 확장자가 없더라도 파일을 만드는데 아무 문제가 없다. 파일은 모두 텍스트일 뿐이다.
- 초기화는 컨트롤 l 또는 clear

- 이동 생성 쓰기 읽기

- 파일 내용 보기
  - cat (전부 출력)
  - head -3 (앞부분 출력 옵션 입력시 그 줄만큼)
  - tail -3 (뒷부분 출력)
  - less (새로운 레이어에 출력)

- cp(copy), mv(move), rm(remove)
  - `rm -r` : 폴더 삭제 (recursive)

grep cd linux.md가 안나온다.

which는 명령어가 어디있는지 출력한다.
--help를 쓰면 거의 대부분 명령어에 대한 설명을 출력한다.

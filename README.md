# 운영체제 Assignment 1

### 이름 : 이준휘

### 학번 : 2018202046

### 교수 : 최상호 교수님

### 강의 시간 : 금 1, 2


## 1. Introduction

```
해당 과제는 다음과 같은 3 개의 소과제로 나눈다. 첫 번째 과제에서는 Linux의 Basic
Command에 대하여 확인하는 과정을 거친다. 그 후 두 번째 과제에서는 Kernel 4.19.67을
Compile하는 과정을 통해 kernel을 어떻게 Compile하는지를 익힌다. 마지막으로 세 번째
과제에서는 Linux agp가 실행되는 지점 탐색을 진행하면서 탐색 방법과 커널 메시지 출
력 방법에 대해 실습한다.
```
## 2. Conclusion & Analysis

### A. Assignment 1- 1

```
해당 사진은 1 - 1 과제를 수행한 모습이다. 우선 username이 os2018202046으로 필자
의 학번에 맞게 생성되었다. 그리고 다음은 과제에서 빈 칸에 맞는 명령을 수행한 결
과다. 우선 1 번으로 assignmet1명의 디렉터리를 생성하기 위해 mkdir명령을 사용하였
다. 그 후 2 번으로 assignment1 디렉터리로 이동하기 위해 cd assignmnent1을 통해
이동 후 “os.txt”파일을 만들기 위해 touch os.txt를 입력하였다. ls를 입력하였을 때 해
당 파일은 정상적으로 생성되었다. 3 번에서는 os.txt를 os_copy.txt명으로 복사하기 위
해 cp os.txt os_copy.txt 명령을 사용하였다. 그 결과 해당 파일명으로 파일이 복사되
었다. 4 번에서는 os_copy.txt의 권한을 모든 대상에게 읽기만 부여하는 것으로 이를 위
해 chmod 444 os_copy.txt를 사용하여 4 (읽기 권한)만 부여하였다. 그 결과 다음 줄에
서 ls -al로 권한을 확인하였을 때 모두 읽기 권한만 존재하는 것을 알 수 있었다. 마
지막으로 5 번에서는 os.txt에 os_학번을 작성 후 터미널에 출력하는 것이다. 우선
```

```
os.txt에 학번을 작성하기 위해 vi os.txt를 사용한다. 그 후 i를 입력하여 insert 모드로
진입 후 os_2018202046을 입력한다. 입력을 마친 후에는 insert모드에서 나오기 위해
esc를 입력하고 :wq를 입력하여 저장 및 vi를 종료한다. 그 후 cat os.txt를 입력하여
os.txt를 출력하였을 때 다음과 같이 정상적으로 출력되는 것을 확인할 수 있다.
```
### B. Assignment 1- 2

```
해당 과제는 우분투 내에서 kernel을 다운로드하고, 컴파일의 모든 과정을 terminal과
vi를 통해 진행한다.
```

우선 Downloads 디렉토리로 이동하여 sudo wget 명령을 통해 linux-4.19.67 커널
을 다운받는다.

다운받은 커널은 tar - Jxvf 명령을 통해 압축을 풀어준다


Kernel의 Extra Version을 수정하기 위해 Makefile를 vim editor로 열어
EXTRAVERSION에 - 2018202046(학번)을 입력한다.

그 후 커널 환경을 설정하기 위해 sudo apt install을 통해 build-essential,


libncurses5-dev, bison, libelf-dev를 설치한다.


(^)
그 다음으로는 Kernel의 환경을 설정한다. sudo make menuconfig를 입력하여 환경
설정으로 들어간다. 크 후 커널 모듈 적재 시 발생할수 있는 문제 해결하고, 컴파
일 시 문제가 될 수 있는 모듈을 제거한다. 마지막으로 이를 .config에 저장한 후
환경설정을 완료한다.
이후 make -j4를 통해 4 개의 thread를 통해 kernel을 컴파일한 후 make


modules_install을 통해 모듈을 설치, 그 후 make install을 통해 컴파일된 kernel을
boot Loader에 등록한다.

그 후 Grub 설정파일에 들어가 Grub 메뉴 숨김 옵션을 false로 설정하고 Grub 메
뉴를 숨기고 기다리는 시간을 0 으로 설정한다.

위의 모든 작업을 완료하고 reboot를 이용하여 재부팅을 하여 Grub 부트로더 선택


#### 메뉴에서 컴파일한 커널을 선택하였을 때 만들어진 커널로 정상적으로 바뀐 것을

#### 확인할 수 있었다.

### C. Assignment 1- 3

```
해당 화면은 cscope -R를 통해 cscope의 DB를 생성하고 cscope를 여는 명령을 수
행한 결과다.
```

Linux agpgart 출력되는 곳을 탐색하기 위해 Find this text string 항목에 해당 text
를 입력하여 파일을 찾았다.

#### 해당 함수의 출력을 정해진 조건과 같이 변경하였으며 현재 해당 파일이

agp_init(void)에 있다는 출력을 추가해준 모습이다.


```
위와 같이 파일을 수정한 후 make – make modules_install - make install – reboot
과정을 통해 module을 컴파일 한 후 reboot를 한 후다. dmesg를 통해 커널 메세
지를 출력할 때 grep을 통해 _os2018202046가 출력되는 부분을 찾을 때 다음과
같이 정상적으로 출력이 나오는 것을 확인할 수 있다. 이를 통해 해당 과제가 정상
적으로 수행되었음을 확인하였다.
```
## 3. Consideration

```
해당 과제를 통해 Linux의 기본 command에 대해 복습하는 시간을 가질 수 있었다. 기본
적인 command와 함께 vim의 사용법과 cscope의 사용법을 알 수 있었다. 또한 커널의
컴파일을 하고 적용하는 과정이 어떻게 진행되는지 공부하고 이를 실제로 구현해볼 수
있는 과제였다. 마지막으로 커널에 message를 출력하는 방법을 배우고, 이를 dmesg 명
령을 통해 확인하며, grep 명령을 통해 특정 부분만을 선별하는 방법을 익힐 수 있었다.
```
## 4. Reference

#### - 강의자료만을 참고



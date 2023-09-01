---
title:  🐧 리눅스 기초편 Bash Shell Script 💡
categories: Linux
tag: [🐧 Linux, 💡 basic]
toc: true
excerpt: false
---
<br>
CLI(Command Line Interface) **기본 명령어**와 그 명령어의 조합으로 만드는 **쉘 스크립트** 강의 정리

강의 : [시스템엔지니어가 알려주는 리눅스 기초편 Bash Shell Script](https://www.inflearn.com/course/%EB%A6%AC%EB%88%85%EC%8A%A4-bash-shellscript)

<br>

# 1. 리눅스와 쉘

## CLI 단축키

### `Tab` : 명령 자동완성

### `Ctrl` + `c` : 실행 중인 프로세스 중단

### `Ctrl` + `a` : 라인 맨 앞으로 커서 이동

### `Ctrl` + `e` : 라인 맨 뒤로 커서 이동

### `Ctrl` + `r` : history 검색

<br><br>

# 2. 리눅스 명령어

## 파일 시스템 관련 명령어

### cd (Change Directory) : 디렉토리 변경

### ls (LiSt) : 현 디렉토리의 파일 목록 출력

### df (Disk Free) : 마운트된 디스크 공간 통계
```
$ df -h    (사람이 보기 편하게 용량 표시)
```
### mkdir (MaKe DIRectory)

### rmdir (ReMove DIRectory)
비어 있는 디렉토리만 삭제 가능

### pwd (Print Working Directory)

### mount : 디스크장치 표시

### stat : 파일통계 출력

<br>

## 파일 관련 명령어

### touch : 빈 파일 생성, 타임스탬프 업데이트

### cat (catenate) : 파일 내용 출력

### head : 지정 라인까지 출력 (기본 10)
```
$ head -n 2 testfile.txt    (위에서 부터 2줄만 출력)
```

### tail : 뒤 부터 지정 라인까지 출력 (기본 10)
```
$ tail -n 2 testfile.txt    (뒤 에서 부터 2줄만 출력)
$ tail -f VWS.access.log    (-f 옵션으로 실시간 로그보기)
```

### cp (CoPy)
```
$ cp -rfp 원본파일패스/이름 복사할파일패스/이름
```
[옵션 `-r` : reculsive(하위디렉토리포함) | `-f` : force (같은이름이 있더라도 덮어씌움) | `-p` : permission]
```
$ cp -rfp  directory1 directory1-1
$ cp -rfp  WORK BACKUP_WORK
```

### mv (MoVe) : 파일이동, 이름변경
```
$ mv BACKUP_WORK WORK_BAK
```

### rename : 파일 이름 변경

```
$ touch test1 test2 test3 test4 test5
$ rename test test0 test?
$ ls
test01 test02 test 03 test04 test05
```

### rm (ReMove) : 파일 삭제
[옵션 `-r` : reculsive(하위디렉토리포함) | `-f` : force (같은이름이 있더라도 덮어씌움)]
```
$ rm -rf 지울폴더    (폴더지울때만 -rf)
$ rm -f test??     (위에 test01 ~ test05 지움)
$ rm -rf WORK_BAK  (폴더지우기)
```
### less : 상하 커서 이동가능한 파일보기
```
$ less testfile.txt
```

### ln (LiNk) : 링크 생성
`-s` 옵션이 없으면 hard link 생성 , `-s` 옵션이 있으면 soft link 생성
```
$ ln aaa.txt hardlink
$ ln -s aaa.txt symboliclink
$ ls -al
-rw-r--r--   2 jay  staff     0B  8 10 17:43 aaa.txt
-rw-r--r--   2 jay  staff     0B  8 10 17:43 hardlink
lrwxr-xr-x   1 jay  staff     7B  8 10 17:45 symboliclink -> aaa.txt
```

### paste : 행을 읽어 탭으로 구분하여 병합
```
$ cat txt1
aaa
bbb
ccc
ddd
$ cat txt2
111
222
333
444
$ cat txt1 txt2
aaa
bbb
ccc
ddd
111
222
333
444
$ paste txt1 txt2
aaa     111
bbb     222
ccc     333
ddd     444
```

### dd (Dataset Dafinition)
블럭 단위로 데이터셋을 정의하여 파일을 쓰고 읽음 (더미파일 생성, 벤치마크 시 많이 사용)
```
$ dd if=인풋파일이름 of=아웃풋파일이름 bs=바이트(크기) count=블럭을복사할횟수
$ dd if=/dev/urandom of=ddtest bs=1024 count=10
$ ls -alh ddtest
-rw-r--r-- 1 root root 10k Sep 27 13:14 ddtest
$ ls -al ddtext
-rw-r--r-- 1 root root 10240 Sep 27 13:14 ddtest
```

### tar (Tape ARchive)
하나의 파일로 만듬 (압축가능)
```
$ tar -cvzf 타프볼파일명 디렉토리명/파일명
$ tar -xvzf 타프볼파일명
...
$ tar -cvzf work.tgz ./WORK  (묶기)
...
$ tar -tf work.tgz  (보기)
...
$ tar -xvzf work.tgz  (풀기)
```

<br>

## 프로세스 관련 명령어

### ps (Process Status)
실행 중인 프로세스에 대한 정보 출력
```
$ ps -ef
...
$ ps aux
...
$ ps auxwwwww
...
```

### pstree (Process Status TREE)

### top : 프로세스 목록 출력 (모니터링)

```
$ top
```

```
Processes: 527 total, 2 running, 525 sleeping, 2227 threads                                                                                                            16:16:12
Load Avg: 1.80, 1.93, 1.95  CPU usage: 1.18% user, 1.7% sys, 97.74% idle    SharedLibs: 629M resident, 126M data, 48M linkedit.
MemRegions: 220238 total, 4726M resident, 607M private, 2092M shared. PhysMem: 14G used (1451M wired, 26M compressor), 906M unused.
VM: 215T vsize, 4283M framework vsize, 0(0) swapins, 0(0) swapouts. Networks: packets: 2214208/3459M in, 1371732/2274M out. Disks: 1558564/14G read, 1311436/31G written.

PID   COMMAND      %CPU TIME     #TH    #WQ  #PORT MEM    PURG   CMPRS PGRP PPID STATE    BOOSTS          %CPU_ME %CPU_OTHRS UID  FAULTS   COW   MSGSENT   MSGRECV   SYSBSD
7741  top          4.3  00:08.64 1/1    0    27    6561K  0B     0B    7741 2823 running  *0[1]           0.00000 0.00000    0    72721+   75    2282593+  1141290+  290671+
7307  Google Chrom 3.2  01:49.99 23     1    209   178M+  144K   0B    667  667  sleeping *0[6]           0.00000 0.00000    501  236164+  693   537030+   261192+   825428+
0     kernel_task  1.9  13:25.94 476/8  0    0     8880K  0B     0B    0    0    running   0[0]           0.00000 0.00000    0    34733    0     52607153+ 40701534+ 0
364   WindowServer 1.7  28:25.43 17     3    1662  425M-  13M-   0B    364  1    sleeping *0[1]           0.00000 0.34674    88   3357668+ 5871  21095625+ 10232547+ 12197800+
1024  Terminal     1.1  03:56.91 8      2    388   161M   39M    0B    1024 1    sleeping *0[3393]        0.00721 0.00000    501  2102432  299   350076+   76630+    3369854+
356   bluetoothd   0.6  01:59.25 12     6    313   11M+   288K   0B    356  1    sleeping *0[1]           0.18483 0.00000    0    15411+   146   449102+   245621+   3547545+
722   Google Chrom 0.3  06:18.30 25     5    248   194M   3584K  0B    667  667  sleeping *1[2]           0.00000 0.00000    501  169888   715   3779548+  5850782+  5013071+
723   Google Chrom 0.2  00:36.74 16     1    112   45M    0B     0B    667  667  sleeping *0[3]           0.00000 0.00000    501  53712    2166  404163+   229273+   1223593+
816   com.apple.Am 0.2  00:31.30 3      1    77    3905K  0B     0B    816  1    sleeping  0[17425]       0.13890 0.00000    0    1512     104   140615+   88581+    570184+
1170  Code Helper  0.1  04:09.60 10     3    156   134M   4352K  0B    1167 1167 sleeping *1[5]           0.00000 0.00000    501  176236   535   2546586   6302625+  4758669+
667   Google Chrom 0.1  03:59.51 45     1    907   221M   464K   0B    667  1    sleeping *0[2116]        0.00000 0.00000    501  397959+  3005  3208782+  1446049+  3357280+
656   sharingd     0.1  00:15.12 4      2    320   11M    0B     0B    656  1    sleeping *0[1]           0.00000 0.10245    501  7824     271   88529+    37576+    330280+
359   corebrightne 0.1  00:35.83 4      3    131   3393K  0B     0B    359  1    sleeping *0[1]           0.20063 0.00000    0    73312+   107   140764+   94791+    889342+
5129  Google Chrom 0.1  01:07.32 21     3    148   66M    0B     0B    5106 5119 sleeping *1[5]           0.00000 0.00000    501  60579    696   482507    2095630+  1583961+
...
```

### nohup (NO HangUPs)
쉘 스크립트 파일을 데몬 형태로 실행   
표준 출력을 지정한 파일로 리다이렉트
```
$ nohup echo "Bash Command"
appending output to nohup.out
...
$ cat nohup.out 
Bash Command
```

### kill : 프로세스 종료
```
$ kill -2 프로세스번호
$ kill -INT 프로세스번호
...
$ kill -15 프로세스번호
$ kill -TERM 프로세스번호
...
$ kill -9 프로세스번호
$ kill -KILL 프로세스번호
```

<br>

## 네트워크 관련 명령어

### ifconfig (InterFace CONFIGration)

네트워크 인터페이스의 활성/비활성화 및 설정

### ip

ip관련 정보 조회 및 설정

###  netstat (NETwork STATistics)

네트워크 프로토콜의 통계와 연결상태를 출력

### ss (Socket Statistics)

네트워크 소켓의 통계와 연결상태를 출력

### iptables

패킷 필터링 도구로 패킷의 출입을 제한하는 방화벽 구성이나 NAT(Network Address Traslation) 구성에 사용

### ufw (Uncomplicated FireWall)

iptables의 제어를 쉽게 하기 위한 도구

### ping 

ICMP 프르토콜의 응답 확인 도구
```
$ ping -c 5 JayuiMacBookAir 
PING jayuimacbookair (192.168.219.107): 56 data bytes
64 bytes from 192.168.219.107: icmp_seq=0 ttl=64 time=0.094 ms
64 bytes from 192.168.219.107: icmp_seq=1 ttl=64 time=0.197 ms
64 bytes from 192.168.219.107: icmp_seq=2 ttl=64 time=0.220 ms
64 bytes from 192.168.219.107: icmp_seq=3 ttl=64 time=0.204 ms
64 bytes from 192.168.219.107: icmp_seq=4 ttl=64 time=0.171 ms

--- jayuimacbookair ping statistics ---
5 packets transmitted, 5 packets received, 0.0% packet loss
round-trip min/avg/max/stddev = 0.094/0.177/0.220/0.045 ms
```

### wget (World wide web + GET)

웹 서버로부터 컨텐츠를 가져오는 도구

```
$ wget https://openresty.org/download/openresty-1.17.8.2.tar.gz
...
```

### curl (Client for URLs)

다양한 프로토콜을 사용하여 데이터를 전송하게 해 주는 도구

```
$ curl -Lkso /dev/null -w "%{http_code}\n" https://gmail.com
200
```

### route

네트워크의 경로 정보(라우팅 테이블)의 출력, 변경하는 도구

<br>

## 검색 / 탐색 관련 명령어

### find

지정한 파일명 또는 정규표현식을 이용하여 파일 검색

```
$ find 옵션 찾기시작할패스 익스프레션
$ find ./ -name test        
.//GitHub_Pages/jay-hong.github.io/test
```

### which

환경변수 PATH에 등록된 디렉토리에 있는 명령어를 찾아주는 도구

쉘 스크립트 작성시 명령어의 전체 경로를 적어야 하는경우 사용

```
$ echo ${PATH}
/Users/jay/anaconda3/bin:/Users/jay/anaconda3/condabin:/Users/jay/.rbenv/shims:appleinternal/bin...
$ which ls
ls: aliased to ls -G
$ which df
/bin/df
$ which ddd
ddd: aliased to ~/Documents
```

### grep (Global / Regular Expression / Print)

텍스트 검색 기능을 가진 도구

파일이나 표준 입력을 검색하여 지정한 정규표현식과 맞는 줄을 출력

```
$ grep 옵션 "찾을문자열" 파일명
$ grep -ir "찾을문자열" 파일(또는패스)
$ grep -ir "error" /var/log/*
...
$ 
```

### history

<br>

## I/O 관련 명령어

### redirection

표준 스트림(stdin, stdout, stderr)을 부등호를 사용하여 지정한 위치로 보낼 수 있는 방향지정 옵션

### echo

문자열을 출력하는 도구

### chmod (CHange MODe)

### chown (CHange the OWNer of a file)

### sudo (SUperuser DO --> Substitude User DO)

### who / w

<br>

## 기타 명령어

### date

현재 날짜와 시간 출력

```
$ date
2023년 8월 13일 일요일 14시 24분 35초 KST
$ date '+%Y-%m-%d %H:%M:%S'
2023-08-13 14:24:27
$ date '+%Y%m%d'  
20230813
```

### seq (SEQuence)

지정 규칙으로 숫자열을 출력하는 도구

```
$ seq 1 5
1
2
3
4
5

$ seq -w 1 10  (가장큰 자리수 맞춤)
01
02
...
09
10

seq -f %02g 1 10
01
02
...
09
10

$ seq -f %03g 1 10
001
002
...
009
010

$ seq -f %13g 1 10  (숫자 앞 13칸 공백)
            1
            2
            ...
            9
           10

```

### more

한 화면씩 지정한 파일의 내용 출력

### watch

지정 명령어를 지정한 시간 마다 재실행하여 출력

### crontab

리눅스의 잡 스케줄러의 내용 출력 편집

```
$ crontab -l
$ crontab -e
$ crontab -r  (* 조심 사용하지 마 * 모두 지워버려)
```

<br>

## 실무에 유용한 명령어 옵션 팁

### ls 활용법

-h : human readable 사람이 읽기 쉽게 용량 표기

-t : 시간 순으로

-r : 역순으로

```
$ ls -alhtr 
```

### watch 간단 모니터링

```
$ watch uptim

Every 2.0s: uptime                                       JayuiMacBookAir: Sun Aug 13 15:05:39 2023

15:05  up  4:05, 3 users, load averages: 1.85 2.15 2.08
```

<br><br>

# 3. 초간단 쉘 스크립트

## 명령어 연속 실행

+ 파이프라인 ( \| )
  - testfile.txt "777" 문자열이 있을 때
```
$ cat testfile.txt| grep 777
777
$ grep 777 testfile.txt
777
```
  - cnet3 서버의 루트 파티션의 용량만을 확인하고 싶다
```
$ ssh cent3 "df -h | grep sda1"
```

+ 세미콜론 ( ; )
  - 독립적으로 명령어 실행

+ AND 조건 ( && )
  - 왼쪽 조건이 참이면 오른쪽 실행

+ OR 조건 ( \|\| )
  - 왼쪽 조건이 거짓이면 오른쪽 실행

## 한 줄 스크립트

```
mkdir tmp;echo tmp > tmp/tmp.txt;cat tmp/tmp.txt
```

<br><br>

# 4. CLI 편집기

## VIM이 대세
입력모드 a, i, o
```
: / 찾을문자열
: ! 명령어  (가능)
: set number
: set nonumber
```

<br><br>

# 5. 간단 쉘 스크립트

helloworld.sh
```
#!/bin/bash
echo "Hello World!?"
TXT="Hello world"
echo "${TXT}"
```

## 조건문 / 반복문

if [ 조건문 ]; then

elif [ 조건문 ]; then

else

if

| 숫자 비교문 |       설 명        | 문자 비교문 |          설 명           | 파일 비교문 |          설 명          |
|:-------:|:-------------------|:-------:|:--------------------------|:-------:|:-----------------------|
| A -eq B | A와 B가 같은가        | A = B  | 문자 A, B가 같은가            | -d file | 파일이 존재하고 디렉토리인가   |
| A -ge B | A가 B보다 크거나 같은가 | A != B | 문자 A, B가 다른가            | -e file | 파일이 존재하는가           |
| A -gt B | A가 B보다 큰가        | A < B  | 문자열 A가 B보다 작은가 (바이트) | -f file | 파일이 존재하고 파일인가      |
| A -le B | A가 B보다 작거나 같은가 | A > B  | 문자열 A가 B 보다 큰가 (바이트)  | -r file | 파일이 존재하고 읽을 수 있는가 |
| A -lt B | A가 B보다 작은가      |  -n A   | A의 문자열 길이가 0보다 큰가    | -s file | 파일이 존재하고 비어있지 않은가 |
| A -ne B | A와 B가 같지 않은가    |  -z A  | A의 문자열의 길이가 0인가       | -w file | 파일이 존재하고 쓰기가 가능한가 |

```
#!/bin/bash
LOAD=$(로드에버리지숫자를가져오는명령)
if [ "${LOAD}" -ge 5 ]; then
  슬랙/텔레그램/메일로 경고메세지를 날리는 명령
else
  echo "NO PROBLEM"
fi
```
```
#!/bin/bash
PID="/run/nginx.pid"
if [ -e "${PID}" ]; then
  kill nginx의pid번호
else
  echo "nginx가 실행중이 아닙니다."
fi
```
```
#!/bin/bash
SVR_NAME=$(hostname)
if [ "${SVR_NAME}" = "cent1" ]; then
  echo "웹 서버입니다"
else
  echo "웹 서버가 아닙니다."
fi
```
&& -a &nbsp; || -o
```
[ 조건1 -a 조건2 -a 조건3 ]
[ 조건1 -o 조건2 -o 조건3 ]
[ 조건1 -a 조건2 -o 조건3 ]
[ -e /var/log/messages -o -f /var/log/messages ]
```

case 변수 in

&nbsp;패턴1)

&nbsp;패턴2)

&nbsp;*)

esac

```
#!/bin/bash
## ./nginx_ctl.sh start       : nginx start
## ./nginx_ctl.sh stop        : nginx stop
## ./nginx_ctl.sh reload      : nginx reload
## ./nginx_ctl.sh configtest  : nginx.config 문법 확인
### ./nginx_ctl.sh a b c
### $1:a , $2:b , $3:c

CMD=$1

case "${CMD}" in
start)
  NGINX를 시작하는 명령;;
stop)
  NGINX를 멈추는 명령;;
reload)
  NGINX를 리로드하는 명령;;
configtest)
  NGINX의 설정파일을 확인하는 명령;;
*)
  echo "사용방법 : ./nginx_ctl.sh {star|stop|reload|configtest}";;
esac
```

for 변수 in 변수에 넣을 데이터<br>
do<br>
&nbsp;&nbsp;명령어<br>
done<br>

```
#!/bin/bash

for SVR in cent1 cent2 cent3
do
  echo "[${SVR}]에 접속합니다.."
  ssh ${SVR} "uptime"
done
```
```
for NUM in $(seq 1 3)
do
  echo "[cent${NUM}]에 접속합니다.."
  ssh cent${NUM} "uptime"
done
```
```
for SVR in $(cat serverlist)
do
  echo "[${SVR}]에 접속합니다.."
  ssh ${SVR} "uptime"
done
```

<br>
while 조건문<br>
do<br>
&nbsp;&nbsp;명령어<br>
done<br>
```
#!/bin/bash

NUM=1
while [ "${NUM}" -le 3 ]
do
  echo "cent${NUM}"
  ssh cent${NUM} "uptime"
  NUM=$(( ${NUM} + 1 ))
done
```
```
while read SVR
do
  echo ${SVR}
done < serverlist
```

## 함수 / 배열

function 함수명 {
  명령어
}

```
#!/bin/bash

function line {
  echo "========================================="
}

line
echo "df 결과입니다."
line
df -h
line
echo "free 결과입니다."
line
free -m
line
```
calc
```
function plus {
  echo "$1 + $2 = "
  echo $[ $1 + $2]
  echo
}

function minus {
  echo "$1 - $2 = "
  echo $[ $1 - $2]
  echo
}

function multi {
  echo "$1 * $2 = "
  echo $[ $1 * $2]
  echo
}

function div {
  echo "$1 / $2 = "
  if [ $2 -eq 0 ]
  then
    echo "0으로 나눌 수 없습니다."
  else
    echo $[ $1 / $2]
  fi
  echo
}
```

user_calc.sh
```
#!/bin/bash

source ./calc

plus 30 40
minus 10 3
multi 11 7
div 2. 0
div 14 2
```

```
$ ./use_calc.sh
30 + 40 = 
70

10 - 3 =
7

11 * 7 =
77

2 / 0 = 
0으로는 나눌 수 없습니다.

14 / 2 = 
7
```
## 리다이렉션의 활용

```
$ ls
txt1 txt2 txt3
$ ls -al txt1 txt2 txt3 txt4 1> ok 2> ng   (0:입력 1:출력 2:에러)
$ cat ok
txt1 txt2 txt3
$ cat ng
ls: cannot access 'txt4': No such file or dirrectory
```

systeminfo.sh
```
#!/bin/bash

# report 파일 생성
touch report
# report 파일 초기화
cp -f /dev/null report

# df -h >> report
# pstree >> report
# free -m >> report
# uptime >> report

{
  echo "====== df -h ======"
  echo
  df -h
  echo "====== pstree ======"
  echo
  pstree
  echo "====== free -m ======"
  echo
  free -m
  echo "====== uptime ======"
  echo
  uptime
  echo
}>> report

# 위 결과 이메일 발송
cat report | mail -s "[report] cent1 system info" hjpyooo@naver.com
```

## 대화식 구성 / 메뉴 구성

read_test.sh
```
#!/bin/bash

#read -sp "화면에표시할문자" 변수이름  (s는 secret모드)
read -p "아무문자나 입력 해 주세요 : " ANY

echo ${ANY}
```
숫자 맞추기 게임
```
#!/bin/bash

GOAL=$(($RANDOM% 100+1))
CNT=0

while true
do
  read -p "1~100 사이의 숫자를 입력해주세요 : " NUM
  CNT=$((${CNT} + 1))

  if [ ${NUM} -gt ${GOAL} ]
  then
    echo "입력한 숫자가 더 큽니다."
  elif [ ${NUM} -lt ${GOAL} ]
  then
    echo "입력한 숫자가 더 작습니다."
  elif [ ${NUM} -eq ${GOAL} ]
  then
    echo "축하합니다!! 정답!! - ${CNT}번 시도"
    exit 0
  fi

done
```

<br><br>

# 6. 고급 명령어

SED

AWK

<br><br>

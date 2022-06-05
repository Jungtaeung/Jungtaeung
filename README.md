# top
1) 시스템의 상태를 전반적으로 가장 빠르게 파악 가능하다.(CPU, Memory, Process)
2) 옵션 없이 입력하면 interval 간격(기본 3초)으로 화면을 갱신하며 정보를 보여준다.
3) **top -b -n 1**
![image](https://t1.daumcdn.net/cfile/tistory/993AF2335985C5DE2C)

# top 실행 전 옵션
1) 순간의 정보를 확인하려면 '-b' 옵션 추가 한다.(batch 모드)
2) top 실행 주기 설정(반복 횟수)을 하려면 '-n' 입력한다.

# top 실행 후 명령어
1) shift + p : CPU 사용률 내림차순
2) shift + m : 메모리 사용률 내림차순
3) shift + t : 프로세스가 돌아가고 있는 시간 순
4) k : kill. k 입력 후 PID 번호 작성. signal은 9
5) f : sort field 선택 화면 -> q 누르면 RES순으로 정렬
6) a : 메모리 사용량에 따라 정렬
7) b : Batch 모드로 작동
8) 1 : CPU Core별로 사용량 보여줌

# ps와 top의 차이점
1) ps는 ps한 시점에 proc에서 검색한 cpu 사용량이다.
2) top은 proc에서 일정 주기로 합산해 cpu 사용율 출력한다.

---
# ps
1) 현재 실행중인 프로세스의 목록과 상태를 보는 명령어이다.
2) 전통적인 유닉스인 System V, BSD, GNU에 따라 결과가 다르게 나타나고 표기법에도 차이를 보인다.(옵션 사용 시 System V 계열은 대시를 사용하고 BSD계열은 대시를 사용하지 않는다.)
3) 원하는 프로세스의 상태를 출력하려면 **정확한 옵션 사용**이 중요하다.
4) ps의 사용법은 "$ ps [option]"이다.
![image](https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=http%3A%2F%2Fcfile5.uf.tistory.com%2Fimage%2F996A90395BC6ECFD11AC3A)

# ps 항목
|항목|의미|
|---|:---:|
|USER|BSD 계열에서 나타나는 항목으로 프로세스 소유자의 이름|
|UID|SYSTEM V 계열에서 나타나는 항목으로 프로세스 소유자의 이름|
|PID|프로세스의 식별 번호|
|PPID|부모 프로세스 ID|
|%CPU|CPU 사용 비율의 추정치(BSD)|
|%MEM|메모리의 사용 비율의 추정치(BSD)|
|VSZ|K단위 또는 페이지 단위의 가상 메모리 사용량|
|RSS|실제 메모리 사용량(Resident Set Size)|
|TTY|프로세스와 연결된 터미널|
|S, STAT|현재 프로세스의 상태 코드(S: Sys V, STAT: BSD)|
|TIME|총 CPU 사용 시간|
|COMMAND|프로세스의 실행 명령행|
|STIME|프로세스가 시작된 시간 혹은 날짜|
|C, CP|짧은 기간 동안의 CPU 사용률(C: Sys V, CP: BSD)|
|F|프로세스의 플래그|
|PRI|실제 실행 우선순위|
|NI|nice 우선순위 번호|

# ps와 top의 차이점
1) ps는 ps한 시점에 proc에서 검색한 cpu 사용량이다.
2) top은 proc에서 일정 주기로 합산해 cpu 사용율 출력한다.

---
# jobs
1) 작업의 상태를 표시하는 명령어이다.
2) 현재 쉘 세션에서 실행시킨 백그라운드 작업의 목록이 출력된다
3) 각 작업에 번호가 붙어 있어 kill 명령어 뒤에 '%번호'등으로 사용할 수 있다.
![image](https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2FbtYqnv%2FbtqTIpUtoEN%2FkStUPnVZdWqdeKYmBF52w1%2Fimg.png)

# jobs로 출력되는 백그라운드 작업의 상태값
|상태|설명|
|---|---|
|Running|작업이 계속 진행중임|
|Done|작업이 완료되어 0을 반환|
|Done(code)|작업이 종료되었으며 0이 아닌 코드를 반환|
|Stopped|작업이 일시 중단|
|Stopped(SIGTSTP)|SIGTSTP 시그널이 작업을 일시 중단|
|Stopped(SIGSTOP)|SIGSTOP 시그널이 작업을 일시 중단|
|Stopped(SIGTTIN)|SIGTTIN 시그널이 작업을 일시 중단|
|Stopped(SIGTTOU)|SIGTTOU 시그널이 작업을 일시 중단|

# 옵션
|옵션|설명|
|---|---|
|-l|프로세스 그룹 ID를 state 필드 앞에 출력|
|-n|프로세스 그룹 중에 대표 프로세스 ID를 출력|
|-p|각 프로세스 ID에 대한 한 행씩 출력|
|command|지정한 명령어를 실행|

---
# kill
1) 프로세스에 특정한 signal을 보내는 명령어이다.
2) 일반적으로 종료되지 않는 프로세스를 종료 시킬 때 많이 사용한다.
3) **$ kill -l**명령어를 이용해 사용할 수 있는 시그널을 확인할 수 있다.
4) 프로세스를 안전하게 종료하기 위해서는 "kill -9 pid", "kill -SIGKILL pid" 형태로 프로세스 강제 종료를 권장하지 않는다. (데이터 유실 위험)
5) 일반적으로 해당 Process에 문제가 있어서 다시 시작하고자 할 때에는 SIGHUP, SIGTERM, SIGKILL의 순서로 시도해본다.
6) kill 명령어는 내부적으로 kill()이란 시스템 콜을 사용하여 구현하고, 프로세스 식별자(PID)로 지시한 프로세스와 프로세스 그룹 식별자(PGID)로 지시한 프로세스 그룹에 시그널을 보낸다.
![image](https://t1.daumcdn.net/cfile/tistory/99E84B455C6378A109)

# 시그널
1) 특정 이벤트가 발생했을 때 프로세스에게 전달하는 신호이다.
2) 리눅스에서 프로세스끼리 통신할 때 사용한다.
3) 시그널 이벤트로는 HW 예외, SW 상태, 사용자 입력, 시스템 콜(kill) 등이 있다.
> ## 옵션
|옵션|내용|
|---|---|
|Ctrl+c|실행중인 프로세스에 SIGINT 신호를 보낸다.(프로세스 종료)|
|Ctrl+z|실행중인 프로세스에 SIGITSTP 신호를 보낸다.(프로세스 정지)|
|Ctrl+\||실행중인 프로세스에 SIGINT 신호를 보낸다.(프로세스 종료 + 코어 덤프)|

---
# vim 에디터에서 매크로 활용방법
1) q + a : a키에 recording 시작
2) 반복을 위한 내가 원하는 동작
3) q : recording 종료
4) @a : 1회 실행(ex: 10@a는 매크로 10회 실행)
5) @@ : 방금 실행한 매크로 실행
> ## 자주 사용하는 매크로 등록 방법
1) **~/.vimrc** 를 연다.
2) let @a = '매크로 문자열' 

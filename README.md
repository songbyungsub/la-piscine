# 42seoul
## (Shell script)

mkfile - 파일 생성

chmod - 파일권한 명령법

ls - 현재 디렉토리 내의 모든 파일 나열

git add - add 저장

git commit - 커밋

git push - 업로드

other - 숨겨진 파일들 찾기

ignored =  무시하는 파일을 찾기

exclude-standard =  출력 옵션

find - 파일이나 디렉토리 찾기

환경변수 설정

특정 사용자에 대해서만 정의된 환경 변수로 로컬 터미널 세션 또는 원격 로그인 세션을 사용하여 로그인할 때마다 로드됨.
c언어에서의 변수선언은 나중에 실행했을때 프로세스에 영향을 주지만 환경변수는 컴퓨터 동작 자체에 영향을 주는 변수선언을 하는것.

printenv 를 통해 환경변수가 제대로 설정되었는지 확인.

find - 현재 디렉토리와 그 하위 디렉토리들에서 파일을 검색

basename - 파일명만 추출하기

wc - 라인 갯수 표시

sed - 다중편집 

ifconfig - 모든 네트워크 인터페이스 구성 확인

grep - 파일의 내용에서 특정 문자열을 찾기

ether - 인터페이스 MAC 주소

awk - 특정 번째 행의 문자열을 출력

rev - 거꾸로 반전하여 출력

tr - 치환 명령어

bc - 연산 언어

---
## (c)

 **strcmp() - 스트링 `비교`**
- 두 문자열이 `같은지 비교`할 수 있으며, 함수 이름은 `string compare`에서 유래 되었다.
- 함수는 `\0`로 끝나는 `문자열`에서 작동한다.
- 함수에 대한 스트링 인수는 스트링 끝을 나타내는 `널 문자(\0)`를 포함해야 한다.
- `확장`된 아스키코드를 받을 때에는 return값에 `unsigned char`를 지정해준다.
- null값을 지정해주는 이유- 문자열의 끝을 지정해주지 않으면 뒤에 있는 `메모리 상의 주소`도 비교를 한다.

**strcat() - 스트링 `연결`**
- strcat() 함수는 string2를 string1에 연결하고 널 문자로 결과 스트링을 종료.
- 함수에 대한 스트링 인수는 스트링 끝을 나타내는 널 문자(\0)를 포함해야 한다.
- 길이 검사는 수행하지 않는다.
- return 값: 연결된 스트링에 대한 `포인터를 리턴`한다.

 **strstr() - 스트링 `확인`**
- `Strcmp` 함수는 문자열과 문자열이 동일한지 `비교`하는 함수이지만, `strstr` 함수는 어떤 문자열에 특정 문자열이 포함되어 있는지 `확인`할 때 사용한다.
- 포인터 `str`이 가리키는 문자열에서 포인터 `strSearch`가 가리키는 문자열이 포함되어 있는지를 찾는 함수.
- strsearch가 가리키는 문자열을 찾은 경우 str이 가리키는 문자열에서 `찾은 주소를 반환`한다.

 **strlcat함수 - `소스`(src)를 `문자열`(dst)에 붙여 원하는 `길이`(len)를 만드는 함수.**
- 이 함수는 strcat 함수와 동일하다. `보안 목적`을 위해 strcat 대신 사용할 목적으로 만들어졌다.
- dst의 기존 데이터에 src 데이터를 `size 만큼` 붙여 넣는다.
- size = dst 길이 + 붙일 데이터 길이 + NULL 값을 넣어야 한다.
- dst 길이보다 작으면 src 데이터가 넣어지진 않는다.

---
**atoi() 함수의 원리**
매개변수로 들어온 문자열을 앞에서 부터 읽어서, "공백" or "숫자가아닌문자" 가 올때까지 숫자로 변환을 해주는 원리이다.

---
<aside>
💡 main 함수의 매개변수

C에서 main 함수는 프로그램의 진입점이다. 즉 최초로 함수로 구동 되어 실행되는 시점이다. 함수의 매개변수(파라미터, 전달인자)는 이 함수를 호출할때전달해주는 정보를 뜻한다. 보통 함수를 만들어놓고 호출할때 바로 매개변수에 정보를 넣어준다.  하지만 argc, argv를 사용하면 main에 정보를 바로 전달 해줄 수 있다.

⭕ 매개 변수의 구성

(1)int argc

- 메인함수에 전달되는 정보의 갯수를 의미한다.
- 인자를 하나도 입력하지 않으면 argc는 1이 된다. 즉 항상 argc > 1 이 된다.
- 인자의 정확한 개수는 argc - 1 (파일명이 0번이기 때문에)

(2)char **argv

- 메인함수에 전달되는 실질적인 정보로, 문자열의 배열을 의미한다. 첫번째 문자열은 프로그램의 실행경로로 항상 고정이 되어 있다.
- argv[0]은 실행 파일명이 저장
- argv[1], argv[2], ... 순서대로 사용자가 입력한 argument가 저장된다.
</aside>

---
<aside>
💡  동적 할당(malloc)

1) 동적 할당은 컴퓨터 프로그래밍에서 실행 시간 동안 `사용할 메모리 공간을 할당`하는 것을 이야기한다. 사용이 끝나면 운영체제가 쓸 수 있도록 반납하고 다음에 요구가 온다면 다시 할당을 받을 수 있다. 이것은 실행하는 순간 프로그램이 사용할 메모리의 크기를 고려하여 메모리의 할당이 이루어지는 `정적 메모리 할당`과는 `대조적`이다.

2) 또한 실행 시간에 크기가 결정되는 `동적 배열` 및 `리스트`와 같은 경우는 힙을 사용하는 것이 보다 공간을 효율적으로 활용할 수 있으나 C언어의 경우 사용한 공간을 명시적으로 반환해주어야 하므로 이 과정을 생략하게 된다면 `메모리 누수`의 원인이 되기도 한다.

- 동적 할당의 장점

상황에 따라 `원하는 크기` 만큼의 메모리가 할당되고 이미 할당된 메모리라도 언제든 크기 `조정` 가능

- 동적 할당의 단점

더 이상 사용하지 않을 때 명시적으로 `메모리를 해제`해 주어야 한다.

</aside>

<aside>
💡 `free 함수`는 동적으로 할당한 `메모리를 해제`하는 함수이다.

동적으로 할당한 메모리는 `부분적`으로 해제할 수 없다.

따라서 프로그램에서는 동적으로 할당한 메모리 주소를 기억해 두었다가 더 이상 사용하지 않을 때 `free 함수`로 `해제`한다.

필요하지 않은 메모리를 계속 점유하고 있는 현상을 ‘`메모리 누수`’ 라고 한다.

참고로 자바의 경우 사용하지 않은 메모리를 알아서 해제해주는 `garbage collector` 기능이 있지만 c와 c++ 은 없다.

 ---
</aside>

- **#define**

#define란 값을 `치환`해 주는 것이다. 예를 들어 절대 안 변하는 파이값 PI=3.14라고 하였을 코드내에서 int PI=3.14라고 해놨다면, 사용자가 실수로 PI=300 이런식으로 할 수 있는데, 이런것을 방지 해준다. 또한 `공통의 값`이 들어갈때 `#define`을 사용할 수 있다.

#ifndef는 'if not define' = '만약 `정의되어 있지 않다면`' 이란 뜻이다.

#endif = header 파일의 `중복`을 막는다. 해당 구조체가 `재선언` 되지 않고 헤더파일의 `중복선언`을 막기 위해서 사용한다.

- **전처리기**

어떤 한 프로그램을 만들어야 할 때, 우리는 `소스`를 짜고, `컴파일`을 한후, `링크`를 하게 된다. 이 전처리기(Preprocessor)는 소스를 짠 뒤에 컴파일 하기 직전에 처리하는 `컴파일러`의 한 부분이다. 전처리기가 하는 일은 #define처럼 `치환`의 역할을 하기도 하고, `디버깅`에도 도움을 주며 헤더파일의 중복 포함도 방지해주는 기능을 한다. 전처리기에서는 몇가지 `지시자`들을 처리하게 된다. 이 지시자들은 `'#'`라는 기호로 시작하며, #include, #define등에서 흔히 찾아 볼 수 있다.

<aside>
💡 **구조체 선언**

typedef struct 구조체이름 (

자료형 멤버 이름

} 구조체별칭;

- '구조체'란 `여러 자료형`을 가진 변수들을 하나로 묶어 `자료형`으로 사용할 수 있도록 정의하는 것을 말한다.
- 접근 연산자(직접접근, 간접접근)
</aside>

<aside>
💡 AR
`아카이버`(archiver), 간단히 `ar`은 여러 파일 그룹을 하나의 `압축 파일`로 관리하는 유닉스 유틸리티이다. 오늘날 ar은 일반적으로 링크 편집기나 링커가 사용하는 `정적 라이브러리` 파일들을 만들고 갱신하기 위해 사용된다.


r : 새로운 `오브젝트` 파일이면 추가, 기존 파일이면 `치환`.

c : 아카이브(라이브러리 파일) 생성, 존재하지 않는 아카이브를 작성(또는 갱신)하는 경우에도 경고 메시지를 출력하지 않음.

</aside>

---
1️⃣ ****Makefile 이란?

- `linux`에서 반복 적으로 발생하는 컴파일을 쉽게 하기위해 사용하는 make 프로그램의 설정 내용이 적힌 `기술 파일`이다.
- make를 이용하면 반복적 명령의 `자동화`로 시간절약 및 실수 `최소화`할 수 있고, 프로그램 관리가 용이하다는 장점이 있다.

2️⃣ Makefile 매크로 작성

- Makefile의 매크로 설정은 함수에서의 `상수 선언`과 `비슷한 개념`이다.
- 반드시 필요한 것은 아니지만 기존 매크로의 기능과 같이 `가독성`이 좋아지고 수정이 편리해진다는 장점이 있다.
- =기호로 `매크로`를 설정할 수 있다.
- <NAME>: 관습적으로 최종적으로 만들 `라이브러리의 이름`을 NAME으로 지정해두어 가장 윗줄에 작성해 준다.

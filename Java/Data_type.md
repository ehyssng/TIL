# 데이터 타입
> 데이터 타입은 조금 어렵다. 후속 수업에서 필수적인 선행지식은 아니지만, 또 뒤에 배치하는 것도 애매하다. 이번 토픽의 학습이 어렵게 느껴지면 다음 토픽으로 넘어가고 나중에 다시 학습하면 된다.

데이터 타입에 대해서 자세히 알아보기 전에 데이터의 크기에 대해서 학습하자.
## 데이터의 크기
|||
|---|---|
| 8 bit (비트) | 1 byte |
| 1024 byte (바이트) | 	1 kilobyte |
| 1024 kilobyte (킬로바이트) | 1 megabyte |
| 1024 megabyte (메가바이트) | 1 gigabyte |
| 1024 gigabyte (기가바이트) | 1 terabyte |
| 1024 terabyte (테라바이트) | 1 petabyte |
| 1024 petabyte (페타바이트) | 1 exabyte |
| 1024 exabyte (엑사바이트) | 1 zettabyte |

위 의 표에서 볼 수 있듯이 컴퓨터에 저장되는 정보의 가장 작은 단위는 bit다. 컴퓨터를 0과 1로 이루어졌다는 말을 들어본 적이 있을 것이다. 바로 이 0과 1이 bit다. 1bit는 0이나 1의 값을 가질 수 있다. byte는 bit 보다 8배 큰 단위다. 1byte는 8비트다. 여기까지 지금 기억해야 할 내용이다. 그 외의 내용은 차차 알게 된다. 

## 정수형
| 데이터 타입 | 메모리의 크기 | 표현 가능 범위 |
|---|---|---|
| byte | 1 byte | -128 ~ 127 |
| short | 2 byte | -32,768 ~ 32,767 |
| int | 4 byte | -2,147,483,648~2,147,483,647 |
| long | 8 byte | -9,223,372,036,854,775,808 ~ 9,223,372,036,854,775,807 |

위의 표는 정수에 해당하는 데이터 타입의 리스트다.
> int가 가장 처리속도도 빠르고, 충분히 큰 수를 표현할 수 있기 때문에 정수형 데이터 타입을 쓸 때에는 int를 쓰는 것이 좋다.

아래와 같이 int를 데이터 타입으로 변수를 생성하면 어떻게 되는지를 생각해보자.
``` java
byte a;
```
이 변수에 담을 수 있는 숫자의 범위는 -128~127까지다. 이 범위 밖의 수인 -129나 128을 변수에 대입하려고 하면 오류가 발생할 것이다. 그럼 매우 큰 표현범위를 가지고 있는 long형을 사용하지 왜 byte 형을 사용할까? 만약 표현하고자 하는 수가 많아봐야 100을 넘지 않는 경우가 있다고 생각해보자.

행정구역을 숫자로 표시한다고 가정해보자.
| | |
|---|---|
| 1 | 경기도 |
| 2 | 전라도 |
| 3 | 충청도 |
| 4 | 경상도 |
| 5 | 제주도 |
| 6 | 강원도 |

코드로는 아래와 같이 나타낼 것이다.
``` java
byte district = 1; //경기도
```
도처럼 그 수가 사실상 정해져있고, 늘어나도 100을 넘을 가능성이 없는 정보의 경우 byte로 표현하면 1byte의 크기만을 사용하게 된다. 하지만 아래와 같이 long을 사용한다면 8배나 많은 메모리를 사용하게 된다.
``` java
long district = 1;
```
반면에 국가별 인구의 수를 변수에 담으려고 하는데 byte형을 사용한다면 byte 형의 최대 한계인 127을 초과해서 오류가 발생할 것이다.
``` java
byte population = 50000000;
```
조금 다른 관점에서 생각해보자. 

아래의 변수 a와 변수 b는 둘 다 똑같이 8byte의 메모리를 사용하게 된다. 데이터 타입이 같기 때문이다.
``` java
long a = 2147483647;
long b = 1;
```
반대로 아래의 변수 a와 변수 b는 똑같은 수를 저장하고 있지만, 변수 b가 2배의 메모리를 사용한다. 데이터 타입이 다르기 때문이다.
``` java
int a = 2147483647;
long b = 2147483647;
```
즉 어떤 숫자를 저장하느냐에 따라서 사용하는 메모리의 크기가 달라지는 것이 아니고, 어떤 데이터 타입으로 변수를 선언했느냐에 따라서 사용하는 메모리의 크기가 달라지는 것이다. 결국, 변수에 들어올 수 있는 숫자의 최대 크기를 잘 판단해서 데이터 타입을 지정해야 귀한 메모리의 용량을 아낄 수 있다. 하지만 오늘날은 메모리의 용량이 늘어났고, 또 어떤 데이터형을 사용할 것이냐는 문제를 판단하기 위해서는 여러 가지가 고려되어야 한다. <u>결과적으로 말해서 정수를 저장할 때는 int를 사용하면 된다.</u> int 형을 처리 할 때 CPU의 처리속도가 빠르고, int는 충분히 큰 수를 표현할 수 있는 데이터 타입이기 때문이다.

## 실수형
| | | |
|---|---|---|
| float | 4byte | ±(1.40129846432481707e-45 ~ 3.40282346638528860e+38) |
| double | 8byte | ±(4.94065645841246544e-324d ~ 1.79769313486231570e+308d) |

실수형은 float과 double이 있다. 실수를 사용할 때는 double을 사용하도록 하자.

## 문자
| | | |
|---|---|---|
| char | 2byte | 모든 유니코드 문자 |

자바에서는 문자와 문자열이 다르다. 문자(character)는 글자 하나를 의미하고, 문자열은 글자들의 집합을 의미한다. 그럼 문자열은 메모리를 얼마나 사용할까? 문자열은 문자의 집합이라고 했다. 문자는 char 형이고, char는 2byte의 메모리를 사용한다. 따라서 6글자를 담고 있는 String 타입의 변수는 12바이트의 공간을 차지하게 된다. 자세한 내용은 [String 클래스의 문자열 길이의 한계](https://javacan.tistory.com/43)를 참고하자.
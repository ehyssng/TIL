# 3. 자바로 프로그램 작성하기

</br>

## 3.1 Hello.java

자바로 프로그램을 개발하려면 JDK 이외에도 편집기가 필요하다. 메모장과 같은 간단한 편집기도 있지만, 이클립스(eclipse)나 인텔리제이(IntelliJ)와 같이 다양하고 편리한 기능을 겸비한 고급 개발도구를 사용하는 것이 좋다.

``` java
class Hello {
    public static void main(String[] args) {
        System.out.println("Hello, World.");    // 화면에 글자를 출력한다.
    }
}
```

위의 예제는 화면에 `Hello, World.`를 출력하는 아주 간단한 프로그램이다.

작성한 다음 'Hello.java'로 저장하자. 이때, 클래스의 이름 `Hello`가 대소문자까지 정확히 같아야 한다.

이 예제를 실행하려면, 먼저 자바컴파일러(javac.exe)를 사용해서 소스 파일(Hello.java)로부터 클래스 파일(Hello.class)을 생성해야 한다. 그다음에 자바 인터프리터(java.exe)로 실행한다.

![process](https://ifh.cc/g/8dZoG7.png)

자바에서 모든 코드는 반드시 클래스 안에 존재해야 하며, 서로 관련된 코드들을 그룹으로 나누어 별도의 클래스를 구성하게 된다. 그리고 이 클래스들이 모여 하나의 Java 애플리케이션을 이룬다.

클래스를 작성하는 방법은 간단하다. 키워드 `class` 다음에 클래스의 이름을 적고, 클래스의 시작과 끝을 의미하는 괄호{} 안에 원하는 코드를 넣으면 된다.

``` java
class 클래스이름 {
    /*
        주석을 제외한 모든 코드는 클래스의 블록{} 내에 작성해야 한다.
    */
}
```

> `package`문과 `import`문은 예외적으로 클래스의 밖에 작성한다.

아래 코드의 `public static void main(String[] args)`은 `main` 메소드의 선언부인데, 프로그램을 실행할 때 'java.exe'에 의해 호출될 수 있도록 미리 약속된 부분이므로 항상 똑같이 적어주어야 한다.

``` java
class 클래스이름 {
    public static void main(String[] args) {    // main 메소드의 선언부
        // 실행될 문장들을 적는다.
    }
}
```

`main` 메소드의 선언부 다음에 나오는 괄호{}는 메소드의 시작과 끝을 의미하며, 이 괄호 사이에 작업할 내용을 작성해 넣으면 된다. Java 애플리케이션은 `main` 메소드의 호출로 시작해서 `main` 메소드의 첫 문장부터 마지막 문장까지 수행을 마치면 종료된다.

모든 클래스가 `main` 메소드를 가지고 있어야 하는 것은 아니지만, 하나의 Java 애플리케이션에는 `main` 메소드를 포함한 클래스가 반드시 하나는 있어야 한다. `main` 메소드는 Java 애플리케이션의 시작점이므로 `main` 메소드 없이는 Java 애플리케이션은 실행될 수 없기 때문이다. 작성된 Java 애플리케이션을 실행할 때는 'java.exe' 다음에 `main` 메소드를 포함한 클래스 이름을 적어줘야 한다.

하나의 소스 파일에 하나의 클래스만을 정의하는 것이 보통이지만, 하나의 소스 파일에 둘 이상의 클래스를 정의하는 것도 가능하다. 이때 주의해야 할 점은 '소스 파일의 이름은 `public class`의 이름과 일치해야 한다.'는 것이다. 만일 소스 파일 내에 `public class`가 없다면, 소스 파일의 이름은 소스 파일 내의 어떤 클래스의 이름으로 해도 상관없다.

![올바른 작성 예](https://ifh.cc/g/5yL0XW.png)

![잘못된 작성 예](https://ifh.cc/g/dmf7Ka.png)

소스 파일(\*.java)과 달리 클래스 파일(\*.class)은 클래스마다 하나씩 만들어지므로 '올바른 작성 예'에 제시된 'Hello2.java'를 컴파일하면 'Hello2.class'와 'Hello3.class' 모두 두 개의 클래스 파일이 생성된다.

</br>

## 3.2 자주 발생하는 에러와 해결 방법

자주 발생하는 기본적인 에러와 해결 방법을 간단히 정리하였다.

### 1. cannot find symbol 또는 cannot resolve symbol

지정된 변수나 메소드를 찾을 수 없다는 뜻으로 선언되지 않은 변수나 메소드를 사용하거나, 변수 또는 메소드의 이름을 잘못 사용한 경우에 발생한다. 자바에서는 대소문자 구분을 하기 때문에 철자 뿐만 아니라 대소문자의 일치 여부도 꼼꼼하게 확인해야 한다.

### 2. ';'expected

세미콜론`;`이 필요한 곳에 없다는 뜻이다. 자바의 모든 문장의 끝에는 `;`을 붙여주어야 하는데 가끔 이를 잊고 실수하기 쉽다.

### 3. Exception in thread "main" java.lang.NoSuchMethodErro: main

'`main` 메소드를 찾을 수 없다.'는 뜻인데 실제로 클래스 내에 `main` 메소드가 존재하지 않거나, 메소드의 선언부 `public static void main(String[] args)`에 오타가 존재하는 경우에 발생한다.   
이 에러의 해결 방법은 `main` 메소드가 클래스에 정의되어 있는지 확인하고, 정의되어 있다면 `main` 메소드의 선언부에 오타가 없는지 확인한다. 자바는 대소문자를 구별하므로 대소문자의 일치 여부까지 정확히 확인해야 한다.

> `args`는 매개변수의 이름이므로 `args` 대신 `argv`나 `arg`와 같이 다른 이름을 사용할 수 있다.

### 4. Exception in thread "main" java.lang.NoClassDefFoundError: Hello

'Hello'라는 클래스를 찾을 수 없다.'라는 뜻이다. 클래스 'Hello'의 철자, 특히 대소문자를 확인해보고 이상이 없으면 클래스 파일(*.class)이 생성되었는지 확인한다.   
예를 들어 'Hello.java'가 정상적으로 컴파일되었다면 클래스 파일 'Hello.class'가 있어야 한다. 클래스 파일이 존재하는데도 동일한 메세지가 반복해서 나타난다면 클래스 패스(classpath)의 설정이 바르게 되었는지 다시 확인해야 한다.

### 5. illegal start of expression

직역하면 문장(또는 수식, expression)의 앞부분이 문법에 맞지 않는다는 의미인데, 간단히 말해서 문장에 문법적 오류가 있다는 뜻이다. 괄호 `(`나 `{`을 열고서 닫지 않거나, 수식이나 `if`문, `for`문 등에 문법적 오류가 있을 때 또는 `public`이나 `static`과 같은 키워드를 잘못 사용한 경우에도 발생한다. 에러가 발생한 곳이 문법적으로 옳은지 확인해야 한다.

### 6. class, interface, or enum expected
이 메세지의 의미는 '키워드 `class`나 `interface` 또는 `enum`이 없다.'지만, 보통 괄호 `{` 또는 `}`의 개수가 일치하지 않는 경우에 발생한다. 열린 괄호 `{`와 닫힌 괄호 `}`의 개수가 같은지 확인해야 한다.

이 외에 에러가 발생하였을 때, 어떻게 해결해야 하는지 알아보겠다.

> 1. 에러 메세지를 잘 읽고 해당 부분의 코드를 잘 살펴본다.   
이상이 없으면 해당 코드의 주위(윗줄과 아래 줄)도 함께 살펴본다.
> 2. 그래도 이상이 없으면 에러 메세지는 잊어버리고 기본적인 부분을 재확인한다.   
대부분의 에러는 사소한 것인 경우가 많다.
> 3. 의심이 가는 부분을 주석 처리하거나 따로 떼어내서 테스트 한다.

</br>

## 3.3 자바프로그램의 실행 과정

콘솔에서 아래와 같이 Java 애플리케이션을 실행시켰을 때

![Java 애플리케이션](https://ifh.cc/g/cDgYHt.png)

내부적인 진행순서는 다음과 같다.

> 1. 프로그램의 실행에 필요한 클래스(*.class)를 로드한다.
> 2. 클래스 파일을 검사한다. (파일 형식, 악성코드 체크)
> 3. 지정된 클래스(Hello)에서 `main(String[] args)`을 호출한다.

`main` 메소드의 첫 줄부터 코드가 실행되기 시작하여 마지막 코드까지 모두 실행되면 프로그램이 종료되고, 프로그램에서 사용했던 자원들은 모두 반환된다.

</br>

## 3.4 주석(Comment)

작성하는 프로그램의 크기가 커질수록 프로그램을 이해하고 변경하는 일이 점점 어려워진다. 심지어는 자신이 작성한 프로그램도 '내가 왜 이렇게 작성했지?'라는 의문이 들기도 하는데, 남이 작성한 코드를 이해한다는 것은 정말 쉬운 일이 아니다.

이러한 어려움을 덜기 위해 사용하는 것이 바로 주석이다. 주석을 이용해서 프로그램 코드에 대한 설명을 적절히 덧붙여 놓으면 프로그램을 이해하는 데 많은 도움이 된다.

그 외에도 주석은 프로그램의 작성자, 작성일지, 버전과 그에 따른 변경이력 등의 정보를 제공할 목적으로 사용된다.

주석을 작성하는 방법은 다음과 같이 두 가지 방법이 있다. `/*`와 `*/`사이에 주석을 넣은 방법과 앞에 `//`을 붙이는 방법이 있다.

> **범위 주석** `/*`와 `*/`사이의 내용은 주석으로 간주한다.   
**한 줄 주석** `//`부터 라인 끝까지의 내용은 주석으로 간주한다.

다음은 주석의 몇 가지 사용 예인데 초록색 글씨로 처리된 부분이 주석이다.

``` java
/*
Date    : 2022. 7. 24
Source  : Hello.java
Author  : 이현성
Email   : hslee7231@gmail.com
*/

class Hello {
    public static void main(String[] args) {    /* 프로그램의 시작 */
        System.out.println("Hello, world.");    // Hello, world를 출력
    }
}
```

컴파일러는 주석을 무시하고 건너뛰기 때문에 위의 코드와 위의 코드에서 주석을 없앤 코드는 동일하게 동작한다. 따라서 주석이 많다고 해서 프로그램의 성능이 떨어지는 일은 없다.

한 가지 주의해야 할 점은 문자열을 의미하는 큰따옴표 (") 안에 주석이 있을 때는 주석이 아닌 문자열로 인식된다는 것이다. Hello.java를 아래와 같이 변경하여 실행해보면, 주석의 내용도 같이 출력되는 것을 확인할 수 있다.

``` java
class Hello {
    public static void main(String[] args) {
        System.out.println("Hello, /* 이것은 주석 아님 */ world.");
        System.out.println("Hello, world. // 이것도 주석 아님");
    }
}
```
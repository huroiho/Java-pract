s[[자바 초급 2025-05-17]]
# 강의내용
---
## 자바 궁금증
- [[자바는 어떻게 코드를 처리하나요]] #자바질문
- [[자바 public static void main(String args) 이 문장 각각의 단어의 기능과 의미 2025-05-19]] #자바질문
- [[자바 필드가 정확히 뭐지, 속성이나 각 데이터를 필드라고 하나 2025-05-19]] #자바질문
- [[자바-힙 영역과 상수 영역의 차이와 각각의 특징2025-05-20]] #자바질문 
- [[System.out.println 이란 코드의 의미와 흐름, 구분된 영역에 들어가는 요소의 종류, 역할 질문 2025-05-22]] #자바질문
- [[public static void main(String args)의 상세 설명]] #자바질문
- [[힙 영역에 생성된 객체들은 Garbage Collector(GC)에 의해 관리되며, 더 이상 참조되지 않는 객체는 GC에 의해 메모리에서 해제 질문]] #자바질문

## class
- [[자바 Class 관련 용어 2025-05-19]]

## 정적필드
### 정적 필드의 특성: 공유 (Sharing)

- **정적 필드는 클래스에 속하며, 해당 클래스의 모든 인스턴스(객체)들이 이 필드를 공유합니다.**
    
- 메모리 상에 단 하나의 공간만 할당되며, 모든 인스턴스는 이 동일한 메모리 공간을 참조합니다.
    
- 따라서, 어떤 인스턴스가 이 정적 필드의 값을 변경하면, 그 변경 사항은 클래스 자체에 반영되고, 결과적으로 다른 모든 인스턴스에서도 변경된 값을 보게 됩니다.

## 필드 선언
- `new car()`로 메모리에 올라가면 주소가 생기고 이 상태를 가지고 있는게 객체, 인스턴스이고 각 객체는 고유한 주소를 가짐
- 필드는 그냥 데이터나 속성 등 객체, 변수, 클래스의 영역 혹은 부속 전체로 이해하는게 좋아 보임
- **객체는 클래스라는 설계도를 바탕으로 메모리(힙)에 실제로 구현된 실체이며, 자신만의 상태(필드 값)와 행동(메서드)을 가집니다. 이 객체는 참조 변수에 의해 참조될 수 있으며, 참조 변수는 해당 객체의 메모리 주소 또는 식별자(참조값)를 저장합니다."**
- JVM은 내부적으로 각 객체를 구별할 수 있는 방법을 가지고 있습니다. 이것이 바로 앞서 언급된 **메모리 주소 또는 내부적인 객체 ID**와 같은 형태입니다

## 메서드(Method)
- 행동
	- 입력값
		- 매개변수 parameter 
			- 전달된 인자를 받아들이는 변수
		- 인자 argument
			- 어떤 함수를 호출 시에 전달되는 값
- 사용
	- 리턴의 유무와 관련된 흐름
	- 기본형과 참조타입에 따른 흐름
- string 클래스의 메소드
	- 자주 사용하는 기능
		- str.length()
		- str.substring(시작 int인덱스, int마지막 인덱스) 해당력
		- str.concat(str)
			- 문자열과 문자열을 결합해주는 메서드, 고쳐주는?
			- 같은 값을 가진 string class를 또 생성하는 경우는 새로운 객체가 생성되지 않음
			- 이게 불변 클래스이다
```
    String str = new String("hello");

    System.out.println(str.concat(" world"));  //출력결과는 hello world 
    System.out.println(str);  //출력결과는 hello 
이 내용는 concat이 해당 인스턴스 변수와 출력사이 값을 추가하는 것으로 해당 변수의 참조값에는 영향을 주지는 않는다

```


## Scope, Static
- global, localScope
- static 으로 정의된 변수는 클래스 변수로 가용성이 있고 가장 최근 선언된 값을 최종적으로 가진다, 해당 클래스의 모든 인스턴스가 공유함
## 열거형 enum
```java
    public class EnumExam {
        public static final String MALE = "MALE";
        public static final String FEMALE = "FEMALE";

        public static void main(String[] args) {
            String gender1;

            gender1 = EnumExam.MALE;
            gender1 = EnumExam.FEMALE;                  
        }
    }

```

#### 상수를 사용했때의 문제점
- String으로 선언된 gender1 에는 MALE,FEMALE 둘 중 한가지 값을 갖기 원하는데, gender1의 type이 String 이기 때문에 gender1 = "소년"; 이렇게 수행 되어도 전혀 문제가 되지 않는다.
- 실행할때 원했던 값인 MALE,FEMALE 이 아닌 다른 값이 들어오게 되므로 문제를 발생시킬 수 있다
```java
    enum Gender{
        MALE, FEMALE;
    }
```

- 열거형 사용 방법

```java
    Gender gender2;

    gender2 = Gender.MALE;
    gender2 = Gender.FEMALE;
```



## 생성자
#### 모든 클래스는 인스턴스화 될때 생성자를 사용한다.
public 클래스 명(매개변수 목록)
#### 생성자의 특징

- 생성자는 리턴타입이 없다.
- 생성자를 프로그래머가 만들지 않으면 매개변수가 없는 생성자가 컴파일할 때 자동으로 만들어진다.
- 매개변수가 없는 생성자를 기본생성자라고 한다.
- 생성자를 하나라도 프로그래머가 만들었다면 기본생성자는 자동으로 만들어지지 않는다.

#### 생성자의 역할

- 생성자가 하는 일은 객체가 될 때 필드를 초기화 하는 역할을 수행한다.
- 자동차가 객체가 될때 반드시 이름을 가지도록 하려면,Car클래스를 다음과 같이 만들어야 한다.

```
    public class Car{
        String name;
        int number;

        public Car(String n){
            name = n;
        }
    }
```

- 위의 Car 클래스를 이용하여 Car 인스턴스를 생성하는 방법

```
    public class CarExam2{
        public static void main(String args[]){

            Car c1 = new Car("소방차");
            Car c2 = new Car("구급차");
            //Car c3 = new Car(); // 컴파일 오류가 발생합니다.

            System.out.println(c1.name);

            System.out.println(c2.name);
        }
    }
```

- Car클래스는 기본 생성자를 가지지 않는다. 그래서 기본생성자로 Car 객체를 생성할 수 없다.

## this
#### this

### this

#### this는 현재 객체, 자기 자신을 나타낸다.

#### this 의 사용

```
    public class Car{
        String name;
        int number;

        public Car(String n){
            name = n;
        }
    }
```

- Car클래스의 생성자 매개변수의 이름이 n 이다. n 이라는 변수명은 무엇을 의미하는지 쉽기 알수 없다.
- n 으로 쓰기 보다는 name 으로 사용하는 것이 좋다.  
    

```
    public Car(String name){
        name = name;
    }
```

- 'name=name' 이라고 코드를 바꾸면, 가깝게 선언된 변수를 우선 사용하기 때문에 'name=name'이라는 코드는 매개변수의 name의 값을 매개변수 name에 대입하라는 의미가 된다.
- 즉, 필드는 바뀌지 않습니다. 이런 경우 필드라는 것을 컴파일러와 JVM에게 알려주기 위해서 this키워드를 사용해야 한다.

```
    public Car(String name){
        this.name = name;
    }
```

- 앞의 this.name은 필드 name을 말하고 =(이퀄) 뒤의 name은 매개변수를 의미한다.
- 즉 매개변수의 값을 필드에 대입하라는 의미가 된다.

클래스 안에서 자기 자신이 가지고 있는 메소드를 사용할 때도 this.메소드명()으로 호출할 수 있다.

## 매서드 오버로딩
- 매개변수의 유형과 개수가 다르게 하여 같은 이름의 메소드를 여러 개 가질 수 있게하는 기술
- 타입과 매개변수의 수가 하나라도 달라야 함, 매개변수의 이름은 별로 상관이 없음'

## 생성자 오버로딩
- this(본인의 생성자를 호출), 코드의 중복 방지

## 패키지
- 클래스 관리를 위해 사용
- #### 패키지

패키지(package)란 서로 관련이 있는 클래스 또는 인터페이스들을 묶어 놓은 묶음이다. 패키지를 사용함으로써 클래스들이 필요할 때만 사용될 수 있도록 하고, 클래스를 패키지 이름과 함께 계층적인 형태로 사용함으로써 다른 그룹에 속한 클래스와 발생할 수 있는 클래스 이름간의 충돌을 막아줌으로 클래스의 관리를 편하게 해준다.

 패키지 정의방법

- package이름은 보통 도메인 이름을 거꾸로 적은 후, 그 뒤에 프로젝트 이름을 붙여서 만든다. 물론, 프로젝트 이름 뒤에 또 다른 이름이 나올 수도 있다.
- package이름은 폴더명 점 폴더명 점 폴더명 과 같은 형식으로 만들어진다. 각각의 폴더명은 숫자로 시작할 수 없다.
- 도메인 이름이 8cruz.com 이고 프로젝트 이름이 javastudy 라면 com.eightcruz.javastudy.Hello 로 패키지를 지정 할 수 있다.
    - 도메인이 숫자로 시작되는데 패키지명은 첫글자에 숫자를 사용할 수 없으므로 적절하게 수정한다.
    - 도메인으로 사용하는 이유는 패키지가 중복되는것을 방지하기 위함이므로, 반드시 존재하는 도메인이 아니라도 상관없다.

 이클립스에서 패키지 생성하기

1. 소스폴더를 선택한 후 우측버튼을 클릭하여 패키지 생성을 선택한다.
2. 패키지 이름에 kr.co.helloWorld.javastudy를 입력한다.
3. 해당 패키지를 선택하고 Hello클래스를 작성한다.
    - 작성된 클래스 파일의 첫줄에 package com.eightcruz.javastudy.Hello; 생성된것을 볼 수 있다.
    - 패키지를 생성하는 예약어는 package 다.

 패키지에 생성된 클래스 사용하기

- java.lang패키지를 제외하고는 다른 패키지에 있는 클래스를사용하려면 import라는 구문을 적어줘야 한다.
- import com.eightcruz.javastudy.Hello;
- 위의 코드는 com.eightcruz.javastudy패키지 아래의 Hello클래스를 사용하겠다는 것을 컴파일러와 JVM에게 알리는 것이다.
- 클래스 이름대신에 * 를 적어도 된다. import com.eightcruz.javastudy.*;

 import 하지 않고 사용하는 방법

- 만약 import를 하기 싫다면, 혹은 각기 다른 패키지에 존재하는 같은 이름의 클래스 파일을 사용해야 한다면 아래와 같이 이용한다.
    - com.eightcruz.javastudy.Hello hello = newe com.eightcruz.javastudy.Hello(); 이렇게 사용한다.

## 상속
#### 상속

#### 상속이란? 부모가 가진것을 자식에게 물려주는것을 의미한다.

- 노트북은 컴퓨터의 한 종류다.
- 침대는 가구의 한 종류다. 혹은 침대는 가구다.
- 소방차는 자동차다.

이렇게 말할 수 있는 관계를 is a 관계 혹은 kind of 관계라고 한다.

#### Car 를 상속받은 Bus 를 class로 표현하는 방법

```
    public class Car{

    }

    public class Bus extends Car{

    }
```

- 자바는 클래스 이름 뒤에 extends 키워드를 적고 부모클래스 이름을 적게 되면 부모 클래스가 가지고 있는 것을 상속받을 수 있게 된다.
- 상속이란 부모가 가지고 있는 것을 자식이 물려받는 것을 말한다. 즉, 부모가 가지고 있는 것을 자식이 사용할 수 있게 된다.

#### 부모클래스에 메소드 추가하기

- Car에 run()메소드를 추가

```
    public class Car{
        public void run(){
            System.out.println("달리다.");
        }
    }
```

- Car를 상속받은 Bus 사용

```
    public class BusExam{
        public static void main(String args[]){
            Bus bus = new Bus();
            bus.run();  
            //Bus class 는 아무런 코드를 가지지 않는다. 그럼에도 run 이라는 메소드를 사용하는데 문제가 발생되지 않는다. 
        }   
    }
```

- Bus에 메소드 추가

```
    public class Bus extends Car{
        public void ppangppang(){
            System.out.println("빵빵");
        }       
    }
```

- Bus는 Car에서 물려받은 run메소드와 ppangppang메소드를 사용할 수 있게 된다.
- 부모가 가지고 있는 메소드외에 추가로 메소드를 선언하는 것을 확장하였다고 표현한다.
- 부모 클래스는 자식이 가지고 있는 클래스는 사용할 수 없음

## 접근 제한자
#### 접근제한자

#### 접근 제한자란 클래스 내에서 멤버의 접근을 제한하는 역할을 한다.

#### 접근제한자의 종류

- public
    - 어떤 클래스든 접근할 수 있다는 것을 의미
- protected
    - 자기 자신, 같은 패키지, 서로 다른 패키지다 하더라도 상속받은 자식 클래스에서는 접근할수 있다는 것을 의미
- private
    - 자기 자신만 접근할 수 있다는 것을 의미
- 접근제한자를 적지 않으면 default접근 지정자
    - 자기자신과 같은 패키지에서만 접근할 수 있다는 것을 의미

```java
    public class AccessObj{
        private int i = 1;
        int k = 2; // default접근 제한자
        public int p = 3;
        protected int p2 = 4;
    }
```

- AccessObj를 사용하는 AccessObjExam
    - AccessObj의 필드 i 의 접근 제한자는 private이므로 다른 클래스인 AccessObjExam에서 접근할 수 없다.

```java
    public class AccessObjExam{
        public static void main(String args[]){
            AccessObj po = new AccessObj();

            System.out.println(po.i); // 컴파일 오류가 발생합니다.
            System.out.println(po.k);
            System.out.println(po.p);
            System.out.println(po.p2);
        }
    }
```

- AccessObj 와 다른 패키지에서 사용해보기
    - 패키지가 달라졌기때문에 default접근제한자로 지정된 필드 k 와 protected 접근제한자로 지정된 필드 p2 도 접근할 없다.

```java
    public class AccessObjExam{
        public static void main(String args[]){
            AccessObj po = new AccessObj();

            System.out.println(po.i); // 컴파일 오류가 발생합니다.
            System.lout.println(po.k);// 컴파일 오류가 발생합니다.
            System.lout.println(po.p);
            System.lout.println(po.p2);// 컴파일 오류가 발생합니다.
        }
    }
```

- AccessObjExam을 AccesObj로 부터 상속받도록 수정한 후 사용해 보기
    - 패키지는 다르지만 상속관계에 있으므로 protected 접근제한자로 지정된 필드 p2에 접근할 수 있다.

```java
    public class AccessObjExam extends AccessObj{
        public static void main(String[] args) {
            AccessObjExam obj = new AccessObjExam();
            System.out.println(obj.p);
            System.out.println(obj.p2);
            System.out.println(obj.k);// 컴파일 오류가 발생합니다.
            System.out.println(obj.i);// 컴파일 오류가 발생합니다.
        }
    }
```
## 추상 클래스
#### 추상클래스

#### 추상 클래스란 구체적이지 않은 클래스를 의미한다. 독수리, 타조는 구체적인 새를 지칭하는데 새, 포유류 같은 것은 구체적이지 않다.

#### 이런 것을 구현한 클래스를 추상 클래스라고 한다.

#### 추상 클래스 정의하기

- 추상 클래스는 클래스 앞에 abstract 키워드를 이용해서 정의한다.
- 추상 클래스는 미완성의 추상 메소드를 포함할 수 있다.
    - 추상 메소드란, 내용이 없는 메소드 이다. 즉 구현이 되지 않은 메소드이다.
    - 추상 메소드는 리턴 타입 앞에 abstract라는 키워드를 붙여야 한다.
- 추상 클래스는 인스턴스를 생성할 수 없다.

```
    public abstract class Bird{
        public abstract void sing();

        public void fly(){
            System.out.println("날다.");
        }
    }
```

#### 추상 클래스를 상속받는 클래스 생성하기

- 추상 클래스를 상속받은 클래스는 추상 클래스가 갖고 있는 추상 메소드를 반드시 구현해야 한다.
- 추상 클래스를 상속받고, 추상 클래스가 갖고 있는 추상 메소드를 구현하지 않으면 해당 클래스도 추상 클래스가 된다.

```
    public class Duck extends Bird{
        @Override
        public void sing() {
            System.out.println("꽥꽥!!");
        }
    }
```

#### 사용하기

- Bird는 추상 클래스 이므로 객체를 생성할 수 없다.

```
    public class DuckExam { 
        public static void main(String[] args) {
            Duck duck = new Duck();
            duck.sing();
            duck.fly();

            //Bird b = new Bird();
        }   
    }
```

## super 와 부모 생성자
#### class가 인스턴스화 될때 생성자가 실행되면서 객체의 초기화를 한다. 그 때 자신의 생성자만 실행이 되는것이 아니고, 부모의 생성자부터 실행된다.

#### 부모 생성자

```
    public class Car{
        public Car(){
            System.out.println("Car의 기본생성자입니다.");
        }
    }

    public class Bus extends Car{
        public Bus(){
            System.out.println("Bus의 기본생성자입니다.");
        }

    }
```

- 생성자 테스트

```
    public class BusExam{
        public static void main(String args[]){
            Bus b = new Bus();
        }
    }
```

- 결과

Car의 기본생성자입니다.  
Bus의 기본생성자입니다.

- new 연산자로 Bus객체를 생성하면, Bus객체가 메모리에 올라갈때 부모인 Car도 함께 메모리에 올라간다.
- 생성자는 객체를 초기화 하는 일을한다.
- 생성자가 호출될 때 자동으로 부모의 생성자가 호출되면서 부모객체를 초기화 하게된다.

#### super

- 자신을 가리키는 키워드가 this 라면, 부모들 가리키는 키워드는 super
- super() 는 부모의 생성자를 의미한다.
- 부모의 생성자를 임의로 호출하지 않으면, 부모 class의 기본 생성자가 자동으로 호출된다.  
    
- 아래 예제처럼 호출해보면 위에서 super()를 호출하지 않을때와 결과가 같다.

```
    public Bus(){
        super();
        System.out.println("Bus의 기본생성자입니다.");
    }
```

#### 부모의 기본생성자가 아닌 다른 생성자를 호출하는 방법

- 클래스는 기본 생성자가 없는 경우도 존재한다.  
0000000000    

```
    public class Car{
        public Car(String name){
            System.out.println(name + " 을 받아들이는 생성자입니다.");
        }
    }
```

- Car class가 위 처럼 수정되면, Bus생성자에서 컴파일 오류가 발생한다.
- 부모가 기본생성자가 없기 때문에 컴파일 오류가 발생하게 되는 것이다.
- 이런 문제를 해결하려면 자식 클래스의 생성자에서 직접 부모의 생성자를 호출해야 합니다.

```
    public Bus(){
        super("소방차"); // 문자열을 매개변수로 받는 부모 생성자를 호출하였다.
        System.out.println("Bus의 기본생성자입니다.");
    }
```

#### super 키워드는 자식에서 부모의 메소드나 필드를 사용할 때도 사용합니다.
## 질문 임시




---

		- 


 
## 아웃링크(이 노트에서 링크된 노트)
```dataview
TABLE WITHOUT ID link.file.link AS "노트", link.cmds AS "카테고리", link.tags AS "태그"
FROM ""
FLATTEN file.outlinks AS link
WHERE contains(file.path, this.file.path)
SORT link.category ASC
```



# 1.수행형 과제

## [주제1] : 생성자(Constructor)

### 내용 설명 및 요약
* 인스턴스가 생성될 때 호출되는 '인스턴스 최기화 메서드'이다. 
* 따라서 인스턴스 변수의 초기화 작업에 주로 사용되며, 인스턴스 생성시에 실행되어야 할 작업을 위해서도 사용된다.

* 기본 생성자
Ex)
클래스이름(){}
Card(){}
기본 생성자가 컴파일러에 의해서 추가되는 경우는 클래스에 정의된 생성자가 하나도 없을 때 뿐이다.

* 매개변수가 있는 생성자
인스턴스 변수의 값을 변경하는 것 보다 매개변수를 갖는 생성자를 사용하는 것이 코드를 보다 간결하고 직관적으로 만든다.  
Ex)  
Car c = new Car();  
c.color = "white";  
c.gearType = "auto";  
c.door = 4;  
↓  
Car c = new Car("White","auto",4);  

* 생성자에서 다른 생성자 호출하기

this(), this  
-생성자의 이름으로 클래 스이름 대신 this를 사요한다.
-한 생성자에서 다른 생성자를 호출할 때는 반드시 첫 줄에서만 호출이 가능하다.
Ex)  
Car(String color){  
  door = 5;  
  Car(color, "auto", 4); //에러1. 생성자의 두 번째 줄에서 다른 생성자 호출  
}                        //에러2. this(color,"auto",4);  

* 생성자를 이용한 인스턴스의 복사  
현재 사용하고 있는 인스턴스와 같은 상태를 갖는 인스턴스를 하나 더 만들고자 할 때 생성자를 이용 가능  
생성된 모든 인스턴스의 메서드와 클래스변수는 서로 동일하기 때문에 인스턴스간의 차이는 인스턴스마다 각기 다른 값을 가질 수 있는 인스턴스 변수 뿐  

인스턴스 생성할 때 2가지 사항을 결정!!  
1.클래스 - 어떤 클래스의 인스턴스를 생성할 것인가?  
2.생성자 - 선택한 클래스의 어떤 생성자로 인스턴스를 생성할 것인가?  

### 예제코드
```java

class Main {
	
	public static void main(String[] args) {
		
		Book book1 = new Book("JAVA", 20, "GOORM");
		book1.Print();
		
	}
}

class Book {
	String Name;
	int page;
	String Author;
	
	Book(String inputName, int inputPage, String inputAuthor) {
		Name = inputName;
		page = inputPage;
		Author = inputAuthor;
	}
	
	void Print() {
		System.out.println(Name + "/" + Author + "/" + page);
	}
}

```

### 코드에 대한 설명
*  매개변수가 있는 생성자 BOOK을만들어서 BOOK클래스에 값을 집어 넣고 출력한다.

## [주제2] : 클래스와 객체

### 내용 설명 및 요약
* 클래스와 객체의 정의와 용도  
정의 : 클래스란 객체를 정의해 놓은 것이다.  
용도 : 클래스는 객체를 생성하는데 사용된다.  

* 객체와 인스턴스
클래스로부터 객체를 만드는 과정을 '클래스의 인스턴스화'  
어떤 클래스로부터 만들어진 객체를 '그 클래스의 인스턴스'  

* 객체의 구성요소 - 속성과 기능  
속성 : 멤버변수, 특성, 필드, 상태  
기능 : 메서드, 함수, 행위  

* 인스턴스의 생성과 사용
클래스명 변수명;  
변수명 = new 클래스명();  

Tv t;  
t = new Tv();  

인스턴스는 참조변수를 통해서만 다룰 수 있으며, 참조변수의 타입은 인스턴스의 타입과 일치해야한다.

* 객체 배열  
Ex)  
Tv[] tvArr = new Tv[100];  
  
for(int i = 0 ; tvArr.length; i++){  
  tvArr[i] = new Tv();  
}  



### 예제코드
```java

public class TV {
 
    String color;
    boolean power;
    int channel;
 
    void power() {
        power = !power;
    }
 
    void channelUp() {
        ++channel;
    }
 
    void channelDown() {
        --channel;
    }
 
    public static void main(String[] args) {
        TV tv = new TV();
        tv.channel = 7;
        tv.channelDown();
        System.out.println("Tv channel is " + tv.channel);
    }
```

### 코드에 대한 설명
* 인스턴스  TV tv = new TV(); 를 생성해서 tv.channel을 7로 넣고 tv.channelDown();해서 tv.cahnnel을 출력시킨다.

## [주제3] : 상속

### 내용 설명 및 요약
* 상속의 정의와 정점
기존의 클래스를 재사용하여 새로운 클래스를 작성하는 것
보다적은 양의 코드로 새로운 클래스를 작성 가능
코드 추가 및 변경이 매우 용이

class Child extends Parent{
  //....
}

생성자와 초기화 블럭은 상속되지 않고 멤버만 상속된다.
자손 클래스의 멤버 개수는 조상 클래스보다 항상 같거나 많다.

* 클래스간의 관계 - 포함관계
클래스간의 포함관계를 맺어 주는 것은 한 클래스의 멤버변수로 다른 클래스 타입의 참조변수를 선언하는것


* 클래스간의 관계 결정하기
class Circle{
  Point c = new Point():
  int r;
}

↓

class Circle extends Point {
  int r;
}

상속관계 = is-a
포함관계 = has-a

* 단일 상속 
자바에서는 오직 단일 상속만 허용

class TVCR extends Tv,VCR{ //에러. 조상은 하나만 허용
  //.....
}

* Object 클래스 - 모든 클래스의 조상
모든 클래스들은 자동적으로 object클래스로부터 상속 받게 한다.




### 예제코드
```java

Class Vehicle {

    public int speed;
    
    public int getSpeed() {
        return speed;
    }
    public void setSpeed(int speed) {
        this.speed = speed;
    }
    
}

class Car extends Vehicle {

}

public class Test {

    public static void main(String[] args) {

        Car A = new Car();
        A.getSpeed();
    }
}
```



### 코드에 대한 설명
*   Car 클래스에는 getSpeed 메소드가 없지만 상속된 Vehicle에 getSpeed 메소드가 있기 때문에 사용 가능하다.

# 2. 실습형 과제

## [실습1]

### 실습코드
```java

package test.exam;

import java.util.Scanner;

public class Test_01 {
	public static void main(String[] args) {

		Scanner scan = new Scanner(System.in);
		System.out.print("첫 번째 포인트의 x, y 좌표 : ");
		int x1 = scan.nextInt();
		int y1 = scan.nextInt();
		
		System.out.print("두 번째 포인트의 x, y 좌표 : ");
		int x2 = scan.nextInt();
		int y2 = scan.nextInt();
		
		int x = x2-x1;
		int y = y2-y1;
		
		int area = x*y;
		
		System.out.println("넓이 : " + Math.abs(area));
		
		scan.close();
	}

}

```
### 실행결과
```console

첫 번째 포인트의 x, y 좌표 :  2 4
두 번째 포인트의 x, y 좌표 :  4 2
넓이 : 4

```

## [실습2]

### 실습코드
```java

package test.exam;

import java.util.Scanner;

public class Test_02 {

	public static void main(String[] args) {
		
		Scanner scan = new Scanner(System.in);
		System.out.print("입력할 정수의 개수 : ");
		int num = scan.nextInt();
		double avg = 0;
		
		for(int i = 1; i <= num ; i++) {
			System.out.print("정수입력 : ");
			int num_input = scan.nextInt();
			avg += num_input;
		}
		System.out.printf("입력의 평균 : %f", avg/num);
		scan.close();
	}

}

```
### 실행결과
```console

입력할 정수의 개수 : 4
정수입력 : 2
정수입력 : 7
정수입력 : 2
정수입력 : 4
입력의 평균 : 3.750000
```

## [실습3]

### 실습코드
```java

package test.exam;

import java.util.Scanner;

public class Test_03 {

	public static void main(String[] args) {
		
		Scanner scan = new Scanner(System.in);
		System.out.print("입력할 정수를 세개 입력하세요... ");
		int num_1 = scan.nextInt();
		int num_2 = scan.nextInt();
		int num_3 = scan.nextInt();
		
		int result = num_1*num_2-num_3;
		System.out.println("결과 : " + result);
		
		scan.close();
	}

}

```
### 실행결과
```console

입력할 정수를 세개 입력하세요... 1 2 3
결과 : -1

```

## [실습4]

### 실습코드
```java

package test.exam;

public class Test_04 {

	public static void main(String[] args) {
		for (int i = 1; i < 8; i++) {
			for (int j = 1; j < 8; j++) {
				if (i + j == 7) {
					int result = (10 * i + j) + (10 * j + i);
					System.out.println((10 * i + j) + " + " + (10 * j + i) + " = " + result);
				}
			}
		}
	}

}

```
### 실행결과
```console

16 + 61 = 77
25 + 52 = 77
34 + 43 = 77
43 + 34 = 77
52 + 25 = 77
61 + 16 = 77

```

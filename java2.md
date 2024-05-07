## 객체 지향 프로그래밍

### 객체 지향 프로그래밍(Object-Oriented Programming, OOP)이란

- 프로그램을 조립하여 만드는 방식
- 프로그램을 부분별로 만든 뒤 전체를 구성하는 형식

자전거를 예로 들면,

- 자전거는 바퀴, 몸체, 손잡이 등의 부품으로 구성
- 자전거를 프로그램이라 한다면 각 부품은 객체가 됨
- 이렇게 각 객체가 모여 전체 프로그램을 구성하는 방식을 OOP라 함

---

## 객체 지향 프로그래밍의 장점

### 유지 보수성

- OOP 기반 프로그램은 객체별 관리 가능
- 문제가 생기더라도 특정 객체의 코드만 고치면 됨

### 코드 재사용성

- 다양한 코드뿐 아니라 다른 프로그램에서까지 손쉽게 사용할 수 있음

### 프로그램 확장성

- 처음부터 조립 방식을 고려해 만들기 때문에 새로운 코드로 확장하기 편리

---

## 클래스와 객체의 관계

### 클래스를 토대로 객체를 만드는 과정을 인스턴스화(instantiation)라 함

- 이러한 이유로 객체를 인스턴스(instance)라고 부르기도 함

<img width="706" alt="Untitled (5)" src="https://github.com/dawoon1229/Java_practice/assets/164113758/de138a10-5d1e-4824-ad96-4a41cc555771">

---


## 클래스 구현하기

### 고양이(Cat)클래스 다이어그램을 실제 코드로 구현한 예

```java
public class Cat {
	String name;
	String breeds;
	double weight;
	
	void claw() {
		System.out.println("할퀴기!!");
	}
	
	void meow() {
		System.out.println("야옹~");
	}
}
```

---

## 객체 생성하기

### 객체 생성 과정

- Cat 클래스를 객체로 만드는 예

```java
Cat c = new Cat(); // Cat 객체 생성 후, 해당 객체를 변수 c에 연결
```

<img width="317" alt="스크린샷 2024-05-07 195852" src="https://github.com/dawoon1229/Java_practice/assets/164113758/35127088-2c03-485d-a6d9-d86667f22f09">

---

## 여러 객체 만들기

### 객체 생성과 필드의 사용

- 두 강아지 객체를 레퍼런스변수 d1과 d2에 연결하는 코드 예

```java
Dog d1 = new Dog(); // Dog 객체 생성 후, d1 변수에 연결
Dog d2 = new Dog(); // Dog 객체 생성 후, d2 변수에 연결
```

<img width="425" alt="스크린샷 2024-05-07 200102" src="https://github.com/dawoon1229/Java_practice/assets/164113758/a63efb40-1acb-4017-af3c-a8a4e617e8f1">


### 객체 생성과 필드의 사용

- 두 강아지의 상태 변경 예(레퍼런스변수와 닷 연산자를 사용)

```java
//d1 객체의 상태 변경
d1.name = "망고";
d1.breeds = "골든리트리버";
d1.age = 2;

//d2 객체의 상태 변경
d2.name = "나미";
d2.breeds = "믹스";
d2.age = 3;
```

---

## 생성자란

### **생성자**(constructor)란 클래스로부터 객체를 만드는 특별한 메소드

- 붕어빵을 만들려면 붕어빵 틀에 재료를 넣고 구워야 함
- 마찬가지로 객체를 만들려면 클래스라는 틀에 재료를 넣어야 함

---

## 생성자 호출과 정의

### 생성자 정의

```java
Cat c = new Cat("네로", "페르시안", 3.78);
```

- 메소드 정의 형식을 닮음
- 입력변수로 필드를 초기화
- 반환 타입이 없음
- 생성자명은 클래스명과 같아야 함

반환값이 없는 메소드는 void 타입이지만, 생성자는 객체의 주소를 반환하므로 타입 자체를 적지 않음

```java
public class Cat {
	String name;
	String breeds;
	double weight;
	
	Cat(String n, String b, double w) {
		name = n;
		breeds = b;
		weight = w;
	}
}
```

---

```java
package javaprac;

public class java0507_2 {
	String name;
	String breeds;
	int age;
	void wag() {
		System.out.printf("[%s] 살랑살랑~\n",name);
	}
	void bark() {
		System.out.printf("[%s] 멍멍!\n",name);
	}
	void bark(int times) {
		String sound = "컹컹!";
		System.out.printf("[%s] %s(x%d)\n", name, sound, times);
	}
	public static void main(String[] args) {
		java0507_2 d1 = new java0507_2();
		java0507_2 d2 = new java0507_2();
		
		d1.name = "망고";
		d1.breeds = "골든리트리버";
		d1.age = 2;
		d2.name = "나미";
		d2.breeds = "믹스";
		d2.age = 3;
		
		System.out.printf("d1 => {%s, %s, %d세}\n",d1.name,d1.breeds,d1.age);
		System.out.printf("d2 => {%s, %s, %d세}\n",d2.name,d2.breeds,d2.age);
		
		d1.wag();
		d2.bark();
		d1.bark(3);
		
	}

}

```

<img width="153" alt="스크린샷 2024-05-07 200851" src="https://github.com/dawoon1229/Java_practice/assets/164113758/b0678f23-9a5c-4565-a419-27a616c1e7c6">



```java
package javaprac;

public class HeroTest {

	public static void main(String[] args) {
		
		Hero ironMan = new Hero("아이언맨", 100, 120);
		Hero hulk = new Hero("헐크", 200, 80);
		
		System.out.println(ironMan.toStr());
		System.out.println(hulk.toStr());

	}
}

class Hero{
	String name;
	int power;
	int speed;
	
	Hero(String n, int p, int s){
		name = n;
		power = p;
		speed = s;
	}
	String toStr() {
		return String.format("Hero{name: %s, power: %d, speed: %d}",name, power, speed);
	}
}
```

<img width="245" alt="스크린샷 2024-05-07 200936" src="https://github.com/dawoon1229/Java_practice/assets/164113758/33d18899-09d6-4c44-a2ab-5f4308521cb0">


```java
package javaprac;

public class Cylinder {
	int radius;
	int height;
	
	double getVolume() {
		return radius * radius * Math.PI * height;
	}
	
	double getSurfaceArea() {
		double circleArea = Math.PI * radius * radius;
		double rectangleArea = height *2 * Math.PI * radius;
		return 2 * circleArea + rectangleArea;
	}
	
	public static void main(String[] args) {
		Cylinder c = new Cylinder();
		c.radius = 4;
		c.height = 5;
		System.out.printf("원기둥의 부피: %.2f\n", c.getVolume());
		System.out.printf("원기둥의 겉넓이: %.2f\n", c.getSurfaceArea());

	}

}
```

<img width="118" alt="스크린샷 2024-05-07 201015" src="https://github.com/dawoon1229/Java_practice/assets/164113758/5e2851ef-feb3-45d4-bc94-58d4a6106dda">






## 상속과 업 캐스팅

예를 들어 정사각형(Square), 삼각형(Triangle), 원(Circle) 클래스가 하나의 도형(Shape) 클래스로부터 파생되었다고 가정할 때,

- Square, Triangle, Circle 객체는 부모 클래스인 Shape 타입으로 해석 가능
- 자식 객체는 부모 타입의 배열 또는 ArrayList 등에 담겨 관리될 수 있음
- 하지만 부모 객체를 자식 타입으로 다운 캐스팅(좁은 범위로 해석)할 수는 없음
```java
package javaprac;

public class UpCastingTest {

	public static void main(String[] args) {
		// TODO Auto-generated method stub
		Square s = new Square();
		s.name = "정사각형";
		Triangle t = new Triangle();
		t.name = "삼각형";
		Circle c = new Circle();
		c.name = "원";
		
		Shape[] shapes = {s,t,c};
		for (int i = 0; i<shapes.length; i++) {
			System.out.printf("%d번 인덱스의 도형: %s\n", i, shapes[i].name);
		}
	}

}

//부모 클래스
class Shape { //도형
	String name;
}

//자식 클래스
class Square extends Shape {} //정사각형
class Triangle extends Shape {} //삼각형
class Circle extends Shape {} //원
```
---

## 메소드 오버라이딩

메소드 오버라이딩(method overriding)은

- 자식 클래스에서 **재정의된 메소드가 수행되는 것**
- 적은 코드로 다양한 동작을 가능케 함
```java
package javaprac;

public class OverridingTest {

	public static void main(String[] args) {
		// TODO Auto-generated method stub
		Archer a = new Archer();
		Archer ma = (Archer) new MasterArcher(); //업 캐스팅
		a.shoot();
		ma.shoot();
	}

}

class Archer {
	void shoot() {
		System.out.println("[아처]의 활 공격이 10만큼의 피해를 주었습니다.");
	}
}
class MasterArcher extends Archer {
	void shoot() {
		System.out.println("[마스터 아처]의 활 공격이 30의 피해를 주었습니다.");
	}
}
```
---

## this 키워드

this는 레퍼런스변수이며, 메소드 수행ㅇ의 주체 객체를 가리킴

this 키워드는 메소드 수행 시

- 필드와 입력변수를 구분하거나
- 소괄호를 붙여 또 다른 생성자를 호출하기 위해 사용
```java
package javaprac;

public class MoreKeywords {

	public static void main(String[] args) {
		Weapon w1 = new Weapon("장검", 1200, 10);
		Weapon w2 = new Weapon();
		w1.printInfo();
		w2.printInfo();
	}

}
abstract class Item {
	String name;
	int price;
	public Item(String name, int price) {
		this.name = name;
		this.price = price;
	}
	public Item() {
		this.name = "이름 없음";
		this.price = -1;
	}
	public String getName() {
		return name;
	}
	public int getPrice() {
		return price;
	}
}
class Weapon extends Item {
	private int power;
	Weapon(String name, int price, int power) {
		super(name, price);
		this.power = power;
	}
	Weapon() {
		super();
		this.power = -1;
	}
	void printInfo() {
		System.out.printf("[%s] 가격: %d 골드, 공격력: %d\n", super.getName(), super.getPrice(), this.power);
	}
}
```
---

## protected 키워드

protected는 접근 제한자 중 하나로

- 같은 패키지 내부 또는 상속 관계에 있는 클래스에게 접근을 허용

<img width="364" alt="스크린샷 2024-05-16 175931" src="https://github.com/dawoon1229/Java_practice/assets/164113758/43e37b74-5a63-4346-b3f0-1f7d756c6904">

private의 경우 외부 접근이 불가능해 게터와 세터 메소드를 만들어야 하는데,

- private은 상속 관계에서 사용하기 다소 불편
- protected를 사용하면 이러한 불편을 해소할 수 있음
```java
package javaprac;

public class MovieDiscountByGenre {

	public static void main(String[] args) {
		// TODO Auto-generated method stub
		ActionMovie am = new ActionMovie("범죄도시");
		HorrorMovie hm = new HorrorMovie("여고괴담");
		ComedyMovie cm = new ComedyMovie("극한직업");
		int sum = 0;
		sum += am.discountedPrice();
		sum += hm.discountedPrice();
		sum += cm.discountedPrice();
		System.out.printf("총 예매 금액: %d원", sum);
	}

}
//영화를 나타내는 추상 클래스 Movie 정의
abstract class Movie {
	protected String title; // 영화 제목
	protected int price;    // 정가

	// 생성자: 제목을 받아 초기화하고 정가는 10000으로 설정
	public Movie(String title) {
		this.title = title;
		this.price = 10000;
	}

	// 추상 메서드: 할인된 가격을 계산하는 메서드
	abstract int discountedPrice();
}

//액션 영화를 나타내는 클래스 ActionMovie 정의
class ActionMovie extends Movie {
	// 생성자: 부모 클래스의 생성자 호출
	public ActionMovie(String title) {
		super(title);
	}

	// 할인된 가격을 계산하는 메서드
	@Override
	int discountedPrice() {
		return price - 1000; // 액션 영화는 1000원 할인
	}
}

//공포 영화를 나타내는 클래스 HorrorMovie 정의
class HorrorMovie extends Movie {
	// 생성자: 부모 클래스의 생성자 호출
	public HorrorMovie(String title) {
		super(title);
	}

	// 할인된 가격을 계산하는 메서드
	@Override
	int discountedPrice() {
		return price - 800; // 공포 영화는 800원 할인
	}
}

//코미디 영화를 나타내는 클래스 ComedyMovie 정의
class ComedyMovie extends Movie {
	// 생성자: 부모 클래스의 생성자 호출
	public ComedyMovie(String title) {
		super(title);
	}

	// 할인된 가격을 계산하는 메서드
	@Override
	int discountedPrice() {
		return price - 1500; // 코미디 영화는 1500원 할인
	}
}
```
---

## static 메소드

인터페이스는 static 메소드를 포함할 수 있음

인터페이스의 static 메소드는 재정의될 수 없으며, 반드시 인터페이스명을 통해서 호출해야 함
```java
package javaprac;

public class StaticMethodInInterface {

	public static void main(String[] args) {
		// TODO Auto-generated method stub
		System.out.printf("3 더하기 7 은 %d 입니다.\n", Calculator.plus(3,7));
		System.out.printf("4 빼기 6 은 %d 입니다.\n", Calculator.minus(4,6));
	}

}
interface Calculator {
	static int plus(int a, int b) {
		return a + b;
	}
	static int minus(int a, int b) {
		return a - b;
	}
}
```
---

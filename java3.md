```java
package javaprac;

public class AvengerTest {

	public static void main(String[] args) {
		// TODO Auto-generated method stub
		Avenger thor = new Avenger("토르", 150);
		Avenger thanos = new Avenger("타노스", 160);
		thor.punch(thanos);
		thor.punch(thanos);
		thanos.punch(thor);
		
	}

}

class Avenger {
	String name;
	int hp;
	
	Avenger(String s, int i){
		name = s;
		hp = i;
	}
	void punch(Avenger enemy) {
		System.out.printf("[%s]의 펀치!",name);
		enemy.hp -=10;
		System.out.printf("-> %s의 체력: %d\n", enemy.name, enemy.hp);
	}
}
```

```java
package javaprac;

public class CoffeeTest {

	public static void main(String[] args) {
		// TODO Auto-generated method stub
		Coffee c = new Coffee("아메리카노", 3000);
		System.out.printf("%s(%d원) -> ", c.getName(), c.getPrice());
		c.setPrice(c.getPrice() + 500);
		System.out.printf("%s(%d원)", c.getName(), c.getPrice());
	}

}

class Coffee {
	private String name;
	private int price;
	
	public Coffee(String n, int p) {
		name = n;
		price = p;
	}
	public String getName() {
		return name;
		
	}
	public int getPrice() {
		return price;
	}
	public void setPrice(int p) {
		price = p;
	}
}
```

```java
package javaprac;

import java.util.Scanner;

public class UserInput {

	public static void main(String[] args) {
		// TODO Auto-generated method stub
		Scanner input = new Scanner(System.in);
		System.out.print("이름: ");
		String name = input.next();
		System.out.print("학번: ");
		int number = input.nextInt();
		System.out.print("학점: ");
		double grade = input.nextDouble();
		System.out.printf("[%s]님의 학번은 %d이며, 학점은 %.2f 입니다.", name, number, grade);

	}

}
```

```java
package javaprac;

import java.lang.Math;

public class MathTest {

	public static void main(String[] args) {
		// TODO Auto-generated method stub
		System.out.printf("수학의 파이(원주율) 값: %f\n", Math.PI);
		System.out.printf("임의 난수 값: %f\n", Math.random());
		System.out.printf("9.81의 내림값: %f\n", Math.floor(9.81));
		System.out.printf("4의 제곱근: %f\n", Math.sqrt(4));
		System.out.printf("2의 3승: %f\n", Math.pow(2,3));
	}

}
```

```java
package javaprac;

import java.util.ArrayList;

public class ArrayListTest {

	public static void main(String[] args) {
		// TODO Auto-generated method stub
		ArrayList<String> names = new ArrayList<String>();
		
		names.add("Kim");
		names.add("Lee");
		names.add("Park");
		names.add("Choi");
		
		names.set(0, "Han");
		String removed = names.remove(1);
		
		for (int i = 0; i < names.size(); i++) {
			System.out.printf("%s ", names.get(i));
		}
	}

}

```

```java
package javaprac;

public class RPGTest {

	public static void main(String[] args) {
		// TODO Auto-generated method stub
		Wizard wizard = new Wizard();
		Knight knight = new Knight();
		wizard.name = "간달프";
		wizard.hp = 100;
		wizard.mp = 80;
		wizard.punch();
		wizard.fireball();
		knight.name = "킹아서";
		knight.hp = 150;
		knight.stamina = 70;
		knight.punch();
		knight.slash();
	}

}

class Novice {
	String name;
	int hp;
	void punch() {
		System.out.printf("%s(HP: %d)의 펀치!\n", name, hp);
		
	}
}

class Wizard extends Novice { 
	int mp;
	void fireball() {
		System.out.printf("%s(HP: %d, MP: %d)의 파이어볼~@\n", name, hp, mp);
	}
}

class Knight extends Novice {
	int stamina;
	void slash() {
		System.out.printf("%s(HP: %d, ST: %d)의 슬래쉬!!\n", name, hp, stamina);
	}

```

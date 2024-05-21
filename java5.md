<img width="1205" alt="스크린샷 2024-05-21 094400" src="https://github.com/dawoon1229/Java_practice/assets/164113758/04332959-b9df-429b-93c1-e4a1d1b99146">

## 예외 처리 예제

```java
package javaprac;

public class ExceptionEX2 {

	public static void main(String[] args) {
		// TODO Auto-generated method stub
		String[] names = {"Kim", "Lee", "Park", "Choi"};
		try {
			System.out.printf("0번 인덱스 요소: %s\n", names[0]);
			System.out.printf("4번 인덱스 요소: %s\n", names[4]);
			System.out.printf("3번 인덱스 요소: %s\n", names[3]);
		} catch (ArrayIndexOutOfBoundsException ex) {
			System.out.println("인덱스 접근이 잘못되었습니다.");
		} finally {
			System.out.println("finally 문은 예외 발생과 상관없이 항상 수행됩니다.");
		}
		System.out.println("프로그램이 종료됩니다.");
	}

}

```

1. “0번 인덱스 요소: Kim”이 출력된다.
2. ‘name[4]’에서 ‘ArrayIndexOutOfBoundException’ 예외가 발생한다.
3. 예외가 발생하므로 ‘catch’ 블록으로 이동하고 “인덱스 접근이 잘못되었습니다.”가 출력된다.
4. ‘finally’ 블록이 실행되어 “finally 문은 예외 발생과 상관없이 항상 수행됩니다.”가 출력된다.
5. 마지막으로 “프로그램이 종료됩니다.”가 출력된다.

<img width="231" alt="스크린샷 2024-05-21 170555" src="https://github.com/dawoon1229/Java_practice/assets/164113758/6bd43456-f7ab-49f4-bf4b-ddee012339f2">


### 사용자가 입력한 값을 이용하여 10을 나누는 과정에서 발생할 수 있는 예외를 처리하는 예제

```java
package javaprac;

import java.util.Scanner;

public class ExceptionEx3 {

	public static void main(String[] args) {
		// TODO Auto-generated method stub
		Scanner scanner = new Scanner(System.in);
		try {
			System.out.printf("10을 X로 나누려 한다.\nX의 값을 입력: ");
			String inputStr = scanner.next();
			int inputNum = Integer.parseInt(inputStr);
			
			int result = 10 / inputNum;
			System.out.printf("10 나누기 %d => %d\n", inputNum, result);
		} catch(NumberFormatException ex) {
			System.out.println("정수 변환에 실패하였습니다.");
		} catch(ArithmeticException e) {
			System.out.println("0으로 나눌 수 없습니다.");
		}
		System.out.println("프로그램이 종료됩니다.");
	}

}
```

1. 사용자에게 값을 입력 받는다.
2. 입력 값을 정수로 변환한다.
3. 10을 입력 받은 정수로 나누고 결과를 출력한다.
4. 변환중 ‘NumberFormatException’ 예외가 발생하면 예외 메시지를 출력한다.
5. 나누기중 ‘ArithmeticException’ 예외가 발생하면 예외 메시지를 출력한다.
6. 마지막으로 프로그램 종료 메시지를 출력한다.

<img width="121" alt="스크린샷 2024-05-21 171421" src="https://github.com/dawoon1229/Java_practice/assets/164113758/a75bb884-a6ae-4d5d-b747-cb8534d2f82e">


### 사용자 정의 예외(’MyException’)를 발생시키고 처리하는 예제

```java
package javaprac;

public class MyExceptionTest {

	public static void main(String[] args) {
		// TODO Auto-generated method stub
		try {
			throw new MyException("예외 발생시키기!!");
		} catch(MyException ex) {
			System.out.printf("예외 메시지: %s\n", ex.getMessage());
		}
	}

}

class MyException extends Exception {
	public MyException() {
		super("내가 만든 예외 발생");
	}
	public MyException(String message) {
		super(message);
	}
}
```

1. ‘main’ 메서드에서 ‘try’ 블록을 실행한다.
2. ‘throw new MyException(”예외 발생시키기!!”);’ 로 인해 ‘MyException’이 발생한다.
3. ‘MyException’은 ‘catch’블록으로 전달되고, 예외 메시지 “예외 발생시키기!!”가 출력된다.

이 코드는 사용자 정의 예외를 발생시키고 처리하는 기본적인 예제이다. 예외가 발생하면 ‘catch’블록에서 적절히 처리한다.

<img width="131" alt="스크린샷 2024-05-21 171846" src="https://github.com/dawoon1229/Java_practice/assets/164113758/5f0c7d15-0ec9-4826-a853-10b3e03cf472">

### 메서드 체인에서 예외를 발생시키고 전달하는 방법을 설명하는 예제

```java
package javaprac;

public class ThrowsTest {

	public static void main(String[] args) {
		// TODO Auto-generated method stub
		try {
			aaa();
		} catch (MyException ex) {
			ex.printStackTrace();
		}
	}
	private static void aaa() throws MyException {
		System.out.println("aaa() 메소드가 호출되었습니다.");
		bbb();
	}
	private static void bbb() throws MyException {
		System.out.println("bbb() 메소드가 호출되었습니다.");
		throw new MyException("bbb()에서 예외 발생");
	}
}
class MyException extends Exception {
	public MyException(String message) {
		super(message);
	}
}
```

1. ‘main’ 메서드가 실행되어 ‘aaa’ 메서드를 호출한다.
2. ‘aaa’ 메서드가 호출되었음을 출력하고 ‘bbb’ 메서드를 호출한다.
3. ‘bbb’ 메서드가 호출되었음을 출력하고 ‘MyException’을 발생시킨다.
4. ‘bbb’ 메서드에서 발생한 예외는 ‘aaa’ 메서드로 전달된다.
5. ‘aaa’ 메서드로 전달된 예외는 ‘main’ 메서드로 다시 전달된다.
6. ‘main’ 메서드의 ‘catch’ 블록에서 예외를 잡아 스택 트레이스를 출력한다.


<img width="323" alt="스크린샷 2024-05-21 172350" src="https://github.com/dawoon1229/Java_practice/assets/164113758/f1c2aa73-e9bf-47cd-a205-c431ad0f3f0b">


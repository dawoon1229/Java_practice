## 상속과 업 캐스팅

예를 들어 정사각형(Square), 삼각형(Triangle), 원(Circle) 클래스가 하나의 도형(Shape) 클래스로부터 파생되었다고 가정할 때,

- Square, Triangle, Circle 객체는 부모 클래스인 Shape 타입으로 해석 가능
- 자식 객체는 부모 타입의 배열 또는 ArrayList 등에 담겨 관리될 수 있음
- 하지만 부모 객체를 자식 타입으로 다운 캐스팅(좁은 범위로 해석)할 수는 없음

---

## 메소드 오버라이딩

메소드 오버라이딩(method overriding)은

- 자식 클래스에서 **재정의된 메소드가 수행되는 것**
- 적은 코드로 다양한 동작을 가능케 함

---

## this 키워드

this는 레퍼런스변수이며, 메소드 수행ㅇ의 주체 객체를 가리킴

this 키워드는 메소드 수행 시

- 필드와 입력변수를 구분하거나
- 소괄호를 붙여 또 다른 생성자를 호출하기 위해 사용

---

## protected 키워드

protected는 접근 제한자 중 하나로

- 같은 패키지 내부 또는 상속 관계에 있는 클래스에게 접근을 허용

<img width="364" alt="스크린샷 2024-05-16 175931" src="https://github.com/dawoon1229/Java_practice/assets/164113758/43e37b74-5a63-4346-b3f0-1f7d756c6904">

private의 경우 외부 접근이 불가능해 게터와 세터 메소드를 만들어야 하는데,

- private은 상속 관계에서 사용하기 다소 불편
- protected를 사용하면 이러한 불편을 해소할 수 있음

---

## static 메소드

인터페이스는 static 메소드를 포함할 수 있음

인터페이스의 static 메소드는 재정의될 수 없으며, 반드시 인터페이스명을 통해서 호출해야 함

---
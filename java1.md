### 학생의 점수를 받아서 해당 점수에 따라 학점을 출력하는 프로그램
```Java
package javaprac;

public class java0423 {
	public static void main(String[] args) {
		printGrade(96);
		printGrade(86);
		printGrade(70);
		printGrade(55);
	}
	public static void printGrade(int score) {
		String grade = "";
		if(score >=90) {
			grade = "A";
		}
		else if (score >=80) {
			grade="B";
		}
		else if (score >=70) {
			grade="C";
		} else {
			grade = "F";
		}
		System.out.printf("%d점의 학점: %s\n", score, grade);
	}
}
```
<img width="80" alt="스크린샷 2024-04-23 183540" src="https://github.com/dawoon1229/Java_practice/assets/164113758/a0165195-d4a7-4277-acc8-a2f92b9699d4">

---
### 사용자의 키와 체중을 입력바당서 BMI를 계산하고, 이에 따라 비만도를 판별하여 출력하는 프로그램
```Java
package javaprac;

public class bmi {
	public static void main(String[] args) {
		printBmi (1.76, 81.6);
		
	}
	public static void printBmi(double height, double kg) {
		String result = "";
		double bmi = kg/(height*height);
		if(bmi >=30) {
			result = "비만";
		} else if (bmi >= 25) { 
			result = "과체중";
		} else if(bmi >= 18.5){
			result = "정상";
		} else
			result = "저체중";
		System.out.printf("키: %.2fm \n체중: %.1fkg\nBMI: %.1f\n비만도: %s", height, kg, bmi, result);
	}
}
```
<img width="75" alt="스크린샷 2024-04-23 184001" src="https://github.com/dawoon1229/Java_practice/assets/164113758/5cd766f4-cb75-4f28-92ee-994f461aa2c9">

---
### 주어진 시급과 근무시간에 따라 임금을 계산하고 출력하는 프로그램
```Java
package javaprac;

public class money {
	public static void main(String[] args) {
		printMoney(10000, 160);
		printMoney(15000, 175);
		printMoney(9000, 180);
		printMoney(13000, 190);
	}
	public static void printMoney(int wage, int hours) {
		String result;
	      if (wage < 10000) {
	         result = "[에러] 기본 시급이 1만 원보다 작습니다.";
	      } else if (hours > 180) {
	         result = "[에러] 근무시간이 180시간을 초과하였습니다.";
	      } else if (hours > 160) {
	         int over = (int)((hours - 160) * 1.5 * wage);
	           result = String.format("%d원", 160 * wage + over);
	      } else {
	         result = String.format("%d원", wage * hours);
	      }
	      System.out.printf("%s\n", result);         
	   }

	}
```
<img width="195" alt="스크린샷 2024-04-23 184048" src="https://github.com/dawoon1229/Java_practice/assets/164113758/239afc45-0fd2-4ef6-b4ad-7424d118d7fb">

- 시급이 1만원 미만일 경우: 에러 메세지 출력
- 근무시간이 180시간을 초과할 경우: 에러 메세지 출력
- 근무시간이 160시간을 초과할 경우: 160시간을 기준으로 시급에 따라 임금을 계산하고 출력한뒤, 초과한 시간은 시급의 1.5배를 적용

---
### 입력된 정수가 홀수인지 짝수인지를 판별하여 출력하는 프로그램
```Java
package javaprac;

public class OddOrEven {
	public static void main(String[] args) {
		printResult(13);
		printResult(6);
	}
	public static void printResult(int n) {
		String result = (n%2==0) ? "짝수": "홀수";
		System.out.printf("정수 %d은 %s 입니다.\n", n, result);
	}
}
```
<img width="104" alt="스크린샷 2024-04-23 184128" src="https://github.com/dawoon1229/Java_practice/assets/164113758/d4f33caa-f610-4588-b47f-d4bdbe535f2c">

- 삼항 연산자(’?:’)를 사용하여 ‘n % 2 == 0’인 경우에는 “짝수”를, 그렇지 않은 경우에는 “홀수”를 ‘result’ 변수에 저장한다
---
### 학생의 이름과 수학, 영어 점수를 받아 해당 학생이 받을 장학금 종류를 판별하여 출력하는 프로그램
```Java
package javaprac;

public class Scholarship2 {
	public static void main(String[] args) {
		printScholarship ("Park", 100, 92);
		printScholarship ("Kim", 82, 96);
		printScholarship ("Choi", 82, 88);
	}
	public static void printScholarship(String name, int math, int eng) {
		String result = "";
		if(math>=90 && eng>= 90) {
			result = "전액 장학금!";
		} else if (math >= 90 || eng >= 90) {
			result = "반액 장학금!";
		} else {
			result = "다음 기회에~";
		}
		System.out.printf("%s => %s\n", name, result);
	}
}
```
<img width="115" alt="스크린샷 2024-04-23 184339" src="https://github.com/dawoon1229/Java_practice/assets/164113758/cdfb6a87-6055-46b0-869a-0a832adce84c">

---
### 특정 패턴의 별표를 출력하는 프로그램(주어진 변수를 사용하여 다이아몬드 모양의 별표를 출력하는 패턴을 생성)
```Java
package javaprac;

public class starPattern {
    public static void main(String[] args) {
        int rows = 19; // 출력할 총 줄 수 (별표 개수의 최대값)
        int numStars = 1; // 초기 별표 개수 설정
        int spaces = rows / 2; // 초기 공백 개수 설정

        // 별표 출력
        for (int i = 1; i <= rows; i++) {
            // 가운데 정렬을 위한 공백 출력
            for (int j = 1; j <= spaces; j++) {
                System.out.print(" ");
            }

            // 별표 출력
            for (int k = 1; k <= numStars; k++) {
                System.out.print("*");
            }

            System.out.println(); // 줄바꿈

            // 증가 또는 감소 패턴 설정
            if (i < rows / 2 + 1) {
                numStars += 2;
                spaces--;
            } else {
                numStars -= 2;
                spaces++;
            }
        }
    }
}
```
<img width="141" alt="스크린샷 2024-04-23 184504" src="https://github.com/dawoon1229/Java_practice/assets/164113758/2f36c54a-85f4-4970-b014-6d4dd7d49cd6">

- ‘rows’ 변수는 출력할 총 줄 수를 나타낸다. 이 값은 홀수로 설정되어야 하며, 별표 개수의 최대값이 된다.
- ‘numStars’ 변수는 초기 별표 개수를 설정한다. 처음에는 한 줄에 하나씩 증가하면서 출력되며, 중간에는 감소하면서 출력된다.
- ‘spaces’ 변수는 초기 공백 개수를 설정한다. 별표를 출력하기 전에 각 줄마다 적절한 공백을 출력하여 가운데 정렬을 구현한다.
- ‘for’ 반복문을 사용하여 별표를 출력한다.
    - 첫 번째 반복문은 전체 줄 수인 ‘rows’만큼 반복하며, 한 줄씩 별표를 출력한다.
    - 두 번째 반복문은 각 줄마다 적절한 공백을 출력하기 위해 사용된다.
    - 세 번째 반복문은 해당 줄에 출력할 별표를 출력한다.
- 별표 출력 후에는 줄바꿈을 수행하여 다음 줄로 넘어간다.
- ‘if-else’ 구문을 사용하여 별표 개수와 공백 개수의 증가 또는 감소 패턴을 설정한다. 이 패턴에 따라 다이아몬드 모양의 별표가 출력된다.
---
### 교통 신호등의 색을 받아와서 해당하는 색에 따라 어떤 동작을 수행하는 프로그램
```Java
package javaprac;

public class TrafficLight {
	public static void main(String[] args) {
		light("RED");
		light("YELLOW");
		light("GREEN");
		light("BLUE");
	}
	public static void light(String color) {
		switch(color) {
		case "RED" :
			System.out.println("빨간불이 켜집니다.");
			break;
		case "YELLOW" :
			System.out.println("노란불이 켜집니다.");
			break;
		case "GREEN" :
			System.out.println("초록불이 켜집니다.");
			break;
		default:
			System.out.printf("에러, 잘못된 색 입력: %s\n", color);
		}
	}
}
```

<img width="133" alt="스크린샷 2024-04-23 184930" src="https://github.com/dawoon1229/Java_practice/assets/164113758/062ed894-1351-4a5d-8c5f-1fd5eb4ded02">

---


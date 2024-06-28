---
title: codingTest 문제(기본개념, DB, 알고리즘)_2
categories: codingTest
tags:
  - codingTest
  - java
---
------------------------------------------
**기본 개념**



1.**상수와 리터럴**:
```java
// 다음 코드의 출력 결과는 무엇인가?
public class Main {
    public static void main(String[] args) {
        final int x = 10;
        x = 20;
        System.out.println(x);
    }
}
```
**정답**: 컴파일 오류

**풀이**: x는 final로 선언되어 값을 변경할 수 없습니다. 따라서 x = 20;에서 컴파일 오류가 발생합니다.



2.**메서드 오버로딩**:
```java
// 두 메서드가 오버로딩되는 코드를 작성하시오.
public class Main {
    public int add(int a, int b) {
        return a + b;
    }

    public double add(double a, double b) {
        return a + b;
    }

    public static void main(String[] args) {
        Main main = new Main();
        System.out.println(main.add(5, 3));       // 정수 덧셈
        System.out.println(main.add(5.0, 3.0));   // 실수 덧셈
    }
}
```
**풀이**: 메서드 이름은 같지만 매개변수의 타입이 다르면 메서드 오버로딩이 됩니다. add(int a, int b)와 add(double a, double b)는 오버로딩된 메서드입니다.



3.**추상 클래스**:
```java
// 추상 클래스를 정의하고 이를 상속하는 클래스를 작성하시오.
abstract class Shape {
    abstract double area();
}

class Circle extends Shape {
    double radius;
    Circle(double radius) {
        this.radius = radius;
    }

    @Override
    double area() {
        return Math.PI * radius * radius;
    }
}

public class Main {
    public static void main(String[] args) {
        Circle circle = new Circle(5.0);
        System.out.println(circle.area());
    }
}
```
**풀이**: Shape 추상 클래스와 이를 상속하는 Circle 클래스에서 area 메서드를 구현합니다.



4.**인터페이스 상속**:
```java
// 다음 인터페이스를 상속하는 클래스를 작성하시오.
interface Printable {
    void print();
}

class Document implements Printable {
    @Override
    public void print() {
        System.out.println("Document is printing");
    }
}

public class Main {
    public static void main(String[] args) {
        Document doc = new Document();
        doc.print();
    }
}
```
**풀이**: Printable 인터페이스를 구현한 Document 클래스에서 print 메서드를 구현합니다.



5.**스레드**:
```java
// 두 개의 스레드를 생성하여 각각 "Thread 1"과 "Thread 2"를 출력하는 코드를 작성하시오.
class MyThread extends Thread {
    private String name;
    MyThread(String name) {
        this.name = name;
    }

    public void run() {
        System.out.println(name);
    }
}

public class Main {
    public static void main(String[] args) {
        MyThread t1 = new MyThread("Thread 1");
        MyThread t2 = new MyThread("Thread 2");
        t1.start();
        t2.start();
    }
}
```
**풀이**: MyThread 클래스를 Thread 클래스를 상속하여 생성하고, run 메서드를 오버라이드하여 스레드에서 실행될 코드를 작성합니다.



**데이터베이스 (DB)**



1.**INNER JOIN**:
```sql
-- Employees 테이블과 Departments 테이블을 INNER JOIN하여 직원의 이름과 부서 이름을 조회하시오.
SELECT Employees.name, Departments.department_name
FROM Employees
INNER JOIN Departments ON Employees.department_id = Departments.id;
```
**풀이**: INNER JOIN을 사용하여 Employees와 Departments 테이블을 연결하고 필요한 열을 조회합니다.


2.**LEFT JOIN**:
```sql
-- Employees 테이블과 Departments 테이블을 LEFT JOIN하여 모든 직원과 해당 부서 이름을 조회하시오. 부서가 없는 직원도 포함합니다.
SELECT Employees.name, Departments.department_name
FROM Employees
LEFT JOIN Departments ON Employees.department_id = Departments.id;
```
**풀이**: LEFT JOIN을 사용하여 Employees 테이블의 모든 행과 일치하는 Departments 테이블의 행을 조회합니다. 부서가 없는 직원도 포함됩니다.


3.**그룹화와 집계 함수**
```sql
-- Employees 테이블에서 부서별 최대 급여를 조회하시오.
SELECT department, MAX(salary) as max_salary
FROM Employees
GROUP BY department;
```
**풀이**: GROUP BY와 MAX 함수를 사용하여 각 부서별 최대 급여를 계산합니다.


4.**HAVING 절**:
```sql
-- Employees 테이블에서 직원이 2명 이상인 부서의 평균 급여를 조회하시오.
SELECT department, AVG(salary) as avg_salary
FROM Employees
GROUP BY department
HAVING COUNT(*) >= 2;
```
**풀이**: HAVING 절을 사용하여 직원이 2명 이상인 부서만 필터링하여 평균 급여를 계산합니다.


5.**서브쿼리와 IN 연산자**:
```sql
-- 급여가 부서 평균 급여보다 높은 직원의 이름과 급여를 조회하시오.
SELECT name, salary
FROM Employees
WHERE salary > (
    SELECT AVG(salary)
    FROM Employees AS e2
    WHERE e2.department = Employees.department
);
```
**풀이**: 서브쿼리를 사용하여 부서별 평균 급여를 계산하고, 이를 이용하여 급여가 부서 평균 급여보다 높은 직원들을 조회합니다.



**알고리즘**



1.**팰린드롬 검사**:
```java
// 주어진 문자열이 팰린드롬인지 확인하는 함수를 작성하시오.
public boolean isPalindrome(String s) {
    int left = 0, right = s.length() - 1;
    while (left < right) {
        if (s.charAt(left) != s.charAt(right)) {
            return false;
        }
        left++;
        right--;
    }
    return true;
}
```
**풀이**: 문자열의 시작과 끝에서부터 문자를 비교하여 팰린드롬 여부를 확인합니다.



2.**두 배열의 교집합**:
```java
// 두 배열의 교집합을 반환하는 함수를 작성하시오.
public int[] intersection(int[] nums1, int[] nums2) {
    Set<Integer> set1 = new HashSet<>();
    for (int num : nums1) {
        set1.add(num);
    }
    Set<Integer> intersection = new HashSet<>();
    for (int num : nums2) {
        if (set1.contains(num)) {
            intersection.add(num);
        }
    }
    int[] result = new int[intersection.size()];
    int i = 0;
    for (int num : intersection) {
        result[i++] = num;
    }
    return result;
}
```
**풀이**: 두 배열의 요소를 집합으로 변환하여 교집합을 구하고, 이를 배열로 반환합니다.



3.**행렬의 회전**:
```java
// 주어진 NxN 행렬을 시계방향으로 90도 회전하는 함수를 작성하시오.
public void rotate(int[][] matrix) {
    int n = matrix.length;
    for (int i = 0; i < n / 2; i++) {
        for (int j = i; j < n - i - 1; j++) {
            int temp = matrix[i][j];
            matrix[i][j] = matrix[n - j - 1][i];
            matrix[n - j - 1][i] = matrix[n - i - 1][n - j - 1];
            matrix[n - i - 1][n - j - 1] = matrix[j][n - i - 1];
            matrix[j][n - i - 1] = temp;
        }
    }
}
```
**풀이**: 네 개의 값을 교환하여 행렬을 시계방향으로 90도 회전시킵니다.



4.**중복 문자 제거**:
```java
// 주어진 문자열에서 중복 문자를 제거하고, 각 문자가 처음 등장하는 순서대로 나열하는 함수를 작성하시오.
public String removeDuplicates(String s) {
    Set<Character> seen = new HashSet<>();
    StringBuilder sb = new StringBuilder();
    for (char c : s.toCharArray()) {
        if (!seen.contains(c)) {
            seen.add(c);
            sb.append(c);
        }
    }
  }
```
**풀이**: 집합을 사용하여 중복 문자를 필터링하고, 처음 등장하는 순서대로 문자열을 작성합니다.



5.**올바른 괄호**:
```java
// 주어진 문자열이 올바른 괄호 문자열인지 확인하는 함수를 작성하시오.
public boolean isValid(String s) {
    Stack<Character> stack = new Stack<>();
    for (char c : s.toCharArray()) {
        if (c == '(') {
            stack.push(c);
        } else if (c == ')') {
            if (stack.isEmpty() || stack.pop() != '(') {
                return false;
            }
        }
    }
    return stack.isEmpty();
}
```
**풀이**: 스택을 사용하여 괄호의 짝을 확인하고, 올바른 괄호 문자열인지 검사합니다.
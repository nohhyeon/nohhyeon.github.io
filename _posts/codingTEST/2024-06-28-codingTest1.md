---
title: codingTest 문제(기본개념, DB, 알고리즘)_1
categories: codingTest
tags:
  - codingTest
  - java
---
------------------------------------------
**1. 기본 개념**



1. **변수와 자료형**:
```java
// 다음 코드의 출력 결과는 무엇인가?
public class Main {
    public static void main(String[] args) {
        int a = 5;
        double b = 4.5;
        double c = a + b;
        System.out.println(c);
    }
}
```
**정답**: 9.5

**풀이**: int 타입 변수 a와 double 타입 변수 b를 더할 때 a가 double로 자동 변환되어 결과는 double 타입인 9.5가 됩니다.


2. **조건문**:
```java
// 다음 조건문이 참이 되도록 x에 어떤 값을 할당해야 하는가?
int x = ???;
if (x > 10 && x < 20) {
    System.out.println("x is between 10 and 20");
}
```
**정답**: 11 (또는 10보다 크고 20보다 작은 임의의 값)

**풀이**: x는 10보다 크고 20보다 작아야 하므로, 예를 들어 11, 15, 19 등이 가능합니다.


3. **반복문**:
```java
// 1부터 100까지의 합을 계산하는 코드를 작성하시오.
public class Main {
    public static void main(String[] args) {
        int sum = 0;
        for (int i = 1; i <= 100; i++) {
            sum += i;
        }
        System.out.println(sum);
    }
}
```
**정답**: 5050

**풀이**: for 루프를 사용하여 1부터 100까지의 숫자를 순회하며 sum에 더해주면 됩니다. 최종적으로 sum에는 1부터 100까지의 합이 저장되어 5050이 출력됩니다.


4. **함수**:
```java
// 두 정수를 받아서 더한 결과를 반환하는 함수를 작성하시오.
public int add(int a, int b) {
    return a + b;
}
```
**풀이**: 함수 add는 두 개의 int 값을 입력받아 그 합을 반환합니다.


5. **클래스와 객체**:
```java
// 다음 클래스의 인스턴스를 생성하고 메서드를 호출하시오.
class Dog {
    String name;
    void bark() {
        System.out.println(name + " says: Woof!");
    }
}

public class Main {
    public static void main(String[] args) {
        Dog myDog = new Dog();
        myDog.name = "Buddy";
        myDog.bark();
    }
}
```
**정답**: Buddy says: Woof!

**풀이**: Dog 클래스의 인스턴스를 생성하고 name을 “Buddy”로 설정한 후 bark 메서드를 호출하면 “Buddy says: Woof!“가 출력됩니다.


6. **상속**:
```java
// 다음 상속 관계에서 자식 클래스의 생성자를 작성하시오.
class Animal {
    String name;
    Animal(String name) {
        this.name = name;
    }
}

class Dog extends Animal {
    Dog(String name) {
        super(name);
    }
}
```
**풀이**: Dog 클래스의 생성자는 Animal 클래스의 생성자를 호출하기 위해 super(name)을 사용합니다.


7. **다형성**:
```java
// 다음 상속 관계에서 자식 클래스의 생성자를 작성하시오.
class Animal {
    String name;
    Animal(String name) {
        this.name = name;
    }
}

class Dog extends Animal {
    Dog(String name) {
        super(name);
    }
}
```
**정답**: Bark Meow

**풀이**: Animal 인터페이스를 구현한 Dog와 Cat 클래스의 인스턴스를 생성하고 각각의 makeSound 메서드를 호출하면, 다형성에 의해 적절한 메서드가 실행됩니다.


8. **캡슐화**:
```java
// 다음 코드를 완성하시오.
interface Animal {
    void makeSound();
}

class Dog implements Animal {
    public void makeSound() {
        System.out.println("Bark");
    }
}

class Cat implements Animal {
    public void makeSound() {
        System.out.println("Meow");
    }
}

public class Main {
    public static void main(String[] args) {
        Animal myDog = new Dog();
        Animal myCat = new Cat();
        myDog.makeSound();
        myCat.makeSound();
    }
}
```
**풀이**: x 변수를 private으로 선언하고, getter와 setter 메서드를 통해 접근하도록 하여 캡슐화합니다.


9. **인터페이스**:
```java
// 다음 인터페이스를 구현하는 클래스를 작성하시오.
interface Animal {
    void eat();
    void sleep();
}

class Dog implements Animal {
    public void eat() {
        System.out.println("Dog is eating");
    }

    public void sleep() {
        System.out.println("Dog is sleeping");
    }
}
```
**풀이**: Animal 인터페이스를 구현한 Dog 클래스는 eat와 sleep 메서드를 구현합니다.


10. **예외 처리**:
```java
// 다음 코드에서 발생하는 예외를 처리하시오.
public class Main {
    public static void main(String[] args) {
        try {
            int result = 10 / 0;
        } catch (ArithmeticException e) {
            System.out.println("Cannot divide by zero");
        }
    }
}
```
**정답**: Cannot divide by zero

**풀이**: try-catch 블록을 사용하여 ArithmeticException을 처리하고, 0으로 나누려 할 때 예외 메시지를 출력합니다.



**2. 데이터베이스 (DB)**

  

1. **SQL 기본**:
```sql
-- Employees 테이블에서 모든 직원의 이름과 급여를 조회하시오.
SELECT name, salary FROM Employees;
```
**풀이**: SELECT 문을 사용하여 Employees 테이블에서 name과 salary 열을 조회합니다.


2. **조건 조회**:
```sql
-- Employees 테이블에서 부서가 'Sales'인 직원의 이름과 급여를 조회하시오.
SELECT name, salary
FROM Employees
WHERE department = 'Sales';
```
**풀이**: WHERE 절을 사용하여 department가 ‘Sales’인 행만 조회합니다.


3. **정렬**:
```sql
-- Employees 테이블에서 급여가 높은 순으로 직원의 이름과 급여를 조회하시오.
SELECT name, salary
FROM Employees
ORDER BY salary DESC;
```
**풀이**: ORDER BY 절을 사용하여 salary를 내림차순으로 정렬합니다.


4. **집계 함수**:
```sql
-- Employees 테이블에서 각 부서의 평균 급여를 조회하시오.
SELECT department, AVG(salary) as avg_salary
FROM Employees
GROUP BY department;
```
**풀이**: GROUP BY 절을 사용하여 department별로 그룹화하고, AVG 함수를 사용하여 평균 급여를 계산합니다.

  
5. **JOIN**:
```sql
-- Employees 테이블과 Departments 테이블을 JOIN하여 직원의 이름과 부서 이름을 조회하시오.
SELECT Employees.name, Departments.department_name
FROM Employees
JOIN Departments ON Employees.department_id = Departments.id;
```
**풀이**: JOIN을 사용하여 Employees 테이블과 Departments 테이블을 department_id와 id를 기준으로 연결합니다.


6. **서브쿼리**:
```sql
-- 급여가 전체 평균 급여보다 높은 직원의 이름과 급여를 조회하시오.
SELECT name, salary
FROM Employees
WHERE salary > (SELECT AVG(salary) FROM Employees);
```
**풀이**: 서브쿼리를 사용하여 전체 평균 급여를 계산하고, 이를 기준으로 급여가 더 높은 직원들을 조회합니다.


7. **데이터 삽입**:
```sql
-- Employees 테이블에 새로운 직원을 추가하시오.
INSERT INTO Employees (name, department, salary)
VALUES ('John Doe', 'Engineering', 75000);
```
**풀이**: INSERT INTO 문을 사용하여 Employees 테이블에 새로운 행을 추가합니다.


8. **데이터 갱신**:
```sql
-- Employees 테이블에서 'John Doe'의 급여를 80000으로 갱신하시오.
UPDATE Employees
SET salary = 80000
WHERE name = 'John Doe';
```
**풀이**: UPDATE 문을 사용하여 name이 ‘John Doe’인 행의 salary를 80000으로 갱신합니다.


9. **데이터 삭제**:
```sql
-- Employees 테이블에서 부서가 'HR'인 모든 직원을 삭제하시오.
DELETE FROM Employees
WHERE department = 'HR';
```
**풀이**: DELETE FROM 문을 사용하여 department가 ‘HR’인 모든 행을 삭제합니다.

  
10. **테이블 생성**:
```sql
-- 새 테이블 Departments를 생성하고, 열로 id, department_name, manager_id를 포함하시오.
CREATE TABLE Departments (
    id INT PRIMARY KEY,
    department_name VARCHAR(50),
    manager_id INT
);
```
**풀이**: CREATE TABLE 문을 사용하여 새로운 테이블 Departments를 생성하고, id, department_name, manager_id 열을 포함시킵니다.

  

**3. 알고리즘**

  

1. **배열의 합**:
```java
// 주어진 정수 배열의 합을 구하는 함수를 작성하시오.
public int sumArray(int[] array) {
    int sum = 0;
    for (int num : array) {
        sum += num;
    }
    return sum;
}
```
**풀이**: 배열을 순회하면서 각 요소를 더하여 sum에 저장하고, 최종적으로 sum을 반환합니다.


2. **문자열 뒤집기**:
```java
// 주어진 문자열을 뒤집는 함수를 작성하시오.
public String reverseString(String str) {
    return new StringBuilder(str).reverse().toString();
}
```
**풀이**: StringBuilder를 사용하여 문자열을 뒤집고, 다시 문자열로 변환하여 반환합니다.

  
3. **피보나치 수열**:
```java
// n번째 피보나치 수를 구하는 재귀함수를 작성하시오.
public int fibonacci(int n) {
    if (n <= 1) {
        return n;
    }
    return fibonacci(n - 1) + fibonacci(n - 2);
}
```
**풀이**: 피보나치 수열의 재귀적 정의를 그대로 구현하여 n번째 피보나치 수를 반환합니다.

  
4. **이진 탐색**:
```java
// 정렬된 배열에서 특정 값을 찾는 이진 탐색 함수를 작성하시오.
public int binarySearch(int[] array, int target) {
    int left = 0, right = array.length - 1;
    while (left <= right) {
        int mid = left + (right - left) / 2;
        if (array[mid] == target) {
            return mid;
        }
        if (array[mid] < target) {
            left = mid + 1;
        } else {
            right = mid - 1;
        }
    }
    return -1; // 찾지 못한 경우
}
```
**풀이**: 이진 탐색 알고리즘을 사용하여 정렬된 배열에서 target 값을 찾고, 인덱스를 반환합니다. 찾지 못하면 -1을 반환합니다.


5. **정렬**:
```java
// 버블 정렬을 사용하여 정수 배열을 정렬하는 함수를 작성하시오.
public void bubbleSort(int[] array) {
    int n = array.length;
    for (int i = 0; i < n - 1; i++) {
        for (int j = 0; j < n - 1 - i; j++) {
            if (array[j] > array[j + 1]) {
                int temp = array[j];
                array[j] = array[j + 1];
                array[j + 1] = temp;
            }
        }
    }
}
```
**풀이**: 버블 정렬 알고리즘을 사용하여 배열을 정렬합니다. 배열의 각 요소를 순회하며 인접한 두 요소를 비교하고, 필요시 교환합니다.

  
6. **최소 공배수**:
```java
// 두 수의 최소 공배수를 구하는 함수를 작성하시오.
public int lcm(int a, int b) {
    return (a * b) / gcd(a, b);
}

public int gcd(int a, int b) {
    if (b == 0) {
        return a;
    }
    return gcd(b, a % b);
}
```
**풀이**: gcd 함수를 사용하여 최대 공약수를 구한 후, 이를 이용하여 최소 공배수를 계산합니다.

  
7. **배낭 문제**:
```java
// 0/1 배낭 문제를 해결하는 동적 계획법 알고리즘을 작성하시오.
public int knapsack(int[] weights, int[] values, int W) {
    int n = weights.length;
    int[][] dp = new int[n + 1][W + 1];
    for (int i = 1; i <= n; i++) {
        for (int w = 0; w <= W; w++) {
            if (weights[i - 1] <= w) {
                dp[i][w] = Math.max(dp[i - 1][w], dp[i - 1][w - weights[i - 1]] + values[i - 1]);
            } else {
                dp[i][w] = dp[i - 1][w];
            }
        }
    }
    return dp[n][W];
}
```
**풀이**: 동적 계획법을 사용하여 dp 배열을 채워나가며 배낭의 최대 가치를 계산합니다.


8. **그래프 탐색 - DFS**:
```java
// 깊이 우선 탐색(DFS) 알고리즘을 작성하시오.
public void dfs(int v, boolean[] visited, List<List<Integer>> adjList) {
    visited[v] = true;
    System.out.print(v + " ");
    for (int adj : adjList.get(v)) {
        if (!visited[adj]) {
            dfs(adj, visited, adjList);
        }
    }
}
```
**풀이**: 재귀 호출을 사용하여 visited 배열을 업데이트하며 그래프를 깊이 우선 탐색합니다.
 

9. **그래프 탐색 - BFS**:
```java
// 너비 우선 탐색(BFS) 알고리즘을 작성하시오.
public void bfs(int start, List<List<Integer>> adjList) {
    boolean[] visited = new boolean[adjList.size()];
    Queue<Integer> queue = new LinkedList<>();
    visited[start] = true;
    queue.add(start);
    while (!queue.isEmpty()) {
        int v = queue.poll();
        System.out.print(v + " ");
        for (int adj : adjList.get(v)) {
            if (!visited[adj]) {
                visited[adj] = true;
                queue.add(adj);
            }
        }
    }
}
```
**풀이**: 큐를 사용하여 visited 배열을 업데이트하며 그래프를 너비 우선 탐색합니다.


10. **최단 경로 알고리즘**:
```java
// 다익스트라 알고리즘을 사용하여 단일 출발지 최단 경로를 구하는 코드를 작성하시오.
public int[] dijkstra(int[][] graph, int src) {
    int V = graph.length;
    int[] dist = new int[V];
    boolean[] sptSet = new boolean[V];

    Arrays.fill(dist, Integer.MAX_VALUE);
    dist[src] = 0;

    for (int count = 0; count < V - 1; count++) {
        int u = minDistance(dist, sptSet);
        sptSet[u] = true;
        for (int v = 0; v < V; v++) {
            if (!sptSet[v] && graph[u][v] != 0 && 
                dist[u] != Integer.MAX_VALUE && dist[u] + graph[u][v] < dist[v]) {
                dist[v] = dist[u] + graph[u][v];
            }
        }
    }
    return dist;
}

private int minDistance(int[] dist, boolean[] sptSet) {
    int min = Integer.MAX_VALUE, minIndex = -1;
    for (int v = 0; v < dist.length; v++) {
        if (!sptSet[v] && dist[v] < min) {
            min = dist[v];
            minIndex = v;
        }
    }
    return minIndex;
}
```
**풀이**: 다익스트라 알고리즘을 사용하여 최단 경로를 계산합니다. dist 배열을 사용하여 출발점에서 각 정점까지의 최단 거리를 기록하고, sptSet 배열을 사용하여 최단 경로 트리에 포함된 정점을 관리합니다.
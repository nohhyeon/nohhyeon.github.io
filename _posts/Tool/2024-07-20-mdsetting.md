---

title : "마크다운 세팅"
categories : information
tag : setting

---
마크다운 세팅

## 마크다운 문법 살펴보기

SBB에 마크다운을 적용하기 전에 먼저 마크다운의 문법을 몇 가지 알아보자.

### 목록 표시하기

SBB에서 내용에 여러 내용을 나열한 목록을 표시하기 위해 다음과 같이 작성했다고 가정해 보자.

> 아직은 SBB에 마크다운을 적용하지 않았으므로 그저 문법을 이해하기 위해 눈으로만 보고 넘어가자.

```plaintext
* 자바
* 스프링부트
* 알고리즘
```

이 문자열을 마크다운 해석기가 HTML로 변환하면 실제 화면에서는 다음과 같이 보인다.

- 자바
- 스프링부트
- 알고리즘

만약 순서가 있는 목록을 표시하고 싶다면 다음과 같이 작성한다.

```plaintext
1. 하나
1. 둘
1. 셋
```

그러면 마크다운 해석기는 다음과 같은 결과를 출력한다.

1. 하나
2. 둘
3. 셋

### 강조 표시하기

작성한 글자에 강조 표시를 하려면 강조할 텍스트 양쪽에 `**`를 넣어 감싸 보자.

```plaintext
스프링부트는 **자바**로 만들어진 웹 프레임워크이다.
```

출력 결과는 다음과 같다.

변환결과스프링부트는 **자바**로 만들어진 웹 프레임워크이다.

### 링크 표시하기

질문이나 답변 내용에 링크를 추가하고 싶다면 다음과 같이 `[링크명](링크주소)` 문법을 적용하여 생성할 수 있다.

```plaintext
스프링 홈페이지는 [https://spring.io](https://spring.io) 입니다.
```

출력 결과는 다음과 같다.

변환결과스프링 홈페이지는 [https://spring.io](https://spring.io/) 입니다.

### 소스 코드 표시하기

소스 코드는 백쿼트 ` 3개를 연이어 붙여 위아래로 감싸면 생성할 수 있다.

> 백쿼트는 백틱이라고도 한다.

```
package com.mysite.sbb;

import org.springframework.stereotype.Controller;
import org.springframework.web.bind.annotation.RequestMapping;
import org.springframework.web.bind.annotation.ResponseBody;

@Controller
public class HelloController {
    @GetMapping("/hello")
    @ResponseBody
    public String hello() {
        return "Hello Spring Boot Board";
    }
}
```

출력 결과는 다음과 같다.

변환결과

```java
package com.mysite.sbb;

import org.springframework.stereotype.Controller;
import org.springframework.web.bind.annotation.RequestMapping;
import org.springframework.web.bind.annotation.ResponseBody;

@Controller
public class HelloController {
    @GetMapping("/hello")
    @ResponseBody
    public String hello() {
        return "Hello Spring Boot Board";
    }
}
```

### 인용 표시하기

질문이나 답변 내용에서 어떤 문장을 인용했다는 표시를 하려면 다음과 같이 `>`를 문장 맨 앞에 입력하고 1칸 띄어쓰기를 한 다음 인용구를 입력한다.

```plaintext
> 마크다운은 Github에서 사용하는 글쓰기 도구이다.
```

출력 결과는 다음과 같을 것이다.

변환결과

> 마크다운은 Github에서 사용하는 글쓰기 도구이다.

사용자 입장에서 이와 같이 마크다운 문법을 사용하면 질문이나 답변을 남길 때 간단하면서 가독성 좋은 글을 작성할 수 있다. 이보다 더 많은 마크다운 문법이 있지만 여기서는 이 정도만 알고 넘어가자.

> 마크다운을 더 자세히 알고 싶다면 [https://www.markdownguide.org/getting-started/](https://www.markdownguide.org/getting-started/)을 방문해 보자.

## 마크다운 설치하기

SBB에 마크다운 기능을 추가하려면 마크다운 라이브러리를 설치해야 한다. 다른 라이브러리를 설치할 때와 마찬가지로 다음과 같이 `build.gradle` 파일을 수정하여 마크다운을 설치하자.

`[파일명:build.gradle]`

```plaintext
(... 생략 ...)
dependencies {
    (... 생략 ...)
    implementation 'org.commonmark:commonmark:0.21.0'
}
(... 생략 ...)
```

[Gradle → Refresh Gradle Project]를 클릭하여 변경 사항을 적용하면 0.21.0 버전의 commonmark 라이브러리가 설치된다. 로컬 서버도 한번 재시작하자.

점프 투 스프링부트**commonmark는 버전 정보를 왜 입력할까?**

지금까지 `build.gradle` 파일에 필요한 라이브러리를 등록할 때 버전을 명시하지 않았다. 하지만 commonmark는 이와 같이 0.21.0이라는 버전을 지정해야 한다. 왜냐하면 스프링 부트의 라이브러리 관리 방식 때문이다. 스프링 부트가 내부적으로 관리하는 라이브러리에 포함되면 버전 정보가 필요 없고 포함되지 않으면 버전 정보가 필요하다. 즉, commonmark는 스프링 부트가 내부적으로 관리하는 라이브러리가 아니어서 이와 같이 명시하는 것이다. 참고로, 스프링 부트가 관리하는 라이브러리의 경우 버전 정보를 명시하지 않으면 스프링 부트가 가장 궁합이 잘 맞는 버전을 자동으로 선택한다. 따라서 라이브러리들의 호환성을 생각한다면 버전 정보는 따로 입력하지 않는 편이 좋다.

## 마크다운 컴포넌트 작성하기

라이브러리 설치를 마쳤으니 이제 질문이나 답변의 ‘내용’ 부분에 마크다운을 적용해 보자. 사실 컨트롤러에서 질문이나 답변을 조회한 후에 마크다운 라이브러리를 적용하면 변환된 HTML을 얻을 수 있다. 하지만 여기서는 개별적으로 사용하기보다 좀 더 범용적으로 사용할수 있는 마크다운 컴포넌트를 만들고 타임리프 템플릿에서 작성한 마크다운 컴포넌트를 사용하는 방법을 알아보자.

그러기 위해 먼저 다음과 같이 CommonUtil이라는 이름으로 마크다운 컴포넌트를 작성해 보자. `com.mysite.sbb` 패키지에 `CommonUtil.java`를 만들어 보자.

`[파일명:CommonUtil.java]`

```java
package com.mysite.sbb;

import org.commonmark.node.Node;
import org.commonmark.parser.Parser;
import org.commonmark.renderer.html.HtmlRenderer;
import org.springframework.stereotype.Component;

@Component
public class CommonUtil {
    public String markdown(String markdown) {
        Parser parser = Parser.builder().build();
        Node document = parser.parse(markdown);
        HtmlRenderer renderer = HtmlRenderer.builder().build();
        return renderer.render(document);
    }
}
```

`@Component` 애너테이션을 사용하여 CommonUtil 클래스를 생성했다. 이렇게 하면 이제 CommonUtil 클래스는 스프링 부트가 관리하는 빈으로 등록된다. 이렇게 빈으로 등록된 컴포넌트는 템플릿에서 사용할 수 있다.

CommonUtil 클래스에는 markdown 메서드를 생성했다. markdown 메서드는 마크다운 텍스트를 HTML 문서로 변환하여 리턴한다. 즉, 마크다운 문법이 적용된 일반 텍스트를 변환된 HTML로 리턴한다.

## 템플릿에 마크다운 적용하기

마크다운 문법은 질문 상세 페이지에서 사용하므로 다음과 같이 `question_detail.html`에 코드를 추가해 보자.

`[파일명:/templates/question_detail.html]`

```html
(... 생략 ...)
<!-- 질문 -->
<h2 class="border-bottom py-2" th:text="${question.subject}"></h2>
<div class="card my-3">
    <div class="card-body">
        <div class="card-text" th:utext="${@commonUtil.markdown(question.content)}"></div>
        <div class="d-flex justify-content-end">
        (... 생략 ...)

<!-- 답변 반복 시작 -->
<div class="card my-3" th:each="answer : ${question.answerList}">
    <a th:id="|answer_${answer.id}|"></a>
    <div class="card-body">
        <div class="card-text" th:utext="${@commonUtil.markdown(answer.content)}"></div>
        <div class="d-flex justify-content-end">
        (... 생략 ...)
```

질문과 답변 영역에 마크다운을 각각 적용하기 위해 줄 바꿈을 표시하려고 사용한 기존의 `style="white-space: pre-line;"` 스타일을 삭제하고 `${@commonUtil.markdown(question.content)}`와 같이 마크다운 컴포넌트를 적용했다. 이때 `th:text`가 아닌 `th:utext`를 사용한 부분에 주의하자. 만약 `th:utext` 대신 `th:text`를 사용할 경우 HTML의 태그들이 이스케이프(escape) 처리되어 화면에 그대로 보일 것이다. 마크다운으로 변환된 HTML 문서를 제대로 표시하려면 이스케이프 처리를 하지 않고 출력하는 `th:utext`를 사용해야 한다.

## 마크다운 확인하기

질문 또는 답변을 마크다운 문법으로 작성하면 브라우저에서 어떻게 보이는지 확인해 보자.

**1)** 다음과 같이 질문 내용에 마크다운 문법을 적용하여 등록해 보자.

![](https://wikidocs.net/images/page/225222/image299_1.png)

**2)** 그러면 다음과 같이 마크다운 문법이 적용된 것을 확인할 수 있을 것이다.

![](https://wikidocs.net/images/page/225222/image299_2.png)

이렇게 마크다운을 적용하니 게시글이 훨씬 보기 좋아졌다!

>
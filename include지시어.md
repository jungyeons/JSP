
# JSP에서의 include 지시어 및 날짜 처리

이번 예제는 JSP에서 `include` 지시어와 날짜 관련 클래스를 사용하는 방법을 다룹니다. 주요 핵심 개념을 정리하여 설명하겠습니다.

## 1. `<%@ page %>` 지시어
JSP 파일에서 `<%@ page %>` 지시어는 페이지의 설정을 정의합니다. 여기서는 `language`, `contentType`, `pageEncoding` 속성을 사용하고 있습니다.

### 예시
```jsp
<%@ page language="java" contentType="text/html; charset=UTF-8" pageEncoding="UTF-8" %>
```
- `language="java"`: JSP에서 사용하는 프로그래밍 언어를 지정합니다. 기본적으로 Java로 설정됩니다.
- `contentType="text/html; charset=UTF-8"`: 응답의 콘텐츠 타입과 문자 인코딩을 설정합니다.
- `pageEncoding="UTF-8"`: JSP 파일 자체의 문자 인코딩을 설정합니다.

## 2. `<%@ page import %>` 지시어
`import` 지시어는 JSP 페이지에서 사용할 Java 클래스를 임포트하는 데 사용됩니다.

### 예시
```jsp
<%@ page import="java.time.LocalDateTime" %>
<%@ page import="java.time.LocalDate" %>
```
- `java.time.LocalDate`와 `java.time.LocalDateTime` 클래스를 임포트하여 날짜와 시간을 다루기 위한 객체를 사용할 수 있습니다.

## 3. 날짜 처리: `LocalDate`와 `LocalDateTime`
- `LocalDate`: 날짜 정보를 다루는 클래스입니다. 시간 정보는 포함되지 않습니다.
- `LocalDateTime`: 날짜와 시간 정보를 모두 포함하는 클래스입니다.

### 예시
```jsp
<%
LocalDate today = LocalDate.now();
LocalDateTime tomorrow = LocalDateTime.now().plusDays(1);
%>
```
- `LocalDate.now()`는 현재 날짜를 반환합니다.
- `LocalDateTime.now().plusDays(1)`은 현재 시간에서 하루를 더한 날짜와 시간을 반환합니다.

## 4. `<%@ include %>` 지시어
`<%@ include %>` 지시어는 다른 JSP 파일을 현재 JSP 페이지에 포함할 때 사용됩니다. 이는 페이지가 요청될 때마다 포함된 파일의 내용이 삽입됩니다.

### 예시
```jsp
<%@ include file="IncludeFile.jsp" %>
```
- `IncludeFile.jsp`라는 파일을 현재 페이지에 포함시킵니다. 이 때 포함된 파일은 요청 시마다 실행됩니다.

## 5. 출력: `out.println()`
JSP에서는 `out.println()`을 사용하여 클라이언트에게 데이터를 출력할 수 있습니다. 여기서는 오늘 날짜와 내일 날짜를 출력하고 있습니다.

### 예시
```jsp
<%
out.println("오늘 날짜 :"+today);
out.println("내일 날짜: "+tomorrow);
%>
```
- `today`와 `tomorrow`는 각각 `LocalDate`와 `LocalDateTime` 객체로 생성된 날짜 정보를 출력합니다.

## 6. 전체 코드 흐름
1. JSP 페이지가 요청되면, `LocalDate`와 `LocalDateTime` 객체가 생성됩니다.
2. `IncludeFile.jsp`가 포함됩니다.
3. `today`와 `tomorrow`의 날짜 정보가 `out.println()`을 통해 출력됩니다.

## 7. 핵심 개념 정리
- **`<%@ page %>`**: JSP 페이지의 설정을 지정합니다.
- **`<%@ page import %>`**: JSP에서 사용할 Java 클래스를 임포트합니다.
- **`<%@ include %>`**: 다른 JSP 파일을 포함합니다.
- **`LocalDate`와 `LocalDateTime`**: 날짜와 시간을 다루는 Java 클래스로 날짜 처리에 사용됩니다.
- **`out.println()`**: 데이터를 클라이언트에게 출력하는 방법입니다.

## 결론
JSP에서 `include` 지시어를 사용하여 다른 파일을 포함하고, 날짜와 시간 처리를 위해 `LocalDate`와 `LocalDateTime` 클래스를 사용하여 동적인 페이지를 구성할 수 있습니다. `out.println()`을 통해 화면에 출력된 날짜를 확인할 수 있습니다.
```

# validation
validation,post json 값 에러 나게 할수 있도록 하는 어노테이션을 공부 한다.

Validation이란?

프로그래밍에 있어서 가장 필요한 부분 중 하나.

특히 Java에서 null 값에 대해서 접근 하려고 할때 null pointer exception 이 발생함

이러한 부분을 방지하기 위해서 미리 검증하는 과정을 Validation이라고 함

​

기존 자바에서의 Validation 문제

1. 검증해야 할 값이 많은 경우 코드의 길이가 길어진다.

2. Service Logic과의 분리가 필요하다.

3. 흩어져 있는 경우 어디에서 검증을 하는지 알기 어려우며, 재사용의 한계가 있다.

4. 검증 Logic이 변경되는 경우 테스트 코드등 참조하는 클래스에서 Logic이 변경되어야 하는 부분이 생긴다.

​

그래서 스프링에서는 annotation으로 다양한 Validation 기능을 제공함

annotation

기능 설명

특징

@Size

문자 길이 측정

Int Type 은 사용 불가능

@NotNull

null 불가능

​

@NotEmpty

null과 "" 불가능

​

@NotBlank

null과 "", " " 불가능

​

@Past

과거 날짜

​

@PastOrPresent

오늘이거나 과거 날짜

​

@Future

미래 날짜

​

@FutureOrPresent

오늘이거나 미래 날짜

​

@Pattern

정규식 적용

​

@Max

최대값

​

@Min

최소값

​

@AssertTrue / False

별도 Logic 적용

​

@ Valid

해당 object validation 실행

​

​

bean validation spec 정보

https://beanvalidation.org/2.0-jsr380/

 
Jakarta Bean Validation - Bean Validation 2.0 (JSR 380)
Bean Validation 2.0 specification API JavaDocs Certified implementations Name Version RI Hibernate Validator 6.0.1.Final TCK The TCK for Bean Validation 2.0 can be found here . Changes between Bean Validation 2.0 and 1.1 Bean Validation 2.0 focused on the following topics: support for validating con...

beanvalidation.org

gradlle dependecies

    implementation 'org.springframework.boot:spring-boot-starter-validation'
[출처] [Spring boot] 스프링의 Validation|작성자 gudals

   @NotBlank
    private String name;
    @Max(90)
    private int age;
    @Email
    private String email;
    @Pattern(regexp ="^\\d{2,3}-\\d{3,4}-\\d{4}$" , message = "010-1111-111이런식으로 입력해주세요")
    private String phoneNumber;


## 10/18

class-template(틀)
new ~ : 객체(instance, object) 생성
싱글톤: 오직 하나의 객체

Framework: 뼈대를 미리 만들어서 제공. 대신 framework 규칙을 따라서(주체가 framework). class들의 묶음 형식 jar
** library(내가 주체), architecture, framework, pattern 개념 및 차이점

**
- POJO: java로 만들어진 class. 특정한 API에 종속적 X 제약 X
- AOP: 공통 관심사로 분리 설계
- PSA:
- IoC/DI
 
-- Container: 객체 생성, 사용, 소멸에 해당하는 라이프 사이클 담당 => 비즈니스 로직에 집중 가능 
 
 
-- Spring Framework

## Java Bean Component 설계 규칙
1. private 멤버 변수 ( encapsulation과 유사)
	- private String userName;
2. public setter() / public getter() 메서드 구현
	- 반드시 이름 규칙을 준수!
	- public void setUserName(String userName){}
	- public String getUserName() {}
3. 기본 생성자
4. package

## 기존 객체 생성 방법
1. 기본 생성자 이용 방법 
	=> 
	<beans>
		<bean id="객체명" class="com.ssafy.model.dto.Member"
			scope="<singleton> | prototype | request | session" ...>
		</bean>
	</beans>
	
	Member member = new Member();
	Member dto = new Member();
	Member m = new Member();
	
2. 중복 생성자 이용 방법
	-- arg 인자는 선언한 순서대로 순차적 지정
	<bean id="" class="" >
		<constructor-arg1 value="값">
		<constructor-arg2 value="값">	
	</bean>
	
	<bean id="" class="" >
		<constructor-arg1 value="값" index="1">
		<constructor-arg2 value="값" index="0">	
	</bean>
	
	-- arg 인자는 index="xx" 선언한 순서로 지정
	<bean id="" class="" >
		<constructor-arg1 value="값">
		<constructor-arg2 value="값">	
	</bean>
	
	Member m = new Member("홍길동", "xxx");
	
3. 기본 생성자 이용 후에 setter() 메서드를 이용한 property 설정 방법
	// Member m = new Member();
	m.setUserName("홍길동");
	m.setXxxx("xxx");

	<bean id="" class="" >
		<property name="userName" value="홍길동" />
		<property name="age" value="26" />
	</bean>
## XML(Extensible Markup Language)
-- 사용자 확장 사용 가능한 Markup Language
-- xml 규칙: well-formed document
	(1) root element 1개
	(2) 대소문자 구분
	(3) 속성명 = "속성값" 속성명='속성값'
	(4) body element: 시작 태그명과 종료 태그명은 동일해야함
		<tag-name att-name1="value" att-name2="value">
			<sub-tagname> ... </sub-tagname>
		</tag-name>
	(5) empty element: body가 없는 element
		(5-1) <tag-name></tag-name>
		(5-2) <tag-name />
	(6) 반드시 첫번째 라인에 xml 선언문 지정해야함
		=> 주석 라인, 공백 라인도 올 수 없음
		=> 형식: <?xml version="1.0" encoding="UTF-8"?>
		
-- xml 문서의 구조 정의(spec)
	(1) DTD(Document Type Definition): mybatis f/w  
	(2) Schema: spring 여러 개로 분리 설계
		=> Namespace: schema에 작성되어 있는 엘리먼트(태그)들의 이름 영역
		=> Default Namespace
			여러 개의 schema 사용 시 1개에 한해서 지정 가능
			Default Namespace 지정하는 태그 사용 시에는 prefix 생략 사용
			xmlns="http://www.springframework.org/schema/beans
			
-- xml document = well-formed(xml 규칙 준수) + valid(문서구조 준수: dtd, schema)			
		
-- xml built-in entity
	=> 형식: &엔티티명;
	=> &: &amp;
			







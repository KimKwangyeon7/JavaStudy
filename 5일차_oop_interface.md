
## 7/21(금): 
-- usage modifier : abstract, static, final
-- abstract class, abstract method
-- interface : is a, is able to
	>> jdk 1.7: 상수, abstract method
	>> jdk 1.8: public default void doA(){...}, public static void doB(){...}
	
-- generic

## method signature 동일시에 우선 순위??
	
## class node type
1. concrete class
-- 객체생성: 직접 객체 생성 가능
-- 구성요소: 멤버변수, 메서드, 생성자
-- 상속 : 선택
-- 단일상속: extends
	public class 부모클래스 {}
	public class 자식클래스 extends 부모클래스 {}
-- 재정의(Overriding): 선택
-- 다형성: 부모타입

2. abstract class
-- 객체생성: 직접 객체 생성 불가
-- 구성요소: 멤버변수, 메서드, 생성자 + [추상메서드]
-- 상속 : 강제
-- 추상메서드(미완성메서드): 메서드의 선언부만 있음, 즉, 메서드구현 {} 없음
-- 추상메서드가 존재하면 반드시 추상클래스로 선언!!!
-- 추상메서드가 존재하지 않아도 상속을 강제하기 위한 목적으로 설계: HttpServlet(JavaEE)
-- 추상메서드 형식:
	[제한자] abstract 반환타입 메서드이름(매개변수타입 매개변수명, 매개변수 매개변수명);   // {} 구현부 없음
-- 단일상속: extends
	public class 부모추상클래스 {}
	public class 자식클래스 extends 부모추상클래스 {}
-- 추상메서드(미완성메서드) 가 존재하면 반드시 재정의해야함!!!
-- 다형성: 부모타입

3. interface
-- 객체생성: 직접 객체 생성 불가
-- 구성요소: 
	>> 상수 + 추상메서드 : jdk 1.7
	>> default 구현메서드, static 구현메서드 : jdk 1.8 
	>> default 구현메서드는 자식 클래스에서 재정의 선택
	>> static 구현메서드는 객체 생성하지 않고 인터페이스이름.static구현메서드() 호출사용
-- 상수: public static final 타입 상수명 = 고정값;
	>> public static final 자동으로 표기해줌
-- 추상메서드: 
	>> 자동으로 public abstract 표기해줌
-- 다중상속(다중구현) : implements 
	public class 부모클래스 {
		public void doD() { ... }
	}
	
	public interface 부모인터페이스1 { void doA(); }
	public interface 부모인터페이스2 { void doB(); }
	
	// 인터페이스 부모, 자식 인터페이스 관계는 extends
	public interface 자식인터페이스 extends 부모인터페이스1 { void doC(); }
	
	public class 자식클래스 implements 자식인터페이스, 부모인터페이스2{
		@Override
		void doA(){}
		@Override
		void doB(){}
		@Override
		void doC(){}
	}
-- 다형성: 부모타입	
	
	
-- 부모클래스, 부모추상클래스와 자식클래스 관계는 단일 상속: extends	
-- 부모인터페이스1, 부모인터페이스2와 자식클래스 관계는 다중 상속(다중 구현) : implements
-- 부모인터페이스와 자식인터페이스 관계는 다중 상속: extends

## JavaAPI : interface
-- java.util.Collection
-- java.util.Map
-- java.sql.* : JDBC


## class node 관계 
public abstract class F {
	public abstract void doA();
}
public class Q extends F{
	@Override
	public void doA() {..}
}


public class A {}

public interface B1 {}
public interface B2 {}
public interface D extends B1, B2{}
public interface C {}

public class K extends B implements D, C { ... }


## marked interface
-- java.io.Serializable
	>> 정의된 메서드가 존재하지 않음
	>> 직렬화객체
	




## 7/20(목): 
- access modifier: public, private
- encapsulation: 도메인 클래스(Member, GeneralMember, ...)
- singleton pattern
	>> stateless??
- polymorphism
	>> 메서드(중복정의 overloading, 재정의 overriding), 생성자(overloading)
	>> 변수의 타입: 큰타입(부모타입)
		=> 변수(기본형, 참조형), 배열(기본형, 참조형), 매개변수, 반환타입
	>> typecasting
	>> instanceof
- has a 
- is a
- 황금붕어빵 < 붕어빵 < ??? < ???	
- 정적 바인딩(static binding)
- 동적 바인딩(dynamic binding)

## 객체에 대한 초기화 방법
1. 생성자
-- 중복정의
-- 매개변수를 전달 받을 수 있음
-- 객체를 생성할 때마 호출 수행
-- 형식:
	public 클래스이름(args) { // 수행문.. }

2. instance block 초기화
-- 객체를 생성할 때마 호출 수행
-- 매개변수를 전달 받을 수 없음
-- 형식: 
	{
		// 수행문..
	}

3. static block 초기화
-- 클래스 로딩시에 딱 한번만 수행
-- 매개변수를 전달 받을 수 없음
-- 형식: 
	static {
		// 수행문..
	}
 
## Singleton pattern 

* ## Singleton Pattern
 * -- 하나의 클래스를 통해서 단일객체(인스턴스) 서비스를 위한 객체
 * -- stateless : 상태정보가 없음, 주로 기능들로 구성됨
 * -- 설계 규칙:
 * 	1. private 생성자
 * 	2. private static 클래스이름 instance = new 클래스이름();
 * 	3. public static 클래스이름 getInstance() { return instance; } 
 * 
 * </pre>
 * @author 임경혜
 *
 */
public class MemberService {
//	private static MemberService instance = new MemberService(); // 2.
	private static MemberService instance; // 2.
	
	static {
		System.out.println("1. static 블럭초기화: 클래스 로딩시 딱 한번 호출 수행됨");
		instance = new MemberService();
	}
	
	{
		System.out.println("2. 인스턴스블럭초기화: 객체 생성시마다 호출 수행됨");
	}
	
	public MemberService() { // 1.	
		System.out.println("3. 객체생성시마다 호출 수행됨: 중복정의를 통해서 매개변수 전달 받을 수 있음");
	}
	
	public static MemberService getInstance() { // 3.
//		if (instance == null) {
//			instance = new MemberService();
//		}
		return instance;
	}
}

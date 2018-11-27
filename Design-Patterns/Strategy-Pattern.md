# Strategy Pattern
- 특징
  - 알고리즘을 사용하는 클래스를 수정하지 않고, 새로운 알고리즘으로 교체 가능
- 장점
  - 알고리즘을 사용하는 클래스의 분기문 제거가능 (알고리즘 인스턴스에 동작을 위임)
  - 사양 변경으로 인한 알고리즘 변경이 용이
- 단점
  - 알고리즘 클래스를 묶을 인터페이스 정의가 필요
  - 알고리즘의 숫자만큼의 클래스 파일이 추가
  - 알고리즘을 인스턴스로 전달하므로 메모리 사용량 증가

## 예제코드
- Strategy pattern 적용 전
```java
package strategy.before;

public class Character {
	private String attackType;
	
	public Character() {
		this.attackType = "weak";
	}
	
	public Character(String attackType) {
		this.attackType = attackType;
	}
	
	public void attack() {
		if("weak".equals(attackType)) {
			weakAttack();
		} else if("strong".equals(attackType)) {
			strongAttack();
		} else {
			throw new IllegalArgumentException("attackType : " + attackType);
		}
	}
	
	private void weakAttack() {
		System.out.println("WeakAttack...");
	}
	
	private void strongAttack() {
		System.out.println("StrongAttack!!!");
	}

	public void setAttackType(String attackType) {
		this.attackType = attackType;
	}
}
```
```java
package strategy.before;

public class ExcuteClass {
	public static void main(String[] args) {
		Character character = new Character();
		character.attack();
		
		Character character2 = new Character("strong");
		character2.attack();
		
		character2.setAttackType("weak");
		character2.attack();
		
		//NormalAttack을 추가해야 할 경우
		//Character 클래스를 수정하지 않고서는 불가능
	}
}
```
- Strategy pattern 적용 후
```java
package strategy.after;

public class Character {
	public static interface AttackType {
		public void attack();
	}
	
	private AttackType attackType;

	public Character() {
		this.attackType = new WeakAttack(); 
	}
	
	public Character(AttackType attackType) {
		this.attackType = attackType;
	}
	
	public void attack() {
		attackType.attack();
	}
	
	public void setAttackType(AttackType attackType) {
		this.attackType = attackType;
	}
	
	public static class WeakAttack implements AttackType {
		@Override
		public void attack() {
			System.out.println("WeakAttack...");
		}
	}
	
	public static class StrongAttack implements AttackType {
		@Override
		public void attack() {
			System.out.println("StrongAttack!!!");
		}
	}
}
```
```java
package strategy.after;

import strategy.after.Character.StrongAttack;
import strategy.after.Character.WeakAttack;

public class ExcuteClass {
	public static void main(String[] args) {
		Character character = new Character();
		character.attack();
		
		Character character2 = new Character(new StrongAttack());
		character2.attack();
		
		character2.setAttackType(new WeakAttack());
		character2.attack();
		
		//NormalAttack을 추가해야 할 경우
		//Character 클래스를 수정하지 않고, 변경 가능! 
		character2.setAttackType(()->{
			System.out.println("NormalAttack");
		});
		character2.attack();
	}
}
```

## Refer
- [Head First Design Patterns: 스토리가 있는 패턴 학습법](http://www.hanbit.co.kr/store/books/look.php?p_code=B9860513241)
- [TECHSCORE-デザインパターン：10. Strategy パターン](http://www.techscore.com/tech/DesignPattern/Strategy.html)
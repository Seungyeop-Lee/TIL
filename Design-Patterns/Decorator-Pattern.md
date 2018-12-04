# Decorator Pattern
- 특징
  - 데코레이터를 이용하여 기존 객체를 감싸서 새로운 기능을 부여
- 장점
  - 상속에 비해 기능을 유연하게 확장 가능
  - 객체에 추가적인 요건을 동적으로 추가 가능
- 단점
  - 구성요소를 초기화하는데 필요한 코드가 복잡해진다.
  - 자잘한 클래스들이 추가되어 가독성이 떨어지는 경우가 있다.

## 예제코드
- Decorator Pattern 적용 전
```java
package decorator.before;

import decorator.before.Armor.IronArmor;
import decorator.before.Armor.RareWoodArmor;
import decorator.before.Armor.WoodArmor;

public class ExcuteClass {
	public static void main(String[] args) {
		Armor woodArmor = new WoodArmor();
		System.out.println(woodArmor);
		
		Armor ironArmor = new IronArmor();
		System.out.println(ironArmor);
		
		Armor rareWoodArmor = new RareWoodArmor();
		System.out.println(rareWoodArmor);
		
		//RareIronArmor를 추가하려면
		//RareIronArmor클래스를 새로 만들어야 한다.
	}
}
```
```java
package decorator.before;

public abstract class Armor {
	
	public abstract String getName();
	public abstract int getDefPower();
	
	public static class WoodArmor extends Armor {

		@Override
		public String getName() {
			return "WoodArmor";
		}

		@Override
		public int getDefPower() {
			return 100;
		}

		@Override
		public String toString() {
			return "[getName()=" + getName() + ", getDefPower()=" + getDefPower() + "]";
		}
		
	}
	
	public static class IronArmor extends Armor {

		@Override
		public String getName() {
			return "IronArmor";
		}

		@Override
		public int getDefPower() {
			return 200;
		}

		@Override
		public String toString() {
			return "[getName()=" + getName() + ", getDefPower()=" + getDefPower() + "]";
		}
		
	}
	
	public static class RareWoodArmor extends WoodArmor {

		@Override
		public String getName() {
			return "Rare" + super.getName();
		}

		@Override
		public int getDefPower() {
			return super.getDefPower() + 50;
		}

		@Override
		public String toString() {
			return "[getName()=" + getName() + ", getDefPower()=" + getDefPower() + "]";
		}
		
	}
}
```
- Decorator Pattern 적용 후
```java
package decorator.after;

import decorator.after.Armor.ArmorType;
import decorator.after.Armor.IronArmor;
import decorator.after.Armor.RareArmor;
import decorator.after.Armor.WoodArmor;

public class ExcuteClass {
	public static void main(String[] args) {
		ArmorType woodArmor = new WoodArmor();
		System.out.println(woodArmor);
		
		ArmorType ironArmor = new IronArmor();
		System.out.println(ironArmor);
		
		ArmorType rareWoodArmor = new RareArmor(woodArmor);
		System.out.println(rareWoodArmor);
		
		//클래스의 추가 없이 RareIronArmor를 추가 할 수있다.
		ArmorType rareIronArmor = new RareArmor(ironArmor);
		System.out.println(rareIronArmor);
	}
}
```
```java
package decorator.after;

public class Armor {
	
	public static interface ArmorType {
		public String getName();
		public int getDefPower();
	}
	
	public static class WoodArmor implements ArmorType {

		@Override
		public String getName() {
			return "WoodArmor";
		}

		@Override
		public int getDefPower() {
			return 100;
		}

		@Override
		public String toString() {
			return "[getName()=" + getName() + ", getDefPower()=" + getDefPower() + "]";
		}
		
	}
	
	public static class IronArmor implements ArmorType {

		@Override
		public String getName() {
			return "IronArmor";
		}

		@Override
		public int getDefPower() {
			return 200;
		}

		@Override
		public String toString() {
			return "[getName()=" + getName() + ", getDefPower()=" + getDefPower() + "]";
		}
		
	}
	
	public static class RareArmor implements ArmorType {
		
		ArmorType armorType;
		
		public RareArmor(ArmorType armorType) {
			this.armorType = armorType;
		}
		
		@Override
		public String getName() {
			return "Rare" + armorType.getName();
		}

		@Override
		public int getDefPower() {
			return armorType.getDefPower() + 50;
		}

		@Override
		public String toString() {
			return "[getName()=" + getName() + ", getDefPower()=" + getDefPower() + "]";
		}
		
	}
}
```

## 참고
- [Head First Design Patterns : 스토리가 있는 패턴 학습법](http://www.hanbit.co.kr/store/books/look.php?p_code=B9860513241)
- [ウィキペディア（Wikipedia）: Decorator パターン](https://ja.wikipedia.org/wiki/Decorator_%E3%83%91%E3%82%BF%E3%83%BC%E3%83%B3)
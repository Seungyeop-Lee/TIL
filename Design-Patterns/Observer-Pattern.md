# Observer Pattern
- 특징
  - 객체에 옵저버로서 등록해놓으면 객체의 상태가 바뀌었을 경우 자동으로 연락을 받을 수 있음
- 장점
  - 통지를 하는 객체와 옵저버가 서로 영향을 주지 않는다. (느슨한 결합)
  - 동적으로 옵저버로서의 등록과 해제가 가능하다.
- 단점
  - 딱히 없음

## 예제코드
- Observer pattern 적용 전
```java
package observer.before;

public class ExcuteClass {
	public static void main(String[] args) {
		ServerNotifier notifier = new ServerNotifier();
		notifier.setNotice("이벤트가 시작 되었습니다.");
		
		//Hades서버를 ServerNotifier에 추가하려면 
		//ServerNotifier클래스의 수정이 필요!
		
		//Zeus서버를 ServerNotifier에서 제거하려면
		//ServerNotifier클래스의 수정이 필요!
	}
}
```
```java
package observer.before;

import observer.before.Server.Athene;
import observer.before.Server.Zeus;

public class ServerNotifier {
	private Zeus zeus;
	private Athene athene;
	
	public ServerNotifier() {
		this.zeus = new Zeus();
		this.athene = new Athene();
	}
	
	public void setNotice(String notice) {
		zeus.notify(notice);
		athene.notify(notice);
		System.out.println("----------------------------");
	}
}
```
```java
package observer.before;

public class Server {
	public static class Zeus {
		public void notify(String notice) {
			System.out.println("Notice(Zeus Server) : " + notice);
		}
	}
	
	public static class Athene {
		public void notify(String notice) {
			System.out.println("Notice(Athene Server) : " + notice);
		}
	}
	
	public static class Hades {
		public void notify(String notice) {
			System.out.println("Notice(Hades Server) : " + notice);
		}
	}
}
```
- Observer pattern 적용 후
```java
package observer.after;

import observer.after.Server.Athene;
import observer.after.Server.Hades;
import observer.after.Server.Zeus;

public class ExcuteClass {
	public static void main(String[] args) {
		ServerNotifier notifier = new ServerNotifier();
		Server zeusServer = new Zeus();
		Server atheneServer = new Athene();
		notifier.addServer(zeusServer);
		notifier.addServer(atheneServer);
		notifier.setNotice("이벤트가 시작 되었습니다.");
		
		//ServerNotifier클래스의 수정없이
		//Hades서버를 ServerNotifier에 추가 가능 
		Server hadesServer = new Hades();
		notifier.addServer(hadesServer);
		notifier.setNotice("긴급점검이 곧 시작됩니다.");
		
		//ServerNotifier클래스의 수정없이
		//Zeus서버를 ServerNotifier에서 제거 가능
		notifier.removeServer(zeusServer);
		notifier.setNotice("긴급점검이 끝났습니다.");
	}
}
```
```java
package observer.after;

import java.util.ArrayList;
import java.util.List;

public class ServerNotifier {
	
	private List<Server> servers;
	
	public ServerNotifier() {
		servers = new ArrayList<>();
	}
	
	public void setNotice(String notice) {
		for(Server server : servers) {
			server.notify(notice);
		}
		System.out.println("----------------------------");
	}
	
	public void addServer(Server server) {
		servers.add(server);
	}
	
	public void removeServer(Server server) {
		servers.remove(server);
	}
}
```
```java
package observer.after;

public abstract class Server {
	
	public abstract void notify(String notice);
	
	public static class Zeus extends Server {
		@Override
		public void notify(String notice) {
			System.out.println("Notice(Zeus Server) : " + notice);
		}
	}
	
	public static class Athene extends Server {
		@Override
		public void notify(String notice) {
			System.out.println("Notice(Athene Server) : " + notice);
		}
	}
	
	public static class Hades extends Server {
		@Override
		public void notify(String notice) {
			System.out.println("Notice(Hades Server) : " + notice);
		}
	}
}
```
## 참고
- [Head First Design Patterns: 스토리가 있는 패턴 학습법](http://www.hanbit.co.kr/store/books/look.php?p_code=B9860513241)
- [TECHSCORE-デザインパターン：17．Observer パターン](http://www.techscore.com/tech/DesignPattern/Observer.html)
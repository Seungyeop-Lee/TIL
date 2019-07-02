# 스윙에서 사용 할 폰트를 코드에서 삽입하는 방법

- 스윙에서 보여 줄 폰트가 사용자의 글꼴로 설치가 되어있지 않는경우, 코드 상에서 `tff`파일이나 `otf`을 이용하여 글꼴을 추가, 사용이 가능하다.

```java
//클래스 패스를 가져온다.
String classPath = System.getProperty("java.class.path");
try {
    //클래스 패스를 기준으로 글꼴파일을 조작 할 수 있는 객체 생성
    File fontFile = new File(classPath + "/KaiGenGothicKR-Regular.ttf");
    //글꼴 객체 생성 
    Font font = Font.createFont(Font.TRUETYPE_FONT, fontFile);
    //그래픽 환경에 생성한 글꼴을 등록
    GraphicsEnvironment.getLocalGraphicsEnvironment().registerFont(font);
} catch (FontFormatException | IOException e) {
    e.printStackTrace();
}
//폰트 이름(font.getName())이나 폰트 family(font.getFamily())를 이용하여 폰트 생성 및 사용 가능
Font userFont = new Font("카이겐고딕 KR Regular", Font.Plain, 20);
```

## 참고

- [The Java™ Tutorials > Physical and Logical Fonts](https://docs.oracle.com/javase/tutorial/2d/text/fonts.html)
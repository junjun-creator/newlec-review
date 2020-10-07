- [x] 더블 버퍼링을 활용하여 AWT 이미지 잔상 처리하기
~~~java
@Override
public void paint(Graphics g) {
    Image buf = this.createImage(this.getWidth(), this.getHeight());
    Graphics bg = buf.getGraphics(); //

    for (int i = 0; i < 3; i++) {
        boys[i].paint(bg);
    }
    g.drawImage(buf, 0, 0, this);

}
~~~
  - AWT에 그림을 그릴 수 있는 것은 윈도우와 이미지가 있다.
  - Graphics 객체는 윈도우와 이미지에 그림을 그릴 수 있는 도구이다. 이것이 없으면 빈 도화지일 뿐이다.
  - 기존 Canvas와 동일한 크기의 빈 이미지를 buf라는 변수로 지정한다.
  - buf에 그림을 그리기 위해서는 도구가 필요하므로 Graphics bg 변수를 만든다. 
  - for문을 돌면서 bg라는 도구로 그림을 buf 이미지에 그려놓는다.
  - buf에 이미지가 그려져 있으므로 이를 윈도우에 넘긴다.

---
layout: post
title: Java GUI and EventListener
subtitle: feat.Input Output
author: Ino
categories: java
banner:
  # video: https://vjs.zencdn.net/v/oceans.mp4
  image: "https://user-images.githubusercontent.com/95608811/169932444-32124c9a-4013-4864-acf7-59a3db654886.png"
  opacity: 0.618
  background: "#000"
  height: "100vh"
  min_height: "38vh"
  heading_style: "font-size: 4.25em; font-weight: bold; text-decoration: underline"
  subheading_style: "color: gold"
tags: [java,gui]
sidebar: []
---
``
> 먼저 모든 import문은 eclipse 자동생성으로 만드는걸 default로 한다.
즉, 코드에 import문은 넣지 않으므로 자동생성 해서 쓰길 권장한다.    

### 입출력 스트림
* 파일 객체 생성    
```java
File f = new File("c:\\windows\\system.ini");
```

```java
* 파일의 경로명   
String filename = f.getName(); 	// "system.ini"
String path = f.getPath(); 			// "c:\\windows\\system.ini"
String parent = f.getParent(); 	// "c:\\windows"
```


## GUI 라이브러리

<img src="https://user-images.githubusercontent.com/95608811/174436039-2b5a9a5c-844e-4b13-941d-0476009b3fa7.png" width="800px">

<img src="https://user-images.githubusercontent.com/95608811/174436141-cb7d575f-f761-4ca6-aff1-2d65656a1801.png" width="800px">


#### GUI Swing 으로 스윙프레임 만들기

```java
import javax.swing.*;
import java.awt.*;
public class ContentPaneEx extends JFrame {
public ContentPaneEx() {
setTitle("ContentPane과 JFrame");
setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);
Container contentPane = getContentPane();
contentPane.setBackground(Color.ORANGE);
contentPane.setLayout(new FlowLayout());
contentPane.add(new JButton("OK"));
contentPane.add(new JButton("Cancel"));
contentPane.add(new JButton("Ignore"));
setSize(300, 150);
setVisible(true);
  }
public static void main(String[] args) {
new ContentPaneEx();
  }
}

```
<img src="https://user-images.githubusercontent.com/95608811/174436227-dbfc5823-32f4-478b-860e-ea8f9a15c8bd.png" width="400px">

#### 스윙응용프로그램의 종료

```java
setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);
```
를 써야하는 이유

<img src="https://user-images.githubusercontent.com/95608811/174436263-cc4f0662-4685-4103-b804-fa4aebd3d709.png" width="800px">


#### 배치관리자의 대표유형 4가지
- FlowLayout : 칸이 없는 그냥 공간속에 들어온 순서대로 밀어넣는 느낌
- BorderLayout : Top,Bottom,Left,Right,Center 다섯 부분으로 쪼개서 배열하는 방식
- GridLayout : 지정된 행,렬의 갯수만큼 배열하는 방식
- CardLayout : 겹겹이 카드 쌓는 느낌의 방식

#### 라디오버튼 생성
<img src="https://user-images.githubusercontent.com/95608811/174437313-d7d2116b-7020-4501-a91e-7e25625a05aa.png" width="800px">

```java
import javax.swing.*;
import java.awt.*;
public class RadioButtonEx extends JFrame {
public RadioButtonEx() {
setTitle("라디오버튼 만들기 예제");
setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);
Container c = getContentPane();
c.setLayout(new FlowLayout());
ImageIcon cherryIcon = new ImageIcon("images/cherry.j pg" );
ImageIcon selectedCherryIcon =
new ImageIcon("images/selectedCherry.jpg");
ButtonGroup g = new ButtonGroup();
JRadioButton apple = new JRadioButton("사과");
JRadioButton pear = new JRadioButton("배", true);
JRadioButton cherry = new JRadioButton("체리", cherryIcon);
cherry.setBorderPainted(true);
cherry.setSelectedIcon(selectedCherryIcon);
g.add(apple);
g.add(pear);
g.add(cherry);
c.add(apple);
c.add(pear);
c.add(cherry);
setSize(250,150);
setVisible(true);
  }
public static void main(String [] args) {
new RadioButtonEx();
  }
}
```

#### 간단한 텍스트필드 만들기

* 텍스트필드란?
- 한 줄 짜리 텍스트(문자열) 입력 창을 구현한 컴포넌트
- 텍스트 입력 도중 `Enter`키가 입력되면 Action 이벤트 발생
- 입력 가능한 문자 개수와 입력 창의 크기는 서로 다름

```java

import javax.swing.*;
import java.awt.*;
public class TextFieldEx extends JFrame {
public TextFieldEx() {
setTitle("텍스트필드 만들기 예제");
setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);
Container c = getContentPane();
c.setLayout(new FlowLayout());
c.add(new JLabel("이름 "));
c.add(new JTextField(20));
c.add(new JLabel("학과 "));
c.add(new JTextField("컴퓨터공학과 ", 20));
c.add(new JLabel("주소 "));
c.add(new JTextField("서울시 ...", 20));
setSize(300,150);
setVisible(true);
  }
public static void main(String [] args) {
new TextFieldEx();
  }
}
```

#### JTextArea 컴포넌트 생성
```java

import javax.swing.*; import java.awt.event.*; import java.awt.*;
public class TextAreaEx extends JFrame {
private JTextField tf = new JTextField(20);
private JTextArea ta = new JTextArea(7, 20);
public TextAreaEx() {
setTitle("텍스트영역 만들기 예제");
setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);
Container c = getContentPane();
c.setLayout(new FlowLayout());
c.add(new JLabel("입력 후 <Enter> 키를 입력하세요"));
c.add(tf);
c.add(new JScrollPane(ta));
tf.addActionListener(new ActionListener() {
public void actionPerformed(ActionEvent e) {
JTextField t = (JTextField)e.getSource();
ta.append(t.getText() + "\n");
t.setText("");
  }
});
setSize(300,300);
setVisible(true);
  }
public static void main(String [] args) {
new TextAreaEx();
  }
}
```

#### 리스트 만들기

* 리스트 컴포넌트란?
- 여러 개의 아이템을 리스트 형식으로 보여주고 선택하는 컴포넌트
- `JComboBox<E>`와 기본적으로 같은 기능
- `JScrollPane에 JList<E>`를 삽입하여 스크롤 가능

```java
import javax.swing.*;
import java.awt.*;
public class ListEx extends JFrame {
private String [] fruits= {"apple", "banana", "kiwi", "mango", "pear",
"peach", "berry", "strawberry", "blackberry"};
private ImageIcon [] images = {
new ImageIcon("images/icon1.png"),
new ImageIcon("images/icon2.png"),
new ImageIcon("images/icon3.png"),
new ImageIcon("images/icon4.png") };
public ListEx() {
setTitle("리스트 만들기 예제");
setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);
Container c = getContentPane();
c.setLayout(new FlowLayout());
JList<String> strList = new JList<String>(fruits);
c.add(strList);
JList<ImageIcon> imageList = new JList<ImageIcon>();
imageList.setListData(images);
c.add(imageList);
JList<String> scrollList = new JList<String>(fruits);
c.add(new JScrollPane(scrollList));
setSize(300,300);
setVisible(true);
  }
public static void main(String [] args) {
new ListEx();
  }
}

```

#### JSlider 컴포넌트
```java
import javax.swing.*;
import java.awt.*;
public class SliderEx extends JFrame {
public SliderEx() {
setTitle("슬라이더 만들기 예제");
setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);
Container c = getContentPane();
c.setLayout(new FlowLayout());
JSlider slider = new JSlider(JSlider.HORIZONTAL, 0, 200, 100);
slider.setPaintLabels(true);
slider.setPaintTicks(true);
slider.setPaintTrack(true);
slider.setMajorTickSpacing(50);
slider.setMinorTickSpacing(10);
c.add(slider);
setSize(300,100);
setVisible(true);
  }
public static void main(String [] args) {
new SliderEx();
  }
}

```


```java

import java.awt.Container;
import java.awt.FlowLayout;
import java.awt.event.ActionEvent;
import java.awt.event.ActionListener;
import java.io.BufferedWriter;
import java.io.FileNotFoundException;
import java.io.FileReader;
import java.io.FileWriter;
import java.io.IOException;
import java.util.ArrayList;
import java.util.Scanner;
import javax.swing.JButton;
import javax.swing.JComboBox;
import javax.swing.JFrame;
import javax.swing.JLabel;
import javax.swing.JTextField;

public class MainProg extends JFrame{
   ArrayList<Student> stList = new ArrayList<Student>(); // ArrayList stList 생성
   JButton btnIns, btnOut, btnBat, btnDis; // JButton 4개 객체 생성
   JTextField tf_id, tf_name; // JTextField id 랑 name 객체 생성
   JComboBox<String> cb_hk; // JComboBox 생성
   public MainProg() {
      createGUI(); // GUI 만드는 함수호출
      btnDis.addActionListener(new ActionListener() { // btnDis의 이벤트 리스너 
      @Override
      public void actionPerformed(ActionEvent e) {
         try { // try-catch 구문, 시도했을 때 잘되면 try 구문 실행, 에러발생시 catch구문 실행
        	 FileWriter fo = new FileWriter("test.txt"); // FileWriter 을 실행한는 fo 객체 생성
        	 for(Student stu:stList) { //Student의 stu:stList 의 갯수만큼 반복실행
        		 fo.write(stu.getStudentId()+" "+stu.getStudentName()+" "+stu.getMajor()+"\n"); // fo 객체에 있는 파일 wirte, stu에 있는 di,name,major 작성
        	 }
        	 System.out.println("파일생성이 완료되었습니다.");
			 fo.close(); // 한번 쓴 파일은 다시 close 해주어야함
		} catch (IOException e1) {
			System.out.println("파일생성오류입니다."); // 그냥 잘 생성 안되면, println 구문실행
			e1.printStackTrace();
		}
         
      	}
      });
      
      btnIns.addActionListener(new ActionListener() { //btnIns 액션 만들기
         
         @Override
         public void actionPerformed(ActionEvent e) {
            int id = Integer.parseInt(tf_id.getText());
            String name = tf_name.getText();
            String hk = (String)(cb_hk.getSelectedItem());
            stList.add(new Student(id, name, hk));
            System.out.println("입력됨"+" "+id+" "+name+" "+hk);
         }
      });

      
      btnOut.addActionListener(new ActionListener() {
         
         @Override
         public void actionPerformed(ActionEvent e) {
            System.out.println("----------------------------------------------------");
            System.out.println("|   학번   |      이름      |       학과       |");
            System.out.println("----------------------------------------------------");
            for(Student stu : stList) {
               System.out.println(stu.getStudentId()+"            "+stu.getStudentName()+"          "+stu.getMajor());
            }
            
         }
      });
      btnBat.addActionListener(new ActionListener() {
		
		@Override
		public void actionPerformed(ActionEvent e) {
			try { //Scanner 객체 scan에 FileReader 해서 txt 파일입력
				Scanner scan = new Scanner(new FileReader("C:\\Users\\studentInfo.txt")); // scan 해올 경로 작성
				while(scan.hasNextLine()==true) {
					int id = scan.nextInt();
					String name = scan.next();
					int hkCode = scan.nextInt();
					String hk="";
					if (hkCode == Define.SW){
          // Define 클래스에서 각 Major를 static final 상수로 선언 (final로 선언된 상수는 바꿀 수 없음 )
          // public class Define {
          // public static final int SW = 1001;
          // public static final int INFO = 1002;
          // public static final int TONGSIN = 2001;
          // public static final int KY = 4001;
          // public static final int AI = 1003;
          // }

					hk = "컴퓨터소프트웨어공학과";
					} else if(hkCode ==Define.INFO) {
						hk = "컴퓨터정보과";
					} else if(hkCode ==Define.TONGSIN) {
						hk = "정보통신과";
					} else if(hkCode ==Define.KY) {
						hk = "경영학과";
					} else if(hkCode==Define.AI) {
						hk = "인공지능과";
					} else {
						hk = "전공학과오류입니다";
					}
					stList.add(new Student(id,name,hk));
				}
				scan.close();
				System.out.println("일괄입력했습니다");
			} catch (FileNotFoundException e1) {
				e1.printStackTrace();
				System.out.println("파일입력에러");
			}
			
		}
	});
   }
   private void createGUI() {
      this.setTitle("Project"); // Title 이름 설정
      this.setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);
      Container con = this.getContentPane(); // Container 객체 con 을 getContentPane으로 생성
      con.setLayout(new FlowLayout());

      con.add(new JLabel("학번"))
      tf_id = new JTextField(20);
      con.add(tf_id);
      con.add(new JLabel("이름"));
      tf_name = new JTextField(20);
      con.add(tf_name);
      con.add(new JLabel("학과"));
      String[] hkdatas = {"컴퓨터소프트웨어공학과", "컴퓨터정보과", "전기전자정보통신과", "디자인과", "경영학과", "이스포츠인공지능학과"   };
      cb_hk = new JComboBox<String>(hkdatas);
      con.add(cb_hk);
      btnBat = new JButton("일괄입력");
      btnIns = new JButton("입력");
      btnDis = new JButton("파일출력");
      btnOut = new JButton("보고서출력");
      con.add(btnBat); con.add(btnIns); con.add(btnDis); con.add(btnOut);
      this.setSize(270,500);
      this.setVisible(true);
   }
   public static void main(String[] args) {
      new MainProg();
   }

}
```
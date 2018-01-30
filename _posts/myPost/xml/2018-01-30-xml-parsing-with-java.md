---
layout: post
title: '[xml] java로 파싱하는 법'
categories:
  - xml
tags:
  - xml
  - parse
  - java
---


java 코드를 사용하여 xml을 파싱하는 방법을 학습합니다.




## 내부 url사용할 때

- 동일한 경로나 디렉토리에 있는 xml파일에 접근하여 xml 데이터를 가져올 수 있다.


#### main.java

```java
import java.io.FileNotFoundException;
import java.io.FileReader;
import java.io.IOException;

import javax.xml.parsers.DocumentBuilderFactory;
import javax.xml.parsers.ParserConfigurationException;

import org.w3c.dom.Document;
import org.w3c.dom.Element;
import org.w3c.dom.NodeList;
import org.xml.sax.InputSource;
import org.xml.sax.SAXException;

public class mainClass {
  public static void main(String[] args) {
    // 자바로 xml 파싱하기
    // org.w3c.dom.Document
    Document xml = null;
    try {
      // 절대 경로로 xml 값을 얻어온다.
      InputSource is = new InputSource(new FileReader("E:\\temp\\datas.xml"));

      xml = DocumentBuilderFactory.newInstance().newDocumentBuilder().parse(is);

      // root element 취득
      Element element = xml.getDocumentElement();

      // child node 취득
      NodeList list = element.getChildNodes();

      // child node 가 1개 이상인 경우
      if(list.getLength() > 0) {
        for(int i=0; i<list.getLength(); i++) {

          NodeList childList = list.item(i).getChildNodes();

          if(childList.getLength() > 0) {
            for (int j = 0; j < childList.getLength(); j++) {

              // 데이터가 있는 애들만 출려되게 한다.
              if(childList.item(j).getNodeName().equals("#text")==false) {
                System.out.println("\t xml tag name : " + childList.item(j).getNodeName() + ", xml값 : "+childList.item(j).getTextContent());                                
              }
            }
          }
          System.out.println();
        }
      }
    } catch (Exception e) {
      // TODO Auto-generated catch block
      e.printStackTrace();
    }
  }
}
```

#### datas.xml

```xml
<?xml version="1.0" encoding="UTF-8"?>
<members>
  <member>
    <number>1</number>
    <name>홍길동</name>
    <address>서울시</address>
    <join>2014/03/12</join>
  </member>
  <member>
    <number>2</number>
    <name>일지매</name>
    <address>부산시</address>
    <join>2012/11/24</join>
  </member>
  <member>
    <number>3</number>
    <name>임꺽정</name>
    <address>광주시</address>
    <join>2015/06/30</join>
  </member>
</members>
```

#### 실행 결과

```
xml tag name : number	 xml값 : 1
xml tag name : name	 xml값 : 홍길동
xml tag name : address	 xml값 : 서울시
xml tag name : join	 xml값 : 2014/03/12


xml tag name : number	 xml값 : 2
xml tag name : name	 xml값 : 일지매
xml tag name : address	 xml값 : 부산시
xml tag name : join	 xml값 : 2012/11/24


xml tag name : number	 xml값 : 3
xml tag name : name	 xml값 : 임꺽정
xml tag name : address	 xml값 : 광주시
xml tag name : join	 xml값 : 2015/06/30
```

<br>

## 외부 url xml파일에 접근할때

- 특정 api를 이용하면 결과값을 xml로 리턴한다.
- 이 xml을 파싱하여 현재 client에 뿌려줄 수 있다.


```java
package main;

import java.io.FileNotFoundException;
import java.io.FileReader;
import java.io.IOException;
import java.net.URL;
import java.net.URLConnection;

import javax.xml.parsers.DocumentBuilderFactory;
import javax.xml.parsers.ParserConfigurationException;

import org.w3c.dom.Document;
import org.w3c.dom.Element;
import org.w3c.dom.NodeList;
import org.xml.sax.InputSource;
import org.xml.sax.SAXException;

public class mainClass2 {
  public static void main(String[] args) {
    Document xml = null;
    try {
      URL url = new URL("<external url>");
      URLConnection urlConnect = url.openConnection();
      urlConnect.connect();

      InputSource is = new InputSource(urlConnect.getInputStream());

      xml = DocumentBuilderFactory.newInstance().newDocumentBuilder().parse(is);

      // root element 취득
      Element element = xml.getDocumentElement();

      // child node 취득
      NodeList list = element.getChildNodes();

      // child node 가 1개 이상인 경우
      if(list.getLength() > 0) {
        for(int i=0; i<list.getLength(); i++) {

          NodeList childList = list.item(i).getChildNodes();

          if(childList.getLength() > 0) {
            for (int j = 0; j < childList.getLength(); j++) {

              // 데이터가 있는 애들만 출려되게 한다.
              if(childList.item(j).getNodeName().equals("#text")==false) {
                System.out.println("\t xml tag name : " + childList.item(j).getNodeName() + ", xml값 : "+childList.item(j).getTextContent());								
              }
            }
          }
          System.out.println();
        }
      }
    } catch (FileNotFoundException e) {
      // TODO Auto-generated catch block
      e.printStackTrace();
    } catch (SAXException e) {
      // TODO Auto-generated catch block
      e.printStackTrace();
    } catch (IOException e) {
      // TODO Auto-generated catch block
      e.printStackTrace();
    } catch (ParserConfigurationException e) {
      // TODO Auto-generated catch block
      e.printStackTrace();
    }
  }
}
```

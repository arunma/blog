---
author: Arun Manivannan
date: '2007-08-02 09:14:58'
layout: post
slug: parse-your-xml-file
status: publish
title: Parse your XML file
wordpress_id: '250'
? ''
: - java
  - JAXP
  - xml Document parse
---

Felt that this will be useful some time. ` package com.nu;`

`import java.io.File;` `import java.io.IOException;`

`import javax.xml.parsers.DocumentBuilder;` `import
javax.xml.parsers.DocumentBuilderFactory;` `import
javax.xml.parsers.ParserConfigurationException;`

`import org.w3c.dom.Document; import org.xml.sax.SAXException;`

`public class ValidateXML {`

`public static void main(String[] args) {` `String xmlFilePath=args[0];`

`new ValidateXML().validate(xmlFilePath);`

`}`

`public void validate(String xmlFilePath){` `Document document=null;` `try {`
`DocumentBuilderFactory factory=DocumentBuilderFactory.newInstance();`
`factory.setValidating(true);` `factory.setNamespaceAware(true);`

`DocumentBuilder builder=factory.newDocumentBuilder();`
**`document=builder.parse(new File(xmlFilePath));`** `} catch
(ParserConfigurationException e) {` `e.printStackTrace();` `} catch
(SAXException e) {` `e.printStackTrace();` `} catch (IOException e) {`
`e.printStackTrace();` `}`

`}`

`}`


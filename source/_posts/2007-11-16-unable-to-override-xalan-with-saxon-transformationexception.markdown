---
author: Arun Manivannan
date: '2007-11-16 13:18:42'
layout: post
comments: true
slug: unable-to-override-xalan-with-saxon-transformationexception
status: publish
title: Unable to override Xalan with Saxon - TransformationException
wordpress_id: '282'
? ''
: - could not find function current-group
  - empty output
  - oracle xdk
  - System.setProperty
  - xslt
  - xslt 2.0
---

I've been breaking my head on this for the last couple of days. I kick off my
standalone app from another application's GUI (primarily a reflection engine
there) and was having trouble overriding xalan with saxon. I use saxon8
primarily because i needed grouping functions available in XSLT 2.0.

The setting of of the System property gave me an empty document.

System.setProperty("javax.xml.transform.TransformerFactory",

"net.sf.saxon.TransformerFactoryImpl"); And I had this standard trace when i
used any of the XSLT 2.0 functions in my stylesheet.

javax.xml.transform.TransformerConfigurationException:
javax.xml.transform.TransformerConfigurationException:
javax.xml.transform.TransformerException:
javax.xml.transform.TransformerException: **Could not find function: current-
group org.apache.xalan.processor.TransformerFactoryImpl.newTransformer(Unknown
Source) **com.ml.cortex.reports.XMLReportGenerator.writeConsolidateReportToFil
e(XMLReportGenerator.java:111) com.ml.cortex.eds.pubsub.EdsPubSubMaster.startG
eneration(EdsPubSubMaster.java:214) com.ml.cortex.eds.pubsub.EdsPubSubMaster.p
rocessPubSub(EdsPubSubMaster.java:77)
sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
sun.reflect.NativeMethodAccessorImpl.invoke(Unknown Source)
sun.reflect.DelegatingMethodAccessorImpl.invoke(Unknown Source)
java.lang.reflect.Method.invoke(Unknown Source)
com.ml.cortex.stax.CortexTestDriver.executeStep(CortexTestDriver.java:231)
sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
sun.reflect.NativeMethodAccessorImpl.invoke(Unknown Source)
sun.reflect.DelegatingMethodAccessorImpl.invoke(Unknown Source)
java.lang.reflect.Method.invoke(Unknown Source)
org.python.core.PyReflectedFunction.__call__(PyReflectedFunction.java)
org.python.core.PyMethod.__call__(PyMethod.java)
org.python.core.PyObject.__call__(PyObject.java)
org.python.core.PyInstance.invoke(PyInstance.java)
org.python.pycode._pyx117.f$0(<pyExec string>:1)
org.python.pycode._pyx117.call_function(<pyExec string>)
org.python.core.PyTableCode.call(PyTableCode.java)
org.python.core.PyCode.call(PyCode.java) org.python.core.Py.runCode(Py.java)
org.python.core.Py.exec(Py.java)
org.python.util.PythonInterpreter.exec(PythonInterpreter.java)
com.ibm.staf.service.stax.STAXThread.pyExec(STAXThread.java:562)
com.ibm.staf.service.stax.STAXScriptAction.execute(STAXScriptAction.java:46)
com.ibm.staf.service.stax.STAXThread.execute(STAXThread.java:1204) com.ibm.sta
f.service.stax.STAXThreadQueue$QueueThread.run(STAXThreadQueue.java:54)

You would understand that Xalan is the transformer that is being used in the
code and not my Saxon. Giving precedence to Saxon in the classpath and
Manifest entry gave no results.

What solved the problem was not a solution but a workaround. I use Oracle XDK
for my parsing needs. Last night I found out that XDK supports some basic XSLT
2.0 functions. Good for me. So, instead of using Saxon, I used Oracle XDK. I
replaced my old javax.xml.TransformerFactory code with much simpler
XSLTProcessor. Here is my transformation.

String xslFileName = "consolidatedreport.xsl";


String outputFileName = "FilesOutput.html";


// Output file


File resultHTMLFile = **new** File(outputFileName);



**if**(resultHTMLFile.exists())

resultHTMLFile.delete();



DOMParser parser=**new** DOMParser();parser.parse(**new** FileInputStream
(**new** File(xslFileName)));

XMLDocument xmlStyleSheetDocument =parser.getDocument();



parser.parse(**new** FileReader("Output.xml"));

XMLDocument xmlDocument=parser.getDocument();



XSLProcessor processor = **new** XSLProcessor();

XSLStylesheet xsl = processor.newXSLStylesheet(xmlStyleSheetDocument);


XMLDocumentFragment fragment=processor.processXSL(xsl, xmlDocument);


fragment.print (**new** FileOutputStream(resultHTMLFile));


System._out_.println("Results saved into " + outputFileName + ".");


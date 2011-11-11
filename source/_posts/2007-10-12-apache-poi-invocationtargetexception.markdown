---
author: Arun Manivannan
date: '2007-10-12 19:12:44'
layout: post
slug: apache-poi-invocationtargetexception
status: publish
title: Apache POI InvocationTargetException
wordpress_id: '281'
? ''
: - InvocationTargetException
  - RecordFormatException
  - Uncategorized
---

Just disable Auto-filter or Advanced filters in your Excel Sheet. You can find
filters in the Data Menu --> Filter.

_

java.lang.reflect.InvocationTargetException


_at sun.reflect.NativeConstructorAccessorImpl.newInstance0(_Native Method_)

at sun.reflect.NativeConstructorAccessorImpl.newInstance(Unknown Source)

at sun.reflect.DelegatingConstructorAccessorImpl.newInstance(Unknown Source)

at java.lang.reflect.Constructor.newInstance(Unknown Source)


at org.apache.poi.hssf.record.RecordFactory.createRecord(_RecordFactory.java:2
24_)

at org.apache.poi.hssf.record.RecordFactory.createRecords(_RecordFactory.java:
160_)at org.apache.poi.hssf.usermodel.HSSFWorkbook.<init>(


_HSSFWorkbook.java:163_)

at
org.apache.poi.hssf.usermodel.HSSFWorkbook.<init>(_HSSFWorkbook.java:130_)at
com.ml.cortex.utils.excel.ExcelUtils.<init>(


_ExcelUtils.java:30_)

at com.ml.cortex.apps.eds.mif2datasoa.MIF2DataSOAExecutor.getRequestObject(_MI
F2DataSOAExecutor.java:185_)at
com.ml.cortex.apps.eds.mif2datasoa.MIF2DataSOAExecutor.process(


_MIF2DataSOAExecutor.java:323_)

at com.ml.cortex.apps.eds.mif2datasoa.MIF2DataSOAExecutor.main(_MIF2DataSOAExe
cutor.java:574_)

Caused by: _java.lang.ArrayIndexOutOfBoundsException_



at java.lang.System.arraycopy(_Native Method_)

at org.apache.poi.hssf.record.UnknownRecord.<init>(_UnknownRecord.java:62_)at
org.apache.poi.hssf.record.SubRecord.createSubRecord(


_SubRecord.java:57_)

at org.apache.poi.hssf.record.ObjRecord.fillFields(_ObjRecord.java:99_)at
org.apache.poi.hssf.record.Record.fillFields(


_Record.java:90_)

at org.apache.poi.hssf.record.Record.<init>(_Record.java:55_)at
org.apache.poi.hssf.record.ObjRecord.<init>(


_ObjRecord.java:61_)

... 12 more


_org.apache.poi.hssf.record.RecordFormatException_: Unable to construct record
instance, the following exception occured: null

at org.apache.poi.hssf.record.RecordFactory.createRecord(_RecordFactory.java:2
37_)at org.apache.poi.hssf.record.RecordFactory.createRecords(


_RecordFactory.java:160_)

at
org.apache.poi.hssf.usermodel.HSSFWorkbook.<init>(_HSSFWorkbook.java:163_)at
org.apache.poi.hssf.usermodel.HSSFWorkbook.<init>(


_HSSFWorkbook.java:130_)

at com.ml.cortex.utils.excel.ExcelUtils.<init>(_ExcelUtils.java:30_)at
com.ml.cortex.apps.eds.mif2datasoa.MIF2DataSOAExecutor.getRequestObject(


_MIF2DataSOAExecutor.java:185_)

at com.ml.cortex.apps.eds.mif2datasoa.MIF2DataSOAExecutor.process(_MIF2DataSOA
Executor.java:323_)

at com.ml.cortex.apps.eds.mif2datasoa.MIF2DataSOAExecutor.main(_MIF2DataSOAExe
cutor.java:574_)



_

java.lang.RuntimeException


_at com.ml.cortex.utils.file.FileUtil.getFileNames(_FileUtil.java:659_)

at com.ml.cortex.apps.eds.mif2datasoa.MIF2DataSOAExecutor.doTheDiff(_MIF2DataS
OAExecutor.java:755_)at
com.ml.cortex.apps.eds.mif2datasoa.MIF2DataSOAExecutor.process(


_MIF2DataSOAExecutor.java:348_)

at com.ml.cortex.apps.eds.mif2datasoa.MIF2DataSOAExecutor.main(_MIF2DataSOAExe
cutor.java:574_)



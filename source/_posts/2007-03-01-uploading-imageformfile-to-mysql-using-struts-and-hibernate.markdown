---
author: Arun Manivannan
date: '2007-03-01 01:12:06'
layout: post
slug: uploading-imageformfile-to-mysql-using-struts-and-hibernate
status: publish
title: Uploading Image/FormFile to MySQL using Struts and Hibernate
wordpress_id: '112'
? ''
: - formfile
  - hibernate
  - java
  - mysql
  - Struts
  - upload image
---

I found this very interesting and thought I could post this here.

Let me jump directly to the code.

On your jsp, you have

`<input id="productimage" name="productimage" type="file">`

Your ActionForm will have

`private FormFile productimage;`

public FormFile **getProductimage**() { return productimage; } public void
**setProductimage**(FormFile productimage) { this.productimage = productimage;
}

My product.hbm.xml has

`<property name="productimage" type="blob" column="productimage" not-
null="true" length="250" /> ` My ActionClass has

`Product product=new Product(); product.setProductimg(`

`product.toByteArrayImpl(adminForm.getProductimage()));
model.addProduct(factory, product);`

And my model.addProduct() has

` public boolean **addProduct**(SessionFactory factory, Product product) {
Session session =null; try { session = factory.openSession();
session.save(product); } catch (Exception e) { e.printStackTrace(); return
false; } finally{ session.flush(); session.close();`

}

return true;

}

and my ProductVO has ` private byte[] **productimg**; private Blob
**productimage**;`

`/** Don't invoke this. Used by Hibernate only. */ public void
**setProductimage**(Blob productimage) { this.productimg =
this.toByteArray(productimage); }`

`/** Don't invoke this. Used by Hibernate only. */ public Blob
**getProductimage**() { return Hibernate.createBlob(this.productimg); }` `
public byte[] **getProductimg**() { return productimg; } public void
**setProductimg**(byte[] productimg) { this.productimg = productimg; }`

public byte[] **toByteArray**(Blob fromBlob) { ByteArrayOutputStream baos =
new ByteArrayOutputStream(); try { return toByteArrayImpl(fromBlob, baos); }
catch (SQLException e) { throw new RuntimeException(e); } catch (IOException
e) { throw new RuntimeException(e); } finally { if (baos != null) { try {
baos.close(); } catch (IOException ex) { } } } }

public byte[] **toByteArrayImpl**(Blob fromBlob, ByteArrayOutputStream baos)
throws SQLException, IOException { byte[] buf = new byte[4000]; InputStream is
= fromBlob.getBinaryStream(); try { for (;;) { int dataSize = is.read(buf);

if (dataSize == -1) break; baos.write(buf, 0, dataSize); } } finally { if (is
!= null) { try { is.close(); } catch (IOException ex) { } } } return
baos.toByteArray(); }

public byte[] **toByteArrayImpl**(FormFile formfile) throws SQLException,
IOException { byte[] buf = new byte[4000]; InputStream is =
formfile.getInputStream(); ByteArrayOutputStream baos = new
ByteArrayOutputStream(); try { for (;;) { int dataSize = is.read(buf);

if (dataSize == -1) break; baos.write(buf, 0, dataSize); } } finally { if (is
!= null) { try { is.close(); } catch (IOException ex) { } } } return
baos.toByteArray(); }



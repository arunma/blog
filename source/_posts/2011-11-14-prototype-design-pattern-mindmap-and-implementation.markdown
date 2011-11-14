---
layout: post
title: "Prototype Design Pattern : Mindmap and implementation"
date: 2011-11-14 21:38
comments: true
categories: tech design
description: "Prototype Design Pattern Mindmap and implementation in Java"
keywords: "prototype, design pattern, example, mindmap, java, registry manager, prototype manager"
---

I was going through the [Gang of Four][4] again after a long time as part of my college elective and had a very interested experience.  

There are some which I misunderstood or realised had few other interesting implementations or forgot they even existed.

Now, comparing and contrasting design patterns is a funny task when all my struggle goes into remembering them. 

I have been using mindmaps lately to help organize my thoughts and thought I'll convert few design patterns into maps. Hope you would find it useful too.

Click to see the full web optimized image. Mail me/Drop a comment for a bigger one or the iMindmap file.

##MindMap

[{% img http://arunma.com/canvas/Prototype.png 800 800 %}] [1]


##Implementation

This implementation snippet is from my college CA task.  The idea is to read a property file and create new instances of `Coin` objects. The `CashPropertyLoader` uses the `StoreObjectFactory` to clone and initialize the `Coin` object. Both these methods are available in the `Coin` object. The `StoreObjectFactory` also uses a `StoreObjectRegistry` to cache the prototypes. The `StoreObjectRegistry` acts as the *prototype manager*

###Class Diagram

[{% img http://arunma.com/canvas/ClassDiagramPrototype.jpg 800 800 %}] [2]


#####Cash Property Loader

{% codeblock CashPropertyLoader lang:java %}


 public CashStoreItem getItem(int idx){
	  
	    CashStoreItem   cit;

	    Map<String,String> params=new HashMap<String, String>();
	    
	    String  item, itemv;

	    item = new String("Name" + idx);
	    itemv = getValue(item);
	    params.put("name", itemv);
	    
	    item = new String("Weight" + idx);
	    itemv = getValue(item);
	    params.put("weight", itemv);

	    item = new String("Value" + idx);
	    itemv = getValue(item);
	    params.put("value", itemv);
	    
	    Coin coin = (Coin)StoreObjectRegistry.lookup(StoreObjectEnum.COIN);
	    coin.initialize(params);
	    
	    System.out.println("ToString" +("Idx :"+idx+ "\nCoin "+coin));

	    item = new String("Quantity" + idx);
	    itemv = getValue(item);

	    cit = new CashStoreItem(coin, Integer.parseInt(itemv));
	    //System.out.println("ToString" +("Idx :"+idx+ "\nCashstore item "+cit));
	    
	    return cit;
  }

{%endcodeblock%}

#####StoreObjectRegistry

{% codeblock StoreObjectRegistry lang:java %}

public class StoreObjectRegistry {

	private static Map<StoreObjectEnum, StoreObject> storeObjectRegistry=new HashMap<StoreObjectEnum, StoreObject>();
	
	public static StoreObject lookup(StoreObjectEnum storeObjecType)  {
		
		StoreObject storeObject=null;
		
		try {
			StoreObject storeObjectImpl=null;
			
			switch(storeObjecType){
				
				case COIN:
					storeObjectImpl=new Coin();
					break;
					
				case DRINK:
					storeObjectImpl=new DrinksBrand();
					break;
				}
				
				if (storeObjectImpl!=null){
					storeObjectRegistry.put(storeObjecType, storeObjectImpl);	
				}
				else{
					System.err.println("Store Object Implementation could not be resolved. Please check your store object type and store object mapping");
				}
				
				storeObject =(StoreObject)storeObjectRegistry.get(storeObjecType).clone();
			
		} catch (CloneNotSupportedException e) {
			e.printStackTrace();
		}
		return storeObject;
		
	}
	
}

{%endcodeblock%}


#####StoreObject

{%codeblock StoreObject lang:java %}


public void initialize(Map<String, String> params){

    	ArrayList<Field> fieldsList=new ArrayList<Field>();
    	addDeclaredAndInheritedFields(this.getClass(), fieldsList);
    	
		for (Field field : fieldsList) {
			
			field.setAccessible(true);
			
			if (params.get(field.getName())==null){
				continue;
			}
			try {

				 if (field.getType() == boolean.class) {
					 
					field.setBoolean(this, new Boolean(params.get(field.getName())));
					
				} else if (field.getType() == int.class) {
					
					field.setInt(this,Integer.parseInt(params.get(field.getName())));
					
				} else if (field.getType() == double.class) {
					field.setDouble(this,Double.parseDouble(params.get(field.getName() )));
					
				} else {
					field.set(this,params.get(field.getName()));
				}
			} catch (Exception e) {
				e.printStackTrace();
				System.out.println("Unable to map field : " + field.getName());
				e.printStackTrace();
			}
		}
    	
    }
    
    
    private static void addDeclaredAndInheritedFields(Class c, List<Field> fields) {
    	
        fields.addAll(Arrays.asList(c.getDeclaredFields())); 
        Class superClass = c.getSuperclass(); 
        if (superClass != null) { 
            addDeclaredAndInheritedFields(superClass, fields); 
        }       
    }
    
    public Object clone() throws CloneNotSupportedException {
        return super.clone();
    }

{%endcodeblock%}

   [1]: http://arunma.com/canvas/Prototype.png
   [2]: http://arunma.com/canvas/ClassDiagramPrototype.jpg
   [4]: http://www.amazon.com/Design-Patterns-Elements-Reusable-Object-Oriented/dp/0201633612


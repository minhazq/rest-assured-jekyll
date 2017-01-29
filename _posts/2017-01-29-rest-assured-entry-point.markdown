---
title: Rest-Assured Entry Point
date: 2017-01-29 17:57:00 -05:00
---

The Entry point of the Rest-Assured framework is creating an instance of *<u>RequestSpacification</u>* Object. Basically you are calling *given()* static method of **RestAssured** Object. Remember this is returning a RequestSpacification Object and nothing else. This is also considered as Syntactic sugar. 
<p>
<pre style='color:#000000;background:#ffffff;'><span style='color:#800000; font-weight:bold; '>package</span><span style='color:#004a43; '> com</span><span style='color:#808030; '>.</span><span style='color:#004a43; '>mquraishi</span><span style='color:#808030; '>.</span><span style='color:#004a43; '>restassured</span><span style='color:#800080; '>;</span>
<span style='color:#800000; font-weight:bold; '>import</span><span style='color:#004a43; '> org</span><span style='color:#808030; '>.</span><span style='color:#004a43; '>testng</span><span style='color:#808030; '>.</span><span style='color:#004a43; '>annotations</span><span style='color:#808030; '>.</span><span style='color:#004a43; '>Test</span><span style='color:#800080; '>;</span>
<span style='color:#800000; font-weight:bold; '>import</span><span style='color:#004a43; '> io</span><span style='color:#808030; '>.</span><span style='color:#004a43; '>restassured</span><span style='color:#808030; '>.</span><span style='color:#004a43; '>RestAssured</span><span style='color:#800080; '>;</span>
<span style='color:#800000; font-weight:bold; '>public</span> <span style='color:#800000; font-weight:bold; '>class</span> AppTest <span style='color:#800080; '>{</span>
	<span style='color:#808030; '>@</span>Test
	<span style='color:#800000; font-weight:bold; '>public</span> <span style='color:#bb7977; '>void</span> test<span style='color:#808030; '>(</span><span style='color:#808030; '>)</span><span style='color:#800080; '>{</span>
		RestAssured<span style='color:#808030; '>.</span>given<span style='color:#808030; '>(</span><span style='color:#808030; '>)</span><span style='color:#800080; '>;</span><span style='color:#696969; '>// this does not make sense but </span>
				   <span style='color:#696969; '>// Just to show that i just made an entry point</span>
	<span style='color:#800080; '>}</span>
<span style='color:#800080; '>}</span>
</pre>
</p>
<p> Rest-Assured framework is build following BBD pattern.</p>
<p><li> Given = a context/Getting a system in a particular state</li>
<li>When = soemthing happens/Poke it</li>
<li>Then = we expect some outcome/examine the new state</li>
<li>Some methods are doing nothing. This is added just for beauty. For example : and(). This type of method called "Syntactic Sugar"</li>
</p> 
<p> Now lets begin to construct a call. I will do the following</p>
<li>RestAssured.given()</li>
<li>param("param_name","param_value)</li>
<li>when() --> Syntactic sugar</li>
<li>get("/title") --> if you look for the title attribute</li>
<li> then()--> **This is not Syntactic sugar**. This returns a **ResponseSpecification** Object.</li>
<li>contentType("JSON").body("title", equalTo("MyTitle") --> Notice i am also verifying here</li>
<li>You can also get the whole response object like this:..<li>extract().response(); --> semicolon. Will return a Response Object.</li></li>
  
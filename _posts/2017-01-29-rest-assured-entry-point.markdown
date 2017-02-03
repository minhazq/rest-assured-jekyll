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
<li>param("param_name","param_value) if any</li>
<li>when() --> Syntactic sugar. It returns same RequestSpecification</li>
<li>get("/title") --> if you look for the title attribute. It is not sugur. It returns Response Object</li>
<li> then()--> **This is not Syntactic sugar**. This returns a **ResponseSpecification** Object.</li>
<li>contentType("JSON").body("title", equalTo("MyTitle") --> Notice i am also verifying here. You need org.hamcrest libs  for this. Also notice that you have to manually add import static org.hamcrest.Matchers.equalTo; because it is a static import</li>
<li>You can also get the whole response object like this:extract().response(); --> semicolon. Will return a Response Object</li>
<pre style='color:#000000;background:#ffffff;'><span style='color:#800000; font-weight:bold; '>package</span><span style='color:#004a43; '> com</span><span style='color:#808030; '>.</span><span style='color:#004a43; '>mquraishi</span><span style='color:#808030; '>.</span><span style='color:#004a43; '>restassured</span><span style='color:#800080; '>;</span>
<span style='color:#800000; font-weight:bold; '>import</span><span style='color:#004a43; '> org</span><span style='color:#808030; '>.</span><span style='color:#004a43; '>testng</span><span style='color:#808030; '>.</span><span style='color:#004a43; '>annotations</span><span style='color:#808030; '>.</span><span style='color:#004a43; '>Test</span><span style='color:#800080; '>;</span>
<span style='color:#800000; font-weight:bold; '>import</span><span style='color:#004a43; '> io</span><span style='color:#808030; '>.</span><span style='color:#004a43; '>restassured</span><span style='color:#808030; '>.</span><span style='color:#004a43; '>RestAssured</span><span style='color:#800080; '>;</span>
<span style='color:#800000; font-weight:bold; '>import</span><span style='color:#004a43; '> io</span><span style='color:#808030; '>.</span><span style='color:#004a43; '>restassured</span><span style='color:#808030; '>.</span><span style='color:#004a43; '>specification</span><span style='color:#808030; '>.</span><span style='color:#004a43; '>RequestSpecification</span><span style='color:#800080; '>;</span>
<span style='color:#800000; font-weight:bold; '>import</span><span style='color:#004a43; '> static org</span><span style='color:#808030; '>.</span><span style='color:#004a43; '>hamcrest</span><span style='color:#808030; '>.</span><span style='color:#004a43; '>Matchers</span><span style='color:#808030; '>.</span><span style='color:#004a43; '>equalTo</span><span style='color:#800080; '>;</span>

<span style='color:#800000; font-weight:bold; '>public</span> <span style='color:#800000; font-weight:bold; '>class</span> AppTest <span style='color:#800080; '>{</span>
 
	<span style='color:#808030; '>@</span>Test
	<span style='color:#800000; font-weight:bold; '>public</span> <span style='color:#bb7977; '>void</span> test<span style='color:#808030; '>(</span><span style='color:#808030; '>)</span><span style='color:#800080; '>{</span>
		RequestSpecification given <span style='color:#808030; '>=</span> RestAssured<span style='color:#808030; '>.</span>given<span style='color:#808030; '>(</span><span style='color:#808030; '>)</span><span style='color:#800080; '>;</span>
		given<span style='color:#808030; '>.</span>
			when<span style='color:#808030; '>(</span><span style='color:#808030; '>)</span><span style='color:#808030; '>.</span>
				get<span style='color:#808030; '>(</span><span style='color:#0000e6; '>"http://www/google.com"</span><span style='color:#808030; '>)</span><span style='color:#808030; '>.</span>
					then<span style='color:#808030; '>(</span><span style='color:#808030; '>)</span><span style='color:#808030; '>.</span>
						contentType<span style='color:#808030; '>(</span><span style='color:#0000e6; '>"JSON"</span><span style='color:#808030; '>)</span><span style='color:#808030; '>.</span>
						body<span style='color:#808030; '>(</span><span style='color:#0000e6; '>"title"</span><span style='color:#808030; '>,</span>equalTo<span style='color:#808030; '>(</span><span style='color:#0000e6; '>"MyTitle"</span><span style='color:#808030; '>)</span><span style='color:#808030; '>)</span><span style='color:#800080; '>;</span>
	<span style='color:#800080; '>}</span>
<span style='color:#800080; '>}</span>
</pre>
<p> The following is the required dependency accept the hamcrest. You need only if you want to perform assert.</p>
<pre style='color:#000000;background:#ffffff;'><span style='color:#a65700; '>&lt;</span><span style='color:#5f5035; '>dependencies</span><span style='color:#a65700; '>></span>
    <span style='color:#a65700; '>&lt;</span><span style='color:#5f5035; '>dependency</span><span style='color:#a65700; '>></span>
      <span style='color:#a65700; '>&lt;</span><span style='color:#5f5035; '>groupId</span><span style='color:#a65700; '>></span>io.rest-assured<span style='color:#a65700; '>&lt;/</span><span style='color:#5f5035; '>groupId</span><span style='color:#a65700; '>></span>
      <span style='color:#a65700; '>&lt;</span><span style='color:#5f5035; '>artifactId</span><span style='color:#a65700; '>></span>rest-assured<span style='color:#a65700; '>&lt;/</span><span style='color:#5f5035; '>artifactId</span><span style='color:#a65700; '>></span>
      <span style='color:#a65700; '>&lt;</span><span style='color:#5f5035; '>version</span><span style='color:#a65700; '>></span>3.0.2<span style='color:#a65700; '>&lt;/</span><span style='color:#5f5035; '>version</span><span style='color:#a65700; '>></span>
    <span style='color:#a65700; '>&lt;/</span><span style='color:#5f5035; '>dependency</span><span style='color:#a65700; '>></span>
    <span style='color:#a65700; '>&lt;</span><span style='color:#5f5035; '>dependency</span><span style='color:#a65700; '>></span>
    	<span style='color:#a65700; '>&lt;</span><span style='color:#5f5035; '>groupId</span><span style='color:#a65700; '>></span>org.testng<span style='color:#a65700; '>&lt;/</span><span style='color:#5f5035; '>groupId</span><span style='color:#a65700; '>></span>
    	<span style='color:#a65700; '>&lt;</span><span style='color:#5f5035; '>artifactId</span><span style='color:#a65700; '>></span>testng<span style='color:#a65700; '>&lt;/</span><span style='color:#5f5035; '>artifactId</span><span style='color:#a65700; '>></span>
    	<span style='color:#a65700; '>&lt;</span><span style='color:#5f5035; '>version</span><span style='color:#a65700; '>></span>6.10<span style='color:#a65700; '>&lt;/</span><span style='color:#5f5035; '>version</span><span style='color:#a65700; '>></span>
    <span style='color:#a65700; '>&lt;/</span><span style='color:#5f5035; '>dependency</span><span style='color:#a65700; '>></span>
    <span style='color:#a65700; '>&lt;</span><span style='color:#5f5035; '>dependency</span><span style='color:#a65700; '>></span>
            <span style='color:#a65700; '>&lt;</span><span style='color:#5f5035; '>groupId</span><span style='color:#a65700; '>></span>org.hamcrest<span style='color:#a65700; '>&lt;/</span><span style='color:#5f5035; '>groupId</span><span style='color:#a65700; '>></span>
            <span style='color:#a65700; '>&lt;</span><span style='color:#5f5035; '>artifactId</span><span style='color:#a65700; '>></span>hamcrest-all<span style='color:#a65700; '>&lt;/</span><span style='color:#5f5035; '>artifactId</span><span style='color:#a65700; '>></span>
            <span style='color:#a65700; '>&lt;</span><span style='color:#5f5035; '>version</span><span style='color:#a65700; '>></span>1.3<span style='color:#a65700; '>&lt;/</span><span style='color:#5f5035; '>version</span><span style='color:#a65700; '>></span>
            <span style='color:#a65700; '>&lt;</span><span style='color:#5f5035; '>scope</span><span style='color:#a65700; '>></span>test<span style='color:#a65700; '>&lt;/</span><span style='color:#5f5035; '>scope</span><span style='color:#a65700; '>></span>
        <span style='color:#a65700; '>&lt;/</span><span style='color:#5f5035; '>dependency</span><span style='color:#a65700; '>></span>
  <span style='color:#a65700; '>&lt;/</span><span style='color:#5f5035; '>dependencies</span><span style='color:#a65700; '>></span>
</pre>
<p>So the pattern is as follows:
<li>given().</li>
<li>param(key,value). --> if any</li>
<li>header().--> if any</li>
<li>when().</li>
<li>get().</li>
<li>then().</li>
<li>body(equalTo());</li>
** Remember Right After then() part , Assertion part started. You got the response now you do whatever you want to do ** 
<p> Thats all for getting it started </p>
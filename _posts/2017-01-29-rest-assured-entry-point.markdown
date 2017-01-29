---
title: Rest-Assured Entry Point
date: 2017-01-29 17:57:00 -05:00
---

The Entry point of the Rest-Assured framework is creating an instance of *RequestSpacification* Object.
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
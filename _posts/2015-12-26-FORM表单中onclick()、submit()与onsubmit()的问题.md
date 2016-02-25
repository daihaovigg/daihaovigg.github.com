<p>最近遇到一次处理form数据的过滤，采用了button的onclick事件来检查，发现return false后表单仍然提交了。</p>
<p>于是仔细研究了下onclick、onsubmit、submit集合函数之间的关系和区别</p>
<pre class="brush: text;">
onsubmit: 
You can override this event by returning false in the event handler.
Use this capability to validate data on the client side to prevent invalid data from being submitted to the server.
If the event handler is called by the onsubmit attribute of the form object,
the code must explicitly request the return value using the return function,
and the event handler must provide an explicit return value for each possible code path in the event handler function.
The submit method does not invoke the onsubmit event handler.

submit:
The submit method does not invoke the onsubmit event handler.
Call the onsubmit event handler directly.
When using Microsoft? Internet Explorer 5.5 and later,
you can call the fireEvent method with a value of onsubmit in the sEvent parameter.
</pre>
<p>首先生成一个form</p>
<pre class="brush:html">
&lt;form action=&quot;#&quot; method=&quot;POST&quot; name=&quot;A&quot; onsubmit=&quot;return X();&quot;&gt;
&lt;input type=&quot;text&quot; value=&quot;&quot; /&gt;
&lt;input onclick=&quot;Y()&quot; type=&quot;submit&quot; value=&quot;提交&quot; /&gt;
&lt;/form&gt;
</pre>
<p>自己写X()、Y()函数，我们会发现，这几个函数的执行顺序</p>
<p>1) onclick: Y();</p>
<p>2) onsubmit: X();</p>
<p>3) submit();</p>
<p>也就是说</p>
<p>只要 onclick 未 return false 那么就继续执行 onsubmit</p>
<p>只要 onsubmit 未return false 那么表单就被提交出去了</p>
<p>另外一点写法上注意一定要 &#8220;return X();&#8221; 才能取得函数的返回值，否则只是调用函数，返回值未被传递</p>
<p><strong>正确写法：</strong><br />
&lt;input type=submit onclick=&#8221;return X();&#8221;&gt;<br />
//X() 返回false后，form的submit会被终止</p>
<p><s>错误写法:<br />
&lt;input type=submit onclick=&#8221;X()&#8221;&gt;</s><br />
//X() 返回false后未传递给onclick事件，form的submit会继续</p>
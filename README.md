<h1>Reactive Hello world application in android</h1>

<h3 id="adding-rxjava-2-to-a-java-project">Adding RxJava 2 library  to a Java project in Android Studio</h3>
<div class="paragraph">

To use RxJava in a Gradle build, add the following as dependency.

</div>
<div class="listingblock">
<div class="content">
<pre class="CodeRay highlight"><code data-lang="groovy">compile <span class="key">group</span>: <span class="string"><span class="delimiter">'</span><span class="content">io.reactivex.rxjava2</span><span class="delimiter">'</span></span>, <span class="key">name</span>: <span class="string"><span class="delimiter">'</span><span class="content">rxjava</span><span class="delimiter">'</span></span>, <span class="key">version</span>: <span class="string"><span class="delimiter">'</span><span class="content">2.1.1</span><span class="delimiter">'</span></span></code></pre>
</div>
</div>
<div class="paragraph">

For Maven, you can add RxJava via the following snippet.

</div>
<div class="listingblock">
<div class="content">
<pre class="CodeRay highlight"><code data-lang="xml"><span class="tag">&lt;dependency&gt;</span>
    <span class="tag">&lt;groupId&gt;</span>io.reactivex.rxjava2<span class="tag">&lt;/groupId&gt;</span>
    <span class="tag">&lt;artifactId&gt;</span>rxjava<span class="tag">&lt;/artifactId&gt;</span>
    <span class="tag">&lt;version&gt;</span>2.0.4<span class="tag">&lt;/version&gt;</span>
<span class="tag">&lt;/dependency&gt;
</span></code></pre>
</div>
</div>
STEP 1:

Declare an observable data items first
<pre>Observable&lt;String&gt; <span>observable </span>= Observable.<span>just</span>(<span>"Hello "</span><span>, </span><span>" World"</span>)<span>;
</span></pre>
STEP 2

Create an Observer like this
<pre>Observer&lt;String&gt; stringObserver = <span>new </span>Observer&lt;String&gt;() {
    <span>@Override
</span><span>    </span><span>public void </span><span>onSubscribe</span>(Disposable d) {
        Log.<span>d</span>(<span>TAG</span><span>, </span><span>"onSubscribe() called with: d = [" </span>+ d + <span>"]"</span>)<span>;
</span><span>    </span>}

    <span>@Override
</span><span>    </span><span>public void </span><span>onNext</span>(String s) {
        Log.<span>d</span>(<span>TAG</span><span>, </span><span>"onNext() called with: s = [" </span>+ s + <span>"]"</span>)<span>;
</span><span>        </span><span>appCompatTextView</span>.setText(String.<span>format</span>(<span>"%s%s"</span><span>, </span><span>appCompatTextView</span>.getText().toString()<span>, </span>s))<span>;
</span><span>    </span>}

    <span>@Override
</span><span>    </span><span>public void </span><span>onError</span>(Throwable e) {
        Log.<span>d</span>(<span>TAG</span><span>, </span><span>"onError() called with: e = [" </span>+ e + <span>"]"</span>)<span>;
</span><span>    </span>}

    <span>@Override
</span><span>    </span><span>public void </span><span>onComplete</span>() {
        Log.<span>d</span>(<span>TAG</span><span>, </span><span>"onComplete() called"</span>)<span>;
</span><span>    </span>}
}<span>;</span>

</pre>
There Are four methods implement when create an Observer
<ul>
 	<li><strong>onSubscribe(Disposable d)</strong></li>
 	<li><strong>onNext(String s) </strong></li>
 	<li><strong> onError(Throwable e)</strong></li>
 	<li><strong>onComplete()</strong></li>
</ul>
When Subscribing  <strong>onSubscribe </strong>called first time that observer is subscribed observable data,After that <b>onNext </b>called twice returning string items,When completed items <strong>onComplete </strong>called and transaction completed. If any error occurs <strong>onError </strong>called .

STEP 3:

Subscribe Observable Using Observer created above.
<pre><span>observable</span>.subscribe(stringObserver)<span>;
</span></pre>
After Subscribing <span>onNext</span>(String s) called two times  because we put two string items in observable

in <span>onNext</span>(String s)  we setting text to a textview.

&nbsp;

<img src="http://thoughtnerds.com/wp-content/uploads/2018/03/device-2018-03-31-124446-162x300.png" alt="" width="318" height="589" class="alignnone wp-image-925 aligncenter" />

&nbsp;



Thanks Happy coding :D

&nbsp;

---
date: 2004-06-05T10:47:00+00:00
title: Early &#038; Adopter fill you in on &#8220;Application Level Events&#8221;
type: posts
---
The [3 Leaf](http://www.3leaf.com/) guys, (well probably just one of them... but who knows which one), talk about ["Application Level Events" in Whidbey](http://ea.3leaf.com/2004/06/application_lev.html)

Here's a code snippet to illustrate what they are talking about... something that I like to think of as "Global.asa" (I haven't done a lot of web work since ASP) for Windows applications...

<pre><font color="blue" family="Microsoft Sans Serif">Namespace My    Partial <font color="blue" family="Microsoft Sans Serif">Friend <font color="blue" family="Microsoft Sans Serif">Class MyApplication        <font color="blue" family="Microsoft Sans Serif">Private <font color="blue" family="Microsoft Sans Serif">Sub MyApplication_Shutdown(<font color="blue" family="Microsoft Sans Serif">ByVal Sender <font color="blue" family="Microsoft Sans Serif">As <font color="blue" family="Microsoft Sans Serif">Object, _            <font color="blue" family="Microsoft Sans Serif">ByVal e <font color="blue" family="Microsoft Sans Serif">As System.Windows.Forms.ShutdownEventArgs) _            <font color="blue" family="Microsoft Sans Serif">Handles <font color="blue" family="Microsoft Sans Serif">Me.Shutdown        <font color="blue" family="Microsoft Sans Serif">End <font color="blue" family="Microsoft Sans Serif">Sub</pre>

<pre><font color="blue" family="Microsoft Sans Serif">Private <font color="blue" family="Microsoft Sans Serif">Sub MyApplication_StartUp(<font color="blue" family="Microsoft Sans Serif">ByVal sender <font color="blue" family="Microsoft Sans Serif">As <font color="blue" family="Microsoft Sans Serif">Object, _            <font color="blue" family="Microsoft Sans Serif">ByVal e <font color="blue" family="Microsoft Sans Serif">As System.Windows.Forms.StartupEventArgs) _            <font color="blue" family="Microsoft Sans Serif">Handles <font color="blue" family="Microsoft Sans Serif">Me.Startup        <font color="blue" family="Microsoft Sans Serif">End <font color="blue" family="Microsoft Sans Serif">Sub</pre>

<pre><font color="blue" family="Microsoft Sans Serif">Private <font color="blue" family="Microsoft Sans Serif">Sub MyApplication_StartupNextInstance(<font color="blue" family="Microsoft Sans Serif">ByVal Sender <font color="blue" family="Microsoft Sans Serif">As <font color="blue" family="Microsoft Sans Serif">Object, _            <font color="blue" family="Microsoft Sans Serif">ByVal e <font color="blue" family="Microsoft Sans Serif">As System.Windows.Forms.StartupNextInstanceEventArgs) _            <font color="blue" family="Microsoft Sans Serif">Handles <font color="blue" family="Microsoft Sans Serif">Me.StartupNextInstance        <font color="blue" family="Microsoft Sans Serif">End <font color="blue" family="Microsoft Sans Serif">Sub</pre>

<pre><font color="blue" family="Microsoft Sans Serif">Private <font color="blue" family="Microsoft Sans Serif">Sub MyApplication_UnhandledException(<font color="blue" family="Microsoft Sans Serif">ByVal sender <font color="blue" family="Microsoft Sans Serif">As <font color="blue" family="Microsoft Sans Serif">Object, _            <font color="blue" family="Microsoft Sans Serif">ByVal e <font color="blue" family="Microsoft Sans Serif">As System.Threading.ThreadExceptionEventArgs) _            <font color="blue" family="Microsoft Sans Serif">Handles <font color="blue" family="Microsoft Sans Serif">Me.UnhandledException        <font color="blue" family="Microsoft Sans Serif">End <font color="blue" family="Microsoft Sans Serif">Sub</pre>

<pre><font color="blue" family="Microsoft Sans Serif">End <font color="blue" family="Microsoft Sans Serif">Class</pre>

<pre><font color="blue" family="Microsoft Sans Serif">End <font color="blue" family="Microsoft Sans Serif">Namespace</pre>

Make sure you check out [the whole post](http://ea.3leaf.com/2004/06/application_lev.html) for a pretty screenshot 🙂
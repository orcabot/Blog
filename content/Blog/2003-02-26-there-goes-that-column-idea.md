<font face="Trebuchet MS" color="teal">Doesn&#8217;t anyone use static web pages anymore? I was playing<br /> around with some code, just doing a quick prototype of an app for my <a href="http://msdn.microsoft.com/columns/codefun.asp" class="broken_link">Coding4Fun</a> column and<br /> (inspired by the cool and useful <a href="http://www.neilogic.com/paint.htm" class="broken_link">PAINT</a> </p> 

<p>
  tool) I decided to create an app that would check<br /> for changes to a website and give you a little quick-launch menu of updated sites<br /> on your system tray (who couldn&#8217;t use one more icon there?).</font><br /> <font face="Trebuchet MS" color="teal">I thought it would be cool<br /> to show how to use the HTTP <a href="http://www.w3.org/Protocols/rfc2616/rfc2616-sec14.html#sec14.25">If-Modified-Since</a><br /> request header combined with the Last-Modified response header to show how quick<br /> and easy it is to check for new content using the System.Net classes. Well, the<br /> code works fine, it is the web that is broken 😉</font>
</p>

<p>
  <font face="Trebuchet MS" color="teal">Every site I tried this on (<a href="http://www.penny-arcade.com">Penny Arcade</a>, <a href="http://www.pvponline.com">PVP Online</a>,<br /> even&nbsp;<a href="http://msdn.microsoft.com">MSDN</a>) happens to be a dynamic<br /> page (php, asp, aspx, whatever), so there is either no Last Modified header<br /> and the web server always says it has been modified (when it hasn&#8217;t)<br /> or there is a Last Modified header but it is always equal to the date/time<br /> of your request. Either way, you can&#8217;t use those headers to check if a site has<br /> been updated. Fine and dandy, I&#8217;m already losing interest in this as a sample for<br /> my column&nbsp;but I still want to finish it; so I figure that a quick<br /> hash of the HTML will accomplish the same thing. Save the hash and compare it<br /> against a hash of the new HTML later, and we&#8217;ll be set. Nope, no go. If there is<br /> a single bit of HTML on the page that is dynamic (such as the page request time<br /> being embedded into the HTML somewhere) then, of course, the hash will change<br /> and I&#8217;ll think the page has been updated.</font>
</p>

<p>
  <font face="Trebuchet MS" color="#008080">I realize that by carefully scraping<br /> the page you could certainly get around these problems, but my two goals had<br /> been:</font>
</p>

<p>
  <font face="Trebuchet MS" color="#008080">#1 to show how to use the headers to<br /> avoid having to even look at the response body (the HTML in this case)<br /> and</font>
</p>

<p>
  <font face="Trebuchet MS" color="#008080">#2 to create a general purpose<br /> utility that would work with most websites. </font>
</p>

<p>
  <font face="Trebuchet MS" color="#008080">On to the next<br /> idea!</font>
</p>

<p>
  <font face="Trebuchet MS" color="#008080">Oh, and if you are wondering how that<br /> <a href="http://www.neilogic.com/paint.htm" class="broken_link">PAINT</a> tool handles this? They<br /> check a special (likely static!) file on the web site that is automatically<br /> updated when the page is changed. That is a perfectly good solution if you are<br /> dealing with a single site, but it doesn&#8217;t really help me with the general case.<br /> And, if you are going to spit out a file that helps people (and their tools)<br /> know when your page has changed&#8230; why not just a RSS feed with links back to<br /> your page so that the advertisers are still getting all their<br /> hits?</font>
</p>
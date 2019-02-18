<font face="Trebuchet MS" color="teal">I have been, since I started using .NET, a big supporter of<br /> the <a href="http://msdn.microsoft.com/msdnmag/issues/02/07/NetSmartClients/toc.asp" class="broken_link">&#8216;Smart<br /> Client&#8217; or &#8216;Rich Client&#8217; application</a>. I&#8217;ve talked about it to people, I&#8217;ve<br /> dug deep into the underlying technology, I&#8217;ve built samples&#8230; <strong>big fan<br /> of the whole idea</strong> </p> 

<p>
  . On a parallel track, I wrote&nbsp;several systems internal<br /> to MSDN using VB.NET and Windows Forms, but I didn&#8217;t make any of them into<br /> auto-deploying apps (aka no-touch apps, aka HREF EXEs, etc.). Why not? Habit I<br /> suppose, it just really didn&#8217;t occur to me, until after I had sent out a few<br /> updates for each of them, then I felt really silly&#8230; I&#8217;m not supposed to have<br /> to do this anymore, sending out updates is a thing of the past!</font>
</p>

<p>
  <font face="Trebuchet MS" color="teal">Tonight I converted them all to HREF EXEs. I had a<br /> little snag, it turns out that when IEExec hosts your EXE it doesn&#8217;t run it in<br /> the&nbsp;same type of Apartment as when you&nbsp;execute it directly (which doesn&#8217;t matter for most<br /> things, but it screws up COM automation and drag and drop), but just adding<br /> </font>
</p>

<p>
  <font face="Courier New" size="2"></p> 
  
  <p>
    System.Threading.Thread.CurrentThread.ApartmentState =<br /> Threading.ApartmentState.STA
  </p>
  
  <p>
    </font>
  </p>
  
  <p>
    <font face="Trebuchet MS" color="teal">to the start of my app fixed that right up. (and, no, just<br /> adding the&nbsp;STA attribute wouldn&#8217;t do it&#8230; in case you are<br /> wondering)</font>
  </p>
  
  <p>
    <font face="Trebuchet MS" color="teal">Now, if I build a new version and copy<br /> those files to the appropriate web server directory&#8230; <strong>bang</strong>,<br /> everyone is running the new version the next time they launch the app. No<br /> update, no need to send out a &#8220;new version&#8221; email, unless I just want to let the<br /> users know what is new&#8230; it is a good thing.</font>
  </p>
  
  <p>
    <font face="Trebuchet MS" color="#008080">Tired now, must stop<br /> coding&#8230;</font>
  </p>
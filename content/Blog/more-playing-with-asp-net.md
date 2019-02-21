---
date: 2004-06-12T10:58:00+00:00
title: More playing with ASP.NET
type: posts
---
As with my earlier messing around with a poll, I took a concept from the [www.asp.net](http://www.asp.net/) site today and made my own "CheckDotNet.aspx" page. The one on [www.asp.net](http://www.asp.net/) only checks for the .NET Framework 1.0 or better, so I modified the logic to detect 1.1 and 1.0 as two distinct cases... recommending an upgrade for no framework or 1.0, and returning "Framework Found" if you have 1.1 already.

<http://www.duncanmackenzie.net/tools/checkdotnet.aspx>

Difficult? Nope... nothing too impressive...

Useful? I have no idea, but I thought it was worth putting up. The page has only one bit of code, the load event handler (and yes, I know I could have overriden OnLoad... but the code I started with was using Page_Load, so I just went with it)...

<pre><span>    </span><span style="FONT-WEIGHT: 400; FONT-SIZE: 12px; COLOR: #0000ff; FONT-FAMILY: Courier New">Sub</span><span> Page_Load(sender </span><span style="FONT-WEIGHT: 400; FONT-SIZE: 12px; COLOR: #0000ff; FONT-FAMILY: Courier New">as</span><span> </span><span style="FONT-WEIGHT: 400; FONT-SIZE: 12px; COLOR: #0000ff; FONT-FAMILY: Courier New">Object</span><span>, e </span><span style="FONT-WEIGHT: 400; FONT-SIZE: 12px; COLOR: #0000ff; FONT-FAMILY: Courier New">as</span><span> EventArgs)</span><span>        </span><span style="FONT-WEIGHT: 400; FONT-SIZE: 12px; COLOR: #0000ff; FONT-FAMILY: Courier New">Dim</span><span> clrVersion </span><span style="FONT-WEIGHT: 400; FONT-SIZE: 12px; COLOR: #0000ff; FONT-FAMILY: Courier New">as</span><span> Version = Request.Browser.ClrVersion        </span><span style="FONT-WEIGHT: 400; FONT-SIZE: 12px; COLOR: #0000ff; FONT-FAMILY: Courier New">If</span><span> clrVersion.Major &gt; 0 </span><span style="FONT-WEIGHT: 400; FONT-SIZE: 12px; COLOR: #0000ff; FONT-FAMILY: Courier New">Then</span><span>         </span><span style="FONT-WEIGHT: 400; FONT-SIZE: 12px; COLOR: #0000ff; FONT-FAMILY: Courier New">If</span><span> clrVersion.Minor &gt; 0 </span><span style="FONT-WEIGHT: 400; FONT-SIZE: 12px; COLOR: #0000ff; FONT-FAMILY: Courier New">Then</span><span>             aOkPanel11.Visible = </span><span style="FONT-WEIGHT: 400; FONT-SIZE: 12px; COLOR: #0000ff; FONT-FAMILY: Courier New">True</span><span>         </span><span style="FONT-WEIGHT: 400; FONT-SIZE: 12px; COLOR: #0000ff; FONT-FAMILY: Courier New">Else</span><span>             aOkPanel1.Visible = </span><span style="FONT-WEIGHT: 400; FONT-SIZE: 12px; COLOR: #0000ff; FONT-FAMILY: Courier New">True</span><span>         </span><span style="FONT-WEIGHT: 400; FONT-SIZE: 12px; COLOR: #0000ff; FONT-FAMILY: Courier New">End</span><span> </span><span style="FONT-WEIGHT: 400; FONT-SIZE: 12px; COLOR: #0000ff; FONT-FAMILY: Courier New">If</span><span>        </span><span style="FONT-WEIGHT: 400; FONT-SIZE: 12px; COLOR: #0000ff; FONT-FAMILY: Courier New">Else</span><span>            downloadPanel.Visible = </span><span style="FONT-WEIGHT: 400; FONT-SIZE: 12px; COLOR: #0000ff; FONT-FAMILY: Courier New">True</span><span>        </span><span style="FONT-WEIGHT: 400; FONT-SIZE: 12px; COLOR: #0000ff; FONT-FAMILY: Courier New">End</span><span> </span><span style="FONT-WEIGHT: 400; FONT-SIZE: 12px; COLOR: #0000ff; FONT-FAMILY: Courier New">If</span><span>     </span><span style="FONT-WEIGHT: 400; FONT-SIZE: 12px; COLOR: #0000ff; FONT-FAMILY: Courier New">End</span><span> </span><span style="FONT-WEIGHT: 400; FONT-SIZE: 12px; COLOR: #0000ff; FONT-FAMILY: Courier New">Sub</span><span></span></pre>

aOkPanel11 on my page contains the text to show if the user has the 1.1 version of the Framework... aOkPanel1 is shown if they have 1.0 only, and downloadPanel appears if they have no Framework at all.

_Ouch... I guess I was porting/modifying that code way too quickly... goofed up the logic in a bunch of ways (thanks for the comments folks!)... at the risk of trying again and **still** screwing it up... here is another try at that routine;_

<pre><span>    </span><span style="FONT-WEIGHT: 400; FONT-SIZE: 12px; COLOR: #0000ff; FONT-FAMILY: Courier New">Sub</span><span> Page_Load(sender </span><span style="FONT-WEIGHT: 400; FONT-SIZE: 12px; COLOR: #0000ff; FONT-FAMILY: Courier New">as</span><span> </span><span style="FONT-WEIGHT: 400; FONT-SIZE: 12px; COLOR: #0000ff; FONT-FAMILY: Courier New">Object</span><span>, e </span><span style="FONT-WEIGHT: 400; FONT-SIZE: 12px; COLOR: #0000ff; FONT-FAMILY: Courier New">as</span><span> EventArgs)
        </span><span style="FONT-WEIGHT: 400; FONT-SIZE: 12px; COLOR: #0000ff; FONT-FAMILY: Courier New">Dim</span><span> clrVersion </span><span style="FONT-WEIGHT: 400; FONT-SIZE: 12px; COLOR: #0000ff; FONT-FAMILY: Courier New">as</span><span> Version = Request.Browser.ClrVersion
        </span><span style="FONT-WEIGHT: 400; FONT-SIZE: 12px; COLOR: #0000ff; FONT-FAMILY: Courier New">if</span><span> clrVersion.Major = 1 </span><span style="FONT-WEIGHT: 400; FONT-SIZE: 12px; COLOR: #0000ff; FONT-FAMILY: Courier New">Then</span><span>
         </span><span style="FONT-WEIGHT: 400; FONT-SIZE: 12px; COLOR: #0000ff; FONT-FAMILY: Courier New">if</span><span> clrVersion.Minor &gt; = 1 </span><span style="FONT-WEIGHT: 400; FONT-SIZE: 12px; COLOR: #0000ff; FONT-FAMILY: Courier New">Then</span><span>
             </span><span style="FONT-WEIGHT: 400; FONT-SIZE: 12px; COLOR: #008000; FONT-FAMILY: Courier New">'1.1 or better, but less than 2.0
</span><span>             aOkPanel11.Visible = </span><span style="FONT-WEIGHT: 400; FONT-SIZE: 12px; COLOR: #0000ff; FONT-FAMILY: Courier New">true</span><span>
         </span><span style="FONT-WEIGHT: 400; FONT-SIZE: 12px; COLOR: #0000ff; FONT-FAMILY: Courier New">ElseIf</span><span> clrVersion.Minor = 0 </span><span style="FONT-WEIGHT: 400; FONT-SIZE: 12px; COLOR: #0000ff; FONT-FAMILY: Courier New">Then</span><span>
             </span><span style="FONT-WEIGHT: 400; FONT-SIZE: 12px; COLOR: #008000; FONT-FAMILY: Courier New">'only 1.0
</span><span>             aOkPanel1.Visible = </span><span style="FONT-WEIGHT: 400; FONT-SIZE: 12px; COLOR: #0000ff; FONT-FAMILY: Courier New">true</span><span>
         </span><span style="FONT-WEIGHT: 400; FONT-SIZE: 12px; COLOR: #0000ff; FONT-FAMILY: Courier New">end</span><span> </span><span style="FONT-WEIGHT: 400; FONT-SIZE: 12px; COLOR: #0000ff; FONT-FAMILY: Courier New">if</span><span>
        </span><span style="FONT-WEIGHT: 400; FONT-SIZE: 12px; COLOR: #0000ff; FONT-FAMILY: Courier New">elseif</span><span> clrVersion.Major &gt; 1 </span><span style="FONT-WEIGHT: 400; FONT-SIZE: 12px; COLOR: #0000ff; FONT-FAMILY: Courier New">Then</span><span>
            </span><span style="FONT-WEIGHT: 400; FONT-SIZE: 12px; COLOR: #008000; FONT-FAMILY: Courier New">'2.x or greater... could have its own panel
</span><span>            </span><span style="FONT-WEIGHT: 400; FONT-SIZE: 12px; COLOR: #008000; FONT-FAMILY: Courier New">'but showing the 1.1 panel is probably the next
</span><span>            </span><span style="FONT-WEIGHT: 400; FONT-SIZE: 12px; COLOR: #008000; FONT-FAMILY: Courier New">'best thing...
</span><span>            aOkPanel11.Visible = </span><span style="FONT-WEIGHT: 400; FONT-SIZE: 12px; COLOR: #0000ff; FONT-FAMILY: Courier New">true</span><span>
        </span><span style="FONT-WEIGHT: 400; FONT-SIZE: 12px; COLOR: #0000ff; FONT-FAMILY: Courier New">else</span><span>
            </span><span style="FONT-WEIGHT: 400; FONT-SIZE: 12px; COLOR: #008000; FONT-FAMILY: Courier New">'anything else... should display for
</span><span>            </span><span style="FONT-WEIGHT: 400; FONT-SIZE: 12px; COLOR: #008000; FONT-FAMILY: Courier New">'&lt; 1.0 or nothing...
</span><span>            downloadPanel.Visible = </span><span style="FONT-WEIGHT: 400; FONT-SIZE: 12px; COLOR: #0000ff; FONT-FAMILY: Courier New">true</span><span>
        </span><span style="FONT-WEIGHT: 400; FONT-SIZE: 12px; COLOR: #0000ff; FONT-FAMILY: Courier New">end</span><span> </span><span style="FONT-WEIGHT: 400; FONT-SIZE: 12px; COLOR: #0000ff; FONT-FAMILY: Courier New">if</span><span>

    </span><span style="FONT-WEIGHT: 400; FONT-SIZE: 12px; COLOR: #0000ff; FONT-FAMILY: Courier New">end</span><span> </span><span style="FONT-WEIGHT: 400; FONT-SIZE: 12px; COLOR: #0000ff; FONT-FAMILY: Courier New">sub</span><span>
</span></pre>

<pre>Also, in the html of the aOkPanel11, which can appear for the .NET Framework 1.1 or greater... I changed the text to reflect this possibility and added&lt;%Response.Write(Request.Browser.ClrVersion)%&gt;</pre>

_hopefully, this &#8216;release' works better than the last one 🙂_

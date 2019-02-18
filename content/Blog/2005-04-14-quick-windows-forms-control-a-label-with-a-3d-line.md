I was mocking up a UI yesterday, and I wanted to produce an interface that looked like Front Page&#8217;s &#8220;New from Template&#8221; dialog&#8230;

<img title="Front Page Template Dialog" src="http://www.duncanmackenzie.net/images/FrontPageTemplates.png" border="0" />

But I couldn&#8217;t easily replicate those little dividers (for Options, Description, Preview), so I created a &#8220;DividerLabel&#8221; with about 10 minutes of VB.NET code (2003)&#8230; 

<img title="Divider Label Sample" src="http://www.duncanmackenzie.net/images/DividerLabelSample.png" border="0" />

And, if you are so inclined, you can set the text to nothing and you have a line!

<img title="Hey Look, a Line!" src="http://www.duncanmackenzie.net/images/HeyLookYouCanMakeALine.png" border="0" />

**The Code**

<pre><font color="blue" family="Microsoft Sans Serif">Imports</font> System.Drawing <font color="blue" family="Microsoft Sans Serif">Imports</font> System.Windows.Forms <font color="blue" family="Microsoft Sans Serif">Public</font> <font color="blue" family="Microsoft Sans Serif">Class</font> DividerLabel <font color="blue" family="Microsoft Sans Serif">Inherits</font> System.Windows.Forms.Label <font color="blue" family="Microsoft Sans Serif">Dim</font> m_spacing <font color="blue" family="Microsoft Sans Serif">As</font> <font color="blue" family="Microsoft Sans Serif">Integer</font> <font color="blue" family="Microsoft Sans Serif">Dim</font> m_borderStyle <font color="blue" family="Microsoft Sans Serif">As</font> Border3DStyle = Border3DStyle.Etched &lt;System.ComponentModel.Category(<font color="red" family="Microsoft Sans Serif">"Appearance"</font>)&gt; _ <font color="blue" family="Microsoft Sans Serif">Public</font> <font color="blue" family="Microsoft Sans Serif">Property</font> LineStyle() <font color="blue" family="Microsoft Sans Serif">As</font> Border3DStyle <font color="blue" family="Microsoft Sans Serif">Get</font> <font color="blue" family="Microsoft Sans Serif">Return</font> m_borderStyle <font color="blue" family="Microsoft Sans Serif">End</font> <font color="blue" family="Microsoft Sans Serif">Get</font> <font color="blue" family="Microsoft Sans Serif">Set</font>(<font color="blue" family="Microsoft Sans Serif">ByVal</font> Value <font color="blue" family="Microsoft Sans Serif">As</font> Border3DStyle) <font color="blue" family="Microsoft Sans Serif">If</font> Value &lt;&gt; m_borderStyle <font color="blue" family="Microsoft Sans Serif">Then</font> m_borderStyle = Value <font color="blue" family="Microsoft Sans Serif">Me</font>.Invalidate() <font color="blue" family="Microsoft Sans Serif">End</font> <font color="blue" family="Microsoft Sans Serif">If</font> <font color="blue" family="Microsoft Sans Serif">End</font> <font color="blue" family="Microsoft Sans Serif">Set</font> <font color="blue" family="Microsoft Sans Serif">End</font> <font color="blue" family="Microsoft Sans Serif">Property</font> &lt;System.ComponentModel.Category(<font color="red" family="Microsoft Sans Serif">"Appearance"</font>)&gt; _ <font color="blue" family="Microsoft Sans Serif">Public</font> <font color="blue" family="Microsoft Sans Serif">Property</font> Spacing() <font color="blue" family="Microsoft Sans Serif">As</font> <font color="blue" family="Microsoft Sans Serif">Integer</font> <font color="blue" family="Microsoft Sans Serif">Get</font> <font color="blue" family="Microsoft Sans Serif">Return</font> m_spacing <font color="blue" family="Microsoft Sans Serif">End</font> <font color="blue" family="Microsoft Sans Serif">Get</font> <font color="blue" family="Microsoft Sans Serif">Set</font>(<font color="blue" family="Microsoft Sans Serif">ByVal</font> Value <font color="blue" family="Microsoft Sans Serif">As</font> <font color="blue" family="Microsoft Sans Serif">Integer</font>) <font color="blue" family="Microsoft Sans Serif">If</font> Value &lt;&gt; m_spacing <font color="blue" family="Microsoft Sans Serif">Then</font> m_spacing = Value <font color="blue" family="Microsoft Sans Serif">Me</font>.Invalidate() <font color="blue" family="Microsoft Sans Serif">End</font> <font color="blue" family="Microsoft Sans Serif">If</font> <font color="blue" family="Microsoft Sans Serif">End</font> <font color="blue" family="Microsoft Sans Serif">Set</font> <font color="blue" family="Microsoft Sans Serif">End</font> <font color="blue" family="Microsoft Sans Serif">Property</font> <font color="blue" family="Microsoft Sans Serif">Protected</font> <font color="blue" family="Microsoft Sans Serif">Overrides</font> <font color="blue" family="Microsoft Sans Serif">Sub</font> OnPaint(<font color="blue" family="Microsoft Sans Serif">ByVal</font> e <font color="blue" family="Microsoft Sans Serif">As</font> PaintEventArgs) <font color="blue" family="Microsoft Sans Serif">Dim</font> g <font color="blue" family="Microsoft Sans Serif">As</font> Graphics = e.Graphics <font color="blue" family="Microsoft Sans Serif">Dim</font> f <font color="blue" family="Microsoft Sans Serif">As</font> Font = <font color="blue" family="Microsoft Sans Serif">Me</font>.Font <font color="blue" family="Microsoft Sans Serif">Dim</font> b <font color="blue" family="Microsoft Sans Serif">As</font> Brush = <font color="blue" family="Microsoft Sans Serif">New</font> SolidBrush(<font color="blue" family="Microsoft Sans Serif">Me</font>.ForeColor) <font color="blue" family="Microsoft Sans Serif">Dim</font> sf <font color="blue" family="Microsoft Sans Serif">As</font> StringFormat = StringFormat.GenericTypographic <font color="blue" family="Microsoft Sans Serif">Dim</font> labelBounds <font color="blue" family="Microsoft Sans Serif">As</font> <font color="blue" family="Microsoft Sans Serif">New</font> RectangleF(0, 0, <font color="blue" family="Microsoft Sans Serif">Me</font>.Width, <font color="blue" family="Microsoft Sans Serif">Me</font>.Height) <font color="blue" family="Microsoft Sans Serif">Dim</font> textSize <font color="blue" family="Microsoft Sans Serif">As</font> SizeF = g.MeasureString(<font color="blue" family="Microsoft Sans Serif">Me</font>.Text, f, <font color="blue" family="Microsoft Sans Serif">Me</font>.Width) g.DrawString(<font color="blue" family="Microsoft Sans Serif">Me</font>.Text, f, b, 0, 0, sf) <font color="blue" family="Microsoft Sans Serif">If</font> textSize.Width + Spacing &lt; <font color="blue" family="Microsoft Sans Serif">Me</font>.Width <font color="blue" family="Microsoft Sans Serif">Then</font> <font color="blue" family="Microsoft Sans Serif">Dim</font> startingPoint <font color="blue" family="Microsoft Sans Serif">As</font> Point startingPoint.X = textSize.Width + Spacing startingPoint.Y = textSize.Height \ 2 ControlPaint.DrawBorder3D(g, startingPoint.X, _ startingPoint.Y, _ <font color="blue" family="Microsoft Sans Serif">Me</font>.Width - startingPoint.X, _ 5, m_borderStyle, Border3DSide.Top) <font color="blue" family="Microsoft Sans Serif">End</font> <font color="blue" family="Microsoft Sans Serif">If</font> <font color="blue" family="Microsoft Sans Serif">End</font> <font color="blue" family="Microsoft Sans Serif">Sub</font> <font color="blue" family="Microsoft Sans Serif">Public</font> <font color="blue" family="Microsoft Sans Serif">Sub</font> <font color="blue" family="Microsoft Sans Serif">New</font>() <font color="blue" family="Microsoft Sans Serif">Me</font>.SetStyle(ControlStyles.DoubleBuffer, <font color="blue" family="Microsoft Sans Serif">True</font>) <font color="blue" family="Microsoft Sans Serif">Me</font>.SetStyle(ControlStyles.AllPaintingInWmPaint, <font color="blue" family="Microsoft Sans Serif">True</font>) <font color="blue" family="Microsoft Sans Serif">Me</font>.SetStyle(ControlStyles.ResizeRedraw, <font color="blue" family="Microsoft Sans Serif">True</font>) <font color="blue" family="Microsoft Sans Serif">End</font> <font color="blue" family="Microsoft Sans Serif">Sub</font> <font color="blue" family="Microsoft Sans Serif">End</font> <font color="blue" family="Microsoft Sans Serif">Class</font> </pre>
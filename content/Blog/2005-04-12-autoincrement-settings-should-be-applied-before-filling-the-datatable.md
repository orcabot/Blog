I ran into a problem recently, where duplicate IDs were being generated by my offline ADO.NET code&#8230; and I had no real idea why this was happening. I had set up the primary key of my DataTable to have the following propery values:

  * AutoIncrement = true
  * AutoIncrementSeed = -1
  * AutoIncrementStep = -1 

This is supposed to result in offline IDs being assigned as -1,-2,-3 and therefore having no possibility of conflict with any **real** IDs used in the database. This has worked great for me on many occasions, so it was a bit of a surprise when I finally tracked down my problem to the IDs that were being assigned to my new rows. I put a break point right after calling NewRow on the DataTable and the newly created Row had a PK value of 141. Another new row and it would have a value of 140, and so on&#8230; it seems the AutoIncrementStep was working, but the seed value was wonky.

I asked around and was told to make sure that I was setting the AutoIncrement properties **before** filling the table, which it turns out I wasn&#8217;t doing. What I had for code was basically like this: 

  1. If table doesn&#8217;t exist in DataSet, set a flag to true indicating that this is the first call to the data load
  2. Fill the table
  3. Check the flag and setup the table, including setting the AutoIncrement properties

With the new guidance I had received, I changed the routine to:

  1. If table doesn&#8217;t exist in DataSet, set a flag to true indicating that this is the first call to the data load
  2. Fill the table&#8217;s schema (FillSchema), to get the columns and the PK
  3. Check the flag and setup the table, including setting the AutoIncrement properties
  4. Fill the table

Of course, all this could be made simpler/cleaner if I built up the schema &#8216;manually&#8217; before loading the table&#8217;s data but I&#8217;m way too lazy for that.
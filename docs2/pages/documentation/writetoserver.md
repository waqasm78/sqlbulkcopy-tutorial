---
layout: default
title: SqlBulkCopy WriteToServer
permalink: writetoserver
---

{% include template-h1.html %}

## Description
Copy all rows from the source to the destination table.

{% include template-example.html %} 
{% highlight csharp %}
using (SqlBulkCopy bulkCopy = new SqlBulkCopy(connectionString))
{
    bulkCopy.DestinationTableName = "TheDestinationTable";
    
    // CALL WriteToServer method.
    bulkCopy.WriteToServer(dt);
}
{% endhighlight %}

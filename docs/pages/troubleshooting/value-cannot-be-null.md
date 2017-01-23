---
layout: default
title: SqlBulkCopy - Value cannot be null.
permalink: value-cannot-be-null
---


{% include template-h1.html %}

{% include begin-block-h2.html title='Problem' %}

{% include template-execute-thrown.html methodName='WriteToServer' %}

{% include template-exception.html message='Value cannot be null.' %}

{% include end-block-h2.html %}

{% include begin-block-h2.html title='Solution' %}

{% include template-exception-cause.html %}

- The provided value for the DestinationTableName is null.

How to Fix

- ENSURE you specify a value to the DestinationTableName property.
- ENSURE the value specified is not empty.

{% include begin-code.html %}
{% highlight csharp %}
string destinationName = "TheDestinationTable";

using (var connection = new SqlConnection(My.Config.ConnectionStrings.BulkOperations))
{
    connection.Open();

    using (var bulkCopy = new SqlBulkCopy(connection))
    {
        // ENSURE you specify a value to the DestinationTableName property.
        // ENSURE the value specified is not empty.
        bulkCopy.DestinationTableName = destinationName;

        bulkCopy.ColumnMappings.Add("TheColumnInt", "TheColumnInt");
        bulkCopy.ColumnMappings.Add("TheColumnString", "TheColumnString");

        bulkCopy.WriteToServer(dt);
    }
}
{% endhighlight %}
{% include end-code.html %}
{% include end-block-h2.html %}
---
layout: default
title: The DestinationTableName property must be set before calling this method.
permalink: destinationtablename-property-must-be-set
---

{% include template-h1.html %}

{% include begin-block-h2.html title='Problem' %}

<p>
The method WriteToServer throw the following error:
</p>

{% include template-exception.html message='The DestinationTableName property must be set before calling this method.' %}

{% include end-block-h2.html %}

{% include begin-block-h2.html title='Solution' %}
This error can be caused for two reasons:
- NO
- An empty string value has been provided to the DestinationTableName property
This error is caused because to value has been set to the DestinationTableName property.

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
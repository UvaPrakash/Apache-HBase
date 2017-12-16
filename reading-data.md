## Reading Data using HBase Client API

* Create a new class ReadData.java
* Use the below code for ReadData.java

```
package com.uva.hbase_java_samples;

/**
 * @author Uva Prakash P
 * Dec 16, 2017
 */

import java.io.IOException;

import org.apache.hadoop.conf.Configuration;
import org.apache.hadoop.hbase.HBaseConfiguration;
import org.apache.hadoop.hbase.TableName;
import org.apache.hadoop.hbase.client.Connection;
import org.apache.hadoop.hbase.client.ConnectionFactory;
import org.apache.hadoop.hbase.client.Get;
import org.apache.hadoop.hbase.client.HTable;
import org.apache.hadoop.hbase.client.Result;
import org.apache.hadoop.hbase.util.Bytes;

public class ReadData {
   public static void main(String[] args) throws IOException, Exception{
      System.out.println("Initializing HBase Read Data");

      // Instantiating Configuration class
      Configuration con = HBaseConfiguration.create();
      Connection connection = null;
      connection = ConnectionFactory.createConnection(con);

      // Instantiating HTable class
      HTable hTable = (HTable) connection.getTable(TableName.valueOf("employee"));

      // Instantiating Get class
      Get g = new Get(Bytes.toBytes("row1"));

      // Reading the data
      Result result = hTable.get(g);

      // Reading values from Result class object
      byte [] value = result.getValue(Bytes.toBytes("personal"),Bytes.toBytes("name"));
      byte [] value1 = result.getValue(Bytes.toBytes("personal"),Bytes.toBytes("city"));

      // Printing the values
      String name = Bytes.toString(value);
      String city = Bytes.toString(value1);

      System.out.println("Name: " + name + " City: " + city);
   }
}
```

* Click on Run -&gt; Run As -&gt; Java Application. Once the project runs successfully, output will be displayed as below.

![](/assets/read_data_eclipse.png)

### Validating from HBase Shell![](/assets/read_data_hbase.png)




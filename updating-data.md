## Updating Data using HBase Client API

**Before Update**![](/assets/Insert_Data_HBase.png)Here we will update the professional:salary value from 50000 to 75000.

* Create a new class UpdateData.java
* Use the below code for UpdateData.java

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
import org.apache.hadoop.hbase.client.HTable;
import org.apache.hadoop.hbase.client.Put;
import org.apache.hadoop.hbase.util.Bytes;

public class UpdateData{

   public static void main(String[] args) throws IOException {
	  System.out.println("Initializing HBase Update Data");

      // Instantiating Configuration class
	  Configuration con = HBaseConfiguration.create();
	  Connection connection = null;
	  connection = ConnectionFactory.createConnection(con);

      // Instantiating HTable class
	  HTable hTable = (HTable) connection.getTable(TableName.valueOf("employee"));

      // Instantiating Put class
      // Accepts a row name
      Put p = new Put(Bytes.toBytes("row1"));

      // Updating a cell value
      p.addColumn(Bytes.toBytes("professional"),
      Bytes.toBytes("salary"),Bytes.toBytes("75000"));

      // Saving the put Instance to the HTable.
      hTable.put(p);
      System.out.println("Data Updated");

      // closing HTable
      hTable.close();
   }
}
```

* Click on Run -&gt; Run As -&gt; Java Application. Once the project runs successfully, output will be displayed as below.

![](/assets/update_data_eclipse.png)

### Validating data from HBase

The value of professional:salary has been updated to 75000.![](/assets/update_data_hbase.png)




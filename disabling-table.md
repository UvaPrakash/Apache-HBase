## Disabling Tables using HBase Admin API

To delete a table or change its settings, you need to first disable the table using the disable command.

* Create a new class DisableTable.java
* Use the below code for DisableTable.java

```
package com.uva.hbase_java_samples;

/**
 * @author Uva Prakash P
 * Dec 16, 2017
 */

import java.io.IOException;

import org.apache.hadoop.conf.Configuration;
import org.apache.hadoop.hbase.HBaseConfiguration;
import org.apache.hadoop.hbase.MasterNotRunningException;
import org.apache.hadoop.hbase.client.Connection;
import org.apache.hadoop.hbase.client.ConnectionFactory;
import org.apache.hadoop.hbase.client.HBaseAdmin;

public class DisableTable{

   public static void main(String args[]) throws MasterNotRunningException, IOException{
      System.out.println("Initializing HBase Disable Table");

      // Instantiating configuration class
      Configuration con = HBaseConfiguration.create();
      Connection connection = null;
      connection = ConnectionFactory.createConnection(con);

      // Instantiating HBaseAdmin class
      HBaseAdmin admin = (HBaseAdmin) connection.getAdmin();

      // Verifying weather the table is disabled
      Boolean bool = admin.isTableDisabled("employee");
      System.out.println("Checking whether the table is already disabled: "+ bool);

      // Disabling the table using HBaseAdmin object
      if(!bool){
         admin.disableTable("employee");
         System.out.println("Table employee disabled");
      }
   }
}
```

* Click on Run -&gt; Run As -&gt; Java Application. Once the project runs successfully, output will be displayed as below.

![](/assets/DisableTable_Eclipse.png)

### Validating from HBase Shell

![](/assets/disabled_table_boolean.png)

![](/assets/hbase_disable_scan_table.png)




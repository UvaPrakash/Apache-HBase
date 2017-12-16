## Enabling Tables using HBase Admin API

* Create a new class EnableTable.java
* Use the below code for EnableTable.java

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

public class EnableTable{

   public static void main(String args[]) throws MasterNotRunningException, IOException{
      System.out.println("Initializing HBase Enable Table");

      // Instantiating configuration class
      Configuration con = HBaseConfiguration.create();
      Connection connection = null;
      connection = ConnectionFactory.createConnection(con);

      // Instantiating HBaseAdmin class
      HBaseAdmin admin = (HBaseAdmin) connection.getAdmin();

      // Verifying weather the table is enabled
      Boolean bool = admin.isTableEnabled("employee");
      System.out.println("Checking whether the table is enabled: "+ bool);

      // Enabling the table using HBaseAdmin object
      if(!bool){
         admin.enableTable("employee");
         System.out.println("Table employee Enabled");
      }
   }
}
```

* Click on Run -&gt; Run As -&gt; Java Application. Once the project runs successfully, output will be displayed as below.

![](/assets/enable_table_eclipse.png)

### Validating from HBase Shell

![](/assets/enable_table_hbase.png)


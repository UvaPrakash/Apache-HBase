## Listing Tables using HBase Admin API

* We will be using the same project hbase\_java\_\_\_samples that we created previously.
* Create a new class ListTable.java

![](/assets/List_Table_Creation.png)

* Use the below code for ListTable.java

```
package com.uva.hbase_java_samples;

/**
 * Author: Uva Prakash P
 * Date: 16-Dec-2017
 *
 */

import java.io.IOException;

import org.apache.hadoop.conf.Configuration;
import org.apache.hadoop.hbase.HBaseConfiguration;
import org.apache.hadoop.hbase.HTableDescriptor;
import org.apache.hadoop.hbase.MasterNotRunningException;
import org.apache.hadoop.hbase.client.Connection;
import org.apache.hadoop.hbase.client.ConnectionFactory;
import org.apache.hadoop.hbase.client.HBaseAdmin;

public class ListTable {

   public static void main(String args[])throws MasterNotRunningException, IOException{
      System.out.println("Initializing HBase List Table");

      // Instantiating a configuration class
      Configuration con = HBaseConfiguration.create();
      Connection connection = null;
      connection = ConnectionFactory.createConnection(con);

      // Instantiating HBaseAdmin class
      HBaseAdmin admin = (HBaseAdmin) connection.getAdmin();

      // Getting all the list of tables using HBaseAdmin object
      HTableDescriptor[] tableDescriptor = admin.listTables();

      // printing all the table names.
      for (int i=0; i<tableDescriptor.length;i++ ){
         System.out.println(tableDescriptor[i].getNameAsString());
      }

   }
}
```

Click on Run -&gt; Run As -&gt; Java Application. Once the project runs successfully, output will be displayed as below.

![](/assets/list_table_eclipse.png)

### Validating List HBase table from HBase Shell

![](/assets/list_table_hbase.png)




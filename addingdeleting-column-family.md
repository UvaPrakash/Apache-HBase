## Enabling Tables using HBase Admin API

* Before adding/deleting column family, we will check the column families that are available in the table 'employee'. We have 2 column family- personal and professional.
* By using HBase Admin API, we will add 2 more columns- employeename, contactdetails and delete 1 column- professional.

![](/assets/column_family.png)

* Create a new class AddDeleteColumnFamily.java
* Use the below code for AddDeleteColumnFamily.java

```
package com.uva.hbase_java_samples;

/**
 * @author Uva Prakash P
 * Dec 16, 2017
 */

import java.io.IOException;

import org.apache.hadoop.conf.Configuration;
import org.apache.hadoop.hbase.HBaseConfiguration;
import org.apache.hadoop.hbase.HColumnDescriptor;
import org.apache.hadoop.hbase.MasterNotRunningException;
import org.apache.hadoop.hbase.client.Connection;
import org.apache.hadoop.hbase.client.ConnectionFactory;
import org.apache.hadoop.hbase.client.HBaseAdmin;

public class AddDeleteColumnFamily {
    public static void main(String[] args) throws MasterNotRunningException, IOException {
      System.out.println("Initializing HBase Add/Delete Column Family");

      // Instantiating configuration class
      Configuration con = HBaseConfiguration.create();
      Connection connection = null;
      connection = ConnectionFactory.createConnection(con);

      // Instantiating HbaseAdmin class
      HBaseAdmin admin = (HBaseAdmin) connection.getAdmin();

      // Adding column families
      admin.addColumn("employee", new HColumnDescriptor("employeename"));
      admin.addColumn("employee", new HColumnDescriptor("contactdetails"));
      System.out.println("Column Added");

      // Deleting a column family
      admin.deleteColumn("employee","professional");
      System.out.println("Column Deleted"); 
   }    
}
```

* Click on Run -&gt; Run As -&gt; Java Application. Once the project runs successfully, output will be displayed as below.

### ![](/assets/Add_Delete_Column_Eclipse.png)

### Validating from HBase Shell![](/assets/Add_Delete_Column_HBase.png)




## Scanning Data using HBase Client API

The **scan **command is used to view the data in HTable.![](/assets/scan_data_hbase.png)

* Create a new class ScanData.java
* Use the below code for ScanData.java

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
import org.apache.hadoop.hbase.client.Result;
import org.apache.hadoop.hbase.client.ResultScanner;
import org.apache.hadoop.hbase.client.Scan;
import org.apache.hadoop.hbase.util.Bytes;

public class ScanTable{

   public static void main(String args[]) throws IOException{
      System.out.println("Initializing HBase Scan Data");
		
      // Instantiating Configuration class
      Configuration con = HBaseConfiguration.create();
      Connection connection = null;
      connection = ConnectionFactory.createConnection(con);

      // Instantiating HTable class
      HTable hTable = (HTable) connection.getTable(TableName.valueOf("employee"));

      // Instantiating the Scan class
      Scan scan = new Scan();

      // Scanning the required columns
      scan.addColumn(Bytes.toBytes("personal"), Bytes.toBytes("name"));
      scan.addColumn(Bytes.toBytes("personal"), Bytes.toBytes("city"));

      // Getting the scan result
      ResultScanner scanner = hTable.getScanner(scan);

      // Reading values from scan result
      for (Result result = scanner.next(); result != null; result = scanner.next())

      System.out.println("Found row : " + result);
      //closing the scanner
      scanner.close();
   }
}

```

* Click on Run -&gt; Run As -&gt; Java Application. Once the project runs successfully, output will be displayed as below.

![](/assets/scan_data_eclipse.png)


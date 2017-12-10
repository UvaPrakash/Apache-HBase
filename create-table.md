## Create Table using HBase Admin API

* Open Eclipse IDE
* Click on File -&gt; New -&gt; Maven Project

![](/assets/new_maven_proj_1.png)

![](/assets/new_maven_proj_2.png)

Mention the name of the project and click on Finish.

![](/assets/new_maven_proj_3.png)

Once done, project will be created as below.

![](/assets/project_structure.png)

Add the below dependencies to pom.xml for including hadoop-common, hadoop-mapreduce-client-common, hadoop-mapreduce-client-core, hbase-client and commons-configuration based on the version that is installed in the machine. Once done, wait for the dependencies to be downloaded.

```
    <!-- https://mvnrepository.com/artifact/org.apache.hadoop/hadoop-common -->
	<dependency>
    	<groupId>org.apache.hadoop</groupId>
    	<artifactId>hadoop-common</artifactId>
    	<version>2.7.3</version>
	</dependency>
    <!-- https://mvnrepository.com/artifact/org.apache.hadoop/hadoop-mapreduce-client-common -->
	<dependency>
	    <groupId>org.apache.hadoop</groupId>
	    <artifactId>hadoop-mapreduce-client-common</artifactId>
	    <version>2.7.3</version>
	</dependency>
    <!-- https://mvnrepository.com/artifact/org.apache.hadoop/hadoop-mapreduce-client-core -->
	<dependency>
	    <groupId>org.apache.hadoop</groupId>
	    <artifactId>hadoop-mapreduce-client-core</artifactId>
	    <version>2.7.3</version>
	</dependency>
    <!-- https://mvnrepository.com/artifact/org.apache.hbase/hbase-client -->
	<dependency>
	    <groupId>org.apache.hbase</groupId>
	    <artifactId>hbase-client</artifactId>
	    <version>1.2.5</version>
	</dependency>
    <!-- https://mvnrepository.com/artifact/commons-configuration/commons-configuration -->
	<dependency>
	    <groupId>commons-configuration</groupId>
	    <artifactId>commons-configuration</artifactId>
	    <version>1.10</version>
	</dependency>
```

Its time to code CreateTable.java.

```
package com.uva.hbase_java_samples;

/**
 * Author: Uva Prakash P
 * Date: 11-Dec-2017
 *
 */

import java.io.IOException;

import org.apache.hadoop.conf.Configuration;
import org.apache.hadoop.hbase.HBaseConfiguration;
import org.apache.hadoop.hbase.HColumnDescriptor;
import org.apache.hadoop.hbase.HTableDescriptor;
import org.apache.hadoop.hbase.TableName;
import org.apache.hadoop.hbase.client.Connection;
import org.apache.hadoop.hbase.client.ConnectionFactory;
import org.apache.hadoop.hbase.client.HBaseAdmin;

public class CreateTable 
{
	   public static void main(String[] args) throws IOException {
		   System.out.println("Initializing HBase Create Table");
		   
	      // Instantiating configuration class
		  Configuration con = HBaseConfiguration.create();
		  Connection connection = null;
		  connection = ConnectionFactory.createConnection(con);

	      // Instantiating HbaseAdmin class
	      HBaseAdmin admin = (HBaseAdmin) connection.getAdmin();

	      // Instantiating table descriptor class
	      HTableDescriptor tableDescriptor = new
	      HTableDescriptor(TableName.valueOf("employee"));

	      // Adding column families to table descriptor
	      tableDescriptor.addFamily(new HColumnDescriptor("personal"));
	      tableDescriptor.addFamily(new HColumnDescriptor("professional"));

	      // Execute the table through admin
	      admin.createTable(tableDescriptor);
	      System.out.println("Table: employee created");
	   }
}
```




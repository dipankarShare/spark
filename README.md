## Spark Overview

<img src="images/01-platform.jpg" alt="Platform" width="600" height="400"/>
<img src="images/02-flow.jpg" alt="Flow" width="600" height="400"/>
<img src="images/03-admin-setting-to-see-the-files-databricks.jpg" alt="Admin Setting for DBFS files" width="600" height="400"/>
<img src="images/04-hivemetastore-delta-table.jpg" alt="Delta Table Location in Hive" width="600" height="400"/>
<img src="images/05-02-word-count-test-suite-flow.jpg" alt="Sequential Flow Spark Job" width="600" height="400"/>

### For Streaming

To change the read/write to `readStream`/`writeStream`, use the following code:

    - outputMode can be complete/append/overwrite
    - it returns a streaming query which can be hold in sQuery (given below), whereas the write method don't
```python
 - return (flattenedDF.writeStream
                    .format("delta")
                    .option("checkpointLocation", f"{self.base_data_dir}/checkpoint/invoices")
                    .outputMode("append")
                    .toTable("invoice_line_items")
        )

 - sQuery = wc.wordCount()
 - stop at the end of execution         sQuery.stop()


```


# Spark Overview

<div align="center">
    <img src="images/01-platform.jpg" alt="Platform" width="700" height="400" style="border: 2px solid #ccc; margin: 10px;"/>
    <img src="images/02-flow.jpg" alt="Flow" width="700" height="400" style="border: 2px solid #ccc; margin: 10px;"/>
    <img src="images/03-admin-setting-to-see-the-files-databricks.jpg" alt="Admin Setting for DBFS files" width="700" height="400" style="border: 2px solid #ccc; margin: 10px;"/>
    <img src="images/04-hivemetastore-delta-table.jpg" alt="Delta Table Location in Hive" width="700" height="400" style="border: 2px solid #ccc; margin: 10px;"/>
    <img src="images/05-02-word-count-test-suite-flow.jpg" alt="Sequential Flow Spark Job" width="700" height="400" style="border: 2px solid #ccc; margin: 10px;"/>
</div>

### For Streaming

To change the read/write to `readStream`/`writeStream`, use the following code:

- `outputMode` can be complete/append/overwrite.
- It returns a streaming query which can be held in `sQuery` (as shown below), whereas the write method doesn't.

```python
sQuery = (flattenedDF.writeStream
                    .format("delta")
                    .option("checkpointLocation", f"{self.base_data_dir}/checkpoint/invoices")
                    .outputMode("append")
                    .toTable("invoice_line_items")
)

# Stop at the end of execution
sQuery.stop()

Stream Processing Flow with API
Streaming Query Background Process

Ensures reading only the new data in each micro batch.
<div align="center"> <img src="images/06-StreamProcessingFlow.jpg" alt="Stream Processing Flow" width="700" height="400" style="border: 2px solid #ccc; margin: 10px;"/> </div>
Available Now Trigger

    It can be unspecified.
    Fixed interval.

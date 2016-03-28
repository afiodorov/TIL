# UDF support from Python

UDF's are BigQuery user-defined functions (written in JavaScript) which
BigQuery can run for post-processing the query. Find more at the [official
docs](https://cloud.google.com/bigquery/user-defined-functions).

Turns out [tylertreat's BigQuery python
module](https://github.com/tylertreat/BigQuery-Python) supports udf:

```python
from oauth2client import client
import bigquery

project_id = [[YOUR_PROJECT_ID]]
credentials = client.GoogleCredentials.get_application_default()
bq_client = bigquery.get_client(project_id, credentials=credentials)

udf_uri = "gs://udf.js"
bq_client.write_to_table(sql,
                         dataset=[[DATASET_NAME]],
                         table=destination_table,
                         external_udf_uris=[udf_uri],
                         allow_large_results=True,
                         write_disposition=bigquery.JOB_WRITE_TRUNCATE)
```

oh and don't forget to run `gsutil cp ./udf.js gs://udf.js` before executing the script!

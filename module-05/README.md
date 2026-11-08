# Module 05: Batch Processing (Spark)

Notebook và script PySpark trên dữ liệu NYC taxi.

| File | Nội dung |
|---|---|
| `code/03_test`, `04_pyspark` | Cài Spark, đọc CSV, ghi parquet, partition. |
| `code/05_taxi_schema` | Định nghĩa schema cho yellow/green. |
| `code/06_spark_sql(.py, _big_query.py)` | Spark SQL; script nhận `--input_green --input_yellow --output`, bản BigQuery ghi kết quả ra BQ. |
| `code/07_groupby_join`, `08_rdds` | Group by, join, RDD. |
| `code/09_spark_gcs`, `cloud.md` | Đọc/ghi GCS, chạy Spark trên cloud (Dataproc). |
| `code/download_data.sh` | `./download_data.sh yellow 2020` tải 12 tháng dữ liệu. |
| `code/homework.ipynb` | Bản gốc của khoá. |
| `homework_result.ipynb` | **Bài làm**: Q1 version Spark, Q2 kích thước parquet, Q3 số chuyến ngày 15/10, Q4 chuyến dài nhất, Q5 zone ít đón nhất (FHV 10/2019). |

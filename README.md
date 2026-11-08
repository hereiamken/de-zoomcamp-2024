# Data Engineering Zoomcamp 2024

Bài tập, ghi chú và capstone của mình cho khoá [DataTalksClub Data Engineering Zoomcamp 2024](https://github.com/DataTalksClub/data-engineering-zoomcamp).

## Cấu trúc

| Thư mục | Nội dung | Công nghệ |
|---|---|---|
| [module-01](module-01) | Containerization & IaC | Docker, Postgres, Terraform (GCP) |
| [module-02](module-02) | Workflow orchestration | Mage: GCS / Postgres pipelines |
| [module-03](module-03) | Data warehouse | BigQuery (partition, cluster), Terraform |
| [module-04](module-04) | Analytics engineering | dbt (`taxi_rides_ny`), BigQuery |
| [module-05](module-05) | Batch processing | Spark / PySpark, Spark SQL, GCS |
| [module-06](module-06) | Streaming | Kafka, PySpark Structured Streaming |
| [workshop-01](workshop-01) | Workshop 1: homework | Python / notebook |
| [workshop-02](workshop-02) | Workshop 2: stream processing SQL | RisingWave, NYC taxi data |
| [workshop-risingwave](workshop-risingwave) | Cấu hình docker cho workshop RisingWave | Prometheus, Grafana |
| [de-zoomcamp-2024-capstone](de-zoomcamp-2024-capstone) | **Capstone**: UEFA Champions League 2016-2022 | Mage, GCS, BigQuery, dbt, Terraform |

## Capstone

Pipeline cho dữ liệu UEFA Champions League (matches, teams, players, stadiums, goals, managers):

```
CSV (data/) → Mage ETL → GCS (data lake) → BigQuery staging → dbt (dim / fact) 
```

Terraform dựng hạ tầng GCP. Chi tiết xem [de-zoomcamp-2024-capstone/README.md](de-zoomcamp-2024-capstone/README.md).

## Lưu ý khi chạy lại

- Các file bí mật (`keys/`, service account JSON), `*.tfstate`, `.terraform/`, `venv/` **không** được commit (xem [.gitignore](.gitignore)). Tự tạo service account GCP và đặt vào `keys/`.
- Cần cài: Docker, Terraform, Python 3.9+, và tài khoản GCP cho các module 1-4 và capstone.
- Dữ liệu lớn (NYC taxi CSV/parquet cho module 1) cần tải lại theo hướng dẫn của khoá.

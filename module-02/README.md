# Module 02: Workflow Orchestration (Mage)

Các block của một pipeline [Mage](https://www.mage.ai/) xử lý NYC **green taxi** (10-12/2020). Repo chỉ giữ code block, không giữ cả project Mage.

| File | Loại block | Việc làm |
|---|---|---|
| `load_data_from_uri.py` | data loader | Tải 3 file `green_tripdata_2020-1x.csv.gz` từ DataTalksClub, ép dtype, parse datetime. |
| `transform_data.py` | transformer | camelCase → snake_case, bỏ chuyến có `passenger_count = 0` hoặc `trip_distance = 0`; kèm các `@test`. |
| `export_data_to_postgres.py` | data exporter | Ghi bảng `mage.green_taxi` vào Postgres. |
| `export_data_to_gcp.py` | data exporter | Ghi parquet partition theo `lpep_pickup_date` vào GCS bucket `ny_green_taxi_module_2`. |

Luồng: `load_data_from_uri → transform_data → export_data_to_postgres / export_data_to_gcp`.

Cần: Mage (Docker), Postgres cấu hình trong `io_config.yaml`, service account GCP (đường dẫn trong `export_data_to_gcp.py`; **không commit key**).

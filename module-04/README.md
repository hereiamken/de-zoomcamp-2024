# Module 04: Analytics Engineering (dbt + BigQuery)

- `web_to_gcs.py`: upload dữ liệu taxi (green/yellow/fhv) lên GCS bucket `dbt_ny_taxi_module_4`.
- `terraform/`: bucket + dataset BigQuery.
- `taxi_rides_ny/`: dbt project.
  - `models/staging/`: `stg_green_trips`, `stg_yellow_trips`, `stg_fhv_trips` (view).
  - `models/core/`: `dim_zones`, `fact_trips`, `fact_fhv_trips`, `dm_monthly_zone_revenue`.
  - `macros/get_payment_type_description.sql`, `seeds/taxi_zone_lookup.csv`.
- `question_3.png`: ảnh kết quả homework.

## Chạy
```bash
cd taxi_rides_ny
dbt deps
dbt seed
dbt build   # hoặc: dbt build --vars 'is_test_run: false'
```
Cần profile dbt (`default`) trỏ tới BigQuery; không commit credentials.

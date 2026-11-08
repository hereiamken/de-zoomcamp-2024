# Capstone: UEFA Champions League 2016-2022

Data pipeline end-to-end trên GCP cho bộ dữ liệu UEFA Champions League (teams, stadiums, players, managers, matches, goals).

```
data/*.csv, *.xlsx ─► Mage ETL (mage_etl/) ─► GCS (data lake)
                                              │
                         external tables ◄────┘
                              │  bq_datawarehouse/staging/*.sql
                              ▼
                       BigQuery stg_* ─► dbt (dbt_ucl/) ─► dim_* / fact_*
```

| Thư mục / file | Vai trò |
|---|---|
| `data/` | Dữ liệu nguồn (file Excel gốc + csv từng sheet). |
| `loads_to_stg_datalake.py` | Đọc từng sheet Excel, upload lên bucket `dezoomcamp2024_capstone`. |
| `mage-docker/`, `mage_etl/` | Mage chạy bằng Docker; loader / transform / exporter (`exporter_to_gcs.py`) cho từng bảng. |
| `bq_datawarehouse/staging/` | SQL tạo `stg_*` (và bản partitioned/clustered) từ external tables. |
| `dbt_ucl/` | dbt: `staging_*` → `dim_cities`, `dim_countries`, `dim_stadiums`, `dim_teams`. |
| `terraform/` | GCS bucket + BigQuery dataset. |
| `note.txt` | Ghi chú thiết kế: dim (matches, dates, teams, players, stadiums, goals), fact (goals, matches, teams), top 10 ghi bàn / kiến tạo. |

## Chạy
```bash
pip install -r requirements.txt
export GOOGLE_APPLICATION_CREDENTIALS=keys/<service-account>.json   # keys/ không được commit
cd terraform && terraform init && terraform apply && cd ..
python loads_to_stg_datalake.py
# chạy các SQL trong bq_datawarehouse/staging/ rồi:
cd dbt_ucl && dbt build
```

# Module 03: Data Warehouse (BigQuery)

- `web_to_gcs.py`: tải `green_tripdata_<year>-<month>.csv.gz` từ DataTalksClub và upload lên GCS (bucket mặc định `ny_green_taxi_module_3`, đổi bằng biến môi trường `GCP_GCS_BUCKET`).
- `terraform/`: tạo GCS bucket (lifecycle xoá multipart dở dang) và BigQuery dataset.
- `images/`: ảnh kết quả homework (external table, bảng thường, partitioned vs non-partitioned, ...).

## Chạy
```bash
pip install pandas pyarrow google-cloud-storage requests
export GOOGLE_APPLICATION_CREDENTIALS=<path-to-key.json>
cd terraform && terraform init && terraform apply
cd .. && python web_to_gcs.py
```
Sau đó tạo external table / bảng native / partition + cluster trong BigQuery từ dữ liệu trên GCS.

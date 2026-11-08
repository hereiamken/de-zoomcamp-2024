# Module 01: Containerization & Infrastructure as Code

## Nội dung
| Thư mục | Mô tả |
|---|---|
| `docker-test/` | Dockerfile + `pipeline.py` nhận tham số qua `sys.argv` (demo cơ bản). |
| `ingest-nyc-taxi-yellow/` | Ingest NYC taxi (yellow/green) và zone lookup vào Postgres bằng pandas + SQLAlchemy theo chunk 100k dòng. `docker-compose.yaml` dựng Postgres 13 (port 5431) + pgAdmin (port 8080). Có notebook kiểm tra kết nối/upload và `note-homework.txt`. |
| `terraform/` | `terraform_basic` (GCS bucket) và `terraform_with_variables` (tách biến), dùng provider Google. |

## Chạy
```bash
cd ingest-nyc-taxi-yellow
docker compose up -d
python ingest_data_green.py --user=root --password=root --host=localhost --port=5431 \
  --db=ny_taxi --table_name=green_taxi_trips --url=<csv-url>

cd ../terraform/terraform_with_variables
terraform init && terraform plan -var="project=<gcp-project-id>"
```
Ảnh minh hoạ lời giải homework nằm trong `ingest-nyc-taxi-yellow/images/`.

> Không commit: dữ liệu Postgres, file `.csv.gz`, `keys/`, `*.tfstate`.

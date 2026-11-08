# Workshop 02: Stream Processing bằng SQL (RisingWave)

Dùng materialized view của [RisingWave](https://risingwave.com/) trên dữ liệu NYC yellow taxi 01/2022.

- `datasets/`: `yellow_tripdata_2022-01.parquet` (~37 MB) và `taxi_zone.csv`.
- `queries/`:
  - `question1.sql`: cặp zone có thời gian chuyến trung bình lớn nhất (`highest_average_trip_time`).
  - `question2.sql`: số chuyến của cặp zone đó (`number_of_trips`).
  - `question3.sql`: 3 zone đón khách nhiều nhất trong 17 giờ cuối của dữ liệu.
- `answers/`: ảnh kết quả.

Bảng `trip_data` và `taxi_zone` được nạp vào RisingWave trước; cấu hình môi trường xem [../workshop-risingwave](../workshop-risingwave).

# IRIS Face Recognition Add-on

[Tiếng Việt](#tiếng-việt) | [English](#english)

## Tiếng Việt

Repository này đóng gói [`anhnvme/facedetect`](https://github.com/anhnvme/facedetect) thành Home Assistant OS add-on.

IRIS chạy nhận diện khuôn mặt local bằng InsightFace. Database, ảnh upload, model và log nằm trên máy Home Assistant, không cần cloud account.

### Thông tin nhanh

- Add-on folder: `iris_face_recognition/`
- Image chạy bên trong: `ghcr.io/anhnvme/facedetect:latest`
- Container port: `80`
- Host port mặc định: `8080`
- Data mặc định trong container: `/data`

### Cài đặt

1. Đẩy repository này lên GitHub.
2. Vào Home Assistant: **Settings -> Add-ons -> Add-on Store -> Repositories**.
3. Thêm URL repository này.
4. Cài add-on **IRIS Face Recognition**.
5. Start add-on.
6. Mở từ sidebar/Ingress hoặc vào `http://homeassistant.local:8080`.

### Cấu hình

```yaml
data_dir: /data
```

`data_dir` là path mà add-on đưa cho IRIS làm thư mục `/data` để lưu dữ liệu.

Mặc định để `/data` là đủ. Home Assistant giữ thư mục này bền vững cho add-on.

Nếu muốn dữ liệu nằm ở khu vực dễ truy cập hơn, đổi thành:

```yaml
data_dir: /share/iris
```

hoặc:

```yaml
data_dir: /media/iris
```

IRIS sẽ lưu bên trong path đó:

```text
database/iris.sqlite3
models/insightface/
uploads/
```

### Đổi port

App lắng nghe container port `80`.

Trong trang add-on của Home Assistant, vào **Network** và đổi mapping của `80/tcp` sang port host mong muốn. Mặc định là `8080`.

### Ghi chú

InsightFace pretrained models có thể bị giới hạn cho mục đích nghiên cứu phi thương mại. Xem license upstream trước khi dùng thương mại.

## English

This repository packages [`anhnvme/facedetect`](https://github.com/anhnvme/facedetect) as a Home Assistant OS add-on.

IRIS runs local face recognition with InsightFace. The database, uploaded images, models, and logs stay on the Home Assistant machine. No cloud account is required.

### Quick Info

- Add-on folder: `iris_face_recognition/`
- Runtime image: `ghcr.io/anhnvme/facedetect:latest`
- Container port: `80`
- Default host port: `8080`
- Default container data directory: `/data`

### Install

1. Push this repository to GitHub.
2. In Home Assistant, go to **Settings -> Add-ons -> Add-on Store -> Repositories**.
3. Add this repository URL.
4. Install **IRIS Face Recognition**.
5. Start the add-on.
6. Open it from the sidebar/Ingress or visit `http://homeassistant.local:8080`.

### Configuration

```yaml
data_dir: /data
```

`data_dir` is the path passed to IRIS as its `/data` storage directory.

The default `/data` is enough. Home Assistant keeps it persistent for this add-on.

If you want the data in an easier-to-access location, use:

```yaml
data_dir: /share/iris
```

or:

```yaml
data_dir: /media/iris
```

IRIS stores these files under that path:

```text
database/iris.sqlite3
models/insightface/
uploads/
```

### Change Port

The app listens on container port `80`.

In the Home Assistant add-on page, open **Network** and change the `80/tcp` host mapping to any port you want. The default is `8080`.

### Notes

InsightFace pretrained models may be limited to non-commercial research use. Review the upstream licensing notes before commercial use.

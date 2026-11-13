# Báo cáo cá nhân — BuiThaoLinh-2A202603093

## 0. Thông tin học viên

- Họ tên: Bùi Thảo Linh
- MSSV: 2A202603093
- Email: ...
- Link repository: https://github.com/buitlinhcv-alt/K5-L2-BuiThaoLinh-2A202603093-KeypointPose-Student
- Phiên bản CVAT (Help → About): ...
- Máy: hệ điều hành Windows · RAM 32 GB · chạy CVAT chế độ đầy đủ
- Bộ ảnh (`src/exports/assignment.json` do `lab.py setup` tạo): có
- Giờ bắt đầu: ...
- Giờ kết thúc: ...

## 1. Kiểm tra label (CP0)

| Label | Kiểu | Số điểm | Tên điểm đúng bảng của lab? | Đúng thứ tự? | Số cạnh |
|---|---|---:|---|---|---:|
| `person` | Skeleton | 17 | Có | Có | 19 |
| `face` | Skeleton | 13 | Có | Có | ... |

Mẫu `person` dựng theo người quay mặt về camera (các điểm `left_*` nằm bên phải khung mẫu)? Có

Cách đổi cờ `occluded` / `outside` cho **một điểm** trên phiên bản CVAT này: Nhấp chuột phải vào điểm cụ thể (node) trên skeleton rồi chọn trạng thái tương ứng (occluded/outside), hoặc bấm chọn điểm rồi dùng phím tắt tương ứng được cấp trong CVAT.

## 2. Số lượng đã gán và thời gian (CP1, CP2)

| Nhóm ảnh | Số ảnh | Số skeleton đã gán | Số người dưới 60 px (không gán) | Số poster / gương / màn hình bỏ qua | Thời gian (phút) |
|---|---:|---:|---:|---:|---:|
| `easy` | 5 | ... | ... | ... | ... |
| `occluded` | 3 | ... | ... | ... | ... |
| `back` | 2 | ... | ... | ... | ... |
| `small` | 1 | ... | ... | ... | ... |
| `crowd` | 1 | ... | ... | ... | ... |
| `faces` | 8 | 8 | — | — | ... |

- Số ảnh người đã xong ở mốc phút 105: ___ / 10
- Thời gian thực tế (phút): CP1 ___ · CP2 ___ · CP3 ___
- Ảnh tốn thời gian nhất là ảnh nào, vì sao? ...

## 3. Bảng ca khó (CP1, CP2)

| Ảnh | Người / mặt | Điểm | Cờ đã chọn | Phân vân giữa | Lý do chọn |
|---|---|---|---:|---|---|
| ... | ... | ... | ... | v = 1 và v = 0 | ... |

## 4. Bảng tự review (CP3)

| Ảnh | Người / mặt | Điểm | Mã lỗi | Ghi chú | Đã sửa? |
|---|---|---|---|---|---|
| 000000461002.jpg | Người #2 | knee, ankle | lr_swap | Có thể gán nhầm trái/phải hoặc người đang vắt chéo chân. | Có/Không |
| 000000542160.jpg | Người #1 | knee, ankle | lr_swap | Có thể gán nhầm trái/phải hoặc người đang vắt chéo chân. | Có/Không |
| ... | ... | ... | ok | Không có lỗi. | Rồi |

Tổng hợp số lỗi theo mã:

| `lr_swap` | `vis_flag` | `position` | `missing` | `extra` | `ok` |
|---:|---:|---:|---:|---:|---:|
| 2 | 0 | 0 | 0 | 0 | 1 |

Điểm còn phân vân giữa `v = 1` và `v = 0` (ghi cả hai lựa chọn và lý do chọn):
...

## 5. Kiểm file xuất và kết quả tự kiểm (CP4)

Tự kiểm tay trong file JSON:

| File | Người / mặt kiểm (ảnh, thứ tự) | Số phần tử `keypoints` | Điểm `outside` ra `v = 0`, `occluded` ra `v = 1`? | `num_keypoints` khớp? |
|---|---|---:|---|---|
| `BuiThaoLinh_persons.zip` | ... | 51 | Có | Có |
| `BuiThaoLinh_persons.zip` | ... | 51 | Có | Có |
| `BuiThaoLinh_faces.zip` | ... | 39 | Có | Có |

Sau khi xuất, CVAT ghi `occluded` thành `v = 1` và `outside` thành `v = 0`. Tọa độ của điểm `outside` trong file là `0, 0` hay tọa độ cũ? Tọa độ cũ.

Hai job đã chuyển sang completed trên CVAT? Có.

Dán phần **TÓM TẮT** in ra từ `src/check_submission.py`:

```text
----- TÓM TẮT (dán vào báo cáo mục 5) -----
- File person: BuiThaoLinh_persons.zip
  Số ảnh: 12 · số skeleton `person`: 19 · mỗi annotation 51 số
  Skeleton theo ảnh: 000000021235=1, 000000150192=1, 000000157271=2, 000000183176=2, 000000297227=2, 000000314154=1, 000000349521=1, 000000390585=1, 000000461002=2, 000000467300=2, 000000542160=3, 000000564304=1
  Cờ v: v=2 214 (66%) · v=1 41 (13%) · v=0 68 (21%)
  num_keypoints trung bình: 13.4
- File face: BuiThaoLinh_faces.zip
  Số ảnh: 8 · số skeleton `face`: 8 · mỗi annotation 39 số
  Skeleton theo ảnh: face_232598=1, face_249336=1, face_300399=1, face_301643=1, face_356144=1, face_425647=1, face_476363=1, face_490361=1
  Cờ v: v=2 88 (85%) · v=1 15 (14%) · v=0 1 (1%)
  num_keypoints trung bình: 12.9
- Ghi chú: 69 điểm v = 0 vẫn mang tọa độ cũ (CVAT 2.x xuất như vậy; chuẩn COCO ghi 0, 0). Không phải lỗi: điểm v = 0 bị bỏ qua khi huấn luyện và khi chấm.
- Số [LỖI]: 0 · số [CẢNH BÁO]: 2
Kết quả: ĐẠT (đọc lại từng cảnh báo ở trên)

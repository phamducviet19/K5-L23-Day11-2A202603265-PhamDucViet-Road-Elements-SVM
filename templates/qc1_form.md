# Phiếu QC 1 — Road v1.0

Lô được kiểm (học viên): 2A2026032923       Người kiểm (học viên):  2A202603265
Ngày:         20/11                 Phiên bản guideline: Road v1.0
File được kiểm (tên + `revision` trong manifest): A01 đến A06; tên file xuất và `revision`: chưa cung cấp
Số ảnh kiểm: 6 (+ 0 ảnh thêm, ghi riêng)   Số nhãn đã kiểm (shape + tag): 78

## Tổng hợp theo mã
| Mã | Loại lỗi | Số mục kiểm | Số lỗi | Mức |
| --- | --- | ---: | ---: | --- |
| QC1-01 tag | bỏ sót | 24 | 1 | nặng |
| QC1-02 đủ L1, R1 | bỏ sót | 13 | 0 | nặng |
| QC1-03 position | sai thuộc tính / thừa | 65 | 0 | nặng |
| QC1-04 tâm vạch, chiều, điểm dừng | sai phạm vi | 26 | 1 | chính |
| QC1-05 vạch đứt, che | sai phạm vi / sai thuộc tính | 7 | 0 | chính |
| QC1-06 style, color, kind | sai thuộc tính | 13 | 0 | chính |
| QC1-07 vùng lái | sai phạm vi / bỏ sót | 15 | 2 | chính |
| QC1-08 đèn, màu | bỏ sót / sai phạm vi / sai thuộc tính | 6 | 0 | nặng / chính |
| QC1-09 facing, type, group, biển phụ | sai thuộc tính | 10 | 1 | chính |
| QC1-10 hình in, đủ biển | bỏ sót / sai phạm vi | 10 | 0 | chính |
| QC1-11 fisheye | sai phạm vi / sai thuộc tính | 0 | 0 | chính |
| QC1-12 file | lỗi file | 1 | 0 | nhẹ / nặng |

Số lỗi tổng hợp theo các phát hiện được cung cấp; 0 nghĩa là chưa ghi nhận lỗi trong danh sách này. A04 chưa tính là lỗi, chờ lead xác nhận. Số mục kiểm theo từng mã cần bổ sung từ kết quả kiểm thực tế; tổng số nhãn đã kiểm là 78. Lỗi `road_curb` dừng sớm được xếp QC1-04 (sai phạm vi / điểm dừng).

## Danh sách lỗi (mỗi lỗi một dòng)
| # | Mã | Ảnh | Nhãn (label, id) | Mức | Mô tả ngắn |
| --- | --- | --- | --- | --- | --- |
| 1 | QC1-04 | A01 | road_curb; id chưa cung cấp | chính | Polyline chưa bao hết đoạn lề đường nhìn thấy, dừng sớm. Cần kéo dài theo mép lề đến hết đoạn còn nhìn thấy. |
| 2 | QC1-01 | A01 | weather (tag bị thiếu) | nặng | Bỏ sót tag thời tiết. Cần thêm tag weather với giá trị phù hợp điều kiện trong ảnh. |
| 3 | QC1-07 | A05 | drivable (direct); id chưa cung cấp | chính | Vùng làn đang đi được vẽ tràn vào khu vực đỗ xe. Cần chỉnh polygon để loại khu vực đỗ xe khỏi vùng direct. |
| 4 | QC1-09 | A06 | traffic_sign; id chưa cung cấp | chính | Gán sai group của biển báo: đang là warning (cảnh báo nguy hiểm), phải sửa thành prohibitory (biển cấm). |
| 5 | QC1-07 | A06 | drivable (vùng làn rẽ trái bị thiếu) | chính | Bỏ sót vùng lái của làn rẽ trái. Cần bổ sung polygon cho phần mặt đường của làn rẽ trái và chọn area_type theo vị trí so với làn đang đi. |

## Ca mơ hồ
| Ảnh | Câu hỏi cho lead | Lời đáp (nếu có) |
| --- | --- | --- |
| A04 | Hai vạch trắng có khoảng cách lớn hơn thông thường: xác nhận đây là một vạch đôi (kind = double) hay hai vạch đơn riêng biệt (kind = single)? Cần hướng dẫn cách gán polyline tương ứng. | Chưa có; chờ lead xác nhận trước khi kết luận QC1-06. |

## Quyết định
Lỗi nặng: 1   Lỗi chính: 4 / 78 nhãn = 5,13 %   Lỗi nhẹ: 0   Ca chờ lead: 1

Quyết định (Release / Hold / Rework): **Rework**.

Lý do (theo luật của phiếu): Tỷ lệ lỗi chính là 4 / 78 × 100 = 5,13 %, vượt ngưỡng 5 %, nên Rework. Theo mức lỗi đang ghi trong bảng, còn có 1 lỗi nặng (A01 thiếu tag weather). A04 vẫn chờ lead xác nhận và chưa tính vào số lỗi.

Lưu ý đối chiếu thang mức lỗi Road v1.0: thiếu tag weather được xếp mức nhẹ. Nếu điều chỉnh lỗi này về mức nhẹ theo thang, tổng sẽ là 0 lỗi nặng, 4 lỗi chính, 1 lỗi nhẹ; quyết định vẫn là Rework vì tỷ lệ lỗi chính vượt 5 %.


Loại lỗi: bỏ sót = thiếu nhãn phải có; thừa = gán cái không phải đối tượng; sai phạm vi = hình lệch, sai chiều, dừng sai chỗ, tràn vùng. Ba loại này theo cách chia lỗi gán nhãn của ISO/IEC 5259-4 (mục 8.4.2); "sai thuộc tính" và "lỗi file" là khóa học thêm. Cách xếp mức: [thang mức lỗi](../docs/qc_severity_road_v1.0.md).

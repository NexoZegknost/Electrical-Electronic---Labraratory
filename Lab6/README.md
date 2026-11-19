# Chapter 6 - Field Effect Transistor / FET (CO2104)

Báo cáo LaTeX theo mẫu Lab 4, 5. Biên dịch: `latexmk` (XeLaTeX). Đổi tên PDF thành `report.pdf` khi nộp.

## Nội dung báo cáo
| Mục | Bài | Loại | Tệp tex | Ảnh (`images/sim/`) | Thư mục PSpice | Tệp mạch nộp |
|---|---|---|---|---|---|---|
| 2.1 | JFET – DC Sweep | bắt buộc | ex01 | ex21_dc | pspice/ex21 | ex2.1.dsn |
| 2.2 | JFET – Nested DC Sweep | bonus | ex02 | ex22_nested | pspice/ex22 | ex2.2.dsn |
| 2.3.1 | JFET Self bias | bắt buộc | ex03 | ex231_bias | pspice/ex231 | ex2.3.1.dsn |
| 2.3.2 | JFET Voltage divider | bắt buộc | ex04 | ex232_bias | pspice/ex232 | ex2.3.2.dsn |
| 3.1 | Depletion-mode MOSFET | bonus | ex05 | ex31_dc, ex31_bias | pspice/ex31 | ex3.1.dsn |
| 3.2 | Enhancement-mode MOSFET | bắt buộc | ex06 | ex32_dc | pspice/ex32 | ex3.2.dsn |
| 4.1 | MOSFET as a switch | bắt buộc | ex07 | ex41_tran, ex41_bias_on, ex41_bias_off | pspice/ex41 | ex4.1.dsn |
| 4.2 | MOSFET Motor Controller | bonus | ex08 | ex42_tran | pspice/ex42 | ex4.2.dsn |
| 4.3 | Complementary MOSFET Motor Controller | bonus | ex08 | ex43_tran | pspice/ex43 | ex4.3.dsn |

Section 5 (Altium Designer) không yêu cầu. Bỏ bài bonus nào thì comment dòng `\input` tương ứng trong `main.tex` (số mục vẫn đúng theo đề).

Ô vàng `\fillcell` = số liệu đọc từ mô phỏng; khung cam = chỗ dán ảnh (lưu đúng tên tệp ở bảng trên là tự hiện).

## Model PSpice dùng để tính lý thuyết
- `JbreakN`: BETA = 1e-4 A/V², VTO = -2 V → IDSS = 400 µA, VP = -2 V (đề ghi "400mA" là nhầm đơn vị).
- `MbreakND`: KP = 20 µA/V², W = L = 100 µm, VTO = -4 V → IDSS = 160 µA, VP = -4 V.
- `MbreakN`: KP = 20 µA/V², VTO = 0 → k = 10 µA/V².

## Lưu ý
- 2.3.2: với JbreakN, VGS ra dương (~ +0.49 V), tiếp giáp cổng phân cực thuận, VG ≈ 2.55 V chứ không phải 4.8 V.
- 4.1: MbreakN mặc định chỉ cho ID ≈ 0.2 mA (không đóng được tải). Báo cáo có thêm trường hợp sửa model KP = 1 (Edit PSpice Model) để thấy ID ≈ 120 mA.

## Nộp bài
`2510290_NguyenHuynhHuuDuc_Chapter6.zip` gồm `report.pdf` và các file `.dsn` ở bảng trên.

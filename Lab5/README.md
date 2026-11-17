# Chapter 5 - Operational Amplifier / OPAMP (CO2104)

## Yêu cầu của đề
- **Bắt buộc:** 3.1 Voltage Follower; 3.3 Follower with Gain; 3.4 Summing (non-inverting); 3.5 Low Pass Filter (inverting); 3.7 Schmitt Trigger.
- **Bonus (vẫn làm):** 3.4 Inverting Summing; 3.5 Non-inverting Low Pass Filter.
- **Không yêu cầu (đã bỏ khỏi khung):** 3.2 High-Current Follower, 3.6 High Pass Filter, Section 4 Altium.

## File nộp
`<MSSV>_<HoVaTen>_Chapter5.zip` → `2510290_NguyenHuynhHuuDuc_Chapter5.zip`, gồm:
- Mỗi bài một file mạch PSpice (đặt tên theo đề: `ex3.1.dsn`, `ex3.3.dsn`, `ex3.4.dsn`, `ex3.5.dsn`, `ex3.7.dsn`; bonus tự đặt: `ex3.4b.dsn`, `ex3.5b.dsn`).
- `report.pdf` (đổi tên từ `main.pdf`): tính toán lý thuyết, ảnh/kết quả mô phỏng, so sánh lý thuyết - mô phỏng, đồ thị AC Sweep + xác định tần số cắt (Low Pass), nhận xét/giải thích (đặc biệt Schmitt).

```
Lab5/
├── Docs/Ch5.pdf       đề gốc
├── main.tex, tex/     khung báo cáo (ex01..ex05: từng bài, đã có lời giải lý thuyết, giá trị lý thuyết trong bảng và nhận xét)
├── images/given/      fig5_01..fig5_17.png - ảnh trích từ đề
├── images/sim/        ảnh PSpice của bạn
├── pspice/            project PSpice (.gitignore)
└── report/            nơi tạo file zip để nộp
```
Biên dịch: `latexmk` (XeLaTeX, PDF ra `main.pdf` (hoặc `build/main.pdf`)). Ảnh chưa có thì hiện khung cam ghi sẵn tên tệp.

## Thứ tự làm bài
| Mục | Bài | Việc cần làm | Tệp tex | Tệp mạch |
|---|---|---|---|---|
| 3.1 | Voltage Follower | Bias Point; đổi `R15` (bảng 4 giá trị); chứng minh `Vout = V(+)` | ex01 | ex3.1.dsn |
| 3.3 | Follower with Gain | Vin = 2 V, gain 3, nguồn tải 12 V, RLOAD = 1k; chọn R1, R2 | ex02 | ex3.3.dsn |
| 3.4 | Summing không đảo | R1=1k, R2=2k, R3=5k, Rf=9k, Ri=1k; V1..V3 = 1, 2, 3 V | ex03 | ex3.4.dsn |
| 3.4 (bonus) | Summing đảo | R1=1k, R2=2k, R3=10k; Vi1=1 V, Vi2=5 V | ex03 | ex3.4b.dsn |
| 3.5 | LPF đảo | R2=10k, C=1n; AC Sweep Linear 1 Hz - 50 kHz, 200 điểm; xác định fc | ex04 | ex3.5.dsn |
| 3.5 (bonus) | LPF không đảo | Tự tính R, C (gain 10, cùng fc); AC Sweep | ex04 | ex3.5b.dsn |
| 3.7 | Schmitt Trigger | OPAMP VPOS/VNEG = ±5 V; VSIN (VOFF 0, VAMPL 5, FREQ 50); Time Domain; giải thích ±4 V | ex05 | ex3.7.dsn |

## Kết quả lý thuyết (đã viết trong báo cáo; ô cam = số mô phỏng cần điền)
- 3.1: `Vout = V(+) = 3 V` với mọi `R15`.
- 3.3: chọn `R1 = 10k`, `R2 = 20k` → gain 3, `Vout = 6 V`, `I_LOAD = 6 mA`, ngõ ra op-amp ≈ 6.7 V.
- 3.4 không đảo: `V_IN ≈ 1.529 V`, `Vout ≈ 15.29 V` → vượt nguồn mặc định 15 V nên bị kẹp ≈ 15 V; chạy thêm với `VPOS = 20 V`.
- 3.4 đảo (bonus): `Vo = -35 V` → bão hòa ≈ -15 V; chạy thêm với `VPOS/VNEG = ±40 V`.
- 3.5 đảo: `f_H ≈ 15.92 kHz`; gain DC 10 (20 dB, Vout 20 V); tại f_H 7.07 (17 dB, 14.14 V).
- 3.5 không đảo (bonus): `R = 9k`, `C = 1.12 nF` → gain 10, `f_c ≈ 15.95 kHz`.
- 3.7: ngõ ra bão hòa ±5 V, `V(+) = ±4 V` = hai ngưỡng chuyển; chuyển tại 2.95 ms và 12.95 ms (+ k·20 ms). Profile: 100 ms, max step 0.1 ms.

Các chỗ có `% TODO` trong tex: phần nhận xét viết theo kết quả dự kiến, kiểm lại sau khi có số liệu mô phỏng.

## Danh sách ảnh cần lưu trong `images/sim/`
| Tệp | Nội dung |
|---|---|
| `ex31_bias.png` | Bias Point mạch follower |
| `ex33_bias.png` | Bias Point follower with gain |
| `ex34_bias.png` | Bias Point cộng không đảo |
| `ex34b_bias.png` | Bias Point cộng đảo (bonus) |
| `ex35_sch.png`, `ex35_ac.png` | Sơ đồ và đồ thị AC Sweep LPF đảo (đánh dấu fc) |
| `ex35b_sch.png`, `ex35b_ac.png` | Sơ đồ và AC Sweep LPF không đảo (bonus) |
| `ex37_sch.png`, `ex37_tran.png` | Sơ đồ và kết quả Time Domain Schmitt |

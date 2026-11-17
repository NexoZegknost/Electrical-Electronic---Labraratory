# Chapter 5 - Operational Amplifier / OPAMP (CO2104)

Đề: PSpice (mục 3.1 - 3.7) + Altium Designer (LED driver, Relay controller). Báo cáo **có yêu cầu** ("Exercise and Report").
Khung báo cáo LaTeX theo cùng mẫu Lab 4 (`main.tex`, `tex/`, `latexmkrc`, ô dán ảnh màu cam, hộp `Tính toán` / `Đáp số` / `Nhận xét`).

```
Lab5/
├── Docs/Ch5.pdf        đề gốc
├── main.tex, tex/      khung báo cáo (ex00 = giới thiệu, ex01..ex09 = từng bài)
├── images/given/       fig5_01..fig5_17.png - ảnh trích từ đề (đã chèn sẵn trong báo cáo)
├── images/sim/         ảnh PSpice của bạn (sơ đồ, Probe)
├── images/altium/      ảnh Altium (schematic, PCB, 3D)
├── pspice/             project PSpice (bị .gitignore)
├── altium/             project Altium (LED driver, Relay)
└── report/             nơi tạo file zip để nộp
```

Biên dịch: `latexmk` (XeLaTeX, PDF ra `build/main.pdf`) hoặc VS Code LaTeX Workshop, giống Lab 4.
Ảnh chưa có thì hiện khung cam ghi sẵn tên tệp; lưu ảnh đúng tên là khung tự biến mất.

## Thứ tự làm bài (mỗi bài: mô phỏng → điền bảng → chụp ảnh → tính tay → nhận xét)

| Mục báo cáo | Bài (đề) | Việc cần làm | Tệp |
|---|---|---|---|
| 5.1 | 3.1 Voltage Follower | Bias Point; đổi `R15` (bảng 4 giá trị); chứng minh `Vout = V(+)` với mọi `R15` | ex01 |
| 5.2 | 3.2 High-Current Follower | Bias Point (V, I); giải thích kết quả | ex02 |
| 5.3 | 3.3 Follower with Gain | Vin = 2 V, gain = 3, nguồn tải 12 V, RLOAD = 1k; chọn R1, R2 | ex03 |
| 5.4 | 3.4 Summing | Không đảo (R1=1k, R2=2k, R3=5k, Rf=9k, Ri=1k; V1..V3 = 1, 2, 3 V); đảo (R1=1k, R2=2k, R3=10k; Vi1=1 V, Vi2=5 V) | ex04 |
| 5.5 | 3.5 Low Pass Filter | Đảo: AC Sweep Linear 1 Hz - 50 kHz, 200 điểm; Không đảo: tự tính R, C (gain 10, cùng fc) | ex05 |
| 5.6 | 3.6 High Pass Filter | Tự thiết kế, AC Sweep, giải thích | ex06 |
| 5.7 | 3.7 Schmitt Trigger | OPAMP VPOS/VNEG = ±5 V; VSIN (VOFF 0, VAMPL 5, FREQ 50); Time Domain; giải thích ±4 V | ex07 |
| 5.8 | 4.1 LED Driver (Altium) | Schematic + PCB + 3D | ex08 |
| 5.9 | 4.2 Relay Controller (Altium) | Schematic + PCB + 3D | ex09 |

## Giá trị tham khảo để đối chiếu với mô phỏng (tự kiểm lại bằng tính tay trong báo cáo)

- 5.1: `Vout = V(+)`, không phụ thuộc `R15` (dòng vào ngõ `-` ≈ 0).
- 5.2 (Hình 5.4: V9 = 3 V, R15 = 10k, R16 = 1k, V10 = 12 V): `Vout ≈ 3 V`, dòng tải ≈ 3 mA.
- 5.3: `Gain = 1 + R2/R1 = 3` → `R2 = 2·R1`; `Vout = 6 V`, `I_LOAD = 6 mA`.
- 5.4 không đảo: `V_IN = (V1/R1+V2/R2+V3/R3)/(1/R1+1/R2+1/R3) ≈ 1.53 V`, `Vout = (1+Rf/Ri)·V_IN ≈ 15.3 V`.
- 5.4 đảo (R3 là điện trở hồi tiếp theo Hình 5.7): `Vo = -(R3/R1·Vi1 + R3/R2·Vi2) = -35 V`. Giá trị này lớn; kiểm tra xem OPAMP có bị giới hạn bởi nguồn cấp hay không và ghi nhận xét.
- 5.5 đảo: `f_H = 1/(2π·R2·C) ≈ 15.9 kHz`; gain DC = 10 (20 dB); tại `f_H` ≈ 7.07 (≈ 17 dB).
- 5.5 không đảo (Hình 5.12: R11 = 1k ở ngõ `-`): gain DC = `1 + Rf/R11 = 10` → `Rf = 9k`; `C ≈ 1/(2π·Rf·f_H) ≈ 1.1 nF`. Điểm -3 dB thực tế lệch nhẹ so với `1/(2π·Rf·C)`, hãy kiểm tra trên đồ thị.
- 5.7 (R23 = 4k, R22 = 1k): ngõ ra bão hòa ±4 V; ngưỡng chuyển `V_TH/V_TL = ±Vsat·R23/(R22+R23) = ±3.2 V`.

## Danh sách ảnh cần chụp/lưu

Ảnh PSpice chụp sơ đồ (kèm V, I hiển thị) dùng khổ nhỏ; ảnh Probe / Altium dùng khổ lớn.

| Tệp | Nội dung |
|---|---|
| `images/sim/ex01_bias.png` | Kết quả Bias Point mạch follower (giá trị R15) |
| `images/sim/ex02_bias.png` | Kết quả Bias Point mạch high-current follower |
| `images/sim/ex03_bias.png` | Kết quả Bias Point mạch follower with gain |
| `images/sim/ex04a_bias.png` | Kết quả Bias Point mạch cộng không đảo |
| `images/sim/ex04b_bias.png` | Kết quả Bias Point mạch cộng đảo |
| `images/sim/ex05a_sch.png` | Sơ đồ mạch inverting low pass filter (PSpice) |
| `images/sim/ex05a_ac.png` | Kết quả AC Sweep: V(out) theo tần số |
| `images/sim/ex05b_sch.png` | Sơ đồ mạch non-inverting low pass filter (PSpice) |
| `images/sim/ex05b_ac.png` | Kết quả AC Sweep: V(out) theo tần số |
| `images/sim/ex06_sch.png` | Sơ đồ mạch high pass filter (PSpice) |
| `images/sim/ex06_ac.png` | Kết quả AC Sweep của high pass filter |
| `images/sim/ex07_sch.png` | Sơ đồ Schmitt trigger đã đặt marker (PSpice) |
| `images/sim/ex07_tran.png` | Kết quả mô phỏng: V_IN, V(+), V_OUT theo thời gian |
| `images/altium/ex08_sch.png` | Sơ đồ nguyên lý mạch LED driver (Altium Designer) |
| `images/altium/ex08_pcb_top.png` | PCB mạch LED driver -- lớp TOP |
| `images/altium/ex08_pcb_bottom.png` | PCB mạch LED driver -- lớp BOTTOM |
| `images/altium/ex08_3d_top.png` | Mô hình 3D mạch LED driver -- mặt trên |
| `images/altium/ex08_3d_bottom.png` | Mô hình 3D mạch LED driver -- mặt dưới / góc nghiêng |
| `images/altium/ex09_sch.png` | Sơ đồ nguyên lý mạch relay controller (Altium Designer) |
| `images/altium/ex09_pcb_top.png` | PCB mạch relay controller -- lớp TOP |
| `images/altium/ex09_pcb_bottom.png` | PCB mạch relay controller -- lớp BOTTOM |
| `images/altium/ex09_3d_top.png` | Mô hình 3D mạch relay controller -- mặt trên |
| `images/altium/ex09_3d_bottom.png` | Mô hình 3D mạch relay controller -- mặt dưới / góc nghiêng |

## Nộp bài (theo cách đặt tên các lab trước, kiểm tra lại với đề/GV)
`2510290_NguyenHuynhHuuDuc_Chapter5.zip` gồm: file báo cáo PDF (`build/main.pdf`), project PSpice, 2 project Altium (`.PrjPcb`, `.SchDoc`, `.PcbDoc`).

# Chapter 4 - Circuit Design with Altium Designer (CO2104)

```
Lab4/
├── main.tex                 file chính (chỉ \input các phần)
├── latexmkrc                cấu hình biên dịch (XeLaTeX, kết quả vào build/)
├── tex/
│   ├── preamble.tex         gói, macro, header/footer (\altfig, \altfigs, \video cho Lab 4)
│   ├── config.tex           thông tin môn học, lớp, sinh viên (sửa ở đây)
│   ├── cover.tex            trang bìa
│   └── exercises/           ex00 (giới thiệu), ex01 (7805), ex02 (LM2596)
├── images/
│   ├── common/              logo (hcmut.png)
│   ├── given/               hình đề bài (fig4_01 ... fig4_04)
│   └── altium/              ảnh chụp từ Altium:
│                              exN_sch, exN_pcb_top, exN_pcb_bottom, exN_3d_top, exN_3d_bottom (.png)
├── altium/
│   ├── ex01_7805/           project Altium mạch 7805 (.PrjPcb, .SchDoc, .PcbDoc)
│   └── ex02_lm2596/         project Altium mạch LM2596
├── report/                  file nộp bài
├── docs/
│   └── Ch4.pdf              đề bài gốc Chapter 4
└── build/                   file trung gian và main.pdf (không đưa vào git)
```

Biên dịch: chạy `latexmk` trong thư mục này, kết quả là `build/main.pdf`.
Ảnh chưa có sẽ hiện thành khung cam "Ô DÁN ẢNH" kèm đúng tên tệp cần lưu; lưu ảnh đúng tên vào `images/altium/` là khung tự biến mất.
Nộp bài: project Altium của 2 mạch và `report.pdf` (đổi tên từ `build/main.pdf`), nén thành `<MSSV>_<HoVaTen>.zip`.

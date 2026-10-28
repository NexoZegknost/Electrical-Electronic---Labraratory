# Chapter 2 - Diode Circuits Analysis (CO2103)

```
Lab2/
├── main.tex                 file chính (chỉ \input các phần)
├── latexmkrc                cấu hình biên dịch (XeLaTeX, kết quả vào build/)
├── tex/
│   ├── preamble.tex         gói, macro, header/footer
│   ├── config.tex           thông tin môn học, lớp, sinh viên (sửa ở đây)
│   ├── cover.tex            trang bìa
│   └── exercises/           ex01.tex ... ex10.tex (mỗi bài một file)
├── images/
│   ├── common/              logo (hcmut.png)
│   ├── given/               hình đề bài (exN_given.png)
│   ├── draw/                mạch vẽ lại / biến đổi (nếu có)
│   └── sim/                 ảnh kết quả mô phỏng (exN_sim.png)
├── pspice/
│   └── ex1 ... ex10/        mỗi bài một project PSpice (exN.opj, EXN.DSN)
├── docs/
│   └── Ch2.pdf              đề bài gốc Chapter 2
└── build/                   file trung gian và main.pdf (không đưa vào git)
```

Biên dịch: chạy `latexmk` trong thư mục này, kết quả là `build/main.pdf`.
Nộp bài: `ex1.dsn` ... `ex10.dsn` (lấy từ `pspice/exN/`) và `report.pdf` (đổi tên từ `build/main.pdf`), nén thành `<MSSV>_<HoVaTen>.zip`.

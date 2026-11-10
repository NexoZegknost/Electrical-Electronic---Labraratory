# Chapter 4 - Circuit Design with Altium Designer (CO2104)

Đề không yêu cầu báo cáo riêng: chỉ nộp file thiết kế Altium của 2 mạch.

```
Lab4/
├── altium/
│   ├── 7805/        7805.PrjPcb, 7805.SchDoc, 7805.PcbDoc     (mạch ổn áp 7805)
│   └── LM2596/      LM2596.PrjPcb, LM2596.SchDoc, LM2596.PcbDoc  (mạch giảm áp LM2596)
├── report/          nơi tạo file zip để nộp
├── docs/Ch4.pdf     đề bài gốc
├── images/          ảnh đề bài (given/) và ảnh chụp Altium (altium/) - chỉ cần nếu muốn làm sổ ghi chép
├── main.tex, tex/   khung báo cáo LaTeX (tùy chọn, KHÔNG bắt buộc nộp)
└── latexmkrc
```

## Yêu cầu từng mạch
1. Vẽ đầy đủ schematic theo mạch mẫu (7805: Hình 4.3; LM2596: Hình 4.4 của TI).
2. Gán footprint phù hợp cho mọi linh kiện.
3. Update PCB, sắp xếp linh kiện hợp lý, hoàn thành routing (chạy DRC không lỗi).
4. Kiểm tra PCB ở chế độ 3D (phím 3) - linh kiện và footprint hiển thị đúng.

## Nộp bài
File tối thiểu: `7805.SchDoc`, `7805.PcbDoc`, `LM2596.SchDoc`, `LM2596.PcbDoc`
(nên kèm `7805.PrjPcb`, `LM2596.PrjPcb` và thư viện tự tạo nếu có, để mở lại không bị thiếu).
Nén thành một file: `2510290_NguyenHuynhHuuDuc_Chapter4.zip`
Trước khi nén: đóng Altium, mở thử lại từng `.PrjPcb` để chắc chắn file mở được và đủ schematic + PCB.

# 🤖 Báo cáo Bài tập nhóm Môn Trí tuệ Nhân tạo

**📋 Thông tin:**

* **📚 Môn học:** MAT3508 - Nhập môn Trí tuệ Nhân tạo

* **📅 Học kỳ:** Học kỳ 1 - 2025-2026

* **🏫 Trường:** VNU-HUS (Đại học Quốc gia Hà Nội - Trường Đại học Khoa học Tự nhiên)

* **📝 Tiêu đề:** Phân tích và mô hình hóa dữ liệu giá nhà tại Boston

* **📅 Ngày nộp:** 29/11/2025

* **📄 Báo cáo PDF:** 📄 [Xem Báo cáo PDF](./Report.pdf)

* **🖥️ Slide thuyết trình:** 🖥️ [Xem slide Thuyết trình](./Phan-tich-va-Mo-hinh-hoa-Du-lieu-Gia-nha-tai-Boston.pptx)

* **📂 Kho lưu trữ:** 📁 [Github Repository](https://github.com/Gaxjvool/VNU-HUS-IntroAI-MiniProject)

  

**👥 Thành viên nhóm:**

  

| 👤 Họ và tên     | 🆔 Mã sinh viên | 🐙 Tên GitHub                           | 🛠️ Đóng góp |
|------------------|------------------|-----------------------------------------|--------------|
| Lương Quý Huy    | 21000683         | [Gaxjvool](https://github.com/Gaxjvool) | Toàn bộ |

  

---

  

## 📑 Tổng quan cấu trúc báo cáo

> ℹ️ **Lưu ý:** Nội dung dưới đây được trích xuất và tổng hợp từ báo cáo "Phân tích và mô hình hóa dữ liệu giá nhà tại Boston" của Nhóm 8.

### Chương 1: Giới thiệu
**📝 Tóm tắt dự án**
   - ✨ **Tổng quan:** Dự án xây dựng một quy trình khoa học dữ liệu hoàn chỉnh để dự đoán giá nhà trung bình (MEDV) tại Boston.
   - **Mục tiêu:** Tìm hiểu các yếu tố ảnh hưởng giá nhà, áp dụng giảm chiều dữ liệu (PCA) và so sánh hiệu năng các mô hình Hồi quy, Phân loại, Phân cụm.
   - **Kết quả nổi bật:** Hồi quy tuyến tính đạt $R^2 \approx 0.61$; Phân loại nhóm giá bằng SVM đạt độ chính xác ~85.29%.

**❓ Bài toán đặt ra**
   - 📌 **Vấn đề:** Dự đoán giá trị trung bình của căn nhà dựa trên 13 đặc trưng kinh tế - xã hội (tội phạm, thuế, giáo dục...).
   - **Thách thức:** Xử lý hiện tượng đa cộng tuyến giữa các biến, dữ liệu nhiễu, phân phối lệch và giới hạn số lượng mẫu.
   - **Ý nghĩa:** Hỗ trợ quy hoạch đô thị, phân tích thị trường bất động sản và làm bài toán chuẩn (benchmark) cho các thuật toán học máy.

### Chương 2: Phương pháp & Triển khai
**⚙️ Phương pháp**
   - 🔍 **Cách tiếp cận:** Tuân theo quy trình chuẩn: Thu thập $\to$ EDA & Tiền xử lý $\to$ Giảm chiều $\to$ Mô hình hóa $\to$ Đánh giá.
   - **Cơ sở lý thuyết & Thuật toán:**
     - **PCA:** Giảm chiều dữ liệu để khử đa cộng tuyến, giữ 95% phương sai.
     - **Hồi quy tuyến tính:** Dự báo giá trị liên tục.
     - **K-Means:** Phân cụm không giám sát để tìm cấu trúc dữ liệu.
     - **KNN & SVM:** Phân loại mức giá (Thấp/Trung bình/Cao) sau khi rời rạc hóa biến mục tiêu.
   - **Dữ liệu:** Bộ dữ liệu Boston Housing (506 mẫu, 13 đặc trưng).

**💻 Triển khai**
   - 🧩 **Công cụ:** Python, pandas, NumPy, scikit-learn, matplotlib, seaborn.
   - **Quy trình chi tiết:**
     1. **Tiền xử lý:** Xử lý giá trị thiếu bằng trung vị, chuẩn hóa Z-score (trừ biến nhị phân CHAS), xử lý đa cộng tuyến.
     2. **Mô hình hóa:** Xây dựng pipeline xử lý riêng biệt cho biến liên tục và biến phân loại sử dụng `ColumnTransformer`.

### Chương 3: Kết quả & Phân tích
**📊 Kết quả & Thảo luận**
   - 📈 **Mô hình Hồi quy:** Đạt $R^2 = 0.6086$, RMSE = 5.3572. Dự đoán tốt ở phân khúc trung bình nhưng đánh giá thấp (underestimate) các nhà giá trị cao.
   - 📈 **Mô hình Phân cụm:** Silhouette Score thấp (0.2370) cho thấy cấu trúc cụm yếu, dữ liệu phân bố liên tục thay vì tách biệt rõ ràng.
   - 📈 **Mô hình Phân loại:** SVM hoạt động tốt nhất (Accuracy 85.29%) với Precision tuyệt đối (1.0) cho lớp "Giá cao". KNN đạt 82.35%, gặp khó khăn ở lớp "Giá thấp".

### Chương 4: Kết luận
**✅ Kết luận & Hướng phát triển**
   - 🔭 **Tổng kết:** Đã xây dựng thành công pipeline xử lý dữ liệu chuẩn mực. Chứng minh được hiệu quả của việc chuyển bài toán sang phân loại (Classification) đối với tập dữ liệu này.
   - **Hạn chế:** Mô hình hồi quy tuyến tính còn đơn giản, chưa bắt được quan hệ phi tuyến; chưa tối ưu siêu tham số.
   - **Đề xuất:** Thử nghiệm Random Forest/Gradient Boosting, áp dụng kỹ thuật đặc trưng (Feature Engineering) như $LSTAT^2$.

### Tài liệu tham khảo & Phụ lục
**📚 Tài liệu tham khảo**
   - 🔗 Các nguồn uy tín: Scikit-learn Documentation, sách "Hands-On Machine Learning" (Géron), bài báo gốc của Harrison & Rubinfeld (1978).

### Phụ lục A – Hướng dẫn chạy mã nguồn (User Guide)
*(Tùy chọn – dành cho người đọc muốn tái lập quy trình chạy Notebook của dự án)*

---
Phụ lục này mô tả chi tiết cách thiết lập môi trường và chạy file Notebook (`.ipynb`) trên hai nền tảng: **Google Colab** và **Jupyter Notebook (Local)**.

---

#### A.2. Tệp tin cần chuẩn bị

1. **Tệp mã nguồn:** `Boston_Housing_Analysis.ipynb`  
2. **Tệp dữ liệu:** `HousingData.csv`

---

#### A.3. Chạy mã nguồn trên Google Colab

##### (1) Mở Notebook
- Truy cập Google Colab.  
- Chọn **File → Upload notebook** và tải lên `Boston_Housing_Analysis.ipynb`.

##### (2) Tải dữ liệu lên
- Mở tab **Files** ở thanh bên trái.  
- Chọn **Upload** và tải lên `HousingData.csv`.  
- File sẽ được lưu tại `/content/`.

##### (3) Cập nhật đường dẫn dữ liệu
Trong cell nạp dữ liệu, chạy:

```python
file_path = 'HousingData.csv'
# hoặc '/content/HousingData.csv'
```
---

#### A.4. Chạy mã nguồn trên Jupyter Notebook (Local)

##### (1) Cài đặt thư viện cần thiết

```bash
pip install pandas numpy matplotlib seaborn scikit-learn
```

##### (2) Tổ chức thư mục

```
Project_Folder/
├── Boston_Housing_Analysis.ipynb
└── HousingData.csv
```

##### (3) Mở Notebook  
- Khởi động Jupyter Notebook hoặc Jupyter Lab.  
- Mở file `Boston_Housing_Analysis.ipynb`.

##### (4) Kiểm tra đường dẫn dữ liệu

```python
file_path = 'HousingData.csv'
```

Nếu file `.csv` và Notebook nằm cùng thư mục, chương trình sẽ tự động đọc được.

##### (5) Chạy toàn bộ mã nguồn  
- Chọn **Cell → Run All**.

---

#### A.5. Xử lý lỗi thường gặp

##### Lỗi phổ biến
```
FileNotFoundError: [Errno 2] No such file or directory: 'HousingData.csv'
```

##### Nguyên nhân thường gặp
- Chưa upload file dữ liệu (khi dùng Colab).  
- File `.csv` không nằm cùng thư mục với Notebook (Local).  
- Sai đường dẫn trong biến `file_path`.

##### Cách khắc phục
1. Kiểm tra lại việc upload file.  
2. Đảm bảo dữ liệu và Notebook cùng một thư mục.  
3. Chỉnh lại biến `file_path` cho đúng vị trí file.

---

  

## 📝 Hướng dẫn nộp bài

  

### 📋 Yêu cầu

  

- **Định dạng:**

+ 🖨️ Báo cáo phải được đánh máy, trình bày rõ ràng và xuất ra định dạng PDF (khuyến nghị dùng LaTeX).

+ 🔁 Một bản báo cáo cần lưu trên kho GitHub của dự án, hai bản nộp trên Canvas (một cho giảng viên, một cho trợ giảng), và hai bản in (một cho giảng viên, một cho trợ giảng). Slide trình bày cũng thực hiện tương tự (không cần bản in slides).

- **Kho lưu trữ:** 📂 Bao gồm báo cáo PDF, slide, toàn bộ mã nguồn và tài liệu liên quan. Nếu vượt quá giới hạn dung lượng của GitHub, có thể tải lên Google Drive hoặc Dropbox và dẫn link trong tài liệu.

- **Làm việc nhóm:** 🤝 Cần ghi rõ đóng góp của từng thành viên trong nhóm.

- **Tài liệu hóa mã nguồn:**

+ 🧾 Có bình luận giải thích rõ các thuật toán/phần logic phức tạp

+ 🧪 Docstring cho hàm/phương thức mô tả tham số, giá trị trả về và mục đích

+ 📘 File README cho từng module mã nguồn, hướng dẫn cài đặt và sử dụng

+ 📝 Bình luận inline cho các đoạn mã không rõ ràng

  

### ✅ Danh sách kiểm tra trước khi nộp

- [X] ✅ Đánh dấu X vào ô để xác nhận hoàn thành

- [X] ✍️ Điền đầy đủ các mục trong mẫu README này

- [X] 📄 Hoàn thiện báo cáo PDF chi tiết theo cấu trúc trên

- [ ] 🎨 Tuân thủ định dạng và nội dung theo hướng dẫn giảng viên

- [ ] ➕ Thêm các mục riêng của dự án nếu cần

- [X] 🔍 Kiểm tra lại ngữ pháp, diễn đạt và độ chính xác kỹ thuật

- [X] ⬆️ Tải lên báo cáo PDF, slide trình bày và mã nguồn

- [X] 🧩 Đảm bảo tất cả mã nguồn được tài liệu hóa đầy đủ với bình luận và docstring

- [ ] 🔗 Kiểm tra các liên kết và tài liệu tham khảo hoạt động đúng

  

### 🏆 Tiêu chí đánh giá Bài tập nhóm

  

Xem 📄 [Rubrics.md](Rubrics.md) để biết chi tiết về tiêu chí đánh giá bài tập nhóm, bao gồm điểm tối đa cho từng tiêu chí và mô tả các mức độ đánh giá (Xuất sắc, Tốt, Cần cải thiện).

  

### 📚 Liên kết hữu ích

  

- 📄 [Mẫu báo cáo](LaTeX%20Template/main-vi.tex) - Mẫu LaTeX để viết báo cáo

- 📘 [Sổ tay dùng LaTeX](https://vietex.blog.fc2.com/blog-entry-516.html) - Hướng dẫn sử dụng LaTeX bằng tiếng Việt

- 🔎 [Một số phương pháp tải bài báo khoa học](https://hoanganhduc.github.io/misc/m%E1%BB%99t-s%E1%BB%91-ph%C6%B0%C6%A1ng-ph%C3%A1p-t%E1%BA%A3i-b%C3%A0i-b%C3%A1o-khoa-h%E1%BB%8Dc/) - Hướng dẫn một số phương pháp tải bài báo khoa học

- 📰 [AI Vietnam Blog](https://aivietnam.edu.vn/blog) - Blog với các bài viết về AI bằng tiếng Việt

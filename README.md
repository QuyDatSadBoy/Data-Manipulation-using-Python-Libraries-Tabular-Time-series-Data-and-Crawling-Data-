# Data Manipulation using Python Libraries: Tabular, Time-series Data and Crawling Data

## 📋 Tổng quan

Repository này chứa các ví dụ thực tiễn về thao tác dữ liệu sử dụng các thư viện Python phổ biến. Dự án bao gồm ba phần chính:
- **Xử lý dữ liệu dạng bảng (Tabular Data)** với Pandas
- **Thu thập dữ liệu từ web (Web Crawling)** với Selenium
- **Phân tích và thống kê dữ liệu** cơ bản

## 🎯 Mục tiêu

- Học cách xử lý và phân tích dữ liệu tabular
- Thực hành thu thập dữ liệu từ website tin tức
- Áp dụng các kỹ thuật thống kê mô tả cơ bản
- Hiểu cách sử dụng Selenium để crawl dữ liệu

## 📁 Cấu trúc thư mục

```
├── README.md
├── tabular_data_handling.ipynb          # Xử lý dữ liệu bảng với Pandas
├── selenium example.ipynb               # Ví dụ cơ bản về Selenium
├── crawl_news(text).ipynb              # Thu thập nội dung tin tức
└── crawl_news(image).ipynb             # Thu thập hình ảnh tin tức
```

## 🔧 Công nghệ sử dụng

### Thư viện Python
- **Pandas**: Xử lý và phân tích dữ liệu
- **Selenium**: Tự động hóa trình duyệt web
- **Requests**: Gửi HTTP requests
- **PIL (Pillow)**: Xử lý hình ảnh
- **tqdm**: Hiển thị progress bar

### Tools & Environment
- **Google Colab**: Môi trường phát triển
- **ChromeDriver**: Driver cho Selenium
- **Chromium Browser**: Trình duyệt headless

## 📊 Chi tiết các module

### 1. Tabular Data Handling (`tabular_data_handling.ipynb`)

**Mô tả**: Phân tích dataset quảng cáo (Advertising.csv) với các kỹ thuật thống kê mô tả.

**Chức năng chính**:
- Tải và đọc dữ liệu từ URL
- Chuyển đổi DataFrame thành list để xử lý
- Tính toán các thống kê cơ bản:
  - Tổng (Sum)
  - Trung bình (Average)
  - Trung vị (Median)
  - Min/Max
  - Phần trăm phân bổ ngân sách

**Dataset**: Advertising.csv (200 rows × 4 columns)
- TV: Ngân sách quảng cáo TV
- Radio: Ngân sách quảng cáo Radio  
- Newspaper: Ngân sách quảng cáo báo chí
- Sales: Doanh số bán hàng

### 2. Web Crawling - Text Content (`crawl_news(text).ipynb`)

**Mô tả**: Thu thập nội dung văn bản từ website VietnamNet.

**Chức năng**:
- Crawl 10 trang tin tức từ VietnamNet
- Trích xuất thông tin:
  - Tiêu đề bài viết
  - Tóm tắt (abstract)
  - Nội dung chính
  - Tác giả
- Lưu từng bài viết thành file .txt
- Tạo archive ZIP cho toàn bộ corpus

**Output**: `vn_news_corpus/` - Thư mục chứa ~135 bài viết

### 3. Web Crawling - Images (`crawl_news(image).ipynb`)

**Mô tả**: Thu thập hình ảnh thumbnail từ các bài viết tin tức.

**Chức năng**:
- Crawl hình ảnh thumbnail từ 10 trang tin tức
- Xử lý và chuẩn hóa format hình ảnh
- Chuyển đổi palette images sang RGB
- Lưu hình ảnh định dạng PNG

**Output**: `vn_news_thumbnail/` - Thư mục chứa ~150 hình ảnh

## 🚀 Hướng dẫn sử dụng

### Yêu cầu hệ thống
```bash
# Cài đặt các thư viện cần thiết
pip install pandas selenium requests pillow tqdm
```

### Cài đặt ChromeDriver (Ubuntu/Colab)
```bash
# Script tự động cài đặt chromium và chromedriver
# (Đã có sẵn trong các notebook)
```

### Chạy các notebook

1. **Phân tích dữ liệu tabular**:
   ```python
   # Mở tabular_data_handling.ipynb
   # Chạy từng cell theo thứ tự
   ```

2. **Thu thập dữ liệu văn bản**:
   ```python
   # Mở crawl_news(text).ipynb
   # Thay đổi n_pages nếu muốn crawl nhiều trang hơn
   n_pages = 10  # Số trang muốn crawl
   ```

3. **Thu thập hình ảnh**:
   ```python
   # Mở crawl_news(image).ipynb
   # Chạy để tải thumbnail images
   ```

## 📈 Kết quả mong đợi

### Thống kê dữ liệu quảng cáo:
- **TV Budget**: 73.2% tổng ngân sách
- **Radio Budget**: 11.6% tổng ngân sách  
- **Newspaper Budget**: 15.2% tổng ngân sách
- **Sales Average**: ~14.02 units

### Corpus tin tức:
- **~135 bài viết** văn bản tiếng Việt
- **~150 hình ảnh** thumbnail chất lượng cao
- **Format chuẩn**: UTF-8 text files và PNG images

## ⚙️ Cấu hình Selenium

```python
# Cấu hình Chrome options cho crawling
chrome_options = webdriver.ChromeOptions()
chrome_options.add_argument('--headless=new')  # Chạy headless
chrome_options.add_argument('--no-sandbox')    # Tăng tính ổn định
```

## 🔍 XPath Selectors sử dụng

```python
# Selector cho danh sách tin tức
news_lst_xpath = '//div[@class="topStory-15nd"]/div/div[1]/a'

# Selector cho nội dung bài viết
main_content_xpath = '//div[@class="content-detail"]'

# Selector cho hình ảnh thumbnail
imgs_lst_xpath = '//div[@class="topStory-15nd"]/div/div[1]/a/img'
```

## 📝 Lưu ý quan trọng

- **Rate Limiting**: Code có thêm `time.sleep(1)` để tránh spam requests
- **Error Handling**: Có xử lý exception cho các trường hợp không crawl được
- **Headless Mode**: Sử dụng browser headless để tăng hiệu suất
- **Data Quality**: Lọc bỏ các bài viết video và nội dung không hợp lệ

## 🛠️ Troubleshooting

### Lỗi ChromeDriver
```bash
# Nếu gặp lỗi chromedriver, chạy lại cell cài đặt:
%%shell
apt-get update
apt-get install chromium chromium-driver
```

### Lỗi Memory trong Colab
```python
# Giảm số trang crawl nếu bị out of memory
n_pages = 5  # Thay vì 10
```

### Lỗi Network/Timeout
```python
# Tăng thời gian chờ
time.sleep(2)  # Thay vì 1 giây
```

## 📊 Metrics & Performance

- **Crawling Speed**: ~15-20 bài viết/phút
- **Success Rate**: ~90% (sau khi lọc nội dung không hợp lệ)
- **Data Size**: 
  - Text corpus: ~5-10MB
  - Image corpus: ~50-100MB

## 🤝 Đóng góp

Mọi đóng góp đều được chào đón! Vui lòng:
1. Fork repository
2. Tạo feature branch
3. Commit changes
4. Push và tạo Pull Request

## 👤 Tác giả

**QuyDatSadBoy**
- GitHub: [@QuyDatSadBoy](https://github.com/QuyDatSadBoy)

---

*Dự án được phát triển để học tập và nghiên cứu về Data Science và Web Scraping.*


# Filter‑DSP

Kho chứa này triển khai các bộ lọc số cơ bản trong xử lý tín hiệu số (DSP), bao gồm bộ lọc IIR (Butterworth) và bộ lọc FIR đơn giản.

---

## Nội dung chính
- **Butter_Filter.m** – Triển khai bộ lọc IIR loại Butterworth để lọc tín hiệu trong miền thời gian.
- **Fir_filter.m** – Triển khai bộ lọc FIR cơ bản, có thể dùng thiết kế cửa sổ (window) hoặc phương pháp khác tùy nội dung trong file.

---

## Nguyên lý hoạt động

### Butterworth IIR (Butter_Filter.m)
- Sử dụng thiết kế bộ lọc Butterworth với hệ số bậc thấp, phổ phẳng trong dải thông qua (maximally flat).
- Người dùng định nghĩa:
  - Bậc bộ lọc n.
  - Tần số cắt (ví dụ: lowpass, highpass).
- Sử dụng hàm `butter()` để tạo hệ số bộ lọc, sau đó áp dụng `filter()` hoặc `filtfilt()` để xử lý tín hiệu đầu vào.

### FIR (Fir_filter.m)
- Bộ lọc FIR có thể thiết kế bằng:
  - Phương pháp cửa sổ: windows như Hamming, Hanning, Blackman.
  - Thiết kế theo đặc tính tần số mong muốn.
- Người dùng sử dụng hàm như `fir1()` để tạo hệ số, sau đó áp dụng `filter()` để lọc tín hiệu.

---

## Cách sử dụng

1. Clone repo:
   ```bash
   git clone https://github.com/NguyenDang010603/Filter-DSP.git
   ```
2. Mở trong MATLAB
3. Chuẩn bị tín hiệu mẫu, ví dụ:
   ```matlab
   fs = 1000;            % tần số mẫu (Hz)
   t = 0:1/fs:1-1/fs;
   x = sin(2*pi*50*t) + 0.5*sin(2*pi*120*t);
   ```
4. **Butterworth**:
   ```matlab
   n = 4;                % bậc bộ lọc
   fc = 100;             % tần số cắt (Hz)
   y = Butter_Filter(x, fs, n, fc);
   ```
5. **FIR**:
   ```matlab
   n = 50;               % bậc FIR
   fc = 100;
   y_fir = Fir_filter(x, fs, n, fc);
   ```
6. Vẽ đồ thị kết quả:
   - Tín hiệu gốc vs tín hiệu lọc.
   - Biên độ phổ (FFT) trước và sau khi lọc, để kiểm chứng hiệu quả lọc.

---

##  Kết quả kỳ vọng
- **Butterworth IIR**: Tín hiệu đầu ra mượt mà với chân dung phổ phẳng trong vùng qua và suy giảm mạnh ngoài vùng qua.
- **FIR**: Phổ hẹp và khuếch đại ổn định, đáp ứng chính xác theo thiết kế.

---

## Ứng dụng
- Loại bỏ nhiễu tần số cao hoặc tần số không mong muốn trong dữ liệu tín hiệu.
- Tiền xử lý trong các hệ thống giám sát và phân tích tín hiệu thời gian thực.
- Nền tảng để phát triển bộ lọc nâng cao và tối ưu hóa hiệu suất DSP.

---

## Tác giả
**Nguyễn Đăng** – dùng để học tập, minh họa thiết kế bộ lọc số trong DSP.

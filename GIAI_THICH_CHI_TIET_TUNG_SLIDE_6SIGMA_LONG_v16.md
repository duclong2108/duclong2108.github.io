# 📘 TÀI LIỆU HƯỚNG DẪN BẢO VỆ DỰ ÁN 6 SIGMA & BẢN CHẤT TỪNG SLIDE (BẢN CHUẨN 100% KHỚP V16)
## Dự Án 6 Sigma Green Belt: Giảm Tỷ Lệ Lỗi Độ Sáng (Luminance NG) Model Porsche CID J1 Dual
**Tác giả:** Nguyễn Đức Long – Kỹ sư IVI LD  
**File báo cáo chính thức:** `6_Sigma_Assignment_Nguyen_Duc_Long_Luminance_value_FINAL_v16.pptx` (29 slides)

---

## 🧭 LỜI DẪN MỞ ĐẦU KHI TRÌNH BÀY VỚI HỘI ĐỒNG THẨM ĐỊNH
> *"Kính thưa Sếp và Hội đồng thẩm định Six Sigma,*  
> *Dự án của em giải quyết bài toán lớn nhất trên chuyền FA Line IVI 5: Tỷ lệ lỗi độ sáng (Luminance NG) trên màn hình đôi Porsche CID J1 Dual lên tới **226,624 ppm** (143 NG / 631 EA, chiếm **87.2%** toàn bộ lỗi của model này). Điều đặc biệt trăn trở là các màn hình báo NG tại nhà máy khi gửi trả lại nhà cung cấp HEESUNG để kiểm tra và scrap thì đo trên bàn chuẩn của hãng đều **PASS 100%**!*  
> *Bằng phương pháp luận DMAIC và kiểm định thống kê chặt chẽ, dự án đã chứng minh được: **Đây là lỗi hệ thống đo lường (Measurement System Bias)** do góc đặt camera quang phổ CS-2000 tại vị trí đo màn hình phụ bị trôi lệch ~1° (còn 88.8°~89.1°), kết hợp với đặc tính màng lọc vi trập quang học (LCF film) cực nhạy góc của màn hình bảo mật Privacy (PID) trên bản tay lái nghịch (RHD). Sau khi hiệu chỉnh góc chuẩn 90.0° (đạt 89.889°), dạy lại tọa độ Robot và thiết lập cơ chế kiểm soát Master Sample (910 ± 5 Cd/m²) đầu mỗi ca, độ chệch hệ thống đo Bias đã giảm từ **−86.00 về −0.05 Cd/m²**, chỉ số **Cgk tăng từ 0.94 lên 23.53**, năng lực quy trình **Cpk tăng vọt từ 0.47 lên 2.39 (Zst = 7.18)**, và tỷ lệ lỗi thực tế đưa về **0 ppm (0 NG / 420 sets)**, tiết kiệm trực tiếp **\$2,255.68/tháng** chi phí scrap linh kiện."*

---

## 🎓 PHẦN ĐẶC BIỆT: GIẢI THÍCH CẶN KẼ & DỄ HIỂU TOÀN BỘ KHÁI NIỆM THỐNG KÊ 6 SIGMA TRONG BÀI (CPK, Z, P-VALUE, CG, CGK, GAGE R&R, NDC, T-TEST, XBAR-R)

> **💡 Bí quyết nắm bản chất trong 5 phút:** Bạn không cần học thuộc lòng như một nhà toán học. Giám khảo 6 Sigma chỉ cần thấy bạn **hiểu ý nghĩa thực tế trên chuyền sản xuất** của từng con số, biết **ngưỡng bao nhiêu là Đạt (OK) / Không đạt (NG)** và **tại sao con số đó lại dẫn tới quyết định cải tiến góc Camera**.

---

### 1. Nhóm khái niệm Kiểm định Giả thuyết: $H_0$, $H_1$, Mức ý nghĩa $\alpha = 0.05$ và $P\text{-value}$

#### a) $H_0$ (Giả thuyết Không - Null Hypothesis) và $H_1$ (Giả thuyết Đối - Alternative Hypothesis) là gì?
* **Hiểu nôm na (Nguyên tắc suy đoán vô tội tại tòa án):**
  * **$H_0$ (Vô tội / Bình thường / Không có gì khác biệt):** Luôn chứa dấu **"Bằng ($=$)"** hoặc trạng thái **"Bình thường"**. Ví dụ:
    * Trong kiểm định phân bố chuẩn (Normality test): $H_0$: *"Dữ liệu tuân theo phân bố chuẩn bình thường"*.
    * Trong Type 1 Gage Study: $H_0$: *"Máy đo không bị lệch ($\text{Bias} = 0$)"*.
    * Trong 2-Sample T-test: $H_0$: *"Thay linh kiện mới hoặc chỉnh góc không làm thay đổi độ sáng ($\mu_{\text{Before}} - \mu_{\text{After}} = 0$)"*.
  * **$H_1$ (Có tội / Bất thường / Có sự khác biệt thật sự):** Ngược lại với $H_0$ (chứa dấu $\ne$). Ví dụ: *"Dữ liệu không chuẩn"*, *"Máy đo bị lệch ($\text{Bias} \ne 0$)"*, *"Chỉnh góc làm độ sáng thay đổi rõ rệt ($\mu_{\text{Before}} \ne \mu_{\text{After}}$)"*.

#### b) $P\text{-value}$ (Giá trị xác suất) và ngưỡng $\alpha = 0.05$ (5%) là gì?
* **Hiểu nôm na:**
  * **$P\text{-value}$** là xác suất (tính từ $0.000$ đến $1.000$, tương ứng $0\%$ đến $100\%$) mà sự khác biệt ta nhìn thấy trong dữ liệu chỉ là do **ngẫu nhiên tình cờ (may rủi)** tạo ra khi $H_0$ vẫn đúng.
  * **Ngưỡng $\alpha = 0.05$ ($5\%$):** Là ranh giới ra quyết định chuẩn quốc tế (tương ứng độ tin cậy $95\%$).
* **Quy tắc vàng đọc $P\text{-value}$ (Chỉ cần nhớ đúng 2 câu này cho mọi biểu đồ Minitab):**
  1. **Nếu $P\text{-value} \le 0.05$ ($P$ nhỏ $\rightarrow$ Bác bỏ $H_0$, chọn $H_1$):** Xác suất ngẫu nhiên quá thấp ($\le 5\%$) $\rightarrow$ **Có sự khác biệt / lệch thật sự (Significant)!**
  2. **Nếu $P\text{-value} > 0.05$ ($P$ lớn $\rightarrow$ Chấp nhận $H_0$):** Chưa đủ bằng chứng bác bỏ $H_0$ $\rightarrow$ **Không có sự khác biệt (hoặc dữ liệu bình thường)!**

#### c) Bảng tra nhanh ý nghĩa $P\text{-value}$ trong từng trang Slide của bài bạn:
*(Cực kỳ quan trọng: Có chỗ cần $P > 0.05$ mới là TỐT, nhưng có chỗ lại cần $P < 0.05$ mới là TỐT — hãy xem bảng dưới đây để không bao giờ nhầm!)*

| Loại kiểm định trong bài | Slide | Giả thuyết $H_0$ | Khi nào là ĐẠT / TỐT? | Con số cụ thể trong bài của bạn |
| :--- | :---: | :--- | :--- | :--- |
| **1. Kiểm định Phân bố chuẩn (Normality Test - Anderson Darling)** | 7, 10, 13, 14, 15, 22, 24 | $H_0$: Dữ liệu tuân theo **Phân bố chuẩn (Normal)** | Cần **$P > 0.05$** (Chấp nhận $H_0$ $\rightarrow$ Dữ liệu chuẩn) | • Slide 10 (Before): $P < 0.005$ ($\le 0.05$) $\rightarrow$ Không chuẩn (do lỗi góc camera kéo lệch đuôi trái).<br>• Slide 24 (After): **$P = 0.503 > 0.05$** $\rightarrow$ **Đạt chuẩn!** |
| **2. Kiểm định Độ chệch máy đo (Type 1 Bias T-test)** | 7, 22 | $H_0$: Máy đo **không bị lệch** ($\text{Bias} = 0$) | Cần **$P > 0.05$** (Chấp nhận $H_0$ $\rightarrow$ Máy không lệch) | • Slide 7 (Before): **$P = 0.000 < 0.05$** $\rightarrow$ Bác bỏ $H_0$, máy lệch âm $-86\text{ Cd/m}^2$ (**FAIL**).<br>• Slide 22 (After): **$P = 0.871 > 0.05$** $\rightarrow$ Hết lệch (**PASS**). |
| **3. ANOVA trong Type 3 Gage R&R (Part effect)** | 8, 23 | $H_0$: 25 tấm màn hình lấy mẫu đều giống hệt nhau | Cần **$P < 0.05$** (Chứng tỏ máy phân biệt được các màn hình khác nhau) | • Slide 8 & 23: **$P = 0.000 < 0.05$** $\rightarrow$ 25 mẫu có độ sáng thực tế khác nhau. |
| **4. Kiểm định 2-Sample T & Paired T tìm nguyên nhân gốc** | 13, 14, 15, 16 | $H_0$: Yếu tố đang thử **không ảnh hưởng** đến độ sáng ($\mu_1 = \mu_2$) | • Nếu **$P > 0.05$**: Yếu tố đó **vô can (Loại trừ)**.<br>• Nếu **$P < 0.05$**: Yếu tố đó chính là **Thủ phạm (Root Cause)**! | • Slide 13 (CANSIM): $P = 0.682 / 0.887 > 0.05$ $\rightarrow$ **Loại**.<br>• Slide 14 (Thân Camera): $P = 0.524 / 0.862 > 0.05$ $\rightarrow$ **Loại**.<br>• Slide 15 (Góc Camera): **$P < 0.001 < 0.05$** $\rightarrow$ **Nguyên nhân gốc rễ!** |

---

### 2. Nhóm khái niệm Đánh giá Hệ thống đo (MSA - Measurement System Analysis): Type 1 ($C_g, C_{gk}, \text{Bias}$) và Type 3 ($\text{Gage R\&R}, \text{NDC}$)

#### a) Độ chụm (Repeatability / Precision) vs. Độ đúng (Bias / Accuracy):
* **Ví dụ bắn bia:** Giả sử hồng tâm bia là mẫu chuẩn **`Reference = 910 Cd/m²`**.
  * **Độ chụm (Repeatability):** Bạn bắn 30 phát đạn, cả 30 phát đều chụm sát vào nhau trong một vòng tròn nhỏ (độ lệch chuẩn $s$ nhỏ).
  * **Độ đúng (Accuracy / Bias):** Tâm của chùm đạn 30 phát đó cách hồng tâm `910` bao xa? Trước cải tiến (Slide 7), trung bình 30 phát bắn rơi vào **`824.00 Cd/m²`**, tức là bị lệch khỏi hồng tâm `910` một khoảng **$\text{Bias} = 824 - 910 = -86.00\text{ Cd/m}^2$**!

#### b) Chỉ số $C_g$ và $C_{gk}$ trong Type 1 Gage Study (Slide 7 & Slide 22):
* **Tiêu chuẩn Đạt (Benchmark):** Cả **$C_g \ge 1.33$** và **$C_{gk} \ge 1.33$** (tương ứng $\%\text{Var} \le 15\%$).
* **Ý nghĩa & Công thức:**
  1. **$C_g$ (Potential Gage Capability – Chỉ đo Độ chụm Repeatability):**
     $$C_g = \frac{0.20 \times \text{Tolerance}}{6 \times s}$$
     * So sánh $20\%$ dung sai sản phẩm ($0.20 \times 1200 = 240\text{ Cd/m}^2$) với độ tản mạn $6s$ của 30 lần đo lặp.
     * Ở Slide 7 (Before): $C_g = \frac{240}{71.994} = \mathbf{3.33 \ge 1.33}$ (**PASS**). Nghĩa là mắt đọc quang học của máy CS-2000 rất chụm!
  2. **$C_{gk}$ (Gage Capability Index – Đo cả Độ chụm VÀ Độ lệch tâm Bias):**
     $$C_{gk} = \frac{0.10 \times \text{Tolerance} - |\text{Bias}|}{3 \times s}$$
     * Khi trừ đi độ lệch tâm $|\text{Bias}| = 86.00\text{ Cd/m}^2$, tử số chỉ còn $120 - 86 = 34$, làm **$C_{gk} = \frac{34}{35.997} = \mathbf{0.94 < 1.33}$ (FAIL)**!
     * Sau khi chỉnh góc camera về $90.0^\circ$ (Slide 22): $\text{Bias} = -0.05 \approx 0$ và $s = 1.700$, nên **$C_g = 23.54$** và **$C_{gk} = 23.53 \ge 1.33$ (PASS xuất sắc)**!
  3. **$\%\text{Var(Repeatability)}$ và $\%\text{Var(Repeatability and Bias)}$:**
     * Chính là tỷ lệ phần trăm dung sai bị sai số máy đo "ăn mất":
       $$\%\text{Var(Repeatability)} = \frac{20\%}{C_g}, \quad \%\text{Var(Repeatability \& Bias)} = \frac{20\%}{C_{gk}}$$
     * Khi $C_g, C_{gk} \ge 1.33$ thì $\%\text{Var} \le \frac{20\%}{1.33} = 15\%$.

#### c) Các chỉ số trong Type 3 Gage R&R (Slide 8 & Slide 23):
* **Tại sao gọi là Type 3 Gage Study?**
  * Thông thường Gage R&R truyền thống (Type 2) có 2 nguồn sai số: **Repeatability (EV - Thiết bị đo lặp lại)** và **Reproducibility (AV - Giữa các người đo khác nhau)**.
  * Nhưng trạm kiểm tra Luminance của chúng ta là **trạm tự động 100% (Automated Test Station)**, công nhân không cầm máy đo nên sai số do người đo $\text{Reproducibility} = 0$. Khi $\text{Reproducibility} = 0$, chuẩn MSA gọi là **Type 3 Gage Study** (đo 25 sản phẩm $\times$ 2 lần để tách biến thiên của máy đo $\sigma_{\text{Gage}}^2$ khỏi biến thiên thực tế giữa các sản phẩm $\sigma_{\text{Part}}^2$).
* **Ba chỉ số đánh giá Gage R&R theo chuẩn AIAG (Slide 8 & 23):**
  1. **$\%\text{Contribution}$ (Tỷ lệ đóng góp phương sai $\sigma^2$):**
     $$\%\text{Contribution} = \frac{\text{VarComp(Gage R\&R)}}{\text{VarComp(Total)}} \times 100\%$$
     * *Tiêu chuẩn AIAG:* **$< 1\%$ là Tốt (OK)**; từ $1\% \sim 9\%$ là Chấp nhận có điều kiện; **$> 9\%$ là Không đạt (NG)**.
     * *Trong bài:* Trước cải tiến = **`10.02% > 9%` (NG)** $\rightarrow$ Sau cải tiến = **`0.22% < 1%` (OK)**.
  2. **$\%\text{Study Var}$ (Tỷ lệ độ lệch chuẩn $\sigma$ - Căn bậc hai của $\%\text{Contribution}$):**
     $$\%\text{Study Var} = \frac{\text{SD(Gage R\&R)}}{\text{SD(Total)}} \times 100\% = \sqrt{\%\text{Contribution}}$$
     * *Lưu ý mẹo toán học:* Vì $\sqrt{0.1002} = 0.3166$, nên $\%\text{Contribution} = 10.02\%$ chính là $\%\text{Study Var} = 31.66\%$!
     * *Tiêu chuẩn AIAG:* **$< 10\%$ là Tốt (OK)**; từ $10\% \sim 30\%$ là Chấp nhận có điều kiện; **$> 30\%$ là Không đạt (NG)**.
     * *Trong bài:* Trước cải tiến = **`31.66% > 30%` (NG)** $\rightarrow$ Sau cải tiến = **`4.64% < 10%` (OK)**.
  3. **$\%\text{Tolerance}$ (Tỷ lệ sai số máy đo so với Dung sai thiết kế `1200 Cd/m²`):**
     $$\%\text{Tolerance} = \frac{6 \times \text{SD(Gage R\&R)}}{\text{USL} - \text{LSL}} \times 100\%$$
     * *Tiêu chuẩn AIAG:* **$< 10\%$ là Tốt (OK)**. Trước cải tiến = `6.00%`, Sau cải tiến = **`0.86% < 10%` (OK)**.
  4. **$\text{NDC}$ (Number of Distinct Categories – Số nhóm phân biệt):**
     $$\text{NDC} = \left\lfloor \sqrt{2} \times \frac{\text{SD(Part-to-Part)}}{\text{SD(Gage R\&R)}} \right\rfloor$$
     * *Hiểu nôm na:* Máy đo có độ phân giải thực tế chia dải sản phẩm thành mấy mức phân biệt rõ ràng? Nếu $\text{NDC} = 1$, máy đo bị "mù", chỉ biết phán bừa.
     * *Tiêu chuẩn AIAG:* **$\text{NDC} \ge 5$ là Đạt (OK)**.
     * *Trong bài:* Trước cải tiến $\text{NDC} = \lfloor 1.414 \times 35.954 / 12.001 \rfloor = \mathbf{4 < 5}$ (**NG**) $\rightarrow$ Sau cải tiến $\text{NDC} = \lfloor 1.414 \times 36.922 / 1.716 \rfloor = \mathbf{30 \ge 5}$ (**OK**).

---

### 3. Nhóm khái niệm Kiểm soát Quy trình bằng Thống kê (SPC): Biểu đồ $X\text{bar-}R$ (Slide 9 & Slide 27)

* **Tại sao lại lấy 5 mẫu/ngày trong 10 ngày ($10 \times 5 = 50$ mẫu) để vẽ biểu đồ $X\text{bar-}R$?**
  * Đó gọi là **Phương pháp lấy mẫu phân nhóm hợp lý (Rational Subgroup Sampling)**:
    * **Biến thiên trong cùng 1 ngày (Within-subgroup variation):** Do 5 sản phẩm đo liên tiếp nhau trong cùng 1 ca tạo ra $\rightarrow$ Phản ánh trên **biểu đồ $R$ (Sample Range = $\text{Max} - \text{Min}$ của 5 mẫu mỗi ngày)**.
    * **Biến thiên giữa các ngày khác nhau (Between-subgroup variation):** Do sự trôi lệch theo thời gian từ ngày 1 đến ngày 10 tạo ra $\rightarrow$ Phản ánh trên **biểu đồ $\bar{X}$ (Sample Mean = Trung bình của 5 mẫu mỗi ngày)**.
* **Giới hạn kiểm soát ($\text{UCL}, \text{LCL}$) KHÁC Giới hạn tiêu chuẩn ($\text{USL}, \text{LSL}$) như thế nào?** *(Câu hỏi kinh điển của Giám khảo!)*
  * **$\text{LSL} = 800, \text{USL} = 2000\text{ Cd/m}^2$ (Specification Limits):** Là **Tiêu chuẩn của Khách hàng (Porsche)** đặt ra cho **từng sản phẩm đơn lẻ** để phán định hàng OK hay NG.
  * **$\text{UCL}, \text{LCL}$ (Control Limits = $\bar{\bar{X}} \pm A_2 \bar{R}$):** Là **Tiếng nói của Quy trình (Voice of Process)**, tính bằng $\pm 3$ độ lệch chuẩn của trung bình nhóm xung quanh đường tâm $\bar{\bar{X}}$, dùng để canh gác xem quy trình có **ổn định theo thời gian hay có biến cố bất thường (Special Cause)** hay không.
* **Điểm báo đỏ số `1` (Out-of-Control point) ở Slide 9 nghĩa là gì?**
  * Trong Minitab, ký hiệu ô vuông đỏ kèm số `1` nghĩa là vi phạm **Test 1 của Nelson Rules**: Có điểm văng ra ngoài biên $\pm 3\sigma$ ($\text{UCL}$ hoặc $\text{LCL}$).
  * Ở Slide 9 (Before): Ngày `20-Feb` có $\bar{X} = 802.70 < \text{LCL } 805.88$, và ngày `01-Mar` có $R = 98.05 > \text{UCL } 74.62$. Điều này chứng minh có **Nguyên nhân đặc biệt (Special Cause)** đang phá đám quy trình (chính là hiện tượng gá camera bị rung lỏng và trôi góc!).
  * Ở Slide 27 (After): Cả 10 ngày (`1-Jul` ~ `10-Jul`) đều nằm êm ru giữa $\text{LCL} = 890.78$ và $\text{UCL} = 933.10$, không có điểm đỏ nào $\rightarrow$ Quy trình đã **ổn định thống kê hoàn toàn (In statistical control)**.

---

### 4. Nhóm khái niệm Năng lực Quy trình (Process Capability): $C_p, C_{pk}, P_p, P_{pk}$ (Slide 10, 24, 25)

#### a) Hiểu bằng hình ảnh chiếc ô tô đi vào cổng Gara:
* Hãy tưởng tượng:
  * **Chiều rộng cổng Gara** là khoảng cách tiêu chuẩn của khách hàng: $\text{Tolerance} = \text{USL} - \text{LSL} = 2000 - 800 = \mathbf{1200\text{ Cd/m}^2}$.
  * **Chiều rộng chiếc ô tô** là độ tản mạn tự nhiên của quy trình sản xuất: **$6\sigma$** (với $\sigma \approx 16 \sim 19\text{ Cd/m}^2$, nên bề rộng chiếc xe $6\sigma \approx 93 \sim 111\text{ Cd/m}^2$).

#### b) Sự khác nhau giữa $C_p$ và $C_{pk}$:
1. **$C_p$ (Potential Capability – Năng lực tiềm năng khi xe đi chính giữa cổng):**
   $$C_p = \frac{\text{USL} - \text{LSL}}{6 \times \sigma_{\text{Within}}}$$
   * Chỉ so sánh **Bề rộng cổng Gara ($1200$)** chia cho **Bề rộng chiếc xe ($6\sigma \approx 111$)**.
   * Vì cổng Gara rộng tới $1200$ mà chiếc xe chỉ rộng $\sim 100$, nên $C_p = 10.78$ (Before) và $12.83$ (After) rất lớn. **Nhưng $C_p$ không biết chiếc xe đang đi ở giữa đường hay đang lao sát vào cột cổng bên trái!**
2. **$C_{pk}$ (Actual Capability – Năng lực thực tế có tính đến độ lệch tâm về phía vách gần nhất):**
   $$C_{pl} = \frac{\text{Mean} - \text{LSL}}{3 \times \sigma_{\text{Within}}}, \quad C_{pu} = \frac{\text{USL} - \text{Mean}}{3 \times \sigma_{\text{Within}}}, \quad C_{pk} = \min(C_{pl}, C_{pu})$$
   * Vì trung bình độ sáng (`Mean = 826.25` trước cải tiến và `911.94` sau cải tiến) nằm gần vách dưới $\text{LSL} = 800$ hơn rất nhiều so với vách trên $\text{USL} = 2000$, nên **$C_{pk}$ chính là $C_{pl}$**!
   * **Tiêu chuẩn Đạt (Benchmark):** **$C_{pk} \ge 1.33$** (tương đương mức $4\sigma$ ngắn hạn).
   * **Trong bài của bạn:**
     * **Trước cải tiến (Slide 10):** $\text{Mean} = 826.25$ nằm quá sát vách trái $\text{LSL} = 800$ (chỉ cách có $26.25\text{ Cd/m}^2$), nên chiếc xe quệt vào cột cổng bên trái:
       $$C_{pk} = C_{pl} = \frac{826.25 - 800}{3 \times 18.557} = \mathbf{0.47 < 1.33 \text{ (NG - Rớt thảm hại!)}}$$
     * **Sau cải tiến (Slide 24):** Chỉnh góc camera về $90.0^\circ$ đưa tâm $\text{Mean}$ về đúng giá trị thực **`911.94 Cd/m²`** (cách vách trái $\text{LSL} = 800$ tới $111.94\text{ Cd/m}^2$), đồng thời $\sigma_{\text{Within}}$ giảm còn $15.594$:
       $$C_{pk} = C_{pl} = \frac{911.94 - 800}{3 \times 15.594} = \mathbf{2.39 \ge 1.33 \text{ (OK - Đạt xuất sắc, tăng gấp 5.1 lần!)}}$$

#### c) Sự khác nhau giữa Nhóm Ngắn hạn ($\text{Within}: \sigma_W, C_p, C_{pk}$) và Nhóm Dài hạn ($\text{Overall}: \sigma_O, P_p, P_{pk}$):
* **$\text{StDev(Within)} = \sigma_W$ (và $C_p, C_{pk}$):** Tính từ độ lệch chuẩn gộp (pooled standard deviation) **bên trong từng ngày** (loại bỏ sự dao động giữa ngày này sang ngày khác). Nó đại diện cho **Năng lực Công nghệ nội tại (Short-term / Potential capability)** của máy móc.
* **$\text{StDev(Overall)} = \sigma_O$ (và $P_p, P_{pk}$):** Tính gộp toàn bộ 50 mẫu của cả 10 ngày lại với nhau (bao gồm cả biến thiên trong ngày lẫn độ trôi giữa các ngày). Nó đại diện cho **Hiệu suất tổng thể dài hạn (Long-term / Overall performance)** mà khách hàng thực sự trải nghiệm.
* Luôn có $\sigma_{\text{Overall}} \ge \sigma_{\text{Within}}$, nên $P_{pk}$ luôn nhỏ hơn hoặc bằng $C_{pk}$ một chút (ở Slide 24: **$C_{pk} = 2.39$**, **$P_{pk} = 2.30$** — hai đường cong `Within` nét đứt và `Overall` nét liền ôm sát khít vào nhau, chứng tỏ giữa 10 ngày hầu như không có sự trôi lệch!).

---

### 5. Nhóm khái niệm Mức Sigma ($Z\text{.Bench}, Z_{st}, Z_{lt}, Z_{\text{shift}}$) & Ma trận 4 Góc Phần Tư A-B-C-D (Slide 25)

* **Mối liên hệ cực dễ nhớ giữa $Z$ và $C_{pk}, P_{pk}$:**
  * Vì công thức $C_{pk} = \frac{\text{Mean} - \text{LSL}}{3\sigma_W}$, còn mức Sigma $Z = \frac{\text{Mean} - \text{LSL}}{\sigma}$ (khoảng cách từ tâm quy trình đến ngưỡng lỗi LSL tính bằng mấy lần độ lệch chuẩn $\sigma$), nên:
    $$\mathbf{Z_{st} = 3 \times C_{pk}} \quad \text{và} \quad \mathbf{Z_{lt} = 3 \times P_{pk}}$$
* **Kiểm chứng ngay trên con số trong bài của bạn:**
  * **Trước cải tiến (Slide 2 & 10):**
    * $Z_{st} = 3 \times C_{pk} = 3 \times 0.47 = \mathbf{1.41\sigma}$ (Mục tiêu $\ge 4.5\sigma$ $\rightarrow$ **NG**).
    * $Z_{lt} = 3 \times P_{pk} = 3 \times 0.45 = \mathbf{1.34\sigma}$.
  * **Sau cải tiến (Slide 24 & 25):**
    * **$Z_{st} (Z\text{ Short term}) = 3 \times 2.393 = \mathbf{7.18\sigma \ge 4.5\sigma}$ (OK - Công nghệ rất tốt!)**
    * **$Z_{lt} (Z\text{ Long term}) = 3 \times 2.298 = \mathbf{6.89\sigma \ge 4.5\sigma}$ (OK - Dài hạn rất tốt!)**
* **Chỉ số $Z_{\text{shift}}$ (Độ trôi quy trình) và Ma trận A-B-C-D ở Slide 25:**
  * **Công thức:**
    $$Z_{\text{shift}} = Z_{st} - Z_{lt} = 7.18 - 6.89 = \mathbf{0.29}$$
  * **Tiêu chuẩn Đạt:** Trong lý thuyết 6 Sigma, một quy trình thông thường theo thời gian được phép trôi tối đa **$1.5\sigma$** ($Z_{\text{shift}} < 1.5$). Ở đây độ trôi thực tế của trạm sau cải tiến chỉ là **$0.29 \ll 1.5$**, chứng tỏ quy trình kiểm soát hàng ngày cực kỳ chặt chẽ (`Proper process control management`).
  * **Ý nghĩa 4 ô A, B, C, D ở góc dưới phải Slide 25:**
    * Trục ngang là **Công nghệ ($Z_{st}$)** với vạch chuẩn $4.5$; Trục đứng là **Quản lý kiểm soát ($Z_{\text{shift}}$)** với vạch chuẩn $1.5$:
      * **Ô A ($Z_{st} < 4.5, Z_{\text{shift}} > 1.5$):** Thiếu cả công nghệ lẫn quản lý (*Lack of management & Lack of skill*).
      * **Ô B ($Z_{st} \ge 4.5, Z_{\text{shift}} > 1.5$):** Công nghệ tốt nhưng quản lý kém làm quy trình bị trôi (*Lack of management & Proper skills*).
      * **Ô C ($Z_{st} < 4.5, Z_{\text{shift}} \le 1.5$):** Quản lý tốt nhưng công nghệ máy móc yếu (*Proper management & Lack of skills*).
      * **Ô D ($Z_{st} \ge 4.5, Z_{\text{shift}} \le 1.5$):** **Tốt cả Quản lý lẫn Công nghệ (*Proper management & Proper skills*)** $\rightarrow$ Chấm vuông đỏ của dự án nằm trọn trong **Ô D**!

---

### 6. Nhóm khái niệm Kiểm định T-test ($T\text{-Value}$, $\text{DF}$, $95\%\text{ CI}$, Paired T vs. 2-Sample T) ở Slide 13, 14, 15

1. **$\text{SE Mean}$ (Standard Error of the Mean – Sai số chuẩn của trung bình):**
   $$\text{SE Mean} = \frac{\text{StDev}}{\sqrt{N}} = \frac{\text{StDev}}{\sqrt{30}}$$
   * Đo độ chính xác của giá trị trung bình mẫu khi cỡ mẫu $N = 30$.
2. **$T\text{-Value}$ (Giá trị thống kê T):**
   $$T\text{-Value} = \frac{\text{Chênh lệch trung bình (Difference)}}{\text{Sai số chuẩn (SE)}}$$
   * **Hiểu nôm na:** $T\text{-Value}$ là **Tỷ số Tín hiệu trên Nhiễu (Signal-to-Noise Ratio)**.
   * Nếu $|T\text{-Value}|$ nhỏ gần bằng $0$ (như ở Slide 13: $T = 0.41$ và $0.14$; Slide 14: $T = -0.64$ và $-0.18$) $\rightarrow$ Tín hiệu nhỏ hơn nhiễu $\rightarrow$ $P\text{-value} > 0.05$ (Không có tác động).
   * Nếu $|T\text{-Value}|$ rất lớn (như ở Slide 15 khi chỉnh góc Camera: **$T = -43.34$** ở Paired T và **$T = -10.61$** ở 2-Sample T) $\rightarrow$ Tín hiệu lớn gấp 10 đến 43 lần nhiễu $\rightarrow$ **$P\text{-value} < 0.001$** (Tác động cực kỳ rõ rệt!).
3. **$95\%\text{ CI for Difference}$ (Khoảng tin cậy 95% của hiệu số $\mu_{\text{Before}} - \mu_{\text{After}}$):**
   * **Mẹo đọc nhanh trong 2 giây:**
     * Nếu khoảng $(CI_{\text{low}}, CI_{\text{high}})$ **chứa số $0$** (một đầu âm, một đầu dương, ví dụ Slide 13 là `(-5.26, 7.94)` hay `(-17.34, 20.02)`) $\rightarrow$ Hiệu số có thể bằng $0$ $\rightarrow$ **Không có sự khác biệt ($P > 0.05$)**.
     * Nếu cả hai đầu của khoảng $95\%\text{ CI}$ **nằm hẳn về một phía của số $0$** (ví dụ Slide 15 là **`(-91.44, -83.20)`** — không chứa số $0$, nghĩa là chắc chắn $95\%$ sau khi chỉnh góc độ sáng tăng từ $+83.20$ đến $+91.44\text{ Cd/m}^2$) $\rightarrow$ **Khác biệt có ý nghĩa thống kê tuyệt đối ($P < 0.001$)**!
4. **Tại sao trên biểu đồ `Individual Value Plot of Differences` (cột giữa Slide 13, 14, 15) lại có dấu cộng đỏ $H_0$ và thanh ngang màu xanh?**
   * **Dấu cộng đỏ ($H_0 = 0$):** Vị trí giả thuyết "không có sự thay đổi".
   * **Thanh ngang màu xanh:** Chính là khoảng tin cậy $95\%\text{ CI}$ của hiệu số.
   * Ở Slide 13 và Slide 14: Thanh ngang màu xanh **đè trực tiếp lên dấu cộng đỏ $H_0 = 0$** $\rightarrow$ Chấp nhận $H_0$ (CANSIM và thân Camera không phải nguyên nhân).
   * Ở Slide 15 (Góc Camera): Thanh ngang màu xanh nằm ở vùng `-87.32`, **cách xa tít tắp dấu cộng đỏ $H_0 = 0$** $\rightarrow$ Bác bỏ $H_0$, khẳng định 100% Góc Camera là nguyên nhân gốc rễ!

---

## 📑 CHI TIẾT TỪNG TRANG SLIDE (SLIDE 01 ~ SLIDE 29)

---

### 🟦 GIAI ĐOẠN 1: DEFINE (ĐỊNH NGHĨA VẤN ĐỀ)

#### SLIDE 01: TRANG TIÊU ĐỀ (COVER PAGE)
* **Tiêu đề:** `Luminance value NG of Porsche CID J1 Dual – 6 Sigma GB Assignment`
* **Mục đích:** Xác lập nhận diện đề tài, chủ nhiệm dự án (`IVI LD Nguyen Duc Long`) và cấu trúc 5 giai đoạn chuẩn DMAIC (`1. Define → 2. Measure → 3. Analyze → 4. Improve → 5. Control`).
* **Bản chất kỹ thuật:** Cụm màn hình Porsche CID J1 Dual là dòng hiển thị đôi cao cấp gồm màn hình trung tâm **CID** (Center Information Display – góc nhìn rộng Public) và màn hình hành khách **PID** (Passenger Information Display – tích hợp màng chống nhìn trộm Privacy).

---

#### SLIDE 02: SIX SIGMA PROJECT REGISTER (PHIẾU ĐĂNG KÝ DỰ ÁN)
* **Tiêu đề:** `Six Sigma Project Register`
* **Thông tin tổ chức:** Team `IVI LD` | Leader: `Nguyen Dinh Huong TL` | Owner/Task leader: `Nguyen Duc Long` | Thành viên: `Hoang Nhan Quoc` (IVI LD), `Pham Van Hung` (IVI PE), `Ta Van Cong` (IVI PM).
* **Thời gian thực hiện (Period & Schedule):** `2026.Mar.09 ~ 2026.Sep.20`
  * **D (Define):** `3/9 ~ 3/31` | **M (Measure):** `4/1 ~ 4/30` | **A (Analyze):** `5/1 ~ 5/18` | **I (Improve):** `5/19 ~ 6/14` | **C (Control):** `6/15 ~ 9/20`.
* **Các chỉ số cam kết cốt lõi:**
  * **KPI (Defect rate):** Hiện tại **`226,624 ppm`** → Mục tiêu (Goal): **`0 ppm`**.
  * **Project Y (Luminance, Spec `800–2000 Cd/m²`):** Hiện tại **`Cpk = 0.47 / Z = 1.41`** → Mục tiêu: **`Cpk ≥ 1.33 / Z = 4.5`**.
  * **Hiệu quả tài chính (Quantitative Performance):** Đơn giá 1 màn hình LCD = **`$118.72`**. Trong tháng 3/2026 (có 30 bộ báo lỗi tại chuyền), sau khi retest có **19 màn hình LCD** không qua được phải gửi trả nhà cung cấp HEESUNG để scrap, gây tổn thất trực tiếp: `19 × $118.72 = $2,255.68/tháng` (`≈ $27,068/năm`). Kết quả sau cải tiến: **`0 NG / 420 sets`**.

---

#### SLIDE 03: 1.1 Y-Y BREAKDOWN (CÂY PHÂN RÃ CHỈ SỐ Y)
* **Tiêu đề:** `1.1 Y-y breakdown`
* **Mục đích:** Dùng kỹ thuật phễu lọc (Funneling) bóc tách từ **Big Y** (`Reduce Porsche CID Defect rate`) qua **Little y1 → Little y2 → Little y3** để chọn đúng Project Y.
* **Số liệu gốc (`Nov.2025 ~ Mar.2026`, tổng sản lượng `631 EA`, tổng lỗi `164 NG = 259,905 PPM`):**
  1. **Little y1 (Phân loại nguồn lỗi):**
     * **Machine defect (Lỗi tại trạm kiểm tra tự động):** `148 EA / 631 EA` = **`90.2%`** (**`234,548 PPM`**).
     * **Hardware defect (Lỗi phần cứng - gãy chân pin PCBA, dị vật...):** `10 EA / 631 EA` = **`6.1%`** (**`15,848 PPM`**) → Giao `Mr. Hai HW` xử lý.
     * **Software defect (Lỗi phần mềm - Black Uniformity):** `6 EA / 631 EA` = **`3.7%`** (**`9,509 PPM`**) → Giao `HQ R&D` xử lý.
  2. **Little y2 (Trong nhóm Machine defect `90.2%`):**
     * **Luminance Function:** `147 EA / 631 EA` = **`89.6%`** (**`232,964 PPM`**).
     * **Haptic/Touch Function:** `1 EA / 631 EA` = **`0.6%`** (**`1,585 PPM`**).
  3. **Little y3 (Trong nhóm Luminance Function `89.6%`):**
     * **Luminance value (Giá trị độ sáng):** `143 EA / 631 EA` = **`87.2%`** (**`226,624 PPM`**) → **Chọn làm Project Y của đề tài 6 Sigma (PIC: IVI LD IE)**.
     * **Calculate contrast value (Độ tương phản):** `4 EA / 631 EA` = **`2.4%`** (**`6,339 PPM`**) → Lỗi vật liệu thật, trả về vendor `HEESUNG`.
* **Biểu đồ cột góc dưới trái:** Khi triệt tiêu hoàn toàn lỗi `Luminance value` (`226,624 PPM → 0 PPM`), tổng tỷ lệ lỗi toàn dự án Porsche CID giảm từ **`259,905 PPM`** xuống còn **`33,281 PPM`** (`259,905 − 226,624 = 33,281 PPM`, tức `21 NG / 631 EA` của các hạng mục ngoài phạm vi đề tài).

---

#### SLIDE 04: 1.2 PARETO (BIỂU ĐỒ PARETO)
* **Tiêu đề:** `1.2 Pareto`
* **Bản chất thống kê (Quy luật 80:20):**
  * Hạng mục **`Luminance value`** đứng đầu bảng với **`226,624 ppm`** (`143 NG`), chiếm **`87.2%`** tổng số lỗi — vượt qua đường ngưỡng **80% (Vital Few)**.
  * Cộng dồn 5 hạng mục (`164 NG / 631 EA = 259,905 ppm`):
    1. `Luminance value`: `226,624 ppm` (`87.2%`, lũy kế **`87.2%`**)
    2. `Hardware`: `15,848 ppm` (`6.1%`, lũy kế **`93.3%`**)
    3. `Software`: `9,509 ppm` (`3.7%`, lũy kế **`97.0%`**)
    4. `Contrast value`: `6,339 ppm` (`2.4%`, lũy kế **`99.4%`**)
    5. `Haptic / Touch`: `1,585 ppm` (`0.6%`, lũy kế **`100.0%`**)

---

#### SLIDE 05: 1.3 DEFINE PROJECT Y (ĐỊNH NGHĨA PROJECT Y & CÔNG THỨC QUANG HỌC)
* **Tiêu đề:** `1.3 Define Project Y`
* **Bản chất vật lý & Phương pháp đo:**
  * **Định nghĩa:** Độ chói (Luminance, đơn vị `cd/m²` hay `nit`) là cường độ sáng phát ra trên một đơn vị diện tích bề mặt theo một hướng xác định.
  * **Công thức vật lý:**
    $$L = \frac{d^2\Phi}{dA \cdot d\omega \cdot \cos\theta}$$
    Trong đó:
    * $d^2\Phi$: Quang thông (luminous flux, đơn vị `lm`).
    * $dA$: Vi phân diện tích bề mặt phát sáng (`m²`).
    * $d\omega$: Vi phân góc khối (`sr`).
    * $\theta$: Góc hợp bởi pháp tuyến bề mặt màn hình (surface normal) và trục nhìn của cảm biến (sight line of detector). Ở trạng thái chuẩn vuông góc 90° so với mặt màn hình thì $\theta = 0^\circ$ ($\cos 0^\circ = 1$).
  * **Tiêu chuẩn (Spec):** **`800 – 2000 cd/m²`**.
  * **Cơ chế đo:** Khi màn hình phát nền trắng ở độ sáng tối đa (maximum brightness), camera quang phổ **CS-2000** di chuyển đến chính tâm màn hình PID để đo (vì vùng tâm luôn có độ sáng chuẩn và cao nhất so với rìa).
  * **Vấn đề (Issue):** Độ sáng đo được trên màn hình **PID (Privacy)** tại trạm thấp hơn độ sáng thực tế của tấm nền (cùng màn hình đó gửi về vendor đo lại đạt OK), làm kết quả rớt dưới cận dưới `800 cd/m²` (báo lỗi NG).

---

### 🟩 GIAI ĐOẠN 2: MEASURE (ĐO LƯỜNG & ĐÁNH GIÁ HỆ THỐNG ĐO MSA)

#### SLIDE 06: 2. PREPARATION OF GAGE R&R (CHUẨN BỊ ĐÁNH GIÁ HỆ THỐNG ĐO)
* **Tiêu đề:** `2. Preparation of Gage R&R`
* **Cấu hình trạm đo Luminance:**
  * Thiết bị: Nguồn cấp (Power supply), đồ gá Pallet, CID test bench, hộp giả lập tín hiệu CAN (**CANSIM**), máy đo quang phổ **Konica Minolta CS-2000 (Spectroradiometer)** có độ phân giải **`0.01 Cd/m²`** (tương đương 0.00083% dung sai 1200 Cd/m², vượt xa chuẩn độ phân giải MSA $\le 5\%$).
  * Phần mềm điều khiển: **LG Moohantech** kết nối hệ thống **GMES**.
* **Tại sao dùng Type 1 và Type 3 Gage Study (mà không dùng Type 2)?**
  * Vì trạm đo Luminance vận hành **tự động hoàn toàn bằng cơ cấu Servo/Robot**, không có yếu tố con người (Operator) căn chỉnh khi đo, nên biến thiên Reproducibility (giữa các người đo) bằng 0. Do đó theo chuẩn MSA (AIAG):
    1. **Type 1 Gage Study:** Đo **1 mẫu chuẩn Golden Sample (`Reference = 910 Cd/m²`) lặp lại 30 lần** để đánh giá **Độ chệch (Bias)** và **Độ lặp lại tĩnh (Repeatability)** thông qua chỉ số $C_g, C_{gk}$.
    2. **Type 3 Gage Study:** Đo **25 mẫu sản phẩm khác nhau, mỗi mẫu lặp lại 2 lần (`N = 50`)** để đánh giá **Độ lặp lại động (Repeatability)** khi gắp/chạy tự động và khả năng phân biệt sản phẩm (**NDC**).

---

#### SLIDE 07: 2.1 TYPE 1 STUDY (ĐÁNH GIÁ THIẾT BỊ TRƯỚC CẢI TIẾN)
* **Tiêu đề:** `2.1 Type 1 Study`
* **Dữ liệu:** 30 lần đo liên tiếp trên mẫu chuẩn `Reference = 910.00 Cd/m²`, `Spec = 800.00 ~ 2000.00 Cd/m²` (`Tolerance = 1200 Cd/m²`).
* **Phân tích kết quả Minitab:**
  * **Kiểm định phân bố chuẩn (Probability Plot):** `Mean = 824.00`, `StDev = 11.999`, `N = 30`, `AD = 0.352`, **`P-Value = 0.445 > 0.05`** → Dữ liệu đo lặp tuân theo phân bố chuẩn, đủ điều kiện dùng kiểm định t-test trong Type 1 Study.
  * **Đánh giá Độ chệch (Bias):**
    * Trung bình đo được `Mean = 824.000 Cd/m²` so với `Ref = 910.00 Cd/m²` → **`Bias = −86.00 Cd/m²`** (cả 30 lần đo đều tụt sâu dưới 910!).
    * Kiểm định t-test (`H0: Bias = 0` vs `H1: Bias ≠ 0`): `T = 39.257`, **`P-Value = 0.000 (< 0.001 ≤ 0.05)`** → **Bác bỏ $H_0$, kết luận hệ thống đo bị lệch âm nghiêm trọng (`−86.00 Cd/m²`) → FAIL!**
  * **Đánh giá Năng lực thiết bị đo ($C_g, C_{gk}$):**
    * $C_g = \frac{0.20 \times \text{Tolerance}}{6 \times s} = \frac{240}{71.994} = \mathbf{3.33 \ge 1.33}$ (**PASS**), tương ứng `%Var(Repeatability) = 20% / Cg = 6.00% ≤ 15%` (**PASS**).
    * $C_{gk} = \frac{0.10 \times \text{Tolerance} - |\text{Bias}|}{3 \times s} = \frac{120 - 86.00}{35.997} = \mathbf{0.94 < 1.33}$ (**FAIL**), tương ứng **`%Var(Repeatability & Bias) = 20% / Cgk = 21.17% > 15%` (FAIL)**.
* **Kết luận cốt lõi cần nhấn mạnh với Giám khảo:**
  > *"Bản thân cảm biến quang học CS-2000 có độ chụm rất tốt ($C_g = 3.33$), nhưng hệ thống đang mắc sai số hệ thống làm lệch tâm âm **−86 Cd/m²** khiến $C_{gk} = 0.94$ bị FAIL. Một màn hình thực tế sáng 910 Cd/m² đưa vào trạm chỉ đọc ra 824 Cd/m², đẩy toàn bộ dải sản phẩm sát xuống vách lỗi 800 Cd/m²!"*

---

#### SLIDE 08: 2.2 TYPE 3 STUDY (ĐỘ LẶP LẠI TRẠM TỰ ĐỘNG TRƯỚC CẢI TIẾN)
* **Tiêu đề:** `2.2 Type 3 Study`
* **Dữ liệu:** 25 mẫu sản phẩm × 2 lần đo lặp (`N = 50`).
* **Phân tích kết quả Minitab Gage R&R (ANOVA):**
  * **Bảng ANOVA:** `Part DF = 24, SS = 65505.2, MS = 2729.38, F = 18.95, P = 0.000`; `Repeatability DF = 25, SS = 3600.7, MS = 144.03`.
  * **%Contribution (Variance Components):** Gage R&R = `144.027 / 1436.706` = **`10.02% > 9%` → NG** (tiêu chuẩn AIAG: `< 1%` đạt tốt, `1%~9%` chấp nhận có điều kiện, `> 9%` không chấp nhận).
  * **%Study Var (Gage Evaluation):** Gage R&R `SD = 12.001`, `Study Var = 72.01` trên `Total Study Var = 227.42` → **`%Study Var = 31.66% > 30%` → NG**.
  * **%Tolerance:** `72.01 / 1200` = **`6.00% < 10%` → OK**.
  * **NDC (Number of Distinct Categories):** $\text{NDC} = \lfloor \sqrt{2} \times \frac{35.954}{12.001} \rfloor = \lfloor 4.237 \rfloor = \mathbf{4 < 5}$ **→ NG**.
* **Kết luận:** Hệ thống đo trước cải tiến **KHÔNG ĐẠT (`NOT acceptable`)** cả về độ chính xác (Type 1 Bias = `−86 Cd/m²`) lẫn độ lặp lại khi chạy hàng loạt trên chuyền (Type 3 `%Contribution = 10.02%`, `%Study Var = 31.66%`, `NDC = 4`).

---

#### SLIDE 09: 2.3 XBAR-R CHART REVIEW (KIỂM SOÁT THỐNG KÊ TRƯỚC CẢI TIẾN)
* **Tiêu đề:** `2.3 Xbar-R Chart Review`
* **Phương pháp lấy mẫu (Rational Subgroup Sampling):** Lấy 5 sản phẩm đầu tiên mỗi ngày tại chuyền FA Line IVI 5 trong 10 ngày liên tiếp (`20-Feb-2026 ~ 01-Mar-2026`, tổng `N = 50` mẫu).
* **Phân tích biểu đồ kiểm soát Xbar-R:**
  * Đường tâm trung bình $\bar{\bar{X}} = \mathbf{826.25\text{ Cd/m}^2}$ (`UCL = 846.62`, `LCL = 805.88`); Đường tâm độ rộng $\bar{R} = \mathbf{35.30\text{ Cd/m}^2}$ (`UCL = 74.62`, `LCL = 0.00`).
  * Phát hiện **2 điểm Out-of-Control (báo đỏ `1`)**:
    1. Subgroup 1 (`20-Feb`): $\bar{X}_1 = \mathbf{802.70 < \text{LCL } 805.88}$.
    2. Subgroup 10 (`01-Mar`): $R_{10} = 853.94 - 755.89 = \mathbf{98.05 > \text{UCL } 74.62}$ (do có mẫu rớt sâu xuống `755.89 Cd/m²`).
  * Có **7 / 50 mẫu (`14.0%`, tương đương `140,000 ppm`)** rớt xuống dưới ngưỡng `LSL = 800 Cd/m²`.
* **Kết luận:** Quy trình đang **KHÔNG ỔN ĐỊNH (Not in statistical control – có mặt nguyên nhân đặc biệt Special Cause)** và trung bình quy trình (`826.25 Cd/m²`) bị kéo quá sát cận dưới `LSL = 800 Cd/m²`.

---

#### SLIDE 10: 2.4 RESULT OF CURRENT CPK (NĂNG LỰC QUY TRÌNH BAN ĐẦU & MỤC TIÊU)
* **Tiêu đề:** `2.4 Result of current Cpk`
* **Phân tích năng lực quy trình (Before Improvement):**
  * **Kiểm định phân bố chuẩn (Anderson-Darling):** `Mean = 826.3`, `StDev = 19.63`, `N = 50`, `AD = 2.985`, **`P-Value < 0.005 < 0.05` → NG** (Dữ liệu bị kéo lệch đuôi trái do các điểm đọc thấp bất thường bởi nguyên nhân đặc biệt đã chỉ ra ở mục 2.3).
  * **Chỉ số năng lực quy trình:**
    * `Mean = 826.25 Cd/m²`, `StDev(Within) = 18.557` (pooled), `StDev(Overall) = 19.627`.
    * **`Cpk = CPL = (826.25 - 800) / (3 × 18.557) = 0.47 < 1.33`** (**`Z.Bench = 1.41`**) → **NG (Lack of process capability)**.
    * `Ppk = PPL = (826.25 - 800) / (3 × 19.627) = 0.45` (`Z.Bench = 1.34`).
* **Thiết lập mục tiêu cải tiến (Target of Improvement):**
  * Triệt tiêu độ chệch hệ thống đo (`Bias → 0`, mẫu chuẩn 910 đọc đúng `910 Cd/m²`).
  * Nâng năng lực quy trình từ **`Cpk = 0.47 (Z = 1.41)`** lên **`Cpk ≥ 1.33 (Z ≥ 4.5)`** (trung bình cần đạt tối thiểu $\text{LSL} + 4.5\sigma = 800 + 4.5 \times 18.56 \approx 884\text{ Cd/m}^2$).
  * Đưa tỷ lệ lỗi từ **`226,624 ppm → 0 ppm`**.

---

### 🟨 GIAI ĐOẠN 3: ANALYZE (PHÂN TÍCH & KIỂM CHỨNG NGUYÊN NHÂN GỐC)

#### SLIDE 11: 3.1 ROOT CAUSE LOGIC TREE (CÂY LOGIC LOẠI TRỪ NGUYÊN NHÂN)
* **Tiêu đề:** `3.1 Root cause of measurement system problem`
* **Phân tích 4M bằng Cây Logic (Logic Tree):**
  1. **Man (Con người):** Quy trình đo tự động 100% → **Loại trừ (`Man is not related`)**.
  2. **Material (Linh kiện LCD):** Gửi trả các màn hình báo NG về nhà cung cấp **HEESUNG** để kiểm tra lại trên bàn đo chuẩn của hãng → **Tất cả đều đạt OK 100% (`LCD is not affected`)** *(có đính kèm file báo cáo thực nghiệm `Return Heesung` ngay trên slide)*.
  3. **Method (Phương pháp/Trình tự test):** Cùng trình tự test (sequence/timing) và cách cắm giắc trên pallet áp dụng cho mọi model khác trên chuyền đều OK, các chức năng khác trên cùng bộ J1 Dual cũng OK → **Loại trừ (`Sequence is not affected`, `Not relate to set plugging in`)**.
  4. **Machine (Thiết bị tại trạm Luminance):**
     * Nguồn cấp (`Power supply`) ổn định; đổi thử `Pallet` khác kết quả không đổi → Loại trừ.
     * Cô lập **3 yếu tố nghi vấn tiềm năng (Potential Factors ✔)** cần kiểm định thống kê:
       * **Yếu tố 1:** Hộp **CANSIM** phát tín hiệu điều khiển yếu làm màn hình LCD không lên hết độ sáng (`Change new CANSIM`).
       * **Yếu tố 2:** Bản thân cảm biến **Camera CS2000** bị lỗi đo sai (`Change new camera`).
       * **Yếu tố 3:** **Góc đặt Camera (Camera Angle)** bị lệch khỏi phương vuông góc 90° (`Change angle of camera`).

---

#### SLIDE 12: 3.1 IDENTIFICATION PLAN (KẾ HOẠCH KIỂM ĐỊNH 2-SAMPLE T)
* **Tiêu đề:** `3.1 Root cause of measurement system problem (2 Samples T)`
* **Thiết kế thực nghiệm:** Sử dụng kiểm định **Paired t-test** (đo trên cùng 30 bộ sản phẩm trước và sau khi thay đổi từng yếu tố) kết hợp **Two-Sample Welch's t-test** ở mức ý nghĩa $\alpha = 0.05$ để đánh giá khách quan từng yếu tố nghi vấn.

---

#### SLIDE 13: KIỂM ĐỊNH YẾU TỐ 1 – THAY HỘP CANSIM MỚI (`CHANGE TO NEW CANSIM`)
* **Giả thuyết:**
  * $H_0$: Thay hộp CANSIM mới **không ảnh hưởng** đến giá trị độ sáng đo tại trạm ($\mu_{\text{diff}} = 0$).
  * $H_1$: Thay hộp CANSIM mới **có ảnh hưởng** đến giá trị độ sáng ($\mu_{\text{diff}} \ne 0$).
* **Kết quả thống kê (30 bộ sản phẩm):**
  1. **Kiểm định chuẩn (Normality Test):** Before `AD = 0.445, P = 0.265 > 0.05`; After `AD = 0.536, P = 0.156 > 0.05` → Cả 2 tập dữ liệu đều tuân theo phân bố chuẩn, đủ điều kiện chạy t-test.
  2. **Giá trị trung bình:** Before `Mean = 831.40 (StDev = 37.30)` vs After `Mean = 830.06 (StDev = 34.92)` → Chênh lệch chỉ `1.34 Cd/m²` (nằm hoàn toàn trong nhiễu đo lường).
  3. **Paired T-Test (trên cùng 30 bộ):** `T-Value = 0.41`, **`P-Value = 0.682 > 0.05`** (`95% CI: -5.26 ~ 7.94` chứa số 0).
  4. **Two-Sample T-Test (Welch, DF = 57):** `T-Value = 0.14`, **`P-Value = 0.887 > 0.05`**.
* **Kết luận:** Chấp nhận $H_0$ → **Hộp CANSIM không phải là nguyên nhân gây lỗi (Loại trừ).**

---

#### SLIDE 14: KIỂM ĐỊNH YẾU TỐ 2 – THAY CAMERA CS2000 MỚI (`CHANGE TO NEW CAMERA`)
* **Giả thuyết:**
  * $H_0$: Thay thân máy Camera CS2000 mới **không ảnh hưởng** đến giá trị độ sáng đo tại trạm.
  * $H_1$: Thay thân máy Camera CS2000 mới **có ảnh hưởng** đến giá trị độ sáng.
* **Kết quả thống kê (30 bộ sản phẩm):**
  1. **Kiểm định chuẩn (Normality Test):** Before `AD = 0.616, P = 0.099 > 0.05`; After `AD = 0.674, P = 0.070 > 0.05` → Đạt phân bố chuẩn.
  2. **Giá trị trung bình:** Before `Mean = 840.75 (StDev = 39.87)` vs After `Mean = 842.57 (StDev = 40.63)` → Chênh lệch `-1.82 Cd/m²` (lắp một chiếc camera mới vào đúng gá đang bị lệch góc thì vẫn đọc thấp như cũ!).
  3. **Paired T-Test (trên cùng 30 bộ):** `T-Value = -0.64`, **`P-Value = 0.524 > 0.05`** (`95% CI: -7.60 ~ 3.96` chứa số 0).
  4. **Two-Sample T-Test (Welch, DF = 57):** `T-Value = -0.18`, **`P-Value = 0.862 > 0.05`**.
* **Kết luận:** Chấp nhận $H_0$ → **Thân máy Camera CS2000 đang dùng hoàn toàn tốt, không bị hỏng cảm biến (Loại trừ).**

---

#### SLIDE 15: KIỂM ĐỊNH YẾU TỐ 3 – HIỆU CHỈNH GÓC CAMERA (`CHANGE CAMERA ANGLE`) ⭐
* **Giả thuyết:**
  * $H_0$: Hiệu chỉnh góc đặt camera **không ảnh hưởng** đến giá trị độ sáng đo tại trạm.
  * $H_1$: Hiệu chỉnh góc đặt camera **có ảnh hưởng** đến giá trị độ sáng.
* **Kết quả thống kê đột phá (30 bộ sản phẩm):**
  1. **Kiểm định chuẩn (Normality Test):** Before `AD = 0.265, P = 0.671 > 0.05`; After `AD = 0.400, P = 0.342 > 0.05` → Đạt phân bố chuẩn hoàn hảo.
  2. **Sự dịch chuyển trung bình:**
     * Trước khi chỉnh góc (Before): `Mean = 825.41 Cd/m²` (`StDev = 34.22`).
     * Sau khi chỉnh góc về 90° (After): **`Mean = 912.73 Cd/m²`** (`StDev = 29.35`).
     * Độ sáng đo được tăng vọt **`+87.32 Cd/m²`** (`Difference = Before − After = −87.32 Cd/m²`) — **khớp hoàn toàn với độ lệch âm `Bias = −86.00 Cd/m²` đã phát hiện trong nghiên cứu Type 1 Study ở Slide 7!**
  3. **Paired T-Test (trên cùng 30 bộ):** `T-Value = -43.34`, **`P-Value < 0.001 (< 0.05)`**, `95% CI: (-91.44, -83.20)`.
  4. **Two-Sample T-Test (Welch, DF = 56):** `T-Value = -10.61`, **`P-Value < 0.001 (< 0.05)`**, `95% CI: (-103.81, -70.83)`.
* **Kết luận:** Bác bỏ $H_0$ → **GÓC ĐẶT CAMERA CHÍNH LÀ NGUYÊN NHÂN GỐC RỄ (ROOT CAUSE VERIFIED)!**

---

#### SLIDE 16: BẢNG TỔNG HỢP KẾT QUẢ KIỂM ĐỊNH (`SUMMARY OF 2 SAMPLES T`)
* **Bảng tóm tắt 3 yếu tố:**
  1. `CANSIM send weak signal`: `P-value = 0.682 > 0.05` → **Not root cause**
  2. `Measure incorrectly (Camera body)`: `P-value = 0.524 > 0.05` → **Not root cause**
  3. `Camera angle changed`: **`P-value < 0.001 < 0.05`** → **✔ Root Cause (Significant effect)**

---

#### SLIDE 17: PHÂN TÍCH 5-WHY & KẾ HOẠCH HÀNH ĐỘNG (`5-WHY & ACTION PLAN`)
* **Hiện trạng lỗi (Problem):** Tháng 2/2026 phát sinh cao điểm `92 EA / 240 EA = 383,333 ppm` (tổng giai đoạn trước cải tiến: `143 EA / 631 EA = 226,624 ppm`). Hình chụp màn hình trạm test cho thấy bước đo `#26 [DETECTOR] MEASUREMENT` báo `773.40 Cd/m² < MIN 800` (NG).
  * *(Lưu ý kỹ thuật để trả lời nếu Giám khảo hỏi về chuỗi số `773.40, 0.322, 0.304` và `800, 0.0001, 0.0001 ~ 9999, 0.9999, 0.9999` trên màn hình phần mềm Moohantech: Máy quang phổ CS-2000 xuất ra bộ 3 giá trị quang học gồm **Độ chói $L_v$ (`773.40 Cd/m²`)** và **tọa độ sắc độ màu CIE 1931 $x = 0.322, y = 0.304$**. Trong bản vẽ kỹ thuật sản phẩm, Spec của Luminance là **`800 ~ 2000 Cd/m²`**; còn ở bước lệnh phần mềm số 26, kỹ sư phần mềm chỉ dùng để chặn cận dưới độ sáng `800 Cd/m²` nên để mở cận trên `9999` và mở dải `x, y` từ `0.0001 ~ 0.9999`)*.
* **Phân tích 5-Why tìm nguyên nhân gốc cơ khí & quản lý:**
  1. **Why 1:** Tại sao độ sáng đo được dưới chuẩn (`800~2000 Cd/m²`)? → Vì trục quang học của camera không vuông góc (`90°`) với bề mặt màn hình LCD.
  2. **Why 2:** Tại sao trục camera không vuông góc? → Vì góc đặt camera bị trôi lệch khỏi chuẩn `90°` sau thời gian dài vận hành sản xuất.
  3. **Why 3:** Tại sao góc camera lại bị trôi lệch? → Vì model J1 Dual có 2 màn hình (PID/CID), cơ cấu gá camera phải di chuyển lặp đi lặp lại liên tục giữa 2 vị trí, rung động cơ học làm lỏng cơ cấu gá chỉnh góc.
  4. **Why 4 & 5:** Tại sao không phát hiện sớm trước khi sinh ra hàng loạt lỗi? → Vì chưa có bảng kiểm tra hàng ngày (Daily Master Sample Check Sheet) để kiểm chứng góc đặt camera đầu mỗi ca sản xuất.
* **Ba hành động khắc phục & phòng ngừa (Improvement Actions):**
  1. Dạy lại tọa độ Robot (Teaching robot) và cân chỉnh góc Camera CS-2000 về chuẩn **`90.0°`** bằng máy quét 3D Creaform (`Mr. Hung PE`, hoàn thành `14-Jun-2026`).
  2. Bổ sung **Check Sheet kiểm tra mẫu chuẩn Master Sample** hàng ngày đầu ca để kiểm soát góc camera.
  3. Thông báo chính thức cho nhà cung cấp **HEESUNG** rằng tấm nền LCD hoàn toàn OK, ngừng việc trả hàng scrap oan uổng.

---

### 🟧 GIAI ĐOẠN 4: IMPROVE (CẢI TIẾN & XÁC THỰC HIỆU QUẢ)

#### SLIDE 18: 4.1 SHORT-TERM IMPROVEMENT – CÂN CHỈNH GÓC CAMERA 3D (BEFORE / AFTER)
* **Tiêu đề:** `4.1 Correct the camera angle (before / after)`
* **Kết quả đo kiểm 3D bằng thiết bị quét quang học 3D Creaform:**
  * **Trước cải tiến (Before):** Góc trục quang học camera so với mặt phẳng màn hình bị nghiêng lệch: **`XZ = 89.075° ; YZ = 88.806°`** (lệch `~0.93°` đến `1.19°` so với phương vuông góc 90°).
  * **Sau cải tiến (After):** Cân chỉnh cơ khí đưa góc trục quang học về sát tuyệt đối 90°: **`XZ = 89.889° ; YZ = 89.889°`** (sai lệch chỉ còn `0.11°`).
* **Kiểm chứng thực tế trên 5 bộ J1 Dual PPR RHD (Dữ liệu PE):**
  * **Before:** `853.95 / 1052.40 / 850.68 / 870.22 / 796.79 Cd/m²` (Trung bình `884.81 Cd/m²`, có 1 bộ NG `796.79 < 800`).
  * **After:** `954.01 / 1094.30 / 952.56 / 971.34 / 901.94 Cd/m²` (Trung bình `974.83 Cd/m²`, **100% OK**, độ sáng tăng trung bình **`+90.02 Cd/m² ≈ +90 Cd/m²`**).

---

#### SLIDE 19: 4.1 KIỂM TRA ĐỒNG TÂM CAMERA & TỌA ĐỘ SERVO (LHD vs RHD)
* **Tiêu đề:** `4.1 Correct the camera angle: camera position and servo position`
* **Bản chất kỹ thuật cực kỳ quan trọng:**
  1. **Đồng tâm quang học:** Qua ống ngắm (viewfinder) của CS-2000, vòng tròn đen hồng tâm của cảm biến đã trùng khít hoàn toàn với tâm phát sáng của màn hình (`Camera center coincides with the SET center`).
  2. **Sự đối xứng gương giữa bản Tay lái nghịch (RHD) và Tay lái thuận (LHD):**
     * Cả 2 dòng xe **J1 Dual PPR RHD** và **J1 Dual PPR LHD** đều dùng chung 2 tọa độ Servo là **Position 48** (bên trái đồ gá) và **Position 49** (bên phải đồ gá):
       * Trên bản **RHD (Right-Hand Drive - ghế lái bên phải, ghế phụ bên trái)**: Màn hình phụ **PID (Privacy)** nằm bên trái (**Position 48**), màn hình chính **CID (Public)** nằm bên phải (**Position 49**).
       * Trên bản **LHD (Left-Hand Drive - ghế lái bên trái, ghế phụ bên phải)**: Màn hình chính **CID (Public)** nằm bên trái (**Position 48**), màn hình phụ **PID (Privacy)** nằm bên phải (**Position 49**).
     * Nhờ chuẩn hóa cả góc 90.0° và tâm tọa độ Servo 48 & 49, cả 2 dòng RHD và LHD đều được đảm bảo đo chính xác ngay tại tâm màn hình.

---

#### SLIDE 20: 4.2 TẠI SAO CHỈ MÀN HÌNH PRIVACY (PID) BỊ LỖI? (BẢN CHẤT QUANG HỌC MÀNG LCF) ⭐
* **Tiêu đề:** `4.2 Why only Privacy (PID) screens failed: angle sensitivity`
* **Giải thích vật lý quang học thuyết phục nhất toàn dự án:**
  * Chuyền IVI 5 sản xuất 13 dòng sản phẩm (Bentayga, Macan LZV, 992, J1 CID, G3 CID, Lamborghini...). Tất cả các màn hình **CID** đều là loại **Public (Normal)** có góc nhìn rộng (Wide Viewing Angle) để cả người lái và hành khách đều nhìn rõ.
  * Riêng màn hình phụ **PID** trên 3 dòng màn hình đôi cao cấp (**`E3PA Dual`, `G3 Dual`, `J1 Dual PPR`**) được trang bị tính năng **Chống nhìn trộm (Privacy Display)**: Bên trong mô-đun đèn nền BLU có ép một lớp màng vi trập quang học **LCF (Light Control Film / Louver Film)** giúp hướng toàn bộ chùm sáng về phía ghế hành khách và cắt sập ánh sáng về phía ghế tài xế để tài xế không bị mất tập trung khi xe chạy.
  * **Chứng minh bằng dữ liệu đo góc (Viewing Angle Curve & Data Table):**
    * Khi góc nhìn thay đổi **chỉ `1°` (từ `89° → 90°`, tức từ `-1°` về `0°`)**:
      * Màn hình **Public (CID)** thay đổi độ sáng từ **`1255 → 1259 cd/m²`** (chênh lệch **`< 0.5%`** — hầu như phẳng tuyệt đối, nên góc camera lệch 1° không hề ảnh hưởng!).
      * Màn hình **Privacy (PID có màng LCF)** nằm đúng trên sườn dốc cắt sáng nên độ sáng thay đổi vọt từ **`722.2 → 816.7 cd/m²`**, tức thay đổi tới **`≈ 13%` (`+13.08%` khi chỉnh từ 89° về 90°, hay tụt `-11.6%` khi nghiêng lệch 1°)**!
    * **Tại sao chỉ bản RHD bị lỗi hàng loạt?** Vì vị trí đo bị trôi góc ~1° là **Position 48 (bên trái)** — nơi đặt màn hình **PID (Privacy)** của bản **RHD** (còn ở Position 48 của bản LHD lại là màn hình CID Public nên không bị ảnh hưởng!). Đây là lý giải vật lý hoàn hảo 100%, gắn kết toàn bộ dữ liệu từ Define đến Improve!

---

#### SLIDE 21: 4.3 LONG-TERM IMPROVEMENT – BAN HÀNH CHECK SHEET MASTER SAMPLE
* **Tiêu đề:** `4.3 Add Master sample check sheet to control the camera angle`
* **Cơ chế kiểm soát phòng ngừa (Preventive Control):**
  * **Trước cải tiến (Before):** Không có mục kiểm tra góc camera bằng mẫu chuẩn độ sáng hàng ngày, nên khi gá camera bị trôi góc chỉ phát hiện được khi hàng loạt sản phẩm thật bị báo NG.
  * **Sau cải tiến (After):** Cập nhật bảng **Master Sample Check Sheet Porsche CID 10.9 inch (Tháng 06/2026)** tại chuyền, bổ sung kiểm tra **Master OK (`Reference = 910 Cd/m²`, giới hạn kiểm soát chặt `910 ± 5 Cd/m²`, Camera angle `90.0°`)** bên cạnh Master NG đầu mỗi ca làm việc để khóa chặt góc đặt camera trước khi cho phép sản xuất.

---

#### SLIDE 22: 4.4 TYPE 1 STUDY AGAIN AFTER IMPROVEMENT (NGHIỆM THU THIẾT BỊ ĐO)
* **Tiêu đề:** `4.4 Type 1 Study again after improvement`
* **Kết quả đo lặp 30 lần mẫu chuẩn `Reference = 910.00 Cd/m²` sau khi chỉnh góc 90.0°:**
  * **Kiểm định phân bố chuẩn:** `Mean = 909.95`, `StDev = 1.700`, `N = 30`, `AD = 0.479`, **`P-Value = 0.218 > 0.05`** (Chuẩn).
  * **Độ chệch (Bias):**
    * `Mean = 909.949 Cd/m²` → **`Bias = −0.05 Cd/m²`** (giảm từ **`−86.00 Cd/m²`** về **`−0.05 Cd/m²`**, coi như bằng 0!).
    * Kiểm định t-test (`H0: Bias = 0`): `T = 0.163`, **`P-Value = 0.871 > 0.05`** → Chấp nhận $H_0$, **Không còn sai số lệch tâm (PASS)!**
  * **Chỉ số năng lực đo ($C_g, C_{gk}$):**
    * `StDev = 1.700 Cd/m²` (`6×StDev = 10.197 Cd/m²` — nhờ cố định chặt lại gá camera, cả độ rung lắc lặp lại cũng giảm 7 lần từ `11.999` xuống `1.700 Cd/m²`!).
    * **`Cg = 23.54 ≥ 1.33` (PASS)** | **`Cgk = 23.53 ≥ 1.33` (PASS)** *(tăng vọt từ `0.94` lên `23.53`)*.
    * **`%Var(Repeatability) = 0.85% ≤ 15%` (PASS)** | **`%Var(Repeatability & Bias) = 0.85% ≤ 15%` (PASS)**.

---

#### SLIDE 23: 4.4 TYPE 3 STUDY AGAIN AFTER IMPROVEMENT (NGHIỆM THU ĐỘ LẶP LẠI TRẠM TỰ ĐỘNG)
* **Tiêu đề:** `4.4 Type 3 Study again after improvement`
* **Kết quả đo lại 25 mẫu × 2 lần lặp (`N = 50`) sau cải tiến:**
  * **%Contribution (Gage R&R):** Giảm từ `10.02%` xuống **`0.22% < 1%` → OK (Đẳng cấp World-Class)**.
  * **%Study Var:** Giảm từ `31.66%` xuống **`4.64% < 10%` → OK** (`SD Repeatability = 1.7161 Cd/m²` so với `SD Part = 36.9218 Cd/m²`).
  * **%Tolerance:** Giảm từ `6.00%` xuống **`0.86% < 10%` → OK**.
  * **NDC (Số nhóm phân biệt):** Tăng vọt từ `4` lên **`30 > 5` → OK**.

---

#### SLIDE 24: 4.5 PROCESS CAPABILITY REVIEW (NĂNG LỰC QUY TRÌNH SAU CẢI TIẾN)
* **Tiêu đề:** `4.5 Process Capability review`
* **Kết quả phân tích trên 50 mẫu sản xuất thực tế (10 ngày × 5 mẫu/ngày):**
  1. **Kiểm định phân bố chuẩn (Anderson-Darling):** `Mean = 911.9`, `StDev = 16.24`, `N = 50`, `AD = 0.334`, **`P-Value = 0.503 > 0.05` → PASS** (Dữ liệu tuân theo phân bố chuẩn hoàn hảo).
  2. **Năng lực quy trình (Process Capability):**
     * `Mean = 911.94 Cd/m²`, `StDev(Within) = 15.594 Cd/m²`, `StDev(Overall) = 16.235 Cd/m²`.
     * **Within Capability:** `Cp = 12.83`, `CPL = 2.39`, `CPU = 23.26` → **`Cpk = 2.39 ≥ 1.33` (`Z.Bench = 7.18`) → PASS!**
     * **Overall Capability:** `Pp = 12.32`, `PPL = 2.30`, `PPU = 22.34` → **`Ppk = 2.30` (`Z.Bench = 6.89`) → PASS!**
     * **Tỷ lệ lỗi kỳ vọng & quan sát (PPM):** `Observed = 0.00 PPM`, `Exp. Within = 0.00 PPM`, `Exp. Overall = 0.00 PPM`.
  3. **Đối chiếu Trước / Sau:**
     * **Before:** `Cpk = 0.47 (Z = 1.41) < 1.33` → **NG**
     * **After:** **`Cpk = 2.39 (Z = 7.18) ≥ 1.33`** → **OK (Tăng gấp 5.1 lần!)**

---

#### SLIDE 25: 4.5 PROCESS CAPABILITY REVIEW – ĐÁNH GIÁ MỨC SIGMA & Z-SHIFT
* **Tiêu đề:** `4.5 Process Capability review (Z value)`
* **Bản chất các chỉ số Z:**
  * **$Z_{\text{short term}} (Z_{st}) = 3 \times C_{pk} = \mathbf{7.18 \ge 4.5}$ → OK (`Technology is OK`):** Thể hiện năng lực công nghệ nội tại của thiết bị và quy trình đạt đẳng cấp vượt chuẩn 6 Sigma.
  * **$Z_{\text{long term}} (Z_{lt}) = 3 \times P_{pk} = \mathbf{6.89 \ge 4.5}$ → OK:** Thể hiện chất lượng thực tế khách hàng nhận được trong dài hạn.
  * **$Z_{\text{shift}} = Z_{st} - Z_{lt} = 7.18 - 6.89 = \mathbf{0.29 < 1.5}$ → OK (`Proper process control management`):** Độ trôi quy trình giữa các ngày cực nhỏ (`0.29` so với ngưỡng cho phép `1.5`), chứng tỏ quy trình được kiểm soát vô cùng chặt chẽ.
  * **Ma trận 4 góc phần tư (A, B, C, D):** Quy trình nằm trọn trong **Ô D (`Proper management & Proper skills` - chấm đỏ)**, khẳng định cả **Quản lý (Control)** và **Công nghệ (Technology)** đều đạt mức Xuất sắc (`Good`).

---

#### SLIDE 26: 4.6 CONCLUSION (TỔNG KẾT GIAI ĐOẠN IMPROVE)
* **Tiêu đề:** `4.6 Conclusion`
* **Tóm tắt logic xuyên suốt:**
  * Xác nhận hệ thống đo tại trạm Luminance bị lỗi lệch tâm do góc đặt camera bị trôi lệch ~1°.
  * Sau khi hiệu chỉnh góc camera về `90.0°`, toàn bộ các chỉ số MSA (`Type 1: Cg = 23.54, Cgk = 23.53 ≥ 1.33`; `Type 3: %Study Var = 4.64% < 10%, %Contribution = 0.22% < 1%, NDC = 30`) và Năng lực quy trình (`Cpk: 0.47 → 2.39`, `Z: 1.41 → 7.18`) đều đạt xuất sắc.
  * Tỷ lệ lỗi thực tế giảm từ **`226,624 ppm → 0 ppm`** trên **420 bộ sản phẩm** sản xuất sau cải tiến (cận trên khoảng tin cậy 95% theo quy tắc 3/n là `3/420 ≈ 7,100 ppm`, tức giảm tối thiểu `> 96%` so với baseline ngay cả ở biên thận trọng nhất).

---

### 🟥 GIAI ĐOẠN 5: CONTROL (KIỂM SOÁT BỀN VỮNG & KẾT QUẢ DỰ ÁN)

#### SLIDE 27: 5.1 XBAR-R CHART REVIEW AFTER IMPROVEMENT (BIỂU ĐỒ KIỂM SOÁT SAU CẢI TIẾN)
* **Tiêu đề:** `5.1 Xbar-R Chart Review after improvement`
* **Dữ liệu theo dõi dài hạn:** 10 ngày liên tiếp (`1-Jul ~ 10-Jul-2026`) × 5 bộ đầu ngày = 50 bộ.
* **Kết quả biểu đồ Xbar-R:**
  * Đường tâm $\bar{\bar{X}} = \mathbf{911.94\text{ Cd/m}^2}$ (`UCL = 933.10`, `LCL = 890.78`); Đường tâm $\bar{R} = \mathbf{36.68\text{ Cd/m}^2}$ (`UCL = 77.54`, `LCL = 0.00`).
  * **0 điểm Out-of-Control**, không có bất kỳ quy tắc Run test nào vi phạm → **Quy trình hoàn toàn ổn định thống kê theo thời gian (Stable over time)**.

---

#### SLIDE 28: 5.2 FUTURE PLAN / MANAGEMENT PLAN (KẾ HOẠCH QUẢN LÝ & NHÂN RỘNG HÀNG NGANG)
* **Tiêu đề:** `5.2 Future plan (Management plan)`
* **Quy trình quản lý mẫu chuẩn (Master Sample Management Procedure):**
  * **Tần suất:** Hàng ngày vào đầu mỗi ca (`08:00~10:00` ca ngày và `20:00~22:00` ca đêm).
  * **Người chịu trách nhiệm:** Kỹ thuật viên PM (`PM Technician`) & Tổ trưởng chuyền (`Line Leader`).
  * **3 Bước thực hiện chuẩn:**
    1. Đo mẫu chuẩn **Master Sample (`Reference = 910 Cd/m²`)** tại trạm Luminance. Giá trị đọc bắt buộc phải nằm trong **giới hạn kiểm soát `910 ± 5 Cd/m²`** (tương ứng `≈ ±3s` của Type 1 sau cải tiến với `s = 1.70 Cd/m²`) và trong Spec (`800~2000 Cd/m²`).
    2. **Kế hoạch phản ứng (Reaction Plan):** Nếu giá trị đọc vượt ngoài `910 ± 5 Cd/m²`, lập tức dừng phán định OK/NG và báo ngay cho Line Leader; đội PE & PM sẽ kiểm tra lại góc camera (mục tiêu `90.0°`) và xác nhận lại bằng Master Sample đạt chuẩn trước khi cho chạy lại chuyền.
    3. Tắt kiểm tra version GMES (SW/HW) trong chế độ đo Master Sample để tập trung đánh giá thuần túy độ ổn định phần cứng đo quang học.
* **Tiêu chuẩn hóa & Nhân rộng hàng ngang (Standardization & Horizontal Deployment):**
  * Đưa bước kiểm tra góc camera `90.0°` vào **SOP thiết lập máy trước sản xuất (Pre-production setup standard)**.
  * Nhân rộng quy trình kiểm tra Master Sample cho toàn bộ các dòng màn hình đôi có tấm nền **Privacy (PID)** đo bằng CS-2000 trên chuyền: **`E3PA Dual`, `G3 Dual`, `J1 Dual PPR`**. Vì màn hình Privacy nhạy góc `≈ 13% / 1°` (nghiêng 1° làm tụt `≈ 86 ~ 105 Cd/m²`), nên giới hạn kiểm soát chặt `±5 Cd/m²` sẽ bắt được mọi hiện tượng trôi góc ngay từ khi mới chớm lệch `< 0.1°`!

---

#### SLIDE 29: 5.3 RESULT OF PROJECT (TỔNG KẾT THÀNH QUẢ TOÀN DỰ ÁN)
* **Tiêu đề:** `5.3 Result of project`
* **Bảng & Biểu đồ theo dõi tỷ lệ lỗi Trước và Sau cải tiến:**
  * **Trước cải tiến (`Nov.2025 ~ Mar.2026`, tổng `143 NG / 631 EA = 226,624 ppm`):**
    * `16.Nov.2025`: `13 NG / 200 EA` = **`65,000 ppm`**
    * `2.Jan.2026`: `8 NG / 120 EA` = **`66,667 ppm`**
    * `23.Feb.2026`: `92 NG / 240 EA` = **`383,333 ppm`**
    * `1.Mar.2026`: `30 NG / 71 EA` = **`422,535 ppm`**
  * **Sau cải tiến (`Jul.2026 ~ Sep.2026`, tổng `0 NG / 420 EA = 0 ppm`):**
    * `15.Jul.2026`: `0 NG / 240 EA` = **`0 ppm`**
    * `21.Aug.2026`: `0 NG / 120 EA` = **`0 ppm`**
    * `20.Sep.2026`: `0 NG / 60 EA` = **`0 ppm`**
  * **Kiểm định thống kê Fisher's Exact Test:** So sánh tỷ lệ lỗi trước (`143/631`) và sau (`0/420`) cho **`p-value < 0.001`** ($p = 1.48 \times 10^{-35}$), khẳng định sự cải thiện về 0 ppm là có ý nghĩa thống kê tuyệt đối.
* **Tổng kết Hiệu quả Định lượng & Định tính (Quantitative & Qualitative Performance):**
  * **Defect rate:** `226,624 ppm → 0 ppm` (`0 NG / 420 sets`) — **Đạt 100% mục tiêu Stretch Goal**.
  * **Process Capability:** `Cpk: 0.47 → 2.39` (mục tiêu `≥ 1.33`), `Z: 1.41 → 7.18` (mục tiêu `≥ 4.5`).
  * **MSA:** Type 1 Bias `−86.00 → −0.05 Cd/m²`, `Cgk: 0.94 → 23.53`; Type 3 `%Study Var: 31.66% → 4.64%`, `NDC: 4 → 30`.
  * **Cost Saving:** Tránh lãng phí scrap oan 19 màn hình LCD/tháng (mức tháng 3/2026): **`19 LCD × $118.72 = $2,255.68/tháng`** (`≈ $27,068/năm`).

---

## 🛡️ BỘ 10 CÂU HỎI PHẢN BIỆN HÓC BÚA NHẤT CỦA GIÁM KHẢO & CÁCH TRẢ LỜI ĐIỂM TUYỆT ĐỐI

### Câu 1: *"Tại sao ở giai đoạn Measure (Slide 10), dữ liệu không chuẩn (P-value < 0.005) và biểu đồ Xbar-R (Slide 9) có 2 điểm Out-of-Control mà em vẫn tính và báo cáo Cpk = 0.47?"*
* **Cách trả lời chuẩn Master Black Belt:**
  > *"Dạ thưa Hội đồng, câu hỏi rất sâu sắc ạ! Đúng theo lý thuyết thống kê Six Sigma, khi quy trình chưa ổn định (có 2 điểm Out-of-Control trên Xbar-R) và không tuân theo phân bố chuẩn (AD P-value < 0.005 do các điểm đọc thấp kéo lệch đuôi trái), thì chỉ số Cpk = 0.47 (và Ppk = 0.45) được dùng như một **chỉ số tham chiếu định hướng (baseline indicator)** để lượng hóa mức độ thiếu hụt năng lực và đối chiếu với tỷ lệ thực tế 14% mẫu (7/50 mẫu = 140,000 ppm) rơi dưới LSL = 800 Cd/m². Ngay sau khi phát hiện 2 điểm Out-of-Control đó ở Slide 9, em đã kết luận quy trình có **Nguyên nhân đặc biệt (Special Cause)** do hệ thống đo bị trôi góc, và sau khi khử nguyên nhân đặc biệt ở giai đoạn Improve (Slide 24 & 27), dữ liệu đã chuẩn hoàn toàn (P = 0.503 > 0.05) và ổn định tuyệt đối trên Xbar-R, lúc đó Cpk = 2.39 phản ánh chính xác 100% năng lực thật của quy trình ạ!"*

### Câu 2: *"Tại sao trong dự án này gốc rễ là lỗi Hệ thống đo (MSA), đáng lẽ phải sửa ngay trong giai đoạn Measure trước khi đo Cpk, nhưng em lại đưa việc tìm nguyên nhân và sửa máy đo vào giai đoạn Analyze và Improve?"*
* **Cách trả lời chuẩn Master Black Belt:**
  > *"Dạ thưa Sếp, trên thực tế sản xuất tại nhà máy, ban đầu khi thấy lỗi Luminance NG cao (226,624 ppm), mọi người đều nghĩ là lỗi màn hình LCD của nhà cung cấp HEESUNG và đã gửi trả LCD về hãng để scrap. Nhờ thực hiện bước MSA (Type 1 & Type 3) và Xbar-R trong giai đoạn Measure, dự án mới phát hiện ra thiết bị đo tại trạm tự động bị lệch Bias −86 Cd/m². Tuy nhiên, tại thời điểm đó **chưa ai biết tại sao trạm đo lại bị lệch** (do hộp CANSIM phát tín hiệu yếu, do hỏng cảm biến CS-2000, hay do lệch góc cơ khí?). Vì vậy, việc lập Cây Logic (Logic Tree), chạy thực nghiệm kiểm định 2-Sample T cho 3 yếu tố (CANSIM, Thân Camera, Góc Camera) và phân tích 5-Why tìm ra nguyên nhân cơ khí + quang học màng LCF chính là linh hồn của giai đoạn **Analyze** và **Improve** trong đề tài cải tiến kỹ thuật kiểm tra (Inspection Engineering Project) này ạ!"*

### Câu 3: *"Ở Slide 7 (Type 1 Study trước cải tiến), tại sao Cg = 3.33 đạt rất cao (PASS) mà Cgk = 0.94 lại FAIL? Ý nghĩa vật lý của 2 con số này khác nhau thế nào?"*
* **Cách trả lời:**
  > *"Dạ, chỉ số $C_g = \frac{0.20 \times \text{Tolerance}}{6s} = 3.33$ chỉ đánh giá **Độ chụm (Repeatability/Precision)** — tức là khi camera đứng yên một chỗ bắn 30 phát liên tiếp vào mẫu chuẩn 910, các phát bắn chụm rất sát nhau quanh mức 824 Cd/m² ($s = 12.0\text{ Cd/m}^2$). Còn chỉ số $C_{gk} = \frac{0.10 \times \text{Tolerance} - |\text{Bias}|}{3s} = 0.94$ đánh giá đồng thời cả **Độ chụm và Độ đúng (Accuracy/Bias)**. Vì góc camera bị nghiêng ~1° làm ánh sáng qua màng LCF bị cản lại, tâm ngắm bị lệch âm **Bias = −86.00 Cd/m²** so với giá trị thật 910 Cd/m², nên $C_{gk}$ rớt xuống 0.94 (< 1.33 FAIL). Nói ngắn gọn: Súng bắn rất chụm ($C_g = 3.33$), nhưng thước ngắm bị lệch tâm 86 đơn vị làm bắn trượt hồng tâm ($C_{gk} = 0.94$)!"*

### Câu 4: *"Tại sao ở Type 1 (Slide 7) độ lệch chuẩn lặp lại là s = 12.0 Cd/m², nhưng sau khi chỉnh góc ở Slide 22 thì s lại giảm xuống còn 1.70 Cd/m² (Cg tăng từ 3.33 lên 23.54)?"*
* **Cách trả lời:**
  > *"Dạ có 2 lý do vật lý rất hay ở đây ạ: Thứ nhất, như phân tích ở 5-Why (Slide 17), trước cải tiến cơ cấu gá kẹp camera bị lỏng do rung chấn khi di chuyển qua lại giữa 2 màn hình, nên khi đo lặp lại có độ rơ rung cơ học ($s = 12.0$). Thứ hai, ở góc nghiêng 89° (Slide 20), điểm đo nằm ngay trên **sườn dốc đứng** của đường cong quang học màng LCF (nơi chỉ cần rung nhẹ $0.1^\circ$ là độ sáng dao động cả chục $Cd/m^2$); còn sau khi chỉnh về góc chuẩn 90.0° và siết chặt cơ cấu gá, điểm đo dịch chuyển lên gần vùng đỉnh thoải hơn và không còn độ rơ cơ khí, nên độ lệch chuẩn lặp lại giảm từ $12.0$ xuống chỉ còn $1.70\text{ Cd/m}^2$!"*

### Câu 5: *"Ở Slide 13, 14, 15, tại sao em trình bày cả Paired T-test lẫn Two-Sample T-test? Hai kiểm định này khác nhau thế nào?"*
* **Cách trả lời:**
  > *"Dạ, trong thực nghiệm em lấy **cùng 30 bộ màn hình (same 30 sets)** đo trước và sau khi thay đổi từng yếu tố. Vì đo trên cùng từng cá thể màn hình trước-sau nên **Paired T-test** là kiểm định chính xác và mạnh nhất (loại bỏ được nhiễu biến thiên giữa các màn hình khác nhau, ví dụ ở Slide 15 cho $T = -43.34, P < 0.001$). Đồng thời em chạy song song cả **Two-Sample Welch's T-test** (coi 2 tập trước-sau là 2 mẫu độc lập không giả định phương sai bằng nhau, cho $T = -10.61, P < 0.001$) theo đúng tên công cụ trong template chuẩn. Cả 2 kiểm định đều cho cùng một kết luận thống nhất tuyệt đối ở cả 3 thí nghiệm!"*

### Câu 6: *"Tại sao cùng trên một trạm đo, camera bị nghiêng 1° mà 12 dòng xe khác (và màn hình CID) đều PASS, chỉ riêng màn hình PID của dòng Porsche J1 Dual PPR RHD lại bị NG?"*
* **Cách trả lời (Điểm ăn tiền lớn nhất ở Slide 19 & 20):**
  > *"Dạ đây chính là phát hiện kỹ thuật tâm đắc nhất của dự án ở Slide 19 và Slide 20 ạ:  
  > 1. **Về mặt quang học (Slide 20):** Màn hình chính CID và các dòng xe thường dùng tấm nền **Public** góc nhìn rộng, nên khi nghiêng 1° độ sáng chỉ đổi `< 0.5%` (`1255 → 1259 Cd/m²`). Ngược lại, màn hình phụ PID của dòng J1 Dual PPR tích hợp màng chống nhìn trộm **LCF (Louver film)** có góc mở cực hẹp; khi nghiêng 1° (`89° → 90°`) độ sáng thay đổi tới **`13%` (`722.2 → 816.7 Cd/m²`)**.  
  > 2. **Về mặt vị trí gá (Slide 19):** Vị trí bị trôi góc ~1° là **Servo Position 48 (bên trái)**. Trên xe tay lái nghịch (**RHD**), ghế phụ nằm bên trái nên màn hình **PID (Privacy)** nằm đúng ở **Position 48** (còn trên xe tay lái thuận **LHD**, ở Position 48 lại là màn hình CID Public!). Đó là lý do vì sao lỗi chỉ đánh trúng vào màn hình PID của bản RHD!"*

### Câu 7: *"Ở Slide 29, bảng dữ liệu ghi ngày 1.Mar.2026 có 30 con NG, nhưng phần tính chi phí Scrap ở Slide 2 và Slide 29 lại tính 19 LCD × $118.72 = $2,255.68. Tại sao là 19 mà không phải 30?"*
* **Cách trả lời:**
  > *"Dạ thưa Sếp, 30 bộ là số lượng báo lỗi NG ở lần test đầu tiên tại trạm trên chuyền FA trong đợt sản xuất tháng 3/2026. Theo quy trình xử lý hàng lỗi tại chuyền (như nêu ở Slide 2 mục Management Issue), các bộ NG được đưa ra retest lại; có 11 bộ nằm mấp mé sát ngưỡng 800 Cd/m² khi gá lại lần 2 đã qua được, còn **19 màn hình LCD** vẫn báo dưới 800 Cd/m² sau retest nên bị tháo ra trả về nhà cung cấp HEESUNG để scrap. Để tính chi phí tài chính trung thực và sát thực tế kế toán nhất, em chỉ tính chi phí scrap trực tiếp trên **19 tấm LCD thực tế bị loại bỏ** trong tháng 3 (`19 × $118.72 = $2,255.68/tháng`), không thổi phồng số liệu ạ!"*

### Câu 8: *"Ở Slide 28, tại sao giới hạn kiểm soát hàng ngày cho mẫu Master Sample (910 Cd/m²) lại đặt là 910 ± 5 Cd/m² trong khi Spec sản phẩm là 800 ~ 2000 Cd/m²?"*
* **Cách trả lời:**
  > *"Dạ, `800 ~ 2000 Cd/m²` là **Giới hạn tiêu chuẩn sản phẩm (Specification Limits - LSL/USL)** dùng để phán định các màn hình sản xuất hàng loạt (vì bản thân độ sáng giữa các tấm nền LCD khác nhau có độ lệch chuẩn $\sigma_{\text{part}} \approx 16 \sim 36\text{ Cd/m}^2$). Còn đối với **1 tấm màn hình mẫu chuẩn duy nhất (Master Sample có độ sáng thực = 910 Cd/m²)**, mục đích của chúng ta là kiểm soát **độ trôi góc của máy đo**. Theo kết quả Type 1 sau cải tiến (Slide 22), khi đo trên mẫu chuẩn 910 này, độ lệch chuẩn lặp lại của máy chỉ là $s = 1.70\text{ Cd/m}^2$. Do đó, giới hạn kiểm soát $\pm 3s$ của riêng máy đo trên mẫu Master là $\pm 3 \times 1.70 = \pm 5.1 \approx \mathbf{\pm 5\text{ Cd/m}^2}$ (`905 ~ 915 Cd/m²`). Nếu để dải rộng 800~2000 cho mẫu Master thì khi góc máy trôi lệch 1° (mẫu 910 tụt xuống 824 Cd/m²) vẫn nằm trên 800 nên sẽ không bắt được lỗi trôi góc! Đặt ngưỡng `910 ± 5 Cd/m²` giúp phát hiện ngay lập tức khi góc camera mới chớm trôi lệch dù chỉ 0.1°!"*

### Câu 9: *"Trên hình chụp màn hình phần mềm test (Slide 17 & 18) và Check Sheet (Slide 21), dòng Spec trong phần mềm ghi `800,0.0001,0.0001 ~ 9999,0.9999,0.9999`, còn kết quả ghi `773.40,0.322,0.304`. Các con số này nghĩa là gì?"*
* **Cách trả lời:**
  > *"Dạ, máy quang phổ Konica Minolta CS-2000 khi đo sẽ trả về chuỗi 3 thông số theo hệ không gian màu CIE 1931 là **`Lv, x, y`**:  
  > - Số đầu tiên (`773.40`) là **Độ chói Luminance ($L_v$, đơn vị $Cd/m^2$)** — đối chiếu với cận dưới `800` nên bị báo đỏ NG.  
  > - Hai số tiếp theo (`0.322, 0.304`) là **tọa độ sắc độ màu trắng CIE ($x, y$)**.  
  > Trong bản vẽ kỹ thuật của Porsche, tiêu chuẩn độ chói là **`800 ~ 2000 Cd/m²`**. Còn trong bước lệnh `#23/#26` của phần mềm test tại trạm, bước này chỉ làm nhiệm vụ bắt lỗi thiếu sáng (`< 800 Cd/m²`), nên lập trình viên đặt cận dưới là `800` và để mở cận trên `9999` cùng tọa độ màu `0.0001 ~ 0.9999` (vì tọa độ màu đã được kiểm tra ở bước White Balance riêng)."*

### Câu 10: *"Sau cải tiến em mới kiểm tra trên 420 bộ sản phẩm (0 NG / 420 sets). Với 420 bộ mà kết luận 0 ppm thì cỡ mẫu có đủ độ tin cậy thống kê không?"*
* **Cách trả lời:**
  > *"Dạ thưa Hội đồng, em đã tính toán kiểm định thống kê cho cỡ mẫu 420 bộ này ở Slide 26 và Slide 29 từ 2 góc độ độc lập:  
  > 1. **Về dữ liệu định tính (Attribute data - 0 NG / 420 sets):** Kiểm định chính xác **Fisher's Exact Test** so sánh trước cải tiến (`143 NG / 631 sets`) và sau cải tiến (`0 NG / 420 sets`) cho **$p\text{-value} = 1.48 \times 10^{-35} \ll 0.001$**. Ngay cả khi lấy cận trên khoảng tin cậy 95% theo quy tắc thống kê $3/n$ ($3/420 = 7,142\text{ ppm}$), thì mức lỗi tối đa có thể xảy ra vẫn giảm hơn **96.8%** so với mức ban đầu (`226,624 ppm`).  
  > 2. **Về dữ liệu định lượng liên tục (Continuous data):** Dựa trên phân bố chuẩn của dữ liệu độ sáng sau cải tiến ($\mu = 911.94\text{ Cd/m}^2, \sigma_W = 15.594\text{ Cd/m}^2, C_{pk} = 2.39, Z_{st} = 7.18$), khoảng cách từ tâm quy trình tới cận dưới `LSL = 800 Cd/m²` lên tới **$7.18\sigma$**, tương ứng xác suất xuất hiện sản phẩm dưới 800 Cd/m² về mặt lý thuyết là **$0.00\text{ ppm}$** ($< 10^{-12}$). Sự kết hợp giữa $C_{pk} = 2.39$ và $0\text{ NG}/420\text{ sets}$ chứng minh kết quả 0 ppm là hoàn toàn vững chắc!"*

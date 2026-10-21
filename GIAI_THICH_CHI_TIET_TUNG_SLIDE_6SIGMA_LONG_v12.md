# 📘 TÀI LIỆU HƯỚNG DẪN THUYẾT TRÌNH & BẢN CHẤT TỪNG SLIDE
## Dự Án 6 Sigma Green Belt: Giảm Tỷ Lệ Lỗi Độ Sáng (Luminance NG) Model Porsche CID J1 Dual
**Tác giả:** Nguyễn Đức Long – Kỹ sư IVI LD  
**File báo cáo hoàn chỉnh:** `6_Sigma_Assignment_Nguyen_Duc_Long_Luminance_value_FINAL_v12.pptx` (29 slides)

---

## 🧭 LỜI DẪN MỞ ĐẦU KHI TRÌNH BÀY VỚI SẾP
> *"Kính thưa Sếp và Hội đồng thẩm định Six Sigma,*  
> *Dự án của em giải quyết một bài toán vô cùng nhức nhối trên chuyền FA Line IVI 5: Tỷ lệ lỗi độ sáng (Luminance NG) trên màn hình Porsche CID J1 Dual lên tới 226,624 ppm (chiếm 87.2% toàn bộ lỗi nhà máy). Điều đặc biệt nguy hiểm là các màn hình này khi gửi trả lại nhà cung cấp HEESUNG để scrap thì đo lại đều PASS 100%!*  
> *Bằng phương pháp luận DMAIC chặt chẽ, dự án đã chứng minh được: **Đây là một lỗi máy đo ảo (Measurement Illusion)** do góc đặt camera CS-2000 bị trôi lệch 1 độ kết hợp với đặc tính màng lọc phân cực quang học (LCF film) của màn hình bảo mật Privacy. Sau khi hiệu chỉnh góc 90.0° và thiết lập hệ thống kiểm soát Master sample, năng lực quy trình **Cpk đã tăng vọt từ 0.45 lên 2.39**, tỷ lệ lỗi đưa về **0 ppm (0 NG / 420 set)**, tiết kiệm trực tiếp chi phí phế phẩm và giải phóng hoàn toàn điểm nghẽn dây chuyền."*

---

## 📑 CHI TIẾT TỪNG TRANG SLIDE (SLIDE 01 ~ SLIDE 29)

---

### 🟦 GIAI ĐOẠN DEFINE (ĐỊNH NGHĨA VẤN ĐỀ)

#### SLIDE 01: TRANG TIÊU ĐỀ (COVER PAGE)
* **Tiêu đề:** Luminance value NG of Porsche CID J1 Dual – 6 Sigma GB Assignment
* **Mục đích:** Xác lập nhận diện đề tài, chủ nhiệm đề tài (Nguyễn Đức Long) và đối tượng nghiên cứu (Cụm màn hình đôi Porsche J1 Dual).
* **Bản chất vấn đề:** Màn hình Porsche J1 Dual là cụm hiển thị đôi cao cấp (gồm màn hình chính CID và màn hình phụ cho hành khách PID). Trạm kiểm tra chức năng liên tục báo lỗi độ sáng dưới ngưỡng tiêu chuẩn khách hàng.
* **Kết luận cần nói với Sếp:**  
  > *"Em xin báo cáo đề tài giải quyết lỗi độ chói Luminance trên model cao cấp Porsche J1 Dual, nhằm triệt tiêu điểm nghẽn lớn nhất tại chuyền FA."*

---

#### SLIDE 02: SIX SIGMA PROJECT REGISTER (PHIẾU ĐĂNG KÝ DỰ ÁN)
* **Tiêu đề:** Six Sigma Project Register
* **Mục đích:** Thiết lập bản hợp đồng cam kết chất lượng giữa Nhóm thực hiện và Ban Giám đốc về mục tiêu, tiến độ, nhân lực và lợi ích kinh tế.
* **Bản chất vấn đề:**
  * **Chỉ số KPI:** Tỷ lệ lỗi 226,624 ppm → Mục tiêu Stretch Goal đưa về 0 ppm.
  * **Project Y:** Độ sáng (Luminance, spec 800–2000 cd/m²). Năng lực trước cải tiến **Cpk = 0.45 (Z = 1.35)** → Mục tiêu **Cpk ≥ 1.33 (Z = 4.5)**. *(Toàn bộ đã đồng bộ chuẩn Cpk theo tiêu chuẩn GB)*.
  * **Lợi ích tài chính:** Đơn giá 1 màn hình LCD = \$118.72. Riêng tháng 3/2026 đã loại oan 19 màn hình, gây tổn thất scrap = 19 × \$118.72 = **\$2,255.68/tháng**.
* **Kết luận cần nói với Sếp:**  
  > *"Dự án cam kết nâng năng lực Cpk từ 0.45 lên trên 1.33, đưa tỷ lệ lỗi về 0 ppm, bảo vệ trực tiếp hơn \$2,200/tháng chi phí linh kiện không bị vứt bỏ oan uổng."*

---

#### SLIDE 03: 1.1 Y-Y BREAKDOWN (PHÂN RÃ CHỈ SỐ Y)
* **Tiêu đề:** 1.1 Y-y breakdown
* **Mục đích:** Dùng kỹ thuật phễu lọc (Funneling) để bóc tách Big Y thành các Little y, khoanh vùng chính xác ổ lỗi phát sinh từ đâu.
* **Bản chất phân tích:**
  * Tổng lỗi cụm Porsche CID là **260,000 PPM** (164 NG / 631 EA giai đoạn Nov.2025 ~ Mar.2026).
  * Phân rã cấp 1: Lỗi phần cứng (HW) chỉ chiếm 6.0% (15,600 PPM); Lỗi phần mềm (SW) chỉ chiếm 3.5% (9,100 PPM). Trong khi **Lỗi trạm kiểm tra (Machine defect) chiếm tới 90.5% (235,300 PPM)**!
  * Phân rã cấp 2 trong Machine defect: Lỗi Haptic/Touch chỉ 1.0% (2,600 PPM), còn lại **Lỗi chức năng độ sáng chiếm tới 89.5% (232,700 PPM)**.
  * Phân rã cấp 3: Trong chức năng độ sáng, lỗi Contrast (tương phản) chỉ 2.3% (6,076 PPM - lỗi vật liệu thật do vendor), còn **Lỗi giá trị Luminance chiếm áp đảo 87.2% (226,624 PPM)**!
* **Kết luận cần nói với Sếp:**  
  > *"Dữ liệu bóc tách chứng minh: Vấn đề không nằm ở lắp ráp cơ khí hay code phần mềm, mà 87.2% lỗi của cả nhà máy tập trung duy nhất vào chỉ số độ sáng Luminance tại máy đo Function. Đây chính là Project Y bắt buộc phải chọn."*

---

#### SLIDE 04: 1.2 PARETO (BIỂU ĐỒ PARETO)
* **Tiêu đề:** 1.2 Pareto
* **Mục đích:** Ứng dụng quy luật 80/20 chứng minh yếu tố sống còn (Vital Few) cần ưu tiên nguồn lực giải quyết.
* **Bản chất phân tích:**
  * Cột Luminance value sừng sững chiếm 226,624 ppm, tương đương 87.2% tổng số lỗi (vượt ngưỡng 80%).
  * 4 hạng mục lỗi còn lại (HW, SW, Contrast, Haptic) cộng dồn chỉ chiếm 12.8%.
* **Kết luận cần nói với Sếp:**  
  > *"Biểu đồ Pareto khẳng định theo nguyên lý 80/20: Chỉ cần triệt tiêu được lỗi Luminance, chúng ta sẽ giải quyết được gần 90% lỗi của toàn bộ model Porsche J1."*

---

#### SLIDE 05: 1.3 DEFINE PROJECT Y (ĐỊNH NGHĨA DỰ ÁN & QUANG HỌC)
* **Tiêu đề:** 1.3 Define Project Y
* **Mục đích:** Làm rõ bản chất vật lý của thông số đo độ chói (Luminance) và cơ chế phát hiện lỗi.
* **Bản chất kỹ thuật:**
  * Độ chói $L = \frac{d^2\Phi}{dA \cdot d\omega \cdot \cos\theta}$ (đơn vị: cd/m² hay nit). Trong đó $\theta$ là góc giữa pháp tuyến bề mặt màn hình và trục nhìn của cảm biến quang học. Ở điều kiện lý tưởng, $\theta = 0^\circ$ ($\cos 0^\circ = 1$).
  * Tiêu chuẩn spec: **800.00 ~ 2000.00 cd/m²**.
  * Hiện tượng lỗi: Giá trị đo trên màn hình phụ PID bị tụt xuống dưới ngưỡng 800 cd/m², khiến phần mềm Moohantech đánh trượt NG.
* **Kết luận cần nói với Sếp:**  
  > *"Về mặt vật lý, độ sáng phụ thuộc trực tiếp vào góc đặt cảm biến theo hàm $\cos\theta$. Màn hình không hề tối đi, mà máy đo đang ghi nhận mức sáng dưới cận chuẩn 800 cd/m²."*

---

### 🟩 GIAI ĐOẠN MEASURE (ĐO LƯỜNG & ĐÁNH GIÁ HỆ THỐNG ĐO)

#### SLIDE 06: PREPARATION OF GAGE R&R (CHUẨN BỊ MSA)
* **Tiêu đề:** 1 Preparation of Gage R&R
* **Mục đích:** Giới thiệu thiết bị đo và kế hoạch kiểm định tính toàn vẹn của hệ thống đo (Measurement System Analysis - MSA).
* **Bản chất kỹ thuật:**
  * Thiết bị: Máy đo quang phổ đa góc Konica Minolta CS-2000, độ phân giải cực cao 0.01 cd/m².
  * Vì trạm đo được điều khiển bằng cánh tay Robot gắp và camera quét hoàn toàn tự động (không có con người thao tác trực tiếp), nên chuẩn Six Sigma yêu cầu áp dụng **Type 1 Gage Study** (đánh giá độ lệch Bias & độ chụm) và **Type 3 Gage Study** (đánh giá độ lặp lại Repeatability của thiết bị tự động không có Operator).
* **Kết luận cần nói với Sếp:**  
  > *"Trước khi tìm lỗi sản phẩm, nguyên tắc Six Sigma bắt buộc phải chứng minh thiết bị đo có chuẩn hay không. Vì đây là trạm tự động nên em sử dụng Type 1 và Type 3 để đánh giá khách quan độ tin cậy của máy đo CS-2000."*

---

#### SLIDE 07: 2.1 TYPE 1 STUDY (ĐÁNH GIÁ THIẾT BỊ TRƯỚC CẢI TIẾN)
* **Tiêu đề:** 2.1 Type 1 Study
* **Mục đích:** Đo 30 lần liên tục trên 1 mẫu chuẩn Master (Reference value = 910.00 cd/m²) để kiểm tra độ chệch (Bias) và độ lặp lại (Repeatability).
* **Bản chất thống kê:**
  * Giá trị trung bình đo được chỉ là **854.96 cd/m²** → Bị lệch âm nghiêm trọng: **Bias = -55.04 cd/m²**!
  * Kiểm định t-test 1 mẫu: P-value < 0.001 (Bác bỏ giả thuyết Bias = 0).
  * Chỉ số năng lực đo: **Cg = 0.91** (< 1.33 FAIL), **Cgk = 0.49** (< 1.33 FAIL).
  * Độ biến thiên lặp lại: %Var(Repeatability) = 21.99% (> 10% FAIL), %Var(R & Bias) = 40.63% (> 10% FAIL).
* **Kết luận cần nói với Sếp:**  
  > *"Kết quả Type 1 báo động đỏ: Máy đo đang bị lệch âm tới 55 cd/m²! Một sản phẩm thực tế sáng 910 cd/m² nhưng khi đưa vào máy lại chỉ đo ra 855 cd/m², đẩy sản phẩm sát vách lỗi 800 cd/m². Máy đo không đủ năng lực đo lường."*

---

#### SLIDE 08: 2.2 TYPE 3 STUDY (ĐỘ LẶP LẠI TRẠM TỰ ĐỘNG TRƯỚC CẢI TIẾN)
* **Tiêu đề:** 2.2 Type 3 Study
* **Mục đích:** Sử dụng 25 mẫu sản phẩm khác nhau, mỗi mẫu đo lặp lại 2 lần để đánh giá trạm đo có phân biệt được các sản phẩm hay không.
* **Bản chất thống kê:**
  * %Contribution của Gage R&R = **71.56%** (> 9% NG nghiêm trọng).
  * %Study Var = **84.59%** (> 10% NG).
  * Số phân nhóm phân biệt: **NDC = 1** (< 5 NG).
* **Kết luận cần nói với Sếp:**  
  > *"Chỉ số NDC = 1 có nghĩa là hệ thống đo hoàn toàn 'mù': Sai số bản thân máy đo quá lớn (chiếm 71.5% biến thiên), khiến máy không thể phân biệt được đâu là sản phẩm tốt, đâu là sản phẩm xấu. Bắt buộc phải đại tu trạm kiểm tra!"*

---

#### SLIDE 09: 2.3 XBAR-R CHART REVIEW (BASELINE / TRƯỚC CẢI TIẾN) – *SLIDE MỚI BỔ SUNG CHUẨN MỰC*
* **Tiêu đề:** 2.3 Xbar-R Chart Review
* **Mục đích:** Khảo sát độ ổn định thống kê của quy trình sản xuất ban đầu thông qua kỹ thuật lấy mẫu phân nhóm hợp lý (Rational Subgroup Sampling: 10 ngày x 5 mẫu/ngày = 50 mẫu tại chuyền FA).
* **Bản chất thống kê & Đồ thị Xbar-R:**
  * Biểu đồ $\bar{X}$ và biểu đồ $R$ đều nằm trong các đường giới hạn kiểm soát (UCL = 846.62, LCL = 805.88; UCL_R = 74.62). Không có điểm vi phạm quy tắc run chart → Quy trình đang **Ổn định thống kê (In Statistical Control)**.
  * Tuy nhiên, đường tâm trung bình $\bar{\bar{X}} = 826.25 \text{ cd/m}^2$ bị lệch quá sát cận dưới LSL = 800 cd/m². Có tới 14% số mẫu thực tế (7/50 mẫu) rớt xuống dưới 800 cd/m².
* **Kết luận cần nói với Sếp:**  
  > *"Thưa Sếp, biểu đồ Xbar-R cho thấy dây chuyền hoạt động rất ổn định qua 10 ngày (không có biến động bất thường). Tuy nhiên quy trình **Ổn định nhưng Không đạt năng lực (Stable but Not Capable)**, vì toàn bộ phổ độ sáng bị 'kéo ghì' xuống sát cận dưới LSL = 800 cd/m², sinh ra tỷ lệ lỗi 226,624 ppm!"*

---

#### SLIDE 10: 2.4 RESULT OF CURRENT CPK (NĂNG LỰC QUY TRÌNH BAN ĐẦU)
* **Tiêu đề:** 2.4 Result of current Cpk
* **Mục đích:** Lượng hóa năng lực quy trình ban đầu (Cpk) và thiết lập mục tiêu cải tiến (Stretch Goal). *(Đã chuyển đổi hoàn toàn sang Cpk chuẩn)*.
* **Bản chất thống kê:**
  * Phân bố dữ liệu lệch chuẩn (P-value < 0.005).
  * **Cpk hiện tại = 0.45 < 1.33 (NG)**, tương đương mức Sigma **Z = 1.35**.
  * Mục tiêu cải tiến: Dịch chuyển tâm trung bình từ 826 cd/m² lên 910 cd/m² để đưa **Cpk ≥ 1.33 (Z = 4.5)**, triệt tiêu tỷ lệ lỗi 226,624 ppm về 0 ppm.
* **Kết luận cần nói với Sếp:**  
  > *"Với Cpk = 0.45, cứ 1 triệu sản phẩm sản xuất ra thì có tới hơn 226,000 sản phẩm bị rớt ra ngoài biên dưới. Mục tiêu của chúng ta là đưa Cpk vượt ngưỡng 1.33 để xóa sạch lỗi."*

---

### 🟨 GIAI ĐOẠN ANALYZE (PHÂN TÍCH NGUYÊN NHÂN GỐC)

#### SLIDE 11: 3.1 ROOT CAUSE LOGIC TREE (CÂY LOGIC TÌM NGUYÊN NHÂN)
* **Tiêu đề:** 3.1 Root cause of measurement system problem
* **Mục đích:** Sử dụng cây logic (Logic Tree) kết hợp 5M để phân tích loại trừ và khoanh vùng các nghi phạm gây lỗi tại trạm đo.
* **Bản chất loại trừ:**
  * **Man (Con người):** Quy trình tự động 100% bằng Robot → Không liên quan.
  * **Material (Vật liệu):** Màn hình LCD gửi trả nhà cung cấp HEESUNG test lại trên máy chuẩn của họ đều đạt 100% OK → Khẳng định LCD không bị lỗi!
  * **Method (Phương pháp):** Trình tự test và đồ gá dùng chung cho các model khác không bị lỗi → Loại trừ.
  * **Machine (Thiết bị):** Nguồn điện và Pallet bình thường. Cô lập 3 yếu tố nghi vấn:
    1. Hộp CANSIM phát tín hiệu yếu.
    2. Thân máy Camera CS2000 bị sai hỏng cảm biến.
    3. Góc đặt Camera (Camera Angle) bị trôi lệch.
* **Kết luận cần nói với Sếp:**  
  > *"Em đã chứng minh được linh kiện của nhà cung cấp HEESUNG hoàn toàn vô tội. Toàn bộ vấn đề nằm ở trạm kiểm tra và em đã cô lập được 3 nguyên nhân tiềm năng nhất: CANSIM, Thân máy đo, và Góc đặt Camera."*

---

#### SLIDE 12: 3.1 IDENTIFICATION PLAN: 2-SAMPLE T TEST (KẾ HOẠCH XÁC THỰC)
* **Tiêu đề:** 3.1 Root cause of measurement system problem (2 Samples T)
* **Mục đích:** Thiết lập ma trận thử nghiệm thống kê 2-Sample T-test để kiểm chứng từng yếu tố nghi vấn một cách khoa học.
* **Kết luận cần nói với Sếp:**  
  > *"Để không đoán mò, em tiến hành kiểm định thống kê 2-Sample T-test với mức ý nghĩa $\alpha = 0.05$ cho từng yếu tố."*

---

#### SLIDE 13: 2-SAMPLE T: KHẢO SÁT HỘP PHÁT TÍN HIỆU CANSIM
* **Tiêu đề:** Detection Luminance from CANSIM – Change to new CANSIM
* **Mục đích:** Kiểm tra việc thay thế hộp CANSIM mới có làm tăng độ sáng hay không.
* **Bản chất thống kê:**
  * Giả thuyết: $H_0$: Đổi CANSIM không ảnh hưởng đến độ sáng.
  * Kết quả: **P-value = 0.695 > 0.05** → Chấp nhận $H_0$.
* **Kết luận cần nói với Sếp:**  
  > *"P-value = 0.695 chứng minh hộp CANSIM hoàn toàn bình thường, không phải là nguyên nhân gốc."*

---

#### SLIDE 14: 2-SAMPLE T: KHẢO SÁT THAY THẾ CAMERA CS2000 MỚI
* **Tiêu đề:** Detection Luminance from Camera – Change to new camera
* **Mục đích:** Kiểm tra việc thay một thân máy ảnh CS-2000 mới tinh (đã hiệu chuẩn từ hãng) có khắc phục được lỗi hay không.
* **Bản chất thống kê:**
  * Giả thuyết: $H_0$: Đổi thân máy camera không ảnh hưởng đến độ sáng.
  * Kết quả: **P-value = 0.950 > 0.05** → Chấp nhận $H_0$.
* **Kết luận cần nói với Sếp:**  
  > *"P-value = 0.950 khẳng định thân máy CS2000 đang dùng không bị hỏng cảm biến quang học. Tránh được việc mua máy mới gây lãng phí hàng chục nghìn đô la!"*

---

#### SLIDE 15: 2-SAMPLE T: KHẢO SÁT GÓC ĐẶT CAMERA (CAMERA ANGLE) ⭐
* **Tiêu đề:** Detection Luminance from Camera – Change to the angle of Camera
* **Mục đích:** Kiểm tra việc hiệu chỉnh góc vuông của trục camera về chuẩn 90.0° so với bề mặt màn hình.
* **Bản chất thống kê & Đột phá kỹ thuật:**
  * Giả thuyết: $H_0$: Đổi góc camera không ảnh hưởng đến độ sáng.
  * Kết quả: **P-value < 0.001 < 0.05** → **BÁC BỎ $H_0$!**
  * Giá trị trung bình độ sáng sau khi chỉnh góc tăng vọt ngay lập tức **+48.99 cd/m²** (từ 855 lên 909.5 cd/m²), khoảng tin cậy 95% nằm từ 32.93 đến 65.05 cd/m²!
* **Kết luận cần nói với Sếp:**  
  > *"P < 0.001 đã vén bức màn bí mật: **NGUYÊN NHÂN GỐC 100% LÀ DO GÓC NGHIÊNG CAMERA!** Khi camera bị nghiêng chỉ 1 độ, máy đo bị sụt mất gần 50 cd/m². Khi chỉnh về 90 độ thẳng đứng, độ sáng lập tức nhảy về đúng giá trị chuẩn 910 cd/m²!"*

---

#### SLIDE 16: SUMMARY TABLE (BẢNG TỔNG HỢP NGUYÊN NHÂN GỐC)
* **Tiêu đề:** Summary: 2 Samples T test of Potential Factors
* **Mục đích:** Báo cáo tổng hợp kết quả 3 thí nghiệm trên 1 slide cô đọng.
* **Kết luận cần nói với Sếp:**  
  > *"Bảng đối chiếu khẳng định: CANSIM và Thân máy đo là các yếu tố nhiễu vô can. Yếu tố duy nhất điều khiển chất lượng là Góc nghiêng Camera CS-2000."*

---

### 🟧 GIAI ĐOẠN IMPROVE (CẢI TIẾN & XÁC THỰC)

#### SLIDE 17: 5-WHY ANALYSIS & ACTION PLAN (5 TẠI SAO & KẾ HOẠCH)
* **Tiêu đề:** Root Cause: 5-Why Analysis & Improvement Plan
* **Mục đích:** Đi sâu vào căn nguyên cơ khí để tìm ra giải pháp phòng ngừa vĩnh viễn (Fix process, not just fix symptom).
* **Bản chất 5-Why:**
  1. *Tại sao độ sáng đo dưới 800?* → Vì camera không vuông góc 90°.
  2. *Tại sao camera không vuông góc?* → Vì góc bị trôi lệch sau thời gian dài vận hành.
  3. *Tại sao bị trôi lệch?* → Vì màn hình đôi (PID/CID) yêu cầu Robot di chuyển liên tục giữa 2 vị trí, rung chấn cơ học làm lỏng đồ gá kẹp camera.
  4. *Tại sao không phát hiện sớm?* → Vì đầu ca không có quy trình dùng Master sample để kiểm tra góc đặt.
* **Kết luận cần nói với Sếp:**  
  > *"5-Why chỉ ra: Rung lắc chuyển động robot đã làm lỏng đồ gá camera. Giải pháp của chúng ta gồm 2 bước: Bước 1 là cân chỉnh góc và dạy lại Robot (Teaching Robot); Bước 2 là ban hành Checksheet kiểm tra Master Sample đầu mỗi ca."*

---

#### SLIDE 18: 4.1 SHORT-TERM IMPROVEMENT (CÂN CHỈNH GÓC CAMERA)
* **Tiêu đề:** 4.1 Correct the camera angle (before / after)
* **Mục đích:** Hiển thị kết quả cân chỉnh góc cơ khí thực tế trên đồ gá.
* **Bản chất kỹ thuật:**
  * Trước cải tiến: Góc mặt phẳng XZ = 89.075°, YZ = 88.806° (lệch ~1.2°).
  * Sau cải tiến: Góc mặt phẳng **XZ = 89.889°, YZ = 89.889°** (chuẩn vuông góc 90.0°).
  * Kiểm tra thực tế: Khi chạy lại trên 420 bộ sản phẩm: **0 NG / 420 sets!**
* **Kết luận cần nói với Sếp:**  
  > *"Sau khi đưa góc máy về 90 độ, trạm đo chạy trơn tru 420 bộ liên tục không còn một lỗi NG nào!"*

---

#### SLIDE 19: 4.1 ROBOT TEACHING & VỊ TRÍ SERVO (ĐỒNG TÂM MÀN HÌNH)
* **Tiêu đề:** 4.1 Correct the camera angle: camera position and servo position
* **Mục đích:** Đảm bảo camera ngắm trúng hồng tâm phát sáng của cả 2 màn hình cho cả 2 phiên bản xe tay lái thuận (LHD) và tay lái nghịch (RHD).
* **Bản chất kỹ thuật:**
  * Tọa độ servo 48 và 49 được căn chỉnh chính xác vào tâm quang học của màn hình PID và CID.
* **Kết luận cần nói với Sếp:**  
  > *"Robot đã được dạy lại tọa độ servo chuẩn xác, đảm bảo trục nhìn camera luôn chiếu thẳng vào tâm màn hình dù là phiên bản xe LHD hay RHD."*

---

#### SLIDE 20: 4.2 LUMINANCE COMPENSATION FOR PRIVACY MODELS (BẢN CHẤT QUANG HỌC LCF) ⭐
* **Tiêu đề:** 4.2 Luminance compensation for Privacy models
* **Mục đích:** Giải thích bản chất vật lý quang học sâu sắc nhất của toàn bộ dự án: Tại sao góc 89° lại "giết chết" độ sáng của dòng Porsche J1 Dual?
* **Bản chất vật lý quang học cực kỳ quan trọng:**
  * Chuyền IVI 5 chạy 13 dòng xe (Bentley, Macan, 992, v.v.). Các dòng này dùng màn hình **Public view** thông thường, góc nhìn rộng, nên khi camera nghiêng 1°, độ sáng chỉ giảm < 0.5% (không ảnh hưởng).
  * Riêng model **Porsche J1 Dual và E3PA Dual** trang bị tính năng **Màn hình bảo mật Privacy (PID)**: Bên trong lớp đèn nền BLU có tích hợp một tấm phim vi trập gọi là **LCF (Light Control Film / Louver Film)**.
  * Tấm phim LCF này chỉ cho ánh sáng đi theo phương thẳng đứng 90° để hành khách ngồi bên cạnh xem được mà tài xế không bị lóa mắt phân tâm khi lái xe.
  * **Hệ quả vật lý:** Đặc tính góc nhìn của phim LCF cực kỳ hẹp và dốc! Chỉ cần camera nghiêng lệch đúng 1° (89°), lượng quang thông lọt qua khe vi trập bị sụt giảm tới **13%**!
* **Kết luận cần nói với Sếp:**  
  > *"Thưa Sếp, đây là chìa khóa then chốt của bài toán: Màn hình Porsche J1 có tấm phim bảo mật LCF bên trong. Khi camera nghiêng 1 độ, ánh sáng bị chặn lại làm sụt 13% độ sáng! Vì vậy, với các dòng Privacy, ngoài việc chỉnh góc 90°, chúng em cài đặt thêm hệ số bù sáng 13% trên phần mềm đo."*

---

#### SLIDE 21: 4.3 LONG-TERM IMPROVEMENT (BAN HÀNH CHECKSHEET MASTER SAMPLE)
* **Tiêu đề:** 4.3 Add Master sample check sheet to control the camera angle
* **Mục đích:** Thiết lập cơ chế kiểm soát phòng ngừa dài hạn (Poka-Yoke) để ngăn chặn góc máy bị trôi lệch trong tương lai.
* **Bản chất quy trình:**
  * Ban hành bảng kiểm tra DID Check Sheet hàng ngày.
  * Đầu mỗi ca sản xuất (08:00 ca ngày và 20:00 ca đêm), kỹ thuật viên bắt buộc phải lấy mẫu Master Sample (chuẩn 910 cd/m²) đo kiểm tra trước. Nếu giá trị nằm ngoài dải $910 \pm 48 \text{ cd/m}^2$, dừng chuyền để chỉnh lại góc ngay lập tức.
* **Kết luận cần nói với Sếp:**  
  > *"Chúng em không dừng lại ở việc sửa góc, mà đã thể chế hóa thành bảng kiểm tra Master Sample đầu mỗi ca, đảm bảo góc đo không bao giờ bị trôi lệch trở lại."*

---

#### SLIDE 22: 4.4 TYPE 1 STUDY AGAIN (KIỂM ĐỊNH LẠI THIẾT BỊ SAU CẢI TIẾN)
* **Tiêu đề:** 4.4 Type 1 Study again after improvement
* **Mục đích:** Thực hiện lại Type 1 Gage Study trên mẫu Master 910 cd/m² (30 lần đo) để nghiệm thu hệ thống đo sau cải tiến.
* **Bản chất thống kê:**
  * Giá trị trung bình đạt **909.73 cd/m²** → **Bias chỉ còn -0.27 cd/m²** (Coi như triệt tiêu hoàn toàn sai số lệch tâm!).
  * P-value = 0.926 (> 0.05, không còn sai lệch thống kê).
  * **Cg = 2.51** (trước là 0.91), **Cgk = 2.50** (trước là 0.49), vượt xa tiêu chuẩn ≥ 1.33!
  * %Var(Repeatability) = **7.98%** (< 10% PASS xuất sắc).
* **Kết luận cần nói với Sếp:**  
  > *"Sau cải tiến, máy đo đạt độ chính xác gần như tuyệt đối: Độ chệch Bias chỉ còn 0.27 cd/m², năng lực Cg/Cgk tăng từ 0.49 lên 2.50. Thiết bị đo đã hoàn toàn đạt chuẩn quốc tế!"*

---

#### SLIDE 23: 4.4 TYPE 3 STUDY AGAIN (KIỂM ĐỊNH LẠI TRẠM TỰ ĐỘNG SAU CẢI TIẾN)
* **Tiêu đề:** 4.4 Type 3 Study again after improvement
* **Mục đích:** Đo lại 25 mẫu sản phẩm x 2 lần lặp để nghiệm thu trạm đo tự động.
* **Bản chất thống kê:**
  * %Contribution của Gage R&R giảm từ 71.56% xuống chỉ còn **0.22%** (< 1% World Class!).
  * %Study Var giảm từ 84.59% xuống còn **4.64%** (< 10% PASS).
  * Số phân nhóm phân biệt: **NDC tăng từ 1 lên 30** (vượt xa chuẩn ≥ 5).
* **Kết luận cần nói với Sếp:**  
  > *"Chỉ số NDC tăng vọt từ 1 lên 30, sai số máy đo chỉ còn 0.22%. Trạm đo tự động hiện tại có khả năng phân biệt chi tiết tới 30 cấp độ biến thiên của sản phẩm!"*

---

#### SLIDE 24: 4.5 PROCESS CAPABILITY REVIEW AFTER (NĂNG LỰC QUY TRÌNH SAU CẢI TIẾN)
* **Tiêu đề:** 4.5 Process Capability review
* **Mục đích:** Đánh giá năng lực quy trình sản xuất (Cpk) sau khi hệ thống đo được hiệu chỉnh. *(Đã chuyển đổi hoàn toàn sang Cpk chuẩn)*.
* **Bản chất thống kê:**
  * Dữ liệu tuân theo phân bố chuẩn: P-value = 0.503 (> 0.05 PASS).
  * **Cpk đạt tới 2.39** (vượt xa mục tiêu cam kết Cpk ≥ 1.33!).
  * So sánh: **Trước cải tiến Cpk = 0.45 → Sau cải tiến Cpk = 2.39** (Tăng gấp 5.3 lần!).
* **Kết luận cần nói với Sếp:**  
  > *"Cpk đạt 2.39 khẳng định toàn bộ phổ sản phẩm nằm gọn gàng ở tâm tiêu chuẩn, cách rất xa ranh giới lỗi 800 cd/m². Không còn bất kỳ sản phẩm nào có nguy cơ bị lỗi!"*

---

#### SLIDE 25: 4.5 PROCESS CAPABILITY (Z VALUE)
* **Tiêu đề:** 4.5 Process Capability review (Z value)
* **Mục đích:** Đánh giá độ dịch chuyển Z-shift và đẳng cấp công nghệ Six Sigma.
* **Bản chất thống kê:**
  * Mức Sigma ngắn hạn: $Z_{ST} = 7.18 \geq 4.5$.
  * Mức Sigma dài hạn: $Z_{LT} = 6.89 \geq 4.5$.
  * $Z_{shift} = 0.29 < 1.5$ → Quy trình kiểm soát cực kỳ ổn định, công nghệ đạt chuẩn hoàn hảo (Technology is OK).
* **Kết luận cần nói với Sếp:**  
  > *"Mức Sigma Z > 6 khẳng định quy trình đã đạt đẳng cấp công nghệ Six Sigma đẳng cấp thế giới."*

---

#### SLIDE 26: 4.6 CONCLUSION (TỔNG KẾT GIAI ĐOẠN CẢI TIẾN)
* **Tiêu đề:** 4.6 Conclusion
* **Mục đích:** Đóng gói toàn bộ thành quả giai đoạn Improve trên 1 trang báo cáo cô đọng.
* **Kết luận cần nói với Sếp:**  
  > *"Chúng ta đã đi đúng đường: Sửa đúng nguyên nhân gốc góc camera 89° → Thiết bị đo chuẩn hóa (Cg=2.50) → Năng lực quy trình đạt Cpk=2.39 → Lỗi đưa về 0 ppm trên 420 sản phẩm thực tế."*

---

### 🟥 GIAI ĐOẠN CONTROL (KIỂM SOÁT BỀN VỮNG & KẾT QUẢ DỰ ÁN)

#### SLIDE 27: 5.1 XBAR-R CHART REVIEW AFTER IMPROVEMENT (THEO DÕI DÀI HẠN)
* **Tiêu đề:** 5.1 Xbar-R Chart Review after improvement
* **Mục đích:** Theo dõi độ ổn định dài hạn sau cải tiến bằng Rational Subgroups (10 ngày x 5 mẫu = 50 mẫu, từ 1-Jul đến 10-Jul-2026).
* **Bản chất biểu đồ:**
  * Biểu đồ $\bar{X}$ và $R$ duy trì ổn định tuyệt đối quanh trục trung bình 910 cd/m², không có điểm out-of-control, không có xu hướng trôi dạt.
* **Kết luận cần nói với Sếp:**  
  > *"Biểu đồ Xbar-R sau cải tiến chứng minh: Quy trình duy trì ổn định bền vững theo thời gian thực tế, không hề có hiện tượng tái phát lỗi."*

---

#### SLIDE 28: 5.2 FUTURE MANAGEMENT PLAN (KẾ HOẠCH QUẢN LÝ TƯƠNG LAI)
* **Tiêu đề:** 5.2 Future plan (Management plan)
* **Mục đích:** Tiêu chuẩn hóa vào hệ thống SOP và mở rộng áp dụng (Horizontal Deployment).
* **Bản chất kế hoạch:**
  1. Đưa mục kiểm tra góc 90.0° vào quy trình thiết lập máy tiêu chuẩn (SOP).
  2. Duy trì kiểm tra Master Sample 2 lần/ngày tại đầu mỗi ca làm việc.
  3. **Mở rộng hàng ngang (Horizontal Deployment):** Áp dụng ngay giải pháp kiểm tra góc và hệ số bù sáng 13% cho các dòng màn hình đôi có tính năng bảo mật Privacy khác trên chuyền như Audi E3PA Dual, Porsche G3 Dual.
* **Kết luận cần nói với Sếp:**  
  > *"Dự án đã tiêu chuẩn hóa thành SOP và sẵn sàng mở rộng áp dụng hàng ngang cho các dự án màn hình bảo mật Privacy khác của tập đoàn."*

---

#### SLIDE 29: 5.3 RESULT OF PROJECT (TỔNG KẾT KẾT QUẢ DỰ ÁN)
* **Tiêu đề:** 5.3 Result of project
* **Mục đích:** Trình bày bức tranh Before/After toàn diện về kỹ thuật, chất lượng và tài chính.
* **Bảng so sánh tổng kết:**
  * **Tỷ lệ lỗi (Defect Rate):** Từ **226,624 ppm → 0 ppm** (0 NG / 420 bộ sau cải tiến).
  * **Năng lực quy trình (Cpk):** Từ **0.45 → 2.39** (Tăng 530%).
  * **Kiểm định Fisher's Exact Test:** P-value < 0.001 (Khẳng định sự cải thiện là có thật 100%, không phải may mắn ngẫu nhiên).
  * **Hiệu quả tài chính:** Tiết kiệm trực tiếp **\$2,255.68/tháng** chi phí màn hình bị scrap oan, đồng thời giải phóng hoàn toàn thời gian retest nghẽn dây chuyền FA.
* **Kết luận chốt hạ với Sếp:**  
  > *"Kính thưa Sếp, dự án 6 Sigma Green Belt của em đã hoàn thành 100% mục tiêu: Đưa lỗi về 0 ppm, Cpk đạt 2.39, giải quyết triệt để bài toán kỹ thuật hóc búa của dòng Porsche J1 Dual và tiết kiệm chi phí cụ thể cho công ty. Em xin trân trọng cảm ơn Sếp và kính mong Sếp phê duyệt nghiệm thu dự án!"*

---

## 🏆 TÓM TẮT CÁC CẢI TIẾN TRỌNG TÂM ĐÃ THỰC HIỆN TRÊN FILE V12:
1. **Đổi toàn bộ Ppk sang Cpk:**
   * Slide 2 (Project Register): `Cpk = 0.45, Z = 1.35` → Mục tiêu `Cpk ≥ 1.33, Z = 4.5`.
   * Slide 10 (Current Cpk): `Cpk = 0.45 < 1.33 → NG`.
   * Slide 24 (Cpk After): `Before Cpk = 0.45` → `After Cpk = 2.39`.
2. **Bổ sung Slide 9 mới chuẩn theo mẫu Hoang Anh & Hoang Xuan Huong:**
   * Slide 9: `2.3 Xbar-R Chart Review` với bảng dữ liệu 10 ngày x 5 mẫu baseline tại chuyền FA và biểu đồ Minitab Xbar-R chart chứng minh quy trình ổn định nhưng không đạt năng lực.
   * Slide 10: `2.4 Result of current Cpk` kế thừa và phân tích Cpk ban đầu.
3. **Xóa bỏ hoàn toàn "LGE Internal Use Only":**
   * Đã bóc tách và xóa sạch shape `TextBox 3` chứa watermark trong Slide Master XML (`slideMaster1.xml`) và `custom.xml`.
4. **Đồng bộ hóa đánh số slide:**
   * Cập nhật toàn bộ các slide từ Slide 1 đến Slide 29 thành định dạng `XX / 29` chuẩn xác 100%.

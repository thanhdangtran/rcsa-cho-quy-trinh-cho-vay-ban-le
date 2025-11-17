# RCSA: CHO VAY TÍN CHẤP NHÂN VIÊN CÔNG TY
## VPBank - Risk & Control Self-Assessment

---

## 1. THÔNG TIN QUY TRÌNH

**Tên quy trình:** Cho vay tín chấp nhân viên công ty (Payroll Lending)

**Đơn vị sở hữu quy trình:** Khối Bán lẻ (Retail Banking Division)

**Phạm vi áp dụng:** Tất cả chi nhánh VPBank

**Mục tiêu quy trình:**
- Cung cấp tín dụng tiêu dùng cho nhân viên các công ty hợp tác
- Đảm bảo thẩm định nhanh (< 4 giờ) với rủi ro kiểm soát
- Duy trì NPL < 2% cho phân khúc này

---

## 2. SƠ ĐỒ QUY TRÌNH

```
┌─────────────────────────────────────────────────────────────────┐
│                    GIAI ĐOẠN 1: ĐỀ NGHỊ VAY                      │
└─────────────────────────────────────────────────────────────────┘
                              │
                              ▼
                    ┌──────────────────┐
                    │  Khách hàng nộp  │
                    │  hồ sơ qua RM/   │◄──── Input: Giấy tờ tùy thân,
                    │  App/Chi nhánh   │      hợp đồng lao động, sổ lương
                    └──────────────────┘
                              │
                              ▼
                    ┌──────────────────┐
                    │   KYC Check      │
                    │  (eKYC system)   │◄──── Control: AML screening,
                    │                  │      blacklist check
                    └──────────────────┘
                              │
                              ▼
                         Pass/Fail?
                              │
                    ┌─────────┴──────────┐
                    │                    │
                Fail ▼                   ▼ Pass
            [Từ chối ngay]    ┌──────────────────┐
                              │                  │
                              
┌─────────────────────────────────────────────────────────────────┐
│                    GIAI ĐOẠN 2: NHẬP LIỆU                        │
└─────────────────────────────────────────────────────────────────┘
                              │
                              ▼
                    ┌──────────────────┐
                    │  Data Entry      │
                    │  Officer nhập    │◄──── Control: 4-eyes check,
                    │  thông tin vào   │      auto validation rules
                    │  LOS system      │
                    └──────────────────┘
                              │
                              ▼
                    ┌──────────────────┐
                    │  Checker xác     │
                    │  nhận độc lập    │◄──── Control: Maker-Checker
                    │  (4-eyes)        │      segregation
                    └──────────────────┘
                              │
                              ▼
┌─────────────────────────────────────────────────────────────────┐
│                   GIAI ĐOẠN 3: THẨM ĐỊNH                         │
└─────────────────────────────────────────────────────────────────┘
                              │
                              ▼
                    ┌──────────────────┐
                    │  Auto scoring    │
                    │  (Credit Model)  │◄──── Control: MoE model,
                    │  + Rule engine   │      reject if score < cutoff
                    └──────────────────┘
                              │
                              ▼
                    ┌──────────────────┐
                    │  Xác minh công   │
                    │  ty (HR confirm) │◄──── Control: Phone call HR,
                    │                  │      check payroll list
                    └──────────────────┘
                              │
                              ▼
                    ┌──────────────────┐
                    │  Kiểm tra CIC    │
                    │  (Credit Bureau) │◄──── Control: Hard stop if
                    │                  │      overdue > 90 days
                    └──────────────────┘
                              │
                              ▼
                    ┌──────────────────┐
                    │  Credit Officer  │
                    │  đánh giá        │◄──── Control: Checklist đầy đủ,
                    │  (manual review  │      không được skip bước
                    │  nếu cần)        │
                    └──────────────────┘
                              │
                              ▼
┌─────────────────────────────────────────────────────────────────┐
│                   GIAI ĐOẠN 4: PHÊ DUYỆT                         │
└─────────────────────────────────────────────────────────────────┘
                              │
                              ▼
                    ┌──────────────────┐
                    │  Auto approval   │
                    │  (nếu score cao  │◄──── Control: Authority matrix,
                    │  + điều kiện OK) │      auto if < 100M & score > 700
                    └──────────────────┘
                              │
                    ┌─────────┴──────────┐
                    │                    │
              Auto  ▼                    ▼ Manual
        ┌──────────────────┐   ┌──────────────────┐
        │  Tự động chấp    │   │  Team Leader/    │◄── Control: 2nd level
        │  thuận           │   │  Manager phê     │    review, không được
        │                  │   │  duyệt           │    approve own case
        └──────────────────┘   └──────────────────┘
                    │                    │
                    └─────────┬──────────┘
                              ▼
┌─────────────────────────────────────────────────────────────────┐
│                   GIAI ĐOẠN 5: GIẢI NGÂN                         │
└─────────────────────────────────────────────────────────────────┘
                              │
                              ▼
                    ┌──────────────────┐
                    │  Ký hợp đồng     │
                    │  điện tử/giấy    │◄──── Control: eSign với OTP,
                    │                  │      hoặc chữ ký ướt + witness
                    └──────────────────┘
                              │
                              ▼
                    ┌──────────────────┐
                    │  Pre-disbursement│
                    │  check           │◄──── Control: Confirm account
                    │                  │      ownership, fraud check
                    └──────────────────┘
                              │
                              ▼
                    ┌──────────────────┐
                    │  Giải ngân vào   │
                    │  tài khoản KH    │◄──── Control: Same-name account,
                    │                  │      limit per day
                    └──────────────────┘
                              │
                              ▼
┌─────────────────────────────────────────────────────────────────┐
│                   GIAI ĐOẠN 6: THU NỢ                            │
└─────────────────────────────────────────────────────────────────┘
                              │
                              ▼
                    ┌──────────────────┐
                    │  Auto deduction  │
                    │  từ payroll      │◄──── Control: Agreement với HR,
                    │  (nếu có thỏa    │      backup plan nếu không auto
                    │  thuận)          │
                    └──────────────────┘
                              │
                              ▼
                    ┌──────────────────┐
                    │  Collection      │
                    │  monitoring      │◄──── Control: Early warning if
                    │  (nếu không auto)│      DPD > 5, escalation matrix
                    └──────────────────┘
                              │
                              ▼
                    ┌──────────────────┐
                    │  NPL handling    │
                    │  (nếu quá hạn    │◄──── Control: Provisioning theo
                    │  > 90 ngày)      │      SBV, write-off policy
                    └──────────────────┘
```

---

## 3. RỦI RO VÀ CONTROLS - THEO TỪNG GIAI ĐOẠN

### 3.1 GIAI ĐOẠN ĐỀ NGHỊ VAY

| Risk ID | Rủi ro (Risk) | Risk Category | Inherent Risk (L x I) | Control Hiện tại | Control Type (COSO) | Control Effectiveness | Residual Risk (L x I) |
|---------|---------------|---------------|---------------------|------------------|---------------------|---------------------|---------------------|
| R01 | Khách hàng dùng giấy tờ giả để apply | Fraud Risk | High (4x5=20) | - eKYC với AI face matching<br>- Cross-check với database công an<br>- AML screening | Preventive / Detective (Control Activities) | Strong | Low (2x4=8) |
| R02 | Nhân viên tư vấn gian dối về điều kiện sản phẩm | Conduct Risk | Medium (3x4=12) | - Call recording 100%<br>- Mystery shopping<br>- Complaint tracking | Detective / Corrective (Monitoring) | Moderate | Medium (2x3=6) |
| R03 | Apply từ công ty không hợp tác/blacklist | Credit Risk | Medium (3x4=12) | - Danh sách công ty hợp tác approved<br>- Hard stop nếu không trong list | Preventive (Control Activities) | Strong | Low (1x3=3) |

### 3.2 GIAI ĐOẠN NHẬP LIỆU

| Risk ID | Rủi ro (Risk) | Risk Category | Inherent Risk (L x I) | Control Hiện tại | Control Type (COSO) | Control Effectiveness | Residual Risk (L x I) |
|---------|---------------|---------------|---------------------|------------------|---------------------|---------------------|---------------------|
| R04 | Nhập sai thông tin khách hàng (số CMND, thu nhập) | Data Quality Risk | High (5x3=15) | - Maker-Checker (4-eyes)<br>- Auto validation rules<br>- Format check<br>- OCR auto-fill để giảm manual | Preventive / Detective (Control Activities) | Strong | Low (2x2=4) |
| R05 | Data entry officer làm giả thông tin để pass qua thẩm định | Fraud Risk | High (3x5=15) | - Segregation of duties (không được approve own entry)<br>- Random audit log review<br>- Red flag report (sửa nhiều lần, pattern bất thường) | Preventive / Detective (Control Activities + Monitoring) | Moderate | Medium (2x4=8) |
| R06 | Hệ thống LOS down, mất data giữa chừng | Technology Risk | Medium (2x4=8) | - Auto-save mỗi 30s<br>- Backup server<br>- Recovery plan < 4h | Preventive / Corrective (Control Activities) | Strong | Low (1x3=3) |

### 3.3 GIAI ĐOẠN THẨM ĐỊNH

| Risk ID | Rủi ro (Risk) | Risk Category | Inherent Risk (L x I) | Inherent Risk | Control Hiện tại | Control Type (COSO) | Control Effectiveness | Residual Risk (L x I) |
|---------|---------------|---------------|---------------------|---------------|------------------|---------------------|---------------------|---------------------|
| R07 | Credit model sai (bias, overfitting) dẫn đến approve sai khách | Model Risk | High (4x5=20) | - Model validation independent team<br>- Champion-challenger testing<br>- Monitoring PSI, Gini quarterly<br>- Override tracking | Detective / Corrective (Monitoring + Risk Assessment) | Moderate | Medium (3x4=12) |
| R08 | Bỏ qua bước xác minh công ty (không gọi HR) | Process Compliance | High (4x4=16) | - Checklist bắt buộc<br>- System không cho next nếu thiếu bước<br>- Quality audit monthly | Preventive / Detective (Control Activities + Monitoring) | Strong | Low (2x3=6) |
| R09 | Không check CIC hoặc bỏ qua nợ xấu trong CIC | Credit Risk | Very High (5x5=25) | - Hard stop nếu không có CIC report<br>- Auto reject nếu NPL > 90 days<br>- Dual control cho override cases | Preventive (Control Activities) | Strong | Low (2x4=8) |
| R10 | Credit officer vượt thẩm quyền approve | Authorization Risk | High (4x4=16) | - Authority matrix trong system<br>- System block nếu vượt limit<br>- Approval log audit | Preventive / Detective (Control Environment + Control Activities) | Strong | Low (1x3=3) |
| R11 | Thông đồng giữa RM và Credit officer để approve khách không đủ điều kiện | Fraud Risk | High (3x5=15) | - Segregation of duties (RM không được thẩm định)<br>- Random case review<br>- Relationship monitoring (cùng approve nhiều case) | Preventive / Detective (Control Environment + Monitoring) | Moderate | Medium (2x4=8) |

### 3.4 GIAI ĐOẠN PHÊ DUYỆT

| Risk ID | Rủi ro (Risk) | Risk Category | Inherent Risk (L x I) | Control Hiện tại | Control Type (COSO) | Control Effectiveness | Residual Risk (L x I) |
|---------|---------------|---------------|---------------------|------------------|---------------------|---------------------|---------------------|
| R12 | Auto-approval sai do rule engine lỗi | Technology Risk | High (3x5=15) | - UAT trước khi deploy rule mới<br>- Monitoring auto-approval rate<br>- Sample review monthly | Preventive / Detective (Control Activities + Monitoring) | Strong | Low (1x4=4) |
| R13 | Manager approve case của chính mình hoặc người thân | Conflict of Interest | Medium (3x4=12) | - System check relationship<br>- Declaration of interest annually<br>- Independent review nếu phát hiện | Preventive / Detective (Control Environment) | Moderate | Medium (2x3=6) |
| R14 | Áp lực doanh số khiến manager approve lỏng lẻo | Conduct Risk | High (4x4=16) | - Balanced scorecard (không chỉ volume mà có NPL)<br>- Independent credit risk approval từ Risk Department<br>- Tone from the top về risk culture | Preventive (Control Environment + Risk Assessment) | Moderate | Medium (3x3=9) |

### 3.5 GIAI ĐOẠN GIẢI NGÂN

| Risk ID | Rủi ro (Risk) | Risk Category | Inherent Risk (L x I) | Control Hiện tại | Control Type (COSO) | Control Effectiveness | Residual Risk (L x I) |
|---------|---------------|---------------|---------------------|------------------|---------------------|---------------------|---------------------|
| R15 | Giải ngân vào tài khoản không phải của khách hàng (money mule) | Fraud / AML Risk | Very High (5x5=25) | - Same-name account check<br>- OTP confirmation từ khách<br>- Fraud screening (tài khoản mở gần đây, pattern lạ)<br>- Daily limit per account | Preventive / Detective (Control Activities) | Strong | Medium (2x4=8) |
| R16 | Không có chữ ký hợp đồng hợp lệ | Legal / Compliance Risk | High (4x5=20) | - eSign với OTP + face matching<br>- Chữ ký ướt phải có witness<br>- Lưu trữ hợp đồng 100% | Preventive (Control Activities) | Strong | Low (2x3=6) |
| R17 | Giải ngân trùng lặp (cùng 1 case disbursed 2 lần) | Operational Risk | Medium (2x5=10) | - Unique ID check<br>- Status lock sau khi disbursed<br>- Reconciliation daily | Preventive / Detective (Control Activities + Information & Communication) | Strong | Low (1x3=3) |
| R18 | Disbursement officer thông đồng với khách để giải ngân sai | Fraud Risk | High (3x5=15) | - Maker-Checker cho disbursement<br>- Random review<br>- Employee background check | Preventive / Detective (Control Environment + Monitoring) | Moderate | Medium (2x4=8) |

### 3.6 GIAI ĐOẠN THU NỢ

| Risk ID | Rủi ro (Risk) | Risk Category | Inherent Risk (L x I) | Control Hiện tại | Control Type (COSO) | Control Effectiveness | Residual Risk (L x I) |
|---------|---------------|---------------|---------------------|------------------|---------------------|---------------------|---------------------|
| R19 | Auto-deduction thất bại do công ty không chuyển lương vào VPBank | Liquidity / Credit Risk | High (4x4=16) | - Agreement với HR công ty<br>- Backup collection plan<br>- Early warning nếu không deduct được | Preventive / Detective (Control Activities + Monitoring) | Moderate | Medium (3x3=9) |
| R20 | Khách nghỉ việc nhưng không thông báo, không trả nợ | Credit Risk | High (5x4=20) | - Monthly employment verification<br>- Early collection nếu DPD > 5<br>- Contact HR ngay khi phát hiện | Detective / Corrective (Monitoring) | Moderate | Medium (3x4=12) |
| R21 | Collector harassment/sai quy trình thu hồi nợ | Conduct / Compliance Risk | Medium (3x4=12) | - Script chuẩn cho collector<br>- Call recording<br>- Complaint monitoring<br>- Training về Conduct Risk | Preventive / Detective (Control Environment + Monitoring) | Strong | Low (1x3=3) |
| R22 | Không provision đúng NPL theo SBV | Compliance / Financial Risk | High (4x5=20) | - Auto classification theo DPD<br>- Provision calculation theo Circular 11<br>- Internal audit review quarterly | Preventive / Detective (Control Activities + Monitoring) | Strong | Low (2x3=6) |

---

## 4. RCSA MATRIX TỔNG HỢP

### 4.1 Heat Map - Inherent Risk

```
Impact
  5 │         R09, R15                    
    │                                     
  4 │   R08, R10, R16, R19, R20          
    │   R02, R03, R05, R11, R13          
  3 │   R04, R06                          
    │                                     
  2 │                                     
    │                                     
  1 │                                     
    └─────────────────────────────────
      1    2    3    4    5  Likelihood
```

### 4.2 Heat Map - Residual Risk

```
Impact
  5 │                                     
    │                                     
  4 │   R07, R09, R11, R15, R18, R20     
    │                                     
  3 │   R02, R05, R13, R14, R19, R22     
    │   R01, R03, R04, R06, R08, R10     
  2 │   R12, R16, R17, R21                
    │                                     
  1 │                                     
    └─────────────────────────────────
      1    2    3    4    5  Likelihood
```

### 4.3 Bảng Đánh Giá Tổng Quát

| Risk Level | Inherent Risk Count | Residual Risk Count | Control Effectiveness |
|------------|---------------------|---------------------|---------------------|
| Very High (>16) | 2 (9%) | 0 (0%) | **Excellent** |
| High (12-16) | 11 (50%) | 0 (0%) | **Strong** |
| Medium (6-11) | 7 (32%) | 13 (59%) | **Good** |
| Low (1-5) | 2 (9%) | 9 (41%) | **Satisfactory** |

**Kết luận:** Controls đang hoạt động hiệu quả, đưa 100% rủi ro cao về mức trung bình/thấp.

---

## 5. LIÊN KẾT VỚI COSO FRAMEWORK

### 5.1 Control Environment (Môi trường kiểm soát)

**Control Objectives:**
- Thiết lập segregation of duties giữa origination, underwriting, approval, disbursement
- Xây dựng tone from the top về risk culture và integrity
- Authority matrix rõ ràng cho từng cấp phê duyệt

**Controls áp dụng:**
- R10: Authority matrix trong system
- R11, R13: Segregation of duties, conflict of interest declaration
- R14: Balanced scorecard, tone from the top
- R18, R21: Employee background check, training về conduct

**Control Deficiencies cần khắc phục:**
- ⚠️ Chưa có formal code of conduct training cho tất cả staff (đặc biệt RM và Credit Officer)
- ⚠️ Conflict of interest declaration chỉ annual, nên có real-time declaration khi approve case

### 5.2 Risk Assessment (Đánh giá rủi ro)

**Control Objectives:**
- Đánh giá rủi ro credit cho từng khách hàng phù hợp với risk appetite
- Phát hiện fraud và money laundering risk sớm

**Controls áp dụng:**
- R07: Model validation, champion-challenger, PSI monitoring
- R14: Independent credit risk approval, risk appetite review

**Control Deficiencies cần khắc phục:**
- ⚠️ Model validation chỉ quarterly, nên tăng lên monthly cho portfolio mới
- ⚠️ Chưa có stress testing cho kịch bản suy thoái (ví dụ: công ty hợp tác phá sản hàng loạt)

### 5.3 Control Activities (Hoạt động kiểm soát)

**Control Objectives:**
- Đảm bảo data accuracy từ origination đến disbursement
- Ngăn chặn fraud, unauthorized access, policy violation
- Tuân thủ quy trình 100% (không skip bước)

**Controls áp dụng:**
- **Preventive:** R01 (eKYC), R03 (company whitelist), R04 (maker-checker), R08 (mandatory checklist), R09 (hard stop), R12 (UAT), R15 (same-name check), R16 (eSign), R17 (unique ID), R22 (auto provision)
- **Detective:** R01 (AML screening), R04 (validation rules), R05 (audit log review), R07 (model monitoring), R08 (quality audit)
- **Corrective:** R06 (recovery plan), R07 (model recalibration)

**Control Deficiencies cần khắc phục:**
- ⚠️ R05: Red flag report chưa tự động, cần AI/ML để detect pattern anomaly
- ⚠️ R11: Relationship monitoring chưa có dashboard real-time

### 5.4 Information & Communication (Thông tin & truyền thông)

**Control Objectives:**
- Truyền tải thông tin chính xác, kịp thời giữa các bước trong quy trình
- Báo cáo control deficiency và risk event lên management

**Controls áp dụng:**
- R17: Daily reconciliation report
- R02: Complaint tracking và reporting
- R07: Quarterly model performance report

**Control Deficiencies cần khắc phục:**
- ⚠️ Chưa có dashboard real-time cho management về key risk indicators (KRI)
- ⚠️ Communication về policy change chưa được documented đầy đủ (nhiều khi chỉ email)

### 5.5 Monitoring Activities (Hoạt động giám sát)

**Control Objectives:**
- Đánh giá hiệu quả của controls thường xuyên
- Phát hiện và xử lý control breakdown kịp thời

**Controls áp dụng:**
- R02: Mystery shopping, call recording review
- R05: Random audit log review
- R07: Model monitoring (PSI, Gini), override tracking
- R08: Monthly quality audit
- R10, R12: Approval log audit, auto-approval monitoring
- R11: Random case review
- R19: Early warning monitoring
- R20: Monthly employment verification
- R21: Call recording review, complaint monitoring
- R22: Internal audit quarterly

**Control Deficiencies cần khắc phục:**
- ⚠️ Random audit chỉ sample 5-10%, nên tăng lên 20% hoặc dùng AI để audit 100%
- ⚠️ Monitoring activities chưa có KPI rõ ràng cho từng control (ví dụ: % audit findings closed within 30 days)

---

## 6. ACTION PLAN - KHẮC PHỤC CONTROL DEFICIENCIES

| ID | Control Deficiency | Severity | Recommended Action | Owner | Timeline | Cost Estimate |
|----|-------------------|----------|-------------------|-------|----------|---------------|
| A01 | Chưa có formal code of conduct training | Medium | Phát triển e-learning module về conduct risk, bắt buộc 100% staff hoàn thành annual | HR + Compliance | Q1 2025 | 50M VND |
| A02 | Conflict of interest declaration chỉ annual | Medium | Tích hợp vào LOS: popup khi approve case, bắt declare real-time | IT + Risk | Q2 2025 | 30M VND |
| A03 | Model validation chỉ quarterly | High | Tăng frequency lên monthly, tự động hóa PSI/Gini report | Data Science + Risk | Q1 2025 | 20M VND |
| A04 | Chưa có stress testing portfolio | High | Xây dựng stress scenarios (company bankrupt, unemployment spike) | Credit Risk | Q2 2025 | 100M VND (consultant) |
| A05 | Red flag report chưa tự động | Medium | Dùng ML để detect anomaly pattern (multiple edits, unusual approval time) | Data Science | Q3 2025 | 150M VND |
| A06 | Dashboard KRI chưa có real-time | Medium | Build dashboard với Power BI/Tableau, refresh mỗi giờ | IT + Risk | Q2 2025 | 80M VND |
| A07 | Random audit chỉ 5-10% sample | Low | Tăng lên 20% hoặc dùng AI audit 100% (prioritize high-risk cases) | Internal Audit | Q3 2025 | 200M VND |
| A08 | Monitoring KPI chưa rõ ràng | Medium | Thiết lập KPI cho từng control (ví dụ: % findings closed < 30 days) | Risk + Audit | Q1 2025 | 10M VND |

**Total Budget:** ~640M VND (~27,000 USD)

**Expected Benefits:**
- Giảm Residual Risk thêm 20-30%
- Tăng control automation từ 60% lên 85%
- Giảm NPL từ 1.8% xuống < 1.5%

---

## 7. KEY RISK INDICATORS (KRI) - MONITORING METRICS

| KRI | Target | Alert Threshold | Data Source | Frequency |
|-----|--------|-----------------|-------------|-----------|
| Auto-approval rate | 70-80% | <60% or >90% | LOS system | Daily |
| Override rate (manual intervention) | <10% | >15% | LOS system | Weekly |
| Data entry error rate (rejected by checker) | <5% | >10% | LOS system | Daily |
| Average application processing time | <4 hours | >6 hours | LOS system | Daily |
| CIC check compliance | 100% | <98% | LOS system | Daily |
| Same-name disbursement compliance | 100% | <99% | Core banking | Daily |
| NPL ratio (>90 DPD) | <2% | >2.5% | Collection system | Monthly |
| Early delinquency rate (5-30 DPD) | <8% | >12% | Collection system | Weekly |
| Employment verification completion | 100% | <95% | Collection system | Monthly |
| Model PSI (Population Stability Index) | <0.1 | >0.25 | Model monitoring | Monthly |
| Gini coefficient (model discrimination) | >0.35 | <0.30 | Model monitoring | Quarterly |
| Fraud case detection rate | 0.5-1% | >2% | Fraud team | Monthly |
| Complaint rate | <0.5% | >1% | CRM system | Monthly |
| Internal audit findings (High severity) | 0 | >2 per quarter | Audit report | Quarterly |

---

## 8. ROLES & RESPONSIBILITIES (RACI MATRIX)

| Activity | RM/Sales | Data Entry | Credit Officer | Team Leader | Risk Dept | IT | Internal Audit |
|----------|----------|------------|----------------|-------------|-----------|-----|----------------|
| KYC check | A | C | I | I | I | R | - |
| Data entry | C | **A** | I | I | - | R | - |
| 4-eyes check | - | R | **A** | I | - | - | - |
| Credit assessment | I | - | **A** | R | C | - | - |
| Approval (auto) | - | - | I | I | - | **R/A** | - |
| Approval (manual) | - | - | R | **A** | C | - | - |
| Disbursement | - | - | I | I | - | **A** | - |
| Collection monitoring | I | - | I | A | C | R | - |
| Control effectiveness review | I | I | I | C | **A** | - | R |
| Audit | I | I | I | I | C | I | **A** |

**Legend:**
- **R** = Responsible (thực hiện)
- **A** = Accountable (chịu trách nhiệm cuối cùng)
- **C** = Consulted (tham vấn)
- **I** = Informed (được thông báo)

---

## 9. APPENDIX - ĐỊNH NGHĨA VÀ THANG ĐO

### 9.1 Risk Rating Scale

**Likelihood (Khả năng xảy ra):**
- 1 = Rare (< 5% cases/year)
- 2 = Unlikely (5-20% cases/year)
- 3 = Possible (20-50% cases/year)
- 4 = Likely (50-80% cases/year)
- 5 = Almost Certain (> 80% cases/year)

**Impact (Tác động):**
- 1 = Negligible (< 10M VND loss/case, không ảnh hưởng danh tiếng)
- 2 = Minor (10-50M VND, khiếu nại nhỏ)
- 3 = Moderate (50-200M VND, báo chí địa phương)
- 4 = Major (200M-1B VND, báo chí quốc gia, SBV warning)
- 5 = Severe (> 1B VND, license risk, criminal prosecution)

**Inherent Risk = Likelihood x Impact**
**Residual Risk = Likelihood (sau khi có control) x Impact (sau khi có control)**

### 9.2 Control Effectiveness Rating

- **Strong (90-100%):** Control đang hoạt động tốt, rất ít deficiency, automation cao
- **Moderate (70-89%):** Control hoạt động nhưng có vài gaps, cần cải thiện
- **Weak (50-69%):** Control có nhiều gaps, cần action plan ngay
- **Deficient (<50%):** Control không hiệu quả, rủi ro cao

### 9.3 COSO Component Mapping

| COSO Component | Purpose | Key Controls in this Process |
|----------------|---------|------------------------------|
| Control Environment | Văn hóa rủi ro, đạo đức, năng lực nhân sự | Authority matrix, segregation of duties, training |
| Risk Assessment | Nhận diện và đánh giá rủi ro | Credit scoring, fraud screening, stress testing |
| Control Activities | Chính sách và thủ tục cụ thể | Maker-checker, hard stops, validation rules |
| Information & Communication | Truyền tải thông tin chính xác, kịp thời | Reporting, dashboard, escalation |
| Monitoring Activities | Đánh giá hiệu quả của ICFR | Audit, quality review, KRI tracking |

---

**Date:** November 15, 2025
**Author:** Dang Tran Thanh
---


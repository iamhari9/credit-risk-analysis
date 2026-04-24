# 📊 Credit Risk Analysis

## 📌 Tổng quan dự án
Các ngân hàng đóng vai trò then chốt trong nền kinh tế thị trường. Họ quyết định ai có thể nhận được tài chính và với những điều kiện nào, đồng thời có thể ảnh hưởng tích cực hoặc tiêu cực đến các quyết định đầu tư. Để thị trường và xã hội vận hành, cá nhân và doanh nghiệp cần tiếp cận tín dụng.

Dự án này phân tích bộ dữ liệu của một ngân hàng nhằm mục đích rút ra những insight về mức độ rủi ro cho vay của ngân hàng.
<img width="4150" height="2400" alt="report_page-0001" src="https://github.com/user-attachments/assets/8e743dc1-2f61-414a-b6e7-b4512bf2bc19" />
<img width="4150" height="2400" alt="report_page-0002" src="https://github.com/user-attachments/assets/4ed25afe-0fad-47ae-bf37-7c09933d7b70" />

---

## 🗂 Dataset
- Tên dataset: Give Me Some Credit
- Nguồn: https://www.kaggle.com/competitions/GiveMeSomeCredit/

---

## 🔄 Quy trình phân tích
1. Tải bộ dữ liệu
2. Import dữ liệu vào Power BI
3. Làm sạch dữ liệu:
- Xoá cột số thứ tự
- Tính trung vị và đặt MonthlyIncome có giá trị null bằng trung vị
- Lọc tuổi > 0
- Đặt mức DebtRatio cao nhất = 3
4. Tính toán các measure sử dụng hàm DAX
5. Xây dựng báo cáo

⚠️ Lưu ý: Việc gán giá trị null của cột MonthlyIncome bằng trung vị và đặt DebtRatio lớn nhất bằng 3 giúp việc phân tích thuận tiện hơn, nhưng sẽ gây ảnh hưởng nhẹ tới kết quả phân tích. Tuy nhiên, xét tổng thể thì xu hướng vẫn nhất quán.

---

## 🛠 Công cụ
- Power BI
- Excel/CSV
- GitHub

---

## 🎯 Các câu hỏi chính
Dự án tập trung vào việc trả lời 3 câu hỏi:
1. Ai có nguy cơ vỡ nợ?
2. Vì sao họ rủi ro?
3. Nhóm nào nên tránh/ưu tiên?

---

## 📊 Phân tích dữ liệu và báo cáo
Trong bộ dữ liệu này, ta xét các yếu tố ảnh hưởng tới tỷ lệ vỡ nợ của khách đi vay bao gồm:
- Tuổi
- Thu nhập
- Số người phụ thuộc
- Tỷ lệ nợ
- Tần suất nợ
- Mức độ nghiêm trọng nợ quá hạn

Số khách hàng đi vay là gần 150 nghìn, với tỷ lệ nợ trung bình là 88.70% và tỷ lệ vỡ nợ là 6.68%.

Tỷ lệ nợ được tính theo công thức:
- Tỷ lệ nợ = (𝐶á𝑐 𝑘ℎ𝑜ả𝑛 𝑝ℎả𝑖 𝑡𝑟ả ℎà𝑛𝑔 𝑡ℎá𝑛𝑔)/(𝑇ổ𝑛𝑔 𝑡ℎ𝑢 𝑛ℎậ𝑝 ℎà𝑛𝑔 𝑡ℎá𝑛𝑔) * 100%

Với mức tỷ lệ nợ trung bình là 88.70%, ta thấy rằng phần lớn thu nhập của số đông khách hàng được sử dụng cho việc trả nợ.
Mức thu nhập trung bình là $6,418, mức thu nhập trung bình không trả được nợ là $5,592.

**1. Tỷ lệ vỡ nợ ảnh hưởng bởi độ tuổi**
<img width="517" height="438" alt="image" src="https://github.com/user-attachments/assets/ba2595c3-8cb4-4b99-989c-30689d866248" />
Chia nhóm tuổi thành 4 nhóm, ta thấy rằng nhóm dưới 30 tuổi là nhóm có tỷ lệ vỡ nợ cao nhất. Nhóm này gồm những người ở độ tuổi sinh viên, mới ra trường và đã đi làm nhưng chưa có thu nhập ổn định. Do đó mức thu nhập của nhóm này thấp, trong khi vẫn phải chi trả các khoản phải trả hàng tháng dẫn tới việc phải đi vay, và vay không trả được.
Nhóm 30-50 tuổi chủ yếu gồm những người đã lập gia đình. Do đã có gia đình nên mức thu nhập của họ sẽ tăng lên -> giảm gánh nặng các khoản chi hàng tháng -> ít phải đi vay -> ít nợ.
Ta thấy rằng tỷ lệ vỡ nợ tỷ lệ nghịch với độ tuổi, tuổi càng cao thì tỷ lệ vỡ nợ càng thấp.

**2. Tỷ lệ vỡ nợ ảnh hưởng bởi thu nhập**
<img width="517" height="450" alt="image" src="https://github.com/user-attachments/assets/89d04efc-1e06-463f-a66f-fb82f7deed2c" />
Thu nhập là một trong những yếu tố quan trọng ảnh hưởng trực tiếp tới việc vay nợ. Nhóm có thu nhập thấp (thu nhập trung bình hàng tháng < $5000) vẫn phải chi trả những khoản chi hàng tháng, trong khi thu nhập không đáp ứng được, dẫn tới việc phải đi vay để chi tiêu. Tuy nhiên thu nhập < chi tiêu -> nợ càng cao càng không trả được -> tỷ lệ vỡ nợ cao. Nhóm có thu nhập trung bình (< $8000) có tỷ lệ vỡ nợ thấp hơn, và nhóm có thu nhập cao (> $8000) có tỷ lệ vỡ nợ thấp nhất. Do đó, tỷ lệ vỡ nợ tỷ lệ nghịch với thu nhập, thu nhập càng cao thì càng có khả năng chi trả và tích luỹ cao dẫn tới việc vỡ nợ thấp, ngược lại thu nhập thấp sẽ phải chịu áp lực tài chính và việc chi trả cho các khoản nợ sẽ rất khó khăn.

**3. Tỷ lệ vỡ nợ ảnh hưởng bởi độ tuổi và thu nhập**
<img width="525" height="225" alt="image" src="https://github.com/user-attachments/assets/eede48ab-4d0d-411f-ada1-013f47eff9cf" />
Thông qua ma trận giữa nhóm tuổi và mức thu nhập trung bình hàng tháng, ta thấy nhóm những người dưới 30 tuổi với mức thu nhập thấp (< $5000) và thu nhập trung bình (< $8000) có tỷ lệ vỡ nợ cao nhất. Do đó cần đặc biệt lưu ý khi cho vay đối với nhóm này.

**4. Tác động của số người phụ thuộc tới tỷ lệ vỡ nợ**
<img width="542" height="492" alt="image" src="https://github.com/user-attachments/assets/652cc97f-f5c4-48a6-8970-b57e03cb6ae1" />
Việc có người phụ thuộc cũng ảnh hưởng đến tỷ lệ vỡ nợ. Tỷ lệ này có xu hướng tăng khi có ít người phụ thuộc, đạt đỉnh là mức 6 người với tỷ lệ vỡ nợ lên tới 15.19%, tuy nhiên lại giảm dần sau đó, với tỷ lệ vỡ nợ là 0% khi có 9 người phụ thuộc. Có nhiều người phụ thuộc sẽ giúp giảm gánh nặng tài chính, đặc biệt là khi bố mẹ sẵn sàng chu cấp để hỗ trợ con cháu của họ. 
Tỷ lệ vỡ nợ đối với nhóm có ít người phụ thuộc cao hơn, phần lớn là nhóm tuổi từ 30-50 và 50-70 tuổi. Việc có ít người phụ thuộc với nhóm tuổi này cho thấy rằng họ đang phải chịu trách nhiệm chính cho việc chi trả các khoản phải trả hàng tháng, và việc phải một mình nuôi "các miệng ăn" sẽ khiến cho chi tiêu cao, khiến việc trả nợ trở nên khó khăn.

**5. Tỷ lệ vay nợ và tỷ lệ nợ**
<img width="542" height="492" alt="image" src="https://github.com/user-attachments/assets/3686dc9b-d8b5-4cd8-8eae-d5893d322ec2" />
Rủi ro vỡ nợ tăng lên khi tỷ lệ nợ tăng từ mức thấp lên mức cao, nhưng lại giảm bất ngờ ở nhóm tỷ lệ nợ rất cao. Việc này xảy ra một phần do tỷ lệ nợ của bộ dữ liệu được đặt ở mức cao nhất là 300%, ngoài ra cũng có thể do những người thuộc nhóm này có tài sản lớn hoặc vay nhiều nhưng vẫn kiểm soát được. Do đó, mối quan hệ giữa tỷ lệ vỡ nợ và tỷ lệ nợ là phi tuyến tính và cần phải theo dõi thêm nhóm Extreme.

**6. Sự ảnh hưởng của tần suất thanh toán chậm tới tỷ lệ vỡ nợ**
<img width="564" height="338" alt="image" src="https://github.com/user-attachments/assets/6f92588a-874a-4671-854a-70d1d760cfb4" />
Tỷ lệ vỡ nợ tăng mạnh theo tần suất thanh toán chậm, đạt mức cao với nhóm 3-5 lần thanh toán chậm với 39.97%, và rất cao là 60.20% khi thanh toán chậm từ 5 lần trở lên. Chỉ với 1-2 lần thanh toán chậm mà tỷ lệ vỡ nợ tăng đáng kể rủi ro như vậy, do đó có thể thấy rằng yếu tố này ảnh hưởng rất lớn tới khả năng vỡ nợ, cần đặc biệt lưu ý đối với các trường hợp thanh toán chậm.
<img width="686" height="248" alt="image" src="https://github.com/user-attachments/assets/c6173983-abb9-4129-ac75-d8507bbfcc0b" />
Qua ma trận giữa tần suất trả chậm và các nhóm tuổi, ta thấy rằng rủi ro vỡ nợ tăng mạnh theo tần suất thanh toán chậm ở mọi nhóm tuổi, đặc biệt nhóm dưới 30 tuổi vẫn là nhóm có rủi ro vỡ nợ cao. Tuy nhiên rủi ro vỡ nợ đạt đỉnh điểm ở nhóm người trung niên, khi áp lực tài chính cao nhất, đặc biệt khi có sự thanh toán chậm trễ.

**7. Mức độ nghiêm trọng của việc thanh toán chậm**
<img width="568" height="336" alt="image" src="https://github.com/user-attachments/assets/b4e86ecc-5308-48a4-9583-a0e31d384757" />
Tỷ lệ vỡ nợ tăng mạnh theo mức độ nghiêm trọng của việc thanh toán chậm, đặc biệt là nhóm thanh toán chậm từ 60 ngày. Đặc biệt đối với nhóm thanh toán chậm 90 ngày, đây là chỉ số rất quan trọng ảnh hưởng tới việc khách hàng không thanh toán nợ. Trên thực tế khi đã chậm trả từ 90 ngày, việc thúc giục khách hàng thanh toán nợ trở nên rất khó khăn. Do đó ta cần lưu ý ngay khi khách hàng có tình trạng chậm nợ từ 30-40 ngày để tránh tình trạng khách vỡ nợ không thanh toán được.

**8. Tác động của tần suất và mức độ nghiệm trọng của việc thanh toán chậm**
<img width="712" height="246" alt="image" src="https://github.com/user-attachments/assets/64402d5f-61ab-4f7e-beeb-744af56551bc" />
Tỷ lệ vỡ nợ tăng lên đáng kể khi cả mức độ nghiêm trọng và tần suất thanh toán chậm đều tăng. Mức độ nghiêm trọng và tần suất chậm thanh toán làm tăng cường tác động của nhau đến rủi ro vỡ nợ. Ngay cả với cùng tần suất, mức độ nghiêm trọng cao hơn sẽ dẫn đến rủi ro vỡ nợ cao hơn và ngược lại, với cùng mức độ nghiệm trọng, tần suất cao hơn cũng dẫn đến rủi ro vỡ nợ cao hơn. Do đó ta thấy rằng tỷ lệ vỡ nợ phát sinh từ tác động tổng hợp của mức độ nghiêm trọng và tần suất chậm thanh toán, cả hai yếu tố này đều tác động lẫn nhau.

**9. Phân nhóm khách hàng theo phân khúc rủi ro**
<img width="1125" height="333" alt="image" src="https://github.com/user-attachments/assets/785e2a37-a051-4866-9ceb-e584b9be6c73" />
Phân khúc rủi ro giúp phân nhóm khách hàng một cách hiệu quả dựa trên khả năng vỡ nợ của họ theo 5 tiêu chí: tuổi, thu nhập, tỷ lệ nợ, tần suất và mức độ nghiêm trọng của việc thanh toán chậm. 

Ta chấm điểm cho từng tiêu chí với 30 điểm/tiêu chí, tổng 150 điểm và phân nhóm dựa theo tổng số điểm của từng khách hàng:
-  Low Risk: <= 38 điểm
-  Medium Risk: <= 75 điểm
-  High Risk: 76+ điểm
```dax
Age Score = SWITCH(TRUE(), 'cs-training'[age] < 30, 30, 'cs-training'[age] < 50, 20, 'cs-training'[age] < 70, 10, 0)
```
```dax
Debt Score = SWITCH(TRUE(), 'cs-training'[DebtRatio_New] > 2, 30, 'cs-training'[DebtRatio_New] > 1, 20, 'cs-training'[DebtRatio_New] > 0.5, 10, 0)
```
``` dax
Income Score = SWITCH(TRUE(), 'cs-training'[MonthlyIncome] < 5000, 30, 'cs-training'[MonthlyIncome] < 8000, 15, 0)
```
```dax
Late Payment Score = SWITCH(TRUE(), 'cs-training'[Total late] = 0, 0, 'cs-training'[Total late] <= 2, 10, 'cs-training'[Total late] <= 5, 20, 30)
```
```dax
Late Severity Score = SWITCH(TRUE(), 'cs-training'[NumberOfTimes90DaysLate] > 0, 30, 'cs-training'[NumberOfTime60-89DaysPastDueNotWorse] > 0, 20, 'cs-training'[NumberOfTime30-59DaysPastDueNotWorse] > 0, 10, 0)
```
Ta thấy rằng khách hàng có rủi ro cao có số khách hàng thấp hơn 2 nhóm còn lại nhưng lại có tỷ lệ vỡ nợ cao đột biến. Do đó cần tập trung xử lý một cách có hiệu quả đối với nhóm này, như từ chối việc cho vay hoặc kiểm soát chặt khoản vay cũng như lịch sử thanh toán. Đối với nhóm rủi ro trung bình, tuy tỷ lệ vỡ nợ là 5.69% nhưng vẫn cần xem xét thêm trước khi cho vay. Nhóm rủi ro thấp có tỷ lệ vỡ nợ thấp nhất nên có thể an toàn cho vay.

---

## 🔍 Insight
1. Tỷ lệ vỡ nợ tỷ lệ nghịch với độ tuổi, tuổi càng cao thì tỷ lệ vỡ nợ càng thấp.
2. Nhóm những người dưới 30 tuổi với mức thu nhập thấp (< $5000) và thu nhập trung bình (< $8000) có tỷ lệ vỡ nợ cao nhất.
3. Tỷ lệ vỡ nợ cao hơn khi có ít người phụ thuộc.
4. Mối quan hệ giữa tỷ lệ vỡ nợ và tỷ lệ nợ là phi tuyến tính và cần phải theo dõi thêm nhóm có tỷ lệ nợ cao.
5. Cần đặc biệt lưu ý đối với các trường hợp có tần suất thanh toán chậm cao và các trường hợp có mức độ thanh toán chậm nghiêm trọng.
6. Nhóm dưới 30 tuổi là nhóm có rủi ro vỡ nợ cao khi thanh toán chậm nhiều lần.
7. Rủi ro vỡ nợ đạt đỉnh ở nhóm người trung niên, khi áp lực tài chính cao nhất, đặc biệt khi có sự thanh toán chậm trễ.
8. Tỷ lệ vỡ nợ phát sinh từ tác động tổng hợp của mức độ nghiêm trọng và tần suất chậm thanh toán, cả hai yếu tố này đều tác động lẫn nhau.
9. Việc phân nhóm khách hàng theo phân khúc rủi ro là một cách hiệu quả cho phép đưa ra quyết định có mục tiêu dựa trên khả năng vỡ nợ của họ.

---

## 🧠 Đề xuất
1. Đối với nhóm dưới 30 tuổi và thu nhập thấp, cần kiểm tra kỹ trước khi duyệt các khoản vay và giảm hạn mức cho vay.
2. Đối với nhóm từ 30-70 tuổi, cần theo dõi tỷ lệ nợ, đặc biệt là các trường hợp có phát sinh thanh toán chậm.
3. Đối với các nhóm khách hàng theo phân khúc rủi ro:

High Risk:
- Giảm hạn mức cho vay
- Tăng các điều khoản cho vay
- Cảnh báo khi có tình trạng chậm thanh toán
- Theo dõi chặt chẽ

Medium Risk:
- Xem xét thêm trước khi duyệt các khoản vay
- Theo dõi lịch sử thanh toán
- Gửi thông báo thanh toán sớm khi gần đến hạn

Low Risk:
- Ưu tiên xét duyệt cho vay nhanh chóng
- Ưu đãi cho khách hàng

4. Triển khai hệ thống cảnh báo sớm dựa trên hành vi thanh toán chậm.

---

## 🏁 Kết luận
Thông qua phân tích dự án này cho thấy rủi ro vỡ nợ chủ yếu xuất phát từ hành vi thanh toán, đặc biệt là tần suất và mức độ nghiêm trọng của việc thanh toán chậm. Mặc dù các yếu tố như thu nhập và tỷ lệ nợ cũng đóng vai trò quan trọng, nhưng các chỉ số hành vi lại cho thấy tín hiệu rủi ro cao nhất. Bằng cách kết hợp các yếu tố này, ta có thể xác định hiệu quả các khách hàng có rủi ro cao và hỗ trợ các quyết định tín dụng dựa trên dữ liệu và thông tin đầy đủ hơn.

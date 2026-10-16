# 🚀 Smart Farm – Hệ Thống Trang Trại Thông Minh

## 1. Giới thiệu dự án

**Smart Farm** là hệ thống ứng dụng công nghệ IoT để giám sát môi trường và tự động hóa hoạt động tưới nước tại trang trại Lan.

Hệ thống thu thập dữ liệu từ cảm biến, xử lý thông tin bằng bộ điều khiển và kích hoạt máy bơm khi điều kiện tưới được đáp ứng.

* Mục tiêu: Tiết kiệm nước, giảm công sức lao động và nâng cao hiệu quả chăm sóc cây trồng.
* Đối tượng sử dụng: Người nông dân và người quản lý trang trại.
* Nguyên tắc hoạt động: Thu thập dữ liệu → Xử lý → Ra quyết định → Điều khiển thiết bị.

## 2. Sơ đồ hệ thống

![Sơ đồ hệ thống Smart Farm: Cảm biến gửi dữ liệu đến bộ điều khiển, bộ điều khiển kích hoạt máy bơm và gửi thông tin đến ứng dụng giám sát.](docs/images/smart-farm-system.png "Sơ đồ phối hợp phần cứng Smart Farm")

**Luồng hoạt động:**

1. Cảm biến thu thập nhiệt độ, độ ẩm không khí và độ ẩm đất.
2. Bộ điều khiển nhận và xử lý dữ liệu.
3. Chương trình so sánh dữ liệu với ngưỡng tưới đã cấu hình.
4. Nếu đất khô và các điều kiện an toàn được đáp ứng, bộ điều khiển kích hoạt máy bơm.
5. Hệ thống ghi nhật ký và cập nhật trạng thái để người nông dân theo dõi.

*Lưu ý:* Hình ảnh sơ đồ được lưu tại `docs/images/smart-farm-system.png`. Cần đặt ảnh sơ đồ thực tế vào đúng đường dẫn này để hình ảnh hiển thị khi mở README.

## 3. Hướng dẫn cài đặt

### 3.1. Chuẩn bị

- Bộ điều khiển tương thích với hệ thống IoT.
- Cảm biến nhiệt độ và độ ẩm.
- Cảm biến độ ẩm đất.
- Rơ-le, máy bơm nước và van tưới phù hợp.
- Nguồn điện và kết nối mạng nếu cần giám sát từ xa.

### 3.2. Chuẩn bị thư mục dự án

```bash
mkdir -p smart-farm/docs/images
mkdir -p smart-farm/src
mkdir -p smart-farm/data/logs
cd smart-farm
```

### 3.3. Cấu hình hệ thống

1. Kết nối cảm biến với bộ điều khiển theo sơ đồ phần cứng.
2. Cài đặt chương trình điều khiển tương thích với thiết bị.
3. Cấu hình ngưỡng nhiệt độ, độ ẩm đất và thời gian tưới theo loại cây trồng.
4. Kiểm tra cảm biến, máy bơm và cơ chế ngắt an toàn trước khi vận hành.
5. Chạy thử với khu vực nhỏ trước khi áp dụng trên toàn trang trại.

*Lưu ý:* Các lệnh trên tạo thư mục dự án, không tự động cài đặt phần mềm hoặc lập trình bộ điều khiển. Cần bổ sung lệnh cài đặt cụ thể theo phần cứng và phần mềm thực tế.

## 4. Tính năng hệ thống

- [x] Thu thập dữ liệu từ cảm biến môi trường.
- [x] Xử lý dữ liệu theo mô hình Input – Process – Output (IPO).
- [x] Kiểm tra ngưỡng để hỗ trợ quyết định tưới nước.
- [x] Điều khiển máy bơm thông qua rơ-le hoặc bộ điều khiển tương thích.
- [x] Ghi nhật ký hoạt động để theo dõi và kiểm tra sự cố.
- [ ] Bổ sung cảnh báo từ xa khi cảm biến hoặc máy bơm gặp lỗi.
- [ ] Phân tích dữ liệu lịch sử để tối ưu lịch tưới.

*Ghi chú:* Các mục đã đánh dấu hoàn thành thể hiện chức năng dự kiến trong tài liệu mẫu. Chỉ đánh dấu hoàn thành khi đã kiểm thử trên hệ thống thực tế.

## 5. Bảng thông số hệ thống

| Thành phần | Chức năng | Dữ liệu hoặc đầu ra |
|---|---|---|
| Cảm biến nhiệt độ | Đo nhiệt độ môi trường | °C |
| Cảm biến độ ẩm không khí | Theo dõi độ ẩm không khí | %RH |
| Cảm biến độ ẩm đất | Xác định tình trạng ẩm của đất | % hoặc giá trị cảm biến |
| CPU/vi điều khiển | Xử lý dữ liệu và điều khiển | Lệnh điều khiển |
| RAM | Lưu tạm dữ liệu đang xử lý | Dung lượng sử dụng |
| Bộ nhớ lưu trữ | Lưu chương trình và nhật ký | Byte, KB hoặc MB |
| Rơ-le | Đóng/ngắt mạch điều khiển | Trạng thái ON/OFF |
| Máy bơm nước | Cung cấp nước tưới | Trạng thái hoạt động |

*Lưu ý:* Bảng trên mô tả các thành phần và đơn vị đo phổ biến, không phải thông số kỹ thuật của một thiết bị cụ thể. Giá trị điện áp, công suất, dung lượng và ngưỡng tưới phải được xác định theo thiết bị thực tế.

## 6. Chu kỳ Fetch – Decode – Execute

Khi chương trình yêu cầu tưới cây tại trang trại Lan, CPU thực hiện chu kỳ xử lý lệnh như sau:

> **Fetch (Nạp lệnh):** CPU lấy lệnh tiếp theo của chương trình điều khiển từ bộ nhớ.
>
> **Decode (Giải mã):** CPU giải mã lệnh để xác định thao tác cần thực hiện, chẳng hạn kiểm tra dữ liệu cảm biến hoặc thay đổi trạng thái đầu ra.
>
> **Execute (Thực thi):** CPU thực hiện thao tác tương ứng. Nếu điều kiện tưới được thỏa mãn, chương trình gửi tín hiệu đến bộ điều khiển đầu ra để kích hoạt rơ-le và máy bơm.
>
> **Kết quả:** Đất được tưới theo điều kiện đã cấu hình. Chương trình tiếp tục giám sát và ngắt bơm khi đạt điều kiện dừng.

*Lưu ý:* CPU không trực tiếp cấp điện cho máy bơm. Tín hiệu điều khiển phải đi qua mạch điều khiển phù hợp; việc bật hoặc tắt bơm còn phụ thuộc vào chương trình và các điều kiện an toàn.

## 7. Mô hình DIKW – Chuyển dữ liệu thành hành động

DIKW gồm bốn cấp độ: Data (Dữ liệu), Information (Thông tin), Knowledge (Tri thức) và Wisdom (Trí tuệ).

```text
                 /\
                /  \
               / W  \       WISDOM – TRÍ TUỆ
              /------\      Chọn thời điểm và lượng nước tưới phù hợp
             /   K    \     KNOWLEDGE – TRI THỨC
            /----------\    Hiểu đất khô cần được tưới
           /     I      \   INFORMATION – THÔNG TIN
          /--------------\  Xác định độ ẩm đất thấp hơn ngưỡng
         /       D        \ DATA – DỮ LIỆU
        /__________________\ Đọc giá trị cảm biến, ví dụ 18%
```

### Ví dụ thực tế

1. **Data – Dữ liệu:** Cảm biến đo độ ẩm đất được 18%.
2. **Information – Thông tin:** Giá trị 18% thấp hơn ngưỡng tưới đã cấu hình là 25%.
3. **Knowledge – Tri thức:** Khi độ ẩm đất thấp, cây có thể cần bổ sung nước; cần xem xét loại cây và điều kiện môi trường.
4. **Wisdom – Trí tuệ:** Nếu cảm biến hoạt động bình thường, nguồn nước đủ và các điều kiện an toàn được đáp ứng, hệ thống quyết định tưới trong khoảng thời gian phù hợp rồi kiểm tra lại độ ẩm.

*Lưu ý:* Các giá trị 18% và 25% chỉ là ví dụ minh họa. Ngưỡng tưới thực tế cần được hiệu chỉnh theo loại đất, loại cây, cảm biến và điều kiện canh tác.

## 8. Lưu ý vận hành và xử lý sự cố

### 8.1. Khi RAM gần đầy do dữ liệu nhật ký

RAM là bộ nhớ tạm thời dành cho chương trình và dữ liệu đang xử lý. Nhật ký được ghi liên tục vào RAM có thể làm tăng mức sử dụng bộ nhớ, khiến hệ thống chậm hoặc chương trình bị lỗi.

**Quy trình xử lý an toàn:**

1. Kiểm tra mức sử dụng RAM và xác định chương trình tạo ra lượng dữ liệu lớn.
2. Dừng hoặc giới hạn việc ghi nhật ký không cần thiết theo cách an toàn; không tùy tiện dừng chương trình điều khiển tưới.
3. Ghi nhật ký cần thiết vào bộ nhớ lưu trữ phù hợp, chẳng hạn tệp log trên thiết bị lưu trữ.
4. Sao lưu nhật ký quan trọng trước khi xóa hoặc luân chuyển tệp.
5. Chỉ xóa các tệp nhật ký cũ đã xác định rõ, không xóa dữ liệu cấu hình hoặc chương trình điều khiển.
6. Khởi động lại dịch vụ nếu cần theo quy trình của thiết bị, sau đó kiểm tra cảm biến, máy bơm và hoạt động ghi log.

**Biện pháp phòng ngừa:**

- Giới hạn kích thước nhật ký và sử dụng cơ chế luân chuyển log (log rotation).
- Theo dõi mức sử dụng RAM định kỳ.
- Không lưu toàn bộ nhật ký dài hạn trong RAM.
- Duy trì bộ nhớ dự phòng để hệ thống tiếp tục xử lý dữ liệu cảm biến.
- Kiểm tra trạng thái máy bơm và cơ chế dừng an toàn sau khi khắc phục sự cố.

### 8.2. Nguyên tắc an toàn

- Không bật máy bơm nếu cảm biến hoặc dữ liệu điều khiển không đáng tin cậy.
- Thiết lập thời gian tưới tối đa và cơ chế ngắt khi xảy ra lỗi.
- Kiểm tra nguồn điện, rơ-le và đường ống trước khi bảo trì.
- Không thao tác trên mạch điện đang cấp nguồn nếu chưa có biện pháp an toàn phù hợp.

## 9. Kết luận

Smart Farm kết hợp cảm biến IoT, bộ điều khiển và thiết bị chấp hành để tự động hóa quá trình chăm sóc cây trồng.

Thông qua IPO, hệ thống xác định rõ đầu vào, quá trình xử lý và đầu ra. SoC hỗ trợ tích hợp các chức năng xử lý trong một thiết bị. Chu kỳ Fetch–Decode–Execute giải thích cách CPU thực hiện lệnh, còn mô hình DIKW thể hiện quá trình chuyển dữ liệu cảm biến thành quyết định tưới nước.

Tài liệu README giúp người sử dụng hiểu cấu trúc, cách vận hành và phương pháp xử lý sự cố cơ bản của hệ thống.

---

**Tài liệu dự án:** Smart Farm  
**Đối tượng sử dụng:** Người vận hành trang trại Lan  
**Định dạng:** Markdown (`README.md`)  
**Môi trường hiển thị:** StackEdit và các nền tảng hỗ trợ Markdown

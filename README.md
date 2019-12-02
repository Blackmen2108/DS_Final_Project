# DS_Final_Project

Final project of data-science course

### 1) Đặt vấn đề
Hiện nay, nhu cầu sử dụng smart phone ngày càng tăng cao, số lượng sản phẩm smart phone tung ra thị trường ngày càng nhiều. Để tăng tính cạnh tranh, các nhãn hàng sẽ cải thiện các thông số của điện thoại cũng như đưa ra giá cả hợp lí. 
Do đó, các công ty cần tham khảo giá thị trường các sản phẩm khác để định giá sản phẩm của mình dựa vào các chi tiết như CPU, RAM, Camera, thương hiệu ... 
Việc định giá được sản phẩm sẽ giúp nhà cung cấp đưa ra mức giá tốt hơn, doanh số bán hàng sẽ cao hơn. Đồng thời người tiêu dùng cũng sẽ biết được giá trị thực của sản phẩm mà không chạy theo giá trị thương hiệu, giúp chi tiêu sẽ hợp lí hơn.

### 2) Thu thập dữ liệu
Dữ liệu được thu thập từ trang web `https://www.devicespecifications.com`
Ta sẽ thu thập bằng cách parse HTML.
Có hơn 11000 link sản phẩm, tuy nhiên chỉ có gần 3000 sản phẩm là có ghi bảng giá.
Ta sẽ train với gần 3000 sản phẩm đó (nếu cần thiết sẽ tự thu thập giá trị của các sản phẩm không có bảng giá để tăng kích thước bộ train). Các sản phẩm không có bảng giá sẽ được dùng để test, giá trị dự đoán sẽ được so sánh với giá trị tự thu thập để check

### 3) Thông tin sản phẩm
    - Brand : tên thương hiệu
    - Name : tên sản phẩm
    - Dim : kích thước sản phẩm
    - Weight : cân nặng sản phẩm
    - Bat : pin của sản phẩm, giá trị mAh biểu thị dung lượng của pin
    - Blue : bluetooth
    - CPU : chip xử lý trung tâm
    - Cam: thể hiện các thông số camera của sản phẩm
    - Cores : biểu thị Chip có bao nhiêu nhân
    - Dis : thông số hiển thị hình ảnh
    - GPU : chip đồ họa
    - Memory card : thẻ nhớ điện thoại sử dụng
    - OS : hệ điều hành 
    - Pos : hệ thống định vị
    - RAM : bộ nhớ truy cập ngẫu nhiên
    - SIM : sim điện thoại sử dụng
    - SoC : hệ thống trên chip
    - Storage : dung lượng lưu trữ 
    - USB 
    - Wi-Fi : cách kết nối dựa trên tiêu chuẩn IEEE 802.11
    - Average price : giá trung bình của các sản phẩm thuộc dòng này
    - ....
 
 Thuộc tính "Average price" sẽ được tách ra làm output để train, các thuộc tính còn lại sẽ được dùng để train.
 Các giá trị của các thuộc tính có thể sẽ giữ nguyên (với những giá trị số) hoặc chuẩn hóa dựa vào những câu hỏi như:
    - Có tồn tại hay không? (đánh số 0, 1)
    - So sánh các thông số trong khoảng giá trị để phân thành các khoảng, mỗi khoảng sẽ được đánh số
    - Xét mức độ mạnh mẽ của chi tiết đó (dựa trên thông số, thành phần của chi tiết)
    
 Đối với các cột có quá nhiều giá trị None, ta có thể loại bỏ các cột đó

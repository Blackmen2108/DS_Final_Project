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

### 4) Thông tin sản phẩm cho dataset ở thư mục data
    Brand and model_Brand : tên nhãn hiệu của công ty sản xuất
    Brand and model_Model : tên model của thiết bị
    Brand and model_Model alias : tên thay thế
    Design_Width : thông tin chiều rộng
    Design_Height : thông tin chiều cao
    Design_Thickness : thông tin bề dày
    Design_Weight : thông tin khối lượng
    Design_Volume : thông tin thể tích
    Design_Colors : thông tin màu sắc
    Design_Body materials : chất liệu sản xuất
    Design_Certification : Thông tin về chuẩn chứng nhận của thiết kế
    SIM card_SIM card type : loại và kích thước của SIM
    SIM card_Number of SIM cards : số lượng SIM
    SIM card_Features : các tính năng về  SIM
    Networks_GSM : mạng điện thoại 1G
    Networks_CDMA : mạng điện thoại 2G - 2.5G
    Networks_CDMA2000 : mạng điện thoại 3G
    Networks_W-CDMA : mạng điện thoại 3G
    Networks_TD-SCDMA : mạng điện thoại 3G
    Networks_UMTS : mạng điện thoại 3G
    Networks_LTE : mạng điện thoại 4G
    Mobile network technologies and bandwidth_Mobile network technologies : công nghệ mạng được sử dụng kèm băng thông
    Operating system_Operating system (OS) : hệ điều hành được sử dụng
    Operating system_User interface (UI) : giao diện được sử dụng
    System on Chip (SoC)_SoC : tên SoC
    System on Chip (SoC)_Process technology : thông tin về công nghệ xử lý 
    System on Chip (SoC)_CPU : CPU
    System on Chip (SoC)_CPU bits : Kích thước bit 
    System on Chip (SoC)_Instruction set : Thông tin tập lệnh bộ xử lý có thể thực hiện
    System on Chip (SoC)_Level 2 cache memory (L2) : Bộ nhớ cache Level 2
    System on Chip (SoC)_CPU cores : Số core CPU
    System on Chip (SoC)_CPU frequency : Tốc độ CPU
    System on Chip (SoC)_GPU : GPU
    System on Chip (SoC)_GPU cores : Số lượng core GPU 
    System on Chip (SoC)_GPU frequency : Tốc độ GPU
    System on Chip (SoC)_RAM capacity : Dung lượng RAM
    System on Chip (SoC)_RAM type : Loại RAM
    System on Chip (SoC)_RAM channels : RAM channel
    System on Chip (SoC)_RAM frequency : Tốc độ RAM
    Storage_Storage : Bộ nhớ
    Memory cards_Types : Loại thẻ nhớ
    Display_Type/technology : Loại / Công nghệ màn hình
    Display_Diagonal size : Kích thước đường chéo
    Display_Width : Chiều rộng
    Display_Height : Chiều cao
    Display_Aspect ratio : Tỉ lệ cạnh
    Display_Resolution : 
    Display_Pixel density : 
    Display_Color depth : 
    Display_Display area : 
    Display_Other features : Các tính năng khác
    Sensors_Sensors : Các sensor tích hợp
    Primary camera_Sensor model : Sensor model
    Primary camera_Sensor type : Loại Sensor
    Primary camera_ISO : Đánh giá ISO
    Primary camera_Aperture : Khẩu độ
    Primary camera_Flash type : Loại đèn Flash
    Primary camera_Image resolution : Độ phân giải hình ảnh
    Primary camera_Video resolution : Độ phân giản video
    Primary camera_Video FPS : số khung hình / giây được hỗ trợ
    Primary camera_Features : Các tính năng khác của video
    Primary camera_Focal length : Focal length
    Secondary camera_Sensor model : Sensor model
    Secondary camera_Sensor type : Loại Sensor
    Secondary camera_ISO : Đánh giá ISO
    Secondary camera_Aperture : Khẩu độ
    Secondary camera_Flash type : Loại đèn Flash
    Secondary camera_Image resolution : Độ phân giải hình ảnh
    Secondary camera_Video resolution : Độ phân giản video
    Secondary camera_Video FPS : số khung hình / giây được hỗ trợ
    Secondary camera_Features : Các tính năng khác của video
    Secondary camera_Focal length : Focal lengthAudio_Speaker : Công nghệ Audio
    Radio_Radio : FM radio
    Tracking/Positioning_Tracking/Positioning : Các dịch vụ theo dõi, định vị
    Wi-Fi_Wi-Fi : Các tiêu chuẩn, loại giao tiếp Wi-Fi
    Bluetooth_Version : Phiên bản Bluetooth
    Bluetooth_Features : Các tính năng Bluetooth
    USB_Connector type : Loại kết nối USB
    USB_Version : Phiên bản kết nối USB
    USB_Features : Các tính khác của kết nối USB
    HDMI_HDMI : Kết nối HDMI
    Headphone jack_Headphone jack : Thông tin cho biết thiết bị có được kết nối với audio jack 3.5 mm không
    Connectivity_Connectivity : Các công nghệ kết nối được hỗ trợ
    Browser_Browser : Chuẩn hỗ trợ của browser
    Audio file formats/codecs_Audio file formats/codecs : Các format audio file được hỗ trợ
    Video file formats/codecs_Video file formats/codecs : Các format video file được hỗ trợ
    Battery_Capacity : Dung lượng Pin
    Battery_Type : Loại Pin
    Battery_2G stand-by time : thời gian sạc đi kết nối 2G liên tục 
    Battery_3G stand-by time : thời gian sạc khi kết nối 3G liên tục
    Battery_Charger output power : 
    Battery_Features : các thuộc tính khác của Pin
    Battery_Quick charge technology : 
    Specific Absorption Rate (SAR)_Head SAR (EU) : SAR rating cho thấy lượng bức xạ người có thể chịu được cho phần đầu theo chuẩn EU
    Specific Absorption Rate (SAR)_Body SAR (EU) : SAR rating cho thấy lượng bức xạ người có thể chịu được cho phần thân theo chuân EU
    Specific Absorption Rate (SAR)_Head SAR (USA) : SAR rating cho thấy lượng bức xạ người có thể chịu được cho phần đầu theo chuẩn USA
    Specific Absorption Rate (SAR)_Body SAR (USA) : SAR rating cho thấy lượng bức xạ người có thể chịu được cho phần thân theo chuẩn USA
    Additional features_Additional features : các tính năng khác 
    Price : giá sản phẩm

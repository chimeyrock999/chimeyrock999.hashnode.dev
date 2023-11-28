---
title: "Tóm tắt cuốn Designing Data-Intensive Applications."
seoTitle: "Tóm tắt cuốn Designing Data-Intensive Applications."
seoDescription: "Tóm tắt cuốn Designing Data-Intensive Applications."
datePublished: Tue Nov 28 2023 09:44:36 GMT+0000 (Coordinated Universal Time)
cuid: clpi5ixb8000008l69akt83na
slug: tom-tat-cuon-designing-data-intensive-applications
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1701153559188/f01b8549-eccb-4b46-a13c-fed3bb40548c.jpeg
ogImage: https://cdn.hashnode.com/res/hashnode/image/upload/v1701164621447/b3a60aac-afad-47b0-80fb-04bea662ec62.jpeg
tags: programming

---

# Abstract

Các ứng dụng ngày nay hiếm khi bị giới hạn bởi CPU, vấn đề lớn hơn nằm ở lượng dữ liệu lớn, độ phức tạp và tốc độ thay đổi của dữ liệu.

Một data-intensive application điển hình sẽ được xây dựng bởi nhiều blocks đáp ứng một số functions nhất định:

* Lưu trữ dữ liệu (databases).
    
* Ghi nhớ kết quả của những thao tác tính toán phức tạp (caches).
    
* Tìm kiếm bằng từ khóa (seach indexes).
    
* Gửi messages giao tiếp bất đồng bộ (stream processing).
    
* Định kỳ xử lý một lượng lớn dữ liệu (batch proccessing).
    

Thực tế có vô số công cụ đáp ứng được những chức năng trên theo những nhu cầu khác nhau và rất khó khăn khi lựa chọn, kết hợp những công cụ này với nhau một cách hiệu quả.

Cuốn sách giới thiệu về các nguyên tắc thiết kế, ví dụ và làm thế nào để sử dụng các công cụ trên để xây dựng một "<mark>data-instensive application</mark>".

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1701157053357/47bcb2c2-d1f8-414f-886f-96ebe5ed7a08.webp align="center")

# Part I. Foundations of Data Systems

## Chapter 1. Reliable, Scalable, and Maintainable Applications

> Chương này chủ yếu giới thiệu về các đặc tính cơ bản như reliable, scalable, maintainable.

Khi thiết kế một data system hoặc một service, chúng ta thường đặt ra một số câu hỏi như: Làm thế nào để chắc chắn dữ liệu duy trì tính chính xác và toàn vẹn, cho dù có vấn đề nội bộ xảy ra? Làm thế nào để bạn cung cấp hiệu suất nhất quán cho người dùng, ngay cả khi một phần của hệ thống bị trục trặc? Làm thế nào để mở rộng quy mô khi tải trọng tăng? API services tốt trông như thế nào?

Có nhiều yếu tố ảnh hưởng đến thiết kế của một hệ thống dữ liệu, bao gồm: kĩ năng và kinh nghiệm của người tham gia, hệ thống kế thừa trước đó, thời gian phát triển hệ thống, những hạn chế về quy định,...

Cuốn sách sẽ chủ yếu tập trung vào các tính chất quan trọng của hầu hết hệ thống phần mềm:

1. **Reliability** (Tính tin cậy): Khả năng hoạt động chính xác (thực hiện đúng các chức năng ở hiệu suất kì vọng) ngay cả khi phải đối mặt với nghịch cảnh (lỗi phần cứng, phần mềm hay thậm chí lỗi thuộc về con người).
    
2. **Scalability** (Khả năng mở rộng): Hệ thống có phương án mở rộng hợp lí trước sự tăng trưởng về khối lượng dữ liệu, lưu lượng truy cập hay mức độ phức tạp.
    
3. **Maintainability** (Tính bảo trì): Theo thời gian, số lượng người làm việc trên cùng hệ thống sẽ tăng lên bao gồm bảo trì, duy trì và mở rộng hệ thống đáp ứng các use cases mới, tất cả họ đều nên có khả năng làm việc một cách hiệu quả trên hệ thống này.
    

### Reliability

Một hệ thống được xem là đáng tin cậy nếu thỏa mãn được các yêu cầu sau:

* Thực hiện các chức năng giống như kì vọng của người dùng.
    
* Hoạt động tốt ngay cả khi người dùng mắc lỗi hoặc sử dụng phần mềm theo cách không mong muốn.
    
* Hiệu năng của nó đủ tốt khi trong hấu hết trường hợp sử dụng (lượng tải và dữ liệu dự kiến trước).
    
* Chống lại những yêu cầu truy cập không được phép.
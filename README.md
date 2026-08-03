# HR Platform

Dự án Java khởi tạo cho nền tảng Quản lý Nhân sự (HR Platform).

## 📁 Cấu trúc Dự án

```text
HR/
├── .gitignore          # Cấu hình Git ignore cho Java & Maven
├── pom.xml             # Maven Project Object Model (Java 17)
├── README.md           # Tài liệu hướng dẫn dự án
└── src/
    ├── main/
    │   └── java/
    │       └── com/
    │           └── hr/
    │               └── Main.java  # Main entry point
    └── test/
        └── java/                  # Thư mục chứa Unit Tests
```

## 🛠 Thư viện & Yêu cầu Hệ thống

- **Java Development Kit (JDK)**: Java 17 trở lên
- **Build Tool**: Apache Maven 3.8+

## 🚀 Hướng dẫn Biên dịch & Khởi chạy

### 1. Biên dịch Dự án

```bash
mvn clean compile
```

### 2. Chạy Ứng dụng

```bash
mvn exec:java -Dexec.mainClass="com.hr.Main"
```

Hoặc biên dịch ra file JAR và chạy:

```bash
mvn clean package
java -jar target/hr-platform-1.0.0-SNAPSHOT.jar
```

### 3. Chạy Unit Tests

```bash
mvn test
```

## 📄 Giấy phép

Dự án được khởi tạo cho nền tảng HR Platform.

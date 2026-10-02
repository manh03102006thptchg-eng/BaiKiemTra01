Câu 1: Phân biệt Value Types và Reference Types 

Value Types (kiểu giá trị): 

Biến lưu trực tiếp giá trị của dữ liệu.  

Thường được lưu trên Stack khi là biến cục bộ.  

Khi gán một biến Value Type cho biến khác, giá trị được sao chép.  

Ví dụ: int, double, bool, struct, enum.  

Reference Types (kiểu tham chiếu): 

Biến lưu địa chỉ/tham chiếu đến đối tượng.  

Đối tượng thường được cấp phát trên Heap.  

Khi gán biến này cho biến khác, tham chiếu được sao chép, nên cả hai có thể cùng trỏ đến một đối tượng.  

Ví dụ: class, object, string, array. 

 

Ví Dụ: 

int a = 10; 

int b = a; 

b = 20; 

// a vẫn bằng 10 

class Student 

{ 

    public string Name; 

} 

Student s1 = new Student(); 

Student s2 = s1; 

s2.Name = "Nam"; 

// s1.Name cũng là "Nam" 

 

Câu 2: Init-only Properties init khác set như thế nào? 

set: 

Cho phép gán giá trị cho thuộc tính bất cứ lúc nào sau khi đối tượng được tạo. 

class Student 

{ 

    public string Name { get; set; } 

} 

Student sv = new Student(); 

sv.Name = "Nam"; 

sv.Name = "Hoàng";   // Được phép 

 

init: 

Chỉ cho phép thiết lập giá trị khi khởi tạo đối tượng.  

Sau khi khởi tạo xong thì không thể thay đổi giá trị đó.  

Được giới thiệu từ C# 9. 

 

class Student 

{ 

    public string Name { get; init; } 

} 

Student sv = new Student { Name = "Nam" }; 

// sv.Name = "Hoàng";    // Lỗi 

 

Câu 3: virtual và override trong tính Đa hình 

virtual: 

Được khai báo ở lớp cha.  

Cho phép lớp con ghi đè (override) phương thức đó. 

class Animal 

{ 

    public virtual void Sound() 

    { 

        Console.WriteLine("Animal sound"); 

    } 

} 

 

override: 

Được khai báo ở lớp con.  

Dùng để thay đổi cách thực hiện phương thức virtual của lớp cha. 

 

class Dog : Animal 

{ 

    public override void Sound() 

    { 

        Console.WriteLine("Gau gau"); 

    } 

} 

Khi sử dụng: 

Animal a = new Dog(); 

a.Sound(); 

Kết quả: 

Gau gau 

 

Câu 4: Tại sao static không truy xuất thông qua Object Instance? 

Thành phần static thuộc về Class, không thuộc về từng Object Instance. 

Ví dụ: 

class Student 

{ 

    public static int Count = 0; 

} 

Count chỉ có một bản sao dùng chung cho cả lớp, không phải mỗi đối tượng một bản sao. 

Do đó phải truy xuất thông qua tên lớp: 

Student.Count++; 

Không truy xuất theo: 

Student sv = new Student(); 

sv.Count++;    // Không được dùng theo cách truy cập instance 

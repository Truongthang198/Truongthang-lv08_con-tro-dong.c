                                              <.><.><.>BÁO CÁO HỌC CON TRỎ ĐỘNG<.><.><.>
#I)CẤP PHÁT VÀ GIẢI PHÓNG BỘ NHỚ ĐỘNG<ul/>
***1)Khái niệm:***<ul/>
**a)Biến động:**<ul/>
 Là các biến được tạo ra lúc chạy chương trình, tùy theo nhu cầu.
 Số biến này hoàn toàn không được xác định từ trước.
 Các biến động không có tên (việc đặt tên thực chất là gán cho nó một địa chỉ xác định).
 
**b)Cách tạo ra biến động và truy nhập đến biến động được tiến hành như sau**<ul/>
<li>Việc tạo ra biến động và xóa nó đi (để thu hồi lại bộ nhớ) được thực hiện nhờ các hàm như malloc() và free() đã có sẵn trong thư viện stdlib.h
<li>Việc truy nhập đến biến động được tiến hành nhờ các biến con trỏ. Các biến con trỏ được định nghĩa như các biến tĩnh ( được khai báo ngay từ đầu trong phần khai báo biến) và được dùng để chứa địa chỉ các biến động
<ul/> VD:
int *p; /* Khai báo biến con trỏ p*/
			p= (int *) malloc(100);/* Tạo biến động*/
<ul/>****2.Cấp phát và giải phóng bộ nhớ động (các hàm thuộc stdlib.h và alloc.h)***
<ul/>**2.1 Cấp phát bộ nhớ động bằng hàm malloc( )**
<ul/>Cú pháp	void *malloc(kiểu _dl   size)
<li>Chức năng:Hàm malloc cấp phát một vùng nhớ có kích thước là size.
<li>size là một giá trị kiểu_dl (là một kiểu dữ liệu định sẵn trong thư viện stdlib.h).
<li>Hàm malloc trả về con trỏ kiểu void chứa địa chỉ ô nhớ đầu của vùng nhớ được cấp phát. Nếu không đủ vùng nhớ để cấp phát hàm trả về giá trị NULL, vì vậy phải kiểm tra giá trị trả về khi sử dụng hàm malloc
<ul/>**2.2 Cấp phát bộ nhớ động bằng hàm calloc**
<ul/>Cú pháp

(datatype *) calloc(n, sizeof(object));

Hàm calloc cấp phát bộ nhớ động cho các kiểu dữ liệu,
trong đó: 
<li>(datatype *) là kiểu con trỏ trỏ tới kiểu dữ liệu datatype.
<li>n là số lượng object thuộc kiểu datatype cần cấp phát bộ nhớ.
<li>datatype có thể là kiểu dữ liệu cơ sở hoặc kiểu dữ liệu mới
<ul/>****2.3 Cấp phát bộ nhớ động bằng hàm relloc***

Cú pháp

(datatype *) realloc(buf _p, newsize);

Hàm có chức năng cấp phát lại bộ nhớ,trong đó:
<li>buf_p là con trỏ đang trỏ đến vùng ô nhớ đã được cấp phát từ trước.
<li>newsize là kích thước mới cần cấp phát, có thể lớn hoặc nhỏ hơn.
<ul/>***2.4 Giải phóng bộ nhớ bằng hàm free***
<ul/>Cú pháp

void free( void *prt)
	<li>Hàm free giải phóng vùng nhớ được trỏ đến bởi con trỏ ptr. 
	<li>Nếu con trỏ ptr = NULL thì hàm free không làm gì cả.
<ul/>****3. Bộ nhớ HEAP và cơ chế tạo biến động***
<ul/>Các biến động do malloc tạo ra được C xếp vào một vùng ô nhớ tự do theo kiểu xếp chồng và được gọi là HEAP ( bộ nhớ cấp phát động). Ngôn ngữ C quản lý HEAP thông qua một con trỏ của HEAP là HEAPPTR. Nó luôn trỏ vào byte tự do đầu tiên của vùng ô nhớ còn tự do của HEAP. Mỗi lần gọi malloc(), con trỏ của HEAP được dịch chuyển về phía đỉnh của vùng ô nhớ tự do một số byte tương ứng với kích thước của biến động mới tạo ra. 
Ngược lại, mỗi khi giải phóng bộ nhớ biến động, bộ nhớ biến động được thu hồi.







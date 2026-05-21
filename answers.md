# Câu A1 — 5 Loại Positioning

Trong CSS có 5 loại position chính gồm: static, relative, absolute, fixed và sticky. Mỗi loại có cách hoạt động khác nhau về vị trí hiển thị, khả năng chiếm chỗ trong flow và hành vi khi cuộn trang.

| Position | Vẫn chiếm chỗ trong flow? | Tham chiếu vị trí | Cuộn theo trang? | Use case |
|---|---|---|---|---|
| static | Có | Vị trí mặc định | Có | Layout thông thường |
| relative | Có | Chính vị trí ban đầu của nó | Có | Dịch chuyển phần tử, làm parent cho absolute |
| absolute | Không | Parent gần nhất có position | Không | Badge, icon góc, popup |
| fixed | Không | Viewport (màn hình trình duyệt) | Không | Header cố định, nút scroll top |
| sticky | Có | Parent/container khi scroll | Ban đầu có, sau đó dính | Sidebar sticky, menu sticky |

Position: static là giá trị mặc định của mọi phần tử HTML. Phần tử sẽ hiển thị theo đúng luồng bình thường của trang web và các thuộc tính top, left, right, bottom sẽ không hoạt động.

Ví dụ:

```css
.box{
    position: static;
    top: 20px;
}
```

# Câu A2 — Flexbox vs Grid

## Trường hợp 1

```css
.container {
    display: flex;
}

.item {
    flex: 1;
}
```
Container sử dụng Flexbox theo chiều ngang mặc định. Thuộc tính flex: 1 giúp các item chia đều chiều rộng của container.

Nếu có 4 items thì bố cục sẽ là:

┌────┬────┬────┬────┐
│ 1  │ 2  │ 3  │ 4  │
└────┴────┴────┴────┘

Tất cả item nằm trên cùng một hàng và có kích thước bằng nhau.

## Trường hợp 2

```css
.container{
    display: flex;
    flex-wrap: wrap;
}

.item{
    width: 45%;
    margin: 2.5%;
}
```
Container sử dụng Flexbox và cho phép xuống dòng bằng flex-wrap: wrap.

Mỗi item có:

width: 45%
margin khoảng 5%

=> tổng chiều rộng khoảng 50%.

Do đó mỗi hàng chứa được 2 item.

Nếu có 6 items thì bố cục sẽ gồm:

3 hàng
2 cột.

Bố cục:
┌──────────┬──────────┐
│    1     │    2     │
├──────────┼──────────┤
│    3     │    4     │
├──────────┼──────────┤
│    5     │    6     │
└──────────┴──────────┘

Nếu không có flex-wrap: wrap thì các item sẽ bị co nhỏ lại trên cùng một hàng.

## Trường hợp 3

```css
.container{
    display: flex;
    justify-content: space-between;
    align-items: center;
}
```
Container sử dụng Flexbox.

Thuộc tính justify-content: space-between giúp các item trải đều theo chiều ngang:

item đầu nằm sát trái
item cuối nằm sát phải
các item còn lại nằm giữa với khoảng cách đều nhau.

Thuộc tính align-items: center giúp căn giữa các item theo chiều dọc.

Nếu có 3 items thì bố cục sẽ là:
┌──────────────────────────────┐
│ 1              2           3 │
└──────────────────────────────┘
Layout này thường được sử dụng cho:

navbar
header
menu điều hướng.

Flexbox rất phù hợp vì đây là layout một chiều theo hàng ngang.

## Trường hợp 4

```css
.container{
    display: grid;
    grid-template-columns: 200px 1fr 200px;
    gap: 20px;
}
```
Container sử dụng CSS Grid với 3 cột:

cột thứ nhất rộng 200px
cột thứ hai chiếm toàn bộ phần không gian còn lại bằng 1fr
cột thứ ba rộng 200px.

Thuộc tính gap: 20px tạo khoảng cách giữa các cột.

Nếu có 3 items thì bố cục sẽ là:
┌────────┬──────────────────┬────────┐
│ Item 1 │      Item 2      │ Item 3 │
└────────┴──────────────────┴────────┘
Layout này thường dùng cho:
sidebar trái
nội dung chính
sidebar phải.

CSS Grid phù hợp vì đây là layout hai chiều với các cột rõ ràng và cố định.

## Trường hợp 5

```css
.container{
    display: grid;
    grid-template-columns: repeat(3, 1fr);
    gap: 10px;
}
```
Container sử dụng CSS Grid.

Thuộc tính repeat(3, 1fr) tạo:

3 cột bằng nhau
mỗi cột chiếm 1 phần bằng nhau của container.

Thuộc tính gap: 10px tạo khoảng cách giữa các item.

Nếu có 7 items thì:

hàng 1 chứa 3 items
hàng 2 chứa 3 items
hàng 3 còn 1 item.

Bố cục sẽ là:
┌────┬────┬────┐
│ 1  │ 2  │ 3  │
├────┼────┼────┤
│ 4  │ 5  │ 6  │
├────┼────┼────┤
│ 7  │    │    │
└────┴────┴────┘
Item số 7 sẽ nằm ở:

hàng thứ 3
cột đầu tiên.

Grid phù hợp cho các layout dạng lưới như:

gallery ảnh
dashboard
product cards
layout sản phẩm thương mại điện tử.

# Câu C1 — Flexbox vs Grid: Khi nào dùng gì?

## 1. Navigation bar ngang (logo + menu + buttons)

Trường hợp này nên dùng Flexbox vì navbar là layout một chiều theo hàng ngang. Flexbox giúp căn chỉnh khoảng cách giữa các phần tử và căn giữa theo chiều dọc dễ dàng.

Ví dụ:

```css
.navbar{
    display: flex;
    justify-content: space-between;
    align-items: center;
}
```
Trong đó:

justify-content: space-between giúp logo nằm bên trái và các button nằm bên phải.
align-items: center giúp các phần tử căn giữa theo chiều dọc.

Flexbox phù hợp vì navbar chỉ cần xử lý theo một chiều ngang.

## 2. Lưới ảnh Instagram (3 cột đều nhau, số ảnh không biết trước)

Trường hợp này nên dùng CSS Grid vì Grid phù hợp với layout dạng lưới hai chiều gồm hàng và cột.

Ví dụ:
```css
.gallery{
    display: grid;
    grid-template-columns: repeat(3, 1fr);
    gap: 10px;
}
```
Trong đó:

repeat(3, 1fr) tạo 3 cột bằng nhau.
gap: 10px tạo khoảng cách giữa các ảnh.

Grid giúp:

bố cục ổn định
tự động xuống hàng
dễ quản lý số lượng ảnh lớn.
## 3. Layout blog: main content + sidebar

Layout blog nên sử dụng CSS Grid kết hợp Flexbox.

Grid dùng cho bố cục chính:
```css
.layout{
    display: grid;
    grid-template-columns: 250px 1fr;
}
```
Trong đó:

sidebar rộng cố định 250px
content chiếm phần không gian còn lại.

Bên trong từng phần có thể dùng Flexbox để căn chỉnh nội dung.

Grid phù hợp vì layout blog là layout hai cột rõ ràng.

## 4. Footer với 4 cột thông tin

Footer nên sử dụng CSS Grid vì cần chia nhiều cột bằng nhau.

Ví dụ:
```css
.footer{
    display: grid;
    grid-template-columns: repeat(4, 1fr);
    gap: 20px;
}
```
Grid giúp:

chia cột dễ dàng
responsive tốt
bố cục rõ ràng hơn Flexbox.
## 5. Card sản phẩm (ảnh trên, text giữa, nút dưới — nút luôn dính đáy)

Card sản phẩm nên dùng Flexbox theo chiều dọc.

Ví dụ:
```css
.card{
    display: flex;
    flex-direction: column;
}

.btn{
    margin-top: auto;
}
```
Trong đó:

flex-direction: column sắp xếp nội dung theo chiều dọc.
margin-top: auto đẩy nút xuống đáy card.

Flexbox phù hợp vì card chỉ cần xử lý layout theo một chiều dọc.

Kết luận
Flexbox phù hợp với layout một chiều.
Grid phù hợp với layout hai chiều.
Trong thực tế thường kết hợp cả Flexbox và Grid để tối ưu giao diện.

# Câu C2 — Debug Flexbox
## Lỗi 1 — Cards không đều chiều cao, nút “Mua” bị lệch

Nguyên nhân

Các card có lượng nội dung khác nhau nên chiều cao mỗi card khác nhau. Vì nút “Mua” không được đẩy xuống đáy card nên vị trí nút bị lệch lên xuống.

Cách sửa

Sử dụng Flexbox theo chiều dọc cho card và dùng margin-top: auto để đẩy nút xuống cuối card.

Code sửa:
```css
.card-container{
    display: flex;
    flex-wrap: wrap;
}

.card{
    width: 30%;
    margin: 1.5%;

    display: flex;
    flex-direction: column;
}

.card img{
    width: 100%;
}

.card .btn{
    padding: 10px;

    margin-top: auto;
}
```
## Lỗi 2 — Muốn items nằm giữa cả ngang lẫn dọc nhưng item vẫn nằm góc trái trên

Nguyên nhân

Container đã dùng Flexbox nhưng chưa có:

+ justify-content
+ align-items

nên item vẫn nằm ở vị trí mặc định là góc trái trên.

Cách sửa:

Thêm:

justify-content: center
align-items: center

Code sửa:
```css
.hero{
    height: 100vh;

    display: flex;

    justify-content: center;

    align-items: center;
}

.hero-content{
    text-align: center;
}
```

## Lỗi 3 — Sidebar bị co lại khi content quá dài

Nguyên nhân

Trong Flexbox, item có thể bị co lại mặc định (flex-shrink: 1). Khi content quá dài, sidebar sẽ bị ép nhỏ lại.

Cách sửa

Thêm:

flex-shrink: 0;

cho sidebar.

Code sửa:
```css
.layout{
    display: flex;
}

.sidebar{
    width: 250px;

    flex-shrink: 0;
}

.content{
    flex: 1;
}
```
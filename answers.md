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

# Câu A2 — Flexbox vs Grid

## Trường hợp 1

```css
.container {
    display: flex;
}

.item {
    flex: 1;
}

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

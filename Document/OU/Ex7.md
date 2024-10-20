# Bài 7 

|[P1](#tạo-project---bố-cục-làm-việc---cấu-trúc-project)|[P2](#thành-phần-scene)|[P3](#tìm-hiểu-về-gameobject)|[P4](#thành-phần-camera)|[P5](#thành-phần-spriterenderer)|[P6](#sử-dụng-tag)|[P7](#sorting-layer-và-order-in-layer)|[P8](#vòng-đời-của-một-gameobject)|[P9](#phương-thức-update-và-đại-lượng-timedeltatime)|[P10](#vector)|[P11](#tìm-hiểu-về-prefab)|[P12](#câu-lệnh-instantiate-và-destroy)|[P13](#component)|
|-|-|-|-|-|-|-|-|-|-|-|-|-|



## Tạo Project - Bố cục làm việc - Cấu trúc Project

- `Tạo Project`: Khi bắt đầu với Unity, bạn có thể tạo một project mới từ Unity Hub. Unity cung cấp nhiều mẫu project khác nhau như 2D, 3D, VR/AR, hay các templates khác tùy thuộc vào nhu cầu.
Bố cục làm việc: Giao diện Unity bao gồm các panel chính:
- `Scene View`: Nơi bạn chỉnh sửa cảnh.
Game View: Hiển thị cách game sẽ được hiển thị khi chạy.
- `Inspector`: Hiển thị thông tin chi tiết của các thành phần (`Components`) của `GameObject`.
- `Hierarchy`: Hiển thị cấu trúc cây của các `GameObject` trong `Scene`.
- `Project`: Hiển thị các tài nguyên (`assets`) trong project của bạn.
- `Cấu trúc Project`: Thư mục `Assets` là nơi chứa các tài nguyên của project, bao gồm `textures`, `scripts`, `materials`, `prefabs` và `models`.

## Thành phần Scene
- `Scene` là một không gian chứa các GameObject trong Unity. Mỗi Scene có thể chứa các yếu tố như nhân vật, môi trường, ánh sáng, camera, và các đối tượng tương tác khác. Bạn có thể lưu, tải và chuyển đổi giữa nhiều Scene khác nhau trong game.

## Tìm hiểu về GameObject
- `GameObject` là đơn vị cơ bản trong Unity. Mọi đối tượng trong game, từ nhân vật, môi trường, camera cho đến UI đều là GameObject. Một GameObject chỉ là một container trống, và sức mạnh của nó đến từ các Component được thêm vào.

## Thành phần Camera
- `Camera` là đối tượng dùng để hiển thị thế giới 2D hoặc 3D trên màn hình. Trong Unity, camera mặc định là camera 3D. Bạn có thể tùy chỉnh góc nhìn, vị trí và nhiều thuộc tính khác của camera để tạo ra góc nhìn phù hợp cho game của mình.

## Thành phần SpriteRenderer
- `SpriteRenderer` là một component được sử dụng trong game 2D để hiển thị hình ảnh (sprites) trên màn hình. Component này chịu trách nhiệm render sprite của GameObject lên màn hình, cho phép bạn đặt hình ảnh như nhân vật, đối tượng, background, v.v.

## Sử dụng Tag
- `Tag` là một cách để gán các nhãn cho GameObject nhằm giúp phân loại chúng. Bạn có thể sử dụng Tags để tìm kiếm hoặc quản lý các đối tượng trong game, ví dụ, gán Tag "Player" cho nhân vật chính hoặc "Enemy" cho kẻ thù.

## Sorting Layer và Order In Layer
- `Sorting Layer`: Trong game 2D, các đối tượng có thể nằm trên các lớp khác nhau để đảm bảo rằng chúng được hiển thị theo thứ tự mong muốn. Các layer này giúp bạn quản lý thứ tự hiển thị của các đối tượng.
Order In Layer: Quyết định thứ tự hiển thị của các đối tượng trong cùng một Sorting Layer. Các giá trị cao hơn sẽ được render trước các giá trị thấp hơn.

## Vòng đời của một GameObject
- Các GameObject trong Unity tuân theo một vòng đời cố định, bao gồm:
    - `Awake()`: Gọi khi GameObject được khởi tạo.
    - `Start()`: Gọi khi GameObject được kích hoạt.
    - `Update()`: Gọi mỗi khung hình để cập nhật logic.
    - `FixedUpdate()`: Gọi định kỳ với tốc độ khung hình cố định, dùng cho vật lý.
    - `LateUpdate()`: Gọi sau Update, thường dùng để đồng bộ camera hoặc các đối tượng khác sau khi logic chính được cập nhật.
    - `OnDestroy()`: Gọi khi GameObject bị hủy.

##  Phương thức Update và đại lượng Time.deltaTime
- `Update()` là phương thức chính được gọi mỗi frame trong game để xử lý các logic liên tục như di chuyển, kiểm tra điều kiện, hay xử lý sự kiện. Để đảm bảo sự mượt mà bất kể tốc độ khung hình, bạn thường sử dụng `Time.deltaTime` để tính toán sự thay đổi theo thời gian (từ frame trước đó).

## Vector
- `Vector` trong Unity được sử dụng để biểu diễn các đại lượng có hướng, như vị trí, vận tốc hay lực. Hai loại vector phổ biến nhất là:
- `Vector2`: Dùng trong không gian 2D (X, Y).
- `Vector3`: Dùng trong không gian 3D (X, Y, Z).


## Tìm hiểu về Prefab
- `Prefab` là một mẫu của GameObject đã được lưu lại để sử dụng lại nhiều lần trong game. Prefab cho phép bạn tạo một đối tượng và lưu nó, sau đó bạn có thể sử dụng lại hoặc instantiate nó ở bất kỳ đâu trong Scene mà không cần tạo lại từ đầu.


## Câu lệnh Instantiate và Destroy
- `Instantiate()`: Được sử dụng để tạo ra một bản sao của GameObject hoặc Prefab trong game.
- `Destroy()`: Được sử dụng để xóa một GameObject khỏi Scene khi nó không còn cần thiết.


## Component
- `Component` là các thành phần giúp GameObject có các thuộc tính và hành vi. Mỗi GameObject có thể chứa nhiều Component như:
    - `Transform`: Quản lý vị trí, xoay, và tỷ lệ của GameObject.
    - `Rigidbody`: Thêm thuộc tính vật lý cho GameObject, cho phép nó tương tác với thế giới vật lý.
    - `Collider`: Giúp GameObject có thể va chạm hoặc phát hiện va chạm với các đối tượng khác.
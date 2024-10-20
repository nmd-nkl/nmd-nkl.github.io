# Bài 8


|[P1](#rigidbody)|[P2](#va-chạm-trong-game-collision-và-trigger)|[P3](#bắt-va-chạm-collision)|[P4](#bắt-va-chạm-trigger)|[P5](#ienumerator)|[P6](#invoke)|[P7](#timescale)|[P8](#giới-thiệu-về-animation)|
|-|-|-|-|-|-|-|-|

## Rigidbody
- `Rigidbody` là một thành phần vật lý trong Unity, được sử dụng để thêm các thuộc tính vật lý như trọng lực, lực va chạm, và sự tương tác vật lý cho GameObject. Khi thêm Rigidbody vào GameObject, đối tượng sẽ bị ảnh hưởng bởi các lực vật lý như trọng lực và va chạm.
- `Mass`: Khối lượng của đối tượng, ảnh hưởng đến mức độ bị tác động bởi lực.
- `Drag`: Lực cản làm chậm đối tượng khi nó di chuyển.
- `Angular Drag`: Lực cản xoay làm chậm sự xoay của đối tượng.
- `Use Gravity`: Cho phép đối tượng chịu tác động của trọng lực.
- `Is Kinematic`: Khi được bật, đối tượng sẽ không bị ảnh hưởng bởi các lực vật lý và chỉ di chuyển khi bạn thay đổi các thuộc tính thủ công.

## Va chạm trong game (Collision và Trigger)
- `Collision`: Là sự va chạm vật lý giữa các GameObject có Rigidbody và Collider. Unity sẽ xử lý các tương tác vật lý giữa các đối tượng này và có thể bắt các sự kiện để xử lý thêm.
-`Trigger`: Là loại Collider không tạo ra va chạm vật lý mà chỉ phát hiện khi một đối tượng khác đi vào vùng của nó. Trigger thường dùng để kích hoạt các sự kiện như mở cửa, bật hiệu ứng hoặc thay đổi trạng thái game.

## Bắt va chạm Collision
- `Collision Detection`: Khi hai đối tượng có Collider và ít nhất một trong số đó có Rigidbody, Unity sẽ tự động bắt sự va chạm. Để bắt sự kiện va chạm, bạn có thể sử dụng các phương thức sau:
    - `OnCollisionEnter()`: Được gọi khi GameObject bắt đầu va chạm với đối tượng khác.
    - `OnCollisionStay()`: Được gọi liên tục khi GameObject vẫn còn va chạm với đối tượng khác.
    - `OnCollisionExit()`: Được gọi khi GameObject dừng va chạm với đối tượng khác.


```C#
void OnCollisionEnter(Collision collision) {
    Debug.Log("Va chạm với: " + collision.gameObject.name);
}
```


## Bắt va chạm Trigger
- Khi bạn sử dụng `Collider` ở chế độ `Trigger` (bật checkbox "`Is Trigger`"), Unity sẽ không xử lý va chạm vật lý mà sẽ chỉ phát hiện khi một đối tượng khác đi vào vùng Trigger. Để bắt sự kiện Trigger, bạn sử dụng các phương thức:
    - `OnTriggerEnter()`: Được gọi khi một GameObject đi vào vùng Trigger.
    - `OnTriggerStay()`: Được gọi liên tục khi một GameObject ở trong vùng Trigger.
    - `OnTriggerExit()`: Được gọi khi một GameObject rời khỏi vùng Trigger.

```C#
void OnTriggerEnter(Collider other) {
    Debug.Log("Đối tượng đi vào Trigger: " + other.gameObject.name);
}
```


## IEnumerator
- `IEnumerator` là một giao diện trong C# được sử dụng để tạo ra các Coroutines trong Unity. Coroutines cho phép bạn tạm dừng quá trình thực thi của một đoạn code trong một khoảng thời gian mà không cần chặn toàn bộ game. Điều này rất hữu ích khi bạn cần thực hiện các tác vụ theo thời gian như delay, chuyển cảnh, hoặc chờ hiệu ứng hoàn thành.

```C#
IEnumerator DelayExample() {
    Debug.Log("Bắt đầu");
    yield return new WaitForSeconds(2); // Dừng 2 giây
    Debug.Log("Kết thúc sau 2 giây");
}
```


## Invoke
- `Invoke` là một phương thức trong Unity giúp bạn gọi một hàm sau một khoảng thời gian delay mà không cần phải sử dụng Coroutines. Nó rất đơn giản và trực tiếp khi bạn chỉ cần thực hiện một hành động duy nhất sau một thời gian nhất định.


```C#
void Start() {
    Invoke("MyFunction", 3f); // Gọi MyFunction sau 3 giây
}
void MyFunction() {
    Debug.Log("Được gọi sau 3 giây");
}
```



## TimeScale
- `Time.timeScale` là một thuộc tính cho phép bạn điều chỉnh tốc độ thời gian của game. Giá trị mặc định là 1, nghĩa là thời gian chạy bình thường. Bạn có thể thay đổi giá trị này để tăng tốc, giảm tốc hoặc tạm dừng game.

```C#
Time.timeScale = 0; để tạm dừng game.
Time.timeScale = 0.5f; để giảm tốc độ game xuống một nửa.


void PauseGame() {
    Time.timeScale = 0; // Tạm dừng game
}

void ResumeGame() {
    Time.timeScale = 1; // Khôi phục tốc độ bình thường
}
```



## Giới thiệu về Animation
- `Animation` là một phần quan trọng trong việc tạo ra trải nghiệm trực quan và sống động cho người chơi. Unity hỗ trợ hệ thống Animator để quản lý và điều khiển các animation. Bạn có thể tạo các trạng thái animation khác nhau và liên kết chúng với các điều kiện để chuyển đổi giữa các trạng thái.
- Các thành phần chính của hệ thống Animation:

    - `Animator Controller`: Điều khiển các trạng thái animation và chuyển đổi giữa chúng.
    - `Animation Clip`: Là các đoạn animation được tạo ra hoặc nhập vào Unity từ các công cụ như Blender, Maya hoặc phần mềm 2D.
    - `Parameter`: Các biến được sử dụng để điều khiển việc chuyển đổi giữa các trạng thái (ví dụ: bool, float, trigger).

- Ví dụ: Bạn có thể sử dụng trigger để chuyển đổi từ trạng thái đứng yên sang chạy khi người chơi nhấn phím di chuyển:

```C# 
Animator animator = GetComponent<Animator>();
animator.SetTrigger("Run");
```
# Chat App - Roadmap Học Tập C++

## 📝 Mô Tả Dự Án

Đây là một **ứng dụng chat desktop** được xây dựng bằng **C** sử dụng SDL2. Mục đích của dự án này là giúp bạn học C++ bằng cách **port từng component một** từ C sang C++, từ cơ bản đến nâng cao.

### Tính năng chính:
- 👥 **Giao diện người dùng desktop** - Xây dựng với SDL2
- 🔗 **Kết nối mạng TCP** - Gửi/nhận tin nhắn qua socket
- 📬 **Quản lý danh sách tin nhắn** - Hiển thị và cuộn tin nhắn
- ⌨️ **Hộp nhập liệu interactive** - Con trỏ nhấp nháy, chọn văn bản
- 🌍 **Hỗ trợ UTF-8** - Ký tự Unicode đa ngôn ngữ
- 🖥️ **Server chat** - Xử lý nhiều clients đồng thời (multi-threading)

## 🛠️ Công Nghệ & Khái Niệm Sẽ Học
- **Ngôn ngữ**: C (nguyên bản), C++17 (port)
- **GUI**: SDL2 + SDL2_ttf
- **Networking**: Socket (TCP)
- **Threading**: pthread (C) / std::thread (C++)
- **Build**: CMake

## 📚 Roadmap Học Tập Chi Tiết

### ✅ Phase 0: Chuẩn Bị & Hiểu Dự Án Gốc (C)
**Mục tiêu**: Hiểu rõ từng component trong dự án C gốc trước khi port sang C++

#### 📖 Kiến thức cần học:
- C struct vs C++ class
- Memory management (malloc/free vs new/delete)
- File organization (.h files và .c files)
- Compilation & linking

#### 📝 Các file cần tìm hiểu:

| File | Chức năng | Độ khó |
|------|----------|--------|
| **main.c** | Entry point, khởi tạo app | ⭐ Rất dễ |
| **app.h/app.c** | Struct app_t, vòng lặp chính | ⭐⭐ Dễ |
| **message_listdef.h** | Định nghĩa struct message | ⭐ Rất dễ |
| **message_list.h/c** | Quản lý danh sách tin nhắn | ⭐⭐ Dễ |
| **inputboxdef.h** | Định nghĩa struct inputbox | ⭐⭐ Dễ |
| **inputbox.h/c** | Xử lý input từ bàn phím | ⭐⭐⭐ Trung bình |
| **chatsock_def.h** | Định nghĩa struct socket | ⭐ Rất dễ |
| **chatsock.h/c** | Kết nối & gửi/nhận dữ liệu | ⭐⭐⭐ Trung bình |
| **chatsock_list.h/c** | Quản lý danh sách socket | ⭐⭐ Dễ |
| **chatserver/chatserver.c** | Server xử lý nhiều clients | ⭐⭐⭐⭐ Khó |

#### ✍️ Công việc:
- [ ] Đọc từng file C gốc, hiểu flow chương trình
- [ ] Vẽ diagram kiến trúc dự án
- [ ] Hiểu các function chính & mục đích của chúng
- [ ] Compile & chạy dự án C gốc để hiểu cách hoạt động

---

### ⭐ Phase 1: Chuẩn Bị Môi Trường & Thiết Lập Project C++

**Mục tiêu**: Tạo cấu trúc dự án C++ và cấu hình build system

#### 💡 Khái niệm C++ cần học:
- C++ project structure best practices
- CMake build system
- Header files & source files organization
- Includes & include guards

#### ✍️ Công việc:
- [ ] Tạo thư mục: `src/`, `include/`, `build/`, `cmake/`
- [ ] Cài đặt SDL2 & SDL2_ttf
- [ ] Tạo CMakeLists.txt cơ bản
- [ ] Tạo first C++ program: `src/main.cpp`
- [ ] Compile thành công chương trình Hello World

#### 📌 Output mong đợi:
```
cpp-chatapp/
├── src/
│   └── main.cpp
├── include/
├── CMakeLists.txt
└── README.md
```

---

### 🟡 Phase 2: Học SDL2 Cơ Bản & Rendering

**Mục tiêu**: Understand SDL2 basics trước khi dùng cho chat app

#### 💡 Khái niệm cần học:
- SDL2 window & renderer
- SDL2 event handling (mouse, keyboard)
- Drawing shapes & text (SDL_ttf)
- Color management (SDL_Color)
- Screen refresh & FPS control

#### ✍️ Công việc:
- [ ] Tạo class `Window` để khởi tạo SDL window
- [ ] Implement `Window::init()`, `Window::destroy()`
- [ ] Tạo class `Renderer` để handle drawing
- [ ] Vẽ hình chữ nhật, text, shapes cơ bản
- [ ] Implement event loop (xử lý quit event)
- [ ] Test rendering text với SDL_ttf

#### 📌 Output mong đợi:
- Cửa sổ SDL hiển thị được
- Có thể vẽ hình, text lên cửa sổ
- Event handling hoạt động (close window)

---

### 🟢 Phase 3: Tạo Classes Cơ Bản & Data Structures

**Mục tiêu**: Port các struct từ C sang C++ classes

#### 💡 Khái niệm cần học:
- C++ classes & OOP (encapsulation, getters/setters)
- Constructors & destructors
- Const correctness
- `std::string` thay cho `char*`
- `std::vector<T>` thay cho dynamic arrays
- Smart pointers (`std::unique_ptr`, `std::shared_ptr`)

#### ✍️ Công việc:

**3.1 - Message Class**
- [ ] Tạo class `Message` (từ message_t)
  - Attributes: text, color, position, padding
  - Methods: getters, setters, render()
- [ ] Sử dụng `std::string` cho text
- [ ] Implement constructor & destructor
- [ ] Test: tạo message object & in ra console

**3.2 - InputBox Class**
- [ ] Tạo class `InputBox` (từ inputbox_t)
  - Attributes: input text, cursor position, selection
  - Methods: addChar(), removeChar(), render(), getText()
- [ ] Sử dụng `std::string` cho input buffer
- [ ] Implement basic keyboard input
- [ ] Test: nhập text và hiển thị lên màn hình

**3.3 - MessageList Class**
- [ ] Tạo class `MessageList` (từ message_list_t)
  - Use `std::vector<Message>` để lưu messages
  - Methods: addMessage(), getMessages(), clear()
- [ ] Implement scrolling logic
- [ ] Test: thêm nhiều messages & scroll qua chúng

#### 📌 Output mong đợi:
- 3 classes hoạt động độc lập
- Có thể tạo & quản lý objects
- Memory được quản lý tự động

---

### 🔵 Phase 4: Làm Việc với SDL2 Event Handling

**Mục tiêu**: Xử lý input từ người dùng một cách toàn diện

#### 💡 Khái niệm cần học:
- SDL event system (SDL_Event)
- Keyboard events & key codes
- Mouse events (motion, clicks)
- Text input events (Unicode/UTF-8)
- Event queue processing

#### ✍️ Công việc:
- [ ] Tạo class `EventHandler`
- [ ] Implement keyboard event handling
  - Detect ASCII characters
  - Detect special keys (Enter, Backspace, Delete)
  - Detect modifiers (Shift, Ctrl)
- [ ] Implement UTF-8 text input
  - Sử dụng SDL_TextInputEvent
  - Handle multi-byte UTF-8 characters
- [ ] Implement mouse event handling
  - Detect clicks
  - Track mouse position
- [ ] Connect events đến InputBox class
- [ ] Test: nhập text từ bàn phím, thấy nó update trên màn hình

#### 📌 Output mong đợi:
- Có thể nhập text từ bàn phím
- Hỗ trợ UTF-8 (tiếng Việt, emoji)
- Keyboard events được xử lý đúng cách

---

### 🔶 Phase 5: Tạo Main App Class & Intergrate Components

**Mục tiêu**: Gộp tất cả components lại thành một ứng dụng hoàn chỉnh

#### 💡 Khái niệm cần học:
- Composition & dependency injection
- Main application loop
- Component lifecycle management
- State management

#### ✍️ Công việc:
- [ ] Tạo class `App` (từ app_t)
  - Composition: Window, Renderer, EventHandler, InputBox, MessageList
  - Method: `run()` - main application loop
  - Method: `handleEvents()`, `update()`, `render()`
- [ ] Implement main loop: event → update → render
- [ ] Connect InputBox để nhập tin nhắn
- [ ] Display messages trong MessageList
- [ ] Implement scroll functionality
- [ ] Test: ứng dụng hoạt động với UI đầy đủ

#### 📌 Output mong đợi:
- GUI chat cơ bản hoạt động
- Có thể nhập text & thêm messages
- Có thể scroll qua messages
- Ứng dụng responds đến input

---

### 🟣 Phase 6: Networking & Socket Communication

**Mục tiêu**: Bật khả năng gửi/nhận tin nhắn qua mạng

#### 💡 Khái niệm cần học:
- Socket programming (TCP/IP)
- Client-server model
- Asynchronous/non-blocking sockets
- Error handling trong networking
- Data serialization (gửi/nhận data)

#### ✍️ Công việc:

**6.1 - ChatSocket Class**
- [ ] Tạo class `ChatSocket` (từ chatsock_t)
  - Methods: connect(), send(), recv(), close()
  - Handle socket creation & destruction
- [ ] Implement connection error handling
- [ ] Test: connect đến server giả (netcat)

**6.2 - Non-blocking Socket**
- [ ] Convert socket sang non-blocking mode
- [ ] Implement `isDataAvailable()` check
- [ ] Implement async `recv()` không block main loop
- [ ] Test: data được nhận mà không lag UI

**6.3 - Message Protocol**
- [ ] Define message format (serialize/deserialize)
  - Format: `[sender_name]:[message_content]`
- [ ] Implement packing/unpacking messages
- [ ] Test: gửi & nhận messages từ socket

#### 📌 Output mong đợi:
- Có thể connect đến server
- Có thể gửi & nhận dữ liệu
- Non-blocking socket không ảnh hưởng UI

---

### 🟥 Phase 7: Multi-threading & Thread Safety

**Mục tiêu**: Implement multi-threading cho concurrent operations

#### 💡 Khái niệm cần học:
- `std::thread` (C++ standard threading)
- Mutex & locks (`std::mutex`, `std::lock_guard`)
- Thread safety & race conditions
- Producer-consumer pattern
- Thread synchronization

#### ✍️ Công việc:
- [ ] Tạo `ReceiveThread` - thread để nhận messages từ socket
  - Chạy background, continuously nhận data
  - Use mutex để protect shared data
- [ ] Tạo receive buffer (message queue)
  - Use `std::deque<std::string>` + mutex
- [ ] Update App::update() để process received messages
- [ ] Implement thread-safe message queue
- [ ] Test: messages được nhận từ server mà không crash

#### 📌 Output mong đợi:
- Background thread nhận messages
- Không có race conditions
- UI responsive ở mọi lúc

---

### 🟫 Phase 8: Chat Server (Multi-client Handling)

**Mục tiêu**: Tạo server để handle nhiều clients

#### 💡 Khái niệm cần học:
- Server socket (listen, accept)
- Client connection management
- Broadcasting messages
- Thread per client model
- Server shutdown gracefully

#### ✍️ Công việc:
- [ ] Tạo class `ChatServer`
  - Method: `start()`, `stop()`
  - Method: `acceptConnections()` (blocking hoặc threading)
- [ ] Implement client connection handling
  - Each client in separate thread
  - Store client list
- [ ] Implement message broadcasting
  - One client sends → all clients receive
- [ ] Implement client list management
  - Add client on connect
  - Remove client on disconnect
- [ ] Test: chạy server & kết nối multiple clients

#### 📌 Output mong đợi:
- Server chạy được
- Multiple clients có thể connect
- Messages được broadcast cho tất cả clients

---

### 🏁 Phase 9: Polish & Optimization

**Mục tiêu**: Cải tiến code quality, performance, & user experience

#### 💡 Khái niệm cần học:
- Memory profiling & optimization
- Performance optimization
- Logging & debugging
- Error handling & user-friendly messages
- Code refactoring

#### ✍️ Công việc:
- [ ] Add logging system (file & console)
- [ ] Implement proper error handling & exceptions
- [ ] Add validation & input sanitization
- [ ] Optimize message rendering (cache fonts, etc)
- [ ] Add configuration file support (JSON/INI)
- [ ] Memory profiling & leak detection
- [ ] Code cleanup & refactoring
- [ ] Write documentation & code comments
- [ ] Create build instructions

#### 📌 Output mong đợi:
- Ứng dụng ổn định & responsive
- Proper error messages
- Well-documented code
- Can build & run easily

---

### 🎁 Phase 10: Optional Enhancements (Khi đã master)

#### Tính năng add-ons:
- [ ] User authentication & login
- [ ] Save message history to file
- [ ] Private messaging (username support)
- [ ] File transfer
- [ ] Emoji support
- [ ] Dark/Light themes
- [ ] User avatars & profiles
- [ ] Typing indicator
- [ ] Message persistence (SQLite)

---

## 💡 Hướng Dẫn Học Tập

### Quy tắc vàng:
1. **Tuần tự từng phase** - đừng bỏ qua phase nào
2. **Hiểu trước khi code** - đọc & hiểu code C gốc trước
3. **Commit thường xuyên** - sau mỗi feature hoàn thành
4. **Test liên tục** - không chờ đến cuối
5. **Debug kỹ lưỡng** - đừng để bugs tích lũy

### Kỹ năng C++ cần biết ở mỗi phase:

| Phase | Kỹ năng C++ chính |
|-------|-------------------|
| 1 | CMake, basic setup |
| 2 | Basic classes, constructors |
| 3 | std::string, std::vector, smart pointers |
| 4 | Methods, const correctness |
| 5 | Composition, dependency |
| 6 | Error handling, basic networking |
| 7 | std::thread, std::mutex, synchronization |
| 8 | Advanced threading, server design |
| 9 | Exception handling, logging |
| 10 | Design patterns, advanced C++ |

---

## 📚 Tài Liệu Tham Khảo & Resources

### C++ Learning:
- **cppreference.com** - STL & C++ reference
- **learncpp.com** - Comprehensive C++ tutorial
- **Effective Modern C++** - Scott Meyers (book)
- **C++ Primer** - Lippman et al. (book)

### SDL2 & Graphics:
- **SDL2 Official Docs**: https://wiki.libsdl.org/
- **SDL2 Tutorials**: https://lazyfoo.net/tutorials/SDL/
- **Real-Time Rendering** - basics for graphics

### Networking:
- **Beej's Network Programming Guide**
- **Linux Man Pages**: `man socket`, `man connect`, etc
- **TCP/IP concepts**

### Tools & Debugging:
- **GDB** - GNU Debugger
- **Valgrind** - Memory profiling
- **CMake** - Build system
- **Git** - Version control

---

## 🚀 Getting Started

```bash
# Clone or navigate to project
cd d:\Project\Cpp-chat

# Create build directory
mkdir build && cd build

# Generate build files with CMake
cmake ..

# Build
cmake --build .

# Run
./chatapp        # Client
./chatserver     # Server (separate terminal)
```

---

## 📊 Progress Tracking

Lần cập nhật: 30/3/2026

**Current Phase**: ⭐ Phase 0 (Understanding C code)

Để track progress, tạo file `PROGRESS.md`:
```
- [x] Phase 0: Understand original C code
- [ ] Phase 1: Setup C++ project
- [ ] Phase 2: Learn SDL2
- [ ] Phase 3: Create basic classes
... (continue for other phases)
```
```

---

**Để áp dụng nội dung này**, bạn cần:
1. Mở file README.md 
2. Xóa nội dung "Hello world."
3. Dán nội dung trên vào file

Danh sách To-Do này sẽ giúp bạn có một kế hoạch rõ ràng để port dự án từng bước! 🎯
# STM32_BTL

Hệ thống giám sát nhiệt độ và điều khiển quạt tự động — **STM32F103C8T6 + FreeRTOS**
(Keil MDK, thư viện Standard Peripheral).

## Cấu trúc thư mục

```
STM32_BTL/
├── bsp/            # Board support & Pin mapping
├── hal/            # Drivers ngoại vi (Hardware Abstraction Layer)
│   ├── inc/        # hal_gpio.h, hal_uart.h, hal_i2c.h...
│   └── src/        # hal_gpio.c, hal_uart.c, hal_i2c.c...
├── middlewares/    # FreeRTOS source (Kernel, Port, Heap)
├── app/            # FreeRTOS Tasks & IPC
│   ├── inc/        # task_sensor.h, task_display.h, app_ipc.h, app_cfg.h...
│   └── src/        # task_sensor.c, task_display.c, app_ipc.c...
├── main.c          # Init hardware, tạo task, vTaskStartScheduler()
├── .gitignore
└── README.md
```

## Chiến lược nhánh

- `main`: code chạy thật trên kit, ổn định. Cấm commit trực tiếp.
- `develop`: nhánh tích hợp chính. Tất cả nhánh con tạo từ đây và merge về đây.
- `feature/<tên-task>`: nhánh làm việc riêng của từng cá nhân.
- `integration/<phiên-bản>`: nhánh ghép nối hệ thống trước khi release.

## Quy tắc commit

- `feat(task-xxx)`: thêm chức năng task hoặc IPC mới.
- `fix(rtos)`: sửa lỗi stack, priority, deadlock hoặc lỗi HAL driver.
- `refactor(...)`: tối ưu hóa cấu trúc code.

Không commit thư mục `build/`, `Debug/`, `Release/` và file tạm của IDE.

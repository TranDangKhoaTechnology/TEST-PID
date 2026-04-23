# PID SPEED UART Studio

App desktop Python để test mode `PID SPEED` điều khiển bằng `UART` theo khung 3 byte:

- `Byte 1`: bit 7 là chiều quay, 7 bit còn lại là địa chỉ `1..127`
- `Byte 2`: tốc độ `0..255`
- `Byte 3`: luôn luôn là `0xFF`

Ví dụ:

- Thuận, address `1`, speed `150` -> `0x81 0x96 0xFF`
- Nghịch, address `1`, speed `50` -> `0x01 0x32 0xFF`

## Chạy app

```powershell
python pid_uart_tester.py
```

## Yêu cầu

- Python 3.10+
- `pyserial`

Nếu máy chưa có `pyserial`:

```powershell
pip install pyserial
```

## Tính năng

- Quét và kết nối cổng COM
- Chọn baudrate
- Chỉnh địa chỉ, tốc độ, chiều quay
- Gửi 1 lần
- Gửi liên tục theo chu kỳ ms
- Gửi trong `T ms` rồi tự dừng
- Preview frame hex trực tiếp
- Log hoạt động

## Lưu ý driver

Nếu driver đang ở mode `PID SPEED` điều khiển bằng `UART`, có thể driver sẽ không kết nối lại với máy tính. Muốn reconnect, kéo chân `Dir` xuống `GND` rồi thử lại.

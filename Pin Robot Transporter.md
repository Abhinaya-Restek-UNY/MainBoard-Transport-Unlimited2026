# Pin Robot Transporter

Repositori ini berisi dokumentasi konfigurasi pin (pinout) untuk sistem kelistrikan dan kontrol Robot Transporter. Arsitektur robot ini menggunakan sistem dual-microcontroller, yaitu ESP32 DevKit V1 (sebagai pengolah data utama/sensor) dan STM32 Blue Pill (didedikasikan khusus untuk kontrol aktuator motor).

---

## 1. Komunikasi Serial (UART)
Jalur komunikasi antara ESP32 dan STM32 menggunakan koneksi UART. Pastikan kabel disilang (RX ke TX, dan TX ke RX) serta kedua board memiliki jalur GND (Ground) yang sama.

| Modul Kelistrikan | Pin RX | Pin TX | Keterangan |
| :--- | :---: | :---: | :--- |
| **ESP32 Devkit V1** | 16 (RX2) | 17 (TX2) | Menggunakan jalur UART2 |
| **STM32 Blue Pill** | PA3 (RX2) | PA2 (TX2) | Menggunakan jalur USART2 |

---

## 2. Motor Driver (STM32 Blue Pill)
Konfigurasi 6 buah Motor DC (M1 - M6) seluruhnya ditangani oleh STM32 untuk mendapatkan sinyal PWM dari Hardware Timer yang stabil.

*F = Forward (Maju), B = Backward (Mundur).*

| Komponen | Arah (Pin Driver) | Pin STM32 | Hardware Timer |
| :--- | :--- | :---: | :--- |
| **Motor 1 (M1)** | F<br>B | PB8<br>PB9 | TIM4_CH3<br>TIM4_CH4 |
| **Motor 2 (M2)** | F<br>B | PB6<br>PB7 | TIM4_CH1<br>TIM4_CH2 |
| **Motor 3 (M3)** | F<br>B | PA10<br>PA11 | TIM1_CH3<br>TIM1_CH4 |
| **Motor 4 (M4)** | F<br>B | PA8<br>PA9 | TIM1_CH1<br>TIM1_CH2 |
| **Motor 5 (M5)** | F<br>B | PA7<br>PA6 | TIM3_CH2<br>TIM3_CH1 |
| **Motor 6 (M6)** | F<br>B | PB1<br>PB0 | TIM3_CH4<br>TIM3_CH3 |

---

## 3. Servo & Aktuator (ESP32 Devkit V1)
Konfigurasi pin untuk penggerak servo dan sistem pneumatik yang diatur langsung oleh ESP32.

| Komponen | Label Pin | Pin ESP32 |
| :--- | :--- | :--- |
| **Servo 1 (S1)** | Signal (S) | 14 |
| **Servo 2 (S2)** | Signal (S) | 27 |
| **Servo 3 (S3)** | Signal (S) | 26 |
| **Servo 4 (S4)** | Signal (S) | 25 |
| **Servo 5 (S5)** | Signal (S) | 33 |
| **Pneumatik** | Selenoid | 5 |

---

## 4. Sensor & Pembacaan Data (ESP32 Devkit V1)
Sistem pembacaan sensor menggunakan ESP32. Sensor berbasis komunikasi I2C berbagi jalur yang sama (SDA: 21, SCL: 22).

| Komponen | Fungsi / Jalur | Pin ESP32 | Keterangan |
| :--- | :--- | :--- | :--- |
| **MPU 6050** | SDA<br>SCL<br>AD0<br>INT | 21<br>22<br>19<br>18 | Sensor IMU (Gyro/Accelerometer) |
| **BNO085** | SDA<br>SCL<br>INT<br>RST | 21<br>22<br>19<br>18 | Sensor Orientasi Absolut |
| **VL53L0X** | SDA<br>SCL<br>GPIO1 | 21<br>22<br>23 | Sensor Jarak (Time-of-Flight) |
| **ID-BAT** | OUT | 13 | Indikator / Pembacaan Baterai |
| **Current Sensor** | OUT | 35 | Pembacaan Arus (Input Analog) |
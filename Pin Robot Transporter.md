# Pin Robot Transporter

---

## 1. Komunikasi Serial (UART)

| Modul Kelistrikan | Pin RX | Pin TX | Keterangan |
| :--- | :---: | :---: | :--- |
| **ESP32 Devkit V1** | 16 (RX2) | 17 (TX2) | Menggunakan jalur UART2 |
| **STM32 Blue Pill** | PA3 (RX2) | PA2 (TX2) | Menggunakan jalur USART2 |

---

## 2. Motor Driver (STM32 Blue Pill)

| Komponen | Arah (Pin Driver) | Pin STM32 | Hardware Timer |
| :--- | :--- | :---: | :--- |
| **Motor 1 (M1)** | F<br>B | PB8<br>PB9 | TIM4_CH3<br>TIM4_CH4 |
| **Motor 2 (M2)** | F<br>B | PB6<br>PB7 | TIM4_CH1<br>TIM4_CH2 |
| **Motor 3 (M3)** | F<br>B | PA10<br>PA11 | TIM1_CH3<br>TIM1_CH4 |
| **Motor 4 (M4)** | F<br>B | PA8<br>PA9 | TIM1_CH1<br>TIM1_CH2 |
| **Motor 5 (M5)** | F<br>B | PA7<br>PA6 | TIM3_CH2<br>TIM3_CH1 |
| **Motor 6 (M6)** | F<br>B | PB1<br>PB0 | TIM3_CH4<br>TIM3_CH3 |

---

## 3. Servo 

| Komponen | Label Pin | Pin ESP32 |
| :--- | :--- | :--- |
| **Servo 1 (S1)** | Signal (S) | 14 |
| **Servo 2 (S2)** | Signal (S) | 27 |
| **Servo 3 (S3)** | Signal (S) | 26 |
| **Servo 4 (S4)** | Signal (S) | 25 |
| **Servo 5 (S5)** | Signal (S) | 33 |
| **Pneumatik** | Selenoid | 5 |

---

## 4. Sensor 

| Komponen | Fungsi / Jalur | Pin ESP32 | Keterangan |
| :--- | :--- | :--- | :--- |
| **MPU 6050** | SDA<br>SCL<br>AD0<br>INT | 21<br>22<br>19<br>18 | Sensor IMU (Gyro/Accelerometer) |
| **BNO085** | SDA<br>SCL<br>INT<br>RST | 21<br>22<br>19<br>18 | Sensor Orientasi Absolut |
| **VL53L0X** | SDA<br>SCL<br>GPIO1 | 21<br>22<br>23 | Sensor Jarak (Time-of-Flight) |
| **ID-BAT** | OUT | 13 | Indikator / Pembacaan Baterai |
| **Current Sensor** | OUT | 35 | Pembacaan Arus (Input Analog) |

## 5. selonoid

| Komponen | Label Pin | Pin ESP32 |
| :--- | :--- | :--- |
| **Pneumatik** | Selenoid | 5 |

---
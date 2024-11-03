## IOT_carcar

##### 2024 產業新尖兵-AI物聯網大數據  

組長：黃柏凱  
組員：徐敏容、簡言蓁、林兪丞、馮棋森  

## 簡介
在Arduino程式碼中，相機影像傳輸和馬達控制 使用的是不同的 WebSocket 連接和資料流，並不是共用同一個資料流。這些功能分別透過兩個 WebSocket 連接來傳輸不同類型的資料：
### 1.相機影像傳輸：
相機影像資料是透過 camera_client 這個 WebSocket 連接來傳輸的。
camera_client 連接到 camera_server_host 和 camera_server_port，指定用於相機影像的傳輸。
在 loop() 函數中，相機影像資料被擷取後以二進位方式 (sendBinary) 傳送到伺服器。
### 2.馬達控制：
馬達控制指令則是透過另一個 WebSocket 連接 control_client 傳送。
control_client 連接到 control_server_host 和 control_server_port，用於接收馬達控制指令。
當伺服器發送控制訊息（如 "up", "down", "left", "right" 等）時，control_client 會收到文字訊息並根據訊息執行相應的馬達控制指令。
## 為何使用兩個 WebSocket 連接
分開使用兩個 WebSocket 連接可以提高系統的穩定性和清晰度：
‧分開資料流：影像資料（相機）和控制指令（馬達控制）有不同的數據需求，影像傳輸是大量的二進位資料，控制指令則是簡單的文字訊息。
‧降低延遲：控制指令是即時性的，可能需要更快速的響應，將影像和控制指令分開可以避免影像傳輸佔用頻寬影響指令的傳輸。
‧便於管理和維護：分開連接讓每個 WebSocket 負責特定的任務，便於進行錯誤排除和管理。

https://www.youtube.com/watch?v=HCwjJNgR1QY

https://github.com/user-attachments/assets/57641af9-c26c-4a5c-90f1-13bc8e73f7a2

![image](https://github.com/rong142/IOT_carcar/blob/main/img%26video/image.png)

![image](https://github.com/rong142/IOT_carcar/blob/main/img%26video/introduce_6.png)

![image](https://github.com/rong142/IOT_carcar/blob/main/img%26video/introduce_5.png)

![image](https://github.com/rong142/IOT_carcar/blob/main/img%26video/introduce_1.png)

![image](https://github.com/rong142/IOT_carcar/blob/main/img%26video/introduce_2.png)

![image](https://github.com/rong142/IOT_carcar/blob/main/img%26video/introduce_3.png)

![image](https://github.com/rong142/IOT_carcar/blob/main/img%26video/introduce_4.png)


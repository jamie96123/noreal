noreal/
├── .github/                              # CI/CD 自動化工作流程
│   └── workflows/
│       └── build.yml                     # 程式碼推送時自動編譯驗證
├── Core/                                 # 核心應用與主要周邊配置
│   ├── Inc/                              # 核心標頭檔
│   │   ├── main.h                        # 系統主要巨集、腳位別名定義
│   │   ├── stm32f4xx_hal_conf.h          # STM32 HAL 模組啟用開關配置
│   │   └── stm32f4xx_it.h                # 中斷處理函式宣告
│   ├── Src/                              # 核心原始碼
│   │   ├── main.c                        # 程式主要入口與輪詢迴圈
│   │   ├── gpio.c                        # GPIO 初始化設定
│   │   ├── usart.c                       # 串列通訊 (UART/USART) 介面配置
│   │   ├── i2c.c                         # I2C 通訊匯流排設定
│   │   ├── spi.c                         # SPI 介面配置
│   │   ├── tim.c                         # 硬體定時器與 PWM 設定
│   │   ├── stm32f4xx_it.c                # 中斷服務常式 (ISR，如 SysTick、EXTI)
│   │   └── system_stm32f4xx.c            # 晶片時脈樹 (Clock Tree) 初始化配置
│   └── Startup/                          # 晶片啟動組合語言代碼
│       └── startup_stm32f407xx.s         # 中斷向量表重定位與重設處理常式
├── BSP/                                  # 板級支援包 (Board Support Package / Hardware)
│   ├── OLED/                             # 螢幕顯示模組驅動 (例如: SSD1306)
│   │   ├── oled.c
│   │   ├── oled.h
│   │   └── oled_font.h                   # 點陣字型檔
│   ├── Sensor/                           # 感測器模組驅動 (例如: MPU6050 / BME280)
│   │   ├── sensor_mpu.c
│   │   └── sensor_mpu.h
│   └── Motor/                            # 馬達/致動器驅動 (PWM 控制)
│       ├── motor.c
│       └── motor.h
├── Middlewares/                          # 系統中介軟體 (依需求啟用)
│   └── Third_Party/
│       └── FreeRTOS/                     # 即時作業系統核心
│           ├── Source/
│           │   ├── tasks.c               # 任務排程器實作
│           │   ├── queue.c               # 佇列與訊息傳遞
│           │   ├── timers.c              # 軟體計時器
│           │   └── portable/             # 處理器架構相依代碼
│           │       ├── GCC/ARM_CM4F/     # Cortex-M4F 暫存器堆疊處理
│           │       └── MemMang/heap_4.c  # 動態記憶體配置演算法
│           └── FreeRTOSConfig.h          # RTOS 核心參數自訂配置
├── Drivers/                              # 原廠標準底層驅動庫
│   ├── CMSIS/                            # ARM Cortex-M 內核介面
│   │   ├── Device/ST/STM32F4xx/Include/  # 暫存器結構體映射宣告
│   │   └── Include/                      # CMSIS 核心標頭檔 (如 core_cm4.h)
│   └── STM32F4xx_HAL_Driver/             # ST 官方硬體抽象層 (HAL)
│       ├── Inc/                          # HAL 標頭檔 (stm32f4xx_hal_*.h)
│       └── Src/                          # HAL 原始碼 (stm32f4xx_hal_*.c)
├── Utilities/                            # 通用演算法與工具函式庫
│   ├── ring_buffer.c                     # 環形緩衝區 (供 UART DMA 接收)
│   ├── ring_buffer.h
│   └── pid.c                             # 閉迴路控制演算法 (PID 控制)
├── Build/                                # 編譯暫存目錄 (通常加入 .gitignore 忽略)
│   ├── noreal.elf                        # 包含偵錯資訊的執行檔
│   ├── noreal.hex                        # 可直接燒錄的十六進位檔案
│   └── noreal.bin                        # 純二進位韌體映像檔
├── noreal.ioc                            # STM32CubeMX 圖形化接腳/時脈專案設定檔
├── STM32F407VGTX_FLASH.ld                # Linker Script (記憶體段落映射腳本)
├── Makefile                              # 命令列建置指令稿 (支援 arm-none-eabi-gcc)
├── .clang-format                         # 程式碼排版風格規範設定檔
├── .gitignore                            # Git 版本控制忽略清單
└── README.md                             # 專案主說明文件

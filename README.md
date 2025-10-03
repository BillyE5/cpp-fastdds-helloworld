# 高效能 DDS 通訊系統實作 (C++ & CMake)

> 本專案旨在學習並實作工業級的 DDS (Data Distribution Service) 即時通訊協定。使用 C++/CMake，在 Windows 平台上從零開始，成功建置並執行了一個完整的發布/訂閱 (Pub/Sub) 應用程式。

**專案狀態：** ✅ 已完成

---

## 技術棧 (Tech Stack)

-   **語言:** C++11
-   **建置系統:** CMake
-   **核心函式庫:** eProsima Fast DDS 3.2.2
-   **依賴項目:** OpenSSL, Oracle JDK
-   **開發環境:** Visual Studio 2022, Windows 11

---

## 如何建置與執行 (Build & Run)

```bash
# 1. 進入 build 資料夾
cd build

# 2. 產生專案檔
cmake ..

# 3. 編譯專案
cmake --build .

# 4. 在兩個獨立的終端機中，分別執行
# (需先 cd 進入 build/Debug 資料夾)
DDSHelloWorldSubscriber.exe
DDSHelloWorldPublisher.exe
```

---

## 挑戰與解決方案 (Challenges & Solutions)
1. 挑戰： C++ 編譯時發生 Could NOT find OpenSSL 錯誤。

    - 解決方案： 分析 CMake 錯誤日誌，定位到缺少 OpenSSL 依賴。透過下載 Windows 版二進位檔並手動設定 OPENSSL_ROOT_DIR 環境變數，成功解決了 CMake 的 find_package 問題。

2. 挑戰： fastddsgen 工具執行時，持續發生 Unable to access jarfile 錯誤。

    - 解決方案： 透過系統性的偵錯（版本比對、路徑檢查、手動執行指令），最終發現問題根源是從 GitHub 下載了「原始碼」而非「預編譯好的 Windows 執行檔」。更換為正確的二進位檔案後，問題立刻解決。

---

## 學習心得 (Key Learnings)
這次專案讓我對 C++ 的跨平台編譯、CMake 的建置流程、以及底層通訊協定的運作有了深刻的實戰經驗。尤其在解決多重環境依賴問題的過程中，大大提升了我的系統性除錯能力。

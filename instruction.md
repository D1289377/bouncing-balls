### 規格書

#### 1. **程式功能**
此程式模擬一群球在畫布（`canvas`）上隨機移動、碰撞並改變顏色的動畫效果。

#### 2. **資料結構**
- **`Ball` 類別**
描述一個球的屬性與行為，包含以下屬性與方法：
  - **屬性**：
    - `x`：球的 x 座標（數值）。
    - `y`：球的 y 座標（數值）。
    - `velX`：球在 x 軸的速度（數值）。
    - `velY`：球在 y 軸的速度（數值）。
    - `color`：球的顏色（字串，格式為 `rgb(r, g, b)`）。
    - `size`：球的半徑（數值）。
  - **方法**：
    - `draw()`：在畫布上繪製球。
    - `update()`：更新球的位置，並檢查是否碰到畫布邊界。
    - `collisionDetect()`：檢測球與其他球的碰撞，若發生碰撞則改變顏色。

- **`balls` 陣列**
儲存所有球的實例（`Ball` 物件）。

#### 3. **主要功能流程**
1. 初始化畫布大小，並設定繪圖上下文（`ctx`）。
2. 定義隨機數生成函數（`random`）與隨機顏色生成函數（`randomRGB`）。
3. 定義 `Ball` 類別，包含繪製、更新位置與碰撞檢測的功能。
4. 建立 25 個隨機球，並將它們存入 `balls` 陣列。
5. 使用 `loop()` 函數進行動畫渲染：
   - 清除畫布。
   - 繪製每個球，更新其位置，並檢測碰撞。
   - 使用 `requestAnimationFrame` 進行遞迴調用。

---

### 測試用白話 Example

1. **測試球的初始化**
- **條件**：建立一個球，`x=50`，`y=50`，`velX=2`，`velY=3`，`color="rgb(255,0,0)"`，`size=10`。
   - **預期結果**：球的屬性應正確設定，且能正確繪製在畫布上。

2. **測試球的邊界反彈**
- **條件**：建立一個球，`x=canvas.width-5`，`y=50`，`velX=5`，`velY=0`，`size=5`。
   - **預期結果**：球碰到右邊界後，`velX` 應變為負值，球應向左移動。

3. **測試球的碰撞檢測**
- **條件**：建立兩個球，`ball1` 的位置為 `(50, 50)`，`ball2` 的位置為 `(55, 50)`，兩球的半徑均為 `10`。
   - **預期結果**：兩球應檢測到碰撞，並改變顏色。

4. **測試多球動畫**
- **條件**：初始化 25 個球，隨機位置、速度與顏色。
   - **預期結果**：所有球應在畫布上隨機移動，碰撞時改變顏色，且不會超出畫布邊界。

5. **測試畫布清除**
- **條件**：執行 `loop()` 函數。
   - **預期結果**：畫布背景應以半透明黑色（`rgba(0, 0, 0, 0.25)`）清除，並保留球的移動軌跡。

這些測試案例可用於驗證程式的正確性與穩定性。
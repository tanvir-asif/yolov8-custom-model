### YOLOv8 Variants for Micro-Crack Detection

1. **YOLOv8n (baseline)**

   - **Description:** The original YOLOv8n model from Ultralytics.
   - **Why:** Serves as a reference to see how a standard lightweight detector performs on your tablet dataset.
   - **Benefits:**
     - Very fast inference (~real-time on moderate GPUs)
     - Low memory usage
     - Limited accuracy for very small micro-cracks

2. **YOLOv8n + P2 (v8-p2)**

   - **Description:** Adds a **P2 feature pyramid layer** (stride=4), a high-resolution feature map early in the backbone.
   - **Why:** Micro cracks are tiny; deeper layers downsample and lose fine details. P2 preserves high-resolution features.
   - **Benefits:**
     - Better detection of tiny cracks
     - Slightly higher memory/computation than baseline
     - Improved mAP for small objects

3. **YOLOv8n + P2 + 5×5 Conv (v8-p2-5x5)**

   - **Description:** Uses **5×5 convolution kernels** in backbone and head instead of 3×3.
   - **Why:** Larger kernels capture more context around cracks, helping detect subtle fractures.
   - **Benefits:**
     - Enhanced feature extraction for micro cracks
     - Slightly higher computation time
     - Better detection consistency for irregular cracks

4. **YOLOv8n + P2 + 5×5 Conv + CBAM (v8-p2-5x5-cbam)**

   - **Description:** Adds **CBAM (Convolutional Block Attention Module)** after fusion blocks.
   - **Why:** CBAM focuses on important spatial regions and channels, helping the model attend to cracks.
   - **Benefits:**
     - Improved precision for micro-cracks
     - Better suppression of irrelevant background
     - Slight increase in memory usage

5. **YOLOv8n + P2 + Attention (v8-p2-attention)**
   - **Description:** Combines **P2 high-resolution layer** and **CBAM modules**, keeping **3×3 convolutions**.
   - **Why:** Balances speed and accuracy for real-time deployment.
   - **Benefits:**
     - High mAP for very small cracks
     - Real-time inference capability
     - Minimal resource increase vs. baseline
     - Ideal for conveyor belt applications

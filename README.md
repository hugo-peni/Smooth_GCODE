# 🛠️ Custom G-code Optimizer for Laser Cutting

**Fixing segmentation issues and optimizing cutting order from LightBurn output**

When using a **Monoprice laser cutter** with **LightBurn**, importing SVG files often results in fragmented G-code. The software splits curves (e.g., arcs and circles) into multiple small segments—straight lines or partial arcs. These fragmented paths can introduce tiny gaps or overlaps at the joints, leaving some cuts incomplete. This makes it difficult to remove parts cleanly and often requires careful trimming with a blade, especially when working with fragile materials like **Mylar foil**.

---

## 🔧 Why I Built This Tool

After repeatedly struggling with these issues, I created a **custom G-code post-processor** to:

- Eliminate segmentation artifacts  
- Reconstruct clean, continuous contours  
- Ensure inner shapes are cut before outer ones for better structural stability  

---

## ✅ What the Tool Does

This tool processes raw G-code exported from LightBurn and performs the following steps:

1. **Import** the raw G-code file.  
2. **Parse and extract** geometric segments representing the contours.  
3. **Group segments** into clusters — each representing one closed shape.  
4. **Extract and sort** the points from each cluster.  
5. **Reconstruct** a continuous path for each contour using a hull-based reordering strategy to ensure smooth cutting.  
6. **Sort contours** by surface area (smallest first) to prioritize cutting inner shapes before outer ones.  
7. **Generate new G-code**, following the reordered, optimized paths — starting from inner to outer contours.  

---

Feel free to contribute or open issues if you want to improve or adapt this tool!

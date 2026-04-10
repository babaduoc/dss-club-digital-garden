---
{"dg-publish":true,"permalink":"/01-tong-quan-ly-du-an/2-phong-van-hanh/presentations/app-update-showcase/","title":"SHOWCASE: HỆ THỐNG TỰ ĐỘNG CẬP NHẬT","tags":["presentation","mockup","simulation"],"dg-note-properties":{"title":"SHOWCASE: HỆ THỐNG TỰ ĐỘNG CẬP NHẬT","tags":["presentation","mockup","simulation"]}}
---


# 🚀 BẢN THUYẾT TRÌNH TƯƠNG TÁC: IN-APP UPDATE

> [!TIP]
> **Hướng dẫn xem:**
> 1. Nhấn **`Ctrl + E`** để chuyển sang chế độ **Reading View**.
> 2. Sử dụng các nút bấm bên phải để mô phỏng kịch bản trên điện thoại.

<div class="obsidian-embed-wrapper" style="background-color: #0f172a; border-radius: 20px; overflow: hidden; border: 1px solid rgba(255,255,255,0.1); box-shadow: 0 10px 40px rgba(0,0,0,0.5); margin: 20px 0;">

<!DOCTYPE html>
<html lang="vi">
<head>
    <meta charset="UTF-8">
    <script src="https://cdn.jsdelivr.net/npm/mermaid/dist/mermaid.min.js"></script>
    <style>
        /* CSS Scoped cho Obsidian */
        .showcase-scope {
            --primary: #00d2ff;
            --secondary: #3a7bd5;
            --accent: #ffeb3b;
            --bg: #0f172a;
            --card-bg: rgba(255, 255, 255, 0.05);
            --text: #f8fafc;
            background-color: var(--bg);
            color: var(--text);
            padding: 20px;
            font-family: 'Segoe UI', Tahoma, sans-serif;
        }

        .showcase-scope .p-container {
            display: grid;
            grid-template-columns: 1fr 1fr;
            gap: 30px;
            align-items: start;
            max-width: 1000px;
            margin: 0 auto;
        }

        @media (max-width: 768px) {
            .showcase-scope .p-container { grid-template-columns: 100%; }
        }

        /* --- Phone Mockup --- */
        .showcase-scope .phone-box {
            display: flex;
            justify-content: center;
        }

        .showcase-scope .phone {
            width: 260px;
            height: 520px;
            background: #000;
            border: 10px solid #334155;
            border-radius: 35px;
            position: relative;
            box-shadow: 0 30px 60px rgba(0,0,0,0.5);
            overflow: hidden;
            transition: transform 0.3s ease;
        }

        .showcase-scope .phone::before {
            content: '';
            position: absolute;
            top: 0; left: 50%;
            transform: translateX(-50%);
            width: 100px; height: 25px;
            background: #334155;
            border-bottom-left-radius: 15px;
            border-bottom-right-radius: 15px;
            z-index: 10;
        }

        .showcase-scope .app-screen {
            width: 100%;
            height: 100%;
            background: linear-gradient(180deg, #1e293b 0%, #0f172a 100%);
            display: flex;
            flex-direction: column;
            justify-content: center;
            align-items: center;
            padding: 15px;
            text-align: center;
        }

        /* --- UI States --- */
        .showcase-scope .popup-card {
            background: #1e293b;
            padding: 15px;
            border-radius: 18px;
            border: 2px solid var(--primary);
            animation: p-slideIn 0.4s ease-out;
        }

        @keyframes p-slideIn {
            from { transform: translateY(30px); opacity: 0; }
            to { transform: translateY(0); opacity: 1; }
        }

        .showcase-scope .btn-main {
            background: var(--primary);
            color: #000;
            border: none;
            padding: 10px 25px;
            border-radius: 20px;
            font-weight: bold;
            margin-top: 15px;
            cursor: pointer;
        }

        /* --- Controls --- */
        .showcase-scope .p-card {
            background: var(--card-bg);
            padding: 20px;
            border-radius: 15px;
            border: 1px solid rgba(255,255,255,0.05);
            margin-bottom: 15px;
        }

        .showcase-scope h3 { color: var(--primary); margin-bottom: 15px; font-size: 1.1rem; }

        .showcase-scope .s-btn {
            display: block;
            width: 100%;
            padding: 12px;
            background: rgba(255,255,255,0.05);
            border: 1px solid rgba(255,255,255,0.1);
            color: #fff;
            text-align: left;
            border-radius: 10px;
            margin-bottom: 8px;
            cursor: pointer;
            font-size: 0.9rem;
        }

        .showcase-scope .s-btn.active { 
            background: var(--primary); 
            color: #000; 
            font-weight: bold; 
            border-color: var(--primary);
        }

        .showcase-scope .mermaid-box {
            background: rgba(0,0,0,0.2);
            padding: 10px;
            border-radius: 10px;
        }
    </style>
</head>
<body>
    <div class="showcase-scope">
        <div class="p-container">
            <!-- Left: Phone -->
            <div class="phone-box">
                <div class="phone" id="obs-phone">
                    <div class="app-screen" id="obs-screen">
                        <div style="font-size: 2.5rem; margin-bottom: 15px;">📱</div>
                        <h3>App Trạng thái</h3>
                        <p style="font-size: 0.75rem; opacity: 0.7;">Version: 1.0.0</p>
                    </div>
                </div>
            </div>

            <!-- Right: Info -->
            <div class="info-box">
                <div class="p-card">
                    <h3>Chọn kịch bản</h3>
                    <button class="s-btn active" onclick="obsSimulate('normal', 0)">1. Hoạt động bình thường</button>
                    <button class="s-btn" onclick="obsSimulate('optional', 1)">2. Cập nhật Tùy chọn</button>
                    <button class="s-btn" onclick="obsSimulate('force', 2)">3. Cập nhật Bắt buộc</button>
                    <button class="s-btn" onclick="obsSimulate('maint', 3)">4. Chế độ Bảo trì</button>
                </div>

                <div class="p-card">
                    <h3>Cơ chế vận hành</h3>
                    <div class="mermaid-box">
                        <div class="mermaid">
                            flowchart TD
                                A[Start] --> B{Maint?}
                                B -- Y --> C[Maint UI]
                                B -- N --> D{Ver < Min?}
                                D -- Y --> E[Force Popup]
                                D -- N --> F[Enter App]
                        </div>
                    </div>
                </div>
            </div>
        </div>
    </div>

    <script>
        function obsSimulate(type, idx) {
            const sc = document.getElementById('obs-screen');
            const ph = document.getElementById('obs-phone');
            
            document.querySelectorAll('.s-btn').forEach((btn, i) => {
                btn.classList.toggle('active', i === idx);
            });

            if(type === 'normal') {
                sc.innerHTML = `<div style="font-size: 2.5rem; margin-bottom: 15px;">📱</div><h3>App Trạng thái</h3><p style="font-size: 0.75rem; opacity: 0.7;">Version: 1.0.0</p>`;
            } else if(type === 'optional') {
                sc.innerHTML = `<div class="popup-card">🚀<h4 style="margin:5px 0">Bản 2.1.0</h4><p style="font-size:0.75rem">Nâng cấp ngay!</p><button class="btn-main">Cập nhật</button><br><small style="font-size:0.6rem;opacity:0.6">Để sau</small></div>`;
            } else if(type === 'force') {
                sc.innerHTML = `<div class="popup-card" style="border-color:#ff4d4d;background:#2d1b1b">⚠️<h4 style="margin:5px 0">Cảnh báo</h4><p style="font-size:0.75rem">Cần nâng cấp để tiếp tục</p><button class="btn-main" style="background:#ff4d4d;color:#fff">Nâng cấp</button></div>`;
            } else if(type === 'maint') {
                sc.innerHTML = `<div><div style="font-size:2.5rem">🛠️</div><h4>Bảo Trì</h4><p style="font-size:0.75rem">Dự kiến xong lúc 04:00</p></div>`;
            }

            ph.style.transform = 'scale(1.05)';
            setTimeout(() => ph.style.transform = 'scale(1)', 150);
        }
        mermaid.initialize({ startOnLoad: true, theme: 'dark' });
    </script>
</body>
</html>

</div>

---
**Giá trị chiến lược:**
- Giảm tỷ lệ người dùng mắc lỗi do version cũ.
- Tối ưu hóa việc phát hành bản vá nóng (Hot-patch).
- Quản trị tập trung qua Release Portal.

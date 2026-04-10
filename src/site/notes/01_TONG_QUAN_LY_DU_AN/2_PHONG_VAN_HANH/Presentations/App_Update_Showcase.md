---
{"dg-publish":true,"permalink":"/01-tong-quan-ly-du-an/2-phong-van-hanh/presentations/app-update-showcase/","title":"SHOWCASE: HỆ THỐNG TỰ ĐỘNG CẬP NHẬT","tags":["presentation","mockup","simulation"],"dg-note-properties":{"title":"SHOWCASE: HỆ THỐNG TỰ ĐỘNG CẬP NHẬT","tags":["presentation","mockup","simulation"]}}
---


# 🚀 BẢN THUYẾT TRÌNH TƯƠNG TÁC: IN-APP UPDATE

Tài liệu này tích hợp bản mô phỏng tương tác để trình bày trực tiếp cho Ban Quản Trị.

> [!TIP]
> **Hướng dẫn xem:**
> 1. Bạn nhấn **`Ctrl + E`** để chuyển sang chế độ **Reading View**.
> 2. Kéo xuống dưới để trải nghiệm mô phỏng trên điện thoại.

<div style="background-color: #0f172a; border-radius: 20px; padding: 20px; border: 1px solid rgba(255,255,255,0.1); box-shadow: 0 10px 40px rgba(0,0,0,0.5);">

<!DOCTYPE html>
<html lang="vi">
<head>
    <meta charset="UTF-8">
    <script src="https://cdn.jsdelivr.net/npm/mermaid/dist/mermaid.min.js"></script>
    <style>
        .p-root {
            --p-primary: #00d2ff;
            --p-accent: #ffeb3b;
            --p-bg: #0f172a;
            --p-card: rgba(255, 255, 255, 0.05);
            --p-text: #f8fafc;
            color: var(--p-text);
            font-family: 'Segoe UI', sans-serif;
            display: grid;
            grid-template-columns: 1fr 1.5fr;
            gap: 30px;
            padding: 20px;
        }

        @media (max-width: 800px) { .p-root { grid-template-columns: 1fr; } }

        .phone-mockup {
            width: 280px; height: 560px;
            background: #000; border: 10px solid #334155; border-radius: 35px;
            position: relative; overflow: hidden; margin: 0 auto;
            box-shadow: 0 20px 50px rgba(0,0,0,0.5);
        }

        .screen {
            width: 100%; height: 100%;
            background: linear-gradient(180deg, #1e293b 0%, #0f172a 100%);
            display: flex; flex-direction: column; justify-content: center;
            align-items: center; padding: 20px; text-align: center;
        }

        .p-card { background: var(--p-card); padding: 20px; border-radius: 15px; border: 1px solid rgba(255,255,255,0.1); margin-bottom: 15px; }
        
        .p-btn {
            display: block; width: 100%; padding: 12px;
            background: rgba(255,255,255,0.05); border: 1px solid rgba(255,255,255,0.1);
            color: #fff; text-align: left; border-radius: 10px; margin-bottom: 8px; cursor: pointer; transition: 0.2s;
        }
        .p-btn:hover { border-color: var(--p-primary); background: rgba(0,210,255,0.05); }
        .p-btn.active { background: var(--p-primary); color: #000; font-weight: bold; }

        .p-popup {
            background: #1e293b; padding: 15px; border-radius: 15px;
            border: 2px solid var(--p-primary); animation: p-slide 0.3s ease-out;
        }
        @keyframes p-slide { from { transform: translateY(20px); opacity: 0; } to { transform: translateY(0); opacity: 1; } }
        
        .p-update-btn { background: var(--p-primary); color: #000; border: none; padding: 10px 20px; border-radius: 20px; font-weight: bold; margin-top: 10px; }
    </style>
</head>
<body>
    <div class="p-root">
        <div class="phone-column">
            <div class="phone-mockup" id="p-body">
                <div class="screen" id="p-screen">
                    <div style="font-size: 2.5rem;">📱</div>
                    <h4>App Trạng thái 1.0</h4>
                </div>
            </div>
        </div>
        <div class="control-column">
            <div class="p-card">
                <h3 style="color: var(--p-primary); margin-bottom: 15px;">Mô phỏng tính năng</h3>
                <button class="p-btn active" onclick="pSim('normal', 0)">Kịch bản 1: Bình thường</button>
                <button class="p-btn" onclick="pSim('optional', 1)">Kịch bản 2: Gợi ý tải (Optional)</button>
                <button class="p-btn" onclick="pSim('force', 2)">Kịch bản 3: Ép cập nhật (Force)</button>
                <button class="p-btn" onclick="pSim('maint', 3)">Kịch bản 4: Đang bảo trì</button>
            </div>
            <div class="p-card" style="font-size: 0.9rem;">
                <h3 style="color: var(--p-accent); margin-bottom: 10px;">Phân tích cho sếp</h3>
                • Đồng bộ phiên bản toàn hệ thống.<br>
                • Tránh lỗi App cũ gọi API mới.<br>
                • Linh hoạt bật/tắt bảo trì trên CMS.
            </div>
        </div>
    </div>
    <script>
        function pSim(type, idx) {
            const s = document.getElementById('p-screen');
            const b = document.getElementById('p-body');
            document.querySelectorAll('.p-btn').forEach((btn, i) => {
                btn.classList.toggle('active', i === idx);
            });
            if(type === 'normal') s.innerHTML = '<div style="font-size: 2.5rem;">📱</div><h4>App Trạng thái 1.0</h4>';
            else if(type === 'optional') s.innerHTML = '<div class="p-popup">🚀<h4>Bản 2.1 mới!</h4><button class="p-update-btn">Cập nhật</button><br><small>Để sau</small></div>';
            else if(type === 'force') s.innerHTML = '<div class="p-popup" style="border-color:#ff4d4d">⚠️<h4>Cập nhật Bắt buộc</h4><button class="p-update-btn" style="background:#ff4d4d;color:#fff">Nâng cấp ngay</button></div>';
            else if(type === 'maint') s.innerHTML = '<div style="padding:10px">🛠️<h4>Đang Bảo Trì</h4><div style="background:rgba(255,235,59,0.1);padding:5px;font-size:0.7rem;color:var(--p-accent);border:1px dashed">Quay lại lúc 04:00</div></div>';
            b.style.transform = 'scale(1.03)';
            setTimeout(() => b.style.transform = 'scale(1)', 150);
        }
    </script>
</body>
</html>

</div>

---
**Giá trị chiến lược:**
- Giảm tỷ lệ người dùng mắc lỗi do version cũ.
- Tối ưu hóa việc phát hành bản vá nóng (Hot-patch).
- Quản trị tập trung qua Release Portal.

<!DOCTYPE html>
<html lang="zh-CN">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>牧夫座双星系统 - Pulcherrima (Izar)</title>
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }
        body, html {
            width: 100%;
            height: 100%;
            overflow: hidden;
            background-color: #030712;
            font-family: system-ui, -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, sans-serif;
            color: #f3f4f6;
        }
        canvas {
            display: block;
            width: 100vw;
            height: 100vh;
        }
        .ui-panel {
            position: absolute;
            top: 20px;
            left: 20px;
            background: rgba(15, 23, 42, 0.75);
            backdrop-filter: blur(12px);
            border: 1px solid rgba(255, 255, 255, 0.1);
            padding: 20px;
            border-radius: 16px;
            box-shadow: 0 20px 25px -5px rgba(0, 0, 0, 0.5);
            max-width: 320px;
            z-index: 10;
            pointer-events: auto;
        }
        h1 {
            font-size: 1.15rem;
            font-weight: 600;
            margin-bottom: 6px;
            background: linear-gradient(to right, #fbbf24, #38bdf8);
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
        }
        p {
            font-size: 0.8rem;
            color: #9ca3af;
            margin-bottom: 16px;
            line-height: 1.4;
        }
        .control-group {
            margin-bottom: 12px;
        }
        label {
            display: flex;
            justify-content: space-between;
            font-size: 0.75rem;
            color: #d1d5db;
            margin-bottom: 4px;
        }
        input[type="range"] {
            width: 100%;
            accent-color: #38bdf8;
            cursor: pointer;
        }
        .btn-row {
            display: flex;
            gap: 8px;
            margin-top: 16px;
        }
        button {
            flex: 1;
            background: rgba(56, 189, 248, 0.15);
            border: 1px solid rgba(56, 189, 248, 0.3);
            color: #38bdf8;
            padding: 8px 12px;
            border-radius: 8px;
            font-size: 0.8rem;
            cursor: pointer;
            transition: all 0.2s;
        }
        button:hover {
            background: rgba(56, 189, 248, 0.3);
        }
        .tips {
            position: absolute;
            bottom: 20px;
            left: 50%;
            transform: translateX(-50%);
            background: rgba(15, 23, 42, 0.6);
            backdrop-filter: blur(8px);
            padding: 8px 16px;
            border-radius: 20px;
            font-size: 0.75rem;
            color: #9ca3af;
            border: 1px solid rgba(255, 255, 255, 0.05);
            pointer-events: none;
        }
    </style>
</head>
<body>

    <div class="ui-panel">
        <h1>Pulcherrima (Izar)</h1>
        <p>牧夫座ε双星系统：金黄色的橙色巨星与亮蓝绿色的伴星正围绕共同质心交织旋转。</p>
        
        <div class="control-group">
            <label><span>公转速度</span><span id="speedVal">1.0x</span></label>
            <input type="range" id="speedRange" min="0.1" max="3.0" step="0.1" value="1.0">
        </div>

        <div class="control-group">
            <label><span>轨迹拖尾长度</span><span id="trailVal">中等</span></label>
            <input type="range" id="trailRange" min="50" max="400" step="10" value="200">
        </div>

        <div class="btn-row">
            <button id="pauseBtn">暂停 / 播放</button>
            <button id="resetBtn">重置视角</button>
        </div>
    </div>

    <div class="tips">提示：按住鼠标左键拖拽可旋转 3D 视角，滚动鼠标滚轮可缩放</div>

    <canvas id="spaceCanvas"></canvas>

    <script>
        const canvas = document.getElementById('spaceCanvas');
        const ctx = canvas.getContext('2d');

        let width, height;
        function resize() {
            width = canvas.width = window.innerWidth;
            height = canvas.height = window.innerHeight;
        }
        window.addEventListener('resize', resize);
        resize();

        // 背景微光粒子
        const stars = Array.from({ length: 300 }, () => ({
            x: (Math.random() - 0.5) * window.innerWidth * 2,
            y: (Math.random() - 0.5) * window.innerHeight * 2,
            z: Math.random() * 1000,
            size: Math.random() * 1.5
        }));

        // 交互控制变量
        let angle = 0;
        let speed = 1.0;
        let trailLength = 200;
        let isPaused = false;

        // 3D 视角旋转
        let rotX = 0.4;
        let rotY = 0.0;
        let isDragging = false;
        let lastMouseX = 0, lastMouseY = 0;

        window.addEventListener('mousedown', e => {
            isDragging = true;
            lastMouseX = e.clientX;
            lastMouseY = e.clientY;
        });

        window.addEventListener('mousemove', e => {
            if (!isDragging) return;
            const dx = e.clientX - lastMouseX;
            const dy = e.clientY - lastMouseY;
            rotY += dx * 0.005;
            rotX += dy * 0.005;
            lastMouseX = e.clientX;
            lastMouseY = e.clientY;
        });

        window.addEventListener('mouseup', () => isDragging = false);

        // 触控支持
        window.addEventListener('touchstart', e => {
            if(e.touches.length === 1) {
                isDragging = true;
                lastMouseX = e.touches[0].clientX;
                lastMouseY = e.touches[0].clientY;
            }
        });
        window.addEventListener('touchmove', e => {
            if (!isDragging || e.touches.length !== 1) return;
            const dx = e.touches[0].clientX - lastMouseX;
            const dy = e.touches[0].clientY - lastMouseY;
            rotY += dx * 0.005;
            rotX += dy * 0.005;
            lastMouseX = e.touches[0].clientX;
            lastMouseY = e.touches[0].clientY;
        });
        window.addEventListener('touchend', () => isDragging = false);

        // 轨迹记录
        let trail1 = [];
        let trail2 = [];

        function project(x, y, z) {
            // 简单的 3D 旋转与透视投影
            // 绕 Y 轴旋转
            let x1 = x * Math.cos(rotY) - z * Math.sin(rotY);
            let z1 = x * Math.sin(rotY) + z * Math.cos(rotY);
            // 绕 X 轴旋转
            let y2 = y * Math.cos(rotX) - z1 * Math.sin(rotX);
            let z2 = y * Math.sin(rotX) + z1 * Math.cos(rotX);

            const fov = 800;
            const scale = fov / (fov + z2 + 400);
            return {
                x: width / 2 + x1 * scale,
                y: height / 2 + y2 * scale,
                scale: scale,
                z: z2
            };
        }

        function animate() {
            // 半透明清屏形成拖尾残影背景
            ctx.fillStyle = 'rgba(3, 7, 18, 0.3)';
            ctx.fillRect(0, 0, width, height);

            // 绘制背景星空
            ctx.fillStyle = '#ffffff';
            stars.forEach(s => {
                let p = project(s.x, s.y, s.z);
                if (p.scale > 0) {
                    ctx.globalAlpha = Math.min(1, p.scale * 0.8);
                    ctx.beginPath();
                    ctx.arc(p.x, p.y, s.size * p.scale, 0, Math.PI * 2);
                    ctx.fill();
                }
            });
            ctx.globalAlpha = 1.0;

            if (!isPaused) {
                angle += 0.015 * speed;
            }

            // 双星轨道计算（围绕质心）
            const dist = 160; 
            const r1 = dist * 0.4;
            const r2 = dist * 0.6;

            const x1 = Math.cos(angle) * r1;
            const z1 = Math.sin(angle) * r1;
            const y1 = Math.sin(angle * 0.5) * 20;

            const x2 = -Math.cos(angle) * r2;
            const z2 = -Math.sin(angle) * r2;
            const y2 = -Math.sin(angle * 0.5) * 20;

            // 记录轨迹
            trail1.unshift(project(x1, y1, z1));
            trail2.unshift(project(x2, y2, z2));
            if (trail1.length > trail50) { // 限制长度
                // 动态控制
            }
            const maxLen = parseInt(document.getElementById('trailRange').value);
            if (trail1.length > maxLen) trail1.pop();
            if (trail2.length > maxLen) trail2.pop();

            // 绘制主星1轨迹 (金橙色)
            if (trail1.length > 1) {
                ctx.beginPath();
                ctx.moveTo(trail1[0].x, trail1[0].y);
                for (let i = 1; i < trail1.length; i++) {
                    ctx.lineTo(trail1[i].x, trail1[i].y);
                }
                ctx.strokeStyle = 'rgba(251, 191, 36, 0.3)';
                ctx.lineWidth = 2;
                ctx.stroke();
            }

            // 绘制伴星2轨迹 (青蓝色)
            if (trail2.length > 1) {
                ctx.beginPath();
                ctx.moveTo(trail2[0].x, trail2[0].y);
                for (let i = 1; i < trail2.length; i++) {
                    ctx.lineTo(trail2[i].x, trail2[i].y);
                }
                ctx.strokeStyle = 'rgba(56, 189, 248, 0.3)';
                ctx.lineWidth = 2;
                ctx.stroke();
            }

            // 计算投影坐标
            let p1 = project(x1, y1, z1);
            let p2 = project(x2, y2, z2);

            // 按 Z 深度排序保证前后遮挡关系正确
            const starsToDraw = [
                { p: p1, color: '#fbbf24', glow: 'rgba(251, 191, 36, 0.6)', radius: 18 },
                { p: p2, color: '#38bdf8', glow: 'rgba(56, 189, 248, 0.6)', radius: 14 }
            ].sort((a, b) => a.p.z - b.p.z);

            // 绘制恒星
            starsToDraw.forEach(star => {
                let r = star.radius * star.p.scale;
                if (r < 1) r = 1;

                // 恒星光晕
                let gradient = ctx.createRadialGradient(star.p.x, star.p.y, 0, star.p.x, star.p.y, r * 3.5);
                gradient.addColorStop(0, star.glow);
                gradient.addColorStop(1, 'rgba(0, 0, 0, 0)');
                ctx.fillStyle = gradient;
                ctx.beginPath();
                ctx.arc(star.p.x, star.p.y, r * 3.5, 0, Math.PI * 2);
                ctx.fill();

                // 恒星本体
                ctx.fillStyle = star.color;
                ctx.beginPath();
                ctx.arc(star.p.x, star.p.y, r, 0, Math.PI * 2);
                ctx.fill();
            });

            requestAnimationFrame(animate);
        }

        animate();

        // UI 绑定
        const speedRange = document.getElementById('speedRange');
        const speedVal = document.getElementById('speedVal');
        speedRange.addEventListener('input', e => {
            speed = parseFloat(e.target.value);
            speedVal.innerText = speed.toFixed(1) + 'x';
        });

        const trailRange = document.getElementById('trailRange');
        const trailVal = document.getElementById('trailVal');
        trailRange.addEventListener('input', e => {
            const val = parseInt(e.target.value);
            trailVal.innerText = val < 100 ? '较短' : val > 300 ? '较长' : '中等';
        });

        const pauseBtn = document.getElementById('pauseBtn');
        pauseBtn.addEventListener('click', () => {
            isPaused = !isPaused;
        });

        const resetBtn = document.getElementById('resetBtn');
        resetBtn.addEventListener('click', () => {
            rotX = 0.4;
            rotY = 0.0;
        });
    </script>
</body>
</html>

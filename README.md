# Industrial-safety
<!DOCTYPE html>
<html lang="ko">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0, user-scalable=yes, maximum-scale=2.0">
  <title>조여성호 202217106 | 골절 분석 시스템</title>
  <!-- 完全不同版型：深色仪表盘风格，使用现代玻璃质感与侧边导航 -->
  <style>
    * {
      margin: 0;
      padding: 0;
      box-sizing: border-box;
    }

    body {
      font-family: 'Segoe UI', 'Roboto', 'Noto Sans KR', system-ui, sans-serif;
      background: #0b0f1a;
      background-image: radial-gradient(circle at 20% 10%, #1a2332 0%, #03050b 90%);
      min-height: 100vh;
      display: flex;
      justify-content: center;
      align-items: center;
      padding: 1.5rem;
      margin: 0;
      color: #e0e5f0;
    }

    /* 仪表板主容器 —— 完全不同布局：卡片组合式，非原页面长滚动设计 */
    .dashboard {
      max-width: 1300px;
      width: 100%;
      display: flex;
      flex-wrap: wrap;
      gap: 1.8rem;
      background: rgba(18, 25, 40, 0.65);
      backdrop-filter: blur(18px);
      -webkit-backdrop-filter: blur(18px);
      border-radius: 3rem;
      padding: 2.2rem;
      box-shadow: 0 30px 50px rgba(0, 0, 0, 0.7), inset 0 1px 0 rgba(255, 255, 255, 0.08);
      border: 1px solid rgba(74, 144, 226, 0.15);
    }

    /* 左侧影像面板 */
    .viewer-panel {
      flex: 2;
      min-width: 320px;
      background: rgba(8, 14, 26, 0.7);
      backdrop-filter: blur(16px);
      -webkit-backdrop-filter: blur(16px);
      border-radius: 2.5rem;
      padding: 1.8rem 1.5rem 1.5rem;
      box-shadow: 0 15px 35px rgba(0, 0, 0, 0.6), inset 0 0 0 1px rgba(255, 255, 255, 0.07);
      display: flex;
      flex-direction: column;
    }

    .student-badge {
      display: flex;
      justify-content: space-between;
      align-items: center;
      margin-bottom: 1.5rem;
      padding: 0 0.3rem;
    }

    .student-info {
      background: linear-gradient(135deg, #1e293b, #0f172a);
      border-radius: 3rem;
      padding: 0.5rem 1.4rem;
      border: 1px solid rgba(56, 189, 248, 0.4);
      box-shadow: 0 0 18px rgba(14, 165, 233, 0.25);
    }

    .student-id {
      font-size: 1.1rem;
      font-weight: 600;
      letter-spacing: 0.03em;
      color: #b9e6ff;
      background: linear-gradient(to right, #a5d8ff, #67c8ff);
      -webkit-background-clip: text;
      -webkit-text-fill-color: transparent;
      background-clip: text;
    }

    .hospital-tag {
      font-size: 0.85rem;
      background: rgba(255, 255, 255, 0.05);
      padding: 0.35rem 1.2rem;
      border-radius: 2rem;
      color: #b0c7e0;
      border: 1px solid rgba(255, 255, 255, 0.15);
      backdrop-filter: blur(5px);
    }

    /* 图像容器 */
    .image-container {
      background: #030712;
      border-radius: 2rem;
      padding: 0.8rem;
      box-shadow: inset 0 0 25px rgba(0, 0, 0, 0.8), 0 20px 35px rgba(0, 0, 0, 0.7);
      margin-bottom: 1.3rem;
      position: relative;
      display: flex;
      justify-content: center;
      align-items: center;
      aspect-ratio: 1 / 1;
      border: 1px solid rgba(255, 255, 255, 0.1);
    }

    .xray-img {
      width: 100%;
      height: 100%;
      object-fit: contain;
      border-radius: 1.2rem;
      display: block;
      filter: brightness(1.05) contrast(1.1);
      transition: all 0.2s ease;
    }

    /* 骨折标记点 (模拟检测效果) */
    .fracture-overlay {
      position: absolute;
      top: 0;
      left: 0;
      width: 100%;
      height: 100%;
      pointer-events: none;
    }

    .marker {
      position: absolute;
      width: 28px;
      height: 28px;
      background: rgba(255, 70, 70, 0.85);
      border: 3px solid #ffffff;
      border-radius: 50%;
      box-shadow: 0 0 20px #ff3b3b, 0 0 35px rgba(255, 60, 60, 0.7);
      transform: translate(-50%, -50%);
      animation: pulse-marker 2s infinite;
      display: flex;
      align-items: center;
      justify-content: center;
    }

    .marker::after {
      content: "";
      width: 8px;
      height: 8px;
      background: white;
      border-radius: 50%;
      box-shadow: 0 0 12px white;
    }

    @keyframes pulse-marker {
      0% { box-shadow: 0 0 15px #ff4d4d, 0 0 30px #ff0000; }
      50% { box-shadow: 0 0 28px #ff6b6b, 0 0 50px #ff1a1a; }
      100% { box-shadow: 0 0 15px #ff4d4d, 0 0 30px #ff0000; }
    }

    .marker-left {
      top: 58%;
      left: 42%;
    }

    .marker-right {
      top: 53%;
      left: 68%;
    }

    /* 控制栏 */
    .control-bar {
      display: flex;
      align-items: center;
      justify-content: space-between;
      gap: 1rem;
      flex-wrap: wrap;
      margin-top: 0.5rem;
    }

    .slice-nav {
      display: flex;
      align-items: center;
      gap: 0.6rem;
      background: rgba(255, 255, 255, 0.06);
      border-radius: 3rem;
      padding: 0.5rem 1.2rem;
      backdrop-filter: blur(8px);
    }

    .nav-btn {
      background: none;
      border: none;
      color: #cbd5e1;
      font-size: 1.6rem;
      cursor: pointer;
      padding: 0 0.3rem;
      transition: 0.2s;
      line-height: 1;
    }

    .nav-btn:hover {
      color: #38bdf8;
      text-shadow: 0 0 8px #0ea5e9;
    }

    .slice-indicator {
      font-weight: 600;
      background: #1e293b;
      padding: 0.3rem 1.2rem;
      border-radius: 2rem;
      color: #b9e6ff;
      font-size: 1rem;
    }

    .detection-badge {
      background: rgba(220, 38, 38, 0.2);
      border: 1px solid #ef4444;
      color: #ffb3b3;
      padding: 0.45rem 1.3rem;
      border-radius: 2rem;
      font-weight: 600;
      font-size: 0.9rem;
      backdrop-filter: blur(8px);
      display: flex;
      align-items: center;
      gap: 0.3rem;
    }

    .detection-badge::before {
      content: "⚡";
      filter: drop-shadow(0 0 5px red);
    }

    /* 右侧信息面板 —— 完全不同于原版的卡片布局 */
    .info-panel {
      flex: 1.2;
      min-width: 260px;
      display: flex;
      flex-direction: column;
      gap: 1.5rem;
    }

    .glass-card {
      background: rgba(15, 23, 42, 0.65);
      backdrop-filter: blur(15px);
      -webkit-backdrop-filter: blur(15px);
      border-radius: 2rem;
      padding: 1.5rem 1.3rem;
      border: 1px solid rgba(255, 255, 255, 0.08);
      box-shadow: 0 12px 28px rgba(0, 0, 0, 0.6);
    }

    .patient-header {
      display: flex;
      justify-content: space-between;
      align-items: baseline;
      border-bottom: 1px solid rgba(255, 255, 255, 0.1);
      padding-bottom: 0.8rem;
      margin-bottom: 1.2rem;
    }

    .patient-name {
      font-size: 1.6rem;
      font-weight: 700;
      background: linear-gradient(to right, #f0f9ff, #bae6fd);
      -webkit-background-clip: text;
      -webkit-text-fill-color: transparent;
      background-clip: text;
    }

    .exam-type {
      background: #1e3a5f;
      padding: 0.2rem 1rem;
      border-radius: 2rem;
      font-size: 0.8rem;
      font-weight: 600;
      color: #d4eaff;
    }

    .info-row {
      display: flex;
      justify-content: space-between;
      margin-bottom: 0.9rem;
      font-size: 0.95rem;
    }

    .info-label {
      color: #94a3b8;
      font-weight: 500;
    }

    .info-value {
      font-weight: 600;
      color: #e2e8f0;
    }

    .fracture-list {
      margin-top: 1rem;
    }

    .fracture-item {
      display: flex;
      align-items: center;
      gap: 0.7rem;
      background: rgba(239, 68, 68, 0.1);
      border-radius: 1.2rem;
      padding: 0.7rem 1rem;
      margin-bottom: 0.7rem;
      border: 1px solid rgba(239, 68, 68, 0.3);
    }

    .dot {
      width: 10px;
      height: 10px;
      background: #ef4444;
      border-radius: 50%;
      box-shadow: 0 0 12px #f87171;
    }

    .confidence {
      margin-left: auto;
      font-weight: 700;
      color: #fca5a5;
    }

    .report-btn {
      background: linear-gradient(145deg, #1e293b, #0f172a);
      border: 1px solid rgba(56, 189, 248, 0.5);
      color: #d9ecff;
      padding: 0.9rem 1.2rem;
      border-radius: 2.5rem;
      font-weight: 700;
      font-size: 1rem;
      width: 100%;
      cursor: pointer;
      transition: 0.3s;
      letter-spacing: 0.5px;
      backdrop-filter: blur(10px);
      margin-top: 0.5rem;
    }

    .report-btn:hover {
      background: #0f2b47;
      border-color: #38bdf8;
      box-shadow: 0 0 18px #0284c7;
      color: white;
    }

    .footer-note {
      text-align: right;
      font-size: 0.7rem;
      color: #64748b;
      margin-top: 0.8rem;
    }

    @media (max-width: 750px) {
      .dashboard {
        flex-direction: column;
      }
    }
  </style>
</head>
<body>
  <div class="dashboard">
    <!-- 左侧：影像查看器 (完全不同于原布局) -->
    <div class="viewer-panel">
      <div class="student-badge">
        <span class="student-id">🦴 조여성호 202217106</span>
        <span class="hospital-tag">정형외과 영상판독</span>
      </div>

      <div class="image-container">
        <!-- CT 스타일 뼈 이미지 (골절 부위 표시) -->
        < img 
          src="https://t1589571682-rgb.github.io/bone-fracture30/ct_image.png" 
          alt="골절 CT 영상" 
          class="xray-img" 
          id="ctImage"
          onerror="this.onerror=null; this.src='data:image/svg+xml,%3Csvg xmlns=\'http://www.w3.org/2000/svg\' width=\'400\' height=\'400\' viewBox=\'0 0 400 400\'%3E%3Crect width=\'400\' height=\'400\' fill=\'%230a0f1a\'/%3E%3Ccircle cx=\'200\' cy=\'180\' r=\'110\' fill=\'none\' stroke=\'%233b4b66\' stroke-width=\'18\' opacity=\'0.9\'/%3E%3Cpath d=\'M140 240 L260 240\' stroke=\'%235a6c85\' stroke-width=\'15\'/%3E%3Ccircle cx=\'160\' cy=\'250\' r=\'28\' fill=\'%232a3647\' stroke=\'%2394a3b8\' stroke-width=\'5\'/%3E%3Ccircle cx=\'240\' cy=\'250\' r=\'28\' fill=\'%232a3647\' stroke=\'%2394a3b8\' stroke-width=\'5\'/%3E%3Cpath d=\'M175 140 L225 140 L215 175 L185 175 Z\' fill=\'%23334056\' opacity=\'0.7\'/%3E%3Ctext x=\'200\' y=\'340\' text-anchor=\'middle\' fill=\'%239ca3af\' font-size=\'14\'%3E골절 이미지 로드%3C/text%3E%3C/svg%3E';"
        >
        <div class="fracture-overlay">
          <div class="marker marker-left" title="요골 원위부 골절"></div>
          <div class="marker marker-right" title="척골 경상돌기 골절"></div>
        </div>
      </div>

      <div class="control-bar">
        <div class="slice-nav">
          <button class="nav-btn" id="prevSlice">◀</button>
          <span class="slice-indicator" id="sliceDisplay">슬라이스 18 / 32</span>
          <button class="nav-btn" id="nextSlice">▶</button>
        </div>
        <div class="detection-badge">
          골절 의심 2곳
        </div>
      </div>
      <div style="font-size:0.75rem; color:#6b7b8f; margin-top:0.6rem; text-align:center; letter-spacing:0.5px;">
        AI 보조 진단 · 조여성호
      </div>
    </div>

    <!-- 右侧：完全不同信息卡片布局 -->
    <div class="info-panel">
      <div class="glass-card">
        <div class="patient-header">
          <span class="patient-name">김민준</span>
          <span class="exam-type">CT 골절 프로토콜</span>
        </div>
        <div class="info-row">
          <span class="info-label">등록번호</span>
          <span class="info-value">202217106</span>
        </div>
        <div class="info-row">
          <span class="info-label">촬영일</span>
          <span class="info-value">2026-06-11</span>
        </div>
        <div class="info-row">
          <span class="info-label">부위</span>
          <span class="info-value">우측 전완 (Radius/Ulna)</span>
        </div>
      </div>

      <div class="glass-card">
        <h3 style="font-weight: 600; margin-bottom: 1rem; color: #cbd5e1; display: flex; align-items: center; gap:0.3rem;">
          <span>🔍 골절 분석 리포트</span>
        </h3>
        <div class="fracture-list">
          <div class="fracture-item">
            <span class="dot"></span>
            <span>요골 원위부 골절</span>
            <span class="confidence">98%</span>
          </div>
          <div class="fracture-item">
            <span class="dot"></span>
            <span>척골 경상돌기 골절</span>
            <span class="confidence">94%</span>
          </div>
        </div>
        <div style="color:#94a3b8; font-size:0.85rem; margin:1rem 0 0.3rem; background:rgba(255,255,255,0.03); padding:0.7rem; border-radius:1rem;">
          ⚡ 전위 가능성: 중등도 · 정형외과 협진 권고
        </div>
        <button class="report-btn" id="detailReportBtn">
          📋 상세 소견서 보기
        </button>
        <div class="footer-note">
          조여성호 · 판독 보조 시스템
        </div>
      </div>
      
      <!-- 额外的학번 강조 카드 (不同于原版) -->
      <div style="display: flex; justify-content: flex-end; align-items: center; gap: 0.5rem; margin-top: 0.2rem;">
        <span style="background: #0b1622; padding: 0.3rem 1.2rem; border-radius: 2rem; font-size: 0.8rem; color: #b9d0f0; border:1px solid #2d4059;">
          학번: 조여성호 202217106
        </span>
      </div>
    </div>
  </div>

  <script>
    (function() {
      // 当前切片模拟
      let currentSlice = 18;
      const totalSlices = 32;
      
      const sliceDisplay = document.getElementById('sliceDisplay');
      const prevBtn = document.getElementById('prevSlice');
      const nextBtn = document.getElementById('nextSlice');
      const ctImage = document.getElementById('ctImage');
      const detailBtn = document.getElementById('detailReportBtn');

      // 更新切片显示
      function updateSliceDisplay() {
        if (sliceDisplay) {
          sliceDisplay.textContent = `슬라이스 ${currentSlice} / ${totalSlices}`;
        }
        // 模拟图像轻微变化：实际中会更换图片，这里仅通过透明度或滤镜示意变化
        if (ctImage) {
          // 通过微小滤镜变化表示不同切片效果
          const contrast = 1.0 + (currentSlice - 18) * 0.02;
          ctImage.style.filter = `brightness(1.05) contrast(${contrast})`;
        }
      }

      // 前一切片
      prevBtn.addEventListener('click', function() {
        if (currentSlice > 1) {
          currentSlice--;
          updateSliceDisplay();
        } else {
          alert('첫 번째 슬라이스입니다.');
        }
      });

      // 后一切片
      nextBtn.addEventListener('click', function() {
        if (currentSlice < totalSlices) {
          currentSlice++;
          updateSliceDisplay();
        } else {
          alert('마지막 슬라이스입니다.');
        }
      });

      // 键盘导航 (额外功能)
      window.addEventListener('keydown', function(e) {
        if (e.key === 'ArrowLeft') {
          e.preventDefault();
          if (currentSlice > 1) {
            currentSlice--;
            updateSliceDisplay();
          }
        } else if (e.key === 'ArrowRight') {
          e.preventDefault();
          if (currentSlice < totalSlices) {
            currentSlice++;
            updateSliceDisplay();
          }
        }
      });

      // 详细报告按钮交互
      detailBtn.addEventListener('click', function() {
        alert('조여성호 202217106\n\n[골절 상세 소견]\n- 요골 원위부 골절 (Colles 골절 유사)\n- 척골 경상돌기 견열 골절\n- 주변 연부조직 부종 동반\n\n※ 본 시스템은 교육용 보조 진단입니다.');
      });

      // 初始设置
      updateSliceDisplay();

      // 确保图像加载失败时保留标记可见
      console.log('조여성호 202217106 골절 분석 시스템 준비 완료');
    })();
  </script>
</body>
</html>

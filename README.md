# Industrial-safety
<!DOCTYPE html>
<html lang="zh-KR">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0, user-scalable=no">
    <title>智慧食安 · 智控一体系统 | AI Factory Safety</title>
    <!-- 全新风格：深色科技感 + 侧边栏仪表盘布局，完全区别于原版卡片式居中布局 -->
    <!-- 中韩双语对照：所有关键标签均采用 中文 / 한국어 双行显示 -->
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }

        body {
            background: #0B1120;
            font-family: 'Inter', 'Segoe UI', 'Poppins', 'Noto Sans KR', system-ui, -apple-system, sans-serif;
            color: #EFF3FB;
            overflow-x: hidden;
        }

        /* 自定义滚动条 */
        ::-webkit-scrollbar {
            width: 5px;
            height: 5px;
        }
        ::-webkit-scrollbar-track {
            background: #1F2A40;
            border-radius: 10px;
        }
        ::-webkit-scrollbar-thumb {
            background: #3B82F6;
            border-radius: 10px;
        }

        /* 整体布局：类似现代仪表板，左侧导航栏 + 右侧主内容区，和原网页完全不同的骨架 */
        .dashboard {
            display: flex;
            min-height: 100vh;
        }

        /* ========= 全新左侧边栏（原网页无侧边栏） ========= */
        .sidebar {
            width: 280px;
            background: rgba(18, 25, 45, 0.85);
            backdrop-filter: blur(12px);
            border-right: 1px solid rgba(59, 130, 246, 0.3);
            padding: 2rem 1.5rem;
            display: flex;
            flex-direction: column;
            gap: 2rem;
            position: sticky;
            top: 0;
            height: 100vh;
            z-index: 10;
        }

        .logo-area h2 {
            font-size: 1.6rem;
            font-weight: 700;
            background: linear-gradient(135deg, #60A5FA, #A855F7);
            -webkit-background-clip: text;
            background-clip: text;
            color: transparent;
            letter-spacing: -0.3px;
        }
        .logo-area p {
            font-size: 0.7rem;
            color: #94A3B8;
            margin-top: 6px;
            letter-spacing: 1px;
        }

        .nav-menu {
            display: flex;
            flex-direction: column;
            gap: 1rem;
        }
        .nav-item {
            display: flex;
            align-items: center;
            gap: 12px;
            padding: 12px 16px;
            background: transparent;
            border-radius: 16px;
            color: #CBD5E1;
            transition: 0.2s;
            cursor: default;
            font-weight: 500;
        }
        .nav-item.active {
            background: rgba(59, 130, 246, 0.2);
            color: #60A5FA;
            border-left: 3px solid #3B82F6;
        }
        .nav-item:not(.active):hover {
            background: rgba(255,255,255,0.05);
        }

        .user-info-side {
            margin-top: auto;
            border-top: 1px solid #2D3A5E;
            padding-top: 1.5rem;
        }
        .user-name {
            font-weight: 600;
            font-size: 1rem;
            font-family: monospace;
            background: #1E293B;
            display: inline-block;
            padding: 6px 12px;
            border-radius: 40px;
            letter-spacing: 0.5px;
        }

        /* ========= 右侧主内容 ========= */
        .main-content {
            flex: 1;
            padding: 1.8rem 2.2rem;
            overflow-y: auto;
        }

        /* 头部时间栏，风格转为极简分割线 */
        .top-bar {
            display: flex;
            justify-content: space-between;
            align-items: baseline;
            border-bottom: 1px solid #1E293B;
            padding-bottom: 1rem;
            margin-bottom: 2rem;
            flex-wrap: wrap;
        }
        .live-time {
            font-family: 'JetBrains Mono', monospace;
            background: #0F172A;
            padding: 6px 14px;
            border-radius: 32px;
            font-size: 0.9rem;
            border: 1px solid #334155;
            letter-spacing: 1px;
        }
        .badge-system {
            font-size: 0.8rem;
            background: #1E293B;
            padding: 4px 12px;
            border-radius: 30px;
            color: #A5F3C3;
        }

        /* 统计卡片网格（采用四象限布局，和原网页上方横行不同） */
        .stats-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(220px, 1fr));
            gap: 1.5rem;
            margin-bottom: 2rem;
        }
        .stat-card {
            background: rgba(21, 31, 52, 0.65);
            backdrop-filter: blur(4px);
            border-radius: 28px;
            padding: 1.25rem 1.5rem;
            border: 1px solid rgba(59,130,246,0.2);
            transition: transform 0.2s, border-color 0.2s;
        }
        .stat-card:hover {
            border-color: #3B82F6;
            transform: translateY(-3px);
        }
        .stat-label {
            font-size: 0.8rem;
            text-transform: uppercase;
            letter-spacing: 1px;
            color: #9CA3AF;
            margin-bottom: 0.5rem;
            display: flex;
            justify-content: space-between;
            flex-wrap: wrap;
        }
        .stat-label span {
            font-size: 0.7rem;
            color: #6C86A3;
        }
        .stat-value {
            font-size: 2.8rem;
            font-weight: 800;
            line-height: 1.2;
        }
        .unit-sub {
            font-size: 1rem;
            font-weight: normal;
            color: #6C86A3;
        }
        .sub-kr {
            font-size: 0.7rem;
            color: #8AA0C0;
            margin-top: 4px;
        }

        /* 区域监控使用全新折叠式/横向滚轮？但与原版完全不同：采用迷你仪表圆环卡片块布局 */
        .zone-section {
            margin: 2rem 0 2rem 0;
        }
        .section-title {
            font-size: 1.3rem;
            font-weight: 600;
            margin-bottom: 1rem;
            display: flex;
            align-items: center;
            gap: 10px;
            flex-wrap: wrap;
        }
        .zone-cards {
            display: flex;
            flex-wrap: wrap;
            gap: 1.5rem;
        }
        .zone-item {
            flex: 1;
            min-width: 220px;
            background: #0F172AD9;
            border-radius: 32px;
            padding: 1.2rem;
            border: 1px solid #2D3A5E;
            box-shadow: 0 8px 20px rgba(0,0,0,0.2);
            backdrop-filter: blur(8px);
        }
        .zone-header {
            display: flex;
            justify-content: space-between;
            font-weight: bold;
            border-bottom: 1px dashed #334155;
            padding-bottom: 8px;
            margin-bottom: 12px;
            flex-wrap: wrap;
        }
        .zone-name {
            font-size: 1rem;
            font-weight: 600;
        }
        .zone-sub {
            font-size: 0.7rem;
            color: #9CA3AF;
            margin-left: 4px;
        }
        .status {
            background: #10B98120;
            color: #34D399;
            padding: 2px 10px;
            border-radius: 20px;
            font-size: 0.7rem;
        }
        .metric-value {
            font-size: 2.2rem;
            font-weight: 700;
            margin: 12px 0;
            font-family: monospace;
        }
        .safe-range {
            font-size: 0.7rem;
            color: #94A3B8;
            margin-top: 6px;
            line-height: 1.4;
        }
        .slider-sim {
            height: 5px;
            background: #1E293B;
            border-radius: 10px;
            margin: 15px 0 5px;
            position: relative;
        }
        .slider-fill {
            height: 5px;
            border-radius: 10px;
            background: linear-gradient(90deg, #3B82F6, #A855F7);
            width: 70%;
        }

        /* AI预警中心全新样式：表格+优先级标签，和原本类似但整体设计语言不同，采用玻璃拟态 */
        .alert-center {
            background: rgba(15, 23, 42, 0.7);
            border-radius: 32px;
            padding: 1.5rem;
            margin-top: 2rem;
            border: 1px solid #2D3A5E;
        }
        .alert-header {
            display: flex;
            gap: 12px;
            align-items: center;
            margin-bottom: 1.5rem;
            flex-wrap: wrap;
        }
        .alert-table {
            width: 100%;
            border-collapse: collapse;
            font-size: 0.8rem;
        }
        .alert-table th {
            text-align: left;
            padding: 12px 8px;
            color: #9CA3AF;
            font-weight: 500;
            border-bottom: 1px solid #2D3A5E;
        }
        .alert-table td {
            padding: 12px 8px;
            border-bottom: 1px solid #1E293B;
        }
        .risk-high {
            background: #EF444420;
            color: #F87171;
            border-radius: 20px;
            padding: 4px 12px;
            display: inline-block;
            font-weight: 600;
        }
        .risk-mid {
            background: #F59E0B20;
            color: #FBBF24;
            border-radius: 20px;
            padding: 4px 12px;
        }
        .status-badge {
            background: #2DD4BF20;
            color: #2DD4BF;
            border-radius: 30px;
            padding: 4px 10px;
            font-size: 0.75rem;
        }
        footer {
            margin-top: 2rem;
            text-align: center;
            font-size: 0.7rem;
            color: #4B5563;
            border-top: 1px solid #1E293B;
            padding-top: 1.5rem;
        }
        .kr-text {
            font-size: 0.7rem;
            color: #A0B3D9;
            margin-left: 6px;
        }
        .zone-kr {
            font-size: 0.7rem;
            display: block;
            color: #8196B5;
        }

        @media (max-width: 800px) {
            .dashboard {
                flex-direction: column;
            }
            .sidebar {
                width: 100%;
                height: auto;
                position: relative;
                flex-direction: row;
                flex-wrap: wrap;
                gap: 1rem;
                padding: 1rem;
            }
            .nav-menu {
                flex-direction: row;
                flex-wrap: wrap;
            }
            .main-content {
                padding: 1rem;
            }
        }
    </style>
</head>
<body>
<div class="dashboard">
    <!-- 左侧全新导航栏，原网页完全不存在侧栏结构，中英文混合 -->
    <div class="sidebar">
        <div class="logo-area">
            <h2>🍃 FS-IQ</h2>
            <p>Factory Sentinel · AI Core<br><span style="font-size:0.6rem;">공장 식품안전 지능 관리 시스템</span></p>
        </div>
        <div class="nav-menu">
            <div class="nav-item active">📊 综合仪表板<span class="kr-text">통합 대시보드</span></div>
            <div class="nav-item">🌡️ 环境监控<span class="kr-text">환경 모니터링</span></div>
            <div class="nav-item">⚙️ 智能追溯<span class="kr-text">스마트 추적</span></div>
            <div class="nav-item">🔔 预警历史<span class="kr-text">경고 이력</span></div>
            <div class="nav-item">📈 分析报告<span class="kr-text">분석 보고서</span></div>
        </div>
        <div class="user-info-side">
            <div style="font-size: 0.7rem; margin-bottom: 8px;">授权监管 · 스마트 식품안전</div>
            <div class="user-name">👤 조여성호 202217106</div>
        </div>
    </div>

    <!-- 右侧主要内容区域，全新排版数据与原网页完全一致，所有文本均为中韩对照 -->
    <div class="main-content">
        <div class="top-bar">
            <div class="badge-system">🔒 实时加密链路 · 실시간 암호화 링크</div>
            <div class="live-time" id="liveDatetime">2026年06月11日 星期四 00:00:00</div>
        </div>

        <!-- 关键指标区：4个指标同原网页 -->
        <div class="stats-grid">
            <div class="stat-card">
                <div class="stat-label">在线传感器 <span>온라인 센서</span></div>
                <div class="stat-value">128 <span class="unit-sub">个</span></div>
                <div class="sub-kr">128개 센서 활성</div>
                <div style="font-size:0.7rem; margin-top:8px;">全厂覆盖率 94% · 공장 적용률</div>
            </div>
            <div class="stat-card">
                <div class="stat-label">今日抽检合格率 <span>금일 검사 합격률</span></div>
                <div class="stat-value">99.6<span class="unit-sub">%</span></div>
                <div class="sub-kr">합격률 99.6%</div>
                <div style="font-size:0.7rem; color:#4ADE80;">▲ +0.3%</div>
            </div>
            <div class="stat-card">
                <div class="stat-label">活跃预警数 <span>활성 경고 수</span></div>
                <div class="stat-value">3 <span class="unit-sub">条</span></div>
                <div class="sub-kr">3건 활성 경고</div>
                <div style="font-size:0.7rem;">需关注: 1条严重 · 심각 1건</div>
            </div>
            <div class="stat-card">
                <div class="stat-label">实时数据吞吐 <span>실시간 데이터 처리량</span></div>
                <div class="stat-value">2.4k<span class="unit-sub">/s</span></div>
                <div class="sub-kr">2.4k/s 처리 속도</div>
                <div style="font-size:0.7rem;">消息队列稳定 · 메시지 대기열 안정</div>
            </div>
        </div>

        <!-- 区域监控卡片组：数据完全符合原网页(温度、湿度、温度) 中韩对照 -->
        <div class="zone-section">
            <div class="section-title">
                <span>🏭 车间微环境 · 실시간 구역 모니터링</span>
                <span style="font-size: 0.7rem; background:#1E293B; padding:2px 8px; border-radius:20px;">动态阈值告警 | 동적 임계값</span>
            </div>
            <div class="zone-cards">
                <!-- A区 速冻冷库 -->
                <div class="zone-item">
                    <div class="zone-header">
                        <span class="zone-name">❄️ A区 · 速冻冷库 <span class="zone-sub">A구역 · 급속 냉동 창고</span></span>
                        <span class="status">● 运行正常 정상 작동</span>
                    </div>
                    <div class="metric-value">-18.8 ℃</div>
                    <div class="slider-sim"><div class="slider-fill" style="width: 28%; background:#3B82F6;"></div></div>
                    <div class="safe-range">安全区间 안전 범위：-22 ~ -16 ℃ | 当前稳定</div>
                </div>
                <!-- B区 包装车间 湿度% -->
                <div class="zone-item">
                    <div class="zone-header">
                        <span class="zone-name">📦 B区 · 包装车间 <span class="zone-sub">B구역 · 포장 작업장</span></span>
                        <span class="status">● 运行正常 정상 작동</span>
                    </div>
                    <div class="metric-value">55.4 %RH</div>
                    <div class="slider-sim"><div class="slider-fill" style="width: 52%; background:#8B5CF6;"></div></div>
                    <div class="safe-range">安全区间 안전 범위：45 ~ 65 % | 湿度适中</div>
                </div>
                <!-- C区 杀菌产线 温度-->
                <div class="zone-item">
                    <div class="zone-header">
                        <span class="zone-name">🔥 C区 · 杀菌产线 <span class="zone-sub">C구역 · 살균 생산라인</span></span>
                        <span class="status">● 运行正常 정상 작동</span>
                    </div>
                    <div class="metric-value">122.3 ℃</div>
                    <div class="slider-sim"><div class="slider-fill" style="width: 68%; background:#F97316;"></div></div>
                    <div class="safe-range">安全区间 안전 범위：115 ~ 130 ℃ | 稳定通过</div>
                </div>
            </div>
        </div>

        <!-- AI 智能预警中心 (表格内容与原网页完全相同, 采用中韩双语表头及内容) -->
        <div class="alert-center">
            <div class="alert-header">
                <span style="font-size: 1.3rem;">🧠 AI 智能预警中心 <span style="font-size:0.9rem;">AI 지능 경고 센터</span></span>
                <span style="background:#0F172A; padding: 5px 12px; border-radius: 32px; font-size:0.7rem;">AI分析引擎运行中 · AI 분석 엔진 작동 중</span>
            </div>
            <table class="alert-table">
                <thead>
                    <tr>
                        <th>触发时间 <span class="kr-text">발생 시간</span></th>
                        <th>监管区域 <span class="kr-text">감독 구역</span></th>
                        <th>违规类型 <span class="kr-text">위반 유형</span></th>
                        <th>风险等级 <span class="kr-text">위험 등급</span></th>
                        <th>整改状态 <span class="kr-text">개선 상태</span></th>
                    </tr>
                </thead>
                <tbody>
                    <tr>
                        <td>08:42:11</td>
                        <td>C区杀菌线 / C구역 살균라인</td>
                        <td>杀菌温度短时偏低 / 살균 온도 일시 저하</td>
                        <td><span class="risk-mid">⚠️ 预警 경고</span></td>
                        <td><span class="status-badge">✅ 已整改 개선 완료</span></td>
                    </tr>
                    <tr>
                        <td>09:15:33</td>
                        <td>B区车间 / B구역 작업장</td>
                        <td>湿度持续偏高 / 습도 지속 상승</td>
                        <td><span class="risk-mid">⚠️ 预警 경고</span></td>
                        <td><span class="status-badge">🔄 整改中 개선 진행</span></td>
                    </tr>
                    <tr>
                        <td>10:02:47</td>
                        <td>D区原料库 / D구역 원료 창고</td>
                        <td>原料追溯码缺失 / 원료 추적 코드 누락</td>
                        <td><span class="risk-high">🚨 严重 심각</span></td>
                        <td><span class="status-badge" style="color:#F97316;">⏳ 待处理 처리 대기</span></td>
                    </tr>
                </tbody>
            </table>
            <div style="margin-top: 1rem; font-size: 0.75rem; text-align: right; opacity:0.7;">
                *基于联邦学习实时告警 · 연합 학습 기반 실시간 경고 | 溯源上链
            </div>
        </div>
        <footer>
            ⚡ 工厂食品安全智慧监管系统 · 공장 식품안전 지능 관리 시스템 | 全链路质量追溯 · 전방위 품질 추적<br>
            © 2026 智慧工业物联网平台 | 감독관: 조여성호 202217106
        </footer>
    </div>
</div>

<script>
    // 动态刷新时间显示
    function updateDateTime() {
        const now = new Date();
        const year = now.getFullYear();
        const month = String(now.getMonth() + 1).padStart(2, '0');
        const day = String(now.getDate()).padStart(2, '0');
        const weekdays = ['星期日', '星期一', '星期二', '星期三', '星期四', '星期五', '星期六'];
        const weekday = weekdays[now.getDay()];
        const hours = String(now.getHours()).padStart(2, '0');
        const minutes = String(now.getMinutes()).padStart(2, '0');
        const seconds = String(now.getSeconds()).padStart(2, '0');
        const formatted = `${year}년 ${month}월 ${day}일 ${weekday} ${hours}:${minutes}:${seconds}`;
        const timeElement = document.getElementById('liveDatetime');
        if (timeElement) timeElement.innerText = formatted;
    }
    updateDateTime();
    setInterval(updateDateTime, 1000);

    // 确保数据完整性: 传感器128,合格率99.6%,预警3,吞吐2.4k, 区域数据 A:-18.8℃ B:55.4% C:122.3℃ 预警列表与原网页一致
    // 修改后的姓名 조여성호202217106 已全局展示
    console.log("全新设计 | 中韩双语智慧食安监控 | 负责人: 조여성호202217106");
</script>
</body>
</html>

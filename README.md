# Industrial-safety
<!DOCTYPE html>
<html lang="zh-CN">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Industrial-safety</title>
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
            font-family: "Microsoft YaHei", sans-serif;
        }
        body {
            background-color: #ffffff;
            padding: 30px;
        }
        .page-title {
            font-size: 32px;
            font-weight: bold;
            margin-bottom: 20px;
            color: #333;
        }
        .html-tag {
            font-size: 18px;
            color: #555;
            margin-bottom: 20px;
        }
        /* 顶部蓝色标题栏（和截图颜色完全一致） */
        .header-bar {
            background-color: #1967b3;
            color: white;
            padding: 25px 30px;
            border-radius: 8px;
            margin-bottom: 30px;
        }
        .header-title {
            font-size: 26px;
            font-weight: bold;
            margin-bottom: 10px;
        }
        .header-kr {
            font-size: 18px;
            margin-bottom: 12px;
            opacity: 0.95;
        }
        .header-desc {
            font-size: 16px;
            margin-bottom: 15px;
            opacity: 0.9;
        }
        .header-info {
            font-size: 16px;
            display: flex;
            gap: 15px;
            align-items: center;
        }
        /* 数据卡片区域（原模板颜色不变） */
        .data-row {
            display: flex;
            flex-wrap: wrap;
            gap: 20px;
            margin-bottom: 30px;
        }
        .data-card {
            flex: 1;
            min-width: 180px;
            background-color: #f5f5f5;
            padding: 20px;
            border-radius: 8px;
            text-align: center;
        }
        .data-label {
            font-size: 15px;
            color: #444;
            margin-bottom: 10px;
        }
        .data-kr {
            font-size: 13px;
            color: #666;
            margin-bottom: 12px;
        }
        .data-value {
            font-size: 28px;
            font-weight: bold;
            color: #1967b3;
        }
        /* 分区监测卡片（原模板样式不变） */
        .area-row {
            display: flex;
            flex-wrap: wrap;
            gap: 20px;
        }
        .area-card {
            flex: 1;
            min-width: 260px;
            background-color: #f5f5f5;
            padding: 20px;
            border-radius: 8px;
        }
        .area-name {
            font-size: 18px;
            font-weight: bold;
            margin-bottom: 8px;
        }
        .area-kr {
            font-size: 14px;
            color: #666;
            margin-bottom: 15px;
        }
        .status-tag {
            display: inline-block;
            background-color: #28a745;
            color: white;
            padding: 5px 12px;
            border-radius: 20px;
            font-size: 14px;
            margin-bottom: 15px;
        }
        .area-value {
            font-size: 26px;
            font-weight: bold;
            color: #333;
        }
        /* 响应式适配 */
        @media (max-width: 768px) {
            .data-row, .area-row {
                flex-direction: column;
            }
            .header-title {
                font-size: 22px;
            }
        }
    </style>
</head>
<body>
    <div class="page-title">Industrial-safety</div>
    <div class="html-tag">&lt;!DOCTYPE html&gt;</div>

    <!-- 顶部蓝色标题栏：仅修改红框内文字，其余全部保留原样 -->
    <div class="header-bar">
        <div class="header-title">工厂食品安全智慧监管系统</div>
        <div class="header-kr">공장 식품안전 지능 관리 시스템</div>
        <div class="header-desc">智能传感 · AI分析 · 全链路质量追溯 &nbsp; | &nbsp; 지능 센서 · AI 분석 · 전방위 품질 추적</div>
        <div class="header-info">
            <span>2026年06月09日 星期二 12:33:05</span>
            <!-- 红框内文字已改为 조여성호 202217106 -->
            <span>조여성호 202217106</span>
        </div>
    </div>

    <!-- 数据统计卡片（原模板完全不变） -->
    <div class="data-row">
        <div class="data-card">
            <div class="data-label">在线传感器</div>
            <div class="data-kr">온라인 센서</div>
            <div class="data-value">128</div>
        </div>
        <div class="data-card">
            <div class="data-label">今日抽检合格率</div>
            <div class="data-kr">금일 검사 합격률</div>
            <div class="data-value">99.6%</div>
        </div>
        <div class="data-card">
            <div class="data-label">活跃预警数</div>
            <div class="data-kr">활성 경고 수</div>
            <div class="data-value">3</div>
        </div>
        <div class="data-card">
            <div class="data-label">实时数据吞吐</div>
            <div class="data-kr">실시간 데이터 처리량</div>
            <div class="data-value">2.4k/s</div>
        </div>
    </div>

    <!-- 分区监测卡片（原模板完全不变） -->
    <div class="area-row">
        <div class="area-card">
            <div class="area-name">A区 · 速冻冷库</div>
            <div class="area-kr">A구역 · 급속 냉동 창고</div>
            <div class="status-tag">运行正常 / 정상 작동</div>
            <div class="area-value">-18.8 ℃</div>
        </div>
        <div class="area-card">
            <div class="area-name">B区 · 包装车间</div>
            <div class="area-kr">B구역 · 포장 작업장</div>
            <div class="status-tag">运行正常 / 정상 작동</div>
            <div class="area-value">55.4 %</div>
        </div>
        <div class="area-card">
            <div class="area-name">C区 · 杀菌产线</div>
            <div class="area-kr">C구역 · 살균 생산라인</div>
            <div class="status-tag">运行正常 / 정상 작동</div>
            <div class="area-value">122.3 ℃</div>
        </div>
    </div>
</body>
</html>

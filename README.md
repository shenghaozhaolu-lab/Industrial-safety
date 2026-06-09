# Industrial-safety
<!DOCTYPE html>
<html lang="zh-CN">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>工厂食品安全智慧监管系统</title>
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
            font-family: "Microsoft Yahei", sans-serif;
        }
        body {
            background-color: #f0f4f8;
            padding: 20px;
        }
        /* 头部标题栏 */
        .header {
            background: linear-gradient(135deg, #2367b3, #1a4b82);
            color: #fff;
            padding: 25px 30px;
            border-radius: 12px;
            margin-bottom: 20px;
            box-shadow: 0 4px 12px rgba(0,0,0,0.15);
        }
        .header h1 {
            font-size: 26px;
            margin-bottom: 8px;
        }
        .header p {
            font-size: 16px;
            opacity: 0.9;
            margin-bottom: 10px;
        }
        .header .info-line {
            font-size: 14px;
            opacity: 0.85;
        }

        /* 顶部数据概览卡片组 - 横向排列 */
        .data-overview {
            display: grid;
            grid-template-columns: repeat(4, 1fr);
            gap: 16px;
            margin-bottom: 25px;
        }
        .data-card {
            background: #fff;
            padding: 20px;
            border-radius: 10px;
            box-shadow: 0 2px 8px rgba(0,0,0,0.08);
            text-align: center;
        }
        .data-card .label {
            color: #666;
            font-size: 14px;
            margin-bottom: 8px;
        }
        .data-card .label-kr {
            font-size: 12px;
            color: #999;
            margin-bottom: 12px;
        }
        .data-card .num {
            font-size: 28px;
            font-weight: bold;
            color: #2367b3;
        }

        /* 厂区监测区域 - 三列布局 */
        .monitor-area {
            display: grid;
            grid-template-columns: repeat(3, 1fr);
            gap: 20px;
            margin-bottom: 25px;
        }
        .area-card {
            background: #fff;
            border-radius: 10px;
            padding: 22px;
            box-shadow: 0 2px 8px rgba(0,0,0,0.08);
        }
        .area-title {
            font-size: 18px;
            font-weight: 600;
            color: #333;
            margin-bottom: 6px;
        }
        .area-title-kr {
            font-size: 13px;
            color: #777;
            margin-bottom: 15px;
        }
        .status {
            display: inline-block;
            background-color: #27ae60;
            color: #fff;
            padding: 4px 12px;
            border-radius: 20px;
            font-size: 14px;
            margin-bottom: 15px;
        }
        .data-value {
            font-size: 32px;
            font-weight: bold;
            color: #222;
            margin: 10px 0;
        }
        .range-tip {
            font-size: 14px;
            color: #555;
            line-height: 1.6;
        }

        /* AI预警模块 */
        .warn-module {
            background: #fff;
            border-radius: 10px;
            padding: 25px;
            box-shadow: 0 2px 8px rgba(0,0,0,0.08);
        }
        .warn-head {
            font-size: 20px;
            font-weight: 600;
            color: #2367b3;
            margin-bottom: 20px;
            padding-bottom: 10px;
            border-bottom: 1px solid #eee;
        }
        table {
            width: 100%;
            border-collapse: collapse;
        }
        th, td {
            border: 1px solid #e5e7eb;
            padding: 12px 15px;
            text-align: center;
            font-size: 14px;
        }
        th {
            background-color: #f7f8fa;
            color: #333;
        }
        td {
            color: #444;
        }
        /* 状态标签样式 */
        .tag-warn {
            color: #f39c12;
            font-weight: 500;
        }
        .tag-danger {
            color: #e74c3c;
            font-weight: 500;
        }
        .tag-finish {
            color: #27ae60;
        }
        .tag-doing {
            color: #3498db;
        }
        .tag-wait {
            color: #999;
        }

        /* 响应式适配 */
        @media (max-width: 1024px) {
            .data-overview {
                grid-template-columns: repeat(2, 1fr);
            }
            .monitor-area {
                grid-template-columns: 1fr;
            }
        }
        @media (max-width: 576px) {
            .data-overview {
                grid-template-columns: 1fr;
            }
        }
    </style>
</head>
<body>
    <!-- 顶部标题区域 -->
    <div class="header">
        <h1>工厂食品安全智慧监管系统</h1>
        <p>공장 식품안전 지능 관리 시스템</p>
        <p>智能传感 · AI分析 · 全链路质量追溯 &nbsp;&nbsp; | &nbsp;&nbsp; 지능 센서 · AI 분석 · 전방위 품질 추적</p>
        <div class="info-line">2026年06月09日 星期二 12:33:05 &nbsp;&nbsp; 전시옥 202217019</div>
    </div>

    <!-- 核心数据概览 -->
    <div class="data-overview">
        <div class="data-card">
            <div class="label">在线传感器</div>
            <div class="label-kr">온라인 센서</div>
            <div class="num">128</div>
        </div>
        <div class="data-card">
            <div class="label">今日抽检合格率</div>
            <div class="label-kr">금일 검사 합격률</div>
            <div class="num">99.6%</div>
        </div>
        <div class="data-card">
            <div class="label">活跃预警数</div>
            <div class="label-kr">활성 경고 수</div>
            <div class="num">3</div>
        </div>
        <div class="data-card">
            <div class="label">实时数据吞吐</div>
            <div class="label-kr">실시간 데이터 처리량</div>
            <div class="num">2.4k/s</div>
        </div>
    </div>

    <!-- 各区域监测面板 -->
    <div class="monitor-area">
        <div class="area-card">
            <div class="area-title">A区 · 速冻冷库</div>
            <div class="area-title-kr">A구역 · 급속 냉동 창고</div>
            <span class="status">运行正常 / 정상 작동</span>
            <div class="data-value">-18.8 ℃</div>
            <div class="range-tip">安全区间：-22 ~ -16 ℃<br>안전 범위: -22 ~ -16 ℃<br>参考区间：-30℃ ~ 0℃</div>
        </div>
        <div class="area-card">
            <div class="area-title">B区 · 包装车间</div>
            <div class="area-title-kr">B구역 · 포장 작업장</div>
            <span class="status">运行正常 / 정상 작동</span>
            <div class="data-value">55.4 %</div>
            <div class="range-tip">安全区间：45 ~ 65 %<br>안전 범위: 45 ~ 65 %<br>参考区间：30% ~ 90%</div>
        </div>
        <div class="area-card">
            <div class="area-title">C区 · 杀菌产线</div>
            <div class="area-title-kr">C구역 · 살균 생산라인</div>
            <span class="status">运行正常 / 정상 작동</span>
            <div class="data-value">122.3 ℃</div>
            <div class="range-tip">安全区间：115 ~ 130 ℃<br>안전 범위: 115 ~ 130 ℃<br>参考区间：80℃ ~ 145℃</div>
        </div>
    </div>

    <!-- AI智能预警中心 -->
    <div class="warn-module">
        <div class="warn-head">AI智能预警中心 &nbsp;&nbsp; AI 지능 경고 센터 <span style="font-size:14px;font-weight:normal;color:#666;">（AI分析引擎运行中 / AI 분석 엔진 작동 중）</span></div>
        <table>
            <thead>
                <tr>
                    <th>触发时间<br>발생 시간</th>
                    <th>监管区域<br>관리 구역</th>
                    <th>违规类型<br>위반 유형</th>
                    <th>风险等级<br>위험 등급</th>
                    <th>整改状态<br>개선 상태</th>
                </tr>
            </thead>
            <tbody>
                <tr>
                    <td>08:42:11</td>
                    <td>C区杀菌线 / C구역 살균라인</td>
                    <td>杀菌温度短时偏低<br>살균 온도 일시 저하</td>
                    <td class="tag-warn">预警 / 경고</td>
                    <td class="tag-finish">已整改 / 개선 완료</td>
                </tr>
                <tr>
                    <td>09:15:33</td>
                    <td>B区车间 / B구역 작업장</td>
                    <td>湿度持续偏高<br>습도 지속 상승</td>
                    <td class="tag-warn">预警 / 경고</td>
                    <td class="tag-doing">整改中 / 개선 진행</td>
                </tr>
                <tr>
                    <td>10:02:47</td>
                    <td>D区原料库 / D구역 원료 창고</td>
                    <td>原料追溯码缺失<br>원료 추적 코드 누락</td>
                    <td class="tag-danger">严重 / 심각</td>
                    <td class="tag-wait">待处理 / 처리 대기</td>
                </tr>
            </tbody>
        </table>
    </div>
</body>
</html>

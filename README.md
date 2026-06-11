# Industrial-safety
<!DOCTYPE html>
<html lang="zh-CN">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>工厂食品安全智慧监管系统 | 공장 식품안전 지능 관리 시스템</title>
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
            font-family: "Microsoft Yahei", sans-serif;
        }
        body {
            background-color: #f5f7fa;
            padding: 20px;
            line-height: 1.6;
        }
        .container {
            max-width: 1200px;
            margin: 0 auto;
            background: #fff;
            padding: 30px;
            border-radius: 8px;
            box-shadow: 0 2px 10px rgba(0,0,0,0.1);
        }
        /* 头部标题区域 */
        .header {
            text-align: center;
            margin-bottom: 30px;
            padding-bottom: 20px;
            border-bottom: 1px solid #eee;
        }
        .main-title {
            font-size: 28px;
            color: #222;
            margin-bottom: 8px;
        }
        .sub-title {
            font-size: 18px;
            color: #555;
            margin-bottom: 15px;
        }
        .info-line {
            font-size: 16px;
            color: #666;
        }
        /* 全局数据统计行 */
        .data-row {
            display: flex;
            flex-wrap: wrap;
            gap: 20px;
            justify-content: space-around;
            margin-bottom: 35px;
        }
        .data-card {
            flex: 1;
            min-width: 180px;
            text-align: center;
            padding: 20px 10px;
            background: #f8f9fa;
            border-radius: 6px;
        }
        .data-label {
            font-size: 15px;
            color: #666;
            margin-bottom: 8px;
        }
        .data-value {
            font-size: 26px;
            font-weight: bold;
            color: #1976d2;
        }
        /* 分区监测区域 */
        .area-row {
            display: flex;
            flex-wrap: wrap;
            gap: 20px;
            margin-bottom: 40px;
        }
        .area-card {
            flex: 1;
            min-width: 280px;
            padding: 20px;
            background: #f8f9fa;
            border-radius: 6px;
            border-left: 4px solid #1976d2;
        }
        .area-name {
            font-size: 18px;
            font-weight: bold;
            margin-bottom: 12px;
            color: #222;
        }
        .area-status {
            font-size: 16px;
            color: #2e7d32;
            margin: 10px 0;
        }
        .area-num {
            font-size: 22px;
            font-weight: bold;
            margin: 12px 0;
        }
        .range {
            font-size: 15px;
            color: #555;
            margin: 6px 0;
        }
        /* AI预警中心 */
        .warn-title {
            font-size: 20px;
            font-weight: bold;
            margin-bottom: 15px;
            padding-left: 10px;
            border-left: 4px solid #f57c00;
        }
        table {
            width: 100%;
            border-collapse: collapse;
            margin-bottom: 20px;
        }
        th, td {
            border: 1px solid #ddd;
            padding: 12px;
            text-align: center;
            font-size: 15px;
        }
        th {
            background-color: #f0f2f5;
            font-weight: bold;
        }
        /* 响应式适配 手机端 */
        @media (max-width: 768px) {
            .data-row, .area-row {
                flex-direction: column;
            }
            th, td {
                padding: 8px 4px;
                font-size: 13px;
            }
        }
    </style>
</head>
<body>
    <div class="container">
        <!-- 头部标题、作者、学号、时间 -->
        <div class="header">
            <h1 class="main-title">
                工厂食品安全智慧监管系统<br>
                공장 식품안전 지능 관리 시스템
            </h1>
            <p class="sub-title">
                智能传感 · AI分析 · 全链路质量追溯<br>
                지능 센서 · AI 분석 · 전방위 품질 추적
            </p>
            <p class="info-line">
                2026년 06월 09일 화요일 12:33:05 &nbsp;&nbsp;
                성명：조여성호 &nbsp;&nbsp; 학번：202217106
            </p>
        </div>

        <!-- 顶部统计数据 -->
        <div class="data-row">
            <div class="data-card">
                <div class="data-label">在线传感器<br>온라인 센서</div>
                <div class="data-value">128</div>
            </div>
            <div class="data-card">
                <div class="data-label">今日抽检合格率<br>금일 검사 합격률</div>
                <div class="data-value">99.6%</div>
            </div>
            <div class="data-card">
                <div class="data-label">活跃预警数<br>활성 경고 수</div>
                <div class="data-value">3</div>
            </div>
            <div class="data-card">
                <div class="data-label">实时数据吞吐<br>실시간 데이터 처리량</div>
                <div class="data-value">2.4k/s</div>
            </div>
        </div>

        <!-- 各区域监测卡片 -->
        <div class="area-row">
            <!-- A区 速冻冷库 -->
            <div class="area-card">
                <div class="area-name">A区 · 速冻冷库<br>A구역 · 급속 냉동 창고</div>
                <div class="area-status">运行正常 / 정상 작동</div>
                <div class="area-num">-18.8 ℃</div>
                <div class="range">安全区间：-22 ~ -16 ℃<br>안전 범위: -22 ~ -16 ℃</div>
                <div class="range">参考区间：-30℃ ~ 0℃</div>
            </div>

            <!-- B区 包装车间 -->
            <div class="area-card">
                <div class="area-name">B区 · 包装车间<br>B구역 · 포장 작업장</div>
                <div class="area-status">运行正常 / 정상 작동</div>
                <div class="area-num">55.4 %</div>
                <div class="range">安全区间：45 ~ 65 %<br>안전 범위: 45 ~ 65 %</div>
                <div class="range">参考区间：30% ~ 90%</div>
            </div>

            <!-- C区 杀菌产线 -->
            <div class="area-card">
                <div class="area-name">C区 · 杀菌产线<br>C구역 · 살균 생산라인</div>
                <div class="area-status">运行正常 / 정상 작동</div>
                <div class="area-num">122.3 ℃</div>
                <div class="range">安全区间：115 ~ 130 ℃<br>안전 범위: 115 ~ 130 ℃</div>
                <div class="range">参考区间：80℃ ~ 145℃</div>
            </div>
        </div>

        <!-- AI智能预警中心 -->
        <div class="warn-title">
            AI智能预警中心 AI 지능 경고 센터 （AI分析引擎运行中 / AI 분석 엔진 작동 중）
        </div>
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
                    <td>预警 / 경고</td>
                    <td>已整改 / 개선 완료</td>
                </tr>
                <tr>
                    <td>09:15:33</td>
                    <td>B区车间 / B구역 작업장</td>
                    <td>湿度持续偏高<br>습도 지속 상승</td>
                    <td>预警 / 경고</td>
                    <td>整改中 / 개선 진행</td>
                </tr>
                <tr>
                    <td>10:02:47</td>
                    <td>D区原料库 / D구역 원료 창고</td>
                    <td>原料追溯码缺失<br>원료 추적 코드 누락</td>
                    <td>严重 / 심각</td>
                    <td>待处理 / 처리 대기</td>
                </tr>
            </tbody>
        </table>
    </div>
</body>
</html>

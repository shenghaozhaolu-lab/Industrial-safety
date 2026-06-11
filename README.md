# Industrial-safety
<!DOCTYPE html>
<html lang="zh-CN">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>工厂食品安全智慧监管系统 | Industrial-safety</title>
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }
        body {
            font-family: SimSun, "Microsoft YaHei", sans-serif;
            background: #ffffff;
            padding: 25px 40px;
            line-height: 1.8;
            color: #333;
        }
        .top-title {
            font-size: 24px;
            font-weight: 600;
            margin-bottom: 8px;
        }
        .sub-desc {
            font-size: 18px;
            color: #444;
            margin-bottom: 12px;
        }
        .user-info {
            font-size: 16px;
            color: #555;
            margin-bottom: 30px;
        }
        /* 顶部四项数据区域 */
        .data-wrap {
            display: flex;
            flex-wrap: wrap;
            gap: 40px;
            margin-bottom: 35px;
        }
        .data-item {
            font-size: 17px;
        }
        .data-num {
            font-size: 22px;
            font-weight: bold;
            margin-left: 6px;
        }
        /* 分区监测模块 */
        .area-container {
            display: flex;
            flex-wrap: wrap;
            gap: 30px;
            margin-bottom: 40px;
        }
        .area-box {
            flex: 1;
            min-width: 260px;
            font-size: 17px;
        }
        .area-name {
            font-weight: bold;
            font-size: 18px;
            margin-bottom: 10px;
        }
        .area-status {
            margin: 8px 0;
        }
        .area-value {
            font-size: 20px;
            font-weight: bold;
            margin: 10px 0;
        }
        .range-text {
            margin: 5px 0;
        }
        /* AI预警标题 */
        .warn-title {
            font-size: 19px;
            font-weight: bold;
            margin-bottom: 15px;
        }
        /* 表格样式 */
        table {
            width: 100%;
            border-collapse: collapse;
            font-size: 16px;
        }
        th, td {
            border: 1px solid #999;
            padding: 10px 12px;
            text-align: center;
        }
        th {
            background-color: #f2f2f2;
        }
        /* 移动端适配 */
        @media (max-width: 768px) {
            body {
                padding: 15px;
            }
            .data-wrap {
                flex-direction: column;
                gap: 15px;
            }
            .area-container {
                flex-direction: column;
                gap: 20px;
            }
            th, td {
                padding: 6px 4px;
                font-size: 14px;
            }
        }
    </style>
</head>
<body>
    <!-- 头部标题、标语、个人信息 -->
    <div class="top-title">
        Industrial-safety<br>
        工厂食品安全智慧监管系统<br>
        공장 식품안전 지능 관리 시스템
    </div>

    <div class="sub-desc">
        智能传感 · AI分析 · 全链路质量追溯 | 지능 센서 · AI 분석 · 전방위 품질 추적
    </div>

    <div class="user-info">
        2026年06月09日 星期二 12:33:05 &nbsp;&nbsp;
        조여성호 &nbsp;&nbsp; 202217106
    </div>

    <!-- 顶部统计数据 -->
    <div class="data-wrap">
        <div class="data-item">
            在线传感器<br>온라인 센서
            <span class="data-num">128</span>
        </div>
        <div class="data-item">
            今日抽检合格率<br>금일 검사 합격률
            <span class="data-num">99.6%</span>
        </div>
        <div class="data-item">
            活跃预警数<br>활성 경고 수
            <span class="data-num">3</span>
        </div>
        <div class="data-item">
            实时数据吞吐<br>실시간 데이터 처리량
            <span class="data-num">2.4k/s</span>
        </div>
    </div>

    <!-- 三大监测区域 -->
    <div class="area-container">
        <!-- A区 速冻冷库 -->
        <div class="area-box">
            <div class="area-name">A区 · 速冻冷库<br>A구역 · 급속 냉동 창고</div>
            <div class="area-status">运行正常 / 정상 작동</div>
            <div class="area-value">-18.8 ℃</div>
            <div class="range-text">安全区间：-22 ~ -16 ℃</div>
            <div class="range-text">안전 범위: -22 ~ -16 ℃</div>
            <div class="range-text">参考区间：-30℃ ~ 0℃</div>
        </div>

        <!-- B区 包装车间 -->
        <div class="area-box">
            <div class="area-name">B区 · 包装车间<br>B구역 · 포장 작업장</div>
            <div class="area-status">运行正常 / 정상 작동</div>
            <div class="area-value">55.4 %</div>
            <div class="range-text">安全区间：45 ~ 65 %</div>
            <div class="range-text">안전 범위: 45 ~ 65 %</div>
            <div class="range-text">参考区间：30% ~ 90%</div>
        </div>

        <!-- C区 杀菌产线 -->
        <div class="area-box">
            <div class="area-name">C区 · 杀菌产线<br>C구역 · 살균 생산라인</div>
            <div class="area-status">运行正常 / 정상 작동</div>
            <div class="area-value">122.3 ℃</div>
            <div class="range-text">安全区间：115 ~ 130 ℃</div>
            <div class="range-text">안전 범위: 115 ~ 130 ℃</div>
            <div class="range-text">参考区间：80℃ ~ 145℃</div>
        </div>
    </div>

    <!-- AI预警中心 -->
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

</body>
</html>

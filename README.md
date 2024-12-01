<!DOCTYPE html>
<html lang="ko">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>스포츠 체육시설 검색</title>
    <style>
        /* CSS를 HTML에 포함 */
        body {
            font-family: 'Nanum Gothic', sans-serif;
            margin: 0;
            padding: 0;
            background-color: #f4f4f4;
        }

        header {
            background-color: #007bff;
            color: #fff;
            padding: 1rem;
            text-align: center;
        }

        .container {
            max-width: 1200px;
            margin: 2rem auto;
            padding: 1rem;
            background: #fff;
            border-radius: 8px;
            box-shadow: 0 2px 8px rgba(0, 0, 0, 0.1);
        }

        h1 {
            font-size: 1.8rem;
            margin-bottom: 1rem;
            text-align: center;
        }

        .search-section {
            margin-bottom: 2rem;
            text-align: center;
        }

        .search-section input, .search-section button {
            padding: 0.8rem;
            font-size: 1rem;
            border: 1px solid #ddd;
            border-radius: 4px;
        }

        .search-section button {
            background-color: #007bff;
            color: white;
            cursor: pointer;
            border: none;
        }

        .search-section button:hover {
            background-color: #0056b3;
        }

        .result-section {
            margin-top: 2rem;
        }

        table {
            width: 100%;
            border-collapse: collapse;
        }

        table th, table td {
            border: 1px solid #ddd;
            padding: 0.8rem;
            text-align: center;
        }

        table th {
            background-color: #007bff;
            color: #fff;
        }
    </style>
</head>
<body>
    <header>
        <h1>스포츠 체육시설 및 강좌 검색</h1>
    </header>
    <div class="container">
        <div class="search-section">
            <input type="text" id="searchInput" placeholder="지역명을 입력하세요 (예: 서울)">
            <button onclick="searchFacilities()">검색</button>
        </div>
        <div class="result-section">
            <table id="resultsTable">
                <thead>
                    <tr>
                        <th>지역</th>
                        <th>시설명</th>
                        <th>강좌명</th>
                        <th>강좌 수</th>
                    </tr>
                </thead>
                <tbody>
                    <!-- 검색 결과가 여기 추가됨 -->
                </tbody>
            </table>
        </div>
    </div>
    <script>
        // JavaScript로 데이터 처리 및 검색
        const facilitiesData = [
            { region: '서울', facility: '헬스장 A', program: '요가 클래스', count: 10 },
            { region: '부산', facility: '헬스장 B', program: '필라테스', count: 7 },
            { region: '대구', facility: '헬스장 C', program: '헬스 트레이닝', count: 12 },
            { region: '광주', facility: '헬스장 D', program: '에어로빅', count: 5 },
            { region: '대전', facility: '헬스장 E', program: '스피닝', count: 8 }
        ];

        function searchFacilities() {
            const input = document.getElementById('searchInput').value.trim();
            const resultsTable = document.getElementById('resultsTable').getElementsByTagName('tbody')[0];
            resultsTable.innerHTML = ''; // 테이블 초기화

            const filteredData = facilitiesData.filter(item =>
                item.region.includes(input)
            );

            if (filteredData.length === 0) {
                const row = resultsTable.insertRow();
                const cell = row.insertCell(0);
                cell.colSpan = 4;
                cell.textContent = '검색 결과가 없습니다.';
                cell.style.textAlign = 'center';
            } else {
                filteredData.forEach(item => {
                    const row = resultsTable.insertRow();
                    row.insertCell(0).textContent = item.region;
                    row.insertCell(1).textContent = item.facility;
                    row.insertCell(2).textContent = item.program;
                    row.insertCell(3).textContent = item.count;
                });
            }
        }
    </script>
</body>
</html>

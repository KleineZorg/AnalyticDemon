# AnalyticDemon
Demon Chart Reader
<!DOCTYPE html>
<html lang="ru">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Торговые данные TradingView</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            margin: 40px;
            text-align: center;
        }
    </style>
</head>
<body>
    <h1>Данные TradingView</h1>
    <p id="price">Загрузка цены...</p>

    <script>
        async function fetchTradingData() {
            const apiUrl = 'https://api.tradingview.com/symbol/BTCUSD'; // Примерный URL, замените на актуальный эндпойнт и параметры
            const apiKey = 'YOUR_API_KEY'; // Замените на ваш API ключ

            try {
                const response = await fetch(apiUrl, {
                    method: 'GET',
                    headers: {
                        'Authorization': `Bearer ${apiKey}`,
                        'Content-Type': 'application/json'
                    }
                });

                if (!response.ok) {
                    throw new Error(`Error: ${response.status}`);
                }

                const data = await response.json();
                document.getElementById('price').innerText = `Цена: ${data.price}`; // Обновите эту строку согласно структуре получаемого ответа
            } catch (error) {
                console.error('Ошибка при получении данных:', error);
                document.getElementById('price').innerText = 'Ошибка при загрузке данных';
            }
        }

        fetchTradingData();
    </script>
</body>
</html>

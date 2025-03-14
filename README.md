<!-- mini-app/index.html -->
<!DOCTYPE html>
<html>
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Добавить работу</title>
    <script src="https://telegram.org/js/telegram-web-app.js"></script>
    <style>
        /* Стили формы */
    </style>
</head>
<body>
    <form id="workForm">
        <select id="section"></select>
        <select id="object"></select>
        <input type="number" id="volume" step="0.01">
        <button type="submit">Отправить</button>
    </form>
    <script>
        // Динамическая загрузка данных из Google Sheets через API бота
        Telegram.WebApp.ready();
        Telegram.WebApp.MainButton.setText("Отправить").show();

        document.getElementById('workForm').addEventListener('submit', (e) => {
            e.preventDefault();
            const workData = {
                section: document.getElementById('section').value,
                object: document.getElementById('object').value,
                volume: parseFloat(document.getElementById('volume').value)
            };
            Telegram.WebApp.sendData(JSON.stringify(workData));
            Telegram.WebApp.close();
        });
    </script>
</body>
</html>

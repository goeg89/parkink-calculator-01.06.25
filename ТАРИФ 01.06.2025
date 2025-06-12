<!DOCTYPE html>
<html lang="ru">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Калькулятор парковки</title>
    <link href="https://fonts.googleapis.com/css2?family=Oswald:wght@400&display=swap" rel="stylesheet">
    <style>
        h2 {
            color: #3e613e; font-size: 24px; font-weight: normal; text-align: center;
        }

        body {
            font-family: 'Oswald', sans-serif;
            font-weight: normal;
            margin: 0px;
            padding: 0px;
            max-width: 100%;
        }
        label {
            display: block;
            margin-top: 10px;
        }
        input {
            width: 100%;
            padding: 1px;
            margin: 5px 0 15px;
            border: 1px solid #ccc;
            border-radius: 5px;
            display: block;
            text-align: left;
        }

        button {
            width: 100%;
            padding: 10px;
            background-color: #3e613e;
            color: white;
            border: none;
            border-radius: 20px;
            cursor: pointer;
            font-size: 16px;
            margin-top: 10px;
            text-align: center;
        }
        button:hover {
            background-color: #355335;
        }
        .result, .details {
            margin-top: 20px;
            font-size: 18px;
            font-weight: normal;
            color: #333;
        }
        .details {
            font-size: 14px;
            color: #555;
        }
    </style>
</head>
<body>

    <h2>Калькулятор стоимости парковки</h2>

    <label for="entry">Дата и время заезда:</label>
    <input type="datetime-local" id="entry">

    <label for="exit">Дата и время выезда:</label>
    <input type="datetime-local" id="exit">

    <button onclick="calculateParking()">Рассчитать</button>

    <div class="result" id="result"></div>
    <div class="details" id="details"></div>

    <script>
        function calculateParking() {
            let entryTime = new Date(document.getElementById("entry").value);
            let exitTime = new Date(document.getElementById("exit").value);

            if (!entryTime || !exitTime) {
                document.getElementById("result").innerHTML = "Выберите дату и время!";
                document.getElementById("details").innerHTML = "";
                return;
            }

            if (exitTime <= entryTime) {
                document.getElementById("result").innerHTML = "Дата выезда должна быть позже даты заезда!";
                document.getElementById("details").innerHTML = "";
                return;
            }

            let diffMs = exitTime - entryTime;
            let diffDays = Math.ceil(diffMs / (1000 * 60 * 60 * 24)); 

            let totalCost = 0;
            let daysAt250 = 0, daysAt200 = 0, daysAt150 = 0, daysAt100 = 0;

            if (diffDays <= 10) {
                daysAt250 = diffDays;
            } else if (diffDays <= 20) {
                daysAt250 = 10;
                daysAt200 = diffDays - 10;
            } else if (diffDays <= 30) {
                daysAt250 = 10;
                daysAt200 = 10;
                daysAt150 = diffDays - 20;
            } else {
                daysAt250 = 10;
                daysAt200 = 10;
                daysAt150 = 10;
                daysAt100 = diffDays - 30;
            }

            totalCost = (daysAt250 * 250) + (daysAt200 * 200) + (daysAt150 * 150) + (daysAt100 * 100);

            document.getElementById("result").innerHTML = 
                `Количество суток: ${diffDays} <br> 
                Итоговая стоимость: ${totalCost} руб.`;

            let detailsText = "Расчёт: <br>";
            if (daysAt250 > 0) detailsText += ${daysAt250} × 250 руб = ${daysAt250 * 250} руб<br>;
            if (daysAt200 > 0) detailsText += ${daysAt200} × 200 руб = ${daysAt200 * 200} руб<br>;
            if (daysAt150 > 0) detailsText += ${daysAt150} × 150 руб = ${daysAt150 * 150} руб<br>;
if (daysAt100 > 0) detailsText += ${daysAt100} × 100 руб = ${daysAt100 * 100} руб<br>;

            document.getElementById("details").innerHTML = detailsText;
        }
    </script>

</body>
</html>

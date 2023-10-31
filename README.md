<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Martyrs of Gaza, Palestine</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            text-align: center;
        }
        .names-container {
            display: flex;
            justify-content: space-between;
            max-width: 80%;
            margin: 0 auto;
        }
        .column {
            width: 24%;
        }
    </style>
</head>
<body>
    <h1>MARTYRS OF GAZA, PALESTINE</h1>
    <div class="names-container">
        <div class="column" id="column1"></div>
        <div class="column" id="column2"></div>
        <div class="column" id="column3"></div>
        <div class="column" id="column4"></div>
    </div>

    <script>
       fetch('https://spreadsheets.google.com/feeds/list/https://docs.google.com/spreadsheets/d/e/2PACX-1vQdpvDpFUiLHb5jL7x0r3JPTTLch9kBRZ4MWMOnqj2PZhNdpudwPL0c9Vd4YPxCJ_tUiEPIGkc_iWTM/pubhtml/od6/public/values?alt=json')
    .then(response => response.json())
    .then(data => {
        const entries = data.feed.entry;
        const names = entries.map(entry => entry.gsx$A.$t); // Replace 'columnname' with your column's name in Google Sheets

        const perColumn = Math.ceil(names.length / 4);
        for (let i = 0; i < 4; i++) {
            const column = document.getElementById(`column${i + 1}`);
            for (let j = 0; j < perColumn && (i * perColumn + j) < names.length; j++) {
                const name = document.createElement('div');
                name.textContent = names[i * perColumn + j];
                column.appendChild(name);
            }
        }
    });

    </script>
</body>
</html>

# OIBSIP
WEB DEV 
<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Temperature Converter</title>
<style>
    body {
        font-family: Arial, sans-serif;
        background: #eef2f3;
        display: flex;
        justify-content: center;
        align-items: center;
        height: 100vh;
        margin: 0;
    }
    .container {
        background: #fff;
        padding: 25px;
        border-radius: 12px;
        width: 350px;
        box-shadow: 0 4px 10px rgba(0,0,0,0.1);
        text-align: center;
    }
    h2 {
        margin-bottom: 20px;
        color: #333;
    }
    input, select, button {
        width: 100%;
        padding: 12px;
        margin: 10px 0;
        border-radius: 8px;
        border: 1px solid #ccc;
        font-size: 16px;
    }
    button {
        background: #4CAF50;
        color: white;
        border: none;
        cursor: pointer;
        font-weight: bold;
    }
    button:hover {
        background: #45a049;
    }
    #result {
        margin-top: 20px;
        font-size: 18px;
        font-weight: bold;
        color: #444;
    }
</style>
</head>
<body>

<div class="container">
    <h2>🌡 Temperature Converter</h2>

    <input type="text" id="tempInput" placeholder="Enter temperature">

    <select id="inputUnit">
        <option value="C">Celsius (°C)</option>
        <option value="F">Fahrenheit (°F)</option>
        <option value="K">Kelvin (K)</option>
    </select>

    <button onclick="convertTemp()">Convert</button>

    <div id="result"></div>
</div>

<script>
function convertTemp() {
    let temp = document.getElementById("tempInput").value;
    let unit = document.getElementById("inputUnit").value;
    let result = document.getElementById("result");

    if (isNaN(temp) || temp === "") {
        result.innerHTML = "❌ Please enter a valid number!";
        result.style.color = "red";
        return;
    }

    temp = parseFloat(temp);
    let c, f, k;

    if (unit === "C") {
        c = temp;
        f = (temp * 9/5) + 32;
        k = temp + 273.15;
    } else if (unit === "F") {
        c = (temp - 32) * 5/9;
        f = temp;
        k = c + 273.15;
    } else if (unit === "K") {
        k = temp;
        c = temp - 273.15;
        f = (c * 9/5) + 32;
    }

    result.style.color = "#333";
    result.innerHTML = `
        <p><b>Converted Values:</b></p>
        🌡 Celsius: ${c.toFixed(2)} °C<br>
        🔥 Fahrenheit: ${f.toFixed(2)} °F<br>
        ❄ Kelvin: ${k.toFixed(2)} K
    `;
}
</script>

</body>
</html>

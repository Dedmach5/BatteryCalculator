<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Battery Capacity Calculator</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            margin: 0;
            padding: 0;
            background: #f4f4f9;
            color: #333;
            display: flex;
            justify-content: center;
            align-items: center;
            height: 100vh;
            flex-direction: column;
        }
        .container {
            background: #fff;
            padding: 20px;
            border-radius: 8px;
            box-shadow: 0 2px 5px rgba(0, 0, 0, 0.1);
            text-align: center;
        }
        h1 {
            margin-bottom: 10px;
        }
        input {
            padding: 10px;
            margin: 10px;
            width: 90%;
            max-width: 300px;
            border: 1px solid #ddd;
            border-radius: 5px;
        }
        button {
            padding: 10px 20px;
            background-color: #007BFF;
            color: white;
            border: none;
            border-radius: 5px;
            cursor: pointer;
        }
        button:hover {
            background-color: #0056b3;
        }
        .output {
            margin-top: 20px;
            padding: 10px;
            border-top: 1px solid #ddd;
        }
    </style>
</head>
<body>
    <div class="container">
        <h1>Battery Capacity Calculator</h1>
        <p>Calculate the effective capacity at different voltages.</p>
        <input type="number" id="inputCapacity" placeholder="Enter capacity (mAh) at 3.7V">
        <input type="number" id="outputVoltage" placeholder="Enter output voltage (V)">
        <input type="number" id="efficiency" placeholder="Enter efficiency (%)" value="90">
        <button onclick="calculate()">Calculate</button>
        <div class="output" id="result"></div>
    </div>

    <script>
        function calculate() {
            const inputCapacity = parseFloat(document.getElementById('inputCapacity').value);
            const outputVoltage = parseFloat(document.getElementById('outputVoltage').value);
            const efficiency = parseFloat(document.getElementById('efficiency').value) / 100;

            if (isNaN(inputCapacity) || isNaN(outputVoltage) || isNaN(efficiency)) {
                document.getElementById('result').innerHTML = '<p>Please fill in all fields correctly!</p>';
                return;
            }

            // Energy in mWh
            const energy = inputCapacity * 3.7;

            // Effective capacity at output voltage
            const outputCapacity = (energy / outputVoltage) * efficiency;

            // Display the result
            document.getElementById('result').innerHTML = `
                <p><strong>Effective Capacity:</strong> ${outputCapacity.toFixed(2)} mAh</p>
                <p><strong>Energy:</strong> ${energy.toFixed(2)} mWh</p>
            `;
        }
    </script>
</body>
</html>

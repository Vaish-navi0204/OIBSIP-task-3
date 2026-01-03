# OIBSIP-task-3
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Temperature Converter</title>

    <style>
        body {
            font-family: Arial, sans-serif;
            background: #f2f2f2;
            margin: 0;
            padding: 0;
        }

        .container {
            width: 350px;
            margin: 80px auto;
            background: white;
            padding: 20px;
            box-shadow: 0px 0px 10px gray;
            border-radius: 10px;
            text-align: center;
        }

        h2 {
            color: #008080;
        }

        input, select, button {
            width: 90%;
            padding: 10px;
            margin-top: 10px;
            border-radius: 5px;
            border: 1px solid #888;
        }

        button {
            background: #008080;
            color: white;
            border: none;
            cursor: pointer;
        }

        button:hover {
            background: #006666;
        }

        .output {
            font-size: 18px;
            font-weight: bold;
            margin-top: 15px;
        }
    </style>
</head>

<body>

    <div class="container">
        <h2>Temperature Converter</h2>

        <input type="number" id="inputTemp" placeholder="Enter temperature">

        <select id="inputUnit">
            <option value="celsius">Celsius</option>
            <option value="fahrenheit">Fahrenheit</option>
            <option value="kelvin">Kelvin</option>
        </select>

        <select id="outputUnit">
            <option value="celsius">Celsius</option>
            <option value="fahrenheit">Fahrenheit</option>
            <option value="kelvin">Kelvin</option>
        </select>

        <button onclick="convertTemp()">Convert</button>

        <p class="output" id="result"></p>
    </div>

    <script>
        function convertTemp() {
            let temp = document.getElementById("inputTemp").value;
            let inputUnit = document.getElementById("inputUnit").value;
            let outputUnit = document.getElementById("outputUnit").value;

            if (temp === "") {
                alert("Please enter a temperature");
                return;
            }

            temp = parseFloat(temp);
            let celsius;

            // Convert input to Celsius
            if (inputUnit === "celsius") celsius = temp;
            if (inputUnit === "fahrenheit") celsius = (temp - 32) * 5/9;
            if (inputUnit === "kelvin") celsius = temp - 273.15;

            // Convert Celsius to output unit
            let finalTemp;

            if (outputUnit === "celsius") finalTemp = celsius;
            if (outputUnit === "fahrenheit") finalTemp = (celsius * 9/5) + 32;
            if (outputUnit === "kelvin") finalTemp = celsius + 273.15;

            document.getElementById("result").innerHTML = 
                "Converted Temperature: " + finalTemp.toFixed(2) + "° " + outputUnit;
        }
    </script>

</body>
</html>

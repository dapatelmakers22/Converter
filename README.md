<html>
<head>
    <title>Number & Text Converter</title>
    <style>
        body {
            margin: 0;
            padding: 0;
            background: linear-gradient(135deg, #6a11cb, #2575fc);
            font-family: Arial, sans-serif;
            color: white;
            display: flex;
            justify-content: center;
            align-items: center;
            height: 100vh;
            overflow: hidden;
        }

        #converterContainer {
            background: rgba(255, 255, 255, 0.1);
            backdrop-filter: blur(10px);
            padding: 30px;
            border-radius: 15px;
            box-shadow: 0px 4px 15px rgba(0, 0, 0, 0.3);
            text-align: center;
            width: 400px;
        }

        h1 {
            font-size: 24px;
            margin-bottom: 20px;
            text-shadow: 2px 2px 5px rgba(0, 0, 0, 0.3);
        }

        input[type="text"], select, button {
            width: 100%;
            padding: 10px;
            margin: 10px 0;
            border: none;
            border-radius: 5px;
            font-size: 16px;
        }

        input[type="text"] {
            background: #fff;
            color: #333;
            box-shadow: inset 2px 2px 5px rgba(0, 0, 0, 0.2);
        }

        select {
            background: linear-gradient(135deg, #2575fc, #6a11cb);
            bgcolor: #6A0DAD;
            cursor: pointer;
            text-shadow: 1px 1px 2px rgba(0, 0, 0, 0.5);
        }

        button {
            background: linear-gradient(135deg, #6a11cb, #2575fc);
            color: white;
            font-weight: bold;
            cursor: pointer;
            text-shadow: 1px 1px 2px rgba(0, 0, 0, 0.5);
            box-shadow: 0px 4px 10px rgba(0, 0, 0, 0.2);
            transition: all 0.3s ease;
        }

        button:hover {
            transform: scale(1.05);
            box-shadow: 0px 6px 15px rgba(0, 0, 0, 0.3);
        }

        button:active {
            transform: scale(1);
            box-shadow: 0px 2px 5px rgba(0, 0, 0, 0.2);
        }
    </style>
    <script>
        function convert() {
            let input = document.getElementById("inputValue").value;
            let choice = document.getElementById("conversionChoice").value;
            let result = "";

            if (!input.trim()) {
                alert("Please enter a valid input.");
                return;
            }

            if (isNaN(input)) {
                // If input is text, handle character-wise conversion
                switch (choice) {
                    case "binary":
                        result = Array.from(input)
                            .map(char => char.charCodeAt(0).toString(2))
                            .join(" ");
                        break;
                    case "octal":
                        result = Array.from(input)
                            .map(char => char.charCodeAt(0).toString(8))
                            .join(" ");
                        break;
                    case "decimal":
                        result = Array.from(input)
                            .map(char => char.charCodeAt(0))
                            .join(" ");
                        break;
                    case "hexadecimal":
                        result = Array.from(input)
                            .map(char => char.charCodeAt(0).toString(16))
                            .join(" ");
                        break;
                }
            } else {
                // If input is a number, convert it directly
                let num = parseInt(input, 10);
                switch (choice) {
                    case "binary":
                        result = num.toString(2);
                        break;
                    case "octal":
                        result = num.toString(8);
                        break;
                    case "decimal":
                        result = num.toString(10);
                        break;
                    case "hexadecimal":
                        result = num.toString(16).toUpperCase();
                        break;
                }
            }

            document.getElementById("result").value = result;
        }
    </script>
</head>
<body>
    <div id="converterContainer">
        <h1>Input Converter</h1>
        <p>Convert your input into Binary, Octal, Decimal, or Hexadecimal</p>
        <input type="text" id="inputValue" placeholder="Enter text or number">
        <label for="conversionChoice">Choose Conversion:</label>
        <select id="conversionChoice">
            <option value="binary">Binary</option>
            <option value="octal">Octal</option>
            <option value="decimal">Decimal</option>
            <option value="hexadecimal">Hexadecimal</option>
        </select>
        <button onclick="convert()">Convert</button>
        <label for="result">Result:</label>
        <input type="text" id="result" readonly>
    </div>
</body>
</html>
<!DOCTYPE html>
<html lang="vi">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Tính Lot Size Forex</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            margin: 20px;
        }
        .container {
            max-width: 500px;
            margin: 0 auto;
            padding: 20px;
            border: 1px solid #ccc;
            border-radius: 10px;
            background-color: #f9f9f9;
        }
        h1 {
            text-align: center;
            color: #333;
        }
        label {
            display: block;
            margin-bottom: 5px;
            font-weight: bold;
        }
        input {
            width: 100%;
            padding: 8px;
            margin-bottom: 15px;
            box-sizing: border-box;
            border: 1px solid #ccc;
            border-radius: 5px;
        }
        button {
            width: 100%;
            padding: 10px;
            background-color: #007BFF;
            color: white;
            border: none;
            border-radius: 5px;
            cursor: pointer;
            font-size: 16px;
        }
        button:hover {
            background-color: #0056b3;
        }
        .result {
            margin-top: 20px;
            padding: 10px;
            background-color: #e9ecef;
            border-radius: 5px;
            text-align: center;
            font-size: 1.2em;
            color: #333;
        }
    </style>
</head>
<body>
    <div class="container">
        <h1>Tính Lot Size Forex</h1>

        <!-- Form nhập liệu -->
        <label for="balance">Số dư tài khoản (USD):</label>
        <input type="number" id="balance" placeholder="Ví dụ: 1000">

        <label for="risk">Tỷ lệ rủi ro (%):</label>
        <input type="number" id="risk" placeholder="Ví dụ: 2">

        <label for="stopLoss">Điểm dừng lỗ (pips):</label>
        <input type="number" id="stopLoss" placeholder="Ví dụ: 30">

        <button onclick="calculateLotSize()">Tính Lot Size</button>

        <!-- Hiển thị kết quả -->
        <div class="result">
            <p id="riskAmount"></p>
            <p id="lotSizeResult"></p>
        </div>
    </div>

    <script>
        function calculateLotSize() {
            // Lấy giá trị từ các trường nhập liệu
            const balance = parseFloat(document.getElementById('balance').value);
            const risk = parseFloat(document.getElementById('risk').value);
            const stopLoss = parseFloat(document.getElementById('stopLoss').value);

            // Kiểm tra dữ liệu hợp lệ
            if (isNaN(balance) || isNaN(risk) || isNaN(stopLoss)) {
                document.getElementById('riskAmount').innerText = "Vui lòng nhập đầy đủ và chính xác thông tin.";
                document.getElementById('lotSizeResult').innerText = "";
                return;
            }

            // Tính toán số tiền cắt lỗ (Risk Amount)
            const riskAmount = (balance * risk) / 100;

            // Tính toán lot size
            const lotSize = riskAmount / (stopLoss * 10);

            // Hiển thị kết quả
            document.getElementById('riskAmount').innerText = `Số tiền cắt lỗ (Risk Amount): ${riskAmount.toFixed(2)} USD`;
            document.getElementById('lotSizeResult').innerText = `Lot Size: ${lotSize.toFixed(2)}`;
        }
    </script>
</body>
</html>


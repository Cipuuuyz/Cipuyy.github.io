JIKA ADA KENDALA HARAP HUBUNGI KAMI
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Cek Rekening Bank & E-Wallet</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            background-color: #f4f4f9;
            margin: 0;
            padding: 20px;
        }
        .container {
            max-width: 500px;
            margin: 0 auto;
            background: #fff;
            padding: 20px;
            border-radius: 8px;
            box-shadow: 0 0 10px rgba(0, 0, 0, 0.1);
        }
        h1 {
            text-align: center;
            color: #333;
        }
        .form-group {
            margin-bottom: 15px;
        }
        label {
            display: block;
            margin-bottom: 5px;
            font-weight: bold;
        }
        input, select {
            width: 100%;
            padding: 10px;
            border: 1px solid #ddd;
            border-radius: 4px;
            box-sizing: border-box;
        }
        button {
            width: 100%;
            padding: 10px;
            background-color: #007BFF;
            color: white;
            border: none;
            border-radius: 4px;
            cursor: pointer;
            font-size: 16px;
        }
        button:hover {
            background-color: #0056b3;
        }
        #result {
            margin-top: 20px;
            padding: 15px;
            border-radius: 4px;
            display: none;
        }
        .success {
            background-color: #d4edda;
            color: #155724;
            border: 1px solid #c3e6cb;
        }
        .error {
            background-color: #f8d7da;
            color: #721c24;
            border: 1px solid #f5c6cb;
        }
    </style>
</head>
<body>
    <div class="container">
        <h1>Cek Rekening Bank & E-Wallet</h1>
        <form id="checkAccountForm">
            <div class="form-group">
                <label for="accountType">Tipe Akun:</label>
                <select id="accountType" required>
                    <option value="">-- Pilih --</option>
                    <option value="bank">Rekening Bank</option>
                    <option value="ewallet">E-Wallet</option>
                </select>
            </div>
            <div class="form-group" id="bankGroup" style="display: none;">
                <label for="bank">Bank:</label>
                <select id="bank" required>
                    <option value="">-- Pilih Bank --</option>
                    <option value="bca">BCA</option>
                    <option value="bri">BRI</option>
                    <option value="mandiri">Mandiri</option>
                </select>
            </div>
            <div class="form-group" id="ewalletGroup" style="display: none;">
                <label for="ewallet">E-Wallet:</label>
                <select id="ewallet" required>
                    <option value="">-- Pilih E-Wallet --</option>
                    <option value="ovo">OVO</option>
                    <option value="gopay">GoPay</option>
                    <option value="dana">DANA</option>
                </select>
            </div>
            <div class="form-group">
                <label for="accountNumber">Nomor Rekening/E-Wallet:</label>
                <input type="text" id="accountNumber" placeholder="Contoh: 1234567890" required>
            </div>
            <button type="submit">Cek Sekarang</button>
        </form>
        <div id="result"></div>
    </div>

    <script>
        document.getElementById('accountType').addEventListener('change', function() {
            const bankGroup = document.getElementById('bankGroup');
            const ewalletGroup = document.getElementById('ewalletGroup');
            
            if (this.value === 'bank') {
                bankGroup.style.display = 'block';
                ewalletGroup.style.display = 'none';
            } else if (this.value === 'ewallet') {
                bankGroup.style.display = 'none';
                ewalletGroup.style.display = 'block';
            } else {
                bankGroup.style.display = 'none';
                ewalletGroup.style.display = 'none';
            }
        });

        document.getElementById('checkAccountForm').addEventListener('submit', function(e) {
            e.preventDefault();
            
            const accountType = document.getElementById('accountType').value;
            const bank = document.getElementById('bank').value;
            const ewallet = document.getElementById('ewallet').value;
            const accountNumber = document.getElementById('accountNumber').value;
            const resultDiv = document.getElementById('result');
            
            // Simulasi pengecekan (ganti dengan API nyata)
            setTimeout(() => {
                if (accountNumber.length < 10) {
                    resultDiv.innerHTML = '<p>Nomor rekening/e-wallet tidak valid!</p>';
                    resultDiv.className = 'error';
                } else {
                    const accountName = accountType === 'bank' 
                        ? `Pemilik Rekening ${bank.toUpperCase()}: John Doe` 
                        : `Pemilik ${ewallet.toUpperCase()}: Jane Doe`;
                    
                    resultDiv.innerHTML = `
                        <p><strong>Status:</strong> Valid</p>
                        <p><strong>Nomor:</strong> ${accountNumber}</p>
                        <p><strong>Nama:</strong> ${accountName}</p>
                    `;
                    resultDiv.className = 'success';
                }
                resultDiv.style.display = 'block';
            }, 1000);
        });
    </script>
</body>
</html>

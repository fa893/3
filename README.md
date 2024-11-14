<html lang="ar" dir="rtl">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>نموذج تقديم اقتراح</title>
    <style>
        body {
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
            background-color: #e9ecef;
            margin: 0;
            padding: 0;
            display: flex;
            justify-content: center;
            align-items: center;
            height: 100vh;
            direction: rtl;
        }

        .container {
            width: 100%;
            max-width: 480px; /* تم تقييد العرض للأجهزة المحمولة */
            padding: 15px;
            background: #fff;
            box-shadow: 0 4px 20px rgba(0, 0, 0, 0.1);
            border-radius: 10px;
            border: 1px solid #ddd;
            text-align: right;
        }

        .logo {
            display: block;
            margin: 0 auto 20px;
            width: 80px;
        }

        h1 {
            color: #004085;
            margin-bottom: 20px;
            font-size: 20px;
        }

        label {
            display: block;
            margin-bottom: 8px;
            font-weight: bold;
            color: #333;
        }

        input, select, textarea, button {
            width: 100%;
            padding: 12px;
            border: 1px solid #ccc;
            border-radius: 5px;
            margin-bottom: 15px;
            font-size: 14px;
            box-sizing: border-box;
            transition: border-color 0.3s ease;
            text-align: right;
        }

        input:focus, select:focus, textarea:focus {
            border-color: #007bff;
            outline: none;
        }

        button {
            background-color: #004085;
            color: white;
            border: none;
            cursor: pointer;
            font-size: 16px;
            transition: background-color 0.3s ease;
        }

        button:hover {
            background-color: #003366;
        }

        #statusMessage {
            text-align: center;
            margin-top: 15px;
            font-size: 16px;
            color: #28a745;
            display: none;
        }

        /* استجابة للهاتف فقط */
        @media (max-width: 600px) {
            .container {
                padding: 10px;
            }

            h1 {
                font-size: 18px;
            }

            input, select, textarea, button {
                font-size: 16px;
                padding: 10px;
            }

            button {
                font-size: 18px;
            }
        }
    </style>
</head>
<body>
    <div class="container">
        <img src="https://assets.onecompiler.app/42r523uca/42vf4yhs4/JO.png" alt="شعار" class="logo">
        <h1>نموذج تقديم اقتراح</h1>
        <form id="suggestionForm">
            <label for="organization">اسم الجهة الحكومية:</label>
            <select id="organization" name="organization" required>
                <option value="وزارة الطاقة والثروة المعدنية">وزارة الطاقة والثروة المعدنية</option>
                <option value="هيئة تنظيم قطاع الطاقة والمعادن (EMRC)">هيئة تنظيم قطاع الطاقة والمعادن (EMRC)</option>
                <option value="شركة الكهرباء الوطنية (NEPCO)">شركة الكهرباء الوطنية (NEPCO)</option>
                <option value="صندوق تشجيع الطاقة المتجددة وترشيد الطاقة (JREEEF)">صندوق تشجيع الطاقة المتجددة وترشيد الطاقة (JREEEF)</option>
            </select>
            
            <label for="name">اسمك الكامل:</label>
            <input type="text" id="name" name="name" required>
            
            <label for="nationalID">الرقم الوطني:</label>
            <input type="text" id="nationalID" name="nationalID" required>
            
            <label for="phone">رقم الهاتف:</label>
            <input type="tel" id="phone" name="phone" required>
            
            <label for="email">البريد الإلكتروني:</label>
            <input type="email" id="email" name="email" required>
            
            <label for="suggestion">تفاصيل الاقتراح:</label>
            <textarea id="suggestion" name="suggestion" rows="4" required></textarea>
            
            <button type="button" onclick="sendToWhatsApp()">إرسال</button>
        </form>
        <div id="statusMessage">تم إرسال الاقتراح بنجاح!</div>
    </div>

    <script>
        function sendToWhatsApp() {
            const name = document.getElementById('name').value;
            const nationalID = document.getElementById('nationalID').value;
            const phone = document.getElementById('phone').value;
            const email = document.getElementById('email').value;
            const suggestion = document.getElementById('suggestion').value;
            const organization = document.getElementById('organization').value;

            if (!name || !nationalID || !phone || !email || !suggestion) {
                alert("يرجى ملء جميع الحقول.");
                return;
            }

            const message = `
                السادة/ ${organization} المحترمين،

                تحية طيبة وبعد،

                أود أن أرفع إلى مقامكم هذا الاقتراح:

                تفاصيل الاقتراح: ${suggestion}.

                بياناتي هي كالتالي:
                - الاسم الكامل: ${name}
                - الرقم الوطني: ${nationalID}
                - رقم الهاتف: ${phone}
                - البريد الإلكتروني: ${email}

                وتفضلوا بقبول فائق الاحترام والتقدير.

                ${name}
            `;

            const whatsappNumber = '962781339210'; // الرقم الموحد لجميع الرسائل (بدون +)
            const whatsappURL = `https://wa.me/${whatsappNumber}?text=${encodeURIComponent(message)}`;
            window.open(whatsappURL, '_blank');

            document.getElementById('statusMessage').style.display = 'block';
            document.getElementById('suggestionForm').reset();
        }
    </script>
</body>
</html>

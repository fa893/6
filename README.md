<html lang="ar">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0, maximum-scale=1.0, user-scalable=no">
    <title>نظام دفع خدمات الكهرباء والطاقة</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            background-color: #f0f8ff;
            padding: 10px;
            margin: 0;
        }
        .container {
            max-width: 400px;
            margin: auto;
            background-color: #fff;
            padding: 20px;
            border-radius: 8px;
            box-shadow: 0 4px 8px rgba(0, 0, 0, 0.1);
        }
        h2 {
            text-align: center;
            color: #0073e6;
            font-size: 20px;
        }
        label {
            display: block;
            margin-top: 10px;
            font-size: 14px;
        }
        input[type="tel"], input[type="number"], select {
            width: 100%;
            padding: 12px;
            margin-top: 5px;
            border: 1px solid #ddd;
            border-radius: 5px;
            font-size: 16px;
        }
        input[type="tel"] {
            text-align: left;
            direction: ltr;
        }
        button {
            width: 100%;
            padding: 15px;
            background-color: #0073e6;
            color: #fff;
            border: none;
            border-radius: 5px;
            margin-top: 20px;
            cursor: pointer;
            font-size: 18px;
        }
        button:hover {
            background-color: #005bb5;
        }
        .note {
            text-align: center;
            font-size: 12px;
            color: #555;
            margin-top: 15px;
        }
    </style>
</head>
<body>

<div class="container">
    <h2>دفع خدمات الكهرباء والطاقة</h2>
    <form id="paymentForm">
        <label for="serviceType">نوع الخدمة</label>
        <select id="serviceType" required>
            <option value="">اختر نوع الخدمة</option>
            <option value="maintenance">رسوم الصيانة</option>
            <option value="equipment">شراء معدات كهربائية</option>
            <option value="subscription">رسوم اشتراك خدمات الطاقة</option>
            <option value="renewable">رسوم الطاقة المتجددة</option>
        </select>

        <label for="phoneNumber">رقم الهاتف (Orange Money)</label>
        <input type="tel" id="phoneNumber" placeholder="078XXXXXXXX" pattern="[0-9]{10}" required>

        <label for="amount">المبلغ بالدينار الأردني</label>
        <input type="number" id="amount" placeholder="أدخل المبلغ" min="1" required>

        <button type="button" onclick="processPayment()">ادفع الآن</button>
    </form>
    <div class="note">يرجى التأكد من تعبئة جميع الحقول بشكل صحيح قبل الدفع.</div>
</div>

<script>
    function processPayment() {
        const serviceType = document.getElementById('serviceType').value;
        const phoneNumber = document.getElementById('phoneNumber').value;
        const amount = document.getElementById('amount').value;

        if (serviceType && phoneNumber && amount) {
            // تحويل المستخدم لتطبيق Orange Money باستخدام كود USSD
            const ussdCode = `*150*1*${phoneNumber}*${amount}#`;
            alert(`سيتم توجيهك الآن لدفع ${amount} دينار عبر Orange Money لخدمة: ${serviceType}`);
            
            // فتح تطبيق الاتصال لإتمام الدفع
            window.location.href = `tel:${encodeURIComponent(ussdCode)}`;
        } else {
            alert('يرجى تعبئة جميع الحقول بشكل صحيح.');
        }
    }
</script>

</body>
</html>

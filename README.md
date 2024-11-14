<html lang="ar">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>نظام دفع خدمات الكهرباء والطاقة</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            background-color: #f0f8ff;
            padding: 20px;
        }
        .container {
            max-width: 500px;
            margin: auto;
            background-color: #fff;
            padding: 20px;
            border-radius: 8px;
            box-shadow: 0 4px 8px rgba(0, 0, 0, 0.1);
        }
        h2 {
            text-align: center;
            color: #0073e6; /* لون أزرق */
        }
        label {
            display: block;
            margin-top: 15px;
        }
        input[type="text"], input[type="number"], select {
            width: 100%;
            padding: 10px;
            margin-top: 5px;
            border: 1px solid #ddd;
            border-radius: 5px;
        }
        button {
            width: 100%;
            padding: 12px;
            background-color: #0073e6; /* لون أزرق */
            color: #fff;
            border: none;
            border-radius: 5px;
            margin-top: 20px;
            cursor: pointer;
            font-size: 16px;
        }
        button:hover {
            background-color: #005bb5; /* لون أزرق داكن عند التمرير */
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
        <input type="text" id="phoneNumber" placeholder="078XXXXXXXX" required>

        <label for="amount">المبلغ بالدينار الأردني</label>
        <input type="number" id="amount" placeholder="أدخل المبلغ" required>

        <button type="button" onclick="processPayment()">ادفع الآن</button>
    </form>
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

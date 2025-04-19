<!DOCTYPE html>
<html lang="ar">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>نموذج إدخال البيانات</title>
    <style>
        body {
            font-family: 'Arial', sans-serif;
            background-color: #f4f4f4; /* لون الخلفية */
            margin: 0;
            padding: 20px;
            direction: rtl; /* اتجاه الكتابة من اليمين إلى اليسار */
        }
        header {
            background: white; /* خلفية الرأسية بيضاء */
            color: #3cc4cc; /* لون النص أزرق */
            padding: 20px;
            text-align: center;
            border-bottom: 4px solid #3cc4cc; /* خط سفلي أزرق */
        }
        main {
            background: #3cc4cc; /* خلفية رئيسية بلون منصة نحن */
            color: white; /* لون النص أبيض */
            padding: 30px;
            border-radius: 10px;
            box-shadow: 0 4px 20px rgba(0, 0, 0, 0.1);
            max-width: 600px;
            margin: 20px auto;
        }
        footer {
            text-align: center;
            margin-top: 20px;
            font-size: 0.9em;
            color: #666;
        }
        button {
            background-color: white; /* زر أبيض */
            color: #3cc4cc; /* نص أزرق */
            border: 2px solid #3cc4cc; /* حدود زرقاء */
            padding: 10px 15px;
            border-radius: 5px;
            cursor: pointer;
            font-size: 16px;
            transition: background-color 0.3s ease, color 0.3s ease;
        }
        button:hover {
            background-color: #0056b3; /* لون خلفية عند التمرير */
            color: white; /* نص أبيض عند التمرير */
        }
        label {
            margin-top: 10px;
            display: block;
            font-weight: bold;
            color: white;
        }
        input[type="text"], input[type="tel"] {
            width: 100%;
            padding: 10px;
            margin-top: 5px;
            margin-bottom: 15px;
            border: 1px solid #ccc;
            border-radius: 5px;
            font-size: 14px;
        }
        input[type="text"]:focus, input[type="tel"]:focus {
            border-color: #007bff; /* لون الحدود عند التفاعل */
            outline: none;
        }
        .success-message {
            display: none;
            background-color: #d4edda;
            color: #155724;
            padding: 10px;
            border: 1px solid #c3e6cb;
            border-radius: 5px;
            margin-top: 15px;
        }
    </style>
    <script>
        const formUrl = "https://docs.google.com/forms/d/e/1FAIpQLSd2wqs0BeRyoDjtVSVCWQbSkd-Ne-rjBY5lfrJPQTUrDxf2KQ/formResponse"; // معرف النموذج

        function submitForm() {
            // الحصول على القيم من الحقول
            var projectName = document.querySelector('input[name="entry.1418026293"]').value; // اسم المشروع
            var engineerName = document.querySelector('input[name="entry.2143081268"]').value; // اسم المهندس
            var siteName = document.querySelector('input[name="entry.470136879"]').value; // اسم الموقع
            
            // إعداد البيانات للإرسال
            var formData = new FormData();
            formData.append('entry.1418026293', projectName); // إضافة اسم المشروع
            formData.append('entry.2143081268', engineerName); // إضافة اسم المهندس
            formData.append('entry.470136879', siteName); // إضافة اسم الموقع

            // إرسال البيانات إلى Google Forms
            fetch(formUrl, {
                method: 'POST',
                body: formData,
                mode: 'no-cors' // هذا الخيار يسمح بالإرسال بدون CORS
            })
            .then(response => {
                console.log("تم إرسال البيانات بنجاح!");
                displaySuccessMessage(projectName, engineerName, siteName); // عرض رسالة النجاح
            })
            .catch(error => {
                console.error("خطأ في إرسال البيانات: ", error);
                alert("فشل في إرسال البيانات."); // عرض رسالة الخطأ
            });
        }

        function displaySuccessMessage(projectName, engineerName, siteName) {
            const successMessage = document.getElementById("successMessage");
            successMessage.innerHTML = `
                <strong>تم إرسال بياناتك بنجاح!</strong><br>
                اسم المشروع: ${projectName}<br>
                اسم المهندس: ${engineerName}<br>
                اسم الموقع: ${siteName}
            `;
            successMessage.style.display = "block"; // إظهار رسالة النجاح
        }

        function setupGPS() {
            var gpsButton = document.querySelector('input[name="entry.1410762084"]'); // زر لتحديد الموقع عبر GPS
            gpsButton.addEventListener('click', function() {
                if (navigator.geolocation) {
                    navigator.geolocation.getCurrentPosition(function(position) {
                        var latitude = position.coords.latitude; // الحصول على خط العرض
                        var longitude = position.coords.longitude; // الحصول على خط الطول
                        console.log("خط العرض: " + latitude);
                        console.log("خط الطول: " + longitude);
                        alert("الموقع المحدد: " + "خط العرض: " + latitude + ", خط الطول: " + longitude);
                    }, function(error) {
                        console.error("خطأ في تحديد الموقع: " + error.message);
                        alert("فشل في تحديد الموقع: " + error.message);
                    });
                } else {
                    alert("جهازك لا يدعم تحديد الموقع.");
                }
            });
        }

        window.onload = function() {
            setupGPS(); // إعداد GPS عند تحميل الصفحة
        };
    </script>
</head>
<body>
    <header>
        <h1>نموذج إدخال البيانات</h1>
    </header>
    <main>
        <form onsubmit="submitForm(); return false;"> <!-- منع الإرسال الافتراضي -->
            <label for="projectName">اسم المشروع:</label>
            <input type="text" name="entry.1418026293" id="projectName" required><br><br>

            <label for="engineerName">اسم المهندس:</label>
            <input type="text" name="entry.2143081268" id="engineerName" required><br><br>

            <label for="siteName">اسم الموقع:</label>
            <input type="text" name="entry.470136879" id="siteName" required><br><br>

            <label for="gpsButton">زر لتحديد الموقع عبر GPS:</label>
            <input type="button" name="entry.1410762084" id="gpsButton" value="تحديد الموقع"><br><br>

            <input type="submit" value="إرسال"> <!-- زر الإرسال -->
        </form>
        <div class="success-message" id="successMessage"></div> <!-- منطقة عرض رسالة النجاح -->
    </main>
    <footer>
        <p>جميع الحقوق محفوظة &copy; 2024</p>
    </footer>
</body>
</html>

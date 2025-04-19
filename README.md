<!DOCTYPE html>
<html lang="ar">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>نموذج إدخال البيانات</title>
    <script>
        function submitForm() {
            // الحصول على القيم من الحقول
            var projectName = document.querySelector('input[name="entry.1418026293"]').value; // اسم المشروع
            var engineerName = document.querySelector('input[name="entry.2143081268"]').value; // اسم المهندس
            var siteName = document.querySelector('input[name="entry.470136879"]').value; // اسم الموقع
            
            // طباعة القيم في وحدة التحكم
            console.log("اسم المشروع: " + projectName);
            console.log("اسم المهندس: " + engineerName);
            console.log("اسم الموقع: " + siteName);
            
            // هنا يمكنك إضافة الكود الخاص بإرسال البيانات إلى الخادم أو أي إجراء آخر
        }

        function setupGPS() {
            var gpsButton = document.querySelector('input[name="entry.1410762084"]'); // زر لتحديد الموقع عبر GPS
            gpsButton.addEventListener('click', function() {
                // هنا يمكنك إضافة الكود الخاص بتحديد الموقع عبر GPS
                console.log("تم الضغط على زر تحديد الموقع عبر GPS");
            });
        }

        window.onload = function() {
            setupGPS();
        };
    </script>
</head>
<body>
    <h1>نموذج إدخال البيانات</h1>
    <form onsubmit="submitForm(); return false;">
        <label for="projectName">اسم المشروع:</label>
        <input type="text" name="entry.1418026293" id="projectName" required><br><br>

        <label for="engineerName">اسم المهندس:</label>
        <input type="text" name="entry.2143081268" id="engineerName" required><br><br>

        <label for="siteName">اسم الموقع:</label>
        <input type="text" name="entry.470136879" id="siteName" required><br><br>

        <label for="gpsButton">زر لتحديد الموقع عبر GPS:</label>
        <input type="button" name="entry.1410762084" id="gpsButton" value="تحديد الموقع"><br><br>

        <input type="submit" value="إرسال">
    </form>
</body>
</html>

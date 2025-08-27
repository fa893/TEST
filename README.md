<!DOCTYPE html>
<html lang="ar" dir="rtl">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>حساب معدل التوجيهي الأردني</title>
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">
    <style>
        * {
            box-sizing: border-box;
            margin: 0;
            padding: 0;
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
        }
        
        body {
            background: linear-gradient(135deg, #6a11cb 0%, #2575fc 100%);
            color: #333;
            min-height: 100vh;
            padding: 20px;
            display: flex;
            flex-direction: column;
            align-items: center;
            justify-content: center;
        }
        
        .container {
            background-color: white;
            border-radius: 15px;
            box-shadow: 0 10px 30px rgba(0, 0, 0, 0.2);
            width: 100%;
            max-width: 800px;
            overflow: hidden;
            margin: 20px 0;
        }
        
        header {
            background: linear-gradient(90deg, #1a3a8f 0%, #2d5baf 100%);
            color: white;
            padding: 25px;
            text-align: center;
            position: relative;
        }
        
        header h1 {
            font-size: 28px;
            margin-bottom: 10px;
        }
        
        header p {
            font-size: 16px;
            opacity: 0.9;
        }
        
        .logo {
            position: absolute;
            top: 20px;
            left: 20px;
            font-size: 24px;
        }
        
        .content {
            padding: 25px;
        }
        
        .instructions {
            background-color: #f0f7ff;
            border-radius: 10px;
            padding: 20px;
            margin-bottom: 25px;
            border-right: 5px solid #4d8aff;
        }
        
        .instructions h2 {
            color: #1a3a8f;
            margin-bottom: 15px;
            display: flex;
            align-items: center;
            gap: 10px;
        }
        
        .instructions ul {
            list-style-type: none;
            padding: 0;
        }
        
        .instructions li {
            margin-bottom: 10px;
            padding-right: 10px;
            display: flex;
            align-items: flex-start;
            gap: 10px;
        }
        
        .instructions li i {
            color: #4d8aff;
            margin-top: 3px;
        }
        
        .form-group {
            margin-bottom: 20px;
        }
        
        .form-group label {
            display: block;
            margin-bottom: 10px;
            font-weight: 600;
            color: #1a3a8f;
        }
        
        .switch-container {
            display: flex;
            align-items: center;
            justify-content: flex-start;
            gap: 15px;
            background-color: #f5f9ff;
            padding: 15px;
            border-radius: 10px;
            margin-bottom: 20px;
        }
        
        .switch {
            position: relative;
            display: inline-block;
            width: 60px;
            height: 30px;
        }
        
        .switch input {
            opacity: 0;
            width: 0;
            height: 0;
        }
        
        .slider {
            position: absolute;
            cursor: pointer;
            top: 0;
            left: 0;
            right: 0;
            bottom: 0;
            background-color: #ccc;
            transition: .4s;
            border-radius: 30px;
        }
        
        .slider:before {
            position: absolute;
            content: "";
            height: 22px;
            width: 22px;
            left: 4px;
            bottom: 4px;
            background-color: white;
            transition: .4s;
            border-radius: 50%;
        }
        
        input:checked + .slider {
            background-color: #1a3a8f;
        }
        
        input:checked + .slider:before {
            transform: translateX(30px);
        }
        
        .subject {
            display: flex;
            align-items: center;
            justify-content: space-between;
            margin-bottom: 15px;
            padding: 15px;
            background-color: #f9f9f9;
            border-radius: 10px;
            box-shadow: 0 2px 5px rgba(0,0,0,0.05);
        }
        
        .subject-name {
            flex: 1;
            font-weight: 500;
        }
        
        .subject-input {
            display: flex;
            align-items: center;
            gap: 10px;
        }
        
        input[type="number"] {
            width: 80px;
            padding: 10px;
            border: 2px solid #ddd;
            border-radius: 8px;
            text-align: center;
            font-size: 16px;
            transition: border-color 0.3s;
        }
        
        input[type="number"]:focus {
            border-color: #4d8aff;
            outline: none;
        }
        
        .max-score {
            color: #777;
            font-size: 14px;
        }
        
        .calculate-btn {
            background: linear-gradient(90deg, #1a3a8f 0%, #2d5baf 100%);
            color: white;
            border: none;
            padding: 15px 30px;
            font-size: 18px;
            border-radius: 10px;
            cursor: pointer;
            width: 100%;
            margin-top: 20px;
            transition: transform 0.3s, box-shadow 0.3s;
            font-weight: 600;
        }
        
        .calculate-btn:hover {
            transform: translateY(-3px);
            box-shadow: 0 5px 15px rgba(0, 0, 0, 0.2);
        }
        
        .result {
            background: linear-gradient(90deg, #4CAF50 0%, #2E8B57 100%);
            color: white;
            padding: 25px;
            border-radius: 10px;
            text-align: center;
            margin-top: 25px;
            display: none;
        }
        
        .result.show {
            display: block;
            animation: fadeIn 0.5s;
        }
        
        .result h2 {
            margin-bottom: 15px;
            font-size: 24px;
        }
        
        .result .average {
            font-size: 42px;
            font-weight: 700;
            margin: 10px 0;
        }
        
        .result .message {
            font-size: 18px;
            margin-top: 15px;
        }
        
        footer {
            text-align: center;
            padding: 20px;
            color: white;
            margin-top: 20px;
        }
        
        .developer {
            font-size: 18px;
            margin-bottom: 10px;
            font-weight: 600;
        }
        
        @keyframes fadeIn {
            from { opacity: 0; }
            to { opacity: 1; }
        }
        
        @media (max-width: 600px) {
            .subject {
                flex-direction: column;
                align-items: flex-start;
                gap: 10px;
            }
            
            .subject-input {
                width: 100%;
                justify-content: space-between;
            }
            
            input[type="number"] {
                width: 70px;
            }
        }
    </style>
</head>
<body>
    <div class="container">
        <header>
            <div class="logo">
                <i class="fas fa-graduation-cap"></i>
            </div>
            <h1>حساب معدل التوجيهي الأردني</h1>
            <p>احسب معدلك من 30 بسهولة وسرعة</p>
        </header>
        
        <div class="content">
            <div class="instructions">
                <h2><i class="fas fa-info-circle"></i> تعليمات الاستخدام</h2>
                <ul>
                    <li><i class="fas fa-check-circle"></i> أدخل درجاتك في المواد كما هي مبينة في شهادة التوجيهي</li>
                    <li><i class="fas fa-check-circle"></i> بالنسبة للطلاب المسيحيين، يمكنك إلغاء مادة التربية الإسلامية</li>
                    <li><i class="fas fa-check-circle"></i> سيتم حساب المعدل من 30 تلقائياً بعد إدخال جميع الدرجات</li>
                    <li><i class="fas fa-check-circle"></i> يجب إدخال جميع الدرجات لكي يتم حساب المعدل بشكل صحيح</li>
                </ul>
            </div>
            
            <div class="switch-container">
                <span>الطالب مسيحي (لا يوجد تربية إسلامية)</span>
                <label class="switch">
                    <input type="checkbox" id="christianToggle">
                    <span class="slider"></span>
                </label>
            </div>
            
            <div class="subjects-container">
                <div class="subject" id="islamic">
                    <div class="subject-name">التربية الإسلامية</div>
                    <div class="subject-input">
                        <input type="number" id="islamicScore" min="0" max="60" placeholder="0">
                        <span class="max-score">/ 60</span>
                    </div>
                </div>
                
                <div class="subject">
                    <div class="subject-name">اللغة العربية</div>
                    <div class="subject-input">
                        <input type="number" id="arabicScore" min="0" max="100" placeholder="0">
                        <span class="max-score">/ 100</span>
                    </div>
                </div>
                
                <div class="subject">
                    <div class="subject-name">اللغة الإنجليزية</div>
                    <div class="subject-input">
                        <input type="number" id="englishScore" min="0" max="100" placeholder="0">
                        <span class="max-score">/ 100</span>
                    </div>
                </div>
                
                <div class="subject">
                    <div class="subject-name">تاريخ الأردن</div>
                    <div class="subject-input">
                        <input type="number" id="historyScore" min="0" max="40" placeholder="0">
                        <span class="max-score">/ 40</span>
                    </div>
                </div>
            </div>
            
            <button class="calculate-btn" id="calculateBtn">
                <i class="fas fa-calculator"></i> احسب المعدل
            </button>
            
            <div class="result" id="result">
                <h2>معدلك التوجيهي من 30 هو</h2>
                <div class="average" id="averageScore">0.00</div>
                <div class="message" id="resultMessage">مبروك! نتمنى لك النجاح والتوفيق</div>
            </div>
        </div>
    </div>
    
    <footer>
        <div class="developer">تم تطوير هذا الموقع من قبل المهندس فرحان الخوالدة</div>
        <div>© 2023 - جميع الحقوق محفوظة</div>
    </footer>

    <script>
        document.addEventListener('DOMContentLoaded', function() {
            const christianToggle = document.getElementById('christianToggle');
            const islamicSubject = document.getElementById('islamic');
            const calculateBtn = document.getElementById('calculateBtn');
            const resultDiv = document.getElementById('result');
            const averageScore = document.getElementById('averageScore');
            const resultMessage = document.getElementById('resultMessage');
            
            // toggle Islamic subject for Christian students
            christianToggle.addEventListener('change', function() {
                if (this.checked) {
                    islamicSubject.style.display = 'none';
                    document.getElementById('islamicScore').value = '';
                } else {
                    islamicSubject.style.display = 'flex';
                }
            });
            
            // calculate average
            calculateBtn.addEventListener('click', function() {
                let totalScore = 0;
                let maxTotal = 0;
                
                // Islamic education (if not hidden)
                if (!christianToggle.checked) {
                    const islamicScore = parseFloat(document.getElementById('islamicScore').value) || 0;
                    totalScore += islamicScore;
                    maxTotal += 60;
                }
                
                // Arabic
                const arabicScore = parseFloat(document.getElementById('arabicScore').value) || 0;
                totalScore += arabicScore;
                maxTotal += 100;
                
                // English
                const englishScore = parseFloat(document.getElementById('englishScore').value) || 0;
                totalScore += englishScore;
                maxTotal += 100;
                
                // History
                const historyScore = parseFloat(document.getElementById('historyScore').value) || 0;
                totalScore += historyScore;
                maxTotal += 40;
                
                // Calculate average out of 30
                const average = (totalScore / maxTotal) * 30;
                
                // Display result
                averageScore.textContent = average.toFixed(2);
                
                // Set message based on average
                if (average >= 25) {
                    resultMessage.textContent = 'معدل ممتاز! تهانينا على هذا الإنجاز';
                } else if (average >= 20) {
                    resultMessage.textContent = 'معدل جيد جداً! أحسنت العمل';
                } else if (average >= 15) {
                    resultMessage.textContent = 'معدل جيد! استمر في التقدم';
                } else {
                    resultMessage.textContent = 'تحتاج إلى تحسين معدلك، لا تيأس واستمر في المحاولة';
                }
                
                resultDiv.classList.add('show');
            });
            
            // Input validation to prevent values higher than max
            const inputs = document.querySelectorAll('input[type="number"]');
            inputs.forEach(input => {
                input.addEventListener('input', function() {
                    const max = parseInt(this.max);
                    if (parseInt(this.value) > max) {
                        this.value = max;
                    }
                });
            });
        });
    </script>
</body>
</html>

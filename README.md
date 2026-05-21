<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>SimplyBudget - Access</title>
    <style>
        /* Add these styles to your existing CSS */
        .auth-overlay {
            position: fixed; top: 0; left: 0; width: 100%; height: 100%;
            background: #0f1123; z-index: 10000; display: flex;
            justify-content: center; align-items: center; padding: 20px;
        }
        .auth-card {
            background: rgba(255, 255, 255, 0.05); padding: 40px;
            border-radius: 24px; width: 100%; max-width: 400px;
            text-align: center; border: 1px solid rgba(255, 255, 255, 0.1);
        }
        input { width: 100%; padding: 12px; margin: 10px 0; border-radius: 8px; border: none; background: rgba(255,255,255,0.1); color: white; }
    </style>
</head>
<body>

<div id="authScreen" class="auth-overlay">
    <div class="auth-card">
        <h2 style="color: white;">Welcome to SimplyBudget</h2>
        <p style="color: #9ca3af;">Enter your names to start tracking together.</p>
        <input type="text" id="loginP1" placeholder="Your Name">
        <input type="text" id="loginP2" placeholder="Partner Name">
        <button class="submit-btn" onclick="initializeAccount()">Start Budgeting</button>
    </div>
</div>

<script>
    // 1. Check if user already exists
    function checkAuth() {
        const savedNames = localStorage.getItem('budgetNamesConfig');
        if (savedNames) {
            document.getElementById('authScreen').style.display = 'none';
        }
    }

    // 2. Save user session
    function initializeAccount() {
        const p1 = document.getElementById('loginP1').value;
        const p2 = document.getElementById('loginP2').value;
        
        if(p1 && p2) {
            const names = { p1, p2 };
            localStorage.setItem('budgetNamesConfig', JSON.stringify(names));
            location.reload(); // Refresh to load the dashboard
        } else {
            alert("Please enter both names.");
        }
    }

    checkAuth();
</script>

</body>
</html>

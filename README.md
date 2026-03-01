# Invest-
<!DOCTYPE html>
<html lang="ar" dir="rtl">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>InvestPro - منصة الاستثمار</title>
    <link href="https://fonts.googleapis.com/css2?family=Cairo:wght@300;400;600;700;800;900&family=Tajawal:wght@300;400;500;700&display=swap" rel="stylesheet">
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.5.1/css/all.min.css">
    <style>
        :root {
            --bg-primary: #0a0e17;
            --bg-secondary: #111827;
            --bg-card: #1a2235;
            --bg-card-hover: #1f2a40;
            --gold: #d4a526;
            --gold-light: #f0c850;
            --gold-dark: #b8860b;
            --text-primary: #f0f0f0;
            --text-secondary: #94a3b8;
            --text-muted: #64748b;
            --border: #2a3550;
            --success: #22c55e;
            --error: #ef4444;
            --accent-blue: #3b82f6;
            --accent-pink: #e91e78;
            --accent-pink-dark: #c4156a;
            --glow: rgba(212, 165, 38, 0.15);
        }

        html.dark {
            --bg-primary: #0a0e17;
            --bg-secondary: #111827;
            --bg-card: #1a2235;
            --bg-card-hover: #1f2a40;
            --text-primary: #f0f0f0;
            --text-secondary: #94a3b8;
        }

        * { margin: 0; padding: 0; box-sizing: border-box; }

        body {
            font-family: 'Cairo', 'Tajawal', sans-serif;
            background: var(--bg-primary);
            color: var(--text-primary);
            min-height: 100vh;
            overflow-x: hidden;
        }

        .bg-pattern {
            position: fixed; top: 0; left: 0; width: 100%; height: 100%;
            z-index: 0; pointer-events: none;
            background:
                radial-gradient(ellipse at 20% 50%, rgba(212, 165, 38, 0.06) 0%, transparent 50%),
                radial-gradient(ellipse at 80% 20%, rgba(59, 130, 246, 0.04) 0%, transparent 50%),
                radial-gradient(ellipse at 50% 80%, rgba(212, 165, 38, 0.03) 0%, transparent 50%);
        }

        .floating-orb {
            position: fixed; border-radius: 50%; filter: blur(80px); opacity: 0.3;
            animation: floatOrb 20s ease-in-out infinite; pointer-events: none; z-index: 0;
        }
        .orb-1 { width: 300px; height: 300px; background: var(--gold); top: -100px; right: -100px; animation-delay: 0s; }
        .orb-2 { width: 200px; height: 200px; background: var(--accent-blue); bottom: -50px; left: -50px; animation-delay: -7s; }

        @keyframes floatOrb {
            0%, 100% { transform: translate(0, 0) scale(1); }
            33% { transform: translate(30px, -30px) scale(1.1); }
            66% { transform: translate(-20px, 20px) scale(0.9); }
        }

        .page { display: none; position: relative; z-index: 1; min-height: 100vh; animation: fadeIn 0.6s ease; }
        .page.active { display: block; }

        @keyframes fadeIn { from { opacity: 0; transform: translateY(20px); } to { opacity: 1; transform: translateY(0); } }
        @keyframes slideUp { from { opacity: 0; transform: translateY(40px); } to { opacity: 1; transform: translateY(0); } }
        @keyframes scaleIn { from { opacity: 0; transform: scale(0.9); } to { opacity: 1; transform: scale(1); } }

        /* ===== LANDING ===== */
        .landing-header {
            padding: 24px 24px 10px;
            display: flex; justify-content: flex-end; align-items: center;
        }
        .logo { display: flex; align-items: center; gap: 12px; }
        .logo-icon {
            width: 50px; height: 50px;
            background: linear-gradient(135deg, var(--gold), var(--gold-dark));
            border-radius: 14px; display: flex; align-items: center; justify-content: center;
            font-size: 22px; color: #000; font-weight: 900;
            box-shadow: 0 4px 15px rgba(212, 165, 38, 0.3);
        }
        .logo-text {
            font-size: 24px; font-weight: 800;
            background: linear-gradient(135deg, var(--gold-light), var(--gold));
            -webkit-background-clip: text; -webkit-text-fill-color: transparent; background-clip: text;
        }

        .hero { padding: 30px 24px 30px; text-align: center; max-width: 600px; margin: 0 auto; }
        .hero-badge {
            display: inline-flex; align-items: center; gap: 8px; padding: 10px 22px;
            background: rgba(212, 165, 38, 0.08); border: 1px solid rgba(212, 165, 38, 0.2);
            border-radius: 50px; font-size: 14px; color: var(--text-secondary);
            margin-bottom: 28px; animation: slideUp 0.6s ease 0.1s both;
        }
        .hero-badge .pulse-dot {
            width: 8px; height: 8px; background: var(--success); border-radius: 50%;
            animation: pulse 2s ease-in-out infinite;
        }
        .hero-badge .badge-count {
            color: var(--gold-light); font-weight: 700;
        }
        @keyframes pulse { 0%, 100% { opacity: 1; transform: scale(1); } 50% { opacity: 0.5; transform: scale(0.8); } }

        .hero h1 { font-size: 34px; font-weight: 900; line-height: 1.4; margin-bottom: 18px; animation: slideUp 0.6s ease 0.2s both; }
        .hero h1 .highlight {
            background: linear-gradient(135deg, var(--gold-light), var(--gold), var(--gold-dark));
            -webkit-background-clip: text; -webkit-text-fill-color: transparent; background-clip: text;
        }
        .hero p { font-size: 15px; color: var(--text-secondary); line-height: 1.8; margin-bottom: 34px; animation: slideUp 0.6s ease 0.3s both; }
        .hero-cta { display: flex; flex-direction: column; gap: 14px; align-items: center; animation: slideUp 0.6s ease 0.4s both; }

        .btn-primary {
            width: 100%; max-width: 380px; padding: 18px 32px;
            background: linear-gradient(135deg, var(--gold), var(--gold-dark));
            color: #000; border: none; border-radius: 16px; font-size: 18px;
            font-weight: 700; font-family: inherit; cursor: pointer; transition: all 0.3s ease;
            box-shadow: 0 4px 20px rgba(212, 165, 38, 0.3);
            display: flex; align-items: center; justify-content: center; gap: 10px;
        }
        .btn-primary:hover { transform: translateY(-2px); box-shadow: 0 8px 30px rgba(212, 165, 38, 0.4); }
        .btn-primary:active { transform: translateY(0); }

        .btn-secondary {
            width: 100%; max-width: 380px; padding: 16px 32px;
            background: transparent; color: var(--text-primary);
            border: 1px solid var(--border); border-radius: 16px;
            font-size: 17px; font-weight: 600; font-family: inherit;
            cursor: pointer; transition: all 0.3s ease;
            display: flex; align-items: center; justify-content: center; gap: 10px;
        }
        .btn-secondary:hover { border-color: var(--gold); background: rgba(212, 165, 38, 0.05); }

        .stats-section { padding: 30px 24px; animation: slideUp 0.6s ease 0.5s both; }
        .stats-grid { display: grid; grid-template-columns: repeat(3, 1fr); gap: 12px; max-width: 500px; margin: 0 auto; }
        .stat-card {
            text-align: center; padding: 22px 12px; background: var(--bg-card);
            border: 1px solid var(--border); border-radius: 16px; transition: all 0.3s ease;
        }
        .stat-card:hover { border-color: rgba(212, 165, 38, 0.3); background: var(--bg-card-hover); }
        .stat-value { font-size: 26px; font-weight: 800; color: var(--gold-light); margin-bottom: 6px; direction: ltr; }
        .stat-label { font-size: 13px; color: var(--text-muted); }

        .features-section { padding: 20px 24px 50px; }
        .section-title { text-align: center; font-size: 24px; font-weight: 800; margin-bottom: 28px; }
        .section-title .gold-text { color: var(--gold-light); }
        .feature-list { display: flex; flex-direction: column; gap: 16px; max-width: 500px; margin: 0 auto; }
        .feature-item {
            display: flex; align-items: center; gap: 18px; padding: 22px 20px;
            background: var(--bg-card); border: 1px solid var(--border); border-radius: 18px;
            transition: all 0.3s ease; animation: slideUp 0.5s ease both;
        }
        .feature-item:nth-child(1) { animation-delay: 0.6s; }
        .feature-item:nth-child(2) { animation-delay: 0.7s; }
        .feature-item:hover { border-color: rgba(212, 165, 38, 0.3); transform: translateX(-4px); }

        .feature-icon {
            width: 56px; height: 56px; min-width: 56px; border-radius: 50%;
            display: flex; align-items: center; justify-content: center; font-size: 22px;
        }
        .feature-icon.gold { background: rgba(212, 165, 38, 0.15); color: var(--gold-light); }
        .feature-icon.blue { background: rgba(59, 130, 246, 0.15); color: #60a5fa; }
        .feature-text { flex: 1; }
        .feature-text h3 { font-size: 16px; font-weight: 700; margin-bottom: 6px; }
        .feature-text p { font-size: 13px; color: var(--text-muted); line-height: 1.6; }

        /* ===== AUTH ===== */
        .auth-container { min-height: 100vh; display: flex; flex-direction: column; align-items: center; justify-content: center; padding: 24px; }
        .auth-card {
            width: 100%; max-width: 420px; background: var(--bg-card);
            border: 1px solid var(--border); border-radius: 24px; padding: 36px 28px; animation: scaleIn 0.5s ease;
        }
        .auth-header { text-align: center; margin-bottom: 32px; }
        .auth-header .back-btn {
            position: absolute; right: 0; top: 0; background: none; border: none;
            color: var(--text-secondary); font-size: 20px; cursor: pointer; padding: 8px; transition: color 0.3s;
        }
        .auth-header .back-btn:hover { color: var(--gold); }
        .auth-header h2 { font-size: 26px; font-weight: 800; margin-bottom: 8px; }
        .auth-header p { color: var(--text-muted); font-size: 14px; }

        .form-group { margin-bottom: 20px; position: relative; }
        .form-group label { display: block; font-size: 14px; font-weight: 600; margin-bottom: 8px; color: var(--text-secondary); }
        .input-wrapper { position: relative; }
        .input-wrapper i { position: absolute; right: 16px; top: 50%; transform: translateY(-50%); color: var(--text-muted); font-size: 16px; pointer-events: none; }
        .form-input {
            width: 100%; padding: 14px 48px 14px 16px; background: var(--bg-secondary);
            border: 1px solid var(--border); border-radius: 12px; font-size: 16px;
            font-family: inherit; color: var(--text-primary); transition: all 0.3s ease; outline: none;
        }
        .form-input:focus { border-color: var(--gold); box-shadow: 0 0 0 3px rgba(212, 165, 38, 0.1); }
        .form-input::placeholder { color: var(--text-muted); }
        .password-toggle {
            position: absolute; left: 16px; top: 50%; transform: translateY(-50%);
            background: none; border: none; color: var(--text-muted); cursor: pointer; font-size: 16px; pointer-events: all;
        }
        .form-error { color: var(--error); font-size: 13px; margin-top: 6px; display: none; }
        .form-error.show { display: block; }
        .auth-footer { text-align: center; margin-top: 24px; font-size: 14px; color: var(--text-muted); }
        .auth-footer a { color: var(--gold); text-decoration: none; font-weight: 600; cursor: pointer; }
        .auth-footer a:hover { text-decoration: underline; }

        /* ===== DASHBOARD ===== */
        .dashboard { min-height: 100vh; padding-bottom: 90px; }
        .dash-header {
            padding: 20px 24px; display: flex; justify-content: space-between; align-items: center;
            border-bottom: 1px solid var(--border);
        }
        .user-info { display: flex; align-items: center; gap: 12px; }
        .user-avatar {
            width: 44px; height: 44px; background: linear-gradient(135deg, var(--gold), var(--gold-dark));
            border-radius: 14px; display: flex; align-items: center; justify-content: center;
            font-size: 18px; font-weight: 800; color: #000;
        }
        .user-name { font-weight: 700; font-size: 16px; }
        .user-status { display: flex; align-items: center; gap: 6px; font-size: 12px; color: var(--success); }
        .user-status .dot { width: 6px; height: 6px; background: var(--success); border-radius: 50%; }
        .logout-btn {
            background: var(--bg-card); border: 1px solid var(--border); color: var(--text-secondary);
            padding: 10px 14px; border-radius: 12px; cursor: pointer; font-size: 16px; transition: all 0.3s;
        }
        .logout-btn:hover { border-color: var(--error); color: var(--error); }

        .dash-content { padding: 24px; max-width: 600px; margin: 0 auto; }
        .balance-card {
            background: linear-gradient(135deg, #1a2235, #0f172a);
            border: 1px solid rgba(212, 165, 38, 0.2); border-radius: 24px; padding: 28px 24px;
            margin-bottom: 24px; position: relative; overflow: hidden;
        }
        .balance-card::before {
            content: ''; position: absolute; top: -50%; left: -50%; width: 200%; height: 200%;
            background: radial-gradient(circle at 30% 30%, rgba(212, 165, 38, 0.08), transparent 50%); pointer-events: none;
        }
        .balance-label { font-size: 14px; color: var(--text-muted); margin-bottom: 8px; }
        .balance-amount { font-size: 40px; font-weight: 900; color: var(--gold-light); direction: ltr; text-align: right; }
        .balance-amount small { font-size: 18px; color: var(--text-muted); }
        .balance-change {
            display: inline-flex; align-items: center; gap: 4px; padding: 4px 12px;
            background: rgba(34, 197, 94, 0.1); color: var(--success); border-radius: 20px;
            font-size: 13px; font-weight: 600; margin-top: 12px;
        }

        .dash-actions { display: grid; grid-template-columns: repeat(2, 1fr); gap: 12px; margin-bottom: 28px; }
        .dash-action-btn {
            padding: 18px; background: var(--bg-card); border: 1px solid var(--border);
            border-radius: 16px; cursor: pointer; text-align: center; transition: all 0.3s;
            font-family: inherit; color: var(--text-primary); text-decoration: none;
            display: flex; flex-direction: column; align-items: center; justify-content: center;
        }
        .dash-action-btn:hover { border-color: rgba(212, 165, 38, 0.3); transform: translateY(-2px); }
        .dash-action-btn i { font-size: 24px; color: var(--gold); display: block; margin-bottom: 8px; }
        .dash-action-btn span { font-size: 14px; font-weight: 600; }

        .recent-section h3 { font-size: 18px; font-weight: 700; margin-bottom: 16px; }
        .transaction-list { display: flex; flex-direction: column; gap: 10px; }
        .transaction-item {
            display: flex; align-items: center; gap: 14px; padding: 16px;
            background: var(--bg-card); border: 1px solid var(--border); border-radius: 14px; transition: all 0.3s;
        }
        .transaction-item:hover { border-color: rgba(212, 165, 38, 0.2); }
        .tx-icon { width: 42px; height: 42px; min-width: 42px; border-radius: 12px; display: flex; align-items: center; justify-content: center; font-size: 16px; }
        .tx-icon.deposit { background: rgba(34, 197, 94, 0.1); color: var(--success); }
        .tx-icon.withdraw { background: rgba(239, 68, 68, 0.1); color: var(--error); }
        .tx-icon.profit { background: rgba(212, 165, 38, 0.1); color: var(--gold); }
        .tx-info { flex: 1; }
        .tx-info .tx-name { font-weight: 600; font-size: 14px; }
        .tx-info .tx-date { font-size: 12px; color: var(--text-muted); margin-top: 2px; }
        .tx-amount { font-weight: 700; font-size: 15px; direction: ltr; }
        .tx-amount.positive { color: var(--success); }
        .tx-amount.negative { color: var(--error); }

        /* ===== BOTTOM NAV ===== */
        .bottom-nav {
            position: fixed; bottom: 0; left: 0; width: 100%; z-index: 50;
            border-top: 1px solid var(--border);
            display: none; padding: 8px 0 12px; backdrop-filter: blur(12px);
            background: rgba(17, 24, 39, 0.95);
        }
        .bottom-nav.show { display: flex; justify-content: space-around; align-items: center; }
        .bottom-nav-item {
            display: flex; flex-direction: column; align-items: center; gap: 4px;
            background: none; border: none; color: var(--text-muted); font-family: inherit;
            font-size: 11px; font-weight: 600; cursor: pointer; padding: 6px 14px;
            border-radius: 12px; transition: all 0.3s;
        }
        .bottom-nav-item i { font-size: 20px; transition: all 0.3s; }
        .bottom-nav-item.active { color: var(--gold-light); }
        .bottom-nav-item.active i { transform: scale(1.15); }
        .bottom-nav-item:hover { color: var(--gold); }
        .bottom-nav-center {
            width: 56px; height: 56px; border-radius: 50%;
            background: linear-gradient(135deg, var(--gold), var(--gold-dark));
            border: 4px solid var(--bg-secondary); color: #000; font-size: 22px;
            display: flex; align-items: center; justify-content: center; cursor: pointer;
            margin-top: -28px; box-shadow: 0 4px 20px rgba(212, 165, 38, 0.4);
            transition: all 0.3s;
        }
        .bottom-nav-center:hover { transform: scale(1.08); }
        .bottom-nav-center.active { box-shadow: 0 4px 25px rgba(212, 165, 38, 0.6); }

        /* ===== INVESTMENT PAGE ===== */
        .invest-page { min-height: 100vh; padding-bottom: 90px; }
        .invest-header {
            padding: 20px 24px; display: flex; align-items: center; gap: 14px;
            border-bottom: 1px solid var(--border);
        }
        .invest-back-btn {
            background: var(--bg-card); border: 1px solid var(--border); color: var(--text-secondary);
            width: 40px; height: 40px; border-radius: 12px; cursor: pointer; font-size: 16px;
            display: flex; align-items: center; justify-content: center; transition: all 0.3s;
        }
        .invest-back-btn:hover { border-color: var(--gold); color: var(--gold); }
        .invest-header h2 { font-size: 20px; font-weight: 800; flex: 1; }
        .invest-header h2 i { color: var(--gold); margin-left: 8px; }

        .invest-content { padding: 20px; max-width: 600px; margin: 0 auto; }

        .plans-grid { display: grid; grid-template-columns: repeat(2, 1fr); gap: 14px; }

        .plan-card {
            background: var(--bg-card); border: 1px solid var(--border); border-radius: 20px;
            overflow: hidden; transition: all 0.3s; animation: slideUp 0.5s ease both;
            position: relative;
        }
        .plan-card:nth-child(1) { animation-delay: 0.1s; }
        .plan-card:nth-child(2) { animation-delay: 0.2s; }
        .plan-card:nth-child(3) { animation-delay: 0.3s; }
        .plan-card:nth-child(4) { animation-delay: 0.4s; }
        .plan-card:nth-child(5) { animation-delay: 0.5s; }
        .plan-card:nth-child(6) { animation-delay: 0.6s; }
        .plan-card:hover { border-color: rgba(212, 165, 38, 0.4); transform: translateY(-4px); }

        .plan-card-top {
            height: 100px; display: flex; align-items: center; justify-content: center;
            position: relative; overflow: hidden;
        }
        .plan-card-top::before {
            content: ''; position: absolute; inset: 0;
            background: linear-gradient(135deg, rgba(212, 165, 38, 0.12), rgba(212, 165, 38, 0.03));
        }
        .plan-icon-wrap {
            width: 64px; height: 64px; border-radius: 50%;
            display: flex; align-items: center; justify-content: center;
            font-size: 28px; position: relative; z-index: 1;
        }
        .plan-icon-wrap.bronze { background: rgba(205, 127, 50, 0.2); color: #cd7f32; }
   

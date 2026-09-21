# MEDICORE
<!DOCTYPE html>
<html lang="en">

<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>MediCore - Enterprise Safe Space & Case Portal</title>
    <!-- Modern Google Font -->
    <link rel="preconnect" href="https://fonts.googleapis.com">
    <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
    <link href="https://fonts.googleapis.com/css2?family=Plus+Jakarta+Sans:wght@300;400;500;600;700;800&family=Noto+Sans:wght@400;600;700&display=swap"
        rel="stylesheet">
    <!-- Chart.js for Multi-Layered Trauma Trajectory Timeline -->
    <script src="https://cdn.jsdelivr.net/npm/chart.js"></script>

    <style>
        :root {
            --font-main: 'Plus Jakarta Sans', 'Noto Sans', -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, sans-serif;

            /* Default: Safe-Feeling Dark Green & Healing Palette (Patient) */
            --bg-body: #0A1412;
            --header-bg: #071917;
            --sidebar-bg: #051311;
            --btn-primary: #10B981;
            --btn-primary-hover: #059669;
            --btn-secondary: #14B8A6;
            --btn-secondary-hover: #0D9488;
            --surface-card: #11221F;
            --surface-card-hover: #152926;
            --alert-important: #F59E0B;
            --alert-emergency: #F87171;
            --text-primary: #ECFDF5;
            --text-secondary: #A7F3D0;
            --text-muted: #6EE7B7;
            --text-dim: #94A3B8;
            --border-subtle: rgba(52, 211, 153, 0.16);
            --surface-input: #0B1715;
            --surface-alt: #0D1C19;

            --radius-sm: 8px;
            --radius-md: 14px;
            --radius-lg: 20px;
            --radius-full: 9999px;

            --shadow-card: 0 10px 30px -10px rgba(0, 0, 0, 0.5), 0 2px 8px -2px rgba(0, 0, 0, 0.3);

            /* Quiet Check-In Specific Palette */
            --ink: #243b36;
            --sage-deep: #3f6b5f;
            --sage: #7fa593;
            --sage-pale: #e4ede7;
            --sand: #f7f4ee;
            --gold: #c9a366;
            --line: #d8ddd8;
            --danger-quiet: #a86a5a;
        }

        /* LOGIN PAGE THEME (Eye-Warming Rose Pink) */
        body.login-active {
            --btn-primary: #F43F5E; 
            --btn-primary-hover: #E11D48;
            --btn-secondary: #FB7185;
            --text-secondary: #FDA4AF;
            --border-subtle: rgba(244, 63, 94, 0.3);
        }

        body.login-active .orb-1 { background: rgba(244, 63, 94, 0.16); }
        body.login-active .orb-2 { background: rgba(251, 113, 133, 0.14); }
        body.login-active .language-switcher-wrapper svg { color: var(--btn-primary); }

        /* ADMIN THEME (Authoritative Blue) */
        body.admin-theme {
            --bg-body: #040914;
            --header-bg: #02060d;
            --sidebar-bg: #01040a;
            --btn-primary: #3B82F6;
            --btn-primary-hover: #2563EB;
            --btn-secondary: #0EA5E9;
            --btn-secondary-hover: #0284C7;
            --surface-card: #0B1121;
            --surface-card-hover: #0F172A;
            --text-primary: #F8FAFC;
            --text-secondary: #BAE6FD;
            --text-muted: #7DD3FC;
            --border-subtle: rgba(59, 130, 246, 0.16);
            --surface-input: #070B14;
            --surface-alt: #090E1A;
            --sage: #3B82F6;
            background-image: radial-gradient(at 0% 0%, rgba(59, 130, 246, 0.12) 0px, transparent 55%), radial-gradient(at 100% 100%, rgba(14, 165, 233, 0.10) 0px, transparent 55%);
        }

        body.admin-theme .orb-1 { background: rgba(59, 130, 246, 0.16); }
        body.admin-theme .orb-2 { background: rgba(14, 165, 233, 0.14); }

        /* SUPERADMIN THEME (White and Dark Blue) */
        body.superadmin-theme {
            --bg-body: #F0F4F8;
            --header-bg: #FFFFFF;
            --sidebar-bg: #FFFFFF;
            --btn-primary: #1E3A8A; 
            --btn-primary-hover: #1E40AF;
            --btn-secondary: #3B82F6;
            --btn-secondary-hover: #2563EB;
            --surface-card: #FFFFFF;
            --surface-card-hover: #F8FAFC;
            --text-primary: #0F172A;
            --text-secondary: #334155;
            --text-muted: #475569;
            --border-subtle: #CBD5E1;
            --surface-input: #F8FAFC;
            --surface-alt: #F1F5F9;
            --shadow-card: 0 4px 6px -1px rgba(0, 0, 0, 0.1), 0 2px 4px -1px rgba(0, 0, 0, 0.06);
            background-image: none;
        }

        body.superadmin-theme .dash-nav { border-bottom: 2px solid var(--btn-primary); }
        body.superadmin-theme .admin-kpi-card { border-left: 4px solid var(--btn-primary); }
        body.superadmin-theme .admin-table th { background: var(--btn-primary); color: white; border-bottom: none; }
        body.superadmin-theme .admin-table td { color: var(--text-primary); border-bottom: 1px solid var(--border-subtle); }
        body.superadmin-theme .admin-action-btn { background: #FFFFFF; border: 1px solid var(--border-subtle); color: var(--text-primary); box-shadow: var(--shadow-card); }
        body.superadmin-theme .admin-action-title { color: var(--text-primary); }
        
        /* Fix Sign Out Button for Superadmin to be perfectly visible */
        body.superadmin-theme .logout-btn { color: #1E3A8A !important; border: 2px solid #1E3A8A !important; background: transparent !important; font-weight: 800 !important; }
        body.superadmin-theme .logout-btn:hover { background: rgba(30, 58, 138, 0.1) !important; }
        body.superadmin-theme .user-name-display { color: var(--text-primary); }
        body.superadmin-theme .user-role-display { color: var(--text-secondary); }

        /* ADMIN EMERGENCY THEME (High Alert Red) */
        body.admin-emergency-theme {
            --bg-body: #1a0505;
            --header-bg: #2b0808;
            --sidebar-bg: #1f0404;
            --btn-primary: #ef4444;
            --btn-primary-hover: #dc2626;
            --btn-secondary: #f87171;
            --btn-secondary-hover: #ef4444;
            --surface-card: #3f0f0f;
            --surface-card-hover: #451010;
            --text-primary: #fef2f2;
            --text-secondary: #fecaca;
            --text-muted: #fca5a5;
            --border-subtle: rgba(239, 68, 68, 0.3);
            --surface-input: #2b0808;
            --surface-alt: #451010;
            --sage: #ef4444;
            background-image: radial-gradient(at 0% 0%, rgba(239, 68, 68, 0.15) 0px, transparent 55%), radial-gradient(at 100% 100%, rgba(248, 113, 113, 0.12) 0px, transparent 55%);
        }

        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
            font-family: var(--font-main);
        }

        body {
            background-color: var(--bg-body);
            color: var(--text-primary);
            min-height: 100vh;
            display: flex;
            flex-direction: column;
            overflow-x: hidden;
            position: relative;
            background-attachment: fixed;
            transition: background-color 0.4s ease, background-image 0.4s ease;
        }

        /* Top Bar Controls */
        .language-switcher-wrapper {
            position: absolute;
            top: 24px;
            right: 28px;
            z-index: 10;
            display: flex;
            align-items: center;
            gap: 8px;
            background: var(--surface-card);
            border: 1px solid var(--border-subtle);
            padding: 6px 12px;
            border-radius: var(--radius-full);
            box-shadow: var(--shadow-card);
        }

        .language-switcher-wrapper svg {
            width: 16px;
            height: 16px;
            color: var(--btn-primary);
        }

        .language-select {
            background: transparent;
            border: none;
            color: var(--text-primary);
            font-size: 0.85rem;
            font-weight: 600;
            outline: none;
            cursor: pointer;
        }

        .language-select option {
            background: #0B1715;
            color: #ECFDF5;
        }

        /* Privacy & Safety Navigation Toolbar */
        .btn-quick-exit {
            background: rgba(239, 68, 68, 0.18);
            border: 1px solid rgba(239, 68, 68, 0.45);
            color: #FECACA;
            font-size: 0.78rem;
            font-weight: 700;
            padding: 0.4rem 0.8rem;
            border-radius: var(--radius-full);
            cursor: pointer;
            display: flex;
            align-items: center;
            gap: 5px;
            transition: 0.2s;
        }

        .btn-quick-exit:hover {
            background: #ef4444;
            color: white;
        }

        .btn-stealth-cover {
            background: rgba(255, 255, 255, 0.08);
            border: 1px solid var(--border-subtle);
            color: var(--text-secondary);
            font-size: 0.78rem;
            font-weight: 600;
            padding: 0.4rem 0.75rem;
            border-radius: var(--radius-full);
            cursor: pointer;
        }

        .btn-stealth-cover:hover {
            background: rgba(255, 255, 255, 0.15);
        }

        .btn-demo-sim {
            background: rgba(59, 130, 246, 0.2);
            border: 1px solid #3b82f6;
            color: #93c5fd;
            font-size: 0.78rem;
            font-weight: 700;
            padding: 0.4rem 0.8rem;
            border-radius: var(--radius-full);
            cursor: pointer;
            display: flex;
            align-items: center;
            gap: 5px;
        }

        .btn-demo-sim:hover {
            background: #3b82f6;
            color: white;
        }

        .btn-tour {
            background: rgba(16, 185, 129, 0.2);
            border: 1px solid var(--btn-primary);
            color: var(--text-primary);
            font-size: 0.78rem;
            font-weight: 700;
            padding: 0.4rem 0.8rem;
            border-radius: var(--radius-full);
            cursor: pointer;
        }

        .btn-tour:hover {
            background: var(--btn-primary);
            color: #04241F;
        }

        /* Universal Back Button Styling */
        .btn-universal-back {
            background: rgba(255, 255, 255, 0.08);
            border: 1px solid var(--border-subtle);
            color: var(--text-secondary);
            font-size: 0.8rem;
            font-weight: 700;
            padding: 0.4rem 0.9rem;
            border-radius: var(--radius-full);
            cursor: pointer;
            display: inline-flex;
            align-items: center;
            gap: 6px;
            transition: 0.2s;
            margin-bottom: 0.5rem;
        }

        .btn-universal-back:hover {
            background: rgba(255, 255, 255, 0.15);
            color: var(--text-primary);
        }

        /* Real-Time Telemetry Ticker Banner */
        .telemetry-ticker-bar {
            background: rgba(15, 23, 42, 0.9);
            border-bottom: 1px solid rgba(59, 130, 246, 0.3);
            color: #93c5fd;
            padding: 0.5rem 1.5rem;
            font-size: 0.82rem;
            font-weight: 600;
            display: flex;
            align-items: center;
            gap: 12px;
            overflow: hidden;
            white-space: nowrap;
        }

        .ticker-pulsar {
            width: 8px;
            height: 8px;
            background: #3b82f6;
            border-radius: 50%;
            box-shadow: 0 0 8px #3b82f6;
            animation: pulse 1.5s infinite;
        }

        /* Cover Screen Camouflage */
        #camouflage-screen {
            display: none;
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background: #ffffff;
            color: #1e293b;
            z-index: 999999;
            padding: 4rem 2rem;
            overflow-y: auto;
            font-family: Georgia, serif;
        }

        #camouflage-screen.active {
            display: block;
        }

        .ambient-orb {
            position: fixed;
            border-radius: 50%;
            filter: blur(110px);
            z-index: 0;
            pointer-events: none;
            opacity: 0.65;
            transition: background 0.4s ease;
        }

        .orb-1 { width: 480px; height: 480px; top: -100px; left: -100px; background: rgba(16, 185, 129, 0.16); }
        .orb-2 { width: 520px; height: 520px; bottom: -150px; right: -100px; background: rgba(20, 184, 166, 0.14); }

        .app-screen {
            position: relative;
            z-index: 1;
            width: 100%;
            min-height: 100vh;
            display: none;
            opacity: 0;
            transition: opacity 0.3s ease;
        }

        .app-screen.active {
            display: flex;
            opacity: 1;
            flex-direction: column;
        }

        /* Login Screen */
        #screen-login {
            align-items: center;
            justify-content: center;
            padding: 2.5rem 1.5rem;
        }

        .login-container {
            width: 100%;
            max-width: 480px;
            display: flex;
            flex-direction: column;
            gap: 1.5rem;
        }

        .login-brand-header {
            display: flex;
            flex-direction: column;
            align-items: center;
            text-align: center;
        }

        .brand-badge {
            display: flex;
            align-items: center;
            justify-content: center;
            gap: 0.5rem;
            background: rgba(16, 185, 129, 0.12);
            border: 1px solid var(--border-subtle);
            padding: 0.4rem 1.1rem;
            border-radius: var(--radius-full);
            font-size: 0.82rem;
            font-weight: 700;
            color: var(--text-secondary);
            margin: 0 auto 1rem auto;
            text-transform: uppercase;
            width: fit-content;
        }

        .brand-badge .status-dot {
            width: 8px;
            height: 8px;
            background: var(--btn-primary);
            border-radius: 50%;
            box-shadow: 0 0 10px var(--btn-primary);
            display: inline-block;
            flex-shrink: 0;
        }

        .login-brand-header h1 {
            font-size: 2.2rem;
            font-weight: 800;
            margin-bottom: 0.5rem;
        }

        .login-tabs {
            display: flex;
            background: rgba(0, 0, 0, 0.2);
            border-radius: 12px;
            padding: 5px;
            margin-bottom: 1rem;
        }

        .login-tab-btn {
            flex: 1;
            padding: 0.8rem;
            border: none;
            background: transparent;
            color: var(--text-secondary);
            font-weight: 700;
            cursor: pointer;
            border-radius: 8px;
            transition: 0.3s;
        }

        .login-tab-btn.active {
            background: var(--btn-primary);
            color: #04241F;
        }

        .login-card {
            background: var(--surface-card);
            border: 1px solid var(--border-subtle);
            border-radius: var(--radius-lg);
            padding: 2.5rem;
            box-shadow: var(--shadow-card);
            position: relative;
            overflow: hidden;
            backdrop-filter: blur(8px);
        }

        .login-form {
            display: none;
            flex-direction: column;
            gap: 1.25rem;
        }

        .login-form.active {
            display: flex;
            animation: fadeIn 0.4s;
        }

        .form-group {
            display: flex;
            flex-direction: column;
            gap: 0.45rem;
        }

        .form-label {
            display: flex;
            justify-content: space-between;
            font-size: 0.86rem;
            font-weight: 600;
            color: var(--text-secondary);
        }

        body.superadmin-theme .form-label { color: var(--text-secondary); }

        .input-box {
            position: relative;
            display: flex;
            align-items: center;
        }

        .input-box svg {
            position: absolute;
            left: 1rem;
            width: 18px;
            height: 18px;
            color: #5E8075;
            pointer-events: none;
        }

        /* Global Input Styling to enforce dark theme in modals and patient views */
        .form-input, .user-editable, .diary-textarea, #nc-type, #nc-priority {
            background-color: var(--surface-input) !important;
            color: var(--text-primary) !important;
            border: 1px solid var(--border-subtle);
            border-radius: var(--radius-sm);
        }

        .input-box input {
            width: 100%;
            padding: 0.9rem 1rem 0.9rem 2.85rem;
            background-color: var(--surface-input) !important;
            border: 1px solid var(--border-subtle);
            border-radius: var(--radius-sm);
            color: var(--text-primary) !important;
            font-size: 0.95rem;
            outline: none;
            transition: 0.2s;
        }

        .input-box input:focus {
            border-color: var(--btn-primary);
            box-shadow: 0 0 0 3px rgba(16, 185, 129, 0.25);
        }

        .login-error-banner {
            display: none;
            align-items: center;
            gap: 0.6rem;
            padding: 0.75rem 1rem;
            margin-bottom: 1.25rem;
            background: rgba(248, 113, 113, 0.12);
            border: 1px solid rgba(248, 113, 113, 0.35);
            border-radius: var(--radius-sm);
            color: var(--alert-emergency);
            font-size: 0.84rem;
            font-weight: 600;
        }

        .login-error-banner.active { display: flex; }

        .btn-login-submit {
            padding: 0.95rem 1.5rem;
            border: none;
            border-radius: var(--radius-sm);
            background: var(--btn-primary);
            color: #04241F;
            font-size: 0.98rem;
            font-weight: 800;
            cursor: pointer;
            display: flex;
            align-items: center;
            justify-content: center;
            gap: 0.5rem;
            margin-top: 0.5rem;
            transition: 0.2s;
            width: 100%;
        }

        .btn-login-submit:hover {
            background: var(--btn-primary-hover);
            transform: translateY(-2px);
        }

        .otp-toggle {
            display: flex;
            gap: 10px;
            margin-bottom: 0.5rem;
        }

        .otp-btn {
            flex: 1;
            background: var(--surface-input);
            color: var(--text-secondary);
            border: 1px solid var(--border-subtle);
            padding: 8px;
            border-radius: 6px;
            cursor: pointer;
            font-size: 0.8rem;
            font-weight: bold;
        }

        .otp-btn.active {
            background: rgba(244, 63, 94, 0.15); /* Match login rose pink */
            border-color: var(--btn-primary);
            color: var(--text-primary);
        }

        /* Sidebar & Header */
        .sidebar-overlay {
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background: rgba(0, 0, 0, 0.6);
            z-index: 199;
            display: none;
            backdrop-filter: blur(4px);
        }

        .sidebar-overlay.active { display: block; }

        .patient-sidebar {
            position: fixed;
            top: 0;
            left: -320px;
            width: 300px;
            height: 100%;
            background: var(--sidebar-bg);
            border-right: 1px solid var(--border-subtle);
            z-index: 200;
            transition: left 0.3s ease;
            display: flex;
            flex-direction: column;
            padding: 2rem 1.5rem;
            box-shadow: 4px 0 20px rgba(0, 0, 0, 0.5);
            overflow-
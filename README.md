#MEDICOREPORTAL
<!DOCTYPE html>
<html lang="en">

<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>MediCore - Enterprise Safe Space & Case Portal</title>
    <!-- Modern Google Font -->
    <link rel="preconnect" href="https://fonts.googleapis.com">
    <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
    <link
        href="https://fonts.googleapis.com/css2?family=Plus+Jakarta+Sans:wght@300;400;500;600;700;800&family=Noto+Sans:wght@400;600;700&display=swap"
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

        body.login-active .orb-1 {
            background: rgba(244, 63, 94, 0.16);
        }

        body.login-active .orb-2 {
            background: rgba(251, 113, 133, 0.14);
        }

        body.login-active .language-switcher-wrapper svg {
            color: var(--btn-primary);
        }

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

        body.admin-theme .orb-1 {
            background: rgba(59, 130, 246, 0.16);
        }

        body.admin-theme .orb-2 {
            background: rgba(14, 165, 233, 0.14);
        }

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

        body.superadmin-theme .dash-nav {
            border-bottom: 2px solid var(--btn-primary);
        }

        body.superadmin-theme .admin-kpi-card {
            border-left: 4px solid var(--btn-primary);
        }

        body.superadmin-theme .admin-table th {
            background: var(--btn-primary);
            color: white;
            border-bottom: none;
        }

        body.superadmin-theme .admin-table td {
            color: var(--text-primary);
            border-bottom: 1px solid var(--border-subtle);
        }

        body.superadmin-theme .admin-action-btn {
            background: #FFFFFF;
            border: 1px solid var(--border-subtle);
            color: var(--text-primary);
            box-shadow: var(--shadow-card);
        }

        body.superadmin-theme .admin-action-title {
            color: var(--text-primary);
        }

        /* Fix Sign Out Button for Superadmin to be perfectly visible */
        body.superadmin-theme .logout-btn {
            color: #1E3A8A !important;
            border: 2px solid #1E3A8A !important;
            background: transparent !important;
            font-weight: 800 !important;
        }

        body.superadmin-theme .logout-btn:hover {
            background: rgba(30, 58, 138, 0.1) !important;
        }

        body.superadmin-theme .user-name-display {
            color: var(--text-primary);
        }

        body.superadmin-theme .user-role-display {
            color: var(--text-secondary);
        }

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

        .orb-1 {
            width: 480px;
            height: 480px;
            top: -100px;
            left: -100px;
            background: rgba(16, 185, 129, 0.16);
        }

        .orb-2 {
            width: 520px;
            height: 520px;
            bottom: -150px;
            right: -100px;
            background: rgba(20, 184, 166, 0.14);
        }

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

        body.superadmin-theme .form-label {
            color: var(--text-secondary);
        }

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
        .form-input,
        .user-editable,
        .diary-textarea,
        #nc-type,
        #nc-priority {
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

        .login-error-banner.active {
            display: flex;
        }

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
            background: rgba(244, 63, 94, 0.15);
            /* Match login rose pink */
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

        .sidebar-overlay.active {
            display: block;
        }

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
            overflow-y: auto;
        }

        .patient-sidebar.active {
            left: 0;
        }

        .sidebar-close {
            align-self: flex-end;
            background: none;
            border: none;
            color: var(--text-secondary);
            font-size: 1.5rem;
            cursor: pointer;
            margin-bottom: 2rem;
        }

        .sidebar-nav {
            display: flex;
            flex-direction: column;
            gap: 0.5rem;
            height: 100%;
        }

        .sidebar-nav button {
            background: transparent;
            border: 1px solid transparent;
            border-radius: var(--radius-sm);
            padding: 1rem 1.25rem;
            text-align: left;
            font-size: 1.05rem;
            font-weight: 600;
            color: var(--btn-secondary);
            cursor: pointer;
            transition: all 0.2s ease;
            display: flex;
            align-items: center;
            gap: 0.75rem;
        }

        .sidebar-nav button:hover {
            background: rgba(255, 255, 255, 0.05);
            color: var(--text-primary);
        }

        .sidebar-nav button.active {
            background: rgba(255, 255, 255, 0.1);
            border-color: rgba(255, 255, 255, 0.2);
            color: #FFFFFF;
            box-shadow: 0 4px 15px rgba(0, 0, 0, 0.2);
        }

        .sidebar-nav-bottom {
            margin-top: auto;
            padding-top: 1rem;
            border-top: 1px solid rgba(255, 255, 255, 0.1);
        }

        .dash-nav {
            background: var(--header-bg);
            padding: 0.9rem 2rem;
            display: flex;
            align-items: center;
            justify-content: space-between;
            position: sticky;
            top: 0;
            z-index: 100;
            border-bottom: 1px solid var(--border-subtle);
            box-shadow: 0 4px 20px -2px rgba(0, 0, 0, 0.4);
        }

        .dash-nav-brand {
            display: flex;
            align-items: center;
            gap: 1rem;
        }

        .menu-toggle-btn {
            background: var(--btn-primary);
            border: none;
            color: #04241F;
            cursor: pointer;
            display: flex;
            align-items: center;
            justify-content: center;
            padding: 0.6rem;
            border-radius: var(--radius-sm);
            transition: 0.2s;
        }

        .dash-nav-logo {
            width: 38px;
            height: 38px;
            border-radius: var(--radius-sm);
            display: flex;
            align-items: center;
            justify-content: center;
            font-weight: 800;
            font-size: 1.1rem;
            color: #04241F;
            background: var(--btn-primary);
        }

        .dash-nav-title strong {
            font-size: 1.05rem;
            font-weight: 700;
            display: block;
        }

        .dash-nav-title span {
            font-size: 0.78rem;
            color: var(--text-secondary);
            text-transform: uppercase;
            font-weight: 600;
            opacity: 0.85;
        }

        .dash-nav-actions {
            display: flex;
            align-items: center;
            gap: 0.85rem;
        }

        .user-status-pill {
            display: flex;
            align-items: center;
            gap: 0.75rem;
            background: var(--surface-alt);
            border: 1px solid var(--border-subtle);
            padding: 0.4rem 0.85rem;
            border-radius: var(--radius-full);
            cursor: pointer;
        }

        .user-avatar {
            width: 30px;
            height: 30px;
            border-radius: 50%;
            display: flex;
            align-items: center;
            justify-content: center;
            font-weight: 800;
            font-size: 0.82rem;
            color: #04241F;
            background: var(--btn-primary);
        }

        .user-name-display {
            font-size: 0.85rem;
            font-weight: 700;
            color: var(--text-primary);
        }

        .user-role-display {
            font-size: 0.7rem;
            color: var(--text-secondary);
            text-transform: uppercase;
        }

        .btn-emergency-header {
            display: flex;
            align-items: center;
            gap: 5px;
            background: rgba(248, 113, 113, 0.15);
            border: 1px solid var(--alert-emergency);
            color: #FECACA;
            padding: 0.4rem 1rem;
            border-radius: var(--radius-full);
            font-weight: bold;
            cursor: pointer;
            animation: pulse 2s infinite;
        }

        .logout-btn {
            display: inline-flex;
            align-items: center;
            gap: 0.45rem;
            background: rgba(255, 255, 255, 0.1);
            border: 1px solid rgba(255, 255, 255, 0.2);
            color: white;
            padding: 0.5rem 1rem;
            border-radius: var(--radius-sm);
            font-size: 0.85rem;
            font-weight: 600;
            cursor: pointer;
            transition: 0.2s;
        }

        .logout-btn:hover {
            background: rgba(255, 255, 255, 0.2);
        }

        .dash-container {
            max-width: 1280px;
            width: 100%;
            margin: 0 auto;
            padding: 2.25rem 2rem 4rem;
            display: flex;
            flex-direction: column;
            gap: 2rem;
            flex-grow: 1;
        }

        .dash-section-card {
            background: var(--surface-card);
            border: 1px solid var(--border-subtle);
            border-radius: var(--radius-lg);
            padding: 1.5rem;
            display: flex;
            flex-direction: column;
            gap: 1.25rem;
            box-shadow: var(--shadow-card);
        }

        .section-header {
            display: flex;
            align-items: center;
            justify-content: space-between;
        }

        .section-header h3 {
            font-size: 1.15rem;
            font-weight: 700;
            display: flex;
            align-items: center;
            gap: 0.6rem;
            color: var(--text-primary);
        }

        .dash-hero {
            background: var(--surface-card);
            border: 1px solid var(--border-subtle);
            border-radius: var(--radius-lg);
            padding: 2rem 2.5rem;
            display: flex;
            align-items: center;
            justify-content: space-between;
            flex-wrap: wrap;
            gap: 1.5rem;
            box-shadow: var(--shadow-card);
        }

        .dash-cols-even {
            display: grid;
            grid-template-columns: repeat(2, 1fr);
            gap: 1.75rem;
        }

        .patient-tab-content {
            display: none;
            flex-direction: column;
            gap: 2rem;
            animation: fadeIn 0.4s ease;
        }

        .patient-tab-content.active {
            display: flex;
        }

        @keyframes fadeIn {
            from {
                opacity: 0;
                transform: translateY(10px);
            }

            to {
                opacity: 1;
                transform: translateY(0);
            }
        }

        .gauge-wrapper {
            position: relative;
            width: 220px;
            height: 110px;
            overflow: hidden;
            margin: 0 auto 1rem auto;
        }

        .gauge-bg {
            position: absolute;
            top: 0;
            left: 0;
            width: 220px;
            height: 220px;
            border-radius: 50%;
            border: 20px solid rgba(255, 255, 255, 0.05);
        }

        .gauge-fill {
            position: absolute;
            top: 0;
            left: 0;
            width: 220px;
            height: 220px;
            border-radius: 50%;
            border: 20px solid var(--btn-primary);
            border-bottom-color: transparent;
            border-left-color: transparent;
            transform: rotate(-45deg);
            transition: transform 1.5s cubic-bezier(0.4, 0, 0.2, 1);
        }

        .gauge-center {
            position: absolute;
            bottom: 0;
            left: 50%;
            transform: translateX(-50%);
            text-align: center;
        }

        .gauge-score {
            font-size: 2rem;
            font-weight: 800;
            color: var(--text-primary);
            line-height: 1;
        }

        .gauge-label {
            font-size: 0.8rem;
            color: var(--text-secondary);
            text-transform: uppercase;
            letter-spacing: 1px;
        }

        .dyn-bar-track {
            width: 100%;
            height: 24px;
            background: var(--surface-input);
            border-radius: var(--radius-full);
            overflow: hidden;
            border: 1px solid var(--border-subtle);
            margin-top: 0.5rem;
        }

        .dyn-bar-fill {
            height: 100%;
            width: 0%;
            background: linear-gradient(90deg, #34D399, #059669);
            border-radius: var(--radius-full);
            transition: width 1.5s ease-out;
        }

        .graph-container {
            display: flex;
            align-items: flex-end;
            gap: 8px;
            height: 180px;
            padding-bottom: 10px;
            border-bottom: 1px solid var(--border-subtle);
            margin-top: 1rem;
        }

        .graph-bar-wrapper {
            flex: 1;
            display: flex;
            flex-direction: column;
            align-items: center;
            gap: 5px;
            height: 100%;
            justify-content: flex-end;
        }

        .graph-bar {
            width: 100%;
            background: var(--btn-secondary);
            border-radius: 4px 4px 0 0;
            height: 0%;
            transition: height 1s ease-out;
        }

        .yearly-graph-container {
            display: flex;
            align-items: flex-end;
            gap: 2px;
            height: 180px;
            border-bottom: 1px solid var(--border-subtle);
            padding-bottom: 5px;
            margin-top: 1rem;
        }

        .yearly-bar {
            flex: 1;
            background: var(--btn-primary);
            border-radius: 2px 2px 0 0;
            min-width: 4px;
            opacity: 0.8;
            height: 0%;
            transition: height 1.5s ease-out;
        }

        /* EMAI Widget & Cloud */
        .emai-widget-container {
            position: fixed;
            bottom: 20px;
            right: 20px;
            z-index: 9999;
            display: none;
            flex-direction: column;
            align-items: flex-end;
            gap: 15px;
        }

        .emai-cloud {
            background: #FFFFFF;
            color: #04241F;
            padding: 10px 15px;
            border-radius: 15px;
            font-size: 0.85rem;
            font-weight: 800;
            box-shadow: 0 4px 15px rgba(0, 0, 0, 0.4);
            animation: float 3s infinite ease-in-out;
            position: relative;
        }

        .emai-cloud::after {
            content: '';
            position: absolute;
            bottom: -8px;
            right: 20px;
            border-width: 8px 8px 0;
            border-style: solid;
            border-color: #FFFFFF transparent transparent transparent;
        }

        @keyframes float {

            0%,
            100% {
                transform: translateY(0);
            }

            50% {
                transform: translateY(-8px);
            }
        }

        .emai-box {
            width: 55px;
            height: 55px;
            background: var(--btn-primary);
            border-radius: 12px;
            display: flex;
            justify-content: center;
            align-items: center;
            gap: 8px;
            cursor: pointer;
            box-shadow: 0 4px 15px rgba(0, 0, 0, 0.4);
            border: 2px solid #04241F;
        }

        .emai-eye {
            width: 8px;
            height: 18px;
            background: #04241F;
            border-radius: 2px;
            animation: blink 4s infinite;
        }

        @keyframes blink {

            0%,
            96%,
            98%,
            100% {
                height: 18px;
                transform: translateY(0);
            }

            97% {
                height: 2px;
                transform: translateY(8px);
            }
        }

        .emai-chat-panel {
            width: 370px;
            background: var(--surface-card);
            border: 1px solid var(--btn-primary);
            border-radius: var(--radius-lg);
            padding: 1.25rem;
            box-shadow: 0 10px 30px rgba(0, 0, 0, 0.5);
            display: none;
            flex-direction: column;
            gap: 1rem;
            position: absolute;
            bottom: 70px;
            right: 0;
            transform-origin: bottom right;
        }

        .emai-chat-panel.active {
            display: flex;
        }

        .emai-chat-header {
            display: flex;
            justify-content: space-between;
            align-items: center;
            border-bottom: 1px solid var(--border-subtle);
            padding-bottom: 0.5rem;
        }

        .emai-chat-header h4 {
            font-size: 1rem;
            color: var(--text-primary);
            display: flex;
            align-items: center;
            gap: 0.5rem;
        }

        .emai-voice-status {
            font-size: 0.72rem;
            color: var(--btn-secondary);
            font-weight: 600;
        }

        .emai-close {
            background: none;
            border: none;
            color: var(--text-primary);
            cursor: pointer;
            font-size: 1.5rem;
            font-weight: bold;
        }

        .emai-chat-history {
            max-height: 260px;
            overflow-y: auto;
            display: flex;
            flex-direction: column;
            gap: 0.75rem;
            padding-right: 5px;
            scroll-behavior: smooth;
        }

        .emai-input-area {
            display: flex;
            gap: 0.4rem;
            border-top: 1px solid var(--border-subtle);
            padding-top: 0.85rem;
            align-items: center;
        }

        .emai-input-area input {
            flex: 1;
            background-color: var(--surface-input) !important;
            border: 1px solid var(--border-subtle);
            border-radius: var(--radius-sm);
            padding: 0.75rem;
            color: var(--text-primary) !important;
            outline: none;
            font-size: 0.9rem;
        }

        .emai-input-area button {
            background: var(--btn-primary);
            border: none;
            padding: 0.75rem 1rem;
            border-radius: var(--radius-sm);
            color: #04241F;
            font-weight: bold;
            cursor: pointer;
        }

        .btn-emai-voice {
            background: var(--surface-alt) !important;
            color: var(--btn-secondary) !important;
            border: 1px solid var(--btn-secondary) !important;
            padding: 0.75rem 0.85rem !important;
            border-radius: var(--radius-sm);
            display: flex;
            align-items: center;
            justify-content: center;
            cursor: pointer;
        }

        .btn-emai-voice.listening {
            background: var(--alert-emergency) !important;
            border-color: var(--alert-emergency) !important;
            color: white !important;
            animation: pulse-voice 1.5s infinite;
        }

        /* Admin Diagnostic Styles */
        .admin-kpi-grid {
            display: grid;
            grid-template-columns: repeat(4, 1fr);
            gap: 1.25rem;
            margin-top: 0.5rem;
        }

        .admin-kpi-card {
            background: var(--surface-card);
            border: 1px solid var(--border-subtle);
            border-radius: var(--radius-md);
            padding: 1.25rem 1.4rem;
            display: flex;
            align-items: center;
            gap: 1.1rem;
            box-shadow: var(--shadow-card);
        }

        .admin-kpi-icon {
            width: 48px;
            height: 48px;
            border-radius: 12px;
            display: flex;
            align-items: center;
            justify-content: center;
            font-size: 1.4rem;
            flex-shrink: 0;
        }

        .admin-kpi-val {
            font-size: 1.85rem;
            font-weight: 800;
            color: var(--text-primary);
            line-height: 1.1;
        }

        .admin-kpi-label {
            font-size: 0.8rem;
            color: var(--text-muted);
            text-transform: uppercase;
            font-weight: 700;
            margin-top: 0.2rem;
        }

        .admin-kpi-sub {
            font-size: 0.72rem;
            color: var(--text-dim);
            margin-top: 0.2rem;
        }

        .table-toolbar {
            display: flex;
            align-items: center;
            justify-content: space-between;
            gap: 1rem;
            flex-wrap: wrap;
            padding: 0.4rem 0;
        }

        .table-search-box {
            display: flex;
            align-items: center;
            background: var(--surface-input);
            border: 1px solid var(--border-subtle);
            border-radius: var(--radius-sm);
            padding: 0.55rem 0.9rem;
            gap: 0.6rem;
            flex: 1;
            max-width: 380px;
        }

        .table-search-box svg {
            width: 16px;
            height: 16px;
            color: var(--text-dim);
        }

        .table-search-box input {
            background: transparent;
            border: none;
            outline: none;
            color: var(--text-primary);
            font-size: 0.88rem;
            width: 100%;
        }

        .table-filter-chips {
            display: flex;
            gap: 0.5rem;
            flex-wrap: wrap;
        }

        .filter-chip {
            background: var(--surface-input);
            border: 1px solid var(--border-subtle);
            color: var(--text-secondary);
            padding: 0.45rem 0.85rem;
            border-radius: var(--radius-sm);
            font-size: 0.8rem;
            font-weight: 600;
            cursor: pointer;
        }

        .filter-chip.active,
        .filter-chip:hover {
            background: var(--btn-primary);
            color: #04241F;
            border-color: var(--btn-primary);
        }

        .admin-action-matrix {
            display: grid;
            grid-template-columns: repeat(2, 1fr);
            gap: 1rem;
        }

        .admin-action-btn {
            background: var(--surface-input);
            border: 1px solid var(--border-subtle);
            border-radius: var(--radius-md);
            padding: 1.1rem;
            color: var(--text-primary);
            display: flex;
            flex-direction: column;
            gap: 0.4rem;
            cursor: pointer;
            text-align: left;
        }

        .admin-action-title {
            font-size: 0.95rem;
            font-weight: 700;
            display: flex;
            align-items: center;
            gap: 0.5rem;
            color: var(--text-primary);
        }

        .admin-action-desc {
            font-size: 0.78rem;
            color: var(--text-dim);
            line-height: 1.35;
        }

        .stats-grid {
            display: grid;
            grid-template-columns: repeat(4, 1fr);
            gap: 1rem;
            margin-bottom: 1.25rem;
        }

        .stat-card {
            background: var(--surface-input);
            border: 1px solid var(--border-subtle);
            border-radius: var(--radius-sm);
            padding: 1rem;
            text-align: center;
        }

        .stat-value {
            font-size: 1.6rem;
            font-weight: 800;
            color: var(--text-primary);
        }

        .stat-label {
            font-size: 0.78rem;
            color: var(--text-dim);
            text-transform: uppercase;
            margin-top: 0.25rem;
        }

        .stat-card.stat-high .stat-value {
            color: var(--alert-emergency);
        }

        .stat-card.stat-moderate .stat-value {
            color: var(--alert-important);
        }

        .stat-card.stat-low .stat-value {
            color: var(--btn-primary);
        }

        .stat-card.stat-pending .stat-value {
            color: #38BDF8;
        }

        .filter-row {
            display: flex;
            gap: 0.5rem;
            margin-bottom: 1rem;
            flex-wrap: wrap;
        }

        .filter-btn {
            background: var(--surface-input);
            border: 1px solid var(--border-subtle);
            color: var(--text-secondary);
            padding: 0.4rem 0.9rem;
            border-radius: var(--radius-sm);
            font-size: 0.8rem;
            cursor: pointer;
            font-weight: 600;
        }

        .filter-btn.active,
        .filter-btn:hover {
            background: var(--btn-primary);
            color: #04241F;
        }

        .table-responsive {
            overflow-x: auto;
            width: 100%;
            border: 1px solid var(--border-subtle);
            border-radius: 12px;
            background: var(--surface-alt);
        }

        table.admin-table {
            width: 100%;
            border-collapse: collapse;
            font-size: 0.9rem;
            white-space: nowrap;
            min-width: 800px;
        }

        table.admin-table th,
        table.admin-table td {
            text-align: left;
            padding: 12px;
            border-bottom: 1px solid var(--border-subtle);
        }

        table.admin-table th {
            color: var(--text-muted);
            text-transform: uppercase;
            font-size: 0.8rem;
            background: rgba(0, 0, 0, 0.2);
        }

        table.submissions {
            width: 100%;
            border-collapse: collapse;
            font-size: 0.88rem;
            min-width: 600px;
        }

        table.submissions th,
        table.submissions td {
            padding: 10px 14px;
            border-bottom: 1px solid var(--border-subtle);
            text-align: left;
        }

        table.submissions th {
            background: rgba(0, 0, 0, 0.3);
            color: var(--text-muted);
            font-size: 0.76rem;
            text-transform: uppercase;
        }

        .level-pill {
            padding: 0.25rem 0.65rem;
            border-radius: var(--radius-full);
            font-weight: 700;
            font-size: 0.75rem;
        }

        .level-low {
            background: rgba(16, 185, 129, 0.15);
            color: #6EE7B7;
            border: 1px solid rgba(16, 185, 129, 0.3);
        }

        .level-moderate {
            background: rgba(245, 158, 11, 0.15);
            color: #FCD34D;
            border: 1px solid rgba(245, 158, 11, 0.3);
        }

        .level-high {
            background: rgba(239, 68, 68, 0.2);
            color: #FCA5A5;
            border: 1px solid rgba(239, 68, 68, 0.4);
        }

        .flag {
            background: rgba(56, 189, 248, 0.15);
            color: #7DD3FC;
            border: 1px solid rgba(56, 189, 248, 0.3);
            padding: 0.2rem 0.55rem;
            border-radius: 4px;
            font-size: 0.75rem;
        }

        .toggle-detail {
            background: transparent;
            border: 1px solid var(--btn-secondary);
            color: var(--btn-secondary);
            padding: 0.3rem 0.65rem;
            border-radius: 6px;
            font-size: 0.75rem;
            cursor: pointer;
        }

        .detail-row {
            display: none;
            background: rgba(0, 0, 0, 0.25);
        }

        .detail-row.show {
            display: table-row;
        }

        /* General UI components */
        .editable-form {
            display: grid;
            grid-template-columns: 1fr 1fr;
            gap: 1.5rem;
        }

        .officer-locked-input {
            background: rgba(15, 23, 42, 0.6) !important;
            border: 1px dashed rgba(148, 163, 184, 0.3) !important;
            color: #94A3B8 !important;
            cursor: not-allowed !important;
        }

        .full-width {
            grid-column: 1 / -1;
        }

        .btn-edit-save {
            padding: 0.8rem 1.5rem;
            background: var(--btn-primary);
            color: #04241F;
            border: none;
            border-radius: var(--radius-sm);
            font-weight: 700;
            cursor: pointer;
        }

        .btn-g-primary {
            background: var(--btn-primary);
            color: #04241F;
            padding: 0.8rem 2rem;
            border-radius: var(--radius-full);
            font-weight: 700;
            border: none;
            cursor: pointer;
        }

        .btn-g-secondary {
            background: transparent;
            color: var(--text-secondary);
            border: 1px solid var(--border-subtle);
            padding: 0.8rem 2rem;
            border-radius: var(--radius-full);
            font-weight: 600;
            cursor: pointer;
        }

        .qa-list {
            display: flex;
            flex-direction: column;
            gap: 1.5rem;
        }

        .qa-item {
            background: var(--surface-alt);
            border-left: 3px solid var(--btn-secondary);
            padding: 1.25rem;
            border-radius: 0 var(--radius-sm) var(--radius-sm) 0;
        }

        .task-list {
            display: flex;
            flex-direction: column;
            gap: 0.75rem;
            width: 100%;
        }

        .task-item {
            display: flex;
            align-items: center;
            gap: 1rem;
            padding: 0.85rem 1rem;
            background: var(--surface-alt);
            border: 1px solid var(--border-subtle);
            border-radius: var(--radius-sm);
            cursor: pointer;
            width: 100%;
            text-align: left;
        }

        .diary-entry-list {
            display: flex;
            flex-direction: column;
            gap: 1rem;
            margin-top: 1.5rem;
        }

        .diary-entry-card {
            background: rgba(255, 255, 255, 0.02);
            border-left: 3px solid var(--btn-primary);
            padding: 1rem;
            border-radius: 0 var(--radius-sm) var(--radius-sm) 0;
        }

        .consultant-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
            gap: 1.5rem;
        }

        .consultant-card {
            background: var(--surface-alt);
            border: 1px solid var(--border-subtle);
            border-radius: var(--radius-md);
            padding: 1.5rem;
            display: flex;
            align-items: center;
            gap: 1rem;
        }

        .btn-chat-now {
            background: var(--surface-alt);
            color: var(--btn-secondary);
            border: 1px solid var(--btn-secondary);
            padding: 0.4rem 0.8rem;
            border-radius: 8px;
            font-size: 0.8rem;
            font-weight: 600;
            cursor: pointer;
        }

        .custom-modal-container {
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background: rgba(0, 0, 0, 0.85);
            z-index: 20000;
            display: none;
            justify-content: center;
            align-items: center;
            padding: 2rem 1rem;
        }

        .custom-modal-container.active {
            display: flex;
        }

        .custom-modal {
            background: var(--surface-card);
            border: 1px solid var(--btn-primary);
            border-radius: var(--radius-lg);
            width: 100%;
            max-width: 550px;
            padding: 2.5rem;
            text-align: center;
            position: relative;
        }

        .emergency-modal {
            background: #450A0A;
            border: 2px solid #EF4444;
            border-radius: var(--radius-lg);
            width: 100%;
            max-width: 600px;
            padding: 3rem;
            text-align: center;
            color: white;
        }

        .admin-sos-banner {
            background: #dc2626;
            color: white;
            padding: 1rem 2rem;
            display: none;
            justify-content: space-between;
            align-items: center;
            font-weight: bold;
            position: sticky;
            top: 70px;
            z-index: 99;
        }

        /* RE-STYLED QUIET CHECK-IN MODAL THEME */
        .checkin-shell {
            background: var(--surface-card);
            border: 1px solid var(--border-subtle);
            border-radius: var(--radius-lg);
            width: 100%;
            max-width: 600px;
            overflow: hidden;
            box-shadow: var(--shadow-card);
            color: var(--text-primary);
        }

        .checkin-top-bar {
            display: flex;
            justify-content: space-between;
            align-items: center;
            padding: 1rem 1.5rem;
            border-bottom: 1px solid var(--border-subtle);
            background: rgba(0, 0, 0, 0.2);
        }

        .checkin-brand {
            font-weight: 700;
            color: var(--btn-primary);
        }

        .checkin-help-link {
            background: none;
            border: none;
            color: var(--text-muted);
            cursor: pointer;
            text-decoration: underline;
            font-size: 0.85rem;
        }

        .checkin-help-panel {
            display: none;
            padding: 1rem 1.5rem;
            background: rgba(248, 113, 113, 0.1);
            border-bottom: 1px solid rgba(248, 113, 113, 0.3);
            font-size: 0.85rem;
        }

        .checkin-help-panel.open {
            display: block;
        }

        .checkin-card {
            padding: 1.5rem;
            text-align: center;
        }

        /* Shrunk padding */
        .checkin-card h1 {
            margin-bottom: 1rem;
            font-size: 1.5rem;
            color: var(--text-primary);
        }

        .checkin-card .lead {
            color: var(--text-secondary);
            margin-bottom: 1.5rem;
        }

        .checkin-start-btn {
            background: var(--btn-primary);
            color: #04241F;
            border: none;
            padding: 0.8rem 2rem;
            border-radius: var(--radius-full);
            font-weight: 700;
            cursor: pointer;
            transition: 0.2s;
        }

        .checkin-start-btn:hover {
            background: var(--btn-primary-hover);
        }

        .checkin-step-label {
            font-size: 0.8rem;
            color: var(--text-dim);
            text-transform: uppercase;
            margin-bottom: 0.5rem;
        }

        .checkin-progress-track {
            background: var(--surface-input);
            height: 6px;
            border-radius: 3px;
            overflow: hidden;
            margin-bottom: 1.5rem;
        }

        .checkin-progress-fill {
            background: var(--btn-primary);
            height: 100%;
            transition: width 0.3s ease;
        }

        .checkin-question-text {
            font-size: 1.25rem;
            font-weight: 600;
            margin-bottom: 1.5rem;
            color: var(--text-primary);
        }

        .checkin-options {
            display: flex;
            flex-direction: column;
            gap: 0.5rem;
            margin-bottom: 1.5rem;
            text-align: left;
        }

        .checkin-option {
            background: var(--surface-input);
            border: 1px solid var(--border-subtle);
            padding: 1rem;
            border-radius: var(--radius-sm);
            cursor: pointer;
            display: flex;
            align-items: center;
            gap: 1rem;
            transition: 0.2s;
        }

        .checkin-option:hover {
            border-color: var(--btn-primary);
        }

        .checkin-option.selected {
            background: rgba(16, 185, 129, 0.15);
            border-color: var(--btn-primary);
        }

        .checkin-option .dot {
            width: 16px;
            height: 16px;
            border-radius: 50%;
            border: 2px solid var(--text-dim);
        }

        .checkin-option.selected .dot {
            border-color: var(--btn-primary);
            background: var(--btn-primary);
        }

        .checkin-nav-row {
            display: flex;
            justify-content: space-between;
            gap: 1rem;
        }

        .checkin-nav {
            flex: 1;
            padding: 0.8rem;
            border-radius: var(--radius-sm);
            font-weight: 600;
            cursor: pointer;
        }

        .checkin-btn-ghost {
            background: transparent;
            border: 1px solid var(--border-subtle);
            color: var(--text-secondary);
        }

        .checkin-btn-ghost:disabled {
            opacity: 0.5;
            cursor: not-allowed;
        }

        .checkin-btn-primary {
            background: var(--btn-primary);
            border: none;
            color: #04241F;
        }

        .checkin-btn-primary:disabled {
            opacity: 0.5;
            cursor: not-allowed;
        }

        .checkin-final-icon {
            font-size: 3rem;
            margin-bottom: 1rem;
        }

        /* Modals form fields inside Register Case */
        .form-input {
            background-color: var(--surface-input) !important;
            color: var(--text-primary) !important;
            border: 1px solid var(--border-subtle);
            border-radius: var(--radius-sm);
            padding: 0.9rem;
            width: 100%;
            outline: none;
        }
    </style>
</head>

<body class="login-active">

    <div class="ambient-orb orb-1"></div>
    <div class="ambient-orb orb-2"></div>

    <!-- CAMOUFLAGE / INCOGNITO STEALTH COVER SCREEN -->
    <div id="camouflage-screen">
        <div style="max-width: 800px; margin: 0 auto;">
            <div
                style="display:flex; justify-content:space-between; align-items:center; border-bottom: 1px solid #cbd5e1; padding-bottom: 1rem; margin-bottom: 2rem;">
                <h2 style="font-family:serif; font-size:1.6rem; color:#0f172a;">Open Learning: Fundamentals of
                    Environmental Science</h2>
                <button onclick="toggleCamouflage(false)"
                    style="background:#0284c7; color:white; border:none; padding:6px 14px; border-radius:6px; font-family:sans-serif; cursor:pointer;">Return
                    to App</button>
            </div>
            <p style="font-size:1.1rem; line-height:1.8; color:#334155; margin-bottom:1.5rem;">
                <strong>Chapter 4: Ecological Succession in Temperate Biomes</strong><br>
                Ecological succession describes the progressive replacement of one biological community by another over
                time. Beginning with primary pioneer species such as lichens and bryophytes, substrate stabilization
                permits vascular colonization...
            </p>
            <p style="font-size:0.95rem; color:#64748b;">[Open educational resource. Press Esc or click Return to App to
                resume your secure session.]</p>
        </div>
    </div>

    <!-- ONBOARDING TOUR MODAL -->
    <div class="custom-modal-container" id="onboarding-tour-modal">
        <div class="custom-modal"
            style="background: var(--surface-card); border-color: var(--btn-primary); text-align: left;">
            <h3 style="color: var(--text-primary); margin-bottom: 1rem;">🚀 Welcome to MediCore Tour</h3>
            <p style="color: var(--text-secondary); font-size: 0.92rem; line-height: 1.6; margin-bottom: 1rem;">
                Here are the key features to test during your hackathon review:
            </p>
            <ul
                style="margin-left: 1.2rem; color: var(--text-muted); font-size: 0.88rem; line-height: 1.6; display: flex; flex-direction: column; gap: 6px;">
                <li><strong>Duress Decoy PIN:</strong> Enter password <code>0000</code> to trigger a stealth grocery
                    decoy while quietly alerting officers.</li>
                <li><strong>Live Judge Demo:</strong> Click the top blue button to simulate live geo-fence breaches and
                    multi-modal sensor fusion.</li>
                <li><strong>Universal Back Buttons:</strong> Available on every sub-page to prevent navigational
                    dead-ends.</li>
                <li><strong>AI Companion EMAI:</strong> Talk or type safely using zero-probing conversational
                    guardrails.</li>
            </ul>
            <button class="btn-login-submit" style="margin-top: 1.5rem; width: 100%;"
                onclick="document.getElementById('onboarding-tour-modal').classList.remove('active')">Got It, Let's
                Begin</button>
        </div>
    </div>

    <!-- REGISTER CASE MODAL (Triggered by Admin/Officer) -->
    <div class="custom-modal-container" id="register-case-modal">
        <div class="custom-modal" style="text-align: left; max-width: 600px;">
            <h3 style="color: var(--text-primary); margin-bottom: 1rem;">➕ Register New Case</h3>
            <form id="new-case-form" class="editable-form" onsubmit="submitNewCase(event)"
                style="display:flex; flex-direction:column; gap:1.2rem;">
                <div class="form-group full-width"><label class="form-label" style="color:var(--text-secondary);">Victim
                        Name</label><input type="text" class="form-input" id="nc-name" required></div>
                <div class="form-group">
                    <label class="form-label" style="color:var(--text-secondary);">Case Type</label>
                    <select class="form-input" id="nc-type" required>
                        <option value="Rape">Rape</option>
                        <option value="Theft">Theft</option>
                        <option value="Murder">Murder</option>
                        <option value="Assault">Assault</option>
                    </select>
                </div>
                <div class="form-group">
                    <label class="form-label" style="color:var(--text-secondary);">Priority</label>
                    <select class="form-input" id="nc-priority" required>
                        <option value="High">High</option>
                        <option value="Medium">Medium</option>
                        <option value="Low">Low</option>
                    </select>
                </div>
                <div class="form-group full-width"><label class="form-label"
                        style="color:var(--text-secondary);">Incident Details</label><textarea class="form-input"
                        id="nc-details" rows="3" required></textarea></div>
                <div class="full-width" style="display:flex; justify-content:flex-end; gap:10px; margin-top:1rem;">
                    <button type="button" class="btn-g-secondary"
                        onclick="document.getElementById('register-case-modal').classList.remove('active')">Cancel</button>
                    <button type="submit" class="btn-g-primary">Submit</button>
                </div>
            </form>
        </div>
    </div>

    <!-- ==========================================
         SCREEN 1: LOGIN
         ========================================== -->
    <main class="app-screen active" id="screen-login">

        <div class="language-switcher-wrapper" id="login-language-picker">
            <svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2">
                <circle cx="12" cy="12" r="10"></circle>
                <line x1="2" y1="12" x2="22" y2="12"></line>
                <path d="M12 2a15.3 15.3 0 0 1 4 10 15.3 15.3 0 0 1-4 10 15.3 15.3 0 0 1 4-10z"></path>
            </svg>
            <select class="language-select" id="site-lang-select" onchange="changeLanguage(this.value)">
                <option value="en">English</option>
                <option value="hi">हिन्दी (Hindi)</option>
                <option value="or">ଓଡ଼ିଆ (Odia)</option>
                <option value="ml">മലയാളം (Malayalam)</option>
                <option value="te">తెలుగు (Telugu)</option>
                <option value="ta">தமிழ் (Tamil)</option>
                <option value="ur">اردو (Urdu)</option>
                <option value="mr">मराठी (Marathi)</option>
                <option value="bn">বাংলা (Bengali)</option>
            </select>
        </div>

        <div class="login-container">
            <header class="login-brand-header">
                <div class="brand-badge">
                    <span class="status-dot"></span>
                    <span data-i18n="badgeGateway">MediCore Safe Gateway</span>
                </div>
                <h1 data-i18n="welcomeTitle">Welcome!</h1>
                <p data-i18n="welcomeSubtitle">Select your portal access below.</p>
                <!-- Tour Launcher -->
                <button class="btn-tour" style="margin-top: 10px;"
                    onclick="document.getElementById('onboarding-tour-modal').classList.add('active')">🚀 Start Guided
                    Tour</button>
            </header>

            <div class="login-card">
                <div class="login-tabs">
                    <button class="login-tab-btn active" id="tab-patient-login" onclick="switchLoginTab('patient')"
                        data-i18n="tabPatient">Login</button>
                    <button class="login-tab-btn" id="tab-admin-login" onclick="switchLoginTab('admin')"
                        data-i18n="tabAdmin">Admin Officer</button>
                </div>

                <div class="login-error-banner" id="login-error-box"><span id="login-error-message"></span></div>

                <!-- PATIENT FORM -->
                <form class="login-form active" id="form-patient" onsubmit="handleUnifiedLogin(event, 'kanika')">
                    <div class="form-group">
                        <label class="form-label"><span data-i18n="labelPatientId">User ID</span></label>
                        <div class="input-box">
                            <svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2">
                                <path d="M20 21v-2a4 4 0 0 0-4-4H8a4 4 0 0 0-4 4v2"></path>
                                <circle cx="12" cy="7" r="4"></circle>
                            </svg>
                            <input type="text" id="login-user-patient" placeholder="e.g. KANIKA"
                                data-i18n-placeholder="phPatientId" required>
                        </div>
                    </div>

                    <div class="otp-toggle" style="margin-top:0.5rem;">
                        <div class="otp-btn active" id="btn-auth-pass" onclick="toggleAuthType('pass')"
                            data-i18n="btnPassword">Password / Duress PIN</div>
                        <div class="otp-btn" id="btn-auth-otp" onclick="toggleAuthType('otp')" data-i18n="btnOtp">Send
                            OTP SMS</div>
                    </div>

                    <div class="form-group" id="input-group-pass">
                        <div class="input-box">
                            <svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2">
                                <rect x="3" y="11" width="18" height="11" rx="2" ry="2"></rect>
                                <path d="M7 11V7a5 5 0 0 1 10 0v4"></path>
                            </svg>
                            <input type="password" id="login-pass-patient"
                                placeholder="•••••••• (Hint: 1234567 | Decoy PIN: 0000)"
                                data-i18n-placeholder="phPassword">
                        </div>
                    </div>
                    <div class="form-group" id="input-group-otp" style="display:none;">
                        <div class="input-box">
                            <svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2">
                                <path d="M12 22s8-4 8-10V5l-8-3-8 3v7c0 6 8 10 8 10z"></path>
                            </svg>
                            <input type="text" id="login-otp-patient" placeholder="Enter 6-digit OTP (Any number)"
                                data-i18n-placeholder="phOtp">
                        </div>
                    </div>
                    <button type="submit" class="btn-login-submit"><span data-i18n="btnSignIn">Sign In
                            Securely</span></button>
                </form>

                <!-- ADMIN FORM -->
                <form class="login-form" id="form-admin" onsubmit="handleUnifiedLogin(event, 'admin')">
                    <div class="form-group">
                        <label class="form-label"><span data-i18n="labelOfficerId">Officer ID</span></label>
                        <div class="input-box">
                            <svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2">
                                <rect x="3" y="4" width="18" height="18" rx="2" ry="2"></rect>
                                <line x1="16" y1="2" x2="16" y2="6"></line>
                                <line x1="8" y1="2" x2="8" y2="6"></line>
                                <line x1="3" y1="10" x2="21" y2="10"></line>
                            </svg>
                            <input type="text" id="login-user-admin" placeholder="RICHARD, MINAKSHI, or TANMAY"
                                data-i18n-placeholder="phOfficerId" required>
                        </div>
                    </div>
                    <div class="form-group">
                        <label class="form-label">
                            <span data-i18n="labelAuthCode">Unique Auth Code</span>
                            <a href="#" style="color: var(--text-secondary); font-size: 0.78rem;"
                                onclick="alert('Admin Protocol: Contact jurisdiction command for recovery.')"
                                data-i18n="forgotCode">Forgot Code?</a>
                        </label>
                        <div class="input-box">
                            <svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2">
                                <path
                                    d="M21 2l-2 2m-7.61 7.61a5.5 5.5 0 1 1-7.778 7.778 5.5 5.5 0 0 1 7.777-7.777zm0 0L15.5 7.5m0 0l3 3L22 7l-3-3m-3.5 3.5L19 4">
                                </path>
                            </svg>
                            <input type="password" id="login-pass-admin" placeholder="•••••••• (Hint: 1234567)"
                                data-i18n-placeholder="phPassword" required>
                        </div>
                    </div>
                    <button type="submit" class="btn-login-submit"><span data-i18n="btnAccessAdmin">Access Admin
                            Console</span></button>
                </form>
            </div>
        </div>
    </main>

    <!-- ==========================================
         SCREEN 2: DASHBOARDS
         ========================================== -->
    <main class="app-screen" id="screen-dashboard">

        <!-- Real-Time Telemetry Ticker Banner -->
        <div class="telemetry-ticker-bar">
            <div class="ticker-pulsar"></div>
            <span id="live-telemetry-ticker-text">SYSTEM MISSION CONTROL: All safe perimeters secure. Multi-modal sensor
                fusion nominal.</span>
        </div>

        <div class="sidebar-overlay" id="sidebar-overlay" onclick="toggleSidebar()"></div>

        <!-- Sidebar -->
        <aside class="patient-sidebar" id="patient-sidebar">
            <button class="sidebar-close" onclick="toggleSidebar()">✕</button>
            <nav class="sidebar-nav">
                <button class="tab-link active" id="btn-nav-home" onclick="switchPatientTab('home', this)"><svg
                        width="20" height="20" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2">
                        <path d="M3 9l9-7 9 7v11a2 2 0 0 1-2 2H5a2 2 0 0 1-2-2z"></path>
                    </svg> <span data-i18n="navHome">Home</span></button>
                <button class="tab-link" onclick="switchPatientTab('activity', this)"><svg width="20" height="20"
                        viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2">
                        <polyline points="22 12 18 12 15 21 9 3 6 12 2 12"></polyline>
                    </svg> <span data-i18n="navActivity">Daily Activity</span></button>
                <button class="tab-link" id="btn-nav-qa" onclick="switchPatientTab('qa', this)"><svg width="20"
                        height="20" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2">
                        <path
                            d="M21 11.5a8.38 8.38 0 0 1-.9 3.8 8.5 8.5 0 0 1-7.6 4.7 8.38 8.38 0 0 1-3.8-.9L3 21l1.9-5.7a8.38 8.38 0 0 1-.9-3.8 8.5 8.5 0 0 1 4.7-7.6 8.38 8.38 0 0 1 3.8-.9h.5a8.48 8.48 0 0 1 8 8v.5z">
                        </path>
                    </svg> <span data-i18n="navQA">Today's Q&A</span></button>
                <button class="tab-link" onclick="switchPatientTab('diary', this)"><svg width="20" height="20"
                        viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2">
                        <path d="M4 19.5A2.5 2.5 0 0 1 6.5 17H20"></path>
                        <path d="M6.5 2H20v20H6.5A2.5 2.5 0 0 1 4 19.5v-15A2.5 2.5 0 0 1 6.5 2z"></path>
                    </svg> <span data-i18n="navDiary">My Diary</span></button>
                <button class="tab-link" id="btn-nav-performance" onclick="switchPatientTab('performance', this)"><svg
                        width="20" height="20" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2">
                        <path d="M2 20h20"></path>
                        <path d="M14 15l4-4 4 4"></path>
                        <path d="M18 15V4"></path>
                    </svg> <span data-i18n="navPerformance">Performance</span></button>
                <button class="tab-link" onclick="switchPatientTab('consultants', this)"><svg width="20" height="20"
                        viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2">
                        <path d="M17 21v-2a4 4 0 0 0-4-4H5a4 4 0 0 0-4 4v2"></path>
                        <circle cx="9" cy="7" r="4"></circle>
                    </svg> <span data-i18n="navTalk">Talk to Someone</span></button>

                <div class="sidebar-nav-bottom">
                    <button class="tab-link" id="btn-nav-personal" onclick="switchPatientTab('personal', this)"><svg
                            width="20" height="20" viewBox="0 0 24 24" fill="none" stroke="currentColor"
                            stroke-width="2">
                            <circle cx="12" cy="12" r="3"></circle>
                            <path
                                d="M19.4 15a1.65 1.65 0 0 0 .33 1.82l.06.06a2 2 0 0 1 0 2.83 2 2 0 0 1-2.83 0l-.06-.06a1.65 1.65 0 0 0-1.82-.33 1.65 1.65 0 0 0-1 1.51V21a2 2 0 0 1-2 2 2 2 0 0 1-2-2v-.09A1.65 1.65 0 0 0 9 19.4a1.65 1.65 0 0 0-1.82.33l-.06.06a2 2 0 0 1-2.83 0 2 2 0 0 1 0-2.83l.06-.06a1.65 1.65 0 0 0 .33-1.82 1.65 1.65 0 0 0-1.51-1H3a2 2 0 0 1-2-2 2 2 0 0 1 2-2h.09A1.65 1.65 0 0 0 4.6 9a1.65 1.65 0 0 0-.33-1.82l-.06-.06a2 2 0 0 1 0-2.83 2 2 0 0 1 2.83 0l.06.06a1.65 1.65 0 0 0 1.82.33H9a1.65 1.65 0 0 0 1-1.51V3a2 2 0 0 1 2-2 2 2 0 0 1 2 2v.09a1.65 1.65 0 0 0 1 1.51 1.65 1.65 0 0 0 1.82-.33l.06-.06a2 2 0 0 1 2.83 0 2 2 0 0 1 0 2.83l-.06-.06a1.65 1.65 0 0 0-.33 1.82V9a1.65 1.65 0 0 0 1.51 1H21a2 2 0 0 1 2 2 2 2 0 0 1-2 2h-.09a1.65 1.65 0 0 0-1.51 1z">
                            </path>
                        </svg> <span data-i18n="navPersonal">Personal Info</span></button>
                </div>
            </nav>
        </aside>

        <!-- Header -->
        <header class="dash-nav">
            <div class="dash-nav-brand">
                <button class="menu-toggle-btn" id="menu-btn" onclick="toggleSidebar()">
                    <svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="3">
                        <line x1="3" y1="12" x2="21" y2="12"></line>
                        <line x1="3" y1="6" x2="21" y2="6"></line>
                        <line x1="3" y1="18" x2="21" y2="18"></line>
                    </svg>
                </button>
                <div class="dash-nav-logo" id="header-logo-icon">MC</div>
                <div class="dash-nav-title">
                    <strong id="header-title-text" data-i18n="headerTitle">MediCore Safe Portal</strong>
                    <span id="header-subtitle-text" data-i18n="headerSubtitle">Operational Suite</span>
                </div>
            </div>

            <div class="dash-nav-actions">
                <!-- Low Bandwidth Resilience Toggle -->
                <button class="btn-stealth-cover" onclick="toggleLowBandwidthMode()"
                    title="Switch to lightweight text-and-audio mode for low connections">📶 Low-Bandwidth Mode</button>
                <!-- Hacker Demo Simulation Button -->
                <button class="btn-demo-sim" onclick="triggerJudgeSimulation()"
                    title="Instantly populate telemetry & breach for judge review">🧪 Live Judge Demo</button>
                <!-- Stealth & Privacy Tools -->
                <button class="btn-stealth-cover" onclick="toggleCamouflage(true)"
                    title="Hide app with neutral study screen">📖 Stealth Mode</button>
                <button class="btn-quick-exit" onclick="executeQuickExit()"
                    title="Press ESC anytime to immediately exit to Google News">⚡ Quick Exit</button>

                <button class="btn-emergency-header" id="btn-patient-emergency" onclick="triggerEmergency()"
                    style="display:none;">🚨 SOS</button>

                <div class="user-status-pill" onclick="openPersonalInfoTab()" title="View Personal Info">
                    <div class="user-avatar" id="header-avatar-badge">K</div>
                    <div class="user-info-text">
                        <div class="user-name-display" id="header-username-display">User</div>
                        <div class="user-role-display" id="header-role-display">Role</div>
                    </div>
                </div>
                <button class="logout-btn" onclick="handleLogout()"><span data-i18n="btnSignOut">Sign
                        Out</span></button>
            </div>
        </header>

        <!-- ADMIN SOS BANNER -->
        <div class="admin-sos-banner" id="admin-sos-banner">
            <div style="display:flex; align-items:center; gap:10px; font-size:1.1rem;">
                <svg width="24" height="24" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2">
                    <path d="M10.29 3.86L1.82 18a2 2 0 0 0 1.71 3h16.94a2 2 0 0 0 1.71-3L13.71 3.86a2 2 0 0 0-3.42 0z">
                    </path>
                    <line x1="12" y1="9" x2="12" y2="13"></line>
                    <line x1="12" y1="17" x2="12.01" y2="17"></line>
                </svg>
                CRITICAL EMERGENCY TRIGGERED
            </div>
            <button
                style="background:white; color:#dc2626; border:none; padding:8px 16px; border-radius:8px; font-weight:bold; cursor:pointer;"
                onclick="openAdminCaseFile('Kanika Jha', '#FIR-2026-993-A', 'Rape')">CLICK TO OPEN CASE FILE</button>
        </div>

        <div class="dash-container" id="dash-main-container">

            <!-- ==========================================
                 SUPERADMIN (ADMINISTRATOR) VIEW 
                 ========================================== -->
            <div id="view-superadmin" style="display: none; flex-direction: column; gap: 2rem;">
                <div><button class="btn-universal-back" onclick="handleLogout()">← Back to Login</button></div>
                <section class="dash-hero" style="background: var(--btn-primary); color: white;">
                    <div class="hero-text" style="flex:1;">
                        <h2 style="color:white;">Welcome back, Administrator Tanmay Singh 🏢</h2>
                        <p style="color:#E2E8F0;">System Oversight & Case Assignment Protocol</p>
                    </div>
                </section>

                <div class="dash-cols-even">
                    <!-- Officer Monitoring -->
                    <section class="dash-section-card">
                        <h3 style="color:var(--btn-primary);">👮 Officer Monitoring</h3>
                        <div style="display:flex; flex-direction:column; gap:1rem;">
                            <div
                                style="padding:1rem; border:1px solid var(--border-subtle); border-radius:var(--radius-sm);">
                                <div style="display:flex; justify-content:space-between; margin-bottom:0.5rem;">
                                    <strong>Officer Richard (ID: #4092)</strong>
                                    <span style="color:var(--btn-primary); font-weight:bold;">Online</span>
                                </div>
                                <div style="font-size:0.85rem; color:var(--text-secondary);">Session Time: 4h 12m</div>
                                <div style="font-size:0.85rem; color:var(--text-secondary);">Cases Handled Today: 4
                                </div>
                                <div style="font-size:0.85rem; color:var(--text-secondary);">Last Action: Reviewed
                                    Dossier (Kanika Jha)</div>
                            </div>
                            <div
                                style="padding:1rem; border:1px solid var(--border-subtle); border-radius:var(--radius-sm);">
                                <div style="display:flex; justify-content:space-between; margin-bottom:0.5rem;">
                                    <strong>Officer Minakshi Verma (ID: #8821)</strong>
                                    <span style="color:var(--text-dim); font-weight:bold;">Away</span>
                                </div>
                                <div style="font-size:0.85rem; color:var(--text-secondary);">Session Time: 2h 45m</div>
                                <div style="font-size:0.85rem; color:var(--text-secondary);">Cases Handled Today: 2
                                </div>
                                <div style="font-size:0.85rem; color:var(--text-secondary);">Last Action: Updated Legal
                                    Logs</div>
                            </div>
                        </div>
                    </section>

                    <!-- Case Assignment Queue -->
                    <section class="dash-section-card">
                        <h3 style="color:var(--btn-primary);">📥 Pending Case Assignments</h3>
                        <p style="font-size:0.85rem; color:var(--text-secondary);">Cases submitted by officers awaiting
                            assignment.</p>
                        <div id="superadmin-pending-cases"
                            style="max-height: 250px; overflow-y:auto; border:1px solid var(--border-subtle); border-radius:var(--radius-sm); padding:0.5rem;">
                            <!-- Populated dynamically via JS -->
                        </div>
                    </section>
                </div>

                <section class="dash-section-card">
                    <h3 style="color:var(--btn-primary);">👥 Global Patient Overview</h3>
                    <div class="table-responsive">
                        <table class="admin-table">
                            <thead>
                                <tr>
                                    <th>Victim Name</th>
                                    <th>Case Type</th>
                                    <th>Priority</th>
                                    <th>Mental Health Risk</th>
                                    <th>Assigned Officer(s)</th>
                                </tr>
                            </thead>
                            <tbody>
                                <tr>
                                    <td>Kanika Jha</td>
                                    <td>Rape</td>
                                    <td>High</td>
                                    <td><span style="color:#ef4444; font-weight:bold;">Critical (92%)</span></td>
                                    <td>Richard, Minakshi Verma</td>
                                </tr>
                                <tr>
                                    <td>Sarah Miller</td>
                                    <td>Assault</td>
                                    <td>High</td>
                                    <td>Moderate (45%)</td>
                                    <td>Richard</td>
                                </tr>
                                <tr>
                                    <td>David Chen</td>
                                    <td>Theft</td>
                                    <td>Medium</td>
                                    <td>Low (12%)</td>
                                    <td>Minakshi Verma</td>
                                </tr>
                                <tr>
                                    <td>Elena Rodriguez</td>
                                    <td>Murder</td>
                                    <td>High</td>
                                    <td>Moderate (58%)</td>
                                    <td>Richard</td>
                                </tr>
                                <tr>
                                    <td>Michael Chang</td>
                                    <td>Theft</td>
                                    <td>Low</td>
                                    <td>Low (8%)</td>
                                    <td>Smith</td>
                                </tr>
                                <tr>
                                    <td>Jessica Taylor</td>
                                    <td>Assault</td>
                                    <td>Medium</td>
                                    <td>Low (19%)</td>
                                    <td>Minakshi Verma</td>
                                </tr>
                                <tr>
                                    <td>Amanda Lewis</td>
                                    <td>Rape</td>
                                    <td>High</td>
                                    <td>Moderate (62%)</td>
                                    <td>Richard</td>
                                </tr>
                                <tr>
                                    <td>James Wilson</td>
                                    <td>Theft</td>
                                    <td>Low</td>
                                    <td>Low (5%)</td>
                                    <td>Smith</td>
                                </tr>
                                <tr>
                                    <td>Oliver Queen</td>
                                    <td>Murder</td>
                                    <td>High</td>
                                    <td>Moderate (41%)</td>
                                    <td>Minakshi Verma</td>
                                </tr>
                                <tr>
                                    <td>Barry Allen</td>
                                    <td>Assault</td>
                                    <td>Medium</td>
                                    <td>Moderate (33%)</td>
                                    <td>Richard</td>
                                </tr>
                            </tbody>
                        </table>
                    </div>
                </section>
            </div>


            <!-- ==========================================
                 OFFICER / ADMIN VIEW 
                 ========================================== -->
            <div id="view-admin" style="display: none; flex-direction: column; gap: 2rem;">
                <div>
                    <button class="btn-universal-back" onclick="handleLogout()">← Back to Login</button>
                </div>
                <section class="dash-hero">
                    <div class="hero-text" style="flex:1;">
                        <h2 data-i18n="adminWelcome" id="admin-welcome-msg">Welcome back, Officer 🛡️</h2>
                        <p data-i18n="adminSub">Case Management Command: Active Cases, Victim Statements, and Legal
                            Audits.</p>
                        <div class="admin-meta-strip">
                            <span class="admin-meta-pill">🏛️ Jurisdiction: Central District</span>
                            <span class="admin-meta-pill"
                                style="color:var(--btn-primary); border-color:var(--btn-primary);">● Command Status:
                                Online & Secure</span>
                            <span class="admin-meta-pill" style="color:#60a5fa; border-color:#3b82f6;">🔒 Zero-Knowledge
                                AES-GCM Vault Active</span>
                        </div>
                    </div>
                </section>

                <div class="admin-kpi-grid">
                    <div class="admin-kpi-card">
                        <div class="admin-kpi-icon" style="background:rgba(59, 130, 246, 0.15); color:#60A5FA;">📁</div>
                        <div>
                            <div class="admin-kpi-val" id="kpi-total-cases">10</div>
                            <div class="admin-kpi-label">Total Cases</div>
                            <div class="admin-kpi-sub">Registered in docket</div>
                        </div>
                    </div>

                    <div class="admin-kpi-card">
                        <div class="admin-kpi-icon" style="background:rgba(239, 68, 68, 0.15); color:#F87171;">🚨</div>
                        <div>
                            <div class="admin-kpi-val" id="kpi-active-cases" style="color:var(--alert-emergency);">2
                            </div>
                            <div class="admin-kpi-label">Active / Safe Room</div>
                            <div class="admin-kpi-sub">High watch & priority</div>
                        </div>
                    </div>

                    <div class="admin-kpi-card">
                        <div class="admin-kpi-icon" style="background:rgba(245, 158, 11, 0.15); color:#FBBF24;">⚖️</div>
                        <div>
                            <div class="admin-kpi-val" id="kpi-trial-cases" style="color:var(--alert-important);">2
                            </div>
                            <div class="admin-kpi-label">Under Court Trial</div>
                            <div class="admin-kpi-sub">Legal filings pending</div>
                        </div>
                    </div>

                    <div class="admin-kpi-card">
                        <div class="admin-kpi-icon" style="background:rgba(16, 185, 129, 0.15); color:#34D399;">✅</div>
                        <div>
                            <div class="admin-kpi-val" id="kpi-resolved-cases" style="color:var(--btn-primary);">6</div>
                            <div class="admin-kpi-label">Discharged / Safe</div>
                            <div class="admin-kpi-sub">Rehabilitated & closed</div>
                        </div>
                    </div>
                </div>

                <!-- PREDICTIVE ENGINE DASHBOARD CARD -->
                <section class="dash-section-card">
                    <div class="section-header">
                        <h3>📈 Dynamic Predictive Engine: Cumulative Trauma Index (CTI) & Decay Curves</h3>
                        <span style="font-size:0.8rem; color:var(--text-dim);">Longitudinal Behavioral Tracking</span>
                    </div>
                    <p style="font-size:0.9rem; color:var(--text-secondary);">Tracking silent decline, anhedonia, and
                        emotional blunting via 30-day Exponential Moving Averages.</p>
                    <div style="position: relative; height: 260px; width: 100%;">
                        <canvas id="officerTraumaChart"></canvas>
                    </div>
                </section>

                <section class="dash-section-card">
                    <div class="section-header">
                        <h3 data-i18n="adminCasesHeader">📁 Registered Victim Cases (10 Total)</h3>
                        <span style="font-size:0.8rem; color:var(--text-dim);" id="admin-table-counter">Showing 10 of 10
                            records</span>
                    </div>

                    <div class="table-toolbar">
                        <div class="table-search-box" style="flex: 1.5; max-width: 380px;">
                            <svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2">
                                <circle cx="11" cy="11" r="8"></circle>
                                <line x1="21" y1="21" x2="16.65" y2="16.65"></line>
                            </svg>
                            <input type="text" id="admin-case-search" placeholder="Search by Victim Name or Case ID..."
                                oninput="filterAdminCases()">
                        </div>

                        <!-- CASE TYPE FILTER DROPDOWN -->
                        <div class="table-search-box" style="flex: 1; max-width: 200px;">
                            <select id="admin-case-type-filter" onchange="filterAdminCases()"
                                style="background: transparent; border: none; outline: none; color: var(--text-primary); font-size: 0.88rem; width: 100%; cursor:pointer;">
                                <option value="all" style="background: #0B1715; color: #ECFDF5;">All Case Types</option>
                                <option value="rape" style="background: #0B1715; color: #ECFDF5;">Rape</option>
                                <option value="theft" style="background: #0B1715; color: #ECFDF5;">Theft</option>
                                <option value="murder" style="background: #0B1715; color: #ECFDF5;">Murder</option>
                                <option value="assault" style="background: #0B1715; color: #ECFDF5;">Assault</option>
                            </select>
                        </div>

                        <div class="table-filter-chips">
                            <button class="filter-chip active" onclick="setCaseFilter('all', this)">All Cases
                                (10)</button>
                            <button class="filter-chip" onclick="setCaseFilter('active', this)">Active (2)</button>
                            <button class="filter-chip" onclick="setCaseFilter('trial', this)">On Trial (2)</button>
                            <button class="filter-chip" onclick="setCaseFilter('completed', this)">Completed
                                (6)</button>
                        </div>
                    </div>

                    <div class="table-responsive">
                        <table class="admin-table" id="admin-cases-table">
                            <thead>
                                <tr>
                                    <th>Case ID</th>
                                    <th>Victim Name</th>
                                    <th>Case Type</th>
                                    <th>Priority</th>
                                    <th>Investigating Officer</th>
                                    <th>Security Status</th>
                                    <th>Actions</th>
                                </tr>
                            </thead>
                            <tbody>
                                <tr data-status="active" data-name="kanika jha" data-id="fir-2026-993-a"
                                    data-type="rape">
                                    <td><strong>#FIR-2026-993-A</strong></td>
                                    <td><strong>Kanika Jha</strong></td>
                                    <td>Rape</td>
                                    <td><span style="color:#ef4444; font-weight:bold;">High</span></td>
                                    <td>Richard, Minakshi</td>
                                    <td><span class="status-badge status-emergency">Active (Safe Room)</span></td>
                                    <td><button class="btn-chat-now"
                                            onclick="openAdminCaseFile('Kanika Jha', '#FIR-2026-993-A', 'Rape')">View
                                            Dossier</button></td>
                                </tr>
                                <tr data-status="active" data-name="sarah miller" data-id="fir-2026-942-b"
                                    data-type="assault">
                                    <td><strong>#FIR-2026-942-B</strong></td>
                                    <td>Sarah Miller</td>
                                    <td>Assault</td>
                                    <td><span style="color:#ef4444; font-weight:bold;">High</span></td>
                                    <td>Richard</td>
                                    <td><span class="status-badge status-emergency">Active</span></td>
                                    <td><button class="btn-chat-now"
                                            onclick="openAdminCaseFile('Sarah Miller', '#FIR-2026-942-B', 'Assault')">View
                                            Dossier</button></td>
                                </tr>
                                <tr data-status="trial" data-name="david chen" data-id="fir-2026-901-c"
                                    data-type="theft">
                                    <td>#FIR-2026-901-C</td>
                                    <td>David Chen</td>
                                    <td>Theft</td>
                                    <td><span style="color:#f59e0b; font-weight:bold;">Medium</span></td>
                                    <td>Minakshi Verma</td>
                                    <td><span class="status-badge status-pending">On Trial</span></td>
                                    <td><button class="btn-chat-now"
                                            onclick="openAdminCaseFile('David Chen', '#FIR-2026-901-C', 'Theft')">View
                                            Dossier</button></td>
                                </tr>
                                <tr data-status="trial" data-name="elena rodriguez" data-id="fir-2026-888-d"
                                    data-type="murder">
                                    <td>#FIR-2026-888-D</td>
                                    <td>Elena Rodriguez</td>
                                    <td>Murder</td>
                                    <td><span style="color:#ef4444; font-weight:bold;">High</span></td>
                                    <td>Richard</td>
                                    <td><span class="status-badge status-pending">On Trial</span></td>
                                    <td><button class="btn-chat-now"
                                            onclick="openAdminCaseFile('Elena Rodriguez', '#FIR-2026-888-D', 'Murder')">View
                                            Dossier</button></td>
                                </tr>
                                <tr data-status="completed" data-name="michael chang" data-id="fir-2026-850-a"
                                    data-type="theft">
                                    <td>#FIR-2026-850-A</td>
                                    <td>Michael Chang</td>
                                    <td>Theft</td>
                                    <td><span style="color:#10b981; font-weight:bold;">Low</span></td>
                                    <td>Smith</td>
                                    <td><span class="status-badge status-success">Completed</span></td>
                                    <td><button class="btn-chat-now"
                                            onclick="openAdminCaseFile('Michael Chang', '#FIR-2026-850-A', 'Theft')">View
                                            Dossier</button></td>
                                </tr>
                                <tr data-status="completed" data-name="jessica taylor" data-id="fir-2026-812-b"
                                    data-type="assault">
                                    <td>#FIR-2026-812-B</td>
                                    <td>Jessica Taylor</td>
                                    <td>Assault</td>
                                    <td><span style="color:#f59e0b; font-weight:bold;">Medium</span></td>
                                    <td>Minakshi Verma</td>
                                    <td><span class="status-badge status-success">Completed</span></td>
                                    <td><button class="btn-chat-now"
                                            onclick="openAdminCaseFile('Jessica Taylor', '#FIR-2026-812-B', 'Assault')">View
                                            Dossier</button></td>
                                </tr>
                                <tr data-status="completed" data-name="amanda lewis" data-id="fir-2026-799-c"
                                    data-type="rape">
                                    <td>#FIR-2026-799-C</td>
                                    <td>Amanda Lewis</td>
                                    <td>Rape</td>
                                    <td><span style="color:#ef4444; font-weight:bold;">High</span></td>
                                    <td>Richard</td>
                                    <td><span class="status-badge status-success">Completed</span></td>
                                    <td><button class="btn-chat-now"
                                            onclick="openAdminCaseFile('Amanda Lewis', '#FIR-2026-799-C', 'Rape')">View
                                            Dossier</button></td>
                                </tr>
                                <tr data-status="completed" data-name="james wilson" data-id="fir-2026-745-a"
                                    data-type="theft">
                                    <td>#FIR-2026-745-A</td>
                                    <td>James Wilson</td>
                                    <td>Theft</td>
                                    <td><span style="color:#10b981; font-weight:bold;">Low</span></td>
                                    <td>Smith</td>
                                    <td><span class="status-badge status-success">Completed</span></td>
                                    <td><button class="btn-chat-now"
                                            onclick="openAdminCaseFile('James Wilson', '#FIR-2026-745-A', 'Theft')">View
                                            Dossier</button></td>
                                </tr>
                                <tr data-status="completed" data-name="oliver queen" data-id="fir-2026-710-b"
                                    data-type="murder">
                                    <td>#FIR-2026-710-B</td>
                                    <td>Oliver Queen</td>
                                    <td>Murder</td>
                                    <td><span style="color:#ef4444; font-weight:bold;">High</span></td>
                                    <td>Minakshi Verma</td>
                                    <td><span class="status-badge status-success">Completed</span></td>
                                    <td><button class="btn-chat-now"
                                            onclick="openAdminCaseFile('Oliver Queen', '#FIR-2026-710-B', 'Murder')">View
                                            Dossier</button></td>
                                </tr>
                                <tr data-status="completed" data-name="barry allen" data-id="fir-2026-680-d"
                                    data-type="assault">
                                    <td>#FIR-2026-680-D</td>
                                    <td>Barry Allen</td>
                                    <td>Assault</td>
                                    <td><span style="color:#f59e0b; font-weight:bold;">Medium</span></td>
                                    <td>Richard</td>
                                    <td><span class="status-badge status-success">Completed</span></td>
                                    <td><button class="btn-chat-now"
                                            onclick="openAdminCaseFile('Barry Allen', '#FIR-2026-680-D', 'Assault')">View
                                            Dossier</button></td>
                                </tr>
                            </tbody>
                        </table>
                    </div>
                </section>

                <div class="dash-cols-even">
                    <section class="dash-section-card">
                        <div class="section-header">
                            <h3 data-i18n="adminMilestonesHeader">🌟 Milestone Verifications</h3>
                            <span class="status-badge status-pending" style="font-size:0.7rem;">1 Pending Proof</span>
                        </div>
                        <div id="admin-milestone-list" style="display:flex; flex-direction:column; gap:10px;">
                            <div
                                style="background:var(--surface-alt); border:1px solid var(--border-subtle); border-radius:var(--radius-sm); padding:1rem; display:flex; justify-content:space-between; align-items:center;">
                                <div>
                                    <strong style="color:var(--text-primary); font-size:0.9rem;">Kanika Jha
                                        (#PT-8842)</strong>
                                    <div style="font-size:0.78rem; color:var(--text-dim); margin-top:2px;">Submitted:
                                        Certificate of Completed Trauma Therapy</div>
                                </div>
                                <div style="display:flex; gap:6px;">
                                    <button class="btn-chat-now"
                                        style="background:var(--btn-primary); color:#04241F; border:none;"
                                        onclick="alert('Proof Approved!')">Approve</button>
                                    <button class="btn-chat-now"
                                        onclick="alert('Document opened in secure sandbox.')">Inspect</button>
                                </div>
                            </div>
                        </div>
                    </section>

                    <section class="dash-section-card">
                        <div class="section-header">
                            <h3 data-i18n="adminQuickActions">⚖️ Quick Actions</h3>
                            <span style="font-size:0.75rem; color:var(--text-dim);">Executive Controls</span>
                        </div>
                        <div class="admin-action-matrix">
                            <button class="admin-action-btn"
                                onclick="document.getElementById('register-case-modal').classList.add('active')">
                                <div class="admin-action-title"><span>➕</span> Register New Case</div>
                                <div class="admin-action-desc">Enroll an incoming protected individual into the
                                    encrypted database.</div>
                            </button>
                            <button class="admin-action-btn"
                                onclick="document.getElementById('admin-case-search').focus()">
                                <div class="admin-action-title"><span>🔍</span> Review Cases</div>
                                <div class="admin-action-desc">Search and audit existing patient case files and
                                    telemetry.</div>
                            </button>
                        </div>
                    </section>
                </div>

                <section class="dash-section-card">
                    <div class="section-header">
                        <h3 data-i18n="adminWellbeing">📊 Today's Wellbeing Check-Ins</h3>
                        <span style="font-size:0.8rem; color:var(--text-dim);">Real-time telemetry reports</span>
                    </div>
                    <div id="admin-checkin-dashboard"></div>
                </section>
            </div>

            <!-- ==========================================
                 PATIENT VIEW 
                 ========================================== -->
            <div id="view-patient" style="display: none; flex-direction: column; gap: 2rem;">

                <!-- TAB 1: HOME -->
                <div id="patient-tab-home" class="patient-tab-content active">
                    <div>
                        <button class="btn-universal-back" onclick="handleLogout()">← Back to Login</button>
                    </div>
                    <section class="dash-hero"
                        style="justify-content: center; text-align: center; border-color: var(--btn-secondary);">
                        <div class="hero-text" style="width: 100%;">
                            <h2 data-i18n="patientHeroTitle">🛡️ SAFE SPACE</h2>
                            <p style="font-size: 1.15rem; margin-top: 0.5rem; color: #5EEAD4; font-weight: 500; font-style: italic;"
                                data-i18n="patientHeroSub">
                                "You are safe here. Take things at your own pace."</p>
                            <!-- Zero-Knowledge Cryptographic Vault Badge -->
                            <div
                                style="margin-top: 1rem; display: inline-block; background: rgba(16, 185, 129, 0.1); border: 1px solid rgba(16, 185, 129, 0.3); padding: 4px 12px; border-radius: 99px; font-size: 0.78rem; color: var(--text-muted);">
                                🔒 Zero-Knowledge Client Vault: Active (AES-GCM Local Encryption)
                            </div>
                        </div>
                    </section>

                    <div class="dash-cols-even">
                        <div style="display:flex; flex-direction:column; gap:2rem;">
                            <section class="dash-section-card"
                                style="background: rgba(20, 184, 166, 0.05); border-left: 4px solid var(--btn-secondary);">
                                <div class="section-header">
                                    <h3 data-i18n="quietCheckinTitle">📝 Today's Quiet Check-In</h3>
                                </div>
                                <p style="color: var(--text-secondary); font-size: 0.95rem; margin-bottom: 1rem;"
                                    data-i18n="quietCheckinDesc">A short, private check-in about how you've been feeling
                                    day to day.</p>
                                <button class="btn-login-submit" onclick="openQuietCheckinModal()"
                                    style="width: fit-content; padding: 0.7rem 1.5rem;" data-i18n="startCheckin">Start
                                    Check-In</button>
                            </section>

                            <section class="dash-section-card">
                                <div class="section-header">
                                    <h3 data-i18n="smallStepsHeader">🌱 5 SMALL STEPS TODAY</h3>
                                </div>
                                <div class="task-list">
                                    <label class="task-item"><input type="checkbox" class="task-checkbox">
                                        <div class="task-content"><span data-i18n="step1">Drink a glass of water</span>
                                        </div>
                                    </label>
                                    <label class="task-item"><input type="checkbox" class="task-checkbox">
                                        <div class="task-content"><span data-i18n="step2">Take a short 5-minute
                                                walk</span></div>
                                    </label>
                                    <label class="task-item"><input type="checkbox" class="task-checkbox">
                                        <div class="task-content"><span data-i18n="step3">Stretch your shoulders &
                                                neck</span></div>
                                    </label>
                                    <label class="task-item"><input type="checkbox" class="task-checkbox">
                                        <div class="task-content"><span data-i18n="step4">Write down one thing you are
                                                grateful for</span></div>
                                    </label>
                                    <label class="task-item"><input type="checkbox" class="task-checkbox">
                                        <div class="task-content"><span data-i18n="step5">Get 15 minutes of fresh
                                                air/sunlight</span></div>
                                    </label>
                                </div>
                            </section>
                        </div>

                        <div style="display:flex; flex-direction:column; gap:2rem;">
                            <section class="dash-section-card">
                                <div class="section-header">
                                    <h3 data-i18n="calmingHeader">🧘 CALMING SPACE</h3>
                                </div>
                                <div class="task-list">
                                    <button class="task-item"
                                        style="border:1px solid var(--border-subtle); width:100%; cursor:pointer; text-align:left; background:var(--surface-alt);"
                                        onclick="openGroundingHub()">
                                        <div class="task-content"><span
                                                style="color:var(--btn-primary); font-weight:700;"
                                                data-i18n="groundingEx">🌱 Grounding Exercises</span></div>
                                    </button>
                                    <button class="task-item"
                                        style="border:1px solid var(--border-subtle); width:100%; cursor:pointer; text-align:left; background:var(--surface-alt);"
                                        onclick="openBreathingModal()">
                                        <div class="task-content"><span
                                                style="color:var(--btn-primary); font-weight:700;"
                                                data-i18n="breathingEx">🌬️ 8-Min Breathing Exercise</span></div>
                                    </button>
                                    <button class="task-item"
                                        style="border:1px solid var(--border-subtle); width:100%; cursor:pointer; text-align:left; background:var(--surface-alt);"
                                        onclick="openAudioModal()">
                                        <div class="task-content"><span
                                                style="color:var(--btn-secondary); font-weight:700;"
                                                data-i18n="audioEx">🎧 Relaxing Audio</span></div>
                                    </button>
                                </div>
                            </section>

                            <section class="dash-section-card">
                                <div class="section-header">
                                    <h3 data-i18n="milestonesHeader">🌟 Big Milestones & Proof</h3>
                                </div>
                                <p style="font-size:0.85rem; color:var(--text-dim); margin-bottom:1rem;"
                                    data-i18n="milestonesSub">Have you achieved a major milestone? Upload a photo or
                                    document as proof for Admin review!</p>
                                <div style="display:flex; flex-direction:column; gap:10px;">
                                    <input type="text" id="milestone-name" class="form-input"
                                        placeholder="E.g., Completed physical therapy"
                                        data-i18n-placeholder="phMilestone">
                                    <input type="file" id="milestone-file" accept="image/*,.pdf"
                                        style="font-size:0.85rem; color:var(--text-secondary);">
                                    <button onclick="submitMilestone()"
                                        style="background:var(--btn-primary); color:#04241F; padding:0.8rem; border:none; border-radius:8px; font-weight:bold; cursor:pointer;"
                                        data-i18n="btnSubmitReview">Submit for Review</button>
                                </div>
                                <div id="milestone-status-list"
                                    style="margin-top:1rem; display:flex; flex-direction:column; gap:5px;"></div>
                            </section>
                        </div>
                    </div>
                </div>

                <!-- TAB 2: DAILY ACTIVITY -->
                <div id="patient-tab-activity" class="patient-tab-content">
                    <div>
                        <button class="btn-universal-back"
                            onclick="switchPatientTab('home', document.getElementById('btn-nav-home'))">← Back to
                            Home</button>
                    </div>
                    <section class="dash-section-card"
                        style="background: rgba(16,185,129,0.05); border-color: var(--btn-primary);">
                        <h3 style="color: var(--btn-primary); margin-bottom: 0.5rem;" data-i18n="messageForYou">A
                            Message For You</h3>
                        <p style="font-size: 1.05rem; line-height: 1.6; color: var(--text-primary);"
                            data-i18n="messageBody">
                            You are doing incredibly well. Taking things one day at a time is a brave and beautiful step
                            forward. We are so proud of your resilience. Remember, healing is not linear, and every
                            small effort you make is a victory. You are safe, you are heard, and your journey matters.
                        </p>
                    </section>
                    <div class="dash-cols-even">
                        <section class="dash-section-card" style="grid-row: span 2;">
                            <div class="section-header">
                                <h3 data-i18n="companionSummary">💬 Companion Summary & Responsiveness</h3>
                            </div>
                            <p style="color:var(--text-secondary); font-size:0.9rem; margin-bottom:1rem;"
                                data-i18n="companionDesc">Your safe responses logged with EMAI are continuously updated
                                in your Q&A section.</p>

                            <div class="gauge-wrapper">
                                <div class="gauge-bg"></div>
                                <div class="gauge-fill" id="activity-gauge-fill"></div>
                                <div class="gauge-center">
                                    <div class="gauge-score" id="activity-gauge-score">0%</div>
                                    <div class="gauge-label" data-i18n="interactionLabel">Interaction</div>
                                </div>
                            </div>
                            <p style="text-align:center; color:var(--btn-primary); font-weight:bold; font-size:0.9rem;"
                                data-i18n="excellentEngagement">Excellent Engagement Today!</p>
                        </section>
                        <section class="dash-section-card">
                            <div class="section-header">
                                <h3 data-i18n="healthScoreHeader">🔋 Positivity & Health Score</h3>
                            </div>
                            <div style="display:flex; justify-content:space-between;"><span
                                    data-i18n="todayLabel">Today</span><strong style="color:var(--btn-primary);">85 /
                                    100</strong></div>
                            <div class="dyn-bar-track">
                                <div class="dyn-bar-fill" id="health-dyn-bar"></div>
                            </div>
                        </section>
                        <section class="dash-section-card">
                            <div class="section-header">
                                <h3 data-i18n="pastWeekHeader">📊 Past Week Analysis</h3>
                            </div>
                            <div class="graph-container" id="weekly-graph-container"></div>
                        </section>
                    </div>
                </div>

                <!-- TAB 3: TODAY'S Q&A -->
                <div id="patient-tab-qa" class="patient-tab-content">
                    <div>
                        <button class="btn-universal-back"
                            onclick="switchPatientTab('home', document.getElementById('btn-nav-home'))">← Back to
                            Home</button>
                    </div>
                    <section class="dash-section-card">
                        <div class="section-header">
                            <h3 data-i18n="todayQAHeader">📝 Today's Q&A & EMAI Conversation</h3>
                            <button onclick="clearEmaiStorage()"
                                style="background:transparent; border:1px solid rgba(248,113,113,0.3); color:#FECACA; padding:4px 8px; border-radius:4px; font-size:0.75rem; cursor:pointer;"
                                data-i18n="clearChat">Clear Chat History</button>
                        </div>
                        <p style="color: var(--text-secondary);" data-i18n="qaDesc">Your daily reflections are stored
                            securely with client-side masking.</p>
                        <div class="qa-list" id="qa-storage-list"></div>
                    </section>
                </div>

                <!-- TAB 4: MY DIARY -->
                <div id="patient-tab-diary" class="patient-tab-content">
                    <div>
                        <button class="btn-universal-back"
                            onclick="switchPatientTab('home', document.getElementById('btn-nav-home'))">← Back to
                            Home</button>
                    </div>
                    <section class="dash-section-card">
                        <div class="section-header">
                            <h3 data-i18n="diaryHeader">📖 My Private Diary</h3>
                        </div>
                        <p style="color: var(--text-secondary); margin-bottom: 1rem;" data-i18n="diaryDesc">Encrypted
                            space to write your thoughts. Only you can access this.</p>
                        <textarea id="diary-input" class="diary-textarea form-input"
                            placeholder="Dear Diary, today I feel..." data-i18n-placeholder="phDiary"></textarea>
                        <button class="btn-edit-save" onclick="saveDiaryEntry()" data-i18n="saveEntry">Save Encrypted
                            Entry</button>
                        <div class="diary-entry-list" id="diary-list"></div>
                    </section>
                </div>

                <!-- TAB 5: PERFORMANCE -->
                <div id="patient-tab-performance" class="patient-tab-content">
                    <div>
                        <button class="btn-universal-back"
                            onclick="switchPatientTab('home', document.getElementById('btn-nav-home'))">← Back to
                            Home</button>
                    </div>
                    <div class="dash-cols-even">
                        <section class="dash-section-card">
                            <div class="section-header">
                                <h3 data-i18n="achievementsHeader">🏆 Achievements</h3>
                            </div>
                            <div class="task-list">
                                <div class="task-item">
                                    <div class="task-content"><span style="color:var(--btn-primary);"
                                            data-i18n="achieve1">✓ Watched: 5 Min Meditation</span></div>
                                </div>
                                <div class="task-item">
                                    <div class="task-content"><span style="color:var(--btn-primary);"
                                            data-i18n="achieve2">✓ Completed Morning Check-in</span></div>
                                </div>
                            </div>
                        </section>
                        <section class="dash-section-card">
                            <div class="section-header">
                                <h3 data-i18n="weeklyMilestonesHeader">📅 Weekly Milestones</h3>
                            </div>
                            <div class="task-list">
                                <label class="task-item"><input type="checkbox" checked class="task-checkbox"><span
                                        data-i18n="weekMile1">Completed 3 Grounding Sessions</span></label>
                                <label class="task-item"><input type="checkbox" checked class="task-checkbox"><span
                                        data-i18n="weekMile2">Logged Daily Emotions</span></label>
                            </div>
                        </section>
                    </div>
                    <section class="dash-section-card">
                        <div class="section-header">
                            <h3 data-i18n="yearlyProgressHeader">📈 Yearly Progress (52 Weeks)</h3>
                        </div>
                        <div class="yearly-graph-container" id="yearly-graph-container"></div>
                    </section>
                </div>

                <!-- TAB 6: CONSULTANTS -->
                <div id="patient-tab-consultants" class="patient-tab-content">
                    <div>
                        <button class="btn-universal-back"
                            onclick="switchPatientTab('home', document.getElementById('btn-nav-home'))">← Back to
                            Home</button>
                    </div>
                    <section class="dash-section-card">
                        <div class="section-header">
                            <h3 data-i18n="consultantsHeader">💬 Mental Health & Support Specialists</h3>
                        </div>
                        <p style="color: var(--text-secondary);" data-i18n="consultantsDesc">Connect securely with
                            dedicated mental health specialists and counselors.</p>
                        <div class="consultant-grid">
                            <div class="consultant-card">
                                <div class="c-avatar">👩‍⚕️</div>
                                <div class="c-info">
                                    <div class="c-name">Dr. Aranya Sharma</div>
                                    <div class="c-title">Clinical Psychiatrist</div>
                                    <button class="btn-chat-now"
                                        onclick="alert('Opening encrypted consultation channel...')"
                                        data-i18n="chatNow">Chat Now</button>
                                </div>
                            </div>
                            <div class="consultant-card">
                                <div class="c-avatar">🧑‍💼</div>
                                <div class="c-info">
                                    <div class="c-name">Marcus Vance, LCSW</div>
                                    <div class="c-title">Trauma Counselor</div>
                                    <button class="btn-chat-now"
                                        onclick="alert('Opening encrypted consultation channel...')"
                                        data-i18n="chatNow">Chat Now</button>
                                </div>
                            </div>
                            <div class="consultant-card">
                                <div class="c-avatar">👩‍🏫</div>
                                <div class="c-info">
                                    <div class="c-name">Dr. Sarah Jenkins</div>
                                    <div class="c-title">Clinical Psychologist</div>
                                    <button class="btn-chat-now"
                                        onclick="alert('Opening encrypted consultation channel...')"
                                        data-i18n="chatNow">Chat Now</button>
                                </div>
                            </div>
                            <div class="consultant-card">
                                <div class="c-avatar">👨‍⚕️</div>
                                <div class="c-info">
                                    <div class="c-name">Dr. David Chen</div>
                                    <div class="c-title">Behavioral Psychiatrist</div>
                                    <button class="btn-chat-now"
                                        onclick="alert('Opening encrypted consultation channel...')"
                                        data-i18n="chatNow">Chat Now</button>
                                </div>
                            </div>
                            <div class="consultant-card">
                                <div class="c-avatar">👩‍⚕️</div>
                                <div class="c-info">
                                    <div class="c-name">Dr. Elena Rodriguez</div>
                                    <div class="c-title">PTSD Specialist</div>
                                    <button class="btn-chat-now"
                                        onclick="alert('Opening encrypted consultation channel...')"
                                        data-i18n="chatNow">Chat Now</button>
                                </div>
                            </div>
                        </div>
                    </section>
                </div>

                <!-- TAB 7: PERSONAL INFO -->
                <div id="patient-tab-personal" class="patient-tab-content">
                    <div>
                        <button class="btn-universal-back"
                            onclick="switchPatientTab('home', document.getElementById('btn-nav-home'))">← Back to
                            Home</button>
                    </div>
                    <section class="dash-section-card">
                        <div class="section-header">
                            <h3 data-i18n="personalInfoHeader">👤 Personal Information</h3>
                            <button id="edit-profile-btn" class="btn-edit-save" onclick="toggleEditProfile()"
                                data-i18n="editProfile">Edit Profile</button>
                        </div>
                        <form id="personal-info-form" class="editable-form"
                            onsubmit="event.preventDefault(); toggleEditProfile();">
                            <div class="form-group"><label class="form-label" data-i18n="piFullName">Full
                                    Name</label><input type="text" id="pi-name" class="user-editable form-input"
                                    value="Kanika Jha" readonly></div>
                            <div class="form-group"><label class="form-label" data-i18n="piAddress">Safe Location /
                                    Address</label><input type="text" id="pi-place" class="user-editable form-input"
                                    value="Apt 4B, Serenity Heights, Seattle" readonly></div>
                            <div class="form-group"><label class="form-label" data-i18n="piPhone">Primary Contact
                                    Number</label><input type="text" id="pi-number" class="user-editable form-input"
                                    value="+1 (555) 019-2834" readonly></div>
                            <div class="form-group"><label class="form-label" data-i18n="piEmergencyContact">Emergency
                                    Contact</label><input type="text" id="pi-emergency" class="user-editable form-input"
                                    value="Sarah Jha (Sister) - 555-019-9999" readonly></div>
                            <div class="form-group full-width"><label class="form-label" data-i18n="piNotes">Safety
                                    Details & Notes</label><textarea id="pi-notes" class="user-editable form-input"
                                    rows="4"
                                    readonly>Prefers quiet environments. Severe anxiety around loud sirens.</textarea>
                            </div>

                            <div class="full-width"
                                style="margin-top: 1.5rem; border-top: 1px solid var(--border-subtle); padding-top: 1.5rem;">
                                <h3 style="color: var(--alert-important); font-size: 1.1rem; margin-bottom: 0.4rem;">🔒
                                    Official Case & Medical Details (Authority Locked)</h3>
                            </div>

                            <div class="form-group"><label class="form-label">FIR Number</label><input type="text"
                                    value="FIR-2026-993-A" class="officer-locked-input form-input" readonly
                                    tabindex="-1"></div>
                            <div class="form-group"><label class="form-label">Police Station Jurisdiction</label><input
                                    type="text" value="Central District Station" class="officer-locked-input form-input"
                                    readonly tabindex="-1"></div>
                            <div class="form-group"><label class="form-label">Date Filed</label><input type="text"
                                    value="Oct 02, 2026" class="officer-locked-input form-input" readonly tabindex="-1">
                            </div>
                            <div class="form-group"><label class="form-label">Assigned Investigating
                                    Officer(s)</label><input type="text"
                                    value="Officer Richard (ID: #4092) & Officer Minakshi Verma"
                                    class="officer-locked-input form-input" readonly tabindex="-1"></div>

                            <div class="form-group full-width">
                                <label class="form-label">Past Medical History / Risk Factors</label>
                                <textarea class="officer-locked-input form-input" rows="3" readonly
                                    tabindex="-1">History of acute stress response. Elevated heart rate observed during clinical intake. Monitor closely for panic disorder signs.</textarea>
                            </div>

                            <div class="full-width"
                                style="margin-top: 1.5rem; border-top: 1px solid var(--border-subtle); padding-top: 1.5rem;">
                                <h3 style="color: var(--btn-secondary); font-size: 1.1rem; margin-bottom: 0.4rem;">⚖️
                                    Legal Representation</h3>
                            </div>
                            <div class="form-group"><label class="form-label">Assigned Attorney</label><input
                                    type="text" value="Amanda Hayes, Esq. (Legal Aid)"
                                    class="officer-locked-input form-input" readonly tabindex="-1"></div>
                            <div class="form-group" style="justify-content: flex-end;">
                                <button type="button"
                                    style="background:var(--btn-secondary); color:#04241F; padding:0.9rem; border:none; border-radius:8px; font-weight:bold; cursor:pointer;"
                                    onclick="alert('Initiating secure call to Attorney Amanda Hayes...')">📞 Contact
                                    Attorney</button>
                            </div>
                        </form>
                    </section>
                </div>
            </div>

            <footer class="app-footer" id="main-footer" style="display:none;">
                © 2026 MediCore Safe Gateway. All rights reserved. Encrypted HIPAA/CJIS compliant platform.
            </footer>
        </div>
    </main>

    <!-- EMAI Voice & Companion Widget -->
    <div class="emai-widget-container" id="emai-container">
        <div class="emai-cloud" data-i18n="emaiCloud">Hello, I'm here if you need to talk ☁️</div>

        <div class="emai-chat-panel" id="emai-chat">
            <div class="emai-chat-header">
                <div>
                    <h4><span
                            style="background:var(--btn-primary); color:#04241F; padding:2px 6px; border-radius:4px; font-weight:800;">EMAI</span>
                        Safe Companion</h4>
                    <span class="emai-voice-status" id="emai-voice-indicator">Voice Ready • Click mic or type</span>
                </div>
                <button class="emai-close" onclick="closeEmai()">✕</button>
            </div>
            <div class="emai-chat-history" id="emai-chat-history"></div>
            <div class="emai-input-area">
                <button type="button" class="btn-emai-voice" id="btn-voice-toggle" onclick="toggleVoiceCompanion()"
                    title="Speak to EMAI">
                    <svg width="18" height="18" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2">
                        <path d="M12 1a3 3 0 0 0-3 3v8a3 3 0 0 0 6 0V4a3 3 0 0 0-3-3z"></path>
                        <path d="M19 10v2a7 7 0 0 1-14 0v-2"></path>
                        <line x1="12" y1="19" x2="12" y2="23"></line>
                        <line x1="8" y1="23" x2="16" y2="23"></line>
                    </svg>
                </button>
                <input type="text" id="emai-input" placeholder="Type gently here..."
                    onkeypress="if(event.key === 'Enter') handleEmaiAnswer()">
                <button onclick="handleEmaiAnswer()" data-i18n="btnSend">Send</button>
            </div>
        </div>
        <div class="emai-box" onclick="toggleEmai()">
            <div class="emai-eye"></div>
            <div class="emai-eye"></div>
        </div>
    </div>

    <!-- AUDIO PLAYER MODAL -->
    <div class="custom-modal-container" id="audio-modal-container">
        <div class="custom-modal">
            <h3 style="font-size:1.5rem; font-weight:800; color:var(--text-primary);">Relaxing Audio Space 🎧</h3>
            <div class="audio-wrapper"><iframe src="https://www.youtube.com/embed/lE6RYpe9IT0?autoplay=0"
                    allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture"
                    allowfullscreen></iframe></div>
            <button class="btn-g-secondary" onclick="closeAudioModal()">Close Audio</button>
        </div>
    </div>

    <!-- 8-MIN BREATHING EXERCISE MODAL -->
    <div class="custom-modal-container" id="breathing-modal-container">
        <div class="custom-modal">
            <h3 style="font-size:1.5rem; font-weight:800; color:var(--text-primary);">8-Minute Breathing 🌬️</h3>
            <p style="color:var(--text-secondary); margin-bottom:1rem;" id="breath-status-text">Ready to begin? Find a
                comfortable position.</p>
            <div style="font-size: 2rem; font-weight:800; color:white; margin-bottom: 1rem;" id="breath-timer">08:00
            </div>
            <div class="breathing-circle-wrapper">
                <div class="breathing-circle" id="breath-circle">READY</div>
            </div>
            <div style="display:flex; justify-content:center; gap:10px;">
                <button class="btn-g-primary" id="btn-start-breath" onclick="startBreathing()">Start Session</button>
                <button class="btn-g-secondary" onclick="stopBreathing()">Cancel</button>
            </div>
        </div>
    </div>

    <!-- GROUNDING HUB MODAL -->
    <div class="custom-modal-container" id="grounding-hub-container">
        <div class="custom-modal">
            <h3 style="font-size:1.5rem; font-weight:800; color:var(--text-primary);">Grounding Exercises 🌱</h3>
            <p style="color:var(--text-secondary); margin-bottom:1rem;">Grounding helps bring you back to the present
                moment when you feel overwhelmed.</p>
            <div style="display:flex; flex-direction:column; gap:10px;">
                <button class="btn-g-primary"
                    onclick="alert('5-4-3-2-1 Technique: Name 5 things you see, 4 you feel, 3 you hear, 2 you smell, 1 you taste.')">5-4-3-2-1
                    Technique</button>
                <button class="btn-g-secondary"
                    onclick="alert('Present Moment: Notice whether you are sitting or standing. Can you feel the ground under your feet?')">Present-Moment
                    Questions</button>
                <button class="btn-g-secondary"
                    onclick="alert('Breathe slowly. Notice your surroundings. Focus on one object.')">Slow
                    Breathing</button>
                <button class="btn-g-secondary"
                    onclick="alert('Imagine a place where you feel completely safe and comfortable. What colors do you see there?')">Safe
                    Place Visualization</button>
            </div>
            <button class="btn-g-secondary" style="border:none; margin-top:20px;"
                onclick="closeGroundingHub()">Close</button>
        </div>
    </div>

    <!-- PATIENT SOS COUNTDOWN MODAL -->
    <div class="custom-modal-container" id="sos-countdown-container" style="background: rgba(69, 10, 10, 0.95);">
        <div class="emergency-modal">
            <h2 style="font-size: 2.5rem; font-weight: 800; margin-bottom: 1rem;" id="sos-modal-title">EMERGENCY SIGNAL
                SENT</h2>
            <p style="font-size: 1.2rem; color: #fecaca; margin-bottom: 2rem;" id="sos-modal-desc">A high-priority alert
                has been dispatched to Officer Richard and the rapid response team. Help is on the way.</p>
            <div style="font-size: 4rem; font-weight: 800; font-variant-numeric: tabular-nums; margin-bottom: 2rem;"
                id="sos-timer">10:00</div>
            <p style="font-size: 1rem; color: #fca5a5;">Your location and encrypted case file have been transmitted.</p>
        </div>
    </div>

    <!-- ADMIN CASE FILE MODAL -->
    <div class="custom-modal-container" id="admin-case-file-modal">
        <div class="custom-modal"
            style="text-align:left; max-width: 800px; background: var(--surface-card); border-color: var(--btn-primary); overflow-y:auto; max-height:90vh;">
            <div
                style="display:flex; justify-content:space-between; border-bottom:1px solid var(--btn-primary); padding-bottom:1rem; margin-bottom:1rem;">
                <h3 style="color:var(--text-primary);" id="admin-case-modal-title">📁 CASE FILE: #FIR-2026-993-A</h3>
                <button onclick="document.getElementById('admin-case-file-modal').classList.remove('active')"
                    style="background:none; border:none; color:white; cursor:pointer; font-size:1.2rem;">✕</button>
            </div>
            <div style="display:grid; grid-template-columns: 1fr 1fr; gap: 1rem; color: var(--text-primary);">
                <div><strong>Victim Name:</strong> <span id="admin-case-victim-name">Kanika Jha</span></div>
                <div><strong>Phone:</strong> +1 (555) 019-2834</div>
                <div
                    style="grid-column: 1 / -1; background:rgba(239,68,68,0.1); padding:1rem; border-radius:8px; border:1px solid #ef4444;">
                    <strong>📍 Current Live Location:</strong> Apt 4B, Serenity Heights, Seattle (Signal Active)
                </div>
                <div style="grid-column: 1 / -1;">
                    <strong style="color:var(--alert-important);">Past Records & Alerts:</strong>
                    <ul style="margin-left: 1.5rem; margin-top:0.5rem; color:var(--text-secondary);">
                        <li>Prior incident logged at same location (Oct 02, 2026).</li>
                        <li>Restraining order actively in place against known threat.</li>
                    </ul>
                </div>
                <div style="grid-column: 1 / -1;">
                    <strong style="color:var(--alert-important);">Medical Details & Risks:</strong>
                    <p style="margin-top:0.5rem; color:var(--text-secondary);">History of acute stress response and
                        panic disorder. Elevated heart rate under duress. Mild allergy to penicillin.</p>
                </div>
                <div
                    style="grid-column: 1 / -1; margin-top: 1rem; border-top: 1px solid var(--border-subtle); padding-top: 1rem;">
                    <strong style="color:var(--text-secondary);">Latest Patient Inputs & Multimodal Telemetry:</strong>
                    <div id="admin-case-responses"
                        style="margin-top:0.5rem; max-height:200px; overflow-y:auto; background:var(--surface-alt); padding:1rem; border-radius:8px;">
                    </div>
                </div>
            </div>

            <!-- ADMIN VIEW DOSSIER QUICK ACTIONS -->
            <div
                style="margin-top:2rem; display:flex; flex-wrap:wrap; gap:10px; justify-content:space-between; padding-top:1rem; border-top: 1px solid var(--border-subtle);">
                <button
                    style="background:var(--btn-secondary); color:#fff; border:none; padding:10px 15px; border-radius:8px; font-weight:bold; cursor:pointer;"
                    onclick="alert('Connecting to Encrypted Counseling Dispatch Line...')">📞 Contact
                    Counseling</button>
                <button
                    style="background:#60a5fa; color:white; border:none; padding:10px 15px; border-radius:8px; font-weight:bold; cursor:pointer;"
                    onclick="exportLegalDossier()">📄 Export PDF</button>
                <button
                    style="background:#ef4444; color:white; border:none; padding:10px 15px; border-radius:8px; font-weight:bold; cursor:pointer;"
                    onclick="alert('Dispatching physical unit to coordinates.')">🚨 Dispatch Unit</button>
                <button
                    style="background:var(--surface-input); color:var(--text-secondary); border:1px solid var(--border-subtle); padding:10px 15px; border-radius:8px; font-weight:bold; cursor:pointer;"
                    onclick="clearSOS()">Clear SOS</button>
            </div>
        </div>
    </div>

    <!-- QUIET CHECK-IN MODAL -->
    <div class="custom-modal-container" id="checkin-modal-container">
        <div class="checkin-shell">
            <div class="checkin-top-bar">
                <div class="checkin-brand">A Quiet Check-In</div>
                <div style="display: flex; align-items: center; gap: 15px;">
                    <button class="checkin-help-link"
                        onclick="document.getElementById('checkin-helpPanel').classList.toggle('open')">Need to talk to
                        someone right now?</button>
                    <button class="emai-close" onclick="closeQuietCheckinModal()">✕</button>
                </div>
            </div>
            <div class="checkin-help-panel" id="checkin-helpPanel">
                <div style="color: #fecaca;"><strong>You don't have to wait for this form to get help.</strong></div>
                <div style="color: #fecaca;">Women Helpline (India): 181 &nbsp;•&nbsp; Police: 100 &nbsp;•&nbsp;
                    National Commission for Women: 7827-170-170</div>
            </div>
            <div class="checkin-card" id="checkin-card"></div>
        </div>
    </div>

    <!-- JavaScript Translations, Security Engine & Core Logic -->
    <script>
        // =======================================================
        // PRIVACY & SECURITY ENGINE
        // =======================================================
        const SecurityEngine = {
            inactivityTimer: null,
            timeoutDuration: 3 * 60 * 1000,

            maskData(str) {
                try { return btoa(encodeURIComponent(str)); } catch (e) { return str; }
            },
            unmaskData(str) {
                try { return decodeURIComponent(atob(str)); } catch (e) { return str; }
            },
            resetInactivityClock() {
                clearTimeout(this.inactivityTimer);
                this.inactivityTimer = setTimeout(() => {
                    if (document.getElementById('screen-dashboard').classList.contains('active')) {
                        alert("Session Auto-Locked for privacy protection due to inactivity.");
                        handleLogout();
                    }
                }, this.timeoutDuration);
            },
            initSecurityWatchdogs() {
                ['mousemove', 'keydown', 'touchstart', 'scroll'].forEach(evt => {
                    window.addEventListener(evt, () => this.resetInactivityClock());
                });
                window.addEventListener('keydown', (e) => {
                    if (e.key === 'Escape') { executeQuickExit(); }
                });
            }
        };

        SecurityEngine.initSecurityWatchdogs();

        function executeQuickExit() {
            window.speechSynthesis.cancel();
            if (PatientTelemetry.audioStream) {
                PatientTelemetry.audioStream.getTracks().forEach(t => t.stop());
            }
            sessionStorage.clear();
            window.location.replace("https://news.google.com");
        }

        function toggleCamouflage(show) {
            const screen = document.getElementById('camouflage-screen');
            if (show) {
                window.speechSynthesis.cancel();
                stopVoiceListening();
                screen.classList.add('active');
            } else {
                screen.classList.remove('active');
            }
        }

        let isLowBandwidth = false;
        function toggleLowBandwidthMode() {
            isLowBandwidth = !isLowBandwidth;
            if (isLowBandwidth) {
                document.body.style.backgroundImage = 'none';
                alert("Low-Bandwidth Mode Enabled: Optimized for lightweight text and audio transmission over unstable connections.");
            } else {
                alert("Standard High-Fidelity Mode Restored.");
            }
        }

        // --- TRANSLATION DICTIONARY ---
        const TRANSLATIONS = {
            en: {
                badgeGateway: "MediCore Safe Gateway",
                welcomeTitle: "Welcome!",
                welcomeSubtitle: "Select your portal access below.",
                tabPatient: "Login",
                tabAdmin: "Admin Officer",
                labelPatientId: "User ID",
                phPatientId: "e.g. KANIKA",
                btnPassword: "Password",
                btnOtp: "Send OTP SMS",
                phPassword: "•••••••• (Hint: 1234567 | Decoy PIN: 0000)",
                phOtp: "Enter 6-digit OTP (Any number)",
                btnSignIn: "Sign In Securely",
                labelOfficerId: "Officer ID",
                phOfficerId: "RICHARD, MINAKSHI, or TANMAY",
                labelAuthCode: "Unique Auth Code",
                forgotCode: "Forgot Code?",
                btnAccessAdmin: "Access Admin Console",
                headerTitle: "MediCore Safe Portal",
                headerSubtitle: "Operational Suite",
                btnSignOut: "Sign Out",
                navHome: "Home",
                navActivity: "Daily Activity",
                navQA: "Today's Q&A",
                navDiary: "My Diary",
                navPerformance: "Performance",
                navTalk: "Talk to Someone",
                navPersonal: "Personal Info",
                patientHeroTitle: "🛡️ SAFE SPACE",
                patientHeroSub: "\"You are safe here. Take things at your own pace.\"",
                quietCheckinTitle: "📝 Today's Quiet Check-In",
                quietCheckinDesc: "A short, private check-in about how you've been feeling day to day.",
                startCheckin: "Start Check-In",
                smallStepsHeader: "🌱 5 SMALL STEPS TODAY",
                step1: "Drink a glass of water",
                step2: "Take a short 5-minute walk",
                step3: "Stretch your shoulders & neck",
                step4: "Write down one thing you are grateful for",
                step5: "Get 15 minutes of fresh air/sunlight",
                calmingHeader: "🧘 CALMING SPACE",
                groundingEx: "🌱 Grounding Exercises",
                breathingEx: "🌬️ 8-Min Breathing Exercise",
                audioEx: "🎧 Relaxing Audio",
                milestonesHeader: "🌟 Big Milestones & Proof",
                milestonesSub: "Have you achieved a major milestone? Upload a photo or document as proof for Admin review!",
                phMilestone: "E.g., Completed physical therapy",
                btnSubmitReview: "Submit for Review",
                messageForYou: "A Message For You",
                messageBody: "You are doing incredibly well. Taking things one day at a time is a brave and beautiful step forward. We are so proud of your resilience. Remember, healing is not linear, and every small effort you make is a victory. You are safe, you are heard, and your journey matters.",
                companionSummary: "💬 Companion Summary & Responsiveness",
                companionDesc: "Your safe responses logged with EMAI are continuously updated in your Q&A section.",
                interactionLabel: "Interaction",
                excellentEngagement: "Excellent Engagement Today!",
                healthScoreHeader: "🔋 Positivity & Health Score",
                todayLabel: "Today",
                pastWeekHeader: "📊 Past Week Analysis",
                todayQAHeader: "📝 Today's Q&A & EMAI Conversation",
                clearChat: "Clear Chat History",
                qaDesc: "Your daily reflections are stored securely here with client-side masking.",
                diaryHeader: "📖 My Private Diary",
                diaryDesc: "A free space to write whatever is on your mind. Only you can see this.",
                phDiary: "Dear Diary, today I feel...",
                saveEntry: "Save Encrypted Entry",
                achievementsHeader: "🏆 Achievements",
                achieve1: "✓ Watched: 5 Min Meditation",
                achieve2: "✓ Completed Morning Check-in",
                weeklyMilestonesHeader: "📅 Weekly Milestones",
                weekMile1: "Completed 3 Grounding Sessions",
                weekMile2: "Logged Daily Emotions",
                yearlyProgressHeader: "📈 Yearly Progress (52 Weeks)",
                consultantsHeader: "💬 Mental Health & Support Specialists",
                consultantsDesc: "Connect securely with dedicated mental health specialists and counselors.",
                chatNow: "Chat Now",
                personalInfoHeader: "👤 Personal Information",
                editProfile: "Edit Profile",
                piFullName: "Full Name",
                piAddress: "Safe Location / Address",
                piPhone: "Primary Contact Number",
                piEmergencyContact: "Emergency Contact",
                piNotes: "Safety Details & Notes",
                emaiCloud: "Hello, I'm here if you need to talk ☁️",
                btnSend: "Send",
                adminWelcome: "Welcome back, Officer ",
                adminSub: "Case Management Command: Active Cases, Victim Statements, and Legal Audits.",
                adminCasesHeader: "📁 Registered Victim Cases (10 Total)",
                adminMilestonesHeader: "🌟 Milestone Verifications",
                adminQuickActions: "⚖️ Quick Actions",
                adminWellbeing: "📊 Today's Wellbeing Check-Ins"
            },
            hi: {
                badgeGateway: "मेडीकोर सुरक्षित गेटवे",
                welcomeTitle: "स्वागत है!",
                welcomeSubtitle: "नीचे अपने पोर्टल का चयन करें।",
                tabPatient: "लॉगिन",
                tabAdmin: "प्रशासन अधिकारी",
                labelPatientId: "यूजर आईडी",
                phPatientId: "उदा. KANIKA",
                btnPassword: "पासवर्ड",
                btnOtp: "ओटीपी एसएमएस भेजें",
                phPassword: "•••••••• (संकेत: 1234567)",
                phOtp: "6-अंकों का ओटीपी दर्ज करें",
                btnSignIn: "सुरक्षित साइन इन करें",
                labelOfficerId: "अधिकारी आईडी",
                phOfficerId: "उदा. RICHARD",
                labelAuthCode: "विशिष्ट प्रमाणीकरण कोड",
                forgotCode: "कोड भूल गए?",
                btnAccessAdmin: "एडमिन कंसोल एक्सेस करें",
                headerTitle: "मेडीकोर सेफ पोर्टल",
                headerSubtitle: "ऑपरेशनल सूट",
                btnSignOut: "साइन आउट",
                navHome: "होम",
                navActivity: "दैनिक गतिविधि",
                navQA: "आज के प्रश्न-उत्तर",
                navDiary: "मेरी डायरी",
                navPerformance: "प्रदर्शन",
                navTalk: "किसी से बात करें",
                navPersonal: "व्यक्तिगत जानकारी",
                patientHeroTitle: "🛡️ सुरक्षित स्थान",
                patientHeroSub: "\"आप यहाँ सुरक्षित हैं। अपनी गति से आगे बढ़ें।\"",
                quietCheckinTitle: "📝 आज का शांत चेक-इन",
                quietCheckinDesc: "प्रतिदिन की भावनाओं के बारे में संक्षिप्त और सुरक्षित चेक-इन।",
                startCheckin: "चेक-इन शुरू करें",
                smallStepsHeader: "🌱 आज के 5 छोटे कदम",
                step1: "एक गिलास पानी पिएं",
                step2: "5 मिनट की छोटी सैर करें",
                step3: "कंधों और गर्दन में खिंचाव करें",
                step4: "एक अच्छी बात लिखें",
                step5: "15 मिनट ताज़ी हवा लें",
                calmingHeader: "🧘 शांत स्थान",
                groundingEx: "🌱 ग्राउंडिंग अभ्यास",
                breathingEx: "🌬️ 8-मिनट श्वास व्यायाम",
                audioEx: "🎧 आरामदायक ऑडियो",
                milestonesHeader: "🌟 प्रमुख मील के पत्थर",
                milestonesSub: "प्रमाण अपलोड करें!",
                phMilestone: "उदा. थेरेपी पूरी की",
                btnSubmitReview: "जमा करें",
                messageForYou: "आपके लिए एक संदेश",
                messageBody: "आप बहुत बहादुर हैं। आपका हर कदम एक जीत है।",
                companionSummary: "💬 साथी सारांश",
                companionDesc: "आपकी बातें सुरक्षित रूप से संग्रहीत हैं।",
                interactionLabel: "बातचीत",
                excellentEngagement: "उत्कृष्ट जुड़ाव!",
                healthScoreHeader: "🔋 स्वास्थ्य स्कोर",
                todayLabel: "आज",
                pastWeekHeader: "📊 साप्ताहिक विश्लेषण",
                todayQAHeader: "📝 आज के प्रश्न-उत्तर",
                clearChat: "इतिहास मिटाएं",
                qaDesc: "आपकी दैनिक बातें गोपनीय रखी जाती हैं।",
                diaryHeader: "📖 मेरी निजी डायरी",
                diaryDesc: "सुरक्षित निजी डायरी।",
                phDiary: "प्रिय डायरी...",
                saveEntry: "सहेजें",
                achievementsHeader: "🏆 उपलब्धियां",
                achieve1: "✓ 5 मिनट ध्यान",
                achieve2: "✓ सुबह का चेक-इन पूरा हुआ",
                weeklyMilestonesHeader: "📅 साप्ताहिक मील के पत्थर",
                weekMile1: "3 ग्राउंडिंग सत्र",
                weekMile2: "भावनाएं दर्ज",
                yearlyProgressHeader: "📈 वार्षिक प्रगति",
                consultantsHeader: "💬 मानसिक स्वास्थ्य विशेषज्ञ",
                consultantsDesc: "विशेषज्ञों से सुरक्षित बात करें।",
                chatNow: "बात करें",
                personalInfoHeader: "👤 व्यक्तिगत जानकारी",
                editProfile: "संपादित करें",
                piFullName: "पूरा नाम",
                piAddress: "सुरक्षित पता",
                piPhone: "फोन नंबर",
                piEmergencyContact: "आपातकालीन संपर्क",
                piNotes: "सुरक्षा नोट्स",
                emaiCloud: "नमस्ते, बात करने के लिए मैं यहाँ हूँ ☁️",
                btnSend: "भेजें",
                adminWelcome: "स्वागत है, अधिकारी ",
                adminSub: "सुरक्षित केस प्रबंधन कमान।",
                adminCasesHeader: "📁 पंजीकृत मामले (कुल 10)",
                adminMilestonesHeader: "🌟 सत्यापन",
                adminQuickActions: "⚖️ त्वरित क्रियाएं",
                adminWellbeing: "📊 आज के चेक-इन"
            },
            or: {
                badgeGateway: "ମେଡିକୋର୍ ସୁରକ୍ଷିତ ଗେଟୱେ",
                welcomeTitle: "ସ୍ୱାଗତ!",
                welcomeSubtitle: "ତଳେ ଆପଣଙ୍କର ପୋର୍ଟାଲ୍ ଚୟନ କରନ୍ତୁ।",
                tabPatient: "ଲଗଇନ୍",
                tabAdmin: "ପ୍ରଶାସକ ଅଧିକାରୀ",
                labelPatientId: "ରୋଗୀ ID",
                phPatientId: "ଯଥା KANIKA",
                btnPassword: "ପାସୱାର୍ଡ",
                btnOtp: "OTP ପଠାନ୍ତୁ",
                phPassword: "•••••••• (ସୂଚନା: 1234567)",
                phOtp: "୬-ଅଙ୍କ ବିଶିଷ୍ଟ OTP ଲେଖନ୍ତୁ",
                btnSignIn: "ସୁରକ୍ଷିତ ଭାବେ ସାଇନ୍ ଇନ୍ କରନ୍ତୁ",
                labelOfficerId: "ଅଧିକାରୀ ID",
                phOfficerId: "ଯଥା RICHARD",
                labelAuthCode: "ପ୍ରମାଣୀକରଣ କୋଡ୍",
                forgotCode: "କୋଡ୍ ଭୁଲିଗଲେ?",
                btnAccessAdmin: "ଆଡମିନ୍ କନସୋଲ୍ ଖୋଲନ୍ତୁ",
                headerTitle: "ମେଡିକୋର୍ ସୁରକ୍ଷା ପୋର୍ଟାଲ୍",
                headerSubtitle: "ଅପରେସନାଲ୍ ସୁଇଟ୍",
                btnSignOut: "ସାଇନ୍ ଆଉଟ୍",
                navHome: "ମୁଖ୍ୟ ପୃଷ୍ଠା",
                navActivity: "ଦୈନନ୍ଦିନ କାର୍ଯ୍ୟକଳାପ",
                navQA: "ଆଜିର ପ୍ରଶ୍ନୋତ୍ତର",
                navDiary: "ମୋର ଡାଏରୀ",
                navPerformance: "ପ୍ରଦର୍ଶନ",
                navTalk: "କାହା ସହ କଥା ହୁଅନ୍ତୁ",
                navPersonal: "ବ୍ୟକ୍ତିଗତ ସୂଚନା",
                patientHeroTitle: "🛡️ ସୁରକ୍ଷିତ ସ୍ଥାନ",
                patientHeroSub: "\"ଆପଣ ଏଠାରେ ସମ୍ପୂର୍ଣ୍ଣ ସୁରକ୍ଷିତ। ନିଜ ଗତିରେ ଆଗକୁ ବଢ଼ନ୍ତୁ।\"",
                quietCheckinTitle: "📝 ଆଜିର ଶାନ୍ତ ଚେକ୍-ଇନ୍",
                quietCheckinDesc: "ଦିନସାରା ଆପଣ କିପରି ଅନୁଭବ କରୁଛନ୍ତି ତାହା ଜଣାଇବା ପାଇଁ ଚେକ୍-ଇନ୍।",
                startCheckin: "ଚେକ୍-ଇନ୍ ଆରମ୍ଭ କରନ୍ତୁ",
                smallStepsHeader: "🌱 ଆଜିର ୫ଟି ଛୋଟ ପଦକ୍ଷେପ",
                step1: "ଗୋଟିଏ ଗ୍ଲାସ୍ ପାଣି ପିଅନ୍ତୁ",
                step2: "୫ ମିନିଟ୍ ଚାଲନ୍ତୁ",
                step3: "କାନ୍ଧ ଏବଂ ବେକ ଷ୍ଟ୍ରେଚ୍ କରନ୍ତୁ",
                step4: "ଏକ କୃତଜ୍ଞତା ଲେଖନ୍ତୁ",
                step5: "୧୫ ମିନିଟ୍ ତାଜା ପବନ ନିଅନ୍ତୁ",
                calmingHeader: "🧘 ଶାନ୍ତ ସ୍ଥାନ",
                groundingEx: "🌱 ଗ୍ରାଉଣ୍ଡିଂ ଅଭ୍ୟାସ",
                breathingEx: "🌬️ ୮ ମିନିଟ୍ ଶ୍ୱାସକ୍ରିୟା ବ୍ୟାୟାମ",
                audioEx: "🎧 ଆରାମଦାୟକ ଅଡିଓ",
                milestonesHeader: "🌟 ସଫଳତା ଓ ପ୍ରମାଣ",
                milestonesSub: "ପ୍ରମାଣ ଅପଲୋଡ୍ କରନ୍ତୁ!",
                phMilestone: "ଯଥା ଥେରାପି ସମାପ୍ତ",
                btnSubmitReview: "ଦାଖଲ କରନ୍ତୁ",
                messageForYou: "ଆପଣଙ୍କ ପାଇଁ ବାର୍ତ୍ତା",
                messageBody: "ଆପଣ ବହୁତ ଭଲ କରୁଛନ୍ତି। ଆପଣଙ୍କ ଯାତ୍ରା ସୁରକ୍ଷିତ।",
                companionSummary: "💬 ସାଥୀ ସାରାଂଶ",
                companionDesc: "ଆପଣଙ୍କ ଉତ୍ତର ଏଠାରେ ସୁରକ୍ଷିତ।",
                interactionLabel: "କଥାବାର୍ତ୍ତା",
                excellentEngagement: "ଉତ୍କୃଷ୍ଟ ଯୋଗାଯୋଗ!",
                healthScoreHeader: "🔋 ସ୍ୱାସ୍ଥ୍ୟ ସ୍କୋର",
                todayLabel: "ଆଜି",
                pastWeekHeader: "📊 ସାପ୍ତାହିକ ବିଶ୍ଳେଷଣ",
                todayQAHeader: "📝 ପ୍ରଶ୍ନୋତ୍ତର ଓ ଆଲୋଚନା",
                clearChat: "ଇତିହାସ ସଫା କରନ୍ତୁ",
                qaDesc: "ପ୍ରତିଫଳନ ସୁରକ୍ଷିତ ରହିଛି।",
                diaryHeader: "📖 ବ୍ୟକ୍ତିଗତ ଡାଏରୀ",
                diaryDesc: "ନିଜ ମନର କଥା ଲେଖନ୍ତୁ।",
                phDiary: "ପ୍ରିୟ ଡାଏରୀ...",
                saveEntry: "ସାଇତି ରଖନ୍ତୁ",
                achievementsHeader: "🏆 ସଫଳତା",
                achieve1: "✓ ୫ ମିନିଟ୍ ଧ୍ୟାନ",
                achieve2: "✓ ଚେକ୍-ଇନ୍ ସମ୍ପନ୍ନ",
                weeklyMilestonesHeader: "📅 ସାପ୍ତାହିକ ଲକ୍ଷ୍ୟ",
                weekMile1: "୩ଟି ଗ୍ରାଉଣ୍ଡିଂ ଅଧିବେଶନ",
                weekMile2: "ଭାବନା ରେକର୍ଡ ହୋଇଛି",
                yearlyProgressHeader: "📈 ବାର୍ଷିକ ଅଗ୍ରଗତି",
                consultantsHeader: "💬 ମାନସିକ ସ୍ୱାସ୍ଥ୍ୟ ବିଶେଷଜ୍ଞ",
                consultantsDesc: "ବିଶେଷଜ୍ଞଙ୍କ ସହ କଥା ହୁଅନ୍ତୁ।",
                chatNow: "କଥା ହୁଅନ୍ତୁ",
                personalInfoHeader: "👤 ବ୍ୟକ୍ତିଗତ ବିବରଣୀ",
                editProfile: "ସଂଶୋଧନ",
                piFullName: "ପୂରା ନାମ",
                piAddress: "ସୁରକ୍ଷିତ ଠିକଣା",
                piPhone: "ଫୋନ୍ ନମ୍ବର",
                piEmergencyContact: "ଜରୁରୀ ଯୋଗାଯୋଗ",
                piNotes: "ସୁରକ୍ଷା ଟିପ୍ପଣୀ",
                emaiCloud: "ନମସ୍କାର, ମୁଁ ଏଠାରେ ଅଛି ☁️",
                btnSend: "ପଠାନ୍ତୁ",
                adminWelcome: "ସ୍ୱାଗତ, ଅଧିକାରୀ ",
                adminSub: "ମାମଲା ପରିଚାଳନା କମାଣ୍ଡ।",
                adminCasesHeader: "📁 ପଞ୍ଜିକୃତ ମାମଲା (୧୦)",
                adminMilestonesHeader: "🌟 ପ୍ରମାଣ ଯାଞ୍ଚ",
                adminQuickActions: "⚖️ ତ୍ୱରିତ କାର୍ଯ୍ୟ",
                adminWellbeing: "📊 ଚେକ୍-ଇନ୍ ବିବରଣୀ"
            },
            ml: { badgeGateway: "മെഡികോർ സുരക്ഷിത ഗേറ്റ്‌വേ", welcomeTitle: "സ്വാഗതം!", welcomeSubtitle: "പോർട്ടൽ തിരഞ്ഞെടുക്കുക.", tabPatient: "ലോഗിൻ", tabAdmin: "അഡ്മിൻ ഓഫീസർ", labelPatientId: "പേഷ്യന്റ് ഐഡി", phPatientId: "KANIKA", btnPassword: "പാസ്‌വേഡ്", btnOtp: "ഒടിപി അയക്കുക", phPassword: "••••••••", phOtp: "ഒടിപി നൽകുക", btnSignIn: "ലോഗിൻ ചെയ്യുക", labelOfficerId: "ഓഫീസർ ഐഡി", phOfficerId: "RICHARD", labelAuthCode: "ഓതന്റിക്കേഷൻ കോഡ്", forgotCode: "കോഡ് മറന്നോ?", btnAccessAdmin: "അഡ്മിൻ കൺസോൾ", headerTitle: "മെഡികോർ സേഫ് പോർട്ടൽ", headerSubtitle: "ഓപ്പറേഷൻസ് സ്യൂട്ട്", btnSignOut: "സൈൻ ഔട്ട്", navHome: "ഹോം", navActivity: "പ്രവർത്തനങ്ങൾ", navQA: "ചോദ്യോത്തരങ്ങൾ", navDiary: "ഡയറി", navPerformance: "പുരോഗതി", navTalk: "സംസാരിക്കാം", navPersonal: "വിവരങ്ങൾ", patientHeroTitle: "🛡️ സുരക്ഷിത ഇടം", patientHeroSub: "\"നിങ്ങൾ സുരക്ഷിതനാണ്.\"", quietCheckinTitle: "📝 ചെക്ക്-ഇൻ", quietCheckinDesc: "സ്വകാര്യ ചെക്ക്-ഇൻ.", startCheckin: "ആരംഭിക്കുക", smallStepsHeader: "🌱 5 ചെറിയ കാര്യങ്ങൾ", step1: "വെള്ളം കുടിക്കുക", step2: "നടക്കുക", step3: "വ്യായാമം ചെയ്യുക", step4: "നന്ദി കുറിക്കുക", step5: "വായു ശ്വസിക്കുക", calmingHeader: "🧘 ശാന്തമായ ഇടം", groundingEx: "ഗ്രൗണ്ടിംഗ്", breathingEx: "ശ്വാസന വ്യായാമം", audioEx: "ഓഡിയോ", milestonesHeader: "🌟 ലക്ഷ്യങ്ങൾ", milestonesSub: "തെളിവ് അപ്‌ലോഡ് ചെയ്യുക!", phMilestone: "കോഴ്സ് പൂർത്തിയാക്കി", btnSubmitReview: "സമർപ്പിക്കുക", messageForYou: "സന്ദേശം", messageBody: "നിങ്ങൾ സുരക്ഷിതനാണ്.", companionSummary: "💬 സംഗ്രഹം", companionDesc: "സംഭാഷണങ്ങൾ സുരക്ഷിതം.", interactionLabel: "ഇടപെടൽ", excellentEngagement: "മികച്ച പങ്കാളിത്തം!", healthScoreHeader: "🔋 സ്കോർ", todayLabel: "ഇന്ന്", pastWeekHeader: "📊 വിശകലനം", todayQAHeader: "📝 ചോദ്യോത്തരങ്ങൾ", clearChat: "മായ്ക്കുക", qaDesc: "വിവരങ്ങൾ സുരക്ഷിതം.", diaryHeader: "📖 ഡയറി", diaryDesc: "സ്വകാര്യ ഇടം.", phDiary: "പ്രിയപ്പെട്ട ഡയറി...", saveEntry: "സൂക്ഷിക്കുക", achievementsHeader: "🏆 നേട്ടങ്ങൾ", achieve1: "ധ്യാനം", achieve2: "ചെക്ക്-ഇൻ", weeklyMilestonesHeader: "📅 നാഴികക്കല്ലുകൾ", weekMile1: "സെഷനുകൾ", weekMile2: "രേഖപ്പെടുത്തി", yearlyProgressHeader: "📈 വാർഷിക പുരോഗതി", consultantsHeader: "💬 വിദഗ്ധർ", consultantsDesc: "സംസാരിക്കുക.", chatNow: "സംസാരിക്കുക", personalInfoHeader: "👤 വിവരങ്ങൾ", editProfile: "മാറ്റുക", piFullName: "പേര്", piAddress: "വിലാസം", piPhone: "ഫോൺ", piEmergencyContact: "അടിയന്തിര നമ്പർ", piNotes: "വിവരങ്ങൾ", emaiCloud: "ഹലോ ☁️", btnSend: "അയക്കുക", adminWelcome: "സ്വാഗതം ", adminSub: "മാനേജ്മെന്റ് കമാൻഡ്.", adminCasesHeader: "📁 കേസുകൾ (10)", adminMilestonesHeader: "🌟 പരിശോധന", adminQuickActions: "⚖️ നടപടികൾ", adminWellbeing: "📊 റിപ്പോർട്ടുകൾ" },
            te: { badgeGateway: "మెడికోర్ సేఫ్ గేట్‌వే", welcomeTitle: "స్వాగతం!", welcomeSubtitle: "పోర్టల్ ఎంచుకోండి.", tabPatient: "లాగిన్", tabAdmin: "అడ్మిన్ ఆఫీసర్", labelPatientId: "పేషెంట్ ID", phPatientId: "KANIKA", btnPassword: "పాస్‌వర్డ్", btnOtp: "OTP పంపండి", phPassword: "••••••••", phOtp: "OTP నమోదు", btnSignIn: "లాగిన్ అవ్వండి", labelOfficerId: "ఆఫీసర్ ID", phOfficerId: "RICHARD", labelAuthCode: "కోడ్", forgotCode: "కోడ్ మర్చిపోయారా?", btnAccessAdmin: "కన్సోల్", headerTitle: "మెడికోర్ పోర్టల్", headerSubtitle: "ఆపరేషన్స్", btnSignOut: "സൈన్ అవుట్", navHome: "హోమ్", navActivity: "కార్యకలాపాలు", navQA: "ప్రశ్నోత్తరాలు", navDiary: "డైరీ", navPerformance: "ప్రగతి", navTalk: "మాట్లాడండి", navPersonal: "సమాచారం", patientHeroTitle: "🛡️ సురక్షిత ప్రదేశం", patientHeroSub: "\"సురక్షితంగా ఉండండి.\"", quietCheckinTitle: "📝 చెక్-ఇన్", quietCheckinDesc: "వ్యక్తిగత చెక్-ఇన్.", startCheckin: "ప్రారంభించండి", smallStepsHeader: "🌱 5 చిన్న అడుగులు", step1: "నీరు త్రాగండి", step2: "నడవండి", step3: "స్ట్రెచ్ చేయండి", step4: "రాయండి", step5: "గాలి పీల్చుకోండి", calmingHeader: "🧘 ప్రశాంతత", groundingEx: "వ్యాయామాలు", breathingEx: "శ్వాస వ్యాయామం", audioEx: "ఆడియో", milestonesHeader: "🌟 విజయాలు", milestonesSub: "అప్‌లోడ్ చేయండి!", phMilestone: "పూర్తయింది", btnSubmitReview: "సమర్పించండి", messageForYou: "సందేశం", messageBody: "మీరు సురక్షితంగా ఉన్నారు.", companionSummary: "💬 సారాంశం", companionDesc: "సంభాషణలు భద్రం.", interactionLabel: "సంభాషణ", excellentEngagement: "ఉత్తమ భాగస్వామ్యం!", healthScoreHeader: "🔋 స్కోరు", todayLabel: "ఈరోజు", pastWeekHeader: "📊 విశ్లేషణ", todayQAHeader: "📝 ప్రశ్నలు", clearChat: "తొలగించు", qaDesc: "భద్రపరచబడింది.", diaryHeader: "📖 డైరీ", diaryDesc: "వ్యక్తిగత ప్రదేశం.", phDiary: "డియర్ డైరీ...", saveEntry: "భద్రపరచు", achievementsHeader: "🏆 విజయాలు", achieve1: "ధ్యానం", achieve2: "చెక్-ఇన్", weeklyMilestonesHeader: "📅 మైలురాళ్ళు", weekMile1: "సెషన్‌లు", weekMile2: "నమోదు", yearlyProgressHeader: "📈 వార్షిక ప్రగతి", consultantsHeader: "💬 నిపుణులు", consultantsDesc: "మాట్లాడండి.", chatNow: "మాట్లాడండి", personalInfoHeader: "👤 సమాచారం", editProfile: "సవరించండి", piFullName: "పూర్తి పేరు", piAddress: "చిరునామా", piPhone: "ఫోన్", piEmergencyContact: "సంప్రదింపు", piNotes: "గమనికలు", emaiCloud: "హలో ☁️", btnSend: "పంపు", adminWelcome: "స్వాగతం ", adminSub: "కమాండ్ సిస్టమ్.", adminCasesHeader: "📁 కేసులు (10)", adminMilestonesHeader: "🌟 ధృవీకరణ", adminQuickActions: "⚖️ చర్యలు", adminWellbeing: "📊 నివేదికలు" },
            ta: { badgeGateway: "மெடிகோர் கேட்வே", welcomeTitle: "வரவேற்பு!", welcomeSubtitle: "தேர்வு செய்யவும்.", tabPatient: "உள்நுழைக", tabAdmin: "அதிகாரி", labelPatientId: "நோயாளி ஐடி", phPatientId: "KANIKA", btnPassword: "கடவுச்சொல்", btnOtp: "OTP", phPassword: "••••••••", phOtp: "OTP உள்ளிடவும்", btnSignIn: "உள்நுழைக", labelOfficerId: "அதிகாரி ஐடி", phOfficerId: "RICHARD", labelAuthCode: "குறியீடு", forgotCode: "மறந்துவிட்டதா?", btnAccessAdmin: "அணுகவும்", headerTitle: "மெடிகோர் போர்டல்", headerSubtitle: "தொகுப்பு", btnSignOut: "வெளியேறு", navHome: "முகப்பு", navActivity: "செயல்பாடு", navQA: "கேள்வி-பதில்", navDiary: "டைரி", navPerformance: "செயல்திறன்", navTalk: "பேசவும்", navPersonal: "தகவல்", patientHeroTitle: "🛡️ பாதுகாப்பான இடம்", patientHeroSub: "\"பாதுகாப்பாக உள்ளீர்கள்.\"", quietCheckinTitle: "📝 செக்-இன்", quietCheckinDesc: "தனிப்பட்ட பதிவு.", startCheckin: "தொடங்கவும்", smallStepsHeader: "🌱 5 அடிகள்", step1: "தண்ணீர்", step2: "நடை", step3: "நீட்சி", step4: "மகிழ்ச்சி", step5: "சுத்த காற்று", calmingHeader: "🧘 அமைதி", groundingEx: "பயிற்சி", breathingEx: "மூச்சுப் பயிற்சி", audioEx: "ஆடியோ", milestonesHeader: "🌟 சாதனைகள்", milestonesSub: "பதிவேற்றவும்!", phMilestone: "முடிந்தது", btnSubmitReview: "சமர்ப்பிக்கவும்", messageForYou: "செய்தி", messageBody: "நீங்கள் பாதுகாப்பாக உள்ளீர்கள்.", companionSummary: "💬 சுருக்கம்", companionDesc: "பாதுகாப்பாக சேமிக்கப்படுகிறது.", interactionLabel: "உரையாடல்", excellentEngagement: "ஈடுபாடு!", healthScoreHeader: "🔋 மதிப்பெண்", todayLabel: "இன்று", pastWeekHeader: "📊 பகுப்பாய்வு", todayQAHeader: "📝 கலந்துரையாடல்", clearChat: "அழிக்கவும்", qaDesc: "பாதுகாக்கப்பட்டது.", diaryHeader: "📖 டைரி", diaryDesc: "சுதந்திர இடம்.", phDiary: "அன்பு டைரி...", saveEntry: "சேமிக்கவும்", achievementsHeader: "🏆 சாதனைகள்", achieve1: "தியானம்", achieve2: "செக்-இன்", weeklyMilestonesHeader: "📅 மைல்கற்கள்", weekMile1: "அமர்வுகள்", weekMile2: "பதிவு", yearlyProgressHeader: "📈 முன்னேற்றம்", consultantsHeader: "💬 ஆலோசகர்கள்", consultantsDesc: "பேசவும்.", chatNow: "பேசவும்", personalInfoHeader: "👤 தகவல்", editProfile: "திருத்தவும்", piFullName: "பெயர்", piAddress: "முகவரி", piPhone: "எண்", piEmergencyContact: "தொடர்பு", piNotes: "குறிப்பு", emaiCloud: "வணக்கம் ☁️", btnSend: "அனுப்பு", adminWelcome: "வருக ", adminSub: "மேலாண்மை.", adminCasesHeader: "📁 வழக்குகள் (10)", adminMilestonesHeader: "🌟 சரிபார்ப்பு", adminQuickActions: "⚖️ நடவடிக்கை", adminWellbeing: "📊 அறிக்கைகள்" },
            ur: { badgeGateway: "میڈی کور گیٹ وے", welcomeTitle: "خوش آمدید!", welcomeSubtitle: "پورٹل منتخب کریں۔", tabPatient: "لاگ ان", tabAdmin: "آفیسر", labelPatientId: "مریض ID", phPatientId: "KANIKA", btnPassword: "پاس ورڈ", btnOtp: "او ٹی پی", phPassword: "••••••••", phOtp: "OTP درج کریں", btnSignIn: "سائن ان", labelOfficerId: "آفیسر ID", phOfficerId: "RICHARD", labelAuthCode: "کوڈ", forgotCode: "بھول گئے؟", btnAccessAdmin: "کنسول", headerTitle: "میڈی کور پورٹل", headerSubtitle: "سسٹم", btnSignOut: "سائن آؤٹ", navHome: "ہوم", navActivity: "سرگرمی", navQA: "سوال و جواب", navDiary: "ڈائری", navPerformance: "کارکردگی", navTalk: "بات کریں", navPersonal: "معلومات", patientHeroTitle: "🛡️ محفوظ جگہ", patientHeroSub: "\"آپ محفوظ ہیں۔\"", quietCheckinTitle: "📝 جائزہ", quietCheckinDesc: "نجی جائزہ۔", startCheckin: "شروع کریں", smallStepsHeader: "🌱 5 اقدامات", step1: "پانی", step2: "واک", step3: "ورزش", step4: "شکر", step5: "تازہ ہوا", calmingHeader: "🧘 سکون", groundingEx: "مشقیں", breathingEx: "سانس کی مشق", audioEx: "آڈیو", milestonesHeader: "🌟 منزلیں", milestonesSub: "ثبوت اپ لوڈ کریں!", phMilestone: "مکمل", btnSubmitReview: "بھیجیں", messageForYou: "پیغام", messageBody: "آپ محفوظ ہیں۔", companionSummary: "💬 خلاصہ", companionDesc: "محفوظ گفتگو۔", interactionLabel: "گفتگو", excellentEngagement: "رابطہ!", healthScoreHeader: "🔋 اسکور", todayLabel: "آج", pastWeekHeader: "📊 تجزیہ", todayQAHeader: "📝 سوالات", clearChat: "صاف کریں", qaDesc: "محفوظ ہے۔", diaryHeader: "📖 ڈائری", diaryDesc: "کھلی جگہ۔", phDiary: "پیاری ڈائری...", saveEntry: "محفوظ کریں", achievementsHeader: "🏆 کامیابیاں", achieve1: "مراقبہ", achieve2: "جائزہ", weeklyMilestonesHeader: "📅 سنگ میل", weekMile1: "سیشن", weekMile2: "درج", yearlyProgressHeader: "📈 پیش رفت", consultantsHeader: "💬 ماہرین", consultantsDesc: "رابطہ کریں۔", chatNow: "بات کریں", personalInfoHeader: "👤 معلومات", editProfile: "تبدیل کریں", piFullName: "نام", piAddress: "پتہ", piPhone: "فون", piEmergencyContact: "رابطہ", piNotes: "نوٹس", emaiCloud: "ہیلو ☁️", btnSend: "بھیجیں", adminWelcome: "خوش آمدید ", adminSub: "کمانڈ۔", adminCasesHeader: "📁 کیسز (10)", adminMilestonesHeader: "🌟 تصدیق", adminQuickActions: "⚖️ اقدامات", adminWellbeing: "📊 رپورٹس" },
            mr: { badgeGateway: "मेडीकोर गेटवे", welcomeTitle: "स्वागत आहे!", welcomeSubtitle: "पोर्टल निवडा.", tabPatient: "लॉगिन", tabAdmin: "अधिकारी", labelPatientId: "रुग्ण आयडी", phPatientId: "KANIKA", btnPassword: "पासवर्ड", btnOtp: "OTP", phPassword: "••••••••", phOtp: "OTP टाका", btnSignIn: "साइन इन", labelOfficerId: "अधिकारी आयडी", phOfficerId: "RICHARD", labelAuthCode: "कोड", forgotCode: "विसरलात?", btnAccessAdmin: "कन्सोल", headerTitle: "मेडीकोर पोर्टल", headerSubtitle: "सुट", btnSignOut: "साइन आउट", navHome: "होम", navActivity: "हालचाली", navQA: "प्रश्नोत्तरे", navDiary: "डायरी", navPerformance: "कामगिरी", navTalk: "बोला", navPersonal: "माहिती", patientHeroTitle: "🛡️ सुरक्षित जागा", patientHeroSub: "\"सुरक्षित रहा.\"", quietCheckinTitle: "📝 चेक-इन", quietCheckinDesc: "खाजगी नोंद.", startCheckin: "सुरू करा", smallStepsHeader: "🌱 5 पावले", step1: "पाणी", step2: "चालणे", step3: "ताणणे", step4: "नोंद", step5: "हवा", calmingHeader: "🧘 शांतता", groundingEx: "व्यायाम", breathingEx: "श्वसन व्यायाम", audioEx: "ऑडिओ", milestonesHeader: "🌟 टप्पे", milestonesSub: "अपलोड करा!", phMilestone: "पूर्ण", btnSubmitReview: "सबमिट करा", messageForYou: "संदेश", messageBody: "तुम्ही सुरक्षित आहात.", companionSummary: "💬 सारांश", companionDesc: "सुरक्षित संभाषण.", interactionLabel: "संवाद", excellentEngagement: "सहभाग!", healthScoreHeader: "🔋 गुण", todayLabel: "आज", pastWeekHeader: "📊 विश्लेषण", todayQAHeader: "📝 प्रश्न", clearChat: "साफ करा", qaDesc: "जतन केले.", diaryHeader: "📖 डायरी", diaryDesc: "मोकळी जागा.", phDiary: "प्रिय डायरी...", saveEntry: "जतन करा", achievementsHeader: "🏆 यश", achieve1: "ध्यान", achieve2: "चेक-इन", weeklyMilestonesHeader: "📅 टप्पे", weekMile1: "सत्रे", weekMile2: "नोंद", yearlyProgressHeader: "📈 प्रगती", consultantsHeader: "💬 तज्ञ", consultantsDesc: "बोला.", chatNow: "बोला", personalInfoHeader: "👤 माहिती", editProfile: "बदला", piFullName: "नाव", piAddress: "पत्ता", piPhone: "फोन", piEmergencyContact: "संपर्क", piNotes: "टिपा", emaiCloud: "नमस्कार ☁️", btnSend: "पाठवा", adminWelcome: "स्वागत ", adminSub: "व्यवस्थापन.", adminCasesHeader: "📁 केसेस (10)", adminMilestonesHeader: "🌟 पडताळणी", adminQuickActions: "⚖️ कृती", adminWellbeing: "📊 अहवाल" },
            bn: { badgeGateway: "মেডিকোর গেটওয়ে", welcomeTitle: "স্বাগতম!", welcomeSubtitle: "পোর্টাল বাছুন।", tabPatient: "লগইন", tabAdmin: "অফিসার", labelPatientId: "রোগীর আইডি", phPatientId: "KANIKA", btnPassword: "পাসওয়ার্ড", btnOtp: "OTP", phPassword: "••••••••", phOtp: "OTP দিন", btnSignIn: "সাইন ইন", labelOfficerId: "অফিসার আইডি", phOfficerId: "RICHARD", labelAuthCode: "কোড", forgotCode: "ভুলে গেছেন?", btnAccessAdmin: "কনসোল", headerTitle: "মেডিকোর পোর্টাল", headerSubtitle: "স্যুট", btnSignOut: "সাইন আউট", navHome: "হোম", navActivity: "কার্যক্রম", navQA: "প্রশ্নোত্তর", navDiary: "ডায়েরি", navPerformance: "অগ্রগতি", navTalk: "কথা বলুন", navPersonal: "তথ্য", patientHeroTitle: "🛡️ নিরাপদ আশ্রয়", patientHeroSub: "\"আপনি নিরাপদ।\"", quietCheckinTitle: "📝 চেক-ইন", quietCheckinDesc: "ব্যক্তিগত চেক-ইন।", startCheckin: "শুরু করুন", smallStepsHeader: "🌱 ৫টি পদক্ষেপ", step1: "জল", step2: "হাঁটা", step3: "ব্যায়াম", step4: "কৃতজ্ঞতা", step5: "বাতাস", calmingHeader: "🧘 শান্তি", groundingEx: "অনুশীলন", breathingEx: "শ্বাস-প্রশ্বাস", audioEx: "অডিও", milestonesHeader: "🌟 মাইলফলক", milestonesSub: "আপলোড করুন!", phMilestone: "সম্পন্ন", btnSubmitReview: "জমা দিন", messageForYou: "বার্তা", messageBody: "আপনি নিরাপদ।", companionSummary: "💬 সারসংক্ষেপ", companionDesc: "বার্তা সুরক্ষিত।", interactionLabel: "কথোপকথন", excellentEngagement: "যোগাযোগ!", healthScoreHeader: "🔋 স্কোর", todayLabel: "আজ", pastWeekHeader: "📊 বিশ্লেষণ", todayQAHeader: "📝 প্রশ্নোত্তর", clearChat: "মুছুন", qaDesc: "সংরক্ষিত।", diaryHeader: "📖 ডায়েরি", diaryDesc: "মুক্ত স্থান।", phDiary: "প্রিয় ডায়েরি...", saveEntry: "সংরক্ষণ", achievementsHeader: "🏆 অর্জন", achieve1: "ধ্যান", achieve2: "চেক-ইন", weeklyMilestonesHeader: "📅 মাইলফলক", weekMile1: "সেশন", weekMile2: "লিপিবদ্ধ", yearlyProgressHeader: "📈 অগ্রগতি", consultantsHeader: "💬 বিশেষজ্ঞ", consultantsDesc: "কথা বলুন।", chatNow: "কথা বলুন", personalInfoHeader: "👤 তথ্য", editProfile: "পরিবর্তন", piFullName: "নাম", piAddress: "ঠিকানা", piPhone: "ফোন", piEmergencyContact: "যোগাযোগ", piNotes: "নোট", emaiCloud: "নমস্কার ☁️", btnSend: "পাঠান", adminWelcome: "স্বাগতম ", adminSub: "ম্যানেজমেন্ট।", adminCasesHeader: "📁 কেস (১০)", adminMilestonesHeader: "🌟 যাচাই", adminQuickActions: "⚖️ পদক্ষেপ", adminWellbeing: "📊 রিপোর্ট" }
        };

        function applyTranslations(lang) {
            const data = TRANSLATIONS[lang] || TRANSLATIONS['en'];
            document.documentElement.setAttribute('dir', lang === 'ur' ? 'rtl' : 'ltr');

            document.querySelectorAll('[data-i18n]').forEach(el => {
                const key = el.getAttribute('data-i18n');
                if (data[key]) el.textContent = data[key];
            });

            document.querySelectorAll('[data-i18n-placeholder]').forEach(el => {
                const key = el.getAttribute('data-i18n-placeholder');
                if (data[key]) el.placeholder = data[key];
            });

            const langSelect = document.getElementById('site-lang-select');
            if (langSelect && langSelect.value !== lang) {
                langSelect.value = lang;
            }
        }

        function changeLanguage(lang) {
            localStorage.setItem('medicore_lang', lang);
            applyTranslations(lang);
        }

        (function initLanguage() {
            const savedLang = localStorage.getItem('medicore_lang') || 'en';
            applyTranslations(savedLang);
        })();

        // ADDED MINAKSHI VERMA & TANMAY SINGH ACCOUNTS
        const ACCOUNTS = {
            'richard': { id: 'RICHARD', name: 'Richard', role: 'admin', displayName: 'Officer Richard', displayRole: 'Investigating Officer', logoText: 'OR' },
            'minakshi': { id: 'MINAKSHI', name: 'Minakshi', role: 'admin', displayName: 'Officer Minakshi Verma', displayRole: 'Investigating Officer', logoText: 'MV' },
            'tanmay': { id: 'TANMAY', name: 'Tanmay', role: 'superadmin', displayName: 'Administrator Tanmay Singh', displayRole: 'System Administrator', logoText: 'TS' },
            'kanika': { id: 'KANIKA', name: 'Kanika', role: 'patient', displayName: 'Kanika Jha', displayRole: 'Safe Space Resident', logoText: 'KJ' }
        };

        function switchLoginTab(type) {
            document.querySelectorAll('.login-tab-btn').forEach(btn => btn.classList.remove('active'));
            document.querySelectorAll('.login-form').forEach(form => form.classList.remove('active'));
            document.getElementById(`tab-${type}-login`).classList.add('active');
            document.getElementById(`form-${type}`).classList.add('active');
            document.getElementById('login-error-box').classList.remove('active');
        }

        function toggleAuthType(type) {
            document.querySelectorAll('.otp-btn').forEach(btn => btn.classList.remove('active'));
            document.getElementById(`btn-auth-${type}`).classList.add('active');
            if (type === 'pass') {
                document.getElementById('input-group-pass').style.display = 'flex'; document.getElementById('input-group-otp').style.display = 'none';
            } else {
                document.getElementById('input-group-pass').style.display = 'none'; document.getElementById('input-group-otp').style.display = 'flex';
            }
        }

        function handleUnifiedLogin(event, roleCheck) {
            event.preventDefault();
            const isPatient = roleCheck === 'kanika';
            const enteredUser = document.getElementById(isPatient ? 'login-user-patient' : 'login-user-admin').value.trim().toUpperCase();
            const enteredPass = document.getElementById(isPatient ? 'login-pass-patient' : 'login-pass-admin').value;

            // --- TRAUMA-INFORMED FEATURE: DURESS PIN / DECOY DISTRESS TRIGGER ---
            if (isPatient && enteredPass === '0000') {
                localStorage.setItem('medicore_sos', 'active');
                document.getElementById('screen-login').classList.remove('active');
                document.getElementById('camouflage-screen').classList.add('active');
                document.querySelector('#camouflage-screen h2').textContent = "My Personal Recipe & Grocery Notes";
                document.querySelector('#camouflage-screen p').innerHTML = "<strong>Weekly Meal Plan:</strong><br>- Almond milk, organic spinach, oats, green tea, whole wheat bread.<br><em>[Duress signal transmitted silently to authorities.]</em>";
                return;
            }

            let isValid = false; let account = null;

            if (isPatient && enteredUser === 'KANIKA') {
                isValid = true; account = ACCOUNTS['kanika'];
                localStorage.removeItem('medicore_sos'); // Clear SOS on a normal, safe login
            } else if (!isPatient && (enteredUser === 'RICHARD' || enteredUser === 'MINAKSHI' || enteredUser === 'TANMAY')) {
                const pass = document.getElementById('login-pass-admin').value;
                if (pass === '1234567') {
                    isValid = true;
                    account = ACCOUNTS[enteredUser.toLowerCase()];
                }
            }

            if (isValid) openRoleDashboard(account);
            else {
                document.getElementById('login-error-box').classList.add('active');
                document.getElementById('login-error-message').textContent = "Invalid Credentials or Auth Code.";
            }
        }

        function openRoleDashboard(account) {
            document.getElementById('header-logo-icon').textContent = account.logoText;
            document.getElementById('header-avatar-badge').textContent = account.name.charAt(0);
            document.getElementById('header-username-display').textContent = account.displayName;
            document.getElementById('header-role-display').textContent = account.displayRole;
            document.body.classList.remove('login-active');

            if (account.role === 'admin') {
                document.body.classList.add('admin-theme');
                document.getElementById('view-superadmin').style.display = 'none';
                document.getElementById('view-admin').style.display = 'flex';
                document.getElementById('view-patient').style.display = 'none';
                document.getElementById('menu-btn').style.display = 'none';
                document.getElementById('emai-container').style.display = 'none';
                document.getElementById('btn-patient-emergency').style.display = 'none';
                document.getElementById('admin-welcome-msg').innerHTML = `Welcome back, ${account.displayName} 🛡️`;
                renderAdminCheckins();
                setTimeout(initOfficerTraumaChart, 200);
            } else if (account.role === 'superadmin') {
                document.body.className = '';
                document.body.classList.add('superadmin-theme');
                document.getElementById('view-superadmin').style.display = 'flex';
                document.getElementById('view-admin').style.display = 'none';
                document.getElementById('view-patient').style.display = 'none';
                document.getElementById('menu-btn').style.display = 'none';
                document.getElementById('emai-container').style.display = 'none';
                document.getElementById('btn-patient-emergency').style.display = 'none';
                renderSuperadminCases();
            } else {
                document.body.classList.remove('admin-theme');
                document.body.classList.remove('superadmin-theme');
                document.getElementById('view-superadmin').style.display = 'none';
                document.getElementById('view-admin').style.display = 'none';
                document.getElementById('view-patient').style.display = 'flex';
                document.getElementById('menu-btn').style.display = 'flex';
                document.getElementById('emai-container').style.display = 'flex';
                document.getElementById('btn-patient-emergency').style.display = 'flex';

                generateYearlyGraph(); initEmai(); renderStoredQA(); renderDiary();
            }
            document.getElementById('screen-login').classList.remove('active');
            document.getElementById('screen-dashboard').classList.add('active');

            const currentLang = localStorage.getItem('medicore_lang') || 'en';
            applyTranslations(currentLang);

            if (account.role === 'patient') {
                setTimeout(() => {
                    document.getElementById('activity-gauge-fill').style.transform = 'rotate(108deg)';
                    document.getElementById('activity-gauge-score').textContent = '85%';
                    document.getElementById('health-dyn-bar').style.width = '85%';
                    animateWeeklyGraph();
                }, 300);
            }
        }

        function handleLogout() {
            window.speechSynthesis.cancel();
            if (PatientTelemetry.audioStream) {
                PatientTelemetry.audioStream.getTracks().forEach(t => t.stop());
            }
            localStorage.removeItem('medicore_lang');
            document.body.className = 'login-active';
            window.location.reload();
        }

        function toggleSidebar() { document.getElementById('patient-sidebar').classList.toggle('active'); document.getElementById('sidebar-overlay').classList.toggle('active'); }
        function switchPatientTab(tabId, btnElement) {
            document.querySelectorAll('.patient-tab-content').forEach(el => el.classList.remove('active'));
            document.querySelectorAll('.sidebar-nav .tab-link').forEach(el => el.classList.remove('active'));
            document.getElementById('patient-tab-' + tabId).classList.add('active');
            btnElement.classList.add('active');
            if (tabId === 'activity') {
                document.getElementById('activity-gauge-fill').style.transform = 'rotate(-45deg)';
                setTimeout(() => { document.getElementById('activity-gauge-fill').style.transform = 'rotate(108deg)'; }, 50);
            }
            if (window.innerWidth <= 768) toggleSidebar();
        }

        function animateWeeklyGraph() {
            const h = [60, 75, 65, 80, 90, 70, 85]; const d = ['M', 'T', 'W', 'T', 'F', 'S', 'S'];
            const container = document.getElementById('weekly-graph-container'); container.innerHTML = '';
            h.forEach((val, i) => {
                let color = val >= 85 ? 'var(--btn-primary)' : 'var(--btn-secondary)';
                container.innerHTML += `<div class="graph-bar-wrapper"><div class="graph-bar" style="background:${color};"></div><span style="font-size:0.7rem; color:var(--text-dim);">${d[i]}</span></div>`;
            });
            setTimeout(() => { container.querySelectorAll('.graph-bar').forEach((bar, i) => { bar.style.height = h[i] + '%'; }); }, 100);
        }

        function generateYearlyGraph() {
            const container = document.getElementById('yearly-graph-container'); if (!container) return;
            container.innerHTML = '';
            for (let i = 0; i < 52; i++) {
                let height = Math.floor(Math.random() * 70) + 20;
                let bar = document.createElement('div'); bar.className = 'yearly-bar'; container.appendChild(bar);
                setTimeout(() => { bar.style.height = height + '%'; }, 100 + (i * 10));
            }
        }

        let currentAdminCaseFilter = 'all';

        function setCaseFilter(filterType, btnElem) {
            currentAdminCaseFilter = filterType;
            document.querySelectorAll('.table-filter-chips .filter-chip').forEach(b => b.classList.remove('active'));
            if (btnElem) btnElem.classList.add('active');
            filterAdminCases();
        }

        function filterAdminCases() {
            const query = (document.getElementById('admin-case-search')?.value || '').toLowerCase().trim();
            const typeFilter = document.getElementById('admin-case-type-filter')?.value || 'all';
            const rows = document.querySelectorAll('#admin-cases-table tbody tr');
            let visibleCount = 0;

            rows.forEach(row => {
                const status = row.getAttribute('data-status');
                const name = row.getAttribute('data-name');
                const id = row.getAttribute('data-id');
                const caseType = row.getAttribute('data-type');

                const matchesStatus = currentAdminCaseFilter === 'all' || status === currentAdminCaseFilter;
                const matchesType = typeFilter === 'all' || caseType === typeFilter;
                const matchesQuery = !query || name.includes(query) || id.includes(query);

                if (matchesStatus && matchesType && matchesQuery) {
                    row.style.display = '';
                    visibleCount++;
                } else {
                    row.style.display = 'none';
                }
            });

            const counter = document.getElementById('admin-table-counter');
            if (counter) counter.textContent = `Showing ${visibleCount} of ${rows.length} records`;
        }

        function triggerEmergency() {
            localStorage.setItem('medicore_sos', 'active'); localStorage.setItem('medicore_sos_time', Date.now());
            document.getElementById('sos-countdown-container').classList.add('active');
            document.getElementById('sos-modal-title').textContent = "EMERGENCY SIGNAL SENT";
            document.getElementById('sos-modal-desc').textContent = "A high-priority alert has been dispatched to authorities and the rapid response team. Help is on the way.";

            let time = 600;
            setInterval(() => {
                time--; let m = Math.floor(time / 60).toString().padStart(2, '0'); let s = (time % 60).toString().padStart(2, '0');
                document.getElementById('sos-timer').textContent = `${m}:${s}`;
            }, 1000);
        }

        function triggerAutoCallingEmergency() {
            localStorage.setItem('medicore_sos', 'active'); localStorage.setItem('medicore_sos_time', Date.now());
            document.getElementById('sos-countdown-container').classList.add('active');
            document.getElementById('sos-modal-title').textContent = "AUTOMATIC EMERGENCY CALL INITIATED";
            document.getElementById('sos-modal-desc').textContent = "Critical risk detected. An automatic call to the on-call psychiatrist and authorities has been triggered.";

            let time = 600;
            setInterval(() => {
                time--; let m = Math.floor(time / 60).toString().padStart(2, '0'); let s = (time % 60).toString().padStart(2, '0');
                document.getElementById('sos-timer').textContent = `${m}:${s}`;
            }, 1000);
        }

        function clearSOS() {
            localStorage.removeItem('medicore_sos');
            document.body.classList.remove('admin-emergency-theme');
            document.body.classList.add('admin-theme');
            document.getElementById('admin-sos-banner').style.display = 'none';
            document.getElementById('admin-case-file-modal').classList.remove('active');
            alert('SOS Alert Cleared. System returning to normal state.');
        }

        // --- NEW CASE REGISTRATION SUBMISSION ---
        function submitNewCase(e) {
            e.preventDefault();
            const name = document.getElementById('nc-name').value;
            const type = document.getElementById('nc-type').value;
            const prio = document.getElementById('nc-priority').value;
            const details = document.getElementById('nc-details').value;

            const newCases = JSON.parse(localStorage.getItem('medicore_pending_cases') || '[]');
            newCases.push({
                id: '#FIR-NEW-' + Math.floor(Math.random() * 9000 + 1000),
                name,
                type,
                priority: prio,
                date: new Date().toLocaleDateString(),
                details
            });
            localStorage.setItem('medicore_pending_cases', JSON.stringify(newCases));

            alert("Case successfully registered and forwarded to Administrator Tanmay Singh for assignment.");
            document.getElementById('register-case-modal').classList.remove('active');
            e.target.reset();

            if (document.getElementById('view-superadmin').style.display === 'flex') {
                renderSuperadminCases();
            }
        }

        function renderSuperadminCases() {
            const container = document.getElementById('superadmin-pending-cases');
            const newCases = JSON.parse(localStorage.getItem('medicore_pending_cases') || '[]');
            if (newCases.length === 0) {
                container.innerHTML = `<p style="padding:1rem; color:var(--text-dim); text-align:center;">No pending cases in queue.</p>`;
                return;
            }
            container.innerHTML = newCases.map((c, i) => `
                <div style="background:var(--surface-input); border:1px solid var(--border-subtle); padding:1rem; border-radius:var(--radius-sm); margin-bottom:0.5rem; display:flex; justify-content:space-between; align-items:center;">
                    <div>
                        <strong style="color:var(--text-primary);">${c.name} (${c.id})</strong><br>
                        <span style="font-size:0.8rem; color:var(--text-secondary);">Type: ${c.type} | Priority: ${c.priority}</span>
                    </div>
                    <button style="background:var(--btn-primary); color:white; border:none; padding:6px 12px; border-radius:4px; font-weight:bold; cursor:pointer;" onclick="alert('Assigning to available officers...')">Assign</button>
                </div>
            `).join('');
        }

        // --- HACKATHON LIVE JUDGE SIMULATOR ---
        function triggerJudgeSimulation() {
            localStorage.setItem('medicore_sos', 'active');
            const simLog = [
                { timestamp: new Date().toLocaleTimeString(), detail: "SIMULATION: Geo-fence perimeter breach detected for #FIR-2026-993-A." },
                { timestamp: new Date().toLocaleTimeString(), detail: "SIMULATION: Sensor fusion override triggered (High typing hesitation & voice tremor)." }
            ];
            localStorage.setItem('medicore_telemetry_logs', JSON.stringify(simLog));
            alert("🧪 Live Demo Scenario Triggered: Geo-fence breach and SOS dispatch simulated successfully! Switch to Admin Officer view (RICHARD, MINAKSHI, or TANMAY) to see live emergency alerts.");
        }

        // --- LEGAL PDF DOSSIER EXPORT ---
        function exportLegalDossier() {
            const reportText = `--- OFFICERS CERTIFIED LEGAL DOSSIER ---\nCase ID: ${currentOpenCase.id}\nVictim: ${currentOpenCase.name}\nCase Type: ${currentOpenCase.type}\nJurisdiction: Central District\nStatus: ACTIVE / EMERGENCY WATCH\nLatest Mental Health / CTI Risk: ${currentOpenCase.risk}%\nTelemetry Analysis: High CTI & Sensor Fusion Masking Detected.\nCertified Secure by MediCore Zero-Knowledge Vault.`;
            const blob = new Blob([reportText], { type: 'text/plain' });
            const url = URL.createObjectURL(blob);
            const a = document.createElement('a');
            a.href = url;
            a.download = `MediCore_Legal_Dossier_${currentOpenCase.id}.txt`;
            a.click();
        }

        // =======================================================
        // ADVANCED DYNAMIC PREDICTIVE ENGINE & SURVIVOR TOOLS
        // =======================================================
        const PatientTelemetry = {
            acoustic: { tremorScore: 0, pauseDurationMs: 0, pitchInstability: 'Normal' },
            nlp: { riskScore: 0, flags: [], threatPerceived: false },
            behavioral: { idleSeconds: 0, suddenWithdrawal: false, lastInteractionTime: Date.now() },

            audioCtx: null,
            analyser: null,
            audioStream: null,
            silenceStart: null,

            keystrokeTimestamps: [],
            lastKeypressTime: Date.now(),
            historicalCTI: 48,

            initTypingWatchdog() {
                const inputElem = document.getElementById('emai-input');
                if (!inputElem) return;

                inputElem.addEventListener('keydown', (e) => {
                    let now = Date.now();
                    let delay = now - this.lastKeypressTime;
                    this.keystrokeTimestamps.push(delay);
                    if (this.keystrokeTimestamps.length > 20) this.keystrokeTimestamps.shift();
                    this.lastKeypressTime = now;

                    if (delay > 1500) {
                        this.triggerFreezeStateAlert("Dissociation / Freeze State Detected: Abnormally long typing hesitation (>1.5s).");
                    }
                });
            },

            async initAcousticStream(mediaStream) {
                try {
                    this.audioStream = mediaStream;
                    if (!this.audioCtx) {
                        this.audioCtx = new (window.AudioContext || window.webkitAudioContext)();
                    }
                    const source = this.audioCtx.createMediaStreamSource(mediaStream);
                    this.analyser = this.audioCtx.createAnalyser();
                    this.analyser.fftSize = 512;
                    source.connect(this.analyser);

                    const bufferLength = this.analyser.frequencyBinCount;
                    const dataArray = new Uint8Array(bufferLength);

                    const checkAcoustics = () => {
                        if (!isVoiceListening) return;
                        this.analyser.getByteFrequencyData(dataArray);

                        let sum = 0;
                        for (let i = 0; i < bufferLength; i++) { sum += dataArray[i] * dataArray[i]; }
                        const rms = Math.sqrt(sum / bufferLength);

                        if (rms < 10) {
                            if (!this.silenceStart) this.silenceStart = Date.now();
                            this.acoustic.pauseDurationMs = Date.now() - this.silenceStart;
                        } else {
                            this.silenceStart = null;
                        }

                        let highBandEnergy = 0;
                        for (let i = 140; i < 240; i++) highBandEnergy += dataArray[i];
                        const jitterRatio = highBandEnergy / (sum + 1);

                        if (jitterRatio > 0.16 || this.acoustic.pauseDurationMs > 3500) {
                            this.acoustic.pitchInstability = 'Elevated Vocal Tremor / Hesitation';
                            this.acoustic.tremorScore = Math.min(100, Math.round(jitterRatio * 380));
                        } else {
                            this.acoustic.pitchInstability = 'Normal';
                            this.acoustic.tremorScore = Math.max(0, Math.round(jitterRatio * 150));
                        }
                        requestAnimationFrame(checkAcoustics);
                    };
                    checkAcoustics();
                } catch (err) {
                    console.warn("Acoustic audio analyzer initialization warning", err);
                }
            },

            evaluateSensorFusion(textSentimentScore, acousticJitterScore, avgTypingDelay) {
                const claimsToBeFine = textSentimentScore > 0.5;
                const highStressMarkers = acousticJitterScore > 65 && avgTypingDelay > 1200;

                if (claimsToBeFine && highStressMarkers) {
                    this.triggerAcuteDistressAlert("Sensor Fusion Alert: Silent Masking Detected. High vocal tremor and typing delay despite positive text.");
                    return true;
                }
                return false;
            },

            updateCTI(sessionStressScore) {
                const alpha = 0.25;
                this.historicalCTI = (alpha * sessionStressScore) + ((1 - alpha) * this.historicalCTI);
                return Math.round(this.historicalCTI);
            },

            triggerFreezeStateAlert(msg) {
                console.warn(`[PREDICTIVE ENGINE - FREEZE STATE]: ${msg}`);
                this.logTelemetryEvent(msg);
            },

            triggerAcuteDistressAlert(msg) {
                console.error(`[PREDICTIVE ENGINE - SENSOR FUSION]: ${msg}`);
                this.logTelemetryEvent(msg);
            },

            evaluateSentiment(inputText) {
                const text = inputText.toLowerCase();
                const markers = {
                    hopelessness: ['give up', 'no point', 'cant take this', 'tired of living', 'nothing matters', 'all my fault', 'empty', 'helpless', 'fine', 'ok'],
                    fear: ['scared', 'terrified', 'shaking', 'hiding', 'panicking', 'nightmare', 'screaming', 'afraid'],
                    threat: ['he is here', 'outside', 'found me', 'watching', 'door', 'stalking', 'kill', 'hurt me', 'break in']
                };

                let detected = [];
                let score = 15;

                for (const [category, words] of Object.entries(markers)) {
                    words.forEach(w => {
                        if (text.includes(w)) {
                            detected.push(`${category.toUpperCase()}: "${w}"`);
                            score += category === 'threat' ? 45 : 20;
                        }
                    });
                }

                const avgDelay = this.keystrokeTimestamps.length > 0
                    ? this.keystrokeTimestamps.reduce((a, b) => a + b, 0) / this.keystrokeTimestamps.length
                    : 300;

                const sentimentIsPositive = !text.includes('sad') && !text.includes('help') && !text.includes('scared');
                this.evaluateSensorFusion(sentimentIsPositive ? 0.9 : 0.1, this.acoustic.tremorScore, avgDelay);

                this.nlp.riskScore = Math.min(100, score);
                this.nlp.flags = detected;
                this.nlp.threatPerceived = score >= 50;

                return this.nlp;
            },

            startBehavioralWatchdog() {
                const resetActivity = () => {
                    this.behavioral.lastInteractionTime = Date.now();
                    this.behavioral.idleSeconds = 0;
                    this.behavioral.suddenWithdrawal = false;
                };

                window.addEventListener('mousemove', resetActivity);
                window.addEventListener('keydown', resetActivity);
                window.addEventListener('touchstart', resetActivity);

                setInterval(() => {
                    const patientScreenActive = document.getElementById('view-patient')?.style.display === 'flex';
                    if (!patientScreenActive) return;

                    const elapsedSec = Math.floor((Date.now() - this.behavioral.lastInteractionTime) / 1000);
                    this.behavioral.idleSeconds = elapsedSec;

                    if (patientTurnCount > 0 && elapsedSec > 90 && !this.behavioral.suddenWithdrawal) {
                        this.behavioral.suddenWithdrawal = true;
                        this.logTelemetryEvent("DISSOCIATION WARNING: Zero screen interaction & sudden behavioral freeze detected (>90s).");
                    }
                }, 5000);
            },

            logTelemetryEvent(msg) {
                const telemetryLogs = JSON.parse(localStorage.getItem('medicore_telemetry_logs') || '[]');
                telemetryLogs.unshift({ timestamp: new Date().toLocaleTimeString(), detail: msg });
                localStorage.setItem('medicore_telemetry_logs', JSON.stringify(telemetryLogs.slice(0, 25)));

                // Update live telemetry ticker banner
                const ticker = document.getElementById('live-telemetry-ticker-text');
                if (ticker) ticker.textContent = `🚨 LIVE ALERT [${new Date().toLocaleTimeString()}]: ${msg}`;
            }
        };

        PatientTelemetry.startBehavioralWatchdog();
        setTimeout(() => PatientTelemetry.initTypingWatchdog(), 1000);

        // --- TRAUMA-INFORMED FEATURE: DYNAMIC SAFE ZONE & GEO-FENCE WATCHDOG ---
        const GeoFenceWatchdog = {
            safeZoneCenter: null,
            allowedRadiusKm: 1.5,

            initGeoFenceMonitor() {
                if (!navigator.geolocation) return;
                navigator.geolocation.watchPosition(
                    (position) => {
                        if (!this.safeZoneCenter) {
                            this.safeZoneCenter = { lat: position.coords.latitude, lng: position.coords.longitude };
                            return;
                        }
                        const distanceKm = this.calculateDistance(
                            position.coords.latitude, position.coords.longitude,
                            this.safeZoneCenter.lat, this.safeZoneCenter.lng
                        );
                        if (distanceKm > this.allowedRadiusKm) {
                            this.triggerGeofenceBreachAlert(distanceKm);
                        }
                    },
                    (error) => { console.warn("Geo-fence tracking inactive for demo environment:", error.message); },
                    { enableHighAccuracy: true, maximumAge: 10000, timeout: 5000 }
                );
            },

            calculateDistance(lat1, lon1, lat2, lon2) {
                const R = 6371;
                const dLat = (lat2 - lat1) * (Math.PI / 180);
                const dLon = (lon2 - lon1) * (Math.PI / 180);
                const a = Math.sin(dLat / 2) * Math.sin(dLat / 2) +
                    Math.cos(lat1 * (Math.PI / 180)) * Math.cos(lat2 * (Math.PI / 180)) *
                    Math.sin(dLon / 2) * Math.sin(dLon / 2);
                return R * (2 * Math.atan2(Math.sqrt(a), Math.sqrt(1 - a)));
            },

            triggerGeofenceBreachAlert(distance) {
                localStorage.setItem('medicore_sos', 'active');
                PatientTelemetry.logTelemetryEvent(`GEOFENCE BREACH: Resident moved outside safe perimeter (${distance.toFixed(2)}km away). Auto-alert dispatched.`);
            }
        };
        GeoFenceWatchdog.initGeoFenceMonitor();

        function initOfficerTraumaChart() {
            const canvas = document.getElementById('officerTraumaChart');
            if (!canvas) return;
            const ctx = canvas.getContext('2d');

            new Chart(ctx, {
                type: 'line',
                data: {
                    labels: ['Day 1', 'Day 5', 'Day 10', 'Day 15', 'Day 20', 'Day 25', 'Today'],
                    datasets: [
                        {
                            label: 'Trauma Trajectory (CTI Score)',
                            data: [68, 62, 59, 65, 54, 48, 52],
                            borderColor: '#F87171',
                            backgroundColor: 'rgba(248, 113, 113, 0.1)',
                            fill: true,
                            tension: 0.35
                        },
                        {
                            label: 'Expected Recovery Baseline',
                            data: [65, 58, 52, 45, 40, 35, 30],
                            borderColor: '#34D399',
                            borderDash: [6, 6],
                            tension: 0.35
                        }
                    ]
                },
                options: {
                    responsive: true,
                    maintainAspectRatio: false,
                    plugins: { legend: { labels: { color: '#F8FAFC' } } },
                    scales: {
                        x: { ticks: { color: '#94A3B8' }, grid: { color: 'rgba(255,255,255,0.05)' } },
                        y: { ticks: { color: '#94A3B8' }, grid: { color: 'rgba(255,255,255,0.05)' }, min: 0, max: 100 }
                    }
                }
            });
        }

        let currentOpenCase = { id: '', name: '', type: '', risk: '0' };

        function openAdminCaseFile(patientName, caseId, caseType) {
            const modal = document.getElementById('admin-case-file-modal');
            const respContainer = document.getElementById('admin-case-responses');
            document.getElementById('admin-case-victim-name').textContent = patientName;

            const isSOS = localStorage.getItem('medicore_sos') === 'active';
            document.getElementById('admin-case-modal-title').innerHTML = isSOS
                ? `🚨 EMERGENCY CASE FILE: ${caseId || '#FIR-2026-993-A'}`
                : `📁 CASE FILE: ${caseId || '#FIR-2026-993-A'}`;

            const rawStored = localStorage.getItem('medicore_emai_chats_enc');
            let emaiChats = [];
            if (rawStored) {
                try { emaiChats = JSON.parse(SecurityEngine.unmaskData(rawStored)); } catch (e) { emaiChats = []; }
            }

            let chatHtml = '';
            let caseRisk = 0;
            if (emaiChats.length > 0) {
                caseRisk = emaiChats[0].telemetry.riskScore;
                emaiChats.forEach(c => {
                    const telem = c.telemetry || { pitchInstability: 'Normal', sentimentFlags: ['Neutral / Regulated'], riskScore: 0 };
                    const riskColor = telem.riskScore >= 50 ? '#ef4444' : (telem.riskScore > 20 ? '#f59e0b' : '#10b981');

                    chatHtml += `
                    <div style="margin-bottom:12px; border-bottom:1px solid var(--border-subtle); padding-bottom:8px;">
                        <div style="display:flex; justify-content:space-between; font-size:0.78rem; color:var(--text-dim);">
                            <span>${c.date} ${c.time}</span>
                            <span style="color:${riskColor}; font-weight:bold;">Predictive Risk Index: ${telem.riskScore}/100</span>
                        </div>
                        <div style="margin: 4px 0;">
                            <strong style="color:var(--text-muted);">Patient:</strong> ${c.q}<br>
                            <strong style="color:var(--text-primary);">EMAI:</strong> ${c.a}
                        </div>
                        <div style="display:flex; gap:6px; flex-wrap:wrap; margin-top:6px; font-size:0.72rem;">
                            <span style="background:rgba(59,130,246,0.15); border:1px solid rgba(59,130,246,0.3); color:#93c5fd; padding:2px 6px; border-radius:4px;">
                                🎙️ Acoustic/Cadence: ${telem.pitchInstability}
                            </span>
                            <span style="background:rgba(239,68,68,0.12); border:1px solid rgba(239,68,68,0.3); color:#fca5a5; padding:2px 6px; border-radius:4px;">
                                🧠 Multi-Modal Markers: ${Array.isArray(telem.sentimentFlags) ? telem.sentimentFlags.join(', ') : 'Neutral'}
                            </span>
                        </div>
                    </div>`;
                });
            } else {
                chatHtml = '<p style="color:gray; font-size:0.9rem;">No recent AI conversations recorded.</p>';
                caseRisk = 48;
            }

            currentOpenCase = { id: caseId || '#FIR-2026-993-A', name: patientName, type: caseType || 'Rape', risk: caseRisk };

            respContainer.innerHTML = chatHtml;
            modal.classList.add('active');
        }

        setInterval(() => {
            if (document.getElementById('view-admin').style.display === 'flex' || document.getElementById('view-superadmin').style.display === 'flex') {
                if (localStorage.getItem('medicore_sos') === 'active') {
                    if (document.getElementById('view-admin').style.display === 'flex') {
                        document.body.classList.add('admin-emergency-theme'); document.body.classList.remove('admin-theme');
                    }
                    document.getElementById('admin-sos-banner').style.display = 'flex';
                } else {
                    if (document.getElementById('view-admin').style.display === 'flex') {
                        document.body.classList.remove('admin-emergency-theme'); document.body.classList.add('admin-theme');
                    }
                    document.getElementById('admin-sos-banner').style.display = 'none';
                }
            }
        }, 1000);

        function openPersonalInfoTab() { if (document.getElementById('view-patient').style.display === 'flex') switchPatientTab('personal', document.getElementById('btn-nav-personal')); }
        function openAudioModal() { document.getElementById('audio-modal-container').classList.add('active'); }
        function closeAudioModal() { document.getElementById('audio-modal-container').classList.remove('active'); }
        function openGroundingHub() { document.getElementById('grounding-hub-container').classList.add('active'); }
        function closeGroundingHub() { document.getElementById('grounding-hub-container').classList.remove('active'); }

        let breathTimer; let breathInterval; let timeLeft = 480;
        function openBreathingModal() {
            document.getElementById('breathing-modal-container').classList.add('active'); document.getElementById('breath-timer').textContent = "08:00";
            document.getElementById('breath-circle').style.transform = "scale(1)"; document.getElementById('btn-start-breath').style.display = 'inline-block'; timeLeft = 480;
        }
        function stopBreathing() { clearInterval(breathTimer); clearInterval(breathInterval); document.getElementById('breathing-modal-container').classList.remove('active'); }
        function startBreathing() {
            document.getElementById('btn-start-breath').style.display = 'none';
            breathTimer = setInterval(() => { timeLeft--; let m = Math.floor(timeLeft / 60).toString().padStart(2, '0'); let s = (timeLeft % 60).toString().padStart(2, '0'); document.getElementById('breath-timer').textContent = `${m}:${s}`; if (timeLeft <= 0) { stopBreathing(); alert("Breathing session complete."); } }, 1000);
            runBreathCycle(); breathInterval = setInterval(runBreathCycle, 19000);
        }
        function runBreathCycle() {
            const circle = document.getElementById('breath-circle'); const status = document.getElementById('breath-status-text');
            status.textContent = "Breathe in deeply..."; circle.textContent = "INHALE"; circle.style.transform = "scale(1.6)"; circle.style.transition = "transform 4s ease-out";
            setTimeout(() => { status.textContent = "Hold..."; circle.textContent = "HOLD"; circle.style.transition = "none"; }, 4000);
            setTimeout(() => { status.textContent = "Exhale slowly..."; circle.textContent = "EXHALE"; circle.style.transform = "scale(1)"; circle.style.transition = "transform 8s ease-in-out"; }, 11000);
        }

        let isEditingProfile = false;
        function toggleEditProfile() {
            const btn = document.getElementById('edit-profile-btn'); const editableInputs = document.querySelectorAll('#personal-info-form .user-editable');
            isEditingProfile = !isEditingProfile;
            if (isEditingProfile) { btn.textContent = "Save Profile"; btn.style.background = "white"; btn.style.color = "var(--header-bg)"; editableInputs.forEach(input => input.removeAttribute('readonly')); document.getElementById('pi-name').focus(); }
            else { btn.textContent = "Edit Profile"; btn.style.background = "var(--btn-primary)"; btn.style.color = "#04241F"; editableInputs.forEach(input => input.setAttribute('readonly', true)); }
        }

        function submitMilestone() {
            const name = document.getElementById('milestone-name').value; if (!name) return;
            document.getElementById('milestone-status-list').innerHTML += `<div style="padding:10px; background:rgba(245, 158, 11, 0.1); border:1px solid var(--alert-important); border-radius:8px; display:flex; justify-content:space-between;"><span style="color:white; font-size:0.9rem;">${name}</span><span style="color:var(--alert-important); font-size:0.8rem; font-weight:bold;">Pending Admin</span></div>`;
            document.getElementById('milestone-name').value = ''; document.getElementById('milestone-file').value = '';
        }

        function saveDiaryEntry() {
            const text = document.getElementById('diary-input').value.trim(); if (!text) return;
            const raw = localStorage.getItem('medicore_diary_enc');
            let entries = [];
            if (raw) {
                try { entries = JSON.parse(SecurityEngine.unmaskData(raw)); } catch (e) { entries = []; }
            }
            entries.unshift({ text: text, date: new Date().toLocaleDateString('en-US', { weekday: 'short', month: 'short', day: 'numeric', year: 'numeric' }), time: new Date().toLocaleTimeString([], { hour: '2-digit', minute: '2-digit' }) });
            localStorage.setItem('medicore_diary_enc', SecurityEngine.maskData(JSON.stringify(entries)));
            document.getElementById('diary-input').value = '';
            renderDiary();
        }

        function deleteDiaryEntry(index) {
            if (confirm('Delete this encrypted entry?')) {
                const raw = localStorage.getItem('medicore_diary_enc');
                let entries = [];
                if (raw) { try { entries = JSON.parse(SecurityEngine.unmaskData(raw)); } catch (e) { entries = []; } }
                entries.splice(index, 1);
                localStorage.setItem('medicore_diary_enc', SecurityEngine.maskData(JSON.stringify(entries)));
                renderDiary();
            }
        }

        function renderDiary() {
            const list = document.getElementById('diary-list');
            const raw = localStorage.getItem('medicore_diary_enc');
            let entries = [];
            if (raw) { try { entries = JSON.parse(SecurityEngine.unmaskData(raw)); } catch (e) { entries = []; } }
            if (entries.length === 0) { list.innerHTML = "<p style='color:gray;'>No diary entries recorded yet.</p>"; return; }
            list.innerHTML = entries.map((e, index) => `
                <div class="diary-entry-card" id="diary-entry-${index}">
                    <div style="display:flex; justify-content:space-between; margin-bottom:0.5rem;"><div style="font-size:0.8rem; color:var(--text-dim);">${e.date} at ${e.time}</div><div><button onclick="deleteDiaryEntry(${index})" style="background:none; border:none; color:var(--alert-emergency); cursor:pointer;">Delete</button></div></div>
                    <div id="diary-text-${index}" style="color:var(--text-primary); font-size:0.95rem; line-height:1.5; white-space: pre-wrap;">${e.text}</div>
                </div>`).join('');
        }

        // ==========================================
        // EMAI VOICE & SMART ADAPTIVE PIPELINE
        // ==========================================
        let emaiInitialized = false;
        let patientTurnCount = 0;
        const MAX_PATIENT_TURNS = 5;

        // Force browser to load voices 
        window.speechSynthesis.onvoiceschanged = () => { window.speechSynthesis.getVoices(); };

        const SpeechRecognition = window.SpeechRecognition || window.webkitSpeechRecognition;
        let voiceRecognizer = null;
        let isVoiceListening = false;

        if (SpeechRecognition) {
            voiceRecognizer = new SpeechRecognition();
            voiceRecognizer.continuous = false;
            voiceRecognizer.interimResults = false;
            voiceRecognizer.lang = 'en-US';

            voiceRecognizer.onresult = (event) => {
                const transcript = event.results[0][0].transcript;
                document.getElementById('emai-input').value = transcript;
                stopVoiceListening();
                handleEmaiAnswer();
            };
            voiceRecognizer.onerror = () => { stopVoiceListening(); };
            voiceRecognizer.onend = () => { stopVoiceListening(); };
        }

        async function toggleVoiceCompanion() {
            if (!voiceRecognizer) {
                alert("Speech Recognition is not supported in this browser. Please use Chrome or Edge.");
                return;
            }
            if (!isVoiceListening) {
                try {
                    const stream = await navigator.mediaDevices.getUserMedia({ audio: true });
                    PatientTelemetry.initAcousticStream(stream);
                    voiceRecognizer.start();
                    isVoiceListening = true;
                    document.getElementById('btn-voice-toggle').classList.add('listening');
                    document.getElementById('emai-voice-indicator').textContent = "🎙️ Listening & Scanning Acoustics... Speak gently";
                } catch (err) {
                    console.error("Mic start failed", err);
                }
            } else {
                stopVoiceListening();
            }
        }

        function stopVoiceListening() {
            isVoiceListening = false;
            const btn = document.getElementById('btn-voice-toggle');
            if (btn) btn.classList.remove('listening');
            const ind = document.getElementById('emai-voice-indicator');
            if (ind) ind.textContent = "Voice Ready • Click mic or type";
            if (voiceRecognizer) { try { voiceRecognizer.stop(); } catch (e) { } }
            if (PatientTelemetry.audioStream) {
                PatientTelemetry.audioStream.getTracks().forEach(t => t.stop());
            }
        }

        function speakText(text) {
            if (!('speechSynthesis' in window)) return;
            window.speechSynthesis.cancel();
            const cleanText = text.replace(/[^\w\s,.?!\'-]/gi, '');
            const utterance = new SpeechSynthesisUtterance(cleanText);

            utterance.rate = 0.94;
            utterance.pitch = 1.1;

            const voices = window.speechSynthesis.getVoices();
            const femaleVoice = voices.find(v =>
                v.name.includes('Female') ||
                v.name.includes('Samantha') ||
                v.name.includes('Zira') ||
                v.name.includes('Victoria') ||
                v.name.includes('Tessa')
            );

            if (femaleVoice) {
                utterance.voice = femaleVoice;
            }

            window.speechSynthesis.speak(utterance);
        }

        function toggleEmai() {
            const p = document.getElementById('emai-chat');
            p.classList.toggle('active');
            if (p.classList.contains('active')) document.getElementById('emai-input').focus();
        }

        function closeEmai() {
            window.speechSynthesis.cancel();
            stopVoiceListening();
            document.getElementById('emai-chat').classList.remove('active');
        }

        function initEmai() {
            if (emaiInitialized) return;
            document.getElementById('emai-chat-history').innerHTML = '';
            const welcomeMsg = "Hello Kanika. I'm EMAI, your safe space companion. You can speak or type to me anytime. How are you feeling today?";
            appendAiBubble(welcomeMsg);
            emaiInitialized = true;
        }

        function appendAiBubble(text) {
            const h = document.getElementById('emai-chat-history');
            h.innerHTML += `<div style="padding:0.8rem; border-radius:12px; background:rgba(16,185,129,0.15); border:1px solid rgba(16,185,129,0.3); align-self:flex-start; border-bottom-left-radius:0; max-width:85%; font-size:0.9rem; line-height:1.4;">${text}</div>`;
            h.scrollTop = h.scrollHeight;
            speakText(text);
        }

        function appendUserBubble(text) {
            const h = document.getElementById('emai-chat-history');
            h.innerHTML += `<div style="padding:0.8rem; border-radius:12px; background:var(--surface-input); border:1px solid var(--border-subtle); align-self:flex-end; border-bottom-right-radius:0; max-width:85%; font-size:0.9rem; line-height:1.4;">${text}</div>`;
            h.scrollTop = h.scrollHeight;
        }

        function handleEmaiAnswer() {
            const input = document.getElementById('emai-input');
            const userMsg = input.value.trim();
            if (!userMsg) return;

            appendUserBubble(userMsg);
            input.value = '';
            patientTurnCount++;

            const nlpResult = PatientTelemetry.evaluateSentiment(userMsg);
            const computedCTI = PatientTelemetry.updateCTI(nlpResult.riskScore);

            let response;
            if (nlpResult.threatPerceived) {
                response = "Kanika, our predictive sensors detect significant distress in your inputs. You are completely safe inside this protected facility. If you feel compromised or threatened, please tap the SOS button immediately so authorities can assist.";
                PatientTelemetry.logTelemetryEvent(`THREAT_FLAG: Detected ${nlpResult.flags.join(', ')} | CTI: ${computedCTI}`);
            } else {
                response = generateEmotionalAiReply(userMsg);
            }

            const raw = localStorage.getItem('medicore_emai_chats_enc');
            let existing = [];
            if (raw) {
                try { existing = JSON.parse(SecurityEngine.unmaskData(raw)); } catch (e) { existing = []; }
            }

            existing.unshift({
                q: userMsg,
                a: response,
                date: new Date().toLocaleDateString('en-US', { month: 'short', day: 'numeric', year: 'numeric' }),
                time: new Date().toLocaleTimeString([], { hour: '2-digit', minute: '2-digit' }),
                telemetry: {
                    pitchInstability: PatientTelemetry.acoustic.pitchInstability,
                    tremorIndex: PatientTelemetry.acoustic.tremorScore,
                    sentimentFlags: nlpResult.flags.length ? nlpResult.flags : ['Neutral / Regulated'],
                    riskScore: computedCTI
                }
            });

            localStorage.setItem('medicore_emai_chats_enc', SecurityEngine.maskData(JSON.stringify(existing)));
            renderStoredQA();

            setTimeout(() => { appendAiBubble(response); }, 600);
        }

        // --- SMART TRAUMA-INFORMED GUARDRAILS & TALKATIVE EMAI ---
        function generateEmotionalAiReply(rawInput) {
            const txt = rawInput.toLowerCase();

            const probingTriggers = ['what happened', 'tell me about the abuse', 'who did this', 'details', 'explain the story', 'recount'];
            if (probingTriggers.some(trigger => txt.includes(trigger))) {
                return "I will never ask you to recount or explain what happened. You are safe right now. Let's focus entirely on this present moment—can you feel the solid ground beneath your feet?";
            }

            const greetings = ['hi', 'hey', 'hello', 'hlo', 'namaste', 'hey emi', 'hey emai', 'good morning', 'good afternoon', 'good evening'];
            if (greetings.some(g => new RegExp(`(^|\\b)${g}(\\b|$)`, 'i').test(txt)) && patientTurnCount <= 2) {
                return "Hello there, Kanika. I'm so glad you checked in with me today. I'm right here by your side, listening closely. How has your mind and body felt over the past few hours?";
            }

            if (txt.includes('anxious') || txt.includes('panic') || txt.includes('scared') || txt.includes('fear') || txt.includes('nervous')) {
                return "I can sense the tension in your words right now, and it makes complete sense that you're feeling this way. Let's pause together for just a second. Notice the weight of your hands resting wherever they are. You are safe in this room.";
            }
            if (txt.includes('sad') || txt.includes('crying') || txt.includes('heavy') || txt.includes('hopeless') || txt.includes('lonely')) {
                return "Thank you for trusting me with that heavy feeling. Grief and sadness take up so much energy, and you don't have to pretend everything is fine. Healing is not a straight line. Let's just take it one micro-step at a time.";
            }
            if (txt.includes('tired') || txt.includes('exhausted') || txt.includes('sleep') || txt.includes('nightmare')) {
                return "Exhaustion can make everything feel much sharper and harder to bear. Your nervous system has been working overtime to keep you safe. If you can, let your shoulders drop down away from your ears right now.";
            }
            if (txt.includes('help') || txt.includes('emergency') || txt.includes('danger') || txt.includes('hurt')) {
                return "Please listen to me carefully: if you feel unsafe or threatened right this second, tap the red SOS button at the top right of your screen immediately. Medical units are on standby.";
            }
            if (txt.includes('thank') || txt.includes('better') || txt.includes('good') || txt.includes('okay') || txt.includes('fine')) {
                return "That brings genuine warmth to my digital heart. Even a small shift toward feeling 'okay' is a massive victory of your resilience. I'm so proud of the grace you're showing yourself today.";
            }
            return `I hear you saying "${rawInput}". It takes courage to put those thoughts into words. To help us stay grounded, let's look around your room right now: can you spot one object with a calming color, and tell me what it is?`;
        }

        function renderStoredQA() {
            const list = document.getElementById('qa-storage-list');
            const raw = localStorage.getItem('medicore_emai_chats_enc');
            let items = [];
            if (raw) { try { items = JSON.parse(SecurityEngine.unmaskData(raw)); } catch (e) { items = []; } }
            if (items.length === 0) {
                list.innerHTML = `<div class="qa-item"><div class="qa-q">No conversations recorded yet.</div></div>`;
                return;
            }
            list.innerHTML = items.map(item => `
                <div class="qa-item" style="border-left-color: var(--btn-primary);">
                    <div class="qa-q" style="color: var(--text-muted); font-size: 0.85rem; margin-bottom: 0.5rem;">
                        <strong>${item.date}</strong> at ${item.time} <br>
                        <span style="font-size: 0.95rem; display:block; margin-top:0.3rem;">You: ${item.q}</span>
                    </div>
                    <div class="qa-a" style="color: var(--text-primary);">EMAI Companion: <strong>${item.a}</strong></div>
                </div>`).join('');
        }

        function clearEmaiStorage() {
            if (confirm("Clear your saved EMAI reflection log?")) {
                localStorage.removeItem('medicore_emai_chats_enc');
                patientTurnCount = 0;
                renderStoredQA();
            }
        }

        // --- QUIET CHECK-IN & ADMIN LOGIC ---
        const CHECKIN_QUESTIONS = [
            ["How has your sleep been lately?", ["Mostly restful", "A bit restless some nights", "Frequently disrupted", "I'm barely sleeping"]],
            ["How's your appetite these days?", ["About the same as usual", "A little more or less than usual", "Noticeably changed", "Very hard to eat normally"]],
            ["How often do you feel like crying, even for no clear reason?", ["Rarely", "Sometimes", "Often", "Almost constantly"]],
            ["How easy is it to focus on everyday tasks?", ["Comes naturally", "Takes a little more effort", "Quite difficult", "I can barely concentrate"]],
            ["How is your energy through the day?", ["Fairly normal", "A bit low", "Often drained", "Exhausted most of the time"]],
            ["Do you still enjoy things you used to enjoy?", ["Yes, mostly", "Somewhat less than before", "Rarely", "Not at all right now"]],
            ["How safe do you feel in your everyday surroundings?", ["Quite safe", "Mostly safe", "Often uneasy", "Rarely safe"]],
            ["How often do worries feel hard to switch off?", ["Rarely", "Occasionally", "Frequently", "Nearly all the time"]],
            ["How would you describe your patience with small things lately?", ["Same as usual", "Slightly shorter", "Often on edge", "Very easily overwhelmed"]],
            ["How much do you feel like being around other people?", ["As much as usual", "Slightly less", "Mostly want to be alone", "Avoiding people entirely"]]
        ];

        let chkCurrent = 0; let chkAnswers = []; let chkDashFilter = 'all';
        let checkinStartTime = 0;

        function openQuietCheckinModal() {
            document.getElementById('checkin-modal-container').classList.add('active');
            checkinStartTime = Date.now();
            renderCheckinIntro();
        }
        function closeQuietCheckinModal() {
            document.getElementById('checkin-modal-container').classList.remove('active');
            let timeSpent = Math.round((Date.now() - checkinStartTime) / 1000);
            PatientTelemetry.logTelemetryEvent(`Quiet Check-In closed after ${timeSpent}s`);
        }

        function renderCheckinIntro() {
            document.getElementById('checkin-card').innerHTML = `
                <h1>Before we begin</h1>
                <p class="lead" style="color: var(--text-secondary);">This is a short, private check-in — simple questions about how you've been feeling day to day.</p>
                <button class="checkin-start-btn" onclick="startCheckinForm()">Begin whenever you're ready</button>
            `;
        }

        function startCheckinForm() {
            chkCurrent = 0;
            // Add 1 extra slot for the final text reflection step
            chkAnswers = new Array(CHECKIN_QUESTIONS.length + 1).fill(null);
            renderCheckinQuestion();
        }

        function renderCheckinQuestion() {
            // Check if we reached the newly added final text question step
            if (chkCurrent === CHECKIN_QUESTIONS.length) {
                const pct = 100;
                document.getElementById('checkin-card').innerHTML = `
                    <div class="checkin-step-label">Final Reflection</div>
                    <div class="checkin-progress-track"><div class="checkin-progress-fill" style="width:${pct}%"></div></div>
                    <div class="checkin-question-text">Is there anything else on your mind today? (Optional)</div>
                    <textarea id="checkin-final-text" style="width:100%; height:120px; background:var(--surface-input); border:1px solid var(--border-subtle); border-radius:8px; padding:10px; color:var(--text-primary); margin-bottom:1.5rem; outline:none; resize:none;" placeholder="Type your thoughts here..."></textarea>
                    <div class="checkin-nav-row"><button class="checkin-nav checkin-btn-ghost" onclick="goCheckinBack()">Back</button><button class="checkin-nav checkin-btn-primary" onclick="submitCheckinForm()">Finish Check-In</button></div>
                `;
                return;
            }

            const [text, opts] = CHECKIN_QUESTIONS[chkCurrent];
            const pct = Math.round((chkCurrent) / (CHECKIN_QUESTIONS.length) * 100);
            const saved = chkAnswers[chkCurrent];

            let optsHtml = opts.map((label, i) => {
                const sel = saved && !saved.isOther && saved.optionIndex === i ? 'selected' : '';
                return `<div class="checkin-option ${sel}" onclick="selectCheckinOption(${i})"><div class="dot"></div><div>${label}</div></div>`;
            }).join('');

            document.getElementById('checkin-card').innerHTML = `
                <div class="checkin-step-label">Question ${chkCurrent + 1} of ${CHECKIN_QUESTIONS.length}</div>
                <div class="checkin-progress-track"><div class="checkin-progress-fill" style="width:${pct}%"></div></div>
                <div class="checkin-question-text">${text}</div>
                <div class="checkin-options">${optsHtml}</div>
                <div class="checkin-nav-row"><button class="checkin-nav checkin-btn-ghost" onclick="goCheckinBack()" ${chkCurrent === 0 ? 'disabled' : ''}>Back</button><button class="checkin-nav checkin-btn-primary" onclick="goCheckinNext()" ${saved ? '' : 'disabled'}>Next</button></div>
            `;
        }

        function selectCheckinOption(i) { chkAnswers[chkCurrent] = { optionIndex: i, label: CHECKIN_QUESTIONS[chkCurrent][1][i], score: i, isOther: false }; renderCheckinQuestion(); }
        function goCheckinBack() { if (chkCurrent > 0) { chkCurrent--; renderCheckinQuestion(); } }

        function goCheckinNext() {
            if (!chkAnswers[chkCurrent]) return;
            chkCurrent++;
            renderCheckinQuestion();
        }

        function submitCheckinForm() {
            // Grab final text response if present
            const finalTextArea = document.getElementById('checkin-final-text');
            if (finalTextArea) {
                chkAnswers[CHECKIN_QUESTIONS.length] = finalTextArea.value.trim();
            }

            // Calculate percentage from the multiple choice answers only
            const mcAnswers = chkAnswers.slice(0, CHECKIN_QUESTIONS.length);
            const total = mcAnswers.reduce((sum, a) => sum + (a ? a.score : 0), 0);
            const maxScore = CHECKIN_QUESTIONS.length * 3;
            const pct = Math.round((total / maxScore) * 100);

            let level = 'Low';
            if (pct > 66) level = 'High'; else if (pct >= 34) level = 'Moderate';

            const timeSpentSeconds = Math.round((Date.now() - checkinStartTime) / 1000);
            const textResponse = (chkAnswers[CHECKIN_QUESTIONS.length] || '').toLowerCase();
            const dangerousWords = ['no hope', 'my life is over', 'i dont want to live', 'kill myself', 'suicide', 'end it all', 'die'];
            const hasDangerousWord = dangerousWords.some(w => textResponse.includes(w));

            // CRITICAL CHECK FOR AUTO-CALL SYSTEM & SOS
            if (pct > 90 || hasDangerousWord) {
                triggerAutoCallingEmergency();
            }

            const record = {
                id: 'CHK-' + Math.random().toString(36).slice(2, 8).toUpperCase(),
                timestamp: new Date().toLocaleString(),
                stressPercent: pct,
                stressLevel: level,
                timeSpent: timeSpentSeconds,
                needsReview: false,
                answers: CHECKIN_QUESTIONS.map((q, i) => ({ question: q[0], response: mcAnswers[i] ? mcAnswers[i].label : '(skipped)' }))
            };

            // Push final text to the record answers so admin can see it
            if (chkAnswers[CHECKIN_QUESTIONS.length]) {
                record.answers.push({ question: "Final Reflection", response: chkAnswers[CHECKIN_QUESTIONS.length] });
            }

            const existing = JSON.parse(localStorage.getItem('medicore_checkins') || '[]'); existing.unshift(record); localStorage.setItem('medicore_checkins', JSON.stringify(existing));

            document.getElementById('checkin-card').innerHTML = `<div class="checkin-final-icon">🌿</div><div style="font-size:17px; color:var(--text-primary); line-height:1.7;">Thank you for sharing. Support is always here.<br><small style="color:var(--text-dim); margin-top: 10px; display: block;">Time spent: ${timeSpentSeconds} seconds</small></div><button class="checkin-start-btn" style="margin-top:20px;" onclick="closeQuietCheckinModal()">Close & Return to Dashboard</button>`;
        }

        function setAdminDashFilter(f) { chkDashFilter = f; renderAdminCheckins(); }
        function renderAdminCheckins() {
            const container = document.getElementById('admin-checkin-dashboard'); if (!container) return;
            const subs = JSON.parse(localStorage.getItem('medicore_checkins') || '[]');
            const total = subs.length; const highCount = subs.filter(r => r.stressLevel === 'High').length; const moderateCount = subs.filter(r => r.stressLevel === 'Moderate').length; const lowCount = subs.filter(r => r.stressLevel === 'Low').length;
            let visible = subs; if (chkDashFilter !== 'all') { visible = subs.filter(r => r.stressLevel === chkDashFilter); }

            let rows = '';
            if (visible.length === 0) { rows = `<tr><td colspan="5" style="color:var(--text-dim); text-align:center; padding: 2rem;">No entries match this filter.</td></tr>`; }
            else {
                visible.forEach((r, idx) => {
                    const pillClass = r.stressLevel === 'Low' ? 'level-low' : (r.stressLevel === 'Moderate' ? 'level-moderate' : 'level-high');
                    const timeSpentDisplay = r.timeSpent ? r.timeSpent + 's' : '—';
                    rows += `<tr><td><strong>${r.id}</strong></td><td>${r.timestamp}</td><td><span class="level-pill ${pillClass}">${r.stressLevel} (${r.stressPercent}%)</span></td><td>${timeSpentDisplay}</td><td><button class="toggle-detail" onclick="document.getElementById('detail-${idx}').classList.toggle('show')">View answers</button></td></tr><tr class="detail-row" id="detail-${idx}"><td colspan="5" style="padding:1rem;">${r.answers.map(a => `<div style="margin-bottom:8px; color:var(--text-secondary);"><strong style="color:var(--text-primary); font-size:0.85rem;">${a.question}</strong><br><span style="font-size:0.9rem;">${a.response}</span></div>`).join('')}</td></tr>`;
                });
            }

            container.innerHTML = `
                <div class="stats-grid">
                    <div class="stat-card"><div class="stat-value">${total}</div><div class="stat-label">Total entries</div></div>
                    <div class="stat-card stat-high"><div class="stat-value">${highCount}</div><div class="stat-label">High level</div></div>
                    <div class="stat-card stat-moderate"><div class="stat-value">${moderateCount}</div><div class="stat-label">Moderate level</div></div>
                    <div class="stat-card stat-low"><div class="stat-value">${lowCount}</div><div class="stat-label">Low level</div></div>
                </div>
                <div class="filter-row">
                    <button class="filter-btn ${chkDashFilter === 'all' ? 'active' : ''}" onclick="setAdminDashFilter('all')">All (${total})</button>
                    <button class="filter-btn ${chkDashFilter === 'High' ? 'active' : ''}" onclick="setAdminDashFilter('High')">High (${highCount})</button>
                    <button class="filter-btn ${chkDashFilter === 'Moderate' ? 'active' : ''}" onclick="setAdminDashFilter('Moderate')">Moderate (${moderateCount})</button>
                    <button class="filter-btn ${chkDashFilter === 'Low' ? 'active' : ''}" onclick="setAdminDashFilter('Low')">Low (${lowCount})</button>
                </div>
                <div class="table-responsive">
                    <table class="submissions"><thead><tr><th>ID</th><th>Time</th><th>Level</th><th>Time Spent</th><th>Action</th></tr></thead><tbody>${rows}</tbody></table>
                </div>
            `;
        }
    </script>
</body>

</html>

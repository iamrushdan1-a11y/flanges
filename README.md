<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Ultimate Flange | Industrial Precision Solutions</title>
    <script src="https://cdn.tailwindcss.com"></script>
    <link href="https://fonts.googleapis.com/css2?family=Inter:wght@300;400;500;600;700;800&display=swap" rel="stylesheet">
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">
    <script src="https://cdn.jsdelivr.net/npm/chart.js"></script>
    <style>
        /* ===== RESET & VARIABLES ===== */
        :root {
            --primary-blue: #1e40af;
            --secondary-blue: #3b82f6;
            --accent-blue: #60a5fa;
            --primary-green: #10b981;
            --primary-orange: #f59e0b;
            --primary-purple: #8b5cf6;
        }
        
        body {
            font-family: 'Inter', sans-serif;
            scroll-behavior: smooth;
            overflow-x: hidden;
        }
        
        /* ===== AUTHENTICATION STYLES ===== */
        #main-content {
            filter: blur(0);
            pointer-events: auto;
            transition: filter 0.5s ease;
        }
        
        /* Auth overlay is hidden by default for visitors */
        #auth-overlay {
            display: none;
        }
        
        /* Show auth overlay only when not authenticated and not in visitor mode */
        body.require-auth #auth-overlay {
            display: flex;
        }
        
        body.require-auth #main-content {
            filter: blur(8px);
            pointer-events: none;
        }
        
        /* Visitor mode - no blur */
        body.visitor-mode #main-content {
            filter: blur(0);
            pointer-events: auto;
        }
        
        /* Authenticated mode - no blur */
        body.authenticated #main-content {
            filter: blur(0);
            pointer-events: auto;
        }
        
        /* Order button should always be clickable */
        .order-button {
            pointer-events: auto;
            cursor: pointer;
            position: relative;
            z-index: 10;
        }
        
        /* ===== FIXED PASSWORD FIELD STYLES ===== */
        input[type="password"] {
            -webkit-text-security: disc;
            font-family: 'Inter', sans-serif;
        }
        
        /* ===== GLASS NAVIGATION ===== */
        .glass-nav {
            background: rgba(255, 255, 255, 0.92);
            backdrop-filter: blur(12px);
            border-bottom: 1px solid rgba(0, 0, 0, 0.08);
            box-shadow: 0 4px 20px rgba(0, 0, 0, 0.05);
        }
        
        .gradient-text {
            background: linear-gradient(135deg, #1e40af 0%, #3b82f6 50%, #60a5fa 100%);
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
            background-clip: text;
        }
        
        .hero-gradient {
            background: linear-gradient(135deg, rgba(30, 64, 175, 0.05) 0%, rgba(59, 130, 246, 0.05) 100%);
        }
        
        /* ===== DASHBOARD STYLES ===== */
        .dashboard-grid {
            display: grid;
            grid-template-columns: 280px 1fr;
            min-height: calc(100vh - 80px);
        }
        
        .sidebar {
            background: linear-gradient(180deg, #1e293b 0%, #0f172a 100%);
            color: white;
        }
        
        .sidebar-menu-item {
            display: flex;
            align-items: center;
            gap: 12px;
            padding: 14px 20px;
            border-radius: 8px;
            transition: all 0.3s ease;
            color: #cbd5e1;
            font-weight: 500;
        }
        
        .sidebar-menu-item:hover, .sidebar-menu-item.active {
            background: rgba(255, 255, 255, 0.1);
            color: white;
            transform: translateX(5px);
        }
        
        .dashboard-card {
            background: white;
            border-radius: 12px;
            padding: 1.5rem;
            box-shadow: 0 1px 3px rgba(0, 0, 0, 0.1);
            border: 1px solid #e2e8f0;
            transition: all 0.3s ease;
        }
        
        .dashboard-card:hover {
            box-shadow: 0 10px 25px rgba(0, 0, 0, 0.1);
            transform: translateY(-2px);
        }
        
        .stat-card {
            background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
            color: white;
            border-radius: 12px;
            padding: 1.5rem;
        }
        
        .stat-card.sales {
            background: linear-gradient(135deg, #4ade80 0%, #22c55e 100%);
        }
        
        .stat-card.orders {
            background: linear-gradient(135deg, #fbbf24 0%, #f59e0b 100%);
        }
        
        .stat-card.customers {
            background: linear-gradient(135deg, #8b5cf6 0%, #7c3aed 100%);
        }
        
        .progress-bar {
            height: 8px;
            background: #e2e8f0;
            border-radius: 4px;
            overflow: hidden;
        }
        
        .progress-fill {
            height: 100%;
            border-radius: 4px;
            background: linear-gradient(90deg, #3b82f6 0%, #1d4ed8 100%);
            transition: width 1s ease;
        }
        
        .table-container {
            overflow-x: auto;
            border-radius: 8px;
            border: 1px solid #e2e8f0;
        }
        
        .table-container table {
            min-width: 100%;
        }
        
        .table-container th {
            background: #f8fafc;
            font-weight: 600;
            color: #475569;
            text-transform: uppercase;
            font-size: 0.75rem;
            letter-spacing: 0.05em;
            padding: 12px 16px;
            border-bottom: 1px solid #e2e8f0;
        }
        
        .table-container td {
            padding: 16px;
            border-bottom: 1px solid #e2e8f0;
            color: #475569;
        }
        
        .table-container tr:hover td {
            background: #f1f5f9;
        }
        
        .badge {
            display: inline-flex;
            align-items: center;
            padding: 4px 12px;
            border-radius: 20px;
            font-size: 0.75rem;
            font-weight: 600;
            text-transform: uppercase;
            letter-spacing: 0.05em;
        }
        
        .badge-success {
            background: #dcfce7;
            color: #166534;
        }
        
        .badge-warning {
            background: #fef3c7;
            color: #92400e;
        }
        
        .badge-danger {
            background: #fee2e2;
            color: #991b1b;
        }
        
        .badge-info {
            background: #dbeafe;
            color: #1e40af;
        }
        
        .reveal {
            opacity: 0;
            transform: translateY(40px);
            transition: all 0.8s cubic-bezier(0.22, 1, 0.36, 1);
        }
        
        .reveal.active {
            opacity: 1;
            transform: translateY(0);
        }
        
        .stagger-delay-1 { transition-delay: 0.1s; }
        .stagger-delay-2 { transition-delay: 0.2s; }
        .stagger-delay-3 { transition-delay: 0.3s; }
        .stagger-delay-4 { transition-delay: 0.4s; }
        
        /* ===== LOADING SHIMMER ===== */
        .loading-shimmer {
            position: fixed;
            top: 0;
            left: -100%;
            width: 100%;
            height: 100%;
            background: linear-gradient(90deg, transparent, rgba(37, 99, 235, 0.8), transparent);
            z-index: 2000;
            transition: left 1.2s cubic-bezier(0.65, 0, 0.35, 1);
        }
        
        .flange-chip {
            transition: all 0.3s cubic-bezier(0.4, 0, 0.2, 1);
            cursor: pointer;
            white-space: nowrap;
        }
        
        .flange-chip.active {
            background-color: var(--primary-blue);
            color: white;
            border-color: var(--primary-blue);
            box-shadow: 0 6px 20px rgba(37, 99, 235, 0.25);
            transform: translateY(-2px);
        }
        
        .no-scrollbar::-webkit-scrollbar {
            display: none;
        }
        
        .no-scrollbar {
            -ms-overflow-style: none;
            scrollbar-width: none;
        }
        
        .feature-card {
            transition: all 0.4s cubic-bezier(0.4, 0, 0.2, 1);
            background: white;
            border: 1px solid rgba(226, 232, 240, 0.9);
        }
        
        .feature-card:hover {
            border-color: var(--secondary-blue);
            transform: translateY(-8px);
            box-shadow: 0 20px 40px -15px rgba(0, 0, 0, 0.1);
        }
        
        .knowledge-card {
            transition: all 0.3s ease;
            background: white;
            border: 1px solid rgba(226, 232, 240, 0.8);
        }
        
        .knowledge-card:hover {
            border-color: var(--secondary-blue);
            transform: translateY(-5px);
            box-shadow: 0 20px 40px -10px rgba(0, 0, 0, 0.08);
        }
        
        .hero-image-container {
            width: 100%;
            height: 400px;
            border-radius: 16px;
            overflow: hidden;
            background: linear-gradient(135deg, #f8fafc 0%, #e2e8f0 100%);
            box-shadow: 0 20px 40px rgba(0, 0, 0, 0.1);
            position: relative;
        }
        
        .hero-image-container img {
            width: 100%;
            height: 100%;
            object-fit: cover;
        }
        
        .search-container {
            transition: all 0.3s ease;
        }
        
        .search-container:focus-within {
            box-shadow: 0 0 0 3px rgba(37, 99, 235, 0.15);
            border-color: var(--secondary-blue);
        }
        
        /* ===== FIXED IMAGE FALLBACK STYLES ===== */
        img {
            max-width: 100%;
            height: auto;
        }
        
        img.error,
        img:not([src]),
        img[src=""],
        img[src="undefined"] {
            display: none;
        }
        
        .img-fallback {
            display: flex;
            align-items: center;
            justify-content: center;
            background: linear-gradient(135deg, #f1f5f9 0%, #e2e8f0 100%);
            color: #64748b;
            font-size: 48px;
            width: 100%;
            height: 100%;
        }
        
        /* ===== SPEC TABLE STYLES ===== */
        .spec-table {
            border-collapse: separate;
            border-spacing: 0;
        }
        
        .spec-table th {
            background: rgba(30, 64, 175, 0.1);
            font-weight: 600;
            text-transform: uppercase;
            letter-spacing: 0.05em;
        }
        
        .spec-table tr:hover td {
            background: rgba(59, 130, 246, 0.03);
        }
        
        /* ===== CONTACT FORM STYLES ===== */
        .contact-form input:focus,
        .contact-form textarea:focus,
        .contact-form select:focus {
            box-shadow: 0 0 0 3px rgba(37, 99, 235, 0.15);
            border-color: var(--secondary-blue);
        }
        
        /* ===== MOBILE MENU STYLES ===== */
        .mobile-menu {
            transform: translateX(100%);
            transition: transform 0.3s cubic-bezier(0.4, 0, 0.2, 1);
            position: fixed;
            top: 0;
            right: 0;
            bottom: 0;
            z-index: 100;
            width: 300px;
            background: white;
            box-shadow: -2px 0 20px rgba(0, 0, 0, 0.1);
            overflow-y: auto;
        }
        
        .mobile-menu.active {
            transform: translateX(0);
        }
        
        .mobile-menu-overlay {
            display: none;
            position: fixed;
            top: 0;
            left: 0;
            right: 0;
            bottom: 0;
            background: rgba(0, 0, 0, 0.5);
            z-index: 99;
        }
        
        .mobile-menu-overlay.active {
            display: block;
        }
        
        /* ===== ORDER MODAL STYLES ===== */
        #order-modal .hidden {
            display: none !important;
        }
        
        .step-container {
            position: relative;
            padding: 1.5rem 0;
        }
        
        .step-line {
            position: absolute;
            top: 2rem;
            left: 1.5rem;
            right: 1.5rem;
            height: 2px;
            background: #e5e7eb;
            z-index: 1;
        }
        
        .step-line-progress {
            position: absolute;
            top: 2rem;
            left: 1.5rem;
            height: 2px;
            background: linear-gradient(90deg, #3b82f6 0%, #1d4ed8 100%);
            transition: width 0.6s cubic-bezier(0.4, 0, 0.2, 1);
            z-index: 2;
        }
        
        .step-indicator {
            width: 3.5rem;
            height: 3.5rem;
            border-radius: 50%;
            display: flex;
            align-items: center;
            justify-content: center;
            font-weight: bold;
            font-size: 1.125rem;
            position: relative;
            z-index: 3;
            transition: all 0.4s cubic-bezier(0.4, 0, 0.2, 1);
            box-shadow: 0 4px 15px rgba(0, 0, 0, 0.1);
        }
        
        .step-indicator.pending {
            background-color: #e5e7eb;
            color: #6b7280;
            border: 2px solid #e5e7eb;
        }
        
        .step-indicator.active {
            background-color: #3b82f6;
            color: white;
            border: 2px solid #3b82f6;
            transform: scale(1.1);
            box-shadow: 0 0 0 8px rgba(59, 130, 246, 0.15);
            animation: pulse 2s infinite;
        }
        
        .step-indicator.completed {
            background-color: #10b981;
            color: white;
            border: 2px solid #10b981;
        }
        
        .step-label {
            position: absolute;
            bottom: -2rem;
            left: 0;
            right: 0;
            text-align: center;
            font-size: 0.75rem;
            font-weight: 600;
            color: #6b7280;
            transition: all 0.3s ease;
        }
        
        .step-indicator.active ~ .step-label {
            color: #3b82f6;
            font-weight: 700;
        }
        
        .step-indicator.completed ~ .step-label {
            color: #10b981;
        }
        
        @keyframes pulse {
            0% {
                box-shadow: 0 0 0 0 rgba(59, 130, 246, 0.4);
            }
            70% {
                box-shadow: 0 0 0 10px rgba(59, 130, 246, 0);
            }
            100% {
                box-shadow: 0 0 0 0 rgba(59, 130, 246, 0);
            }
        }
        
        .order-step {
            animation: slideIn 0.5s cubic-bezier(0.4, 0, 0.2, 1) forwards;
        }
        
        @keyframes slideIn {
            from {
                opacity: 0;
                transform: translateX(20px);
            }
            to {
                opacity: 1;
                transform: translateX(0);
            }
        }
        
        /* ===== SHIMMER LOADING ANIMATION ===== */
        .shimmer {
            background: linear-gradient(90deg, 
                #f0f0f0 25%, 
                #e0e0e0 50%, 
                #f0f0f0 75%);
            background-size: 200% 100%;
            animation: shimmer 1.5s infinite;
        }
        
        @keyframes shimmer {
            0% {
                background-position: -200% 0;
            }
            100% {
                background-position: 200% 0;
            }
        }
        
        .form-input-enhanced {
            transition: all 0.3s cubic-bezier(0.4, 0, 0.2, 1);
            border: 2px solid #e5e7eb;
            background: linear-gradient(to bottom, #ffffff, #fafafa);
        }
        
        .form-input-enhanced:focus {
            border-color: #3b82f6;
            box-shadow: 0 0 0 3px rgba(59, 130, 246, 0.1), 
                        0 4px 20px rgba(59, 130, 246, 0.15);
            transform: translateY(-1px);
        }
        
        .btn-gradient {
            background: linear-gradient(135deg, #3b82f6 0%, #1d4ed8 100%);
            position: relative;
            overflow: hidden;
        }
        
        .btn-gradient:hover {
            background: linear-gradient(135deg, #2563eb 0%, #1e40af 100%);
            transform: translateY(-2px);
            box-shadow: 0 10px 25px rgba(37, 99, 235, 0.25);
        }
        
        .btn-gradient:active {
            transform: translateY(0);
        }
        
        .btn-gradient::after {
            content: '';
            position: absolute;
            top: 0;
            left: -100%;
            width: 100%;
            height: 100%;
            background: linear-gradient(90deg, transparent, rgba(255, 255, 255, 0.2), transparent);
            transition: left 0.5s;
        }
        
        .btn-gradient:hover::after {
            left: 100%;
        }
        
        .product-thumbnail {
            width: 100%;
            height: 180px;
            border-radius: 12px;
            overflow: hidden;
            background: linear-gradient(135deg, #f1f5f9 0%, #e2e8f0 100%);
            display: flex;
            align-items: center;
            justify-content: center;
            transition: all 0.3s ease;
            cursor: pointer;
        }
        
        .product-thumbnail:hover {
            transform: translateY(-4px);
            box-shadow: 0 12px 24px rgba(0, 0, 0, 0.1);
        }
        
        .product-thumbnail img {
            width: 100%;
            height: 100%;
            object-fit: cover;
        }
        
        .product-placeholder {
            display: flex;
            flex-direction: column;
            align-items: center;
            justify-content: center;
            color: #64748b;
        }
        
        .product-placeholder i {
            font-size: 48px;
            margin-bottom: 12px;
            color: #94a3b8;
        }
        
        .product-image-container {
            width: 100%;
            height: 400px;
            border-radius: 16px;
            overflow: hidden;
            background: linear-gradient(135deg, #f8fafc 0%, #e2e8f0 100%);
            box-shadow: 0 20px 40px rgba(0, 0, 0, 0.1);
            position: relative;
        }
        
        .product-image-container img {
            width: 100%;
            height: 100%;
            object-fit: contain;
            background: #f8fafc;
        }
        
        .gallery-product-card {
            height: 100%;
            transition: all 0.3s ease;
        }
        
        .gallery-product-card:hover {
            transform: translateY(-8px);
            box-shadow: 0 20px 40px rgba(0, 0, 0, 0.1);
        }
        
        .tab-button {
            padding: 12px 24px;
            border: none;
            background: none;
            font-weight: 500;
            color: #64748b;
            border-bottom: 2px solid transparent;
            transition: all 0.3s ease;
            cursor: pointer;
        }
        
        .tab-button.active {
            color: #3b82f6;
            border-bottom-color: #3b82f6;
        }
        
        .tab-content {
            display: none;
        }
        
        .tab-content.active {
            display: block;
        }
        
        .tracking-container {
            background: linear-gradient(135deg, #f8fafc 0%, #f1f5f9 100%);
            border-radius: 1.5rem;
            overflow: hidden;
        }
        
        .tracking-step {
            position: relative;
            padding-left: 2.5rem;
            margin-bottom: 2rem;
        }
        
        .tracking-step:not(:last-child)::before {
            content: '';
            position: absolute;
            left: 1.5rem;
            top: 2.5rem;
            bottom: -2rem;
            width: 2px;
            background: #e5e7eb;
        }
        
        .tracking-step.completed:not(:last-child)::before {
            background: linear-gradient(180deg, #10b981 0%, #059669 100%);
        }
        
        .tracking-step-icon {
            width: 3rem;
            height: 3rem;
            border-radius: 50%;
            display: flex;
            align-items: center;
            justify-content: center;
            position: absolute;
            left: 0;
            top: 0;
            z-index: 2;
            transition: all 0.3s ease;
        }
        
        .tracking-step-icon.pending {
            background: #f3f4f6;
            color: #9ca3af;
            border: 2px solid #e5e7eb;
        }
        
        .tracking-step-icon.current {
            background: #3b82f6;
            color: white;
            border: 2px solid #3b82f6;
            box-shadow: 0 4px 20px rgba(59, 130, 246, 0.3);
            animation: pulse 2s infinite;
        }
        
        .tracking-step-icon.completed {
            background: #10b981;
            color: white;
            border: 2px solid #10b981;
            box-shadow: 0 4px 20px rgba(16, 185, 129, 0.3);
        }
        
        .tracking-step-content {
            background: white;
            border-radius: 1rem;
            padding: 1.5rem;
            box-shadow: 0 4px 6px -1px rgba(0, 0, 0, 0.1);
            transition: all 0.3s ease;
        }
        
        .tracking-step.completed .tracking-step-content {
            border-left: 4px solid #10b981;
        }
        
        .tracking-step.current .tracking-step-content {
            border-left: 4px solid #3b82f6;
            transform: translateX(4px);
        }
        
        .chat-modal {
            position: fixed;
            top: 0;
            right: -400px;
            width: 400px;
            height: 100vh;
            background: white;
            box-shadow: -5px 0 30px rgba(0, 0, 0, 0.1);
            transition: right 0.3s cubic-bezier(0.4, 0, 0.2, 1);
            z-index: 9999;
            display: flex;
            flex-direction: column;
        }
        
        .chat-modal.active {
            right: 0;
        }
        
        .chat-messages {
            flex: 1;
            overflow-y: auto;
            padding: 20px;
        }
        
        .chat-message {
            margin-bottom: 15px;
            max-width: 80%;
        }
        
        .chat-message.sent {
            margin-left: auto;
        }
        
        .chat-input-container {
            border-top: 1px solid #e5e7eb;
            padding: 15px;
        }
        
        .supplier-card {
            transition: all 0.3s ease;
            cursor: pointer;
        }
        
        .supplier-card:hover {
            transform: translateY(-2px);
            box-shadow: 0 10px 25px rgba(0, 0, 0, 0.1);
        }
        
        .supplier-card.selected {
            border-color: #3b82f6;
            background-color: #eff6ff;
        }
        
        .supplier-section {
            background: linear-gradient(135deg, #f8fafc 0%, #f1f5f9 100%);
            border-radius: 1rem;
            padding: 1.5rem;
            margin-bottom: 1.5rem;
        }
        
        .supplier-badge {
            display: inline-flex;
            align-items: center;
            padding: 4px 8px;
            background: #10b981;
            color: white;
            border-radius: 6px;
            font-size: 0.75rem;
            font-weight: 600;
            margin-left: 8px;
        }
        
        /* ===== LOADING SPINNER ===== */
        .loading-spinner {
            display: inline-block;
            width: 20px;
            height: 20px;
            border: 3px solid rgba(59, 130, 246, 0.3);
            border-radius: 50%;
            border-top-color: #3b82f6;
            animation: spin 1s ease-in-out infinite;
        }
        
        @keyframes spin {
            to { transform: rotate(360deg); }
        }
        
        .loading-overlay {
            position: fixed;
            top: 0;
            left: 0;
            right: 0;
            bottom: 0;
            background: rgba(255, 255, 255, 0.8);
            display: flex;
            align-items: center;
            justify-content: center;
            z-index: 10000;
        }
        
        /* ===== ERROR MESSAGE STYLES ===== */
        .error-message {
            background-color: #fee2e2;
            border: 1px solid #fecaca;
            color: #991b1b;
            padding: 12px 16px;
            border-radius: 8px;
            margin: 10px 0;
            font-size: 14px;
            display: flex;
            align-items: center;
            gap: 10px;
        }
        
        .error-message i {
            color: #ef4444;
        }
        
        .success-message {
            background-color: #dcfce7;
            border: 1px solid #bbf7d0;
            color: #166534;
            padding: 12px 16px;
            border-radius: 8px;
            margin: 10px 0;
            font-size: 14px;
            display: flex;
            align-items: center;
            gap: 10px;
        }
        
        .success-message i {
            color: #22c55e;
        }
        
        .info-message {
            background-color: #dbeafe;
            border: 1px solid #bfdbfe;
            color: #1e40af;
            padding: 12px 16px;
            border-radius: 8px;
            margin: 10px 0;
            font-size: 14px;
            display: flex;
            align-items: center;
            gap: 10px;
        }
        
        .info-message i {
            color: #3b82f6;
        }
        
        /* ===== VALIDATION STYLES ===== */
        .input-error {
            border-color: #ef4444 !important;
        }
        
        .validation-message {
            color: #ef4444;
            font-size: 12px;
            margin-top: 4px;
            display: block;
        }
        
        /* ===== RESPONSIVE FIXES ===== */
        @media (max-width: 768px) {
            #auth-overlay .bg-white {
                max-height: 90vh;
                overflow-y: auto;
                padding: 1.5rem;
            }
            
            #auth-overlay .text-3xl {
                font-size: 1.75rem;
            }
            
            #auth-overlay .p-8 {
                padding: 1.5rem;
            }
            
            .py-3\.5, .py-4 {
                padding-top: 0.875rem !important;
                padding-bottom: 0.875rem !important;
            }
            
            #order-address {
                min-height: 100px;
            }
            
            .hero-image-container {
                height: 250px;
            }
            
            .mobile-menu {
                width: 100%;
                max-width: 300px;
                padding: 1.5rem;
            }
            
            .step-container {
                padding: 1rem 0;
            }
            
            .step-indicator {
                width: 2.5rem;
                height: 2.5rem;
                font-size: 0.875rem;
            }
            
            .step-line {
                top: 1.25rem;
                left: 1rem;
                right: 1rem;
            }
            
            .step-line-progress {
                top: 1.25rem;
                left: 1rem;
            }
            
            .step-label {
                font-size: 0.7rem;
                bottom: -1.5rem;
            }
            
            .chat-modal {
                width: 100%;
                right: -100%;
            }
            
            .product-image-container {
                height: 250px;
            }
            
            .product-thumbnail {
                height: 140px;
            }
            
            .product-thumbnail i {
                font-size: 32px;
            }
            
            .product-thumbnail span {
                font-size: 12px;
            }
            
            .gallery-product-card .product-image-container {
                height: 160px;
            }
            
            .spec-table th,
            .spec-table td {
                padding: 10px 12px;
                font-size: 12px;
            }
            
            .tab-button {
                padding: 8px 16px;
                font-size: 14px;
            }
            
            .stat-card {
                padding: 1rem;
            }
            
            .stat-card h3 {
                font-size: 1.5rem;
            }
            
            .dashboard-card {
                padding: 1rem;
            }
        }
        
        /* ===== FIXED CLASS NAME CONFLICTS ===== */
        .bg-gradient {
            background: linear-gradient(135deg, var(--primary-blue), var(--secondary-blue));
        }
        
        .text-gradient {
            background: linear-gradient(135deg, var(--primary-blue), var(--secondary-blue));
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
            background-clip: text;
        }
        
        .card-hover {
            transition: all 0.3s ease;
        }
        
        .card-hover:hover {
            transform: translateY(-5px);
            box-shadow: 0 15px 30px rgba(0, 0, 0, 0.1);
        }
        
        textarea {
            min-height: 100px;
            resize: vertical;
        }
        
        html, body {
            scroll-padding-top: 80px;
        }
    </style>
</head>
<body class="bg-slate-50 text-slate-900 visitor-mode">
    <!-- Loading Overlay -->
    <div id="loading-overlay" class="loading-overlay hidden">
        <div class="bg-white p-6 rounded-xl shadow-xl text-center">
            <div class="loading-spinner mx-auto mb-4" style="width: 40px; height: 40px;"></div>
            <p class="text-slate-700 font-medium" id="loading-message">Loading...</p>
        </div>
    </div>

    <div id="transition-loader" class="loading-shimmer"></div>

    <!-- Login/Signup Modal Overlay -->
    <div id="auth-overlay" class="fixed inset-0 bg-slate-900/70 backdrop-blur-lg flex items-center justify-center p-4 z-50">
        <div class="bg-white w-full max-w-md rounded-3xl shadow-2xl overflow-hidden p-4 sm:p-6 md:p-8 relative" style="max-height: 90vh; overflow-y: auto;">
            <button onclick="closeAuth()" class="absolute top-4 right-4 text-slate-400 hover:text-slate-700 z-10">
                <i class="fas fa-times text-xl"></i>
            </button>
            
            <div id="login-form">
                <div class="text-center mb-6 md:mb-8">
                    <div class="bg-gradient-to-br from-blue-600 to-blue-800 w-16 h-16 md:w-20 md:h-20 rounded-2xl flex items-center justify-center mx-auto mb-4 md:mb-6 shadow-xl">
                        <i class="fas fa-industry text-white text-2xl md:text-3xl"></i>
                    </div>
                    <h2 class="text-2xl md:text-3xl font-bold text-slate-900">Portal Access</h2>
                    <p class="text-slate-500 mt-2 text-sm md:text-base">Sign in to access technical data and pricing</p>
                </div>
                <div id="login-error-container" class="error-message hidden"></div>
                <form class="space-y-4 md:space-y-5" onsubmit="loginUser(event)">
                    <div>
                        <label class="block text-sm font-semibold text-slate-700 mb-2">Email Address</label>
                        <input type="email" id="login-email" required placeholder="name@company.com" 
                               class="w-full px-4 md:px-5 py-3 rounded-xl border-2 border-slate-200 focus:ring-2 focus:ring-blue-500 outline-none transition text-sm md:text-base">
                        <span class="validation-message hidden" id="login-email-error"></span>
                    </div>
                    <div>
                        <label class="block text-sm font-semibold text-slate-700 mb-2">Password</label>
                        <input type="password" id="login-password" required placeholder="••••••••" 
                               class="w-full px-4 md:px-5 py-3 rounded-xl border-2 border-slate-200 focus:ring-2 focus:ring-blue-500 outline-none transition text-sm md:text-base">
                        <span class="validation-message hidden" id="login-password-error"></span>
                    </div>
                    <div class="flex items-center justify-between">
                        <label class="flex items-center">
                            <input type="checkbox" id="remember-me" class="rounded border-slate-300 text-blue-600 focus:ring-blue-500">
                            <span class="ml-2 text-sm text-slate-600">Remember me</span>
                        </label>
                        <a href="#" class="text-sm text-blue-600 font-medium hover:text-blue-800">Forgot password?</a>
                    </div>
                    
                    <!-- User Type Selection -->
                    <div>
                        <label class="block text-sm font-semibold text-slate-700 mb-2">Login As</label>
                        <div class="grid grid-cols-2 gap-3">
                            <button type="button" onclick="setUserType('partner')" 
                                    class="px-3 md:px-4 py-2.5 md:py-3 rounded-lg border-2 border-blue-200 bg-blue-50 text-blue-700 font-medium flex items-center justify-center gap-2 text-sm md:text-base">
                                <i class="fas fa-user-shield"></i>
                                Partner
                            </button>
                            <button type="button" onclick="setUserType('supplier')" 
                                    class="px-3 md:px-4 py-2.5 md:py-3 rounded-lg border-2 border-slate-200 hover:border-blue-200 hover:bg-blue-50 font-medium flex items-center justify-center gap-2 text-sm md:text-base">
                                <i class="fas fa-building"></i>
                                Supplier
                            </button>
                        </div>
                    </div>
                    
                    <button type="submit" 
                            class="w-full py-3 md:py-4 bg-gradient-to-r from-blue-600 to-blue-800 text-white font-bold rounded-xl hover:from-blue-700 hover:to-blue-900 transition-all transform hover:-translate-y-1 active:scale-95 shadow-lg shadow-blue-100 hover:shadow-xl text-sm md:text-base">
                        <i class="fas fa-sign-in-alt mr-2"></i>Login to Portal
                    </button>
                    
                    <div class="relative flex py-3 md:py-4 items-center">
                        <div class="flex-grow border-t border-slate-100"></div>
                        <span class="flex-shrink mx-4 text-slate-400 text-xs font-bold uppercase tracking-widest">or</span>
                        <div class="flex-grow border-t border-slate-100"></div>
                    </div>

                    <button type="button" onclick="handleVisitor(event)" 
                            class="w-full py-3 bg-white border-2 border-slate-100 text-slate-700 font-bold rounded-xl hover:border-blue-200 hover:text-blue-600 transition-all flex items-center justify-center gap-3 group text-sm md:text-base">
                        <i class="fas fa-user text-slate-400 group-hover:text-blue-500"></i>
                        <span>Continue as Visitor</span>
                        <i class="fas fa-arrow-right text-sm group-hover:translate-x-1 transition-transform"></i>
                    </button>

                    <p class="text-center text-sm text-slate-500 mt-6 md:mt-8">
                        Don't have access? <button type="button" onclick="toggleAuthView('signup')" 
                        class="text-blue-600 font-semibold hover:text-blue-800 hover:underline">Request Account</button>
                    </p>
                </form>
            </div>

            <!-- SIGNUP FORM -->
            <div id="signup-form" class="hidden">
                <div class="text-center mb-6 md:mb-8">
                    <h2 class="text-2xl md:text-3xl font-bold text-slate-900">Create Partner Account</h2>
                    <p class="text-slate-500 mt-2 text-sm md:text-base">Join our industrial network for exclusive access</p>
                </div>
                <div id="signup-error-container" class="error-message hidden"></div>
                <form class="space-y-4 md:space-y-5" onsubmit="signupUser(event)">
                    <div class="grid grid-cols-2 gap-3 md:gap-4">
                        <div>
                            <label class="block text-sm font-semibold text-slate-700 mb-2">First Name</label>
                            <input type="text" id="signup-firstname" required 
                                   class="w-full px-3 md:px-4 py-2.5 md:py-3 rounded-xl border-2 border-slate-200 focus:ring-2 focus:ring-blue-500 outline-none transition text-sm md:text-base">
                        </div>
                        <div>
                            <label class="block text-sm font-semibold text-slate-700 mb-2">Last Name</label>
                            <input type="text" id="signup-lastname" required 
                                   class="w-full px-3 md:px-4 py-2.5 md:py-3 rounded-xl border-2 border-slate-200 focus:ring-2 focus:ring-blue-500 outline-none transition text-sm md:text-base">
                        </div>
                    </div>
                    <div>
                        <label class="block text-sm font-semibold text-slate-700 mb-2">Email</label>
                        <input type="email" id="signup-email" required 
                               class="w-full px-3 md:px-4 py-2.5 md:py-3 rounded-xl border-2 border-slate-200 focus:ring-2 focus:ring-blue-500 outline-none transition text-sm md:text-base">
                    </div>
                    <div>
                        <label class="block text-sm font-semibold text-slate-700 mb-2">Password</label>
                        <input type="password" id="signup-password" required placeholder="Create a password" 
                               class="w-full px-3 md:px-4 py-2.5 md:py-3 rounded-xl border-2 border-slate-200 focus:ring-2 focus:ring-blue-500 outline-none transition text-sm md:text-base">
                    </div>
                    <div>
                        <label class="block text-sm font-semibold text-slate-700 mb-2">Company</label>
                        <input type="text" id="signup-company" required 
                               class="w-full px-3 md:px-4 py-2.5 md:py-3 rounded-xl border-2 border-slate-200 focus:ring-2 focus:ring-blue-500 outline-none transition text-sm md:text-base">
                    </div>
                    <div>
                        <label class="block text-sm font-semibold text-slate-700 mb-2">Industry</label>
                        <select id="signup-industry" class="w-full px-3 md:px-4 py-2.5 md:py-3 rounded-xl border-2 border-slate-200 focus:ring-2 focus:ring-blue-500 outline-none transition text-sm md:text-base">
                            <option value="">Select Industry</option>
                            <option value="oil_gas">Oil & Gas</option>
                            <option value="chemical">Chemical Processing</option>
                            <option value="power">Power Generation</option>
                            <option value="marine">Marine & Offshore</option>
                            <option value="construction">Construction</option>
                            <option value="other">Other</option>
                        </select>
                    </div>
                    <button type="submit" 
                            class="w-full py-3 md:py-4 bg-gradient-to-r from-blue-600 to-blue-800 text-white font-bold rounded-xl hover:from-blue-700 hover:to-blue-900 transition-all shadow-lg shadow-blue-100 text-sm md:text-base">
                        <i class="fas fa-user-plus mr-2"></i>Create Partner Profile
                    </button>
                    <p class="text-center text-sm text-slate-500 mt-6 md:mt-8">
                        Already have an account? <button type="button" onclick="toggleAuthView('login')" 
                        class="text-blue-600 font-semibold hover:text-blue-800 hover:underline">Sign In</button>
                    </p>
                </form>
            </div>
        </div>
    </div>

    <!-- Supplier Chat Modal -->
    <div id="chat-modal" class="chat-modal">
        <div class="border-b border-slate-200 p-4 flex items-center justify-between">
            <div class="flex items-center gap-3">
                <div class="w-10 h-10 bg-green-100 rounded-full flex items-center justify-center">
                    <i class="fas fa-user-tie text-green-600"></i>
                </div>
                <div>
                    <h3 class="font-bold text-slate-900" id="chat-supplier-name">Supplier Name</h3>
                    <p class="text-slate-500 text-sm" id="chat-supplier-status">Online</p>
                </div>
            </div>
            <button onclick="closeChat()" class="text-slate-400 hover:text-slate-700">
                <i class="fas fa-times text-xl"></i>
            </button>
        </div>
        
        <div class="chat-messages" id="chat-messages">
            <div class="text-center text-slate-500 text-sm py-4">
                Chat started with supplier
            </div>
        </div>
        
        <div class="chat-input-container">
            <div class="flex gap-2">
                <input type="text" id="chat-input" placeholder="Type your message..." 
                       class="flex-1 px-4 py-2 border border-slate-300 rounded-lg focus:ring-2 focus:ring-blue-500 focus:border-blue-500 outline-none">
                <button onclick="sendChatMessage()" class="px-4 py-2 bg-blue-600 text-white rounded-lg hover:bg-blue-700 transition">
                    <i class="fas fa-paper-plane"></i>
                </button>
            </div>
        </div>
    </div>

    <!-- Order Process Modal -->
    <div id="order-modal" class="fixed inset-0 bg-black/60 backdrop-blur-md hidden items-center justify-center p-4 z-50">
        <div class="bg-white w-full max-w-2xl rounded-3xl shadow-2xl overflow-hidden relative" style="max-height: 90vh; overflow-y: auto;">
            <button onclick="closeOrderModal()" class="absolute top-4 right-4 text-slate-400 hover:text-slate-700 z-10">
                <i class="fas fa-times text-2xl"></i>
            </button>
            
            <!-- Step Indicators -->
            <div class="px-4 md:px-8 pt-6 md:pt-8">
                <div class="mb-6 md:mb-8">
                    <h2 class="text-2xl md:text-3xl font-bold text-slate-900 text-center mb-2">Order Request</h2>
                    <p class="text-slate-600 text-center text-sm md:text-base">Follow these simple steps to place your order</p>
                </div>
                
                <div class="step-container">
                    <div class="step-line"></div>
                    <div class="step-line-progress" id="step-progress" style="width: 0%"></div>
                    
                    <div class="flex justify-between relative">
                        <!-- Step 1 -->
                        <div class="flex flex-col items-center relative" style="flex: 1;">
                            <div id="step-indicator-1" class="step-indicator pending">
                                1
                            </div>
                            <span class="step-label">Product</span>
                        </div>
                        
                        <!-- Step 2 -->
                        <div class="flex flex-col items-center relative" style="flex: 1;">
                            <div id="step-indicator-2" class="step-indicator pending">
                                2
                            </div>
                            <span class="step-label">Supplier</span>
                        </div>
                        
                        <!-- Step 3 -->
                        <div class="flex flex-col items-center relative" style="flex: 1;">
                            <div id="step-indicator-3" class="step-indicator pending">
                                3
                            </div>
                            <span class="step-label">Contact</span>
                        </div>
                        
                        <!-- Step 4 -->
                        <div class="flex flex-col items-center relative" style="flex: 1;">
                            <div id="step-indicator-4" class="step-indicator pending">
                                4
                            </div>
                            <span class="step-label">Confirm</span>
                        </div>
                    </div>
                </div>
            </div>
            
            <div id="order-error-container" class="px-4 md:px-8 error-message hidden"></div>
            
            <!-- Step 1: Product Selection -->
            <div id="order-step-1" class="p-4 md:p-8 order-step">
                <form class="space-y-5 md:space-y-6">
                    <div class="transform transition-all duration-300 hover:scale-[1.02]">
                        <label class="block text-sm font-semibold text-slate-700 mb-2">Product *</label>
                        <select id="order-product" class="w-full px-4 md:px-5 py-3 md:py-3.5 rounded-xl form-input-enhanced focus:ring-2 focus:ring-blue-500 outline-none transition-all text-sm md:text-base" onchange="loadSuppliersForProduct(this.value)">
                            <option value="">Select Product</option>
                            <option value="wnf">Weld Neck Flange</option>
                            <option value="lwn">Long Weld Neck Flange</option>
                            <option value="slipon">Slip-On Flange</option>
                            <option value="blind">Blind Flange</option>
                            <option value="puddle">Puddle Flange</option>
                            <option value="plasma">Plasma CNC Cutting</option>
                            <option value="profile">Profile Cutting Services</option>
                            <option value="custom">Custom Requirements</option>
                        </select>
                        <span class="validation-message hidden" id="order-product-error"></span>
                    </div>
                    
                    <div class="grid md:grid-cols-2 gap-4 md:gap-5">
                        <div class="transform transition-all duration-300 hover:scale-[1.02]">
                            <label class="block text-sm font-semibold text-slate-700 mb-2">Quantity *</label>
                            <input type="number" min="1" value="1" id="order-quantity" class="w-full px-4 md:px-5 py-3 md:py-3.5 rounded-xl form-input-enhanced focus:ring-2 focus:ring-blue-500 outline-none transition-all text-sm md:text-base">
                            <span class="validation-message hidden" id="order-quantity-error"></span>
                        </div>
                        <div class="transform transition-all duration-300 hover:scale-[1.02]">
                            <label class="block text-sm font-semibold text-slate-700 mb-2">Size / Dimensions *</label>
                            <input type="text" id="order-size" placeholder="e.g., 10-inch, DN250" class="w-full px-4 md:px-5 py-3 md:py-3.5 rounded-xl form-input-enhanced focus:ring-2 focus:ring-blue-500 outline-none transition-all text-sm md:text-base">
                            <span class="validation-message hidden" id="order-size-error"></span>
                        </div>
                    </div>
                    
                    <div class="transform transition-all duration-300 hover:scale-[1.02]">
                        <label class="block text-sm font-semibold text-slate-700 mb-2">Material Specification *</label>
                        <select id="order-material" class="w-full px-4 md:px-5 py-3 md:py-3.5 rounded-xl form-input-enhanced focus:ring-2 focus:ring-blue-500 outline-none transition-all text-sm md:text-base">
                            <option value="">Select Material</option>
                            <option value="carbon">Carbon Steel (A105)</option>
                            <option value="stainless">Stainless Steel 316</option>
                            <option value="alloy">Alloy Steel</option>
                            <option value="duplex">Duplex Stainless</option>
                            <option value="custom">Custom Material</option>
                        </select>
                        <span class="validation-message hidden" id="order-material-error"></span>
                    </div>
                    
                    <div class="transform transition-all duration-300 hover:scale-[1.02]">
                        <label class="block text-sm font-semibold text-slate-700 mb-2">Additional Specifications</label>
                        <textarea rows="3" id="order-specs" class="w-full px-4 md:px-5 py-3 md:py-3.5 rounded-xl form-input-enhanced focus:ring-2 focus:ring-blue-500 outline-none transition-all text-sm md:text-base" placeholder="Pressure rating, surface finish, coating, etc."></textarea>
                    </div>
                    
                    <button type="button" onclick="validateAndNextStep(1, 2)" class="w-full py-3 md:py-4 btn-gradient text-white font-bold rounded-xl transition-all transform hover:-translate-y-1 active:scale-95 shadow-lg hover:shadow-xl text-sm md:text-base">
                        Next: Choose Supplier <i class="fas fa-arrow-right ml-2 transition-transform group-hover:translate-x-1"></i>
                    </button>
                </form>
            </div>
            
            <!-- Step 2: Supplier Selection -->
            <div id="order-step-2" class="p-4 md:p-8 hidden order-step">
                <div class="supplier-section">
                    <h3 class="text-lg md:text-xl font-bold text-slate-900 mb-4">Available Suppliers for <span id="selected-product-name">Product</span></h3>
                    <p class="text-slate-600 mb-4 text-sm md:text-base">Select a supplier to chat with them directly before ordering</p>
                    
                    <div class="space-y-4" id="suppliers-list">
                        <!-- Suppliers will be loaded here dynamically -->
                    </div>
                    
                    <div id="no-suppliers-message" class="hidden text-center py-8">
                        <div class="w-16 h-16 bg-slate-100 rounded-full flex items-center justify-center mx-auto mb-4">
                            <i class="fas fa-users text-slate-400 text-2xl"></i>
                        </div>
                        <h4 class="text-lg font-bold text-slate-700 mb-2">No Suppliers Available</h4>
                        <p class="text-slate-500 max-w-md mx-auto">No registered suppliers are available for this product at the moment.</p>
                        <button onclick="prevOrderStep(1)" class="mt-4 px-4 py-2 bg-blue-600 text-white rounded-lg hover:bg-blue-700 transition">
                            Go Back
                        </button>
                    </div>
                </div>
                
                <div class="flex gap-3 md:gap-4 mt-6">
                    <button type="button" onclick="prevOrderStep(1)" class="flex-1 py-3 md:py-3.5 bg-slate-200 text-slate-700 font-bold rounded-xl hover:bg-slate-300 transition transform hover:-translate-y-1 active:scale-95 text-sm md:text-base">
                        <i class="fas fa-arrow-left mr-2"></i>Back
                    </button>
                    <button type="button" onclick="validateAndNextStep(2, 3)" class="flex-1 py-3 md:py-3.5 btn-gradient text-white font-bold rounded-xl transition-all transform hover:-translate-y-1 active:scale-95 shadow-lg hover:shadow-xl text-sm md:text-base">
                        Next: Contact Details <i class="fas fa-arrow-right ml-2"></i>
                    </button>
                </div>
            </div>
            
            <!-- Step 3: Contact & Delivery -->
            <div id="order-step-3" class="p-4 md:p-8 hidden order-step">
                <form class="space-y-5 md:space-y-6">
                    <div class="bg-blue-50 rounded-xl p-4 md:p-5 mb-4">
                        <div class="flex items-center gap-3">
                            <div class="w-10 h-10 bg-green-100 rounded-full flex items-center justify-center">
                                <i class="fas fa-user-tie text-green-600"></i>
                            </div>
                            <div>
                                <h4 class="font-bold text-slate-900">Selected Supplier</h4>
                                <p class="text-slate-600" id="selected-supplier-display">Not selected</p>
                            </div>
                        </div>
                    </div>
                    
                    <div class="grid md:grid-cols-2 gap-4 md:gap-5">
                        <div class="transform transition-all duration-300 hover:scale-[1.02]">
                            <label class="block text-sm font-semibold text-slate-700 mb-2">First Name *</label>
                            <input type="text" id="order-firstname" required class="w-full px-4 md:px-5 py-3 md:py-3.5 rounded-xl form-input-enhanced focus:ring-2 focus:ring-blue-500 outline-none transition-all text-sm md:text-base">
                            <span class="validation-message hidden" id="order-firstname-error"></span>
                        </div>
                        <div class="transform transition-all duration-300 hover:scale-[1.02]">
                            <label class="block text-sm font-semibold text-slate-700 mb-2">Last Name *</label>
                            <input type="text" id="order-lastname" required class="w-full px-4 md:px-5 py-3 md:py-3.5 rounded-xl form-input-enhanced focus:ring-2 focus:ring-blue-500 outline-none transition-all text-sm md:text-base">
                            <span class="validation-message hidden" id="order-lastname-error"></span>
                        </div>
                    </div>
                    
                    <div class="grid md:grid-cols-2 gap-4 md:gap-5">
                        <div class="transform transition-all duration-300 hover:scale-[1.02]">
                            <label class="block text-sm font-semibold text-slate-700 mb-2">Email *</label>
                            <input type="email" id="order-email" required class="w-full px-4 md:px-5 py-3 md:py-3.5 rounded-xl form-input-enhanced focus:ring-2 focus:ring-blue-500 outline-none transition-all text-sm md:text-base">
                            <span class="validation-message hidden" id="order-email-error"></span>
                        </div>
                        <div class="transform transition-all duration-300 hover:scale-[1.02]">
                            <label class="block text-sm font-semibold text-slate-700 mb-2">Phone *</label>
                            <input type="tel" id="order-phone" required class="w-full px-4 md:px-5 py-3 md:py-3.5 rounded-xl form-input-enhanced focus:ring-2 focus:ring-blue-500 outline-none transition-all text-sm md:text-base">
                            <span class="validation-message hidden" id="order-phone-error"></span>
                        </div>
                    </div>
                    
                    <div class="transform transition-all duration-300 hover:scale-[1.02]">
                        <label class="block text-sm font-semibold text-slate-700 mb-2">Company *</label>
                        <input type="text" id="order-company" required class="w-full px-4 md:px-5 py-3 md:py-3.5 rounded-xl form-input-enhanced focus:ring-2 focus:ring-blue-500 outline-none transition-all text-sm md:text-base">
                        <span class="validation-message hidden" id="order-company-error"></span>
                    </div>
                    
                    <div class="transform transition-all duration-300 hover:scale-[1.02]">
                        <label class="block text-sm font-semibold text-slate-700 mb-2">Delivery Address</label>
                        <textarea rows="3" id="order-address" class="w-full px-4 md:px-5 py-3 md:py-3.5 rounded-xl form-input-enhanced focus:ring-2 focus:ring-blue-500 outline-none transition-all text-sm md:text-base" placeholder="Full address for delivery"></textarea>
                    </div>
                    
                    <div class="bg-blue-50 rounded-xl p-4 md:p-5 transform transition-all duration-300 hover:scale-[1.02]">
                        <label class="block text-sm font-semibold text-slate-700 mb-2">Preferred Contact Method</label>
                        <div class="flex flex-wrap gap-3 md:gap-4 mt-2">
                            <label class="flex items-center px-3 py-2 bg-white rounded-lg cursor-pointer hover:bg-blue-50 transition">
                                <input type="radio" name="contactMethod" value="email" checked class="mr-2 text-blue-600">
                                <span class="text-slate-700"><i class="fas fa-envelope mr-2"></i>Email</span>
                            </label>
                            <label class="flex items-center px-3 py-2 bg-white rounded-lg cursor-pointer hover:bg-blue-50 transition">
                                <input type="radio" name="contactMethod" value="phone" class="mr-2 text-blue-600">
                                <span class="text-slate-700"><i class="fas fa-phone mr-2"></i>Phone</span>
                            </label>
                            <label class="flex items-center px-3 py-2 bg-white rounded-lg cursor-pointer hover:bg-blue-50 transition">
                                <input type="radio" name="contactMethod" value="whatsapp" class="mr-2 text-blue-600">
                                <span class="text-slate-700"><i class="fab fa-whatsapp mr-2"></i>WhatsApp</span>
                            </label>
                        </div>
                    </div>
                    
                    <div class="flex gap-3 md:gap-4">
                        <button type="button" onclick="prevOrderStep(2)" class="flex-1 py-3 md:py-3.5 bg-slate-200 text-slate-700 font-bold rounded-xl hover:bg-slate-300 transition transform hover:-translate-y-1 active:scale-95 text-sm md:text-base">
                            <i class="fas fa-arrow-left mr-2"></i>Back
                        </button>
                        <button type="button" onclick="validateAndNextStep(3, 4)" class="flex-1 py-3 md:py-3.5 btn-gradient text-white font-bold rounded-xl transition-all transform hover:-translate-y-1 active:scale-95 shadow-lg hover:shadow-xl text-sm md:text-base">
                            Next: Review <i class="fas fa-arrow-right ml-2"></i>
                        </button>
                    </div>
                </form>
            </div>
            
            <!-- Step 4: Review & Submit -->
            <div id="order-step-4" class="p-4 md:p-8 hidden order-step">
                <div class="bg-gradient-to-br from-blue-50 to-slate-50 rounded-2xl p-4 md:p-6 mb-4 md:mb-6 transform transition-all duration-300 hover:scale-[1.02]">
                    <h4 class="font-bold text-slate-800 mb-3 md:mb-4 text-lg md:text-xl">Order Summary</h4>
                    <div class="space-y-3 md:space-y-4">
                        <div class="flex justify-between items-center p-3 bg-white/50 rounded-lg">
                            <span class="text-slate-600">Product:</span>
                            <span class="font-semibold text-slate-900" id="review-product">-</span>
                        </div>
                        <div class="flex justify-between items-center p-3 bg-white/50 rounded-lg">
                            <span class="text-slate-600">Supplier:</span>
                            <span class="font-semibold text-slate-900" id="review-supplier">-</span>
                        </div>
                        <div class="flex justify-between items-center p-3 bg-white/50 rounded-lg">
                            <span class="text-slate-600">Quantity:</span>
                            <span class="font-semibold text-slate-900" id="review-quantity">-</span>
                        </div>
                        <div class="flex justify-between items-center p-3 bg-white/50 rounded-lg">
                            <span class="text-slate-600">Material:</span>
                            <span class="font-semibold text-slate-900" id="review-material">-</span>
                        </div>
                        <div class="flex justify-between items-center p-3 bg-white/50 rounded-lg">
                            <span class="text-slate-600">Contact Method:</span>
                            <span class="font-semibold text-slate-900" id="review-contact">-</span>
                        </div>
                        <div class="flex justify-between items-center p-3 bg-green-50 rounded-lg border border-green-200">
                            <span class="text-green-700">Response Time:</span>
                            <span class="font-bold text-green-600">Within 24 hours</span>
                        </div>
                    </div>
                </div>
                
                <div class="bg-blue-50 rounded-2xl p-4 md:p-6 mb-4 md:mb-6 transform transition-all duration-300 hover:scale-[1.02]">
                    <h4 class="font-bold text-blue-800 mb-3 flex items-center gap-2 text-lg md:text-xl">
                        <i class="fas fa-info-circle"></i>What happens next?
                    </h4>
                    <div class="text-blue-700 text-sm md:text-base space-y-2">
                        <p>1. Your order is sent <strong>directly to the selected supplier</strong></p>
                        <p>2. Supplier will contact you via your preferred method</p>
                        <p>3. You'll receive <strong>pricing, delivery expectations, and invoice</strong></p>
                        <p>4. Finalize order and schedule production/delivery</p>
                    </div>
                </div>
                
                <div class="flex gap-3 md:gap-4">
                    <button type="button" onclick="prevOrderStep(3)" class="flex-1 py-3 md:py-3.5 bg-slate-200 text-slate-700 font-bold rounded-xl hover:bg-slate-300 transition transform hover:-translate-y-1 active:scale-95 text-sm md:text-base">
                        <i class="fas fa-arrow-left mr-2"></i>Back
                    </button>
                    <button type="button" onclick="submitOrder()" class="flex-1 py-3 md:py-3.5 bg-gradient-to-r from-green-600 to-green-800 text-white font-bold rounded-xl hover:from-green-700 hover:to-green-900 transition transform hover:-translate-y-1 active:scale-95 shadow-lg hover:shadow-xl text-sm md:text-base">
                        <i class="fas fa-paper-plane mr-2"></i>Submit to Supplier
                    </button>
                </div>
            </div>
            
            <!-- Step 5: Confirmation -->
            <div id="order-step-5" class="p-4 md:p-8 hidden order-step">
                <div class="text-center py-6 md:py-8">
                    <div class="w-16 h-16 md:w-20 md:h-20 bg-green-100 rounded-full flex items-center justify-center mx-auto mb-4 md:mb-6 animate-bounce">
                        <i class="fas fa-check text-green-600 text-2xl md:text-3xl"></i>
                    </div>
                    <h2 class="text-2xl md:text-3xl font-bold text-slate-900 mb-3 md:mb-4 animate-pulse">Order Sent to Supplier!</h2>
                    
                    <div class="bg-gradient-to-br from-green-50 to-blue-50 rounded-2xl p-4 md:p-6 mb-4 md:mb-6 transform transition-all duration-500 hover:scale-[1.02]">
                        <p class="text-slate-700 mb-3 md:mb-4 text-sm md:text-base">
                            <strong>Your order has been sent directly to the selected supplier.</strong>
                        </p>
                        <p class="text-slate-600 text-sm md:text-base mb-3">
                            <i class="fas fa-user-tie text-blue-500 mr-2"></i>
                            <span id="confirmation-supplier">Supplier</span> will contact you within <strong>24 hours</strong> with:
                        </p>
                        <ul class="text-slate-600 text-sm md:text-base mt-3 space-y-2">
                            <li class="flex items-center gap-2"><i class="fas fa-rupee-sign text-green-500"></i>Detailed pricing and quotation</li>
                            <li class="flex items-center gap-2"><i class="fas fa-truck text-blue-500"></i>Delivery timeline and expectations</li>
                            <li class="flex items-center gap-2"><i class="fas fa-file-invoice-dollar text-purple-500"></i>Proforma invoice for approval</li>
                        </ul>
                    </div>
                    
                    <div class="text-sm md:text-base text-slate-500 mb-4 md:mb-6 bg-white p-3 rounded-lg inline-block">
                        Order Reference: <strong id="order-reference" class="text-blue-600">UF-ORD-123456</strong>
                    </div>
                    
                    <div class="bg-yellow-50 border border-yellow-200 rounded-xl p-3 md:p-4 mb-4 md:mb-6 transform transition-all duration-300 hover:scale-[1.02]">
                        <p class="text-sm md:text-base text-yellow-800">
                            <i class="fas fa-exclamation-circle mr-2"></i>
                            <strong>Note:</strong> The supplier will contact you directly via the email/phone you provided.
                        </p>
                    </div>
                    
                    <div class="space-y-3 md:space-y-4">
                        <button onclick="trackOrderWithCode()" class="w-full py-3 md:py-3.5 bg-gradient-to-r from-purple-600 to-purple-800 text-white font-bold rounded-xl hover:from-purple-700 hover:to-purple-900 transition transform hover:-translate-y-1 active:scale-95 shadow-lg hover:shadow-xl text-sm md:text-base">
                            <i class="fas fa-search mr-2"></i>Track This Order
                        </button>
                        <button onclick="closeOrderModal()" class="w-full py-3 md:py-3.5 btn-gradient text-white font-bold rounded-xl transition transform hover:-translate-y-1 active:scale-95 shadow-lg hover:shadow-xl text-sm md:text-base">
                            <i class="fas fa-home mr-2"></i>Return to Home
                        </button>
                    </div>
                </div>
            </div>
        </div>
    </div>

    <!-- Order Tracking Modal -->
    <div id="tracking-modal" class="fixed inset-0 bg-black/60 backdrop-blur-md hidden items-center justify-center p-4 z-50">
        <div class="bg-white w-full max-w-4xl rounded-3xl shadow-2xl overflow-hidden relative" style="max-height: 90vh; overflow-y: auto;">
            <button onclick="closeTrackingModal()" class="absolute top-4 right-4 text-slate-400 hover:text-slate-700 z-10">
                <i class="fas fa-times text-2xl"></i>
            </button>
            
            <div class="p-4 md:p-8">
                <div class="text-center mb-6 md:mb-8">
                    <h2 class="text-2xl md:text-3xl font-bold text-slate-900">Order Tracking</h2>
                    <p class="text-slate-600 mt-2">Track your order status in real-time</p>
                </div>
                
                <!-- Search Section -->
                <div class="mb-6 md:mb-8">
                    <div class="flex flex-col md:flex-row gap-3 md:gap-4">
                        <div class="flex-1 relative">
                            <input type="text" id="tracking-input" placeholder="Enter Order ID or Reference Number" 
                                   class="w-full px-4 md:px-5 py-3 md:py-3.5 rounded-xl border-2 border-slate-300 focus:ring-2 focus:ring-blue-500 outline-none transition text-sm md:text-base">
                            <button onclick="searchOrder()" class="absolute right-2 top-2 px-4 py-2 bg-blue-600 text-white rounded-lg hover:bg-blue-700 transition">
                                <i class="fas fa-search"></i>
                            </button>
                        </div>
                        <button onclick="showMyOrders()" class="px-4 md:px-6 py-3 md:py-3.5 bg-slate-200 text-slate-700 rounded-xl font-bold hover:bg-slate-300 transition flex items-center gap-2 text-sm md:text-base">
                            <i class="fas fa-history"></i>My Orders
                        </button>
                    </div>
                    <p class="text-slate-500 text-xs md:text-sm mt-2">
                        Enter your order reference number (e.g., UF-ORD-123456) or order ID
                    </p>
                </div>
                
                <!-- Tracking Results -->
                <div id="tracking-results" class="hidden">
                    <div class="bg-gradient-to-br from-slate-900 to-blue-900 rounded-2xl p-4 md:p-6 text-white mb-4 md:mb-6">
                        <div class="flex flex-col md:flex-row justify-between items-start md:items-center gap-4">
                            <div>
                                <h3 class="text-lg md:text-xl font-bold mb-1" id="tracking-order-id">#UF-ORD-123456</h3>
                                <p class="text-blue-300 text-sm" id="tracking-product-name">Long Weld Neck Flange</p>
                            </div>
                            <div class="bg-white/20 rounded-lg px-3 md:px-4 py-1 md:py-2">
                                <span class="font-bold text-sm md:text-base" id="tracking-status">Processing</span>
                            </div>
                        </div>
                        <div class="grid grid-cols-2 md:grid-cols-4 gap-3 md:gap-4 mt-4">
                            <div>
                                <p class="text-blue-300 text-xs">Quantity</p>
                                <p class="font-bold" id="tracking-quantity">50 pieces</p>
                            </div>
                            <div>
                                <p class="text-blue-300 text-xs">Order Date</p>
                                <p class="font-bold" id="tracking-date">Mar 15, 2024</p>
                            </div>
                            <div>
                                <p class="text-blue-300 text-xs">Estimated Delivery</p>
                                <p class="font-bold" id="tracking-delivery">Mar 25, 2024</p>
                            </div>
                            <div>
                                <p class="text-blue-300 text-xs">Total Amount</p>
                                <p class="font-bold" id="tracking-amount">₹245,000</p>
                            </div>
                        </div>
                    </div>
                    
                    <!-- Tracking Timeline -->
                    <div class="tracking-container p-4 md:p-6">
                        <h4 class="font-bold text-lg md:text-xl text-slate-900 mb-4 md:mb-6">Order Progress</h4>
                        <div id="tracking-timeline">
                            <!-- Timeline will be populated by JavaScript -->
                        </div>
                    </div>
                    
                    <!-- Order Details -->
                    <div class="mt-4 md:mt-6 grid md:grid-cols-2 gap-4 md:gap-6">
                        <div class="bg-slate-50 rounded-xl p-4 md:p-5">
                            <h5 class="font-bold text-slate-800 mb-3">Customer Details</h5>
                            <div class="space-y-2 text-sm md:text-base">
                                <p><span class="text-slate-600">Name:</span> <span id="tracking-customer-name" class="font-medium">John Doe</span></p>
                                <p><span class="text-slate-600">Company:</span> <span id="tracking-company" class="font-medium">Oil & Gas Corp</span></p>
                                <p><span class="text-slate-600">Contact:</span> <span id="tracking-contact" class="font-medium">john@example.com</span></p>
                            </div>
                        </div>
                        <div class="bg-slate-50 rounded-xl p-4 md:p-5">
                            <h5 class="font-bold text-slate-800 mb-3">Supplier Information</h5>
                            <div class="space-y-2 text-sm md:text-base">
                                <p><span class="text-slate-600">Supplier:</span> <span id="tracking-supplier" class="font-medium">Precision Flange Co.</span></p>
                                <p><span class="text-slate-600">Contact:</span> <span id="tracking-supplier-contact" class="font-medium">sales@precisionflange.com</span></p>
                                <p><span class="text-slate-600">Phone:</span> <span id="tracking-supplier-phone" class="font-medium">+91 9876543210</span></p>
                            </div>
                        </div>
                    </div>
                    
                    <!-- Action Buttons -->
                    <div class="mt-6 flex flex-col sm:flex-row gap-3 md:gap-4">
                        <button onclick="downloadInvoice()" class="flex-1 py-3 bg-blue-600 text-white rounded-xl font-bold hover:bg-blue-700 transition flex items-center justify-center gap-2">
                            <i class="fas fa-download"></i>Download Invoice
                        </button>
                        <button onclick="contactSupplier()" class="flex-1 py-3 bg-green-600 text-white rounded-xl font-bold hover:bg-green-700 transition flex items-center justify-center gap-2">
                            <i class="fas fa-headset"></i>Contact Supplier
                        </button>
                    </div>
                </div>
                
                <!-- My Orders Section -->
                <div id="my-orders-section" class="hidden">
                    <h4 class="font-bold text-lg md:text-xl text-slate-900 mb-4 md:mb-6">My Recent Orders</h4>
                    <div class="space-y-4" id="my-orders-list">
                        <!-- Orders will be populated by JavaScript -->
                    </div>
                </div>
                
                <!-- Empty State -->
                <div id="tracking-empty" class="text-center py-8 md:py-12">
                    <div class="w-16 h-16 md:w-20 md:h-20 bg-slate-100 rounded-full flex items-center justify-center mx-auto mb-4 md:mb-6">
                        <i class="fas fa-search text-slate-400 text-2xl md:text-3xl"></i>
                    </div>
                    <h4 class="text-lg md:text-xl font-bold text-slate-700 mb-2">Track Your Order</h4>
                    <p class="text-slate-500 max-w-md mx-auto text-sm md:text-base">
                        Enter your order reference number above to view real-time tracking information, delivery status, and order details.
                    </p>
                </div>
                
                <!-- Loading State -->
                <div id="tracking-loading" class="hidden text-center py-8 md:py-12">
                    <div class="w-16 h-16 md:w-20 md:h-20 shimmer rounded-full mx-auto mb-4 md:mb-6"></div>
                    <div class="space-y-3">
                        <div class="h-4 shimmer rounded w-48 mx-auto"></div>
                        <div class="h-3 shimmer rounded w-32 mx-auto"></div>
                    </div>
                </div>
            </div>
        </div>
    </div>

    <!-- Dashboard Modal -->
    <div id="dashboard-modal" class="fixed inset-0 bg-black/60 backdrop-blur-md hidden items-center justify-center p-4 z-50">
        <div class="bg-white w-full max-w-7xl h-[90vh] rounded-3xl shadow-2xl overflow-hidden relative flex flex-col">
            <div class="px-4 md:px-8 pt-6 md:pt-8 pb-4 border-b border-slate-200">
                <div class="flex justify-between items-center">
                    <div>
                        <h2 class="text-xl md:text-3xl font-bold text-slate-900">Supplier Dashboard</h2>
                        <p class="text-slate-600 mt-1 text-sm md:text-base">Manage your orders, inventory, and customer interactions</p>
                    </div>
                    <div class="flex items-center gap-3 md:gap-4">
                        <div class="relative group">
                            <button class="w-8 h-8 md:w-10 md:h-10 rounded-full bg-slate-100 flex items-center justify-center text-slate-700 hover:bg-slate-200 transition">
                                <i class="fas fa-bell text-sm md:text-base"></i>
                            </button>
                            <span class="absolute top-0 right-0 w-2 h-2 md:w-3 md:h-3 bg-red-500 rounded-full border-2 border-white"></span>
                        </div>
                        <button onclick="closeDashboard()" class="text-slate-400 hover:text-slate-700">
                            <i class="fas fa-times text-xl md:text-2xl"></i>
                        </button>
                    </div>
                </div>
                
                <!-- Dashboard Tabs -->
                <div class="flex gap-1 mt-4 md:mt-6 border-b border-slate-200 overflow-x-auto">
                    <button onclick="switchDashboardTab('overview')" class="tab-button active whitespace-nowrap text-sm md:text-base">
                        <i class="fas fa-chart-bar mr-2"></i>Overview
                    </button>
                    <button onclick="switchDashboardTab('orders')" class="tab-button whitespace-nowrap text-sm md:text-base">
                        <i class="fas fa-shopping-cart mr-2"></i>Orders
                    </button>
                    <button onclick="switchDashboardTab('inventory')" class="tab-button whitespace-nowrap text-sm md:text-base">
                        <i class="fas fa-boxes mr-2"></i>Inventory
                    </button>
                    <button onclick="switchDashboardTab('customers')" class="tab-button whitespace-nowrap text-sm md:text-base">
                        <i class="fas fa-users mr-2"></i>Customers
                    </button>
                    <button onclick="switchDashboardTab('analytics')" class="tab-button whitespace-nowrap text-sm md:text-base">
                        <i class="fas fa-chart-line mr-2"></i>Analytics
                    </button>
                    <button onclick="switchDashboardTab('settings')" class="tab-button whitespace-nowrap text-sm md:text-base">
                        <i class="fas fa-cog mr-2"></i>Settings
                    </button>
                </div>
            </div>
            
            <!-- Dashboard Content -->
            <div class="flex-1 overflow-auto p-4 md:p-8">
                <!-- Overview Tab -->
                <div id="dashboard-overview" class="tab-content active space-y-6 md:space-y-8">
                    <!-- Stats Cards -->
                    <div class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-4 gap-4 md:gap-6">
                        <div class="stat-card sales">
                            <div class="flex justify-between items-start">
                                <div>
                                    <p class="text-sm opacity-90">Total Revenue</p>
                                    <h3 class="text-2xl md:text-3xl font-bold mt-2">₹2,847,500</h3>
                                    <p class="text-sm mt-2 flex items-center">
                                        <i class="fas fa-arrow-up mr-1"></i> 12.5% from last month
                                    </p>
                                </div>
                                <div class="w-10 h-10 md:w-12 md:h-12 bg-white/20 rounded-lg flex items-center justify-center">
                                    <i class="fas fa-rupee-sign text-xl md:text-2xl"></i>
                                </div>
                            </div>
                        </div>
                        
                        <div class="stat-card orders">
                            <div class="flex justify-between items-start">
                                <div>
                                    <p class="text-sm opacity-90">Active Orders</p>
                                    <h3 class="text-2xl md:text-3xl font-bold mt-2">47</h3>
                                    <p class="text-sm mt-2 flex items-center">
                                        <i class="fas fa-clock mr-1"></i> 8 pending approval
                                    </p>
                                </div>
                                <div class="w-10 h-10 md:w-12 md:h-12 bg-white/20 rounded-lg flex items-center justify-center">
                                    <i class="fas fa-shopping-cart text-xl md:text-2xl"></i>
                                </div>
                            </div>
                        </div>
                        
                        <div class="stat-card customers">
                            <div class="flex justify-between items-start">
                                <div>
                                    <p class="text-sm opacity-90">Active Customers</p>
                                    <h3 class="text-2xl md:text-3xl font-bold mt-2">156</h3>
                                    <p class="text-sm mt-2 flex items-center">
                                        <i class="fas fa-user-plus mr-1"></i> +12 this month
                                    </p>
                                </div>
                                <div class="w-10 h-10 md:w-12 md:h-12 bg-white/20 rounded-lg flex items-center justify-center">
                                    <i class="fas fa-users text-xl md:text-2xl"></i>
                                </div>
                            </div>
                        </div>
                        
                        <div class="stat-card">
                            <div class="flex justify-between items-start">
                                <div>
                                    <p class="text-sm opacity-90">Inventory Value</p>
                                    <h3 class="text-2xl md:text-3xl font-bold mt-2">₹5,620,000</h3>
                                    <p class="text-sm mt-2 flex items-center">
                                        <i class="fas fa-box mr-1"></i> 87 items in stock
                                    </p>
                                </div>
                                <div class="w-10 h-10 md:w-12 md:h-12 bg-white/20 rounded-lg flex items-center justify-center">
                                    <i class="fas fa-warehouse text-xl md:text-2xl"></i>
                                </div>
                            </div>
                        </div>
                    </div>
                    
                    <!-- Charts and Recent Orders -->
                    <div class="grid lg:grid-cols-2 gap-6 md:gap-8">
                        <!-- Sales Chart -->
                        <div class="dashboard-card">
                            <h3 class="font-bold text-lg text-slate-900 mb-4">Revenue Trend</h3>
                            <div class="h-64">
                                <canvas id="salesChart"></canvas>
                            </div>
                        </div>
                        
                        <!-- Recent Orders -->
                        <div class="dashboard-card">
                            <div class="flex justify-between items-center mb-4">
                                <h3 class="font-bold text-lg text-slate-900">Recent Orders</h3>
                                <a href="#" class="text-blue-600 text-sm font-medium hover:text-blue-800">View All</a>
                            </div>
                            <div class="space-y-4">
                                <div class="flex items-center justify-between p-3 bg-slate-50 rounded-lg">
                                    <div>
                                        <div class="font-medium">#ORD-7842</div>
                                        <div class="text-sm text-slate-500">Weld Neck Flange</div>
                                    </div>
                                    <div class="text-right">
                                        <div class="font-medium">₹245,000</div>
                                        <span class="badge badge-warning">Processing</span>
                                    </div>
                                </div>
                                <div class="flex items-center justify-between p-3 bg-slate-50 rounded-lg">
                                    <div>
                                        <div class="font-medium">#ORD-7841</div>
                                        <div class="text-sm text-slate-500">Long Weld Neck</div>
                                    </div>
                                    <div class="text-right">
                                        <div class="font-medium">₹187,500</div>
                                        <span class="badge badge-success">Shipped</span>
                                    </div>
                                </div>
                                <div class="flex items-center justify-between p-3 bg-slate-50 rounded-lg">
                                    <div>
                                        <div class="font-medium">#ORD-7840</div>
                                        <div class="text-sm text-slate-500">Blind Flange</div>
                                    </div>
                                    <div class="text-right">
                                        <div class="font-medium">₹92,300</div>
                                        <span class="badge badge-danger">Pending</span>
                                    </div>
                                </div>
                                <div class="flex items-center justify-between p-3 bg-slate-50 rounded-lg">
                                    <div>
                                        <div class="font-medium">#ORD-7839</div>
                                        <div class="text-sm text-slate-500">Plasma CNC Cutting</div>
                                    </div>
                                    <div class="text-right">
                                        <div class="font-medium">₹315,800</div>
                                        <span class="badge badge-info">Approved</span>
                                    </div>
                                </div>
                            </div>
                        </div>
                    </div>
                    
                    <!-- Quick Stats -->
                    <div class="grid md:grid-cols-3 gap-4 md:gap-6">
                        <div class="dashboard-card">
                            <h3 class="font-bold text-lg text-slate-900 mb-4">Order Status</h3>
                            <div class="space-y-3">
                                <div>
                                    <div class="flex justify-between mb-1">
                                        <span class="text-sm">Pending Approval</span>
                                        <span class="text-sm font-medium">8</span>
                                    </div>
                                    <div class="progress-bar">
                                        <div class="progress-fill" style="width: 17%"></div>
                                    </div>
                                </div>
                                <div>
                                    <div class="flex justify-between mb-1">
                                        <span class="text-sm">In Production</span>
                                        <span class="text-sm font-medium">15</span>
                                    </div>
                                    <div class="progress-bar">
                                        <div class="progress-fill" style="width: 32%"></div>
                                    </div>
                                </div>
                                <div>
                                    <div class="flex justify-between mb-1">
                                        <span class="text-sm">Ready to Ship</span>
                                        <span class="text-sm font-medium">12</span>
                                    </div>
                                    <div class="progress-bar">
                                        <div class="progress-fill" style="width: 26%"></div>
                                    </div>
                                </div>
                                <div>
                                    <div class="flex justify-between mb-1">
                                        <span class="text-sm">Delivered</span>
                                        <span class="text-sm font-medium">12</span>
                                    </div>
                                    <div class="progress-bar">
                                        <div class="progress-fill" style="width: 26%"></div>
                                    </div>
                                </div>
                            </div>
                        </div>
                        
                        <div class="dashboard-card">
                            <h3 class="font-bold text-lg text-slate-900 mb-4">Top Products</h3>
                            <div class="space-y-3">
                                <div class="flex items-center justify-between">
                                    <div class="flex items-center gap-3">
                                        <div class="w-10 h-10 bg-blue-100 rounded-lg flex items-center justify-center">
                                            <i class="fas fa-fire text-blue-600"></i>
                                        </div>
                                        <div>
                                            <div class="font-medium">Weld Neck Flange</div>
                                            <div class="text-sm text-slate-500">₹1.2M revenue</div>
                                        </div>
                                    </div>
                                    <div class="text-lg font-bold">42%</div>
                                </div>
                                <div class="flex items-center justify-between">
                                    <div class="flex items-center gap-3">
                                        <div class="w-10 h-10 bg-green-100 rounded-lg flex items-center justify-center">
                                            <i class="fas fa-ruler-vertical text-green-600"></i>
                                        </div>
                                        <div>
                                            <div class="font-medium">Long Weld Neck</div>
                                            <div class="text-sm text-slate-500">₹850K revenue</div>
                                        </div>
                                    </div>
                                    <div class="text-lg font-bold">30%</div>
                                </div>
                                <div class="flex items-center justify-between">
                                    <div class="flex items-center gap-3">
                                        <div class="w-10 h-10 bg-purple-100 rounded-lg flex items-center justify-center">
                                            <i class="fas fa-bolt text-purple-600"></i>
                                        </div>
                                        <div>
                                            <div class="font-medium">Plasma CNC</div>
                                            <div class="text-sm text-slate-500">₹620K revenue</div>
                                        </div>
                                    </div>
                                    <div class="text-lg font-bold">22%</div>
                                </div>
                            </div>
                        </div>
                        
                        <div class="dashboard-card">
                            <h3 class="font-bold text-lg text-slate-900 mb-4">Quick Actions</h3>
                            <div class="space-y-3">
                                <button class="w-full py-3 bg-blue-50 text-blue-700 rounded-lg font-medium hover:bg-blue-100 transition flex items-center justify-center gap-2">
                                    <i class="fas fa-plus"></i> Add New Product
                                </button>
                                <button class="w-full py-3 bg-green-50 text-green-700 rounded-lg font-medium hover:bg-green-100 transition flex items-center justify-center gap-2">
                                    <i class="fas fa-file-invoice"></i> Create Invoice
                                </button>
                                <button class="w-full py-3 bg-purple-50 text-purple-700 rounded-lg font-medium hover:bg-purple-100 transition flex items-center justify-center gap-2">
                                    <i class="fas fa-chart-bar"></i> Generate Report
                                </button>
                                <button class="w-full py-3 bg-orange-50 text-orange-700 rounded-lg font-medium hover:bg-orange-100 transition flex items-center justify-center gap-2">
                                    <i class="fas fa-box"></i> Update Inventory
                                </button>
                            </div>
                        </div>
                    </div>
                </div>
                
                <!-- Orders Tab -->
                <div id="dashboard-orders" class="tab-content hidden">
                    <div class="flex justify-between items-center mb-6">
                        <h3 class="text-xl md:text-2xl font-bold text-slate-900">Order Management</h3>
                        <button class="px-3 md:px-4 py-2 bg-blue-600 text-white rounded-lg hover:bg-blue-700 transition flex items-center gap-2">
                            <i class="fas fa-plus"></i> New Order
                        </button>
                    </div>
                    
                    <div class="table-container">
                        <table class="w-full">
                            <thead>
                                <tr>
                                    <th>Order ID</th>
                                    <th>Customer</th>
                                    <th>Product</th>
                                    <th>Quantity</th>
                                    <th>Amount</th>
                                    <th>Status</th>
                                    <th>Date</th>
                                    <th>Actions</th>
                                </tr>
                            </thead>
                            <tbody>
                                <tr>
                                    <td class="font-medium">#ORD-7842</td>
                                    <td>Oil & Gas Corp</td>
                                    <td>Weld Neck Flange</td>
                                    <td>50</td>
                                    <td class="font-bold">₹245,000</td>
                                    <td><span class="badge badge-warning">Processing</span></td>
                                    <td>2024-03-15</td>
                                    <td>
                                        <button class="text-blue-600 hover:text-blue-800 mr-3">
                                            <i class="fas fa-eye"></i>
                                        </button>
                                        <button class="text-green-600 hover:text-green-800">
                                            <i class="fas fa-edit"></i>
                                        </button>
                                    </td>
                                </tr>
                                <tr>
                                    <td class="font-medium">#ORD-7841</td>
                                    <td>PowerGen Ltd</td>
                                    <td>Long Weld Neck</td>
                                    <td>25</td>
                                    <td class="font-bold">₹187,500</td>
                                    <td><span class="badge badge-success">Shipped</span></td>
                                    <td>2024-03-14</td>
                                    <td>
                                        <button class="text-blue-600 hover:text-blue-800 mr-3">
                                            <i class="fas fa-eye"></i>
                                        </button>
                                        <button class="text-green-600 hover:text-green-800">
                                            <i class="fas fa-edit"></i>
                                        </button>
                                    </td>
                                </tr>
                                <tr>
                                    <td class="font-medium">#ORD-7840</td>
                                    <td>Marine Solutions</td>
                                    <td>Blind Flange</td>
                                    <td>100</td>
                                    <td class="font-bold">₹92,300</td>
                                    <td><span class="badge badge-danger">Pending</span></td>
                                    <td>2024-03-13</td>
                                    <td>
                                        <button class="text-blue-600 hover:text-blue-800 mr-3">
                                            <i class="fas fa-eye"></i>
                                        </button>
                                        <button class="text-green-600 hover:text-green-800">
                                            <i class="fas fa-edit"></i>
                                        </button>
                                    </td>
                                </tr>
                                <tr>
                                    <td class="font-medium">#ORD-7839</td>
                                    <td>Chemical Process</td>
                                    <td>Plasma CNC Cutting</td>
                                    <td>1</td>
                                    <td class="font-bold">₹315,800</td>
                                    <td><span class="badge badge-info">Approved</span></td>
                                    <td>2024-03-12</td>
                                    <td>
                                        <button class="text-blue-600 hover:text-blue-800 mr-3">
                                            <i class="fas fa-eye"></i>
                                        </button>
                                        <button class="text-green-600 hover:text-green-800">
                                            <i class="fas fa-edit"></i>
                                        </button>
                                    </td>
                                </tr>
                                <tr>
                                    <td class="font-medium">#ORD-7838</td>
                                    <td>Construction Co</td>
                                    <td>Slip-On Flange</td>
                                    <td>200</td>
                                    <td class="font-bold">₹156,400</td>
                                    <td><span class="badge badge-success">Delivered</span></td>
                                    <td>2024-03-10</td>
                                    <td>
                                        <button class="text-blue-600 hover:text-blue-800 mr-3">
                                            <i class="fas fa-eye"></i>
                                        </button>
                                        <button class="text-green-600 hover:text-green-800">
                                            <i class="fas fa-edit"></i>
                                        </button>
                                    </td>
                                </tr>
                            </tbody>
                        </table>
                    </div>
                </div>
                
                <!-- Inventory Tab -->
                <div id="dashboard-inventory" class="tab-content hidden">
                    <div class="flex justify-between items-center mb-6">
                        <h3 class="text-xl md:text-2xl font-bold text-slate-900">Inventory Management</h3>
                        <button class="px-3 md:px-4 py-2 bg-blue-600 text-white rounded-lg hover:bg-blue-700 transition flex items-center gap-2">
                            <i class="fas fa-plus"></i> Add Stock
                        </button>
                    </div>
                    
                    <div class="grid md:grid-cols-2 lg:grid-cols-3 gap-4 md:gap-6 mb-6 md:mb-8">
                        <div class="dashboard-card">
                            <div class="flex items-center justify-between">
                                <div>
                                    <div class="text-sm text-slate-500">Total Items</div>
                                    <div class="text-2xl md:text-3xl font-bold mt-1">87</div>
                                </div>
                                <div class="w-10 h-10 md:w-12 md:h-12 bg-blue-100 rounded-lg flex items-center justify-center">
                                    <i class="fas fa-boxes text-blue-600 text-lg md:text-xl"></i>
                                </div>
                            </div>
                        </div>
                        <div class="dashboard-card">
                            <div class="flex items-center justify-between">
                                <div>
                                    <div class="text-sm text-slate-500">Low Stock Items</div>
                                    <div class="text-2xl md:text-3xl font-bold mt-1">12</div>
                                </div>
                                <div class="w-10 h-10 md:w-12 md:h-12 bg-red-100 rounded-lg flex items-center justify-center">
                                    <i class="fas fa-exclamation-triangle text-red-600 text-lg md:text-xl"></i>
                                </div>
                            </div>
                        </div>
                        <div class="dashboard-card">
                            <div class="flex items-center justify-between">
                                <div>
                                    <div class="text-sm text-slate-500">Out of Stock</div>
                                    <div class="text-2xl md:text-3xl font-bold mt-1">3</div>
                                </div>
                                <div class="w-10 h-10 md:w-12 md:h-12 bg-orange-100 rounded-lg flex items-center justify-center">
                                    <i class="fas fa-times-circle text-orange-600 text-lg md:text-xl"></i>
                                </div>
                            </div>
                        </div>
                    </div>
                    
                    <div class="table-container">
                        <table class="w-full">
                            <thead>
                                <tr>
                                    <th>Product</th>
                                    <th>SKU</th>
                                    <th>Current Stock</th>
                                    <th>Reorder Level</th>
                                    <th>Value</th>
                                    <th>Status</th>
                                    <th>Actions</th>
                                </tr>
                            </thead>
                            <tbody>
                                <tr>
                                    <td class="font-medium">Weld Neck Flange DN50</td>
                                    <td>SKU-WNF-50</td>
                                    <td>250</td>
                                    <td>100</td>
                                    <td class="font-bold">₹1,250,000</td>
                                    <td><span class="badge badge-success">In Stock</span></td>
                                    <td>
                                        <button class="text-blue-600 hover:text-blue-800 mr-3">
                                            <i class="fas fa-edit"></i>
                                        </button>
                                        <button class="text-red-600 hover:text-red-800">
                                            <i class="fas fa-trash"></i>
                                        </button>
                                    </td>
                                </tr>
                                <tr>
                                    <td class="font-medium">Long Weld Neck DN100</td>
                                    <td>SKU-LWN-100</td>
                                    <td>85</td>
                                    <td>50</td>
                                    <td class="font-bold">₹850,000</td>
                                    <td><span class="badge badge-warning">Low Stock</span></td>
                                    <td>
                                        <button class="text-blue-600 hover:text-blue-800 mr-3">
                                            <i class="fas fa-edit"></i>
                                        </button>
                                        <button class="text-red-600 hover:text-red-800">
                                            <i class="fas fa-trash"></i>
                                        </button>
                                    </td>
                                </tr>
                                <tr>
                                    <td class="font-medium">Blind Flange DN80</td>
                                    <td>SKU-BF-80</td>
                                    <td>0</td>
                                    <td>25</td>
                                    <td class="font-bold">₹0</td>
                                    <td><span class="badge badge-danger">Out of Stock</span></td>
                                    <td>
                                        <button class="text-blue-600 hover:text-blue-800 mr-3">
                                            <i class="fas fa-edit"></i>
                                        </button>
                                        <button class="text-red-600 hover:text-red-800">
                                            <i class="fas fa-trash"></i>
                                        </button>
                                    </td>
                                </tr>
                                <tr>
                                    <td class="font-medium">Slip-On Flange DN40</td>
                                    <td>SKU-SOF-40</td>
                                    <td>120</td>
                                    <td>75</td>
                                    <td class="font-bold">₹480,000</td>
                                    <td><span class="badge badge-success">In Stock</span></td>
                                    <td>
                                        <button class="text-blue-600 hover:text-blue-800 mr-3">
                                            <i class="fas fa-edit"></i>
                                        </button>
                                        <button class="text-red-600 hover:text-red-800">
                                            <i class="fas fa-trash"></i>
                                        </button>
                                    </td>
                                </tr>
                                <tr>
                                    <td class="font-medium">Puddle Flange DN150</td>
                                    <td>SKU-PF-150</td>
                                    <td>45</td>
                                    <td>30</td>
                                    <td class="font-bold">₹675,000</td>
                                    <td><span class="badge badge-warning">Low Stock</span></td>
                                    <td>
                                        <button class="text-blue-600 hover:text-blue-800 mr-3">
                                            <i class="fas fa-edit"></i>
                                        </button>
                                        <button class="text-red-600 hover:text-red-800">
                                            <i class="fas fa-trash"></i>
                                        </button>
                                    </td>
                                </tr>
                            </tbody>
                        </table>
                    </div>
                </div>
                
                <!-- Customers Tab -->
                <div id="dashboard-customers" class="tab-content hidden">
                    <div class="flex justify-between items-center mb-6">
                        <h3 class="text-xl md:text-2xl font-bold text-slate-900">Customer Management</h3>
                        <button class="px-3 md:px-4 py-2 bg-blue-600 text-white rounded-lg hover:bg-blue-700 transition flex items-center gap-2">
                            <i class="fas fa-user-plus"></i> Add Customer
                        </button>
                    </div>
                    
                    <div class="grid md:grid-cols-3 gap-4 md:gap-6 mb-6 md:mb-8">
                        <div class="dashboard-card">
                            <div class="flex items-center gap-4">
                                <div class="w-14 h-14 md:w-16 md:h-16 bg-blue-100 rounded-full flex items-center justify-center">
                                    <i class="fas fa-building text-blue-600 text-xl md:text-2xl"></i>
                                </div>
                                <div>
                                    <div class="text-sm text-slate-500">Total Customers</div>
                                    <div class="text-2xl md:text-3xl font-bold mt-1">156</div>
                                </div>
                            </div>
                        </div>
                        <div class="dashboard-card">
                            <div class="flex items-center gap-4">
                                <div class="w-14 h-14 md:w-16 md:h-16 bg-green-100 rounded-full flex items-center justify-center">
                                    <i class="fas fa-star text-green-600 text-xl md:text-2xl"></i>
                                </div>
                                <div>
                                    <div class="text-sm text-slate-500">Active Customers</div>
                                    <div class="text-2xl md:text-3xl font-bold mt-1">128</div>
                                </div>
                            </div>
                        </div>
                        <div class="dashboard-card">
                            <div class="flex items-center gap-4">
                                <div class="w-14 h-14 md:w-16 md:h-16 bg-purple-100 rounded-full flex items-center justify-center">
                                    <i class="fas fa-medal text-purple-600 text-xl md:text-2xl"></i>
                                </div>
                                <div>
                                    <div class="text-sm text-slate-500">Premium Clients</div>
                                    <div class="text-2xl md:text-3xl font-bold mt-1">42</div>
                                </div>
                            </div>
                        </div>
                    </div>
                    
                    <div class="table-container">
                        <table class="w-full">
                            <thead>
                                <tr>
                                    <th>Customer</th>
                                    <th>Company</th>
                                    <th>Industry</th>
                                    <th>Total Orders</th>
                                    <th>Total Spent</th>
                                    <th>Last Order</th>
                                    <th>Status</th>
                                    <th>Actions</th>
                                </tr>
                            </thead>
                            <tbody>
                                <tr>
                                    <td class="font-medium">Rajesh Kumar</td>
                                    <td>Oil & Gas Corp</td>
                                    <td>Oil & Gas</td>
                                    <td>24</td>
                                    <td class="font-bold">₹2,450,000</td>
                                    <td>2024-03-15</td>
                                    <td><span class="badge badge-success">Active</span></td>
                                    <td>
                                        <button class="text-blue-600 hover:text-blue-800 mr-3">
                                            <i class="fas fa-eye"></i>
                                        </button>
                                        <button class="text-green-600 hover:text-green-800">
                                            <i class="fas fa-edit"></i>
                                        </button>
                                    </td>
                                </tr>
                                <tr>
                                    <td class="font-medium">Priya Sharma</td>
                                    <td>PowerGen Ltd</td>
                                    <td>Power Generation</td>
                                    <td>18</td>
                                    <td class="font-bold">₹1,875,000</td>
                                    <td>2024-03-14</td>
                                    <td><span class="badge badge-success">Active</span></td>
                                    <td>
                                        <button class="text-blue-600 hover:text-blue-800 mr-3">
                                            <i class="fas fa-eye"></i>
                                        </button>
                                        <button class="text-green-600 hover:text-green-800">
                                            <i class="fas fa-edit"></i>
                                        </button>
                                    </td>
                                </tr>
                                <tr>
                                    <td class="font-medium">Amit Patel</td>
                                    <td>Marine Solutions</td>
                                    <td>Marine & Offshore</td>
                                    <td>12</td>
                                    <td class="font-bold">₹923,000</td>
                                    <td>2024-03-13</td>
                                    <td><span class="badge badge-success">Active</span></td>
                                    <td>
                                        <button class="text-blue-600 hover:text-blue-800 mr-3">
                                            <i class="fas fa-eye"></i>
                                        </button>
                                        <button class="text-green-600 hover:text-green-800">
                                            <i class="fas fa-edit"></i>
                                        </button>
                                    </td>
                                </tr>
                                <tr>
                                    <td class="font-medium">Suresh Nair</td>
                                    <td>Chemical Process</td>
                                    <td>Chemical</td>
                                    <td>8</td>
                                    <td class="font-bold">₹1,580,000</td>
                                    <td>2024-02-28</td>
                                    <td><span class="badge badge-warning">Inactive</span></td>
                                    <td>
                                        <button class="text-blue-600 hover:text-blue-800 mr-3">
                                            <i class="fas fa-eye"></i>
                                        </button>
                                        <button class="text-green-600 hover:text-green-800">
                                            <i class="fas fa-edit"></i>
                                        </button>
                                    </td>
                                </tr>
                                <tr>
                                    <td class="font-medium">Meena Reddy</td>
                                    <td>Construction Co</td>
                                    <td>Construction</td>
                                    <td>15</td>
                                    <td class="font-bold">₹1,564,000</td>
                                    <td>2024-03-10</td>
                                    <td><span class="badge badge-success">Active</span></td>
                                    <td>
                                        <button class="text-blue-600 hover:text-blue-800 mr-3">
                                            <i class="fas fa-eye"></i>
                                        </button>
                                        <button class="text-green-600 hover:text-green-800">
                                            <i class="fas fa-edit"></i>
                                        </button>
                                    </td>
                                </tr>
                            </tbody>
                        </table>
                    </div>
                </div>
                
                <!-- Analytics Tab -->
                <div id="dashboard-analytics" class="tab-content hidden">
                    <div class="mb-6">
                        <h3 class="text-xl md:text-2xl font-bold text-slate-900">Business Analytics</h3>
                        <p class="text-slate-600 mt-2 text-sm md:text-base">Detailed insights and performance metrics</p>
                    </div>
                    
                    <div class="grid lg:grid-cols-2 gap-6 md:gap-8 mb-6 md:mb-8">
                        <div class="dashboard-card">
                            <h4 class="font-bold text-lg text-slate-900 mb-4">Revenue by Product Category</h4>
                            <div class="h-64">
                                <canvas id="categoryChart"></canvas>
                            </div>
                        </div>
                        <div class="dashboard-card">
                            <h4 class="font-bold text-lg text-slate-900 mb-4">Monthly Performance</h4>
                            <div class="h-64">
                                <canvas id="performanceChart"></canvas>
                            </div>
                        </div>
                    </div>
                    
                    <div class="grid md:grid-cols-3 gap-4 md:gap-6">
                        <div class="dashboard-card">
                            <h4 class="font-bold text-lg text-slate-900 mb-4">Order Conversion Rate</h4>
                            <div class="text-center py-6 md:py-8">
                                <div class="relative inline-block">
                                    <canvas id="conversionChart" width="200" height="200"></canvas>
                                    <div class="absolute top-1/2 left-1/2 transform -translate-x-1/2 -translate-y-1/2 text-center">
                                        <div class="text-2xl md:text-3xl font-bold text-blue-600">68%</div>
                                        <div class="text-sm text-slate-500">Conversion</div>
                                    </div>
                                </div>
                            </div>
                        </div>
                        
                        <div class="dashboard-card">
                            <h4 class="font-bold text-lg text-slate-900 mb-4">Top Performing Industries</h4>
                            <div class="space-y-4">
                                <div>
                                    <div class="flex justify-between mb-1">
                                        <span>Oil & Gas</span>
                                        <span class="font-medium">42%</span>
                                    </div>
                                    <div class="progress-bar">
                                        <div class="progress-fill" style="width: 42%"></div>
                                    </div>
                                </div>
                                <div>
                                    <div class="flex justify-between mb-1">
                                        <span>Power Generation</span>
                                        <span class="font-medium">28%</span>
                                    </div>
                                    <div class="progress-bar">
                                        <div class="progress-fill" style="width: 28%"></div>
                                    </div>
                                </div>
                                <div>
                                    <div class="flex justify-between mb-1">
                                        <span>Chemical</span>
                                        <span class="font-medium">18%</span>
                                    </div>
                                    <div class="progress-bar">
                                        <div class="progress-fill" style="width: 18%"></div>
                                    </div>
                                </div>
                                <div>
                                    <div class="flex justify-between mb-1">
                                        <span>Marine</span>
                                        <span class="font-medium">12%</span>
                                    </div>
                                    <div class="progress-bar">
                                        <div class="progress-fill" style="width: 12%"></div>
                                    </div>
                                </div>
                            </div>
                        </div>
                        
                        <div class="dashboard-card">
                            <h4 class="font-bold text-lg text-slate-900 mb-4">Customer Retention</h4>
                            <div class="text-center py-6 md:py-8">
                                <div class="text-4xl md:text-5xl font-bold text-green-600 mb-2">92%</div>
                                <div class="text-slate-600">Retention Rate</div>
                                <div class="text-sm text-slate-500 mt-4">Industry Average: 85%</div>
                            </div>
                        </div>
                    </div>
                </div>
                
                <!-- Settings Tab -->
                <div id="dashboard-settings" class="tab-content hidden">
                    <div class="mb-6">
                        <h3 class="text-xl md:text-2xl font-bold text-slate-900">Account Settings</h3>
                        <p class="text-slate-600 mt-2 text-sm md:text-base">Manage your supplier account preferences</p>
                    </div>
                    
                    <div class="grid lg:grid-cols-2 gap-6 md:gap-8">
                        <div class="dashboard-card">
                            <h4 class="font-bold text-lg text-slate-900 mb-4">Company Information</h4>
                            <form class="space-y-4">
                                <div>
                                    <label class="block text-sm font-medium text-slate-700 mb-2">Company Name</label>
                                    <input type="text" value="Ultimate Flange Manufacturing" class="w-full px-3 md:px-4 py-2 rounded-lg border border-slate-300 focus:ring-2 focus:ring-blue-500 focus:border-blue-500 outline-none">
                                </div>
                                <div>
                                    <label class="block text-sm font-medium text-slate-700 mb-2">Contact Email</label>
                                    <input type="email" value="supplier@ultimateflange.com" class="w-full px-3 md:px-4 py-2 rounded-lg border border-slate-300 focus:ring-2 focus:ring-blue-500 focus:border-blue-500 outline-none">
                                </div>
                                <div>
                                    <label class="block text-sm font-medium text-slate-700 mb-2">Phone Number</label>
                                    <input type="tel" value="+91 7307709671" class="w-full px-3 md:px-4 py-2 rounded-lg border border-slate-300 focus:ring-2 focus:ring-blue-500 focus:border-blue-500 outline-none">
                                </div>
                                <button type="button" class="w-full py-3 bg-blue-600 text-white rounded-lg font-medium hover:bg-blue-700 transition">
                                    Update Information
                                </button>
                            </form>
                        </div>
                        
                        <div class="dashboard-card">
                            <h4 class="font-bold text-lg text-slate-900 mb-4">Notification Preferences</h4>
                            <div class="space-y-3">
                                <label class="flex items-center justify-between p-3 bg-slate-50 rounded-lg">
                                    <div>
                                        <div class="font-medium">New Order Notifications</div>
                                        <div class="text-sm text-slate-500">Get notified for new orders</div>
                                    </div>
                                    <input type="checkbox" checked class="w-6 h-6 text-blue-600 rounded">
                                </label>
                                <label class="flex items-center justify-between p-3 bg-slate-50 rounded-lg">
                                    <div>
                                        <div class="font-medium">Low Stock Alerts</div>
                                        <div class="text-sm text-slate-500">Receive low inventory alerts</div>
                                    </div>
                                    <input type="checkbox" checked class="w-6 h-6 text-blue-600 rounded">
                                </label>
                                <label class="flex items-center justify-between p-3 bg-slate-50 rounded-lg">
                                    <div>
                                        <div class="font-medium">Payment Notifications</div>
                                        <div class="text-sm text-slate-500">Get payment status updates</div>
                                    </div>
                                    <input type="checkbox" class="w-6 h-6 text-blue-600 rounded">
                                </label>
                                <label class="flex items-center justify-between p-3 bg-slate-50 rounded-lg">
                                    <div>
                                        <div class="font-medium">Monthly Reports</div>
                                        <div class="text-sm text-slate-500">Receive monthly sales reports</div>
                                    </div>
                                    <input type="checkbox" checked class="w-6 h-6 text-blue-600 rounded">
                                </label>
                            </div>
                        </div>
                    </div>
                </div>
            </div>
        </div>
    </div>

    <!-- Mobile Menu Overlay -->
    <div id="mobile-menu-overlay" class="mobile-menu-overlay" onclick="toggleMobileMenu()"></div>

    <!-- Mobile Menu -->
    <div id="mobile-menu" class="mobile-menu">
        <div class="flex justify-between items-center mb-8 p-6">
            <span class="text-xl font-bold text-blue-600">UltimateFlange</span>
            <button onclick="toggleMobileMenu()" class="text-slate-500 hover:text-slate-800">
                <i class="fas fa-times text-xl"></i>
            </button>
        </div>
        <div class="space-y-4 px-6">
            <a href="#home" onclick="toggleMobileMenu()" class="block text-slate-700 hover:text-blue-600 font-medium py-3 border-b border-slate-100">Home</a>
            <a href="#products" onclick="toggleMobileMenu()" class="block text-slate-700 hover:text-blue-600 font-medium py-3 border-b border-slate-100">Products</a>
            <a href="#specifications" onclick="toggleMobileMenu()" class="block text-slate-700 hover:text-blue-600 font-medium py-3 border-b border-slate-100">Specifications</a>
            <a href="#about" onclick="toggleMobileMenu()" class="block text-slate-700 hover:text-blue-600 font-medium py-3 border-b border-slate-100">Know More</a>
            <a href="#contact" onclick="toggleMobileMenu()" class="block text-slate-700 hover:text-blue-600 font-medium py-3 border-b border-slate-100">Contact</a>
            <a href="#" onclick="toggleMobileMenu(); openTrackingModal();" class="block text-slate-700 hover:text-blue-600 font-medium py-3 border-b border-slate-100">Track Order</a>
            <a href="#" onclick="toggleMobileMenu(); openDashboard();" id="mobile-dashboard-link" class="block text-slate-700 hover:text-blue-600 font-medium py-3 border-b border-slate-100 hidden">My Account</a>
            <a href="#" onclick="toggleMobileMenu(); openDashboard();" id="mobile-supplier-dashboard-link" class="block text-slate-700 hover:text-blue-600 font-medium py-3 border-b border-slate-100 hidden">Supplier Dashboard</a>
            <a href="#" onclick="toggleMobileMenu(); showProfile();" id="mobile-profile-link" class="block text-slate-700 hover:text-blue-600 font-medium py-3 border-b border-slate-100 hidden">My Profile</a>
            
            <div class="pt-6 border-t border-slate-200">
                <div id="mobile-user-status" class="px-3 py-2 bg-slate-100 rounded-lg text-sm font-bold text-slate-600 mb-4">Visitor</div>
                <div class="space-y-3">
                    <button onclick="toggleMobileMenu(); logout();" id="mobile-logout-btn" class="w-full text-left text-slate-500 hover:text-red-600 font-medium py-2 flex items-center gap-2 hidden">
                        <i class="fas fa-sign-out-alt"></i>Logout
                    </button>
                    <button onclick="toggleMobileMenu(); openAuthModal();" id="mobile-login-btn" class="w-full py-3 bg-gradient-to-r from-blue-600 to-blue-800 text-white font-bold rounded-xl hover:from-blue-700 hover:to-blue-900 transition">
                        <i class="fas fa-sign-in-alt mr-2"></i>Login
                    </button>
                </div>
            </div>
        </div>
    </div>

    <div id="main-content">
        <!-- Enhanced Navigation -->
        <nav class="fixed top-0 w-full z-40 glass-nav">
            <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8">
                <div class="flex justify-between h-20 items-center">
                    <div class="flex items-center gap-3">
                        <div class="w-10 h-10 bg-gradient-to-br from-blue-600 to-blue-800 rounded-xl flex items-center justify-center shadow-md">
                            <i class="fas fa-cogs text-white text-lg"></i>
                        </div>
                        <div>
                            <span class="text-xl font-bold text-slate-900 tracking-tight">UltimateFlange</span>
                            <span class="block text-xs text-slate-500 font-medium">Industrial Solutions</span>
                        </div>
                    </div>
                    
                    <!-- Desktop Navigation -->
                    <div class="hidden lg:flex space-x-8 font-medium text-sm items-center">
                        <a href="#home" class="hover:text-blue-600 transition text-slate-700 font-medium">Home</a>
                        <a href="#products" class="hover:text-blue-600 transition text-slate-700 font-medium">Products</a>
                        <a href="#specifications" class="hover:text-blue-600 transition text-slate-700 font-medium">Specifications</a>
                        <a href="#about" class="hover:text-blue-600 transition text-slate-700 font-medium">Know More</a>
                        <a href="#contact" class="hover:text-blue-600 transition text-slate-700 font-medium">Contact</a>
                        <a href="#" onclick="openTrackingModal()" class="hover:text-blue-600 transition text-slate-700 font-medium">Track Order</a>
                        
                        <div class="flex items-center gap-4">
                            <div id="user-status" class="px-3 py-1.5 bg-blue-50 rounded-full text-xs font-bold text-blue-600 uppercase border border-blue-100">
                                <i class="fas fa-user mr-1"></i>Visitor
                            </div>
                            <button onclick="showProfile()" id="profile-btn" class="text-slate-400 hover:text-blue-600 transition text-xs font-bold uppercase tracking-wider hidden">
                                <i class="fas fa-user-circle mr-1"></i>My Profile
                            </button>
                            <button onclick="openDashboard()" id="dashboard-btn" class="text-slate-400 hover:text-blue-600 transition text-xs font-bold uppercase tracking-wider hidden">
                                <i class="fas fa-chart-bar mr-1"></i>My Account
                            </button>
                            <button onclick="openDashboard()" id="supplier-dashboard-btn" class="text-slate-400 hover:text-blue-600 transition text-xs font-bold uppercase tracking-wider hidden">
                                <i class="fas fa-building mr-1"></i>Supplier Dashboard
                            </button>
                            <button onclick="logout()" id="logout-btn" class="text-slate-400 hover:text-red-600 transition text-xs font-bold uppercase tracking-wider hidden">
                                <i class="fas fa-sign-out-alt mr-1"></i>Logout
                            </button>
                            <button onclick="openAuthModal()" id="login-btn" class="text-slate-400 hover:text-blue-600 transition text-xs font-bold uppercase tracking-wider">
                                <i class="fas fa-sign-in-alt mr-1"></i>Login
                            </button>
                            <button onclick="checkAuthBeforeOrder()" class="px-5 py-2.5 bg-gradient-to-r from-blue-600 to-blue-800 text-white font-semibold rounded-lg hover:from-blue-700 hover:to-blue-900 transition shadow-md order-button">
                                <i class="fas fa-file-invoice-dollar mr-2"></i>Order Now
                            </button>
                        </div>
                    </div>
                    
                    <!-- Mobile Menu Button -->
                    <button onclick="toggleMobileMenu()" class="lg:hidden text-slate-700 hover:text-blue-600">
                        <i class="fas fa-bars text-xl"></i>
                    </button>
                </div>
            </div>
        </nav>

        <!-- Enhanced Hero Section -->
        <section id="home" class="pt-32 pb-20 px-4 reveal hero-gradient">
            <div class="max-w-7xl mx-auto">
                <div class="flex flex-col lg:flex-row items-center gap-12 lg:gap-16">
                    <div class="flex-1 space-y-8">
                        <div class="space-y-4">
                            <span class="inline-block px-4 py-1.5 bg-blue-100 text-blue-700 rounded-full text-sm font-bold uppercase tracking-widest">
                                <i class="fas fa-award mr-2"></i>Industry Leader
                            </span>
                            <h1 class="text-4xl md:text-5xl lg:text-7xl font-bold leading-tight">
                                Precision <span class="gradient-text">Industrial</span> Solutions
                            </h1>
                            <p class="text-lg md:text-xl text-slate-600 max-w-2xl leading-relaxed">
                                Setting the global standard for high-pressure flanges, precision metal cutting, and industrial components. Durability, accuracy, and reliability delivered worldwide.
                            </p>
                        </div>
                        
                        <div class="flex flex-col sm:flex-row gap-4">
                            <button onclick="checkAuthBeforeOrder()" class="px-6 md:px-8 py-3 md:py-3.5 bg-gradient-to-r from-blue-600 to-blue-800 text-white font-semibold rounded-xl shadow-lg shadow-blue-200 hover:shadow-xl hover:scale-105 transition-all flex items-center justify-center gap-2 order-button">
                                <i class="fas fa-shopping-cart"></i>Order Now
                            </button>
                            <a href="#contact" class="px-6 md:px-8 py-3 md:py-3.5 border-2 border-slate-300 font-semibold rounded-xl hover:bg-slate-50 hover:border-blue-300 transition flex items-center justify-center gap-2">
                                <i class="fas fa-comment-dots"></i>Request Consultation
                            </a>
                        </div>
                        
                        <div class="grid grid-cols-2 md:grid-cols-4 gap-4 md:gap-6 pt-8">
                            <div class="text-center">
                                <div class="text-2xl md:text-3xl font-bold text-blue-700">25+</div>
                                <div class="text-sm text-slate-500">Years Experience</div>
                            </div>
                            <div class="text-center">
                                <div class="text-2xl md:text-3xl font-bold text-blue-700">500+</div>
                                <div class="text-sm text-slate-500">Projects Completed</div>
                            </div>
                            <div class="text-center">
                                <div class="text-2xl md:text-3xl font-bold text-blue-700">40+</div>
                                <div class="text-sm text-slate-500">Countries Served</div>
                            </div>
                            <div class="text-center">
                                <div class="text-2xl md:text-3xl font-bold text-blue-700">ISO</div>
                                <div class="text-sm text-slate-500">9001:2015 Certified</div>
                            </div>
                        </div>
                    </div>
                    
                    <div class="flex-1 w-full">
                        <div class="relative">
                            <!-- Hero Image Container with Fallback -->
                            <div class="hero-image-container" id="hero-image-container">
                                <img src="industry.png" alt="Industrial Flange Manufacturing Facility" onerror="handleImageError(this)">
                            </div>
                        </div>
                    </div>
                </div>

                <!-- What Are Flanges Section -->
                <div class="mt-16 md:mt-20 pt-12 md:pt-16 border-t border-slate-200 reveal">
                    <div class="text-center mb-8 md:mb-12">
                        <h2 class="text-3xl md:text-4xl font-bold text-slate-900 mb-4">Understanding Flanges</h2>
                        <p class="text-slate-600 max-w-3xl mx-auto text-base md:text-lg">Essential components in industrial piping systems that ensure secure connections and operational reliability</p>
                    </div>
                    
                    <div class="grid lg:grid-cols-2 gap-6 md:gap-8 items-start">
                        <div class="bg-white p-6 md:p-8 rounded-3xl border border-slate-200 shadow-lg">
                            <div class="flex items-start gap-4 mb-6">
                                <div class="w-12 h-12 md:w-14 md:h-14 bg-blue-100 rounded-2xl flex items-center justify-center flex-shrink-0">
                                    <i class="fas fa-link text-blue-600 text-xl md:text-2xl"></i>
                                </div>
                                <div>
                                    <h3 class="text-xl md:text-2xl font-bold text-slate-900 mb-3">What Are Flanges?</h3>
                                    <p class="text-slate-600 leading-relaxed text-sm md:text-base">
                                        Flanges are widely used in numerous applications across engineering and industries as they play vital roles as linkages between pipes, valves, pumps, and others. They offer an opportunity to connect or link various elements of a system in a way that is mechanically possible. Generally, flanges are anhedral circular plates with holes arranged uniformly along their circumference for bolts or studs that join them.
                                    </p>
                                </div>
                            </div>
                            
                            <div class="bg-blue-50 rounded-2xl p-4 md:p-6">
                                <h4 class="font-bold text-blue-800 mb-3 flex items-center gap-2">
                                    <i class="fas fa-cogs"></i>Primary Functions
                                </h4>
                                <ul class="space-y-2 text-blue-700 text-sm md:text-base">
                                    <li class="flex items-start gap-2"><i class="fas fa-check-circle text-green-500 mt-1"></i>Secure connection between pipeline components</li>
                                    <li class="flex items-start gap-2"><i class="fas fa-check-circle text-green-500 mt-1"></i>Easy assembly and disassembly for maintenance</li>
                                    <li class="flex items-start gap-2"><i class="fas fa-check-circle text-green-500 mt-1"></i>Pressure containment and leak prevention</li>
                                    <li class="flex items-start gap-2"><i class="fas fa-check-circle text-green-500 mt-1"></i>System flexibility and expansion capability</li>
                                </ul>
                            </div>
                        </div>
                        
                        <div class="bg-white p-6 md:p-8 rounded-3xl border border-slate-200 shadow-lg">
                            <div class="flex items-start gap-4 mb-6">
                                <div class="w-12 h-12 md:w-14 md:h-14 bg-green-100 rounded-2xl flex items-center justify-center flex-shrink-0">
                                    <i class="fas fa-industry text-green-600 text-xl md:text-2xl"></i>
                                </div>
                                <div>
                                    <h3 class="text-xl md:text-2xl font-bold text-slate-900 mb-3">Our Manufacturing Capabilities</h3>
                                    <p class="text-slate-600 leading-relaxed text-sm md:text-base">
                                        We specialize in precision manufacturing of industrial components with comprehensive material options and rapid production capabilities.
                                    </p>
                                </div>
                            </div>
                            
                            <div class="space-y-6">
                                <div>
                                    <h4 class="font-bold text-slate-800 mb-3 text-lg">Flanges We Manufacture</h4>
                                    <div class="grid grid-cols-2 gap-3">
                                        <div class="bg-slate-50 p-3 rounded-xl">
                                            <div class="flex items-center gap-2">
                                                <i class="fas fa-circle text-blue-500 text-xs"></i>
                                                <span class="font-medium text-sm">MS Plate Flange</span>
                                            </div>
                                        </div>
                                        <div class="bg-slate-50 p-3 rounded-xl">
                                            <div class="flex items-center gap-2">
                                                <i class="fas fa-circle text-blue-500 text-xs"></i>
                                                <span class="font-medium text-sm">Forged Flange</span>
                                            </div>
                                        </div>
                                        <div class="bg-slate-50 p-3 rounded-xl">
                                            <div class="flex items-center gap-2">
                                                <i class="fas fa-circle text-blue-500 text-xs"></i>
                                                <span class="font-medium text-sm">Weld Neck Flanges</span>
                                            </div>
                                        </div>
                                        <div class="bg-slate-50 p-3 rounded-xl">
                                            <div class="flex items-center gap-2">
                                                <i class="fas fa-circle text-blue-500 text-xs"></i>
                                                <span class="font-medium text-sm">Special/Ring as per drawing</span>
                                            </div>
                                        </div>
                                    </div>
                                </div>
                                
                                <div>
                                    <h4 class="font-bold text-slate-800 mb-3 text-lg">Additional Products</h4>
                                    <div class="grid grid-cols-2 gap-3">
                                        <div class="bg-slate-50 p-3 rounded-xl">
                                            <div class="flex items-center gap-2">
                                                <i class="fas fa-circle text-green-500 text-xs"></i>
                                                <span class="font-medium text-sm">Pipes Fitting (B/W & S/W)</span>
                                            </div>
                                            <p class="text-xs text-slate-500 mt-1 pl-4">Hydrolick products, Elbow, Bend, Tee, Reducer, Cap, Coupling, Union</p>
                                        </div>
                                        <div class="bg-slate-50 p-3 rounded-xl">
                                            <div class="flex items-center gap-2">
                                                <i class="fas fa-circle text-green-500 text-xs"></i>
                                                <span class="font-medium text-sm">Pipes</span>
                                            </div>
                                            <p class="text-xs text-slate-500 mt-1 pl-4">Round & Square Pipes</p>
                                        </div>
                                    </div>
                                </div>
                                
                                <div class="bg-gradient-to-r from-blue-50 to-green-50 rounded-2xl p-4 md:p-5">
                                    <h4 class="font-bold text-slate-800 mb-2 flex items-center gap-2">
                                        <i class="fas fa-boxes"></i>Material Inventory
                                    </h4>
                                    <p class="text-slate-600 text-sm">
                                        Our comprehensive inventory includes stainless steel, mild steel, alloy steel, and other unique materials, allowing us to commence production immediately upon receiving your order. We hold a wide stock range of austenitic 300 series, mild, alloy, and other unique stainless steel qualities, and we can begin fabrication immediately after placing the order.
                                    </p>
                                </div>
                            </div>
                        </div>
                    </div>
                </div>
            </div>
        </section>

        <!-- Product Exploration Section -->
        <section id="catalog-access" class="bg-white border-y border-slate-200 py-12 md:py-16 overflow-hidden reveal">
            <div class="max-w-7xl mx-auto px-4">
                <div class="flex flex-col items-center gap-8 md:gap-10">
                    <div class="text-center max-w-3xl mx-auto">
                        <span class="text-blue-600 font-bold uppercase tracking-widest text-sm">Product Catalog</span>
                        <h2 class="text-3xl md:text-4xl font-bold text-slate-900 mt-2 mb-4">Explore Our Products</h2>
                        <p class="text-slate-600 text-base md:text-lg">Browse our extensive range of industrial flanges and precision components</p>
                    </div>
                    
                    <!-- Product Thumbnails Grid with Fixed Image Paths -->
                    <div class="w-full grid grid-cols-2 md:grid-cols-3 lg:grid-cols-4 gap-4 md:gap-6 mb-8 md:mb-12 reveal stagger-delay-1">
                        <!-- Weld Neck Flange -->
                        <div class="product-thumbnail" onclick="updateProduct('wnf')">
                            <img src="weld-neck.png" alt="Weld Neck Flange" onerror="handleImageError(this, 'Weld Neck')">
                        </div>
                        
                        <!-- Long Weld Neck -->
                        <div class="product-thumbnail" onclick="updateProduct('lwn')">
                            <img src="long-weldneck.png" alt="Long Weld Neck Flange" onerror="handleImageError(this, 'Long Weld Neck')">
                        </div>
                        
                        <!-- Slip-On Flange -->
                        <div class="product-thumbnail" onclick="updateProduct('slipon')">
                            <img src="slip-on-flange.png" alt="Slip-On Flange" onerror="handleImageError(this, 'Slip-On')">
                        </div>
                        
                        <!-- Blind Flange -->
                        <div class="product-thumbnail" onclick="updateProduct('blind')">
                            <img src="blind.png" alt="Blind Flange" onerror="handleImageError(this, 'Blind')">
                        </div>
                        
                        <!-- Puddle Flange -->
                        <div class="product-thumbnail" onclick="updateProduct('puddle')">
                            <img src="puddle-flange.png" alt="Puddle Flange" onerror="handleImageError(this, 'Puddle')">
                        </div>
                        
                        <!-- Plasma CNC -->
                        <div class="product-thumbnail" onclick="updateProduct('plasma')">
                            <img src="plasma-cutting.png" alt="Plasma CNC Cutting" onerror="handleImageError(this, 'Plasma CNC')">
                        </div>
                        
                        <!-- Profile Cutting -->
                        <div class="product-thumbnail" onclick="updateProduct('profile')">
                            <img src="profile-cutting.jpg" alt="Profile Cutting Services" onerror="handleImageError(this, 'Profile')">
                        </div>
                        
                        <!-- All Products -->
                        <div class="product-thumbnail bg-gradient-to-br from-blue-600 to-blue-800" onclick="showAllProducts()">
                            <div class="product-placeholder text-white">
                                <i class="fas fa-boxes text-2xl md:text-3xl"></i>
                                <span class="font-semibold mt-2 text-sm md:text-base">View All Products</span>
                            </div>
                        </div>
                    </div>
                    
                    <div class="w-full flex flex-col lg:flex-row items-center justify-center gap-4 md:gap-6">
                        <div class="search-container relative w-full lg:w-96 flex-shrink-0 border-2 border-slate-300 rounded-full bg-white px-4 md:px-6 py-2.5 md:py-3.5 transition-all">
                            <div class="flex items-center gap-3">
                                <i class="fas fa-search text-slate-400"></i>
                                <input type="text" id="product-search" placeholder="Search product codes, names, or specs..." 
                                       class="bg-transparent border-none outline-none text-sm md:text-base w-full text-slate-700 placeholder:text-slate-400"
                                       onkeyup="handleSearch(this.value)">
                            </div>
                        </div>

                        <div class="w-full overflow-x-auto no-scrollbar py-2">
                            <div class="flex justify-start lg:justify-center gap-2 md:gap-3 min-w-max px-2" id="suggestion-bar">
                                <div onclick="updateProduct('wnf')" id="chip-wnf" class="flange-chip px-3 md:px-5 py-2 md:py-2.5 rounded-full border-2 border-slate-200 bg-white text-xs md:text-sm font-semibold flex items-center gap-2">
                                    <i class="fas fa-fire"></i>Weld Neck
                                </div>
                                <div onclick="updateProduct('lwn')" id="chip-lwn" class="flange-chip active px-3 md:px-5 py-2 md:py-2.5 rounded-full border-2 border-slate-200 bg-white text-xs md:text-sm font-semibold flex items-center gap-2">
                                    <i class="fas fa-ruler-vertical"></i>Long Weld Neck
                                </div>
                                <div onclick="updateProduct('slipon')" id="chip-slipon" class="flange-chip px-3 md:px-5 py-2 md:py-2.5 rounded-full border-2 border-slate-200 bg-white text-xs md:text-sm font-semibold flex items-center gap-2">
                                    <i class="fas fa-sliders-h"></i>Slip-On
                                </div>
                                <div onclick="updateProduct('blind')" id="chip-blind" class="flange-chip px-3 md:px-5 py-2 md:py-2.5 rounded-full border-2 border-slate-200 bg-white text-xs md:text-sm font-semibold flex items-center gap-2">
                                    <i class="fas fa-ban"></i>Blind
                                </div>
                                <div onclick="updateProduct('puddle')" id="chip-puddle" class="flange-chip px-3 md:px-5 py-2 md:py-2.5 rounded-full border-2 border-slate-200 bg-white text-xs md:text-sm font-semibold flex items-center gap-2">
                                    <i class="fas fa-water"></i>Puddle
                                </div>
                                <div onclick="updateProduct('plasma')" id="chip-plasma" class="flange-chip px-3 md:px-5 py-2 md:py-2.5 rounded-full border-2 border-slate-200 bg-white text-xs md:text-sm font-semibold flex items-center gap-2">
                                    <i class="fas fa-bolt"></i>Plasma CNC
                                </div>
                                <div onclick="updateProduct('profile')" id="chip-profile" class="flange-chip px-3 md:px-5 py-2 md:py-2.5 rounded-full border-2 border-slate-200 bg-white text-xs md:text-sm font-semibold flex items-center gap-2">
                                    <i class="fas fa-cut"></i>Profile Cutting
                                </div>
                            </div>
                        </div>
                    </div>
                </div>
            </div>
        </section>

        <!-- Product Details Section -->
        <section id="products" class="py-12 md:py-20 bg-slate-50 reveal">
            <div class="max-w-7xl mx-auto px-4">
                <div class="bg-white p-6 md:p-8 lg:p-12 rounded-3xl border border-slate-100 transition-all duration-500 shadow-lg" id="product-card">
                    <div class="prose prose-slate max-w-none">
                        <!-- Product Image Section -->
                        <div class="mb-8 md:mb-12 reveal stagger-delay-1">
                            <div class="flex flex-col lg:flex-row gap-6 md:gap-8 items-start">
                                <!-- Product Image -->
                                <div class="flex-1">
                                    <div class="product-image-container" id="product-image-container">
                                        <img src="long-weldneck.png" alt="Long Weld Neck Flange" id="product-main-image" onerror="handleImageError(this, 'Long Weld Neck')">
                                    </div>
                                </div>
                                
                                <!-- Product Info -->
                                <div class="flex-1">
                                    <div class="bg-gradient-to-br from-slate-900 to-blue-900 rounded-2xl p-4 md:p-6 text-white h-full">
                                        <h4 class="text-lg md:text-xl font-bold mb-3 md:mb-4 flex items-center gap-2">
                                            <i class="fas fa-info-circle text-blue-300"></i>Product Information
                                        </h4>
                                        <div class="space-y-3 md:space-y-4 mb-4 md:mb-6">
                                            <div>
                                                <div class="text-xs md:text-sm text-blue-300 mb-1">Current Product</div>
                                                <div class="font-bold text-base md:text-lg" id="current-product-name">Long Weld Neck Flange</div>
                                            </div>
                                            <div>
                                                <div class="text-xs md:text-sm text-blue-300 mb-1">Reference Code</div>
                                                <div class="font-medium">ASMEB16.5-900-DN15</div>
                                            </div>
                                            <div>
                                                <div class="text-xs md:text-sm text-blue-300 mb-1">Standard</div>
                                                <div class="font-medium">ASME B16.5</div>
                                            </div>
                                            <div>
                                                <div class="text-xs md:text-sm text-blue-300 mb-1">Nominal Diameter</div>
                                                <div class="font-medium">DN15 (1/2")</div>
                                            </div>
                                            <div>
                                                <div class="text-xs md:text-sm text-blue-300 mb-1">Pressure Rating</div>
                                                <div class="font-medium">Class 900 (150#)</div>
                                            </div>
                                        </div>
                                        
                                        <div class="space-y-2 md:space-y-3">
                                            <h5 class="font-bold text-lg mb-2">Available Suppliers</h5>
                                            <div id="product-suppliers-list" class="text-xs md:text-sm text-slate-300 space-y-2">
                                                <!-- Suppliers will be loaded here -->
                                            </div>
                                        </div>
                                        
                                        <div class="mt-4 md:mt-6 pt-4 md:pt-6 border-t border-slate-700">
                                            <button onclick="downloadProductFiles()" class="w-full py-2.5 md:py-3 bg-blue-600 text-white font-bold rounded-xl hover:bg-blue-700 transition mb-2 md:mb-3 text-sm md:text-base">
                                                <i class="fas fa-download mr-2"></i>Download Technical Files
                                            </button>
                                            <button onclick="checkAuthBeforeOrder()" class="w-full py-2.5 md:py-3 bg-slate-800 text-white font-bold rounded-xl hover:bg-slate-700 transition text-sm md:text-base order-button">
                                                <i class="fas fa-shopping-cart mr-2"></i>Order Now
                                            </button>
                                        </div>
                                    </div>
                                </div>
                            </div>
                        </div>
                        
                        <div class="flex flex-col md:flex-row md:items-center justify-between gap-4 md:gap-6 mb-6 md:mb-10">
                            <div>
                                <h3 class="text-3xl md:text-4xl font-bold text-slate-900" id="p-title">Long Weld Neck Flange (LWN)</h3>
                                <div class="flex flex-wrap items-center gap-2 md:gap-4 mt-2">
                                    <span class="px-2 md:px-3 py-1 bg-blue-50 text-blue-700 rounded-full text-xs font-bold">ASME B16.5</span>
                                    <span class="px-2 md:px-3 py-1 bg-green-50 text-green-700 rounded-full text-xs font-bold">Class 900</span>
                                    <span class="px-2 md:px-3 py-1 bg-purple-50 text-purple-700 rounded-full text-xs font-bold">CAD Available</span>
                                    <span class="px-2 md:px-3 py-1 bg-orange-50 text-orange-700 rounded-full text-xs font-bold">DN15</span>
                                    <span class="supplier-badge">
                                        <i class="fas fa-users mr-1"></i>Multiple Suppliers
                                    </span>
                                </div>
                            </div>
                            <div class="flex gap-2 md:gap-3 mt-4 md:mt-0">
                                <button onclick="checkAuthBeforeOrder()" class="px-4 md:px-6 py-2.5 md:py-3 bg-gradient-to-r from-blue-600 to-blue-800 text-white rounded-lg font-bold shadow-md hover:from-blue-700 hover:to-blue-900 transition flex items-center gap-2 text-sm md:text-base order-button">
                                    <i class="fas fa-shopping-cart"></i>Order Now
                                </button>
                                <button onclick="downloadProductFiles()" class="px-4 md:px-6 py-2.5 md:py-3 bg-slate-100 text-slate-700 rounded-lg font-bold hover:bg-slate-200 transition flex items-center gap-2 text-sm md:text-base">
                                    <i class="fas fa-download"></i>Download Specifications
                                </button>
                            </div>
                        </div>
                        <p class="text-slate-600 text-base md:text-xl leading-relaxed mb-6 md:mb-10 max-w-4xl" id="p-desc">
                            Long Weld Neck flanges are specifically designed for pressure vessel applications and high-pressure piping systems. Featuring an extended neck that provides reinforcement and stress distribution, these flanges are ideal for critical applications where reliability is paramount. Our ASME B16.5 Class 900 DN15 model represents precision engineering for demanding industrial environments.
                        </p>
                        
                        <div class="grid md:grid-cols-2 lg:grid-cols-3 gap-4 md:gap-6 mb-8 md:mb-12" id="p-features">
                            <!-- Features will be populated by JavaScript -->
                        </div>
                        
                        <!-- Available Suppliers Section -->
                        <div class="bg-gradient-to-r from-blue-50 to-green-50 rounded-2xl p-4 md:p-6 mb-6 md:mb-8">
                            <h4 class="text-lg md:text-xl font-bold text-slate-900 mb-3 md:mb-4 flex items-center gap-2">
                                <i class="fas fa-user-tie text-blue-600"></i>Available Suppliers
                            </h4>
                            <p class="text-slate-600 mb-4 text-sm md:text-base">Connect with verified suppliers for this product. Chat with them directly before placing your order.</p>
                            <div id="dynamic-suppliers-list" class="grid md:grid-cols-2 gap-3 md:gap-4">
                                <!-- Suppliers will be dynamically loaded here -->
                            </div>
                            <button onclick="showAllSuppliers()" class="mt-4 px-4 py-2 bg-white border border-slate-300 rounded-lg hover:bg-slate-50 transition text-sm font-medium">
                                <i class="fas fa-eye mr-2"></i>View All Suppliers
                            </button>
                        </div>
                        
                        <!-- Additional Product Info -->
                        <div class="bg-blue-50 rounded-2xl p-4 md:p-6 mb-6 md:mb-8">
                            <h4 class="text-lg md:text-xl font-bold text-slate-900 mb-3 md:mb-4 flex items-center gap-2">
                                <i class="fas fa-cube text-blue-600"></i>Documentation Available
                            </h4>
                            <div class="grid md:grid-cols-2 gap-4 md:gap-6">
                                <div>
                                    <h5 class="font-bold text-slate-800 mb-2">Technical Documents</h5>
                                    <ul class="text-slate-600 space-y-1 text-sm md:text-base">
                                        <li class="flex items-start gap-2"><i class="fas fa-check text-green-500 mt-1"></i>Detailed technical data sheets</li>
                                        <li class="flex items-start gap-2"><i class="fas fa-check text-green-500 mt-1"></i>Material certification (EN 10204 3.1)</li>
                                        <li class="flex items-start gap-2"><i class="fas fa-check text-green-500 mt-1"></i>Dimensional drawings with tolerances</li>
                                        <li class="flex items-start gap-2"><i class="fas fa-check text-green-500 mt-1"></i>Pressure-temperature ratings</li>
                                        <li class="flex items-start gap-2"><i class="fas fa-check text-green-500 mt-1"></i>Installation and maintenance guides</li>
                                    </ul>
                                </div>
                                <div>
                                    <h5 class="font-bold text-slate-800 mb-2">File Formats Available</h5>
                                    <ul class="text-slate-600 space-y-1 text-sm md:text-base">
                                        <li class="flex items-start gap-2"><i class="fas fa-check text-green-500 mt-1"></i>PDF (Technical data sheets)</li>
                                        <li class="flex items-start gap-2"><i class="fas fa-check text-green-500 mt-1"></i>STEP (CAD integration)</li>
                                        <li class="flex items-start gap-2"><i class="fas fa-check text-green-500 mt-1"></i>DWG (AutoCAD compatible)</li>
                                        <li class="flex items-start gap-2"><i class="fas fa-check text-green-500 mt-1"></i>IGES (Engineering design)</li>
                                        <li class="flex items-start gap-2"><i class="fas fa-check text-green-500 mt-1"></i>Excel (Material specifications)</li>
                                    </ul>
                                </div>
                            </div>
                        </div>
                    </div>
                </div>
            </div>
        </section>

        <!-- Detailed Technical Specifications -->
        <section id="specifications" class="py-12 md:py-20 bg-slate-900 text-white reveal">
            <div class="max-w-7xl mx-auto px-4">
                <div class="text-center mb-10 md:mb-14">
                    <h2 class="text-3xl md:text-4xl lg:text-5xl font-bold mb-4" id="spec-title">Technical Specifications</h2>
                    <p class="text-slate-400 max-w-3xl mx-auto text-base md:text-lg">Comprehensive technical data and material specifications compliant with international standards including ASME, ANSI, EN, and DIN.</p>
                </div>
                
                <div class="grid lg:grid-cols-2 gap-6 md:gap-8 mb-8 md:mb-12" id="spec-tables-container">
                    <!-- Tables dynamically injected here -->
                </div>
                
                <!-- Standards Compliance -->
                <div class="bg-slate-800/50 rounded-3xl p-6 md:p-8">
                    <h3 class="text-xl md:text-2xl font-bold mb-4 md:mb-6 flex items-center gap-3">
                        <i class="fas fa-certificate text-blue-400"></i>Standards & Compliance
                    </h3>
                    <div class="grid md:grid-cols-2 lg:grid-cols-4 gap-4 md:gap-6">
                        <div class="bg-slate-900/50 p-4 md:p-5 rounded-2xl">
                            <div class="text-blue-400 text-2xl mb-2">
                                <i class="fas fa-balance-scale"></i>
                            </div>
                            <h4 class="font-bold text-base md:text-lg mb-2">ASME Standards</h4>
                            <p class="text-slate-400 text-xs md:text-sm">B16.5, B16.47, B31.3, Section VIII Div. 1</p>
                        </div>
                        <div class="bg-slate-900/50 p-4 md:p-5 rounded-2xl">
                            <div class="text-blue-400 text-2xl mb-2">
                                <i class="fas fa-globe-europe"></i>
                            </div>
                            <h4 class="font-bold text-base md:text-lg mb-2">European Standards</h4>
                            <p class="text-slate-400 text-xs md:text-sm">EN 1092-1, PED 2014/68/EU, ATEX</p>
                        </div>
                        <div class="bg-slate-900/50 p-4 md:p-5 rounded-2xl">
                            <div class="text-blue-400 text-2xl mb-2">
                                <i class="fas fa-industry"></i>
                            </div>
                            <h4 class="font-bold text-base md:text-lg mb-2">Material Standards</h4>
                            <p class="text-slate-400 text-xs md:text-sm">ASTM A105, A182, A350, A694</p>
                        </div>
                        <div class="bg-slate-900/50 p-4 md:p-5 rounded-2xl">
                            <div class="text-blue-400 text-2xl mb-2">
                                <i class="fas fa-shield-alt"></i>
                            </div>
                            <h4 class="font-bold text-base md:text-lg mb-2">Quality Certifications</h4>
                            <p class="text-slate-400 text-xs md:text-sm">ISO 9001:2015, PED, NORSOK, API</p>
                        </div>
                    </div>
                </div>
            </div>
        </section>

        <!-- Product Gallery Section with Fixed Image Paths -->
        <section id="product-gallery" class="py-12 md:py-24 bg-white reveal">
            <div class="max-w-7xl mx-auto px-4">
                <div class="text-center mb-12 md:mb-16">
                    <span class="text-blue-600 font-bold uppercase tracking-widest text-sm">Product Gallery</span>
                    <h2 class="text-3xl md:text-4xl lg:text-5xl font-bold text-slate-900 mt-2 mb-4">Explore All Products</h2>
                    <p class="text-slate-600 max-w-3xl mx-auto text-base md:text-lg">Click on any product to view detailed specifications and technical information</p>
                </div>
                
                <div class="grid md:grid-cols-2 lg:grid-cols-3 gap-6 md:gap-8">
                    <!-- Long Weld Neck -->
                    <div class="gallery-product-card bg-slate-50 rounded-3xl overflow-hidden border border-slate-200 hover:border-blue-300 transition-all duration-300">
                        <div class="product-image-container" style="height: 200px;">
                            <img src="long-weldneck.png" alt="Long Weld Neck Flange" onerror="handleImageError(this, 'Long Weld Neck')" style="object-fit: contain;">
                        </div>
                        <div class="p-4 md:p-6">
                            <h4 class="font-bold text-lg md:text-xl text-slate-900 mb-2">Long Weld Neck Flange</h4>
                            <p class="text-slate-600 mb-3 md:mb-4 text-sm md:text-base">ASME B16.5 Class 900 DN15 with extended hub design</p>
                            <div class="flex gap-2 md:gap-3">
                                <button onclick="updateProduct('lwn')" class="flex-1 py-2 md:py-2.5 bg-blue-600 text-white rounded-lg font-medium hover:bg-blue-700 transition text-xs md:text-sm">
                                    <i class="fas fa-info-circle mr-2"></i>View Details
                                </button>
                                <button onclick="checkAuthBeforeOrder('lwn')" class="flex-1 py-2 md:py-2.5 bg-slate-200 text-slate-700 rounded-lg font-medium hover:bg-slate-300 transition text-xs md:text-sm">
                                    <i class="fas fa-shopping-cart mr-2"></i>Order
                                </button>
                            </div>
                        </div>
                    </div>
                    
                    <!-- Weld Neck Flange -->
                    <div class="gallery-product-card bg-slate-50 rounded-3xl overflow-hidden border border-slate-200 hover:border-blue-300 transition-all duration-300">
                        <div class="product-image-container" style="height: 200px;">
                            <img src="weld-neck.png" alt="Weld Neck Flange" onerror="handleImageError(this, 'Weld Neck')" style="object-fit: contain;">
                        </div>
                        <div class="p-4 md:p-6">
                            <h4 class="font-bold text-lg md:text-xl text-slate-900 mb-2">Weld Neck Flange</h4>
                            <p class="text-slate-600 mb-3 md:mb-4 text-sm md:text-base">High-pressure applications with tapered hub design</p>
                            <div class="flex gap-2 md:gap-3">
                                <button onclick="updateProduct('wnf')" class="flex-1 py-2 md:py-2.5 bg-blue-600 text-white rounded-lg font-medium hover:bg-blue-700 transition text-xs md:text-sm">
                                    <i class="fas fa-info-circle mr-2"></i>View Details
                                </button>
                                <button onclick="checkAuthBeforeOrder('wnf')" class="flex-1 py-2 md:py-2.5 bg-slate-200 text-slate-700 rounded-lg font-medium hover:bg-slate-300 transition text-xs md:text-sm">
                                    <i class="fas fa-shopping-cart mr-2"></i>Order
                                </button>
                            </div>
                        </div>
                    </div>
                    
                    <!-- Slip-On Flange -->
                    <div class="gallery-product-card bg-slate-50 rounded-3xl overflow-hidden border border-slate-200 hover:border-blue-300 transition-all duration-300">
                        <div class="product-image-container" style="height: 200px;">
                            <img src="slip-on-flange.png" alt="Slip-On Flange" onerror="handleImageError(this, 'Slip-On')" style="object-fit: contain;">
                        </div>
                        <div class="p-4 md:p-6">
                            <h4 class="font-bold text-lg md:text-xl text-slate-900 mb-2">Slip-On Flange</h4>
                            <p class="text-slate-600 mb-3 md:mb-4 text-sm md:text-base">Cost-effective solution for standard pressure duty</p>
                            <div class="flex gap-2 md:gap-3">
                                <button onclick="updateProduct('slipon')" class="flex-1 py-2 md:py-2.5 bg-blue-600 text-white rounded-lg font-medium hover:bg-blue-700 transition text-xs md:text-sm">
                                    <i class="fas fa-info-circle mr-2"></i>View Details
                                </button>
                                <button onclick="checkAuthBeforeOrder('slipon')" class="flex-1 py-2 md:py-2.5 bg-slate-200 text-slate-700 rounded-lg font-medium hover:bg-slate-300 transition text-xs md:text-sm">
                                    <i class="fas fa-shopping-cart mr-2"></i>Order
                                </button>
                            </div>
                        </div>
                    </div>
                    
                    <!-- Blind Flange -->
                    <div class="gallery-product-card bg-slate-50 rounded-3xl overflow-hidden border border-slate-200 hover:border-blue-300 transition-all duration-300">
                        <div class="product-image-container" style="height: 200px;">
                            <img src="blind.png" alt="Blind Flange" onerror="handleImageError(this, 'Blind')" style="object-fit: contain;">
                        </div>
                        <div class="p-4 md:p-6">
                            <h4 class="font-bold text-lg md:text-xl text-slate-900 mb-2">Blind Flange</h4>
                            <p class="text-slate-600 mb-3 md:mb-4 text-sm md:text-base">System closure and pressure isolation</p>
                            <div class="flex gap-2 md:gap-3">
                                <button onclick="updateProduct('blind')" class="flex-1 py-2 md:py-2.5 bg-blue-600 text-white rounded-lg font-medium hover:bg-blue-700 transition text-xs md:text-sm">
                                    <i class="fas fa-info-circle mr-2"></i>View Details
                                </button>
                                <button onclick="checkAuthBeforeOrder('blind')" class="flex-1 py-2 md:py-2.5 bg-slate-200 text-slate-700 rounded-lg font-medium hover:bg-slate-300 transition text-xs md:text-sm">
                                    <i class="fas fa-shopping-cart mr-2"></i>Order
                                </button>
                            </div>
                        </div>
                    </div>
                    
                    <!-- Puddle Flange -->
                    <div class="gallery-product-card bg-slate-50 rounded-3xl overflow-hidden border border-slate-200 hover:border-blue-300 transition-all duration-300">
                        <div class="product-image-container" style="height: 200px;">
                            <img src="puddle-flange.png" alt="Puddle Flange" onerror="handleImageError(this, 'Puddle')" style="object-fit: contain;">
                        </div>
                        <div class="p-4 md:p-6">
                            <h4 class="font-bold text-lg md:text-xl text-slate-900 mb-2">Puddle Flange</h4>
                            <p class="text-slate-600 mb-3 md:mb-4 text-sm md:text-base">Waterproofing for pipe penetrations</p>
                            <div class="flex gap-2 md:gap-3">
                                <button onclick="updateProduct('puddle')" class="flex-1 py-2 md:py-2.5 bg-blue-600 text-white rounded-lg font-medium hover:bg-blue-700 transition text-xs md:text-sm">
                                    <i class="fas fa-info-circle mr-2"></i>View Details
                                </button>
                                <button onclick="checkAuthBeforeOrder('puddle')" class="flex-1 py-2 md:py-2.5 bg-slate-200 text-slate-700 rounded-lg font-medium hover:bg-slate-300 transition text-xs md:text-sm">
                                    <i class="fas fa-shopping-cart mr-2"></i>Order
                                </button>
                            </div>
                        </div>
                    </div>
                    
                    <!-- Plasma CNC -->
                    <div class="gallery-product-card bg-slate-50 rounded-3xl overflow-hidden border border-slate-200 hover:border-blue-300 transition-all duration-300">
                        <div class="product-image-container" style="height: 200px;">
                            <img src="plasma-cutting.png" alt="Plasma CNC Cutting" onerror="handleImageError(this, 'Plasma CNC')" style="object-fit: contain;">
                        </div>
                        <div class="p-4 md:p-6">
                            <h4 class="font-bold text-lg md:text-xl text-slate-900 mb-2">Plasma CNC Cutting</h4>
                            <p class="text-slate-600 mb-3 md:mb-4 text-sm md:text-base">High-precision automated cutting service</p>
                            <div class="flex gap-2 md:gap-3">
                                <button onclick="updateProduct('plasma')" class="flex-1 py-2 md:py-2.5 bg-blue-600 text-white rounded-lg font-medium hover:bg-blue-700 transition text-xs md:text-sm">
                                    <i class="fas fa-info-circle mr-2"></i>View Details
                                </button>
                                <button onclick="checkAuthBeforeOrder('plasma')" class="flex-1 py-2 md:py-2.5 bg-slate-200 text-slate-700 rounded-lg font-medium hover:bg-slate-300 transition text-xs md:text-sm">
                                    <i class="fas fa-shopping-cart mr-2"></i>Order
                                </button>
                            </div>
                        </div>
                    </div>
                </div>
                
                <div class="text-center mt-12 md:mt-16">
                    <button onclick="showAllProducts()" class="px-6 md:px-8 py-3 md:py-3.5 bg-gradient-to-r from-blue-600 to-blue-800 text-white font-bold rounded-xl hover:from-blue-700 hover:to-blue-900 transition shadow-lg text-sm md:text-base">
                        <i class="fas fa-boxes mr-2"></i>View All Products Catalog
                    </button>
                </div>
            </div>
        </section>

        <!-- "Know More" Deep Dive Section -->
        <section id="about" class="py-12 md:py-24 bg-white reveal">
            <div class="max-w-7xl mx-auto px-4">
                <div class="grid lg:grid-cols-2 gap-12 md:gap-16 items-start">
                    <div class="space-y-8 md:space-y-10">
                        <div>
                            <span class="text-blue-600 font-bold uppercase tracking-widest text-sm">Industrial Insight</span>
                            <h2 class="text-3xl md:text-4xl lg:text-5xl font-bold text-slate-900 mt-2">Engineering Excellence in Flange Manufacturing</h2>
                            <p class="text-slate-600 mt-4 md:mt-6 leading-relaxed text-base md:text-lg">
                                At <strong class="text-blue-700">Ultimate Flange</strong>, we believe that a flange is more than just a connector; it is a critical safety component of your infrastructure. Our engineering philosophy centers on four core pillars that ensure reliability under the most demanding conditions.
                            </p>
                        </div>

                        <div class="space-y-4 md:space-y-6">
                            <div class="knowledge-card p-6 md:p-8 rounded-3xl">
                                <div class="flex items-start gap-4">
                                    <div class="w-10 h-10 md:w-12 md:h-12 bg-blue-100 rounded-xl flex items-center justify-center flex-shrink-0">
                                        <i class="fas fa-atom text-blue-600 text-lg md:text-xl"></i>
                                    </div>
                                    <div>
                                        <h4 class="font-bold text-slate-900 text-lg md:text-xl mb-3">Metallurgical Integrity</h4>
                                        <p class="text-slate-600 leading-relaxed text-sm md:text-base">
                                            Every component starts with raw forging stock that undergoes rigorous ultrasonic testing. We ensure zero internal voids or inclusions that could lead to failure under high-cycle fatigue or cryogenic temperatures. Our material traceability is certified to EN 10204 3.1 standards.
                                        </p>
                                    </div>
                                </div>
                            </div>

                            <div class="knowledge-card p-6 md:p-8 rounded-3xl">
                                <div class="flex items-start gap-4">
                                    <div class="w-10 h-10 md:w-12 md:h-12 bg-blue-100 rounded-xl flex items-center justify-center flex-shrink-0">
                                        <i class="fas fa-ruler-combined text-blue-600 text-lg md:text-xl"></i>
                                    </div>
                                    <div>
                                        <h4 class="font-bold text-slate-900 text-lg md:text-xl mb-3">Precision Geometry</h4>
                                        <p class="text-slate-600 leading-relaxed text-sm md:text-base">
                                            Using CNC vertical turning centers with laser measurement systems, we maintain tolerances of ±0.05mm. Our gasket faces are machined to exact Ra values (0.8-3.2 μm) to guarantee 100% leak-proof sealing upon installation, even in high-vibration environments.
                                        </p>
                                    </div>
                                </div>
                            </div>

                            <div class="knowledge-card p-6 md:p-8 rounded-3xl">
                                <div class="flex items-start gap-4">
                                    <div class="w-10 h-10 md:w-12 md:h-12 bg-blue-100 rounded-xl flex items-center justify-center flex-shrink-0">
                                        <i class="fas fa-bolt text-blue-600 text-lg md:text-xl"></i>
                                    </div>
                                    <div>
                                        <h4 class="font-bold text-slate-900 text-lg md:text-xl mb-3">Advanced Fabrication</h4>
                                        <p class="text-slate-600 leading-relaxed text-sm md:text-base">
                                            Beyond standard flanges, our Plasma CNC division provides custom profile cutting from carbon or stainless steel up to 100mm thick with minimal Heat Affected Zones (HAZ). Our oxy-fuel cutting handles sections up to 350mm for structural applications.
                                        </p>
                                    </div>
                                </div>
                            </div>
                        </div>
                    </div>

                    <div class="lg:sticky lg:top-24 bg-gradient-to-br from-slate-900 to-blue-900 rounded-3xl p-6 md:p-8 lg:p-10 text-white shadow-2xl">
                        <h3 class="text-2xl md:text-3xl font-bold mb-8 md:mb-12">Why Partner With Us?</h3>
                        <div class="space-y-6 md:space-y-10">
                            <div class="flex gap-4 md:gap-6">
                                <div class="text-blue-300 font-bold text-2xl md:text-4xl">01</div>
                                <div>
                                    <h5 class="font-bold text-lg md:text-xl mb-2 md:mb-3">Direct Supplier Connection</h5>
                                    <p class="text-slate-300 leading-relaxed text-sm md:text-base">Connect directly with verified suppliers through our real-time chat system. Negotiate terms, get instant quotes, and build relationships before placing orders.</p>
                                </div>
                            </div>
                            <div class="flex gap-4 md:gap-6">
                                <div class="text-blue-300 font-bold text-2xl md:text-4xl">02</div>
                                <div>
                                    <h5 class="font-bold text-lg md:text-xl mb-2 md:mb-3">Rapid Engineering Support</h5>
                                    <p class="text-slate-300 leading-relaxed text-sm md:text-base">Our in-house design team can translate complex technical requirements into CNC-ready CAD files in under 4 hours. We provide FEA analysis for custom applications.</p>
                                </div>
                            </div>
                            <div class="flex gap-4 md:gap-6">
                                <div class="text-blue-300 font-bold text-2xl md:text-4xl">03</div>
                                <div>
                                    <h5 class="font-bold text-lg md:text-xl mb-2 md:mb-3">Supplier Verification System</h5>
                                    <p class="text-slate-300 leading-relaxed text-sm md:text-base">All suppliers are verified, rated, and reviewed. You can see their track record, response times, and customer satisfaction before making contact.</p>
                                </div>
                            </div>
                            <div class="flex gap-4 md:gap-6">
                                <div class="text-blue-300 font-bold text-2xl md:text-4xl">04</div>
                                <div>
                                    <h5 class="font-bold text-lg md:text-xl mb-2 md:mb-3">Direct Order Routing</h5>
                                    <p class="text-slate-300 leading-relaxed text-sm md:text-base">When you place an order, it goes directly to your chosen supplier. No middlemen, faster processing, and better communication throughout.</p>
                                </div>
                            </div>
                        </div>
                        
                        <div class="mt-8 md:mt-12 pt-6 md:pt-8 border-t border-slate-700">
                            <button onclick="checkAuthBeforeOrder()" class="w-full py-3 md:py-4 bg-white text-slate-900 font-bold rounded-xl hover:bg-blue-50 transition text-center block text-sm md:text-base order-button">
                                <i class="fas fa-calendar-check mr-2"></i>Connect with Suppliers
                            </button>
                        </div>
                    </div>
                </div>
            </div>
        </section>

        <!-- Contact Section -->
        <section id="contact" class="py-12 md:py-20 bg-slate-50 reveal">
            <div class="max-w-7xl mx-auto px-4">
                <div class="text-center mb-12 md:mb-16">
                    <h2 class="text-3xl md:text-4xl lg:text-5xl font-bold text-slate-900 mb-4">Get in Touch</h2>
                    <p class="text-slate-600 max-w-3xl mx-auto text-base md:text-lg">Contact our engineering team for technical support, quotes, or consultation on your next project.</p>
                </div>
                
                <div class="grid lg:grid-cols-3 gap-6 md:gap-8">
                    <div class="bg-white p-6 md:p-8 rounded-3xl shadow-lg">
                        <div class="w-12 h-12 md:w-14 md:h-14 bg-blue-100 rounded-2xl flex items-center justify-center mb-4 md:mb-6">
                            <i class="fas fa-phone-alt text-blue-600 text-xl md:text-2xl"></i>
                        </div>
                        <h3 class="text-lg md:text-xl font-bold text-slate-900 mb-2 md:mb-3">Call Us</h3>
                        <p class="text-slate-600 mb-3 md:mb-4 text-sm md:text-base">Speak directly with our technical sales team</p>
                        <a href="tel:+919123456789" class="text-blue-700 font-bold text-base md:text-lg hover:text-blue-800">+91 7307709671</a>
                        <p class="text-slate-500 text-xs md:text-sm mt-2">Mon-Fri, 8:00 AM - 6:00 PM IST</p>
                    </div>
                    
                    <div class="bg-white p-6 md:p-8 rounded-3xl shadow-lg">
                        <div class="w-12 h-12 md:w-14 md:h-14 bg-blue-100 rounded-2xl flex items-center justify-center mb-4 md:mb-6">
                            <i class="fas fa-envelope text-blue-600 text-xl md:text-2xl"></i>
                        </div>
                        <h3 class="text-lg md:text-xl font-bold text-slate-900 mb-2 md:mb-3">Email Us</h3>
                        <p class="text-slate-600 mb-3 md:mb-4 text-sm md:text-base">Send detailed project requirements for quotes</p>
                        <a href="mailto:sales@ultimateflange.com" class="text-blue-700 font-bold text-base md:text-lg hover:text-blue-800">sales@ultimateflange.com</a>
                        <p class="text-slate-500 text-xs md:text-sm mt-2">Response within 4 business hours</p>
                    </div>
                    
                    <div class="bg-white p-6 md:p-8 rounded-3xl shadow-lg">
                        <div class="w-12 h-12 md:w-14 md:h-14 bg-blue-100 rounded-2xl flex items-center justify-center mb-4 md:mb-6">
                            <i class="fas fa-map-marker-alt text-blue-600 text-xl md:text-2xl"></i>
                        </div>
                        <h3 class="text-lg md:text-xl font-bold text-slate-900 mb-2 md:mb-3">Visit Us</h3>
                        <p class="text-slate-600 mb-3 md:mb-4 text-sm md:text-base">Schedule a plant tour or in-person meeting</p>
                        <address class="text-slate-700 not-italic font-medium text-sm md:text-base">
                            pipe road kurla west<br>
                            mumbai, pin-400070<br>
                            india maharashtra
                        </address>
                        <p class="text-slate-500 text-xs md:text-sm mt-2">By appointment only</p>
                    </div>
                </div>
                
                <!-- Quick Order Button -->
                <div class="mt-12 md:mt-16 text-center">
                    <button onclick="checkAuthBeforeOrder()" class="px-6 md:px-10 py-3 md:py-4 bg-gradient-to-r from-green-600 to-green-800 text-white font-bold rounded-xl hover:from-green-700 hover:to-green-900 transition shadow-lg text-base md:text-base order-button">
                        <i class="fas fa-bolt mr-2"></i>Connect with Suppliers
                    </button>
                    <p class="text-slate-500 mt-3 md:mt-4 text-xs md:text-sm">Chat with suppliers and get instant quotes</p>
                </div>
            </div>
        </section>

        <!-- Footer -->
        <footer class="bg-slate-900 text-white py-12 md:py-16 px-4">
            <div class="max-w-7xl mx-auto">
                <div class="grid md:grid-cols-4 gap-8 md:gap-10 mb-8 md:mb-12">
                    <div>
                        <div class="flex items-center gap-3 mb-4 md:mb-6">
                            <div class="w-10 h-10 bg-blue-600 rounded-xl flex items-center justify-center">
                                <i class="fas fa-cogs text-white"></i>
                            </div>
                            <span class="text-xl font-bold">UltimateFlange</span>
                        </div>
                        <p class="text-slate-400 text-sm leading-relaxed">Setting the global standard for precision industrial components since 1999.</p>
                    </div>
                    
                    <div>
                        <h4 class="font-bold text-lg mb-4 md:mb-6">Products</h4>
                        <ul class="space-y-2 md:space-y-3 text-slate-400 text-sm">
                            <li><a href="#" onclick="updateProduct('lwn'); return false;" class="hover:text-white transition">Long Weld Neck Flanges</a></li>
                            <li><a href="#" onclick="updateProduct('wnf'); return false;" class="hover:text-white transition">Weld Neck Flanges</a></li>
                            <li><a href="#" onclick="updateProduct('slipon'); return false;" class="hover:text-white transition">Slip-On Flanges</a></li>
                            <li><a href="#" onclick="updateProduct('blind'); return false;" class="hover:text-white transition">Blind Flanges</a></li>
                            <li><a href="#" onclick="updateProduct('plasma'); return false;" class="hover:text-white transition">Plasma CNC Cutting</a></li>
                        </ul>
                    </div>
                    
                    <div>
                        <h4 class="font-bold text-lg mb-4 md:mb-6">Resources</h4>
                        <ul class="space-y-2 md:space-y-3 text-slate-400 text-sm">
                            <li><a href="#" onclick="document.getElementById('specifications').scrollIntoView({behavior:'smooth'}); return false;" class="hover:text-white transition">Technical Specifications</a></li>
                            <li><a href="#" onclick="downloadProductFiles(); return false;" class="hover:text-white transition">CAD Drawings</a></li>
                            <li><a href="#" onclick="document.getElementById('about').scrollIntoView({behavior:'smooth'}); return false;" class="hover:text-white transition">Material Selection Guide</a></li>
                            <li><a href="#" class="hover:text-white transition">Installation Manuals</a></li>
                            <li><a href="#" onclick="showAllProducts(); return false;" class="hover:text-white transition">Product Catalog</a></li>
                        </ul>
                    </div>
                    
                    <div>
                        <h4 class="font-bold text-lg mb-4 md:mb-6">Ordering Process</h4>
                        <ul class="space-y-2 md:space-y-3 text-slate-400 text-sm">
                            <li><a href="#" onclick="checkAuthBeforeOrder(); return false;" class="hover:text-white transition">Connect with Suppliers</a></li>
                            <li><a href="#" onclick="openTrackingModal(); return false;" class="hover:text-white transition">Track Order</a></li>
                            <li><a href="#" class="hover:text-white transition">Payment Terms</a></li>
                            <li><a href="#" class="hover:text-white transition">Order Tracking</a></li>
                            <li><a href="#" onclick="openDashboard(); return false;" class="hover:text-white transition">Supplier Portal</a></li>
                        </ul>
                    </div>
                </div>
                
                <div class="pt-6 md:pt-8 border-t border-slate-800 flex flex-col md:flex-row justify-between items-center">
                    <p class="text-slate-400 text-xs md:text-sm">© 2024 Ultimate Flange Manufacturing Ltd. All rights reserved.</p>
                    <div class="flex gap-3 md:gap-4 mt-3 md:mt-0">
                        <a href="#" class="text-slate-400 hover:text-white">
                            <i class="fab fa-linkedin text-base md:text-lg"></i>
                        </a>
                        <a href="#" class="text-slate-400 hover:text-white">
                            <i class="fab fa-twitter text-base md:text-lg"></i>
                        </a>
                        <a href="#" class="text-slate-400 hover:text-white">
                            <i class="fab fa-youtube text-base md:text-lg"></i>
                        </a>
                    </div>
                </div>
            </div>
        </footer>
    </div>

    <script>
        // ========== CONFIGURATION ==========
        const API_BASE_URL = "http://localhost:8080"; // Will be moved to environment variable
        const SESSION_TIMEOUT = 30 * 60 * 1000; // 30 minutes in milliseconds
        let sessionTimeoutId = null;

        // ========== GLOBAL STATE MANAGEMENT ==========
        let appState = {
            isAuthenticated: false,
            currentUser: { type: 'visitor' },
            currentUserType: 'visitor',
            isSupplier: false,
            currentOrderStep: 1,
            currentProductKey: 'lwn',
            selectedSupplier: null,
            userOrders: [],
            chatMessages: {},
            charts: {} // Store chart instances for cleanup
        };

        // ========== SUPPLIER DATA (Will be moved to backend) ==========
        const supplierData = {
            'lwn': [
                {
                    id: 'sup1',
                    name: 'Precision Flange Co.',
                    company: 'Precision Manufacturing Ltd.',
                    rating: 4.8,
                    reviews: 142,
                    responseTime: '2 hours',
                    specialization: ['ASME B16.5', 'High Pressure', 'Pressure Vessel'],
                    location: 'Mumbai, India',
                    email: 'sales@precisionflange.com',
                    phone: '+91 9876543210',
                    status: 'Online',
                    minOrder: '₹50,000',
                    leadTime: '2-3 weeks'
                },
                {
                    id: 'sup2',
                    name: 'SteelTech Industries',
                    company: 'SteelTech Manufacturing',
                    rating: 4.6,
                    reviews: 89,
                    responseTime: '4 hours',
                    specialization: ['Carbon Steel', 'Stainless Steel', 'Alloy'],
                    location: 'Pune, India',
                    email: 'orders@steeltech.com',
                    phone: '+91 9876543211',
                    status: 'Online',
                    minOrder: '₹25,000',
                    leadTime: '3-4 weeks'
                },
                {
                    id: 'sup3',
                    name: 'Global Forge Ltd.',
                    company: 'Global Forge Corporation',
                    rating: 4.9,
                    reviews: 256,
                    responseTime: '1 hour',
                    specialization: ['Forged Flanges', 'Heavy Duty', 'Custom'],
                    location: 'Delhi, India',
                    email: 'info@globalforge.com',
                    phone: '+91 9876543212',
                    status: 'Away',
                    minOrder: '₹1,00,000',
                    leadTime: '4-5 weeks'
                }
            ],
            'wnf': [
                {
                    id: 'sup4',
                    name: 'WeldMaster Corp',
                    company: 'WeldMaster Industries',
                    rating: 4.7,
                    reviews: 178,
                    responseTime: '3 hours',
                    specialization: ['Weld Neck', 'High Temperature', 'Cryogenic'],
                    location: 'Chennai, India',
                    email: 'sales@weldmaster.com',
                    phone: '+91 9876543213',
                    status: 'Online',
                    minOrder: '₹75,000',
                    leadTime: '2-3 weeks'
                }
            ],
            'slipon': [
                {
                    id: 'sup5',
                    name: 'Standard Flange Co.',
                    company: 'Standard Manufacturing',
                    rating: 4.5,
                    reviews: 95,
                    responseTime: '6 hours',
                    specialization: ['Slip-On', 'Standard Pressure', 'Budget'],
                    location: 'Ahmedabad, India',
                    email: 'info@standardflange.com',
                    phone: '+91 9876543214',
                    status: 'Online',
                    minOrder: '₹20,000',
                    leadTime: '1-2 weeks'
                }
            ],
            'blind': [
                {
                    id: 'sup6',
                    name: 'Blind Flange Specialists',
                    company: 'BFS Manufacturing',
                    rating: 4.8,
                    reviews: 112,
                    responseTime: '2 hours',
                    specialization: ['Blind Flanges', 'Pressure Isolation', 'Custom'],
                    location: 'Bangalore, India',
                    email: 'sales@bfs.com',
                    phone: '+91 9876543215',
                    status: 'Online',
                    minOrder: '₹30,000',
                    leadTime: '2-3 weeks'
                }
            ]
        };
        
        // ========== PRODUCT DATA ==========
        const productData = {
            lwn: {
                title: "Long Weld Neck Flange (LWN)",
                desc: "ASME B16.5 Class 900 DN15 Long Weld Neck flange with extended hub design for pressure vessel applications. Engineered for high-pressure systems where reliability and structural integrity are critical. Manufactured with full traceability and compliance to international standards.",
                features: [
                    "ASME B16.5 Class 900 compliant",
                    "Nominal Diameter: DN15 (1/2\")",
                    "Extended hub for stress distribution",
                    "Full material traceability",
                    "Precision machined sealing surface",
                    "Ideal for pressure vessel connections"
                ],
                specs: {
                    general: {
                        "Reference": "ASMEB16.5-900-DN15",
                        "Standard": "ASME B16.5",
                        "Nominal Pressure": "150",
                        "Nominal Diameter": "15 mm (1/2\")",
                        "Design": "Flange ASME B16.5 - ASME 900 - Long Weld Neck",
                        "Supplier": "CAMAN",
                        "OmniClass23": "23.27.45.29"
                    },
                    materials: {
                        "Stainless Steel": "ASTM A182 F316/316L, F304/304L",
                        "Carbon Steel": "ASTM A105, A350 LF2",
                        "Alloy Steel": "ASTM A182 F11, F22, F91",
                        "Duplex Steel": "A182 F51 (2205), F53 (2507)",
                        "Special Alloys": "Inconel 625, Monel 400, Hastelloy"
                    }
                }
            },
            wnf: {
                title: "Weld Neck Flange (WNF)",
                desc: "High-performance flanges engineered for severe service conditions, featuring a long tapered hub that reduces stress concentrations and improves fatigue resistance. Ideal for high-pressure, high-temperature, and cryogenic applications.",
                features: [
                    "Designed for high-pressure systems (up to 2500#)",
                    "Long tapered hub reduces stress concentration",
                    "Matches pipe internal diameter for smooth flow",
                    "Certified for high-temperature and cryogenic service",
                    "ASME B16.5 compliant design",
                    "Available with RF, RTJ, or FF faces"
                ],
                specs: {
                    general: {
                        "Size Range": "1/2\" to 72\" (DN15 to DN1800)",
                        "Standards": "ANSI B16.5, B16.47, ASME Section VIII",
                        "Pressure Ratings": "150# to 2500# (PN6 to PN420)",
                        "Face Types": "RF, RTJ, FF, LMF",
                        "Bolt Circle": "Per ASME B16.5 tables",
                        "Thickness": "Schedule 10 to XXS"
                    },
                    materials: {
                        "Stainless Steel": "A182 F316/304L, F316H, F321",
                        "Carbon Steel": "A105, A350 LF2, A694 F52",
                        "Alloy Steel": "A182 F11, F22, F91",
                        "Duplex/Super Duplex": "F51 (2205), F53 (2507)",
                        "Nickel Alloys": "Inconel 625, Monel 400, Hastelloy"
                    }
                }
            },
            slipon: {
                title: "Slip-On Flange",
                desc: "A cost-effective flange solution that slides over the pipe and is welded both inside and outside for strength. Easier to align than weld neck flanges and suitable for lower pressure applications.",
                features: [
                    "Lower installation cost and time",
                    "Easy alignment during installation",
                    "Suitable for standard pressure duty",
                    "Internal and external welding for strength",
                    "Available in raised face or flat face"
                ],
                specs: {
                    general: {
                        "Size Range": "1/2\" to 60\" (DN15 to DN1500)",
                        "Standards": "ANSI B16.5, B16.47, EN 1092-1",
                        "Pressure Ratings": "150# to 600# (PN6 to PN100)",
                        "Face Types": "RF, FF",
                        "Hub Length": "Shorter than weld neck",
                        "Weight": "Approximately 1/3 less than WNF"
                    },
                    materials: {
                        "Stainless Steel": "A182 F304L, F316L",
                        "Carbon Steel": "A105, A350 LF2",
                        "Alloy Steel": "Limited grades available",
                        "Mild Steel": "S235JR, S355JR"
                    }
                }
            },
            blind: {
                title: "Blind Flange",
                desc: "Used to seal the end of a piping system, pressure vessel, or valve. Designed to handle high stress from internal pressure and provide a positive shut-off for maintenance or future expansion.",
                features: [
                    "Pressure isolation and system closure",
                    "Removable for maintenance access",
                    "Solid forged construction for strength",
                    "Critical safety shut-off component",
                    "Available with or without jack screw holes"
                ],
                specs: {
                    general: {
                        "Size Range": "1/2\" to 72\" (DN15 to DN1800)",
                        "Standards": "B16.5, B16.47, EN 1092-1",
                        "Pressure Ratings": "150# to 2500#",
                        "Face Types": "RF, RTJ, FF",
                        "Thickness": "Per ASME B16.5 Table 8",
                        "Test Pressure": "1.5x rated pressure"
                    },
                    materials: {
                        "Stainless Steel": "A182 F316L, F304L",
                        "Carbon Steel": "A105, A350 LF2",
                        "Alloy Steel": "A182 F22, F11",
                        "Lining Options": "Rubber, PTFE, Glass"
                    }
                }
            },
            puddle: {
                title: "Puddle Flange",
                desc: "Specialty flange used in construction to prevent fluid seepage where pipes pass through concrete walls or foundations. Provides a watertight seal between pipe and structure.",
                features: [
                    "Waterproofing for pipe penetrations",
                    "Cast iron or fabricated construction",
                    "Civil engineering standard compliance",
                    "Watertight seal with concrete",
                    "Available with or without anchoring studs"
                ],
                specs: {
                    general: {
                        "Size Range": "DN50 to DN2000",
                        "Standards": "EN1092-1, BS4504, AWWA",
                        "Pressure Ratings": "PN6, PN10, PN16",
                        "Application": "Water Treatment, Sewage",
                        "Seal Type": "Rubber gasket or mechanical"
                    },
                    materials: {
                        "Stainless Steel": "316 / 304, 1.4404 / 1.4301",
                        "Carbon Steel": "Galvanized S235, S355",
                        "Coating": "Fusion Bonded Epoxy, Hot Dip Galv",
                        "Other Materials": "Ductile Iron EN-GJS-400-15"
                    }
                }
            },
            plasma: {
                title: "Plasma CNC Cutting",
                desc: "High-precision automated plasma cutting service for custom plate shapes, flange blanks, and structural components with tight tolerances and superior edge quality.",
                features: [
                    "Cutting capacity up to 100mm thickness",
                    "Complex CAD geometry translation",
                    "Fast turnaround (3-5 business days)",
                    "Superior edge finish with minimal dross",
                    "Nesting optimization for material efficiency"
                ],
                specs: {
                    general: {
                        "Max Plate Size": "3000mm x 6000mm (10' x 20')",
                        "Thickness Range": "3mm to 100mm (1/8\" to 4\")",
                        "Tolerance": "± 1.5mm (± 0.060\")",
                        "Edge Quality": "Ra 25-50 μm, minimal HAZ",
                        "Bevel Cutting": "Up to 45 degrees"
                    },
                    materials: {
                        "Mild Steel": "S235, S355, A36, A572",
                        "Stainless Steel": "304, 316, 310, 321",
                        "Aluminium": "5083, 6082, 5052",
                        "Wear Plate": "Hardox 400/500, AR400/500"
                    }
                }
            },
            profile: {
                title: "Profile Cutting Services",
                desc: "Heavy-duty oxy-fuel profile cutting for thick carbon steel sections, base plates, and structural components used in bridges, buildings, and heavy machinery.",
                features: [
                    "Extreme thickness capability (300mm+)",
                    "Structural integrity preservation",
                    "Massive scale capacity",
                    "Precision oxy-fuel technology",
                    "Straightness within 1mm per meter"
                ],
                specs: {
                    general: {
                        "Max Thickness": "350mm (14\") carbon steel",
                        "Width Capacity": "Up to 4000mm (13')",
                        "Accuracy": "± 2mm (± 0.080\")",
                        "Beveling": "Available up to 30 degrees",
                        "Surface Finish": "As-cut or machined"
                    },
                    materials: {
                        "Structural Steel": "S275, S355, A992",
                        "Pressure Vessel": "A516 Grade 70, A537",
                        "Marine Grade": "Grade A, AH32, DH36",
                        "Hardness": "Consistent through-cut up to 400 HB"
                    }
                }
            }
        };

        // ========== UTILITY FUNCTIONS ==========
        
        function showLoading(message = 'Loading...') {
            const overlay = document.getElementById('loading-overlay');
            const messageEl = document.getElementById('loading-message');
            if (overlay && messageEl) {
                messageEl.textContent = message;
                overlay.classList.remove('hidden');
            }
        }

        function hideLoading() {
            const overlay = document.getElementById('loading-overlay');
            if (overlay) {
                overlay.classList.add('hidden');
            }
        }

        function showError(containerId, message) {
            const container = document.getElementById(containerId);
            if (container) {
                container.innerHTML = `
                    <i class="fas fa-exclamation-circle"></i>
                    <span>${message}</span>
                `;
                container.classList.remove('hidden');
                
                // Auto hide after 5 seconds
                setTimeout(() => {
                    container.classList.add('hidden');
                }, 5000);
            } else {
                alert(message);
            }
        }

        function showSuccess(containerId, message) {
            const container = document.getElementById(containerId);
            if (container) {
                container.innerHTML = `
                    <i class="fas fa-check-circle"></i>
                    <span>${message}</span>
                `;
                container.classList.remove('hidden');
                container.className = 'success-message';
                
                setTimeout(() => {
                    container.classList.add('hidden');
                }, 5000);
            }
        }

        function validateEmail(email) {
            const re = /^[^\s@]+@[^\s@]+\.[^\s@]+$/;
            return re.test(email);
        }

        function validatePhone(phone) {
            const re = /^[\+]?[(]?[0-9]{3}[)]?[-\s\.]?[0-9]{3}[-\s\.]?[0-9]{4,6}$/;
            return re.test(phone);
        }

        function validateRequired(value) {
            return value && value.trim() !== '';
        }

        function clearValidationErrors() {
            document.querySelectorAll('.validation-message').forEach(el => {
                el.classList.add('hidden');
                el.textContent = '';
            });
            document.querySelectorAll('.input-error').forEach(el => {
                el.classList.remove('input-error');
            });
        }

        function showFieldError(fieldId, message) {
            const field = document.getElementById(fieldId);
            const errorEl = document.getElementById(fieldId + '-error');
            if (field && errorEl) {
                field.classList.add('input-error');
                errorEl.textContent = message;
                errorEl.classList.remove('hidden');
            }
        }

        // ========== SESSION MANAGEMENT ==========
        
        function startSessionTimer() {
            if (sessionTimeoutId) {
                clearTimeout(sessionTimeoutId);
            }
            
            sessionTimeoutId = setTimeout(() => {
                if (appState.isAuthenticated) {
                    logout('Session expired. Please login again.');
                }
            }, SESSION_TIMEOUT);
        }

        function resetSessionTimer() {
            if (appState.isAuthenticated) {
                startSessionTimer();
            }
        }

        // ========== AUTHENTICATION FUNCTIONS ==========
        
        function initializeAuth() {
            // Check localStorage only (single source of truth)
            const token = localStorage.getItem('authToken');
            const userData = localStorage.getItem('userData');
            
            if (token && userData) {
                try {
                    appState.currentUser = JSON.parse(userData);
                    appState.isAuthenticated = true;
                    appState.currentUserType = appState.currentUser.type || 'partner';
                    appState.isSupplier = appState.currentUser.type === 'supplier';
                    
                    document.body.classList.add('authenticated');
                    document.body.classList.remove('visitor-mode', 'require-auth');
                    document.getElementById('auth-overlay').style.display = 'none';
                    
                    updateUIAfterAuth();
                    startSessionTimer();
                } catch (e) {
                    console.error('Failed to parse user data:', e);
                    clearAuth();
                }
            } else {
                // Default to visitor mode
                clearAuth(true); // true for initial load to keep visitor mode
            }
        }

        function clearAuth(keepVisitorMode = false) {
            localStorage.removeItem('authToken');
            localStorage.removeItem('userData');
            
            appState.isAuthenticated = false;
            appState.currentUser = { type: 'visitor' };
            appState.currentUserType = 'visitor';
            appState.isSupplier = false;
            
            // For initial load, keep visitor mode without auth overlay
            if (keepVisitorMode) {
                document.body.classList.add('visitor-mode');
                document.body.classList.remove('authenticated', 'require-auth');
                document.getElementById('auth-overlay').style.display = 'none';
            } else {
                // When logging out, show auth overlay
                document.body.classList.add('require-auth');
                document.body.classList.remove('authenticated', 'visitor-mode');
                document.getElementById('auth-overlay').style.display = 'flex';
            }
            
            if (sessionTimeoutId) {
                clearTimeout(sessionTimeoutId);
                sessionTimeoutId = null;
            }
            
            updateUIAfterAuth();
        }

        function loginUser(event) {
            event.preventDefault();
            clearValidationErrors();
            
            const email = document.getElementById('login-email').value;
            const password = document.getElementById('login-password').value;
            const rememberMe = document.getElementById('remember-me').checked;

            // Validation
            let isValid = true;
            
            if (!validateEmail(email)) {
                showFieldError('login-email', 'Please enter a valid email address');
                isValid = false;
            }
            
            if (!validateRequired(password)) {
                showFieldError('login-password', 'Password is required');
                isValid = false;
            }

            if (!isValid) return;

            showLoading('Logging in...');

            // Simulate API call
            setTimeout(() => {
                // Demo login (will be replaced with actual API)
                if (email && password) {
                    const userData = {
                        id: '1',
                        email: email,
                        type: appState.currentUserType || 'partner',
                        name: email.split('@')[0]
                    };
                    
                    localStorage.setItem('authToken', 'demo-token-' + Date.now());
                    localStorage.setItem('userData', JSON.stringify(userData));
                    
                    appState.isAuthenticated = true;
                    appState.currentUser = userData;
                    
                    document.body.classList.add('authenticated');
                    document.body.classList.remove('visitor-mode', 'require-auth');
                    document.getElementById('auth-overlay').style.display = 'none';
                    
                    updateUIAfterAuth();
                    startSessionTimer();
                    
                    showSuccess('login-error-container', 'Login successful!');
                } else {
                    showError('login-error-container', 'Invalid credentials');
                }
                
                hideLoading();
            }, 1000);
        }

        function signupUser(event) {
            event.preventDefault();
            clearValidationErrors();
            
            const firstName = document.getElementById('signup-firstname').value;
            const lastName = document.getElementById('signup-lastname').value;
            const email = document.getElementById('signup-email').value;
            const password = document.getElementById('signup-password').value;
            const company = document.getElementById('signup-company').value;
            const industry = document.getElementById('signup-industry').value;

            // Validation
            let isValid = true;
            
            if (!validateRequired(firstName)) {
                showFieldError('signup-firstname', 'First name is required');
                isValid = false;
            }
            
            if (!validateRequired(lastName)) {
                showFieldError('signup-lastname', 'Last name is required');
                isValid = false;
            }
            
            if (!validateEmail(email)) {
                showFieldError('signup-email', 'Please enter a valid email address');
                isValid = false;
            }
            
            if (!validateRequired(password) || password.length < 6) {
                showFieldError('signup-password', 'Password must be at least 6 characters');
                isValid = false;
            }
            
            if (!validateRequired(company)) {
                showFieldError('signup-company', 'Company name is required');
                isValid = false;
            }

            if (!isValid) return;

            showLoading('Creating account...');

            // Simulate API call
            setTimeout(() => {
                const userData = {
                    id: Date.now().toString(),
                    email: email,
                    type: 'partner',
                    name: firstName + ' ' + lastName,
                    company: company,
                    industry: industry
                };
                
                localStorage.setItem('authToken', 'demo-token-' + Date.now());
                localStorage.setItem('userData', JSON.stringify(userData));
                
                appState.isAuthenticated = true;
                appState.currentUser = userData;
                
                document.body.classList.add('authenticated');
                document.body.classList.remove('visitor-mode', 'require-auth');
                document.getElementById('auth-overlay').style.display = 'none';
                
                updateUIAfterAuth();
                startSessionTimer();
                
                showSuccess('signup-error-container', 'Account created successfully!');
                hideLoading();
            }, 1500);
        }

        function handleVisitor(e) {
            if(e) e.preventDefault();
            
            // Clear any existing auth state
            localStorage.removeItem('authToken');
            localStorage.removeItem('userData');
            
            appState.isAuthenticated = false;
            appState.currentUser = { type: 'visitor' };
            appState.currentUserType = 'visitor';
            appState.isSupplier = false;
            
            // Set visitor mode
            document.body.classList.add('visitor-mode');
            document.body.classList.remove('authenticated', 'require-auth');
            document.getElementById('auth-overlay').style.display = 'none';
            
            updateUIAfterAuth();
            
            showSuccess('login-error-container', 'Continuing as visitor');
        }

        function logout(message = 'Logged out successfully') {
            clearAuth(false); // false to show auth overlay
            closeDashboard();
            closeOrderModal();
            closeTrackingModal();
            closeChat();
            showSuccess('login-error-container', message);
        }

        // ========== UI UPDATE FUNCTIONS ==========
        
        function updateUIAfterAuth() {
            const statusBadge = document.getElementById('user-status');
            const mobileStatus = document.getElementById('mobile-user-status');
            
            if (appState.isAuthenticated && appState.currentUser.type !== 'visitor') {
                statusBadge.innerHTML = `<i class="fas fa-user-shield mr-1"></i>${appState.currentUser.type === 'supplier' ? 'Supplier' : 'Partner'}`;
                mobileStatus.innerHTML = appState.currentUser.type === 'supplier' ? 'Supplier' : 'Partner';
                
                // Show relevant buttons
                const logoutBtn = document.getElementById('logout-btn');
                const mobileLogoutBtn = document.getElementById('mobile-logout-btn');
                const loginBtn = document.getElementById('login-btn');
                const mobileLoginBtn = document.getElementById('mobile-login-btn');
                const profileBtn = document.getElementById('profile-btn');
                const mobileProfileLink = document.getElementById('mobile-profile-link');
                const dashboardBtn = document.getElementById('dashboard-btn');
                const mobileDashboardLink = document.getElementById('mobile-dashboard-link');
                const supplierDashboardBtn = document.getElementById('supplier-dashboard-btn');
                const mobileSupplierDashboardLink = document.getElementById('mobile-supplier-dashboard-link');
                
                if (logoutBtn) logoutBtn.classList.remove('hidden');
                if (mobileLogoutBtn) mobileLogoutBtn.classList.remove('hidden');
                if (loginBtn) loginBtn.classList.add('hidden');
                if (mobileLoginBtn) mobileLoginBtn.classList.add('hidden');
                if (profileBtn) profileBtn.classList.remove('hidden');
                if (mobileProfileLink) mobileProfileLink.classList.remove('hidden');
                
                if (appState.currentUser.type === 'supplier') {
                    if (supplierDashboardBtn) supplierDashboardBtn.classList.remove('hidden');
                    if (mobileSupplierDashboardLink) mobileSupplierDashboardLink.classList.remove('hidden');
                    if (dashboardBtn) dashboardBtn.classList.add('hidden');
                    if (mobileDashboardLink) mobileDashboardLink.classList.add('hidden');
                } else {
                    if (dashboardBtn) dashboardBtn.classList.remove('hidden');
                    if (mobileDashboardLink) mobileDashboardLink.classList.remove('hidden');
                    if (supplierDashboardBtn) supplierDashboardBtn.classList.add('hidden');
                    if (mobileSupplierDashboardLink) mobileSupplierDashboardLink.classList.add('hidden');
                }
            } else {
                // Visitor mode
                statusBadge.innerHTML = '<i class="fas fa-user mr-1"></i>Visitor';
                mobileStatus.innerHTML = 'Visitor';
                
                // Hide authenticated buttons
                const logoutBtn = document.getElementById('logout-btn');
                const mobileLogoutBtn = document.getElementById('mobile-logout-btn');
                const loginBtn = document.getElementById('login-btn');
                const mobileLoginBtn = document.getElementById('mobile-login-btn');
                const profileBtn = document.getElementById('profile-btn');
                const mobileProfileLink = document.getElementById('mobile-profile-link');
                const dashboardBtn = document.getElementById('dashboard-btn');
                const mobileDashboardLink = document.getElementById('mobile-dashboard-link');
                const supplierDashboardBtn = document.getElementById('supplier-dashboard-btn');
                const mobileSupplierDashboardLink = document.getElementById('mobile-supplier-dashboard-link');
                
                if (logoutBtn) logoutBtn.classList.add('hidden');
                if (mobileLogoutBtn) mobileLogoutBtn.classList.add('hidden');
                if (loginBtn) loginBtn.classList.remove('hidden');
                if (mobileLoginBtn) mobileLoginBtn.classList.remove('hidden');
                if (profileBtn) profileBtn.classList.add('hidden');
                if (mobileProfileLink) mobileProfileLink.classList.add('hidden');
                if (dashboardBtn) dashboardBtn.classList.add('hidden');
                if (mobileDashboardLink) mobileDashboardLink.classList.add('hidden');
                if (supplierDashboardBtn) supplierDashboardBtn.classList.add('hidden');
                if (mobileSupplierDashboardLink) mobileSupplierDashboardLink.classList.add('hidden');
            }
        }

        function toggleAuthView(view) {
            const loginForm = document.getElementById('login-form');
            const signupForm = document.getElementById('signup-form');
            if (view === 'login') {
                loginForm.classList.remove('hidden');
                signupForm.classList.add('hidden');
            } else {
                loginForm.classList.add('hidden');
                signupForm.classList.remove('hidden');
            }
        }
        
        function openAuthModal() {
            document.body.classList.add('require-auth');
            document.body.classList.remove('visitor-mode');
            document.getElementById('auth-overlay').style.display = 'flex';
            document.body.style.overflow = 'hidden';
        }
        
        function closeAuth() {
            // If we're closing auth without authenticating, go back to visitor mode
            if (!appState.isAuthenticated) {
                document.body.classList.add('visitor-mode');
                document.body.classList.remove('require-auth');
            }
            document.getElementById('auth-overlay').style.display = 'none';
            document.body.style.overflow = 'auto';
        }

        function setUserType(type) {
            appState.currentUserType = type;
            const buttons = document.querySelectorAll('#login-form button[onclick^="setUserType"]');
            buttons.forEach(btn => {
                if (btn.textContent.includes(type === 'partner' ? 'Partner' : 'Supplier')) {
                    btn.classList.add('border-blue-200', 'bg-blue-50', 'text-blue-700');
                    btn.classList.remove('border-slate-200', 'hover:border-blue-200', 'hover:bg-blue-50');
                } else {
                    btn.classList.remove('border-blue-200', 'bg-blue-50', 'text-blue-700');
                    btn.classList.add('border-slate-200', 'hover:border-blue-200', 'hover:bg-blue-50');
                }
            });
        }

        // ========== MOBILE MENU ==========
        
        function toggleMobileMenu() {
            const menu = document.getElementById('mobile-menu');
            const overlay = document.getElementById('mobile-menu-overlay');
            
            if (menu && overlay) {
                if (menu.classList.contains('active')) {
                    menu.classList.remove('active');
                    overlay.classList.remove('active');
                    document.body.style.overflow = 'auto';
                } else {
                    menu.classList.add('active');
                    overlay.classList.add('active');
                    document.body.style.overflow = 'hidden';
                }
            }
        }

        // ========== CHAT FUNCTIONS ==========
        
        function openChat(supplier) {
            if (!appState.isAuthenticated || appState.currentUser.type === 'visitor') {
                showError('login-error-container', 'Please login to chat with suppliers.');
                openAuthModal();
                return;
            }
            
            appState.selectedSupplier = supplier;
            
            const chatModal = document.getElementById('chat-modal');
            const chatName = document.getElementById('chat-supplier-name');
            const chatStatus = document.getElementById('chat-supplier-status');
            
            if (chatModal) chatModal.classList.add('active');
            if (chatName) chatName.textContent = supplier.name;
            if (chatStatus) chatStatus.textContent = supplier.status;
            
            loadChatMessages();
        }
        
        function closeChat() {
            const chatModal = document.getElementById('chat-modal');
            if (chatModal) chatModal.classList.remove('active');
            document.body.style.overflow = 'auto';
        }
        
        function loadChatMessages() {
            const supplierId = appState.selectedSupplier ? appState.selectedSupplier.id : 'default';
            
            if (!appState.chatMessages[supplierId]) {
                const timestamp = new Date().toLocaleTimeString([], {hour: '2-digit', minute:'2-digit'});
                appState.chatMessages[supplierId] = [
                    {
                        id: 1,
                        sender: 'supplier',
                        text: `Hello! I'm from ${appState.selectedSupplier ? appState.selectedSupplier.name : 'our company'}. How can I help you?`,
                        time: timestamp
                    }
                ];
            }
            
            updateChatDisplay(supplierId);
        }
        
        function updateChatDisplay(supplierId) {
            const chatContainer = document.getElementById('chat-messages');
            if (!chatContainer) return;
            
            const messages = appState.chatMessages[supplierId] || [];
            
            chatContainer.innerHTML = messages.map(msg => `
                <div class="chat-message ${msg.sender === 'user' ? 'sent' : ''}">
                    <div class="bg-${msg.sender === 'user' ? 'blue' : 'slate'}-100 p-3 rounded-lg">
                        <p class="text-slate-800">${msg.text}</p>
                        <p class="text-xs text-slate-500 mt-1 text-right">${msg.time}</p>
                    </div>
                </div>
            `).join('');
            
            chatContainer.scrollTop = chatContainer.scrollHeight;
        }
        
        function sendChatMessage() {
            const input = document.getElementById('chat-input');
            if (!input) return;
            
            const message = input.value.trim();
            if (!message) return;
            
            const supplierId = appState.selectedSupplier ? appState.selectedSupplier.id : 'default';
            
            if (!appState.chatMessages[supplierId]) {
                appState.chatMessages[supplierId] = [];
            }
            
            const timestamp = new Date().toLocaleTimeString([], {hour: '2-digit', minute:'2-digit'});
            appState.chatMessages[supplierId].push({
                id: Date.now(),
                sender: 'user',
                text: message,
                time: timestamp
            });
            
            input.value = '';
            updateChatDisplay(supplierId);
            
            // Simulate supplier response
            setTimeout(() => {
                const responses = [
                    "Thank you for your message. We'll get back to you shortly.",
                    "Can you please share more details about your requirements?",
                    "I'll check availability and get back to you.",
                    "Would you like me to send you our catalog?"
                ];
                
                const response = responses[Math.floor(Math.random() * responses.length)];
                const responseTime = new Date().toLocaleTimeString([], {hour: '2-digit', minute:'2-digit'});
                
                appState.chatMessages[supplierId].push({
                    id: Date.now() + 1,
                    sender: 'supplier',
                    text: response,
                    time: responseTime
                });
                
                updateChatDisplay(supplierId);
            }, 2000);
        }

        // ========== SUPPLIER FUNCTIONS ==========
        
        function loadSuppliersForProduct(productKey) {
            const productSelect = document.getElementById('order-product');
            const productNameEl = document.getElementById('selected-product-name');
            
            if (productSelect && productNameEl) {
                const selectedOption = productSelect.options[productSelect.selectedIndex];
                const productName = selectedOption ? selectedOption.text : 'Product';
                productNameEl.textContent = productName;
            }
            
            const suppliers = supplierData[productKey] || [];
            const suppliersList = document.getElementById('suppliers-list');
            const noSuppliersMessage = document.getElementById('no-suppliers-message');
            
            if (!suppliersList || !noSuppliersMessage) return;
            
            if (suppliers.length === 0) {
                suppliersList.innerHTML = '';
                noSuppliersMessage.classList.remove('hidden');
                return;
            }
            
            noSuppliersMessage.classList.add('hidden');
            
            suppliersList.innerHTML = suppliers.map(supplier => {
                const escapedSupplier = JSON.stringify(supplier).replace(/"/g, '&quot;');
                return `
                <div class="supplier-card bg-white p-4 rounded-xl border-2 border-slate-200" onclick="selectSupplier('${productKey}', '${supplier.id}')">
                    <div class="flex items-start justify-between">
                        <div class="flex items-start gap-3">
                            <div class="w-12 h-12 bg-green-100 rounded-full flex items-center justify-center">
                                <i class="fas fa-user-tie text-green-600"></i>
                            </div>
                            <div>
                                <h4 class="font-bold text-slate-900">${supplier.name}</h4>
                                <p class="text-slate-600 text-sm">${supplier.company}</p>
                                <div class="flex items-center gap-2 mt-1">
                                    <div class="flex items-center">
                                        <i class="fas fa-star text-yellow-500 text-sm"></i>
                                        <span class="text-sm font-medium ml-1">${supplier.rating}</span>
                                        <span class="text-slate-500 text-xs ml-1">(${supplier.reviews})</span>
                                    </div>
                                    <span class="text-xs bg-green-100 text-green-700 px-2 py-0.5 rounded">${supplier.status}</span>
                                </div>
                            </div>
                        </div>
                        <button onclick="event.stopPropagation(); openChat(${escapedSupplier})" 
                                class="text-blue-600 hover:text-blue-800">
                            <i class="fas fa-comment-dots text-lg"></i>
                        </button>
                    </div>
                    <div class="mt-3 grid grid-cols-2 gap-2">
                        <div class="text-xs">
                            <span class="text-slate-500">Response:</span>
                            <span class="font-medium ml-1">${supplier.responseTime}</span>
                        </div>
                        <div class="text-xs">
                            <span class="text-slate-500">Min Order:</span>
                            <span class="font-medium ml-1">${supplier.minOrder}</span>
                        </div>
                        <div class="text-xs">
                            <span class="text-slate-500">Location:</span>
                            <span class="font-medium ml-1">${supplier.location}</span>
                        </div>
                        <div class="text-xs">
                            <span class="text-slate-500">Lead Time:</span>
                            <span class="font-medium ml-1">${supplier.leadTime}</span>
                        </div>
                    </div>
                    <div class="mt-3">
                        <div class="flex flex-wrap gap-1">
                            ${supplier.specialization.map(spec => `
                                <span class="text-xs bg-blue-100 text-blue-700 px-2 py-0.5 rounded">${spec}</span>
                            `).join('')}
                        </div>
                    </div>
                </div>
            `}).join('');
        }
        
        function selectSupplier(productKey, supplierId) {
            const suppliers = supplierData[productKey] || [];
            appState.selectedSupplier = suppliers.find(s => s.id === supplierId);
            
            document.querySelectorAll('.supplier-card').forEach(card => {
                card.classList.remove('selected');
            });
            
            const selectedCard = document.querySelector(`[onclick*="${supplierId}"]`);
            if (selectedCard) {
                selectedCard.classList.add('selected');
            }
            
            const displayEl = document.getElementById('selected-supplier-display');
            if (displayEl) {
                displayEl.textContent = appState.selectedSupplier ? 
                    `${appState.selectedSupplier.name} (${appState.selectedSupplier.company})` : 'Not selected';
            }
        }
        
        function showAllSuppliers() {
            showInfo('order-error-container', 'Showing all available suppliers for this product');
        }
        
        function showInfo(containerId, message) {
            const container = document.getElementById(containerId);
            if (container) {
                container.innerHTML = `
                    <i class="fas fa-info-circle"></i>
                    <span>${message}</span>
                `;
                container.classList.remove('hidden');
                container.className = 'info-message';
                
                setTimeout(() => {
                    container.classList.add('hidden');
                }, 3000);
            }
        }
        
        function updateProductSuppliers(productKey) {
            const suppliers = supplierData[productKey] || [];
            const suppliersList = document.getElementById('dynamic-suppliers-list');
            const productSuppliersList = document.getElementById('product-suppliers-list');
            
            if (!suppliersList || !productSuppliersList) return;
            
            if (suppliers.length === 0) {
                suppliersList.innerHTML = `
                    <div class="col-span-2 text-center py-8">
                        <i class="fas fa-users text-4xl text-slate-300 mb-3"></i>
                        <p class="text-slate-600">No suppliers available for this product</p>
                    </div>
                `;
                productSuppliersList.innerHTML = '<p class="text-slate-400">No suppliers available</p>';
                return;
            }
            
            suppliersList.innerHTML = suppliers.slice(0, 2).map(supplier => {
                const escapedSupplier = JSON.stringify(supplier).replace(/"/g, '&quot;');
                return `
                <div class="supplier-card bg-white p-4 rounded-xl border border-slate-200 hover:border-blue-300 transition">
                    <div class="flex items-start justify-between">
                        <div class="flex items-start gap-3">
                            <div class="w-10 h-10 bg-green-100 rounded-full flex items-center justify-center">
                                <i class="fas fa-user-tie text-green-600"></i>
                            </div>
                            <div>
                                <h5 class="font-bold text-slate-900">${supplier.name}</h5>
                                <p class="text-slate-600 text-sm">${supplier.company}</p>
                                <div class="flex items-center gap-2 mt-1">
                                    <div class="flex items-center">
                                        <i class="fas fa-star text-yellow-500 text-xs"></i>
                                        <span class="text-xs font-medium ml-1">${supplier.rating}</span>
                                    </div>
                                    <span class="text-xs bg-green-100 text-green-700 px-2 py-0.5 rounded">${supplier.status}</span>
                                </div>
                            </div>
                        </div>
                        <button onclick="openChat(${escapedSupplier})" 
                                class="text-blue-600 hover:text-blue-800">
                            <i class="fas fa-comment-dots"></i>
                        </button>
                    </div>
                    <div class="mt-3">
                        <div class="flex flex-wrap gap-1">
                            ${supplier.specialization.slice(0, 2).map(spec => `
                                <span class="text-xs bg-blue-100 text-blue-700 px-2 py-0.5 rounded">${spec}</span>
                            `).join('')}
                        </div>
                    </div>
                    <button onclick="checkAuthBeforeOrder('${productKey}')" 
                            class="w-full mt-3 py-2 bg-blue-600 text-white rounded-lg hover:bg-blue-700 transition text-sm font-medium">
                        <i class="fas fa-shopping-cart mr-2"></i>Order Now
                    </button>
                </div>
            `}).join('');
            
            productSuppliersList.innerHTML = suppliers.slice(0, 3).map(supplier => {
                const escapedSupplier = JSON.stringify(supplier).replace(/"/g, '&quot;');
                return `
                <div class="flex items-center justify-between py-2 border-b border-slate-700/50 last:border-0">
                    <div class="flex items-center gap-2">
                        <i class="fas fa-user-tie text-blue-400"></i>
                        <span>${supplier.name}</span>
                    </div>
                    <div class="flex items-center gap-2">
                        <span class="text-xs bg-green-900 text-green-300 px-2 py-0.5 rounded">${supplier.rating} ★</span>
                        <button onclick="openChat(${escapedSupplier})" 
                                class="text-blue-400 hover:text-blue-300">
                            <i class="fas fa-comment"></i>
                        </button>
                    </div>
                </div>
            `}).join('');
        }

        // ========== DASHBOARD FUNCTIONS ==========
        
        function openDashboard() {
            if (!appState.isAuthenticated || appState.currentUser.type === 'visitor') {
                showError('login-error-container', 'Please login to access the dashboard.');
                openAuthModal();
                return;
            }
            
            if (appState.currentUser.type !== 'supplier') {
                showError('login-error-container', 'Dashboard access is only available for supplier accounts.');
                return;
            }
            
            const dashboard = document.getElementById('dashboard-modal');
            if (dashboard) {
                dashboard.classList.remove('hidden');
                document.body.style.overflow = 'hidden';
                initDashboardCharts();
            }
        }
        
        function closeDashboard() {
            const dashboard = document.getElementById('dashboard-modal');
            if (dashboard) {
                dashboard.classList.add('hidden');
                document.body.style.overflow = 'auto';
                destroyDashboardCharts();
            }
        }
        
        function destroyDashboardCharts() {
            // Destroy chart instances to prevent memory leaks
            if (appState.charts.salesChart) {
                appState.charts.salesChart.destroy();
                delete appState.charts.salesChart;
            }
            if (appState.charts.categoryChart) {
                appState.charts.categoryChart.destroy();
                delete appState.charts.categoryChart;
            }
            if (appState.charts.performanceChart) {
                appState.charts.performanceChart.destroy();
                delete appState.charts.performanceChart;
            }
            if (appState.charts.conversionChart) {
                appState.charts.conversionChart.destroy();
                delete appState.charts.conversionChart;
            }
        }
        
        function switchDashboardTab(tabName) {
            // Update tab buttons
            document.querySelectorAll('#dashboard-modal .tab-button').forEach(btn => {
                const onclickAttr = btn.getAttribute('onclick');
                if (onclickAttr && onclickAttr.includes(tabName)) {
                    btn.classList.add('active');
                } else {
                    btn.classList.remove('active');
                }
            });
            
            // Update tab content
            document.querySelectorAll('#dashboard-modal .tab-content').forEach(content => {
                if (content.id === `dashboard-${tabName}`) {
                    content.classList.add('active');
                    content.classList.remove('hidden');
                } else {
                    content.classList.remove('active');
                    content.classList.add('hidden');
                }
            });
            
            if (tabName === 'analytics') {
                setTimeout(() => {
                    initAnalyticsCharts();
                }, 100);
            }
        }
        
        function showProfile() {
            if (!appState.isAuthenticated) {
                showError('login-error-container', 'Please login to view your profile.');
                openAuthModal();
                return;
            }
            showInfo('login-error-container', 'Profile page is under development.');
        }

        // ========== ORDER TRACKING FUNCTIONS ==========
        
        function openTrackingModal() {
            const modal = document.getElementById('tracking-modal');
            if (modal) {
                modal.classList.remove('hidden');
                document.body.style.overflow = 'hidden';
            }
        }
        
        function closeTrackingModal() {
            const modal = document.getElementById('tracking-modal');
            if (modal) {
                modal.classList.add('hidden');
                document.body.style.overflow = 'auto';
            }
        }
        
        function trackOrderWithCode() {
            const orderRef = document.getElementById('order-reference');
            if (orderRef) {
                const orderId = orderRef.textContent;
                closeOrderModal();
                setTimeout(() => {
                    openTrackingModal();
                    const input = document.getElementById('tracking-input');
                    if (input) input.value = orderId;
                    searchOrder();
                }, 500);
            }
        }
        
        function searchOrder() {
            const input = document.getElementById('tracking-input');
            if (!input) return;
            
            const orderId = input.value.trim();
            if (!orderId) {
                showError('tracking-modal .error-message', 'Please enter an order ID');
                return;
            }
            
            const emptyEl = document.getElementById('tracking-empty');
            const resultsEl = document.getElementById('tracking-results');
            const ordersEl = document.getElementById('my-orders-section');
            const loadingEl = document.getElementById('tracking-loading');
            
            if (emptyEl) emptyEl.classList.add('hidden');
            if (resultsEl) resultsEl.classList.add('hidden');
            if (ordersEl) ordersEl.classList.add('hidden');
            if (loadingEl) loadingEl.classList.remove('hidden');
            
            // Simulate API call
            setTimeout(() => {
                if (loadingEl) loadingEl.classList.add('hidden');
                if (resultsEl) resultsEl.classList.remove('hidden');
                
                // Populate tracking timeline
                const timelineEl = document.getElementById('tracking-timeline');
                if (timelineEl) {
                    timelineEl.innerHTML = `
                        <div class="tracking-step completed">
                            <div class="tracking-step-icon completed">
                                <i class="fas fa-check"></i>
                            </div>
                            <div class="tracking-step-content">
                                <p class="text-sm text-slate-500">Mar 15, 2024 - 09:30 AM</p>
                                <h5 class="font-bold text-slate-900 mb-1">Order Received</h5>
                                <p class="text-slate-600">Your order has been received by the supplier.</p>
                            </div>
                        </div>
                        <div class="tracking-step current">
                            <div class="tracking-step-icon current">
                                <i class="fas fa-sync-alt"></i>
                            </div>
                            <div class="tracking-step-content">
                                <p class="text-sm text-slate-500">Mar 16, 2024 - 11:00 AM</p>
                                <h5 class="font-bold text-slate-900 mb-1">Processing</h5>
                                <p class="text-slate-600">Your order is being processed and verified.</p>
                            </div>
                        </div>
                        <div class="tracking-step pending">
                            <div class="tracking-step-icon pending">
                                <i class="fas fa-cogs"></i>
                            </div>
                            <div class="tracking-step-content">
                                <p class="text-sm text-slate-500">Estimated: Mar 18-20</p>
                                <h5 class="font-bold text-slate-900 mb-1">Manufacturing</h5>
                                <p class="text-slate-600">Components are being manufactured.</p>
                            </div>
                        </div>
                        <div class="tracking-step pending">
                            <div class="tracking-step-icon pending">
                                <i class="fas fa-truck"></i>
                            </div>
                            <div class="tracking-step-content">
                                <p class="text-sm text-slate-500">Estimated: Mar 23-25</p>
                                <h5 class="font-bold text-slate-900 mb-1">Shipping</h5>
                                <p class="text-slate-600">Order will be shipped soon.</p>
                            </div>
                        </div>
                    `;
                }
            }, 1000);
        }
        
        function showMyOrders() {
            if (!appState.isAuthenticated || appState.currentUser.type === 'visitor') {
                showError('tracking-modal .error-message', 'Please login to view your orders.');
                openAuthModal();
                return;
            }
            
            const resultsEl = document.getElementById('tracking-results');
            const emptyEl = document.getElementById('tracking-empty');
            const loadingEl = document.getElementById('tracking-loading');
            const ordersEl = document.getElementById('my-orders-section');
            
            if (resultsEl) resultsEl.classList.add('hidden');
            if (emptyEl) emptyEl.classList.add('hidden');
            if (loadingEl) loadingEl.classList.remove('hidden');
            if (ordersEl) ordersEl.classList.remove('hidden');
            
            setTimeout(() => {
                if (loadingEl) loadingEl.classList.add('hidden');
                
                const ordersList = document.getElementById('my-orders-list');
                if (ordersList) {
                    ordersList.innerHTML = `
                        <div class="bg-white p-4 rounded-xl border border-slate-200">
                            <div class="flex justify-between items-start">
                                <div>
                                    <div class="flex items-center gap-3">
                                        <h4 class="font-bold text-slate-900">#ORD-7842</h4>
                                        <span class="badge badge-warning">Processing</span>
                                    </div>
                                    <p class="text-sm text-slate-600 mt-1">Long Weld Neck Flange - 50 pieces</p>
                                    <p class="text-xs text-slate-500 mt-1">Ordered: Mar 15, 2024</p>
                                </div>
                                <div class="text-right">
                                    <p class="font-bold">₹245,000</p>
                                    <button onclick="trackOrder('ORD-7842')" class="text-sm text-blue-600 hover:text-blue-800">Track</button>
                                </div>
                            </div>
                        </div>
                        <div class="bg-white p-4 rounded-xl border border-slate-200">
                            <div class="flex justify-between items-start">
                                <div>
                                    <div class="flex items-center gap-3">
                                        <h4 class="font-bold text-slate-900">#ORD-7841</h4>
                                        <span class="badge badge-success">Shipped</span>
                                    </div>
                                    <p class="text-sm text-slate-600 mt-1">Weld Neck Flange - 25 pieces</p>
                                    <p class="text-xs text-slate-500 mt-1">Ordered: Mar 14, 2024</p>
                                </div>
                                <div class="text-right">
                                    <p class="font-bold">₹187,500</p>
                                    <button onclick="trackOrder('ORD-7841')" class="text-sm text-blue-600 hover:text-blue-800">Track</button>
                                </div>
                            </div>
                        </div>
                        <div class="bg-white p-4 rounded-xl border border-slate-200">
                            <div class="flex justify-between items-start">
                                <div>
                                    <div class="flex items-center gap-3">
                                        <h4 class="font-bold text-slate-900">#ORD-7840</h4>
                                        <span class="badge badge-danger">Pending</span>
                                    </div>
                                    <p class="text-sm text-slate-600 mt-1">Blind Flange - 100 pieces</p>
                                    <p class="text-xs text-slate-500 mt-1">Ordered: Mar 13, 2024</p>
                                </div>
                                <div class="text-right">
                                    <p class="font-bold">₹92,300</p>
                                    <button onclick="trackOrder('ORD-7840')" class="text-sm text-blue-600 hover:text-blue-800">Track</button>
                                </div>
                            </div>
                        </div>
                    `;
                }
            }, 800);
        }
        
        function trackOrder(orderId) {
            const input = document.getElementById('tracking-input');
            if (input) {
                input.value = orderId;
                searchOrder();
            }
        }
        
        function downloadInvoice() {
            showInfo('tracking-modal .error-message', 'Invoice download feature is under development.');
        }
        
        function contactSupplier() {
            showInfo('tracking-modal .error-message', 'Contacting supplier... This would open your email client.');
        }

        // ========== ORDER FUNCTIONS ==========
        
        function checkAuthBeforeOrder(productKey = null) {
            resetSessionTimer(); // Reset timer on user action
            
            if (!appState.isAuthenticated || appState.currentUser.type === 'visitor') {
                showError('login-error-container', 'Please login or create an account to connect with suppliers.');
                openAuthModal();
                return;
            }
            
            if (productKey) {
                openOrderModalWithProduct(productKey);
            } else {
                openOrderModal();
            }
        }

        function openOrderModal() {
            if (!appState.isAuthenticated || appState.currentUser.type === 'visitor') {
                checkAuthBeforeOrder();
                return;
            }
            
            const modal = document.getElementById('order-modal');
            if (modal) {
                modal.classList.remove('hidden');
                document.body.style.overflow = 'hidden';
                resetOrderSteps();
            }
        }
        
        function openOrderModalWithProduct(productKey) {
            if (!appState.isAuthenticated || appState.currentUser.type === 'visitor') {
                checkAuthBeforeOrder(productKey);
                return;
            }
            
            openOrderModal();
            const productSelect = document.getElementById('order-product');
            if (productSelect) {
                productSelect.value = productKey;
                loadSuppliersForProduct(productKey);
            }
        }
        
        function closeOrderModal() {
            const modal = document.getElementById('order-modal');
            if (modal) {
                modal.classList.add('hidden');
                document.body.style.overflow = 'auto';
            }
            appState.selectedSupplier = null;
        }

        function resetOrderSteps() {
            appState.currentOrderStep = 1;
            updateStepIndicators();
            
            for (let i = 1; i <= 5; i++) {
                const stepEl = document.getElementById(`order-step-${i}`);
                if (stepEl) stepEl.classList.add('hidden');
            }
            
            const step1 = document.getElementById('order-step-1');
            if (step1) step1.classList.remove('hidden');
            
            appState.selectedSupplier = null;
            const displayEl = document.getElementById('selected-supplier-display');
            if (displayEl) displayEl.textContent = 'Not selected';
            
            clearValidationErrors();
        }

        function updateStepIndicators() {
            const progress = document.getElementById('step-progress');
            if (progress) {
                const stepWidth = 100 / 4;
                progress.style.width = `${(appState.currentOrderStep - 1) * stepWidth}%`;
            }
            
            for (let i = 1; i <= 4; i++) {
                const indicator = document.getElementById(`step-indicator-${i}`);
                if (indicator) {
                    if (i < appState.currentOrderStep) {
                        indicator.classList.remove('pending', 'active');
                        indicator.classList.add('completed');
                    } else if (i === appState.currentOrderStep) {
                        indicator.classList.remove('pending', 'completed');
                        indicator.classList.add('active');
                    } else {
                        indicator.classList.remove('active', 'completed');
                        indicator.classList.add('pending');
                    }
                }
            }
        }

        function validateStep1() {
            let isValid = true;
            clearValidationErrors();
            
            const product = document.getElementById('order-product').value;
            const quantity = document.getElementById('order-quantity').value;
            const size = document.getElementById('order-size').value;
            const material = document.getElementById('order-material').value;
            
            if (!validateRequired(product)) {
                showFieldError('order-product', 'Please select a product');
                isValid = false;
            }
            
            if (!validateRequired(quantity) || quantity < 1) {
                showFieldError('order-quantity', 'Please enter a valid quantity (minimum 1)');
                isValid = false;
            }
            
            if (!validateRequired(size)) {
                showFieldError('order-size', 'Please enter size/dimensions');
                isValid = false;
            }
            
            if (!validateRequired(material)) {
                showFieldError('order-material', 'Please select a material');
                isValid = false;
            }
            
            return isValid;
        }

        function validateStep2() {
            if (!appState.selectedSupplier) {
                showError('order-error-container', 'Please select a supplier before proceeding.');
                return false;
            }
            return true;
        }

        function validateStep3() {
            let isValid = true;
            clearValidationErrors();
            
            const firstName = document.getElementById('order-firstname').value;
            const lastName = document.getElementById('order-lastname').value;
            const email = document.getElementById('order-email').value;
            const phone = document.getElementById('order-phone').value;
            const company = document.getElementById('order-company').value;
            
            if (!validateRequired(firstName)) {
                showFieldError('order-firstname', 'First name is required');
                isValid = false;
            }
            
            if (!validateRequired(lastName)) {
                showFieldError('order-lastname', 'Last name is required');
                isValid = false;
            }
            
            if (!validateEmail(email)) {
                showFieldError('order-email', 'Please enter a valid email address');
                isValid = false;
            }
            
            if (!validatePhone(phone)) {
                showFieldError('order-phone', 'Please enter a valid phone number');
                isValid = false;
            }
            
            if (!validateRequired(company)) {
                showFieldError('order-company', 'Company name is required');
                isValid = false;
            }
            
            return isValid;
        }

        function validateAndNextStep(currentStep, nextStep) {
            let isValid = false;
            
            switch(currentStep) {
                case 1:
                    isValid = validateStep1();
                    break;
                case 2:
                    isValid = validateStep2();
                    break;
                case 3:
                    isValid = validateStep3();
                    break;
                default:
                    isValid = true;
            }
            
            if (isValid) {
                nextOrderStep(nextStep);
            }
        }

        function nextOrderStep(step) {
            if (step < 1 || step > 5) return;
            
            if (step === 4) {
                updateReviewSection();
            }
            
            const currentStep = document.getElementById(`order-step-${appState.currentOrderStep}`);
            if (currentStep) currentStep.classList.add('hidden');
            
            appState.currentOrderStep = step;
            const nextStep = document.getElementById(`order-step-${step}`);
            if (nextStep) nextStep.classList.remove('hidden');
            
            updateStepIndicators();
        }

        function prevOrderStep(step) {
            nextOrderStep(step);
        }

        function updateReviewSection() {
            const productSelect = document.getElementById('order-product');
            const productText = productSelect ? (productSelect.options[productSelect.selectedIndex]?.text || '-') : '-';
            const quantity = document.getElementById('order-quantity')?.value || '0';
            const materialSelect = document.getElementById('order-material');
            const materialText = materialSelect ? (materialSelect.options[materialSelect.selectedIndex]?.text || '-') : '-';
            const contactMethod = document.querySelector('input[name="contactMethod"]:checked')?.value || 'email';
            
            const reviewProduct = document.getElementById('review-product');
            const reviewSupplier = document.getElementById('review-supplier');
            const reviewQuantity = document.getElementById('review-quantity');
            const reviewMaterial = document.getElementById('review-material');
            const reviewContact = document.getElementById('review-contact');
            const confirmationSupplier = document.getElementById('confirmation-supplier');
            
            if (reviewProduct) reviewProduct.textContent = productText;
            if (reviewSupplier) reviewSupplier.textContent = appState.selectedSupplier ? 
                `${appState.selectedSupplier.name} (${appState.selectedSupplier.company})` : 'Not selected';
            if (reviewQuantity) reviewQuantity.textContent = `${quantity} pieces`;
            if (reviewMaterial) reviewMaterial.textContent = materialText;
            if (reviewContact) reviewContact.textContent = contactMethod.charAt(0).toUpperCase() + contactMethod.slice(1);
            if (confirmationSupplier) confirmationSupplier.textContent = appState.selectedSupplier ? appState.selectedSupplier.name : 'Supplier';
        }

        function submitOrder() {
            if (!appState.selectedSupplier) {
                showError('order-error-container', 'Please select a supplier before submitting the order.');
                return;
            }
            
            const orderRef = document.getElementById('order-reference');
            if (orderRef) {
                const orderId = 'UF-ORD-' + Math.floor(100000 + Math.random() * 900000);
                orderRef.textContent = orderId;
                
                // Save to user orders
                if (!appState.userOrders) appState.userOrders = [];
                appState.userOrders.push({
                    id: orderId,
                    date: new Date().toISOString(),
                    supplier: appState.selectedSupplier,
                    product: document.getElementById('order-product').options[document.getElementById('order-product').selectedIndex]?.text,
                    quantity: document.getElementById('order-quantity').value,
                    status: 'Submitted'
                });
            }
            
            nextOrderStep(5);
            showSuccess('order-error-container', `Order submitted to ${appState.selectedSupplier.name}! They will contact you shortly.`);
        }

        // ========== PRODUCT FUNCTIONS ==========
        
        function updateProduct(key) {
            appState.currentProductKey = key;
            const data = productData[key] || productData.lwn;
            
            document.querySelectorAll('.flange-chip').forEach(c => c.classList.remove('active'));
            const activeChip = document.getElementById(`chip-${key}`);
            if (activeChip) activeChip.classList.add('active');
            
            const currentProductEl = document.getElementById('current-product-name');
            const pTitle = document.getElementById('p-title');
            const pDesc = document.getElementById('p-desc');
            
            if (currentProductEl) currentProductEl.textContent = data.title;
            if (pTitle) pTitle.innerText = data.title;
            if (pDesc) pDesc.innerText = data.desc;
            
            const featuresContainer = document.getElementById('p-features');
            if (featuresContainer) {
                featuresContainer.innerHTML = data.features.map((f, i) => `
                    <div class="feature-card p-4 md:p-5 rounded-2xl opacity-100 reveal stagger-delay-${i % 4}">
                        <div class="flex items-start gap-3 md:gap-4">
                            <div class="mt-1 w-7 h-7 md:w-8 md:h-8 bg-blue-600 rounded-lg flex items-center justify-center flex-shrink-0">
                                <i class="fas fa-check text-white text-xs md:text-sm"></i>
                            </div>
                            <span class="text-slate-700 font-semibold text-sm md:text-base">${f}</span>
                        </div>
                    </div>
                `).join('');
            }

            const specTitle = document.getElementById('spec-title');
            if (specTitle) specTitle.innerText = `${data.title} - Technical Specifications`;
            
            renderSpecTables(data.specs);
            updateProductSuppliers(key);
            
            const productCard = document.getElementById('product-card');
            if (productCard) {
                productCard.style.opacity = '0';
                productCard.style.transform = 'translateY(20px)';
                setTimeout(() => {
                    productCard.style.opacity = '1';
                    productCard.style.transform = 'translateY(0)';
                    const productsSection = document.getElementById('products');
                    if (productsSection) productsSection.scrollIntoView({ behavior: 'smooth' });
                }, 50);
            }
        }

        function renderSpecTables(specs) {
            const container = document.getElementById('spec-tables-container');
            if (!container) return;
            container.innerHTML = ''; 

            const categories = [
                { id: 'general', label: 'Attribute', valueLabel: 'Detail / Capability', icon: 'fas fa-ruler-combined' },
                { id: 'materials', label: 'Material Grade', valueLabel: 'ASTM / ASME / EN Specifications', icon: 'fas fa-weight' }
            ];

            categories.forEach(cat => {
                const tableData = specs[cat.id];
                if (!tableData) return;

                const tableHTML = `
                    <div class="overflow-hidden rounded-2xl border border-slate-800 bg-slate-900/50">
                        <div class="bg-slate-800/70 px-4 md:px-6 py-3 md:py-4 border-b border-slate-700 flex items-center gap-3">
                            <i class="${cat.icon} text-blue-400"></i>
                            <h3 class="font-bold text-base md:text-lg">${cat.id === 'general' ? 'General Specifications' : 'Material Grades'}</h3>
                        </div>
                        <div class="overflow-x-auto">
                            <table class="w-full spec-table">
                                <thead class="bg-slate-800/40 text-blue-300 text-xs uppercase tracking-widest font-bold">
                                    <tr>
                                        <th class="px-4 md:px-6 py-2 md:py-4 text-left">${cat.label}</th>
                                        <th class="px-4 md:px-6 py-2 md:py-4 text-left">${cat.valueLabel}</th>
                                    </tr>
                                </thead>
                                <tbody class="divide-y divide-slate-800 text-xs md:text-sm">
                                    ${Object.entries(tableData).map(([attr, detail], index) => `
                                        <tr class="${index % 2 === 0 ? 'bg-slate-900/20' : ''}">
                                            <td class="px-4 md:px-6 py-2 md:py-4 font-semibold text-slate-300">${attr}</td>
                                            <td class="px-4 md:px-6 py-2 md:py-4 text-slate-400">${detail}</td>
                                        </tr>
                                    `).join('')}
                                </tbody>
                            </table>
                        </div>
                    </div>
                `;
                container.innerHTML += tableHTML;
            });
        }

        function downloadProductFiles() {
            const currentProduct = getCurrentProduct();
            showInfo('login-error-container', `Preparing ${currentProduct.title} technical files for download...`);
        }

        function showAllProducts() {
            const gallery = document.getElementById('product-gallery');
            if (gallery) gallery.scrollIntoView({ behavior: 'smooth' });
        }

        function handleSearch(query) {
            const term = query.toLowerCase().trim();
            if (term.length < 2) return;
            
            for (const [key, data] of Object.entries(productData)) {
                if (data.title.toLowerCase().includes(term) || 
                    key.includes(term) || 
                    data.desc.toLowerCase().includes(term)) {
                    updateProduct(key);
                    break;
                }
            }
        }

        function getCurrentProduct() {
            return productData[appState.currentProductKey] || productData.lwn;
        }

        // ========== IMAGE HANDLING ==========
        
        function handleImageError(img, fallbackText) {
            img.style.display = 'none';
            const parent = img.parentNode;
            
            if (parent && !parent.querySelector('.img-fallback')) {
                parent.classList.add('img-fallback');
                
                const icon = document.createElement('i');
                icon.className = 'fas fa-industry';
                parent.appendChild(icon);
                
                if (fallbackText && !parent.classList.contains('product-image-container')) {
                    const text = document.createElement('span');
                    text.className = 'text-sm mt-2 block';
                    text.textContent = fallbackText;
                    parent.appendChild(text);
                }
            }
        }

        function initImageErrorHandlers() {
            const images = document.querySelectorAll('img');
            images.forEach(img => {
                img.addEventListener('error', function() {
                    handleImageError(this);
                });
                
                // Also check if src is empty or invalid
                if (!img.src || img.src === '' || img.src.includes('undefined')) {
                    handleImageError(img);
                }
            });
        }

        // ========== REVEAL ANIMATIONS ==========
        
        function initReveal() {
            const reveals = document.querySelectorAll('.reveal');
            const observer = new IntersectionObserver((entries) => {
                entries.forEach(entry => {
                    if (entry.isIntersecting) {
                        entry.target.classList.add('active');
                    }
                });
            }, { threshold: 0.1 });
            
            reveals.forEach(r => observer.observe(r));
        }

        // ========== CHART FUNCTIONS ==========
        
        function initDashboardCharts() {
            destroyDashboardCharts(); // Clean up existing charts
            
            const salesCtx = document.getElementById('salesChart')?.getContext('2d');
            if (salesCtx) {
                appState.charts.salesChart = new Chart(salesCtx, {
                    type: 'line',
                    data: {
                        labels: ['Jan', 'Feb', 'Mar', 'Apr', 'May', 'Jun'],
                        datasets: [{
                            label: 'Revenue (₹)',
                            data: [1200000, 1850000, 1500000, 2200000, 2450000, 2847500],
                            borderColor: '#3b82f6',
                            backgroundColor: 'rgba(59, 130, 246, 0.1)',
                            borderWidth: 2,
                            fill: true,
                            tension: 0.4
                        }]
                    },
                    options: {
                        responsive: true,
                        maintainAspectRatio: false,
                        plugins: { legend: { display: false } },
                        scales: {
                            y: {
                                beginAtZero: true,
                                ticks: {
                                    callback: function(value) {
                                        return '₹' + (value / 1000000).toFixed(1) + 'M';
                                    }
                                }
                            }
                        }
                    }
                });
            }
        }
        
        function initAnalyticsCharts() {
            destroyDashboardCharts(); // Clean up existing charts
            
            const categoryCtx = document.getElementById('categoryChart')?.getContext('2d');
            if (categoryCtx) {
                appState.charts.categoryChart = new Chart(categoryCtx, {
                    type: 'doughnut',
                    data: {
                        labels: ['Weld Neck', 'Long Weld Neck', 'Blind Flange', 'Plasma CNC', 'Others'],
                        datasets: [{
                            data: [42, 30, 12, 8, 8],
                            backgroundColor: ['#3b82f6', '#10b981', '#f59e0b', '#8b5cf6', '#64748b']
                        }]
                    },
                    options: {
                        responsive: true,
                        maintainAspectRatio: false,
                        plugins: { legend: { position: 'bottom' } }
                    }
                });
            }
            
            const performanceCtx = document.getElementById('performanceChart')?.getContext('2d');
            if (performanceCtx) {
                appState.charts.performanceChart = new Chart(performanceCtx, {
                    type: 'bar',
                    data: {
                        labels: ['Jan', 'Feb', 'Mar', 'Apr', 'May', 'Jun'],
                        datasets: [
                            {
                                label: 'Orders',
                                data: [32, 45, 38, 52, 47, 56],
                                backgroundColor: '#3b82f6'
                            },
                            {
                                label: 'Revenue (₹L)',
                                data: [120, 185, 150, 220, 245, 284],
                                backgroundColor: '#10b981'
                            }
                        ]
                    },
                    options: {
                        responsive: true,
                        maintainAspectRatio: false,
                        scales: { y: { beginAtZero: true } }
                    }
                });
            }
            
            const conversionCtx = document.getElementById('conversionChart')?.getContext('2d');
            if (conversionCtx) {
                appState.charts.conversionChart = new Chart(conversionCtx, {
                    type: 'doughnut',
                    data: {
                        labels: ['Converted', 'Not Converted'],
                        datasets: [{
                            data: [68, 32],
                            backgroundColor: ['#3b82f6', '#e2e8f0']
                        }]
                    },
                    options: {
                        responsive: true,
                        maintainAspectRatio: false,
                        cutout: '70%',
                        plugins: { legend: { display: false } }
                    }
                });
            }
        }

        // ========== EVENT LISTENERS ==========
        
        function setupEventListeners() {
            // Escape key handler
            document.addEventListener('keydown', (e) => {
                if (e.key === 'Escape') {
                    const orderModal = document.getElementById('order-modal');
                    const dashboardModal = document.getElementById('dashboard-modal');
                    const authOverlay = document.getElementById('auth-overlay');
                    const trackingModal = document.getElementById('tracking-modal');
                    const chatModal = document.getElementById('chat-modal');
                    const mobileMenu = document.getElementById('mobile-menu');
                    
                    if (orderModal && !orderModal.classList.contains('hidden')) closeOrderModal();
                    if (dashboardModal && !dashboardModal.classList.contains('hidden')) closeDashboard();
                    if (authOverlay && authOverlay.style.display === 'flex') closeAuth();
                    if (trackingModal && !trackingModal.classList.contains('hidden')) closeTrackingModal();
                    if (chatModal && chatModal.classList.contains('active')) closeChat();
                    if (mobileMenu && mobileMenu.classList.contains('active')) toggleMobileMenu();
                }
            });

            // Click outside to close modals
            document.addEventListener('click', (e) => {
                const authOverlay = document.getElementById('auth-overlay');
                const dashboardModal = document.getElementById('dashboard-modal');
                const trackingModal = document.getElementById('tracking-modal');
                const orderModal = document.getElementById('order-modal');
                
                if (authOverlay && e.target === authOverlay) {
                    closeAuth();
                }
                
                if (dashboardModal && e.target === dashboardModal) {
                    closeDashboard();
                }
                
                if (trackingModal && e.target === trackingModal) {
                    closeTrackingModal();
                }
                
                if (orderModal && e.target === orderModal) {
                    closeOrderModal();
                }
            });

            // Product select change
            const productSelect = document.getElementById('order-product');
            if (productSelect) {
                productSelect.addEventListener('change', function() {
                    const selectedValue = this.value;
                    if (selectedValue && selectedValue !== 'custom') {
                        loadSuppliersForProduct(selectedValue);
                    }
                });
            }

            // Chat input enter key
            const chatInput = document.getElementById('chat-input');
            if (chatInput) {
                chatInput.addEventListener('keypress', function(e) {
                    if (e.key === 'Enter') {
                        sendChatMessage();
                    }
                });
            }

            // Activity listeners for session timeout
            ['click', 'mousemove', 'keypress', 'scroll'].forEach(event => {
                document.addEventListener(event, resetSessionTimer);
            });
        }

        // ========== INITIALIZATION ==========
        
        document.addEventListener('DOMContentLoaded', function() {
            // Initialize auth state
            initializeAuth();
            
            // Set default user type
            setUserType('partner');
            
            // Update product to default
            updateProduct('lwn');
            
            // Initialize reveal animations
            initReveal();
            
            // Setup image error handlers
            initImageErrorHandlers();
            
            // Setup event listeners
            setupEventListeners();
            
            // Prefill order form if user is logged in
            if (appState.isAuthenticated && appState.currentUser) {
                const orderEmail = document.getElementById('order-email');
                const orderCompany = document.getElementById('order-company');
                
                if (orderEmail && appState.currentUser.email) {
                    orderEmail.value = appState.currentUser.email;
                }
                
                if (orderCompany && appState.currentUser.company) {
                    orderCompany.value = appState.currentUser.company;
                }
            }
        });

        // Cleanup on page unload
        window.addEventListener('beforeunload', function() {
            destroyDashboardCharts();
            if (sessionTimeoutId) {
                clearTimeout(sessionTimeoutId);
            }
        });

    </script>
</body>
</html>

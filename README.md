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
        
        /* Dashboard Styles */
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
        
        /* Enhanced Animations */
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
        
        /* Auth Overlay */
        #auth-overlay {
            z-index: 9999;
        }
        
        /* Loading Animation */
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
        
        /* Enhanced Chip Styles */
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
        
        /* Enhanced Cards */
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
        
        /* Hero Image Container */
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
        
        /* Enhanced Search */
        .search-container {
            transition: all 0.3s ease;
        }
        
        .search-container:focus-within {
            box-shadow: 0 0 0 3px rgba(37, 99, 235, 0.15);
            border-color: var(--secondary-blue);
        }
        
        /* Hidden content until login */
        #main-content {
            filter: blur(8px);
            pointer-events: none;
            transition: filter 0.5s ease;
        }
        
        body.authenticated #main-content {
            filter: blur(0);
            pointer-events: auto;
        }
        
        /* Enhanced Table */
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
        
        /* Contact Form */
        .contact-form input:focus,
        .contact-form textarea:focus,
        .contact-form select:focus {
            box-shadow: 0 0 0 3px rgba(37, 99, 235, 0.15);
            border-color: var(--secondary-blue);
        }
        
        /* Stats Counter */
        .stat-card {
            background: white;
            border-radius: 16px;
            padding: 2rem;
            box-shadow: 0 10px 30px rgba(0, 0, 0, 0.05);
            transition: transform 0.3s ease;
        }
        
        .stat-card:hover {
            transform: translateY(-5px);
        }
        
        /* Mobile Menu */
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
        
        /* Order Modal Styles */
        #order-modal .hidden {
            display: none !important;
        }
        
        /* Enhanced Step indicators */
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
        
        /* Order step animations */
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
        
        /* Shimmer effect for loading */
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
        
        /* Enhanced form inputs */
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
        
        /* Enhanced buttons */
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
        
        /* Product Thumbnails */
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
        
        /* Product Image Container */
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
        
        /* Gallery Product Cards */
        .gallery-product-card {
            height: 100%;
            transition: all 0.3s ease;
        }
        
        .gallery-product-card:hover {
            transform: translateY(-8px);
            box-shadow: 0 20px 40px rgba(0, 0, 0, 0.1);
        }
        
        /* Tabs */
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
        
        /* Order Tracking Styles */
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
        
        /* Supplier Chat Modal */
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
        
        /* Supplier Section */
        .supplier-section {
            background: linear-gradient(135deg, #f8fafc 0%, #f1f5f9 100%);
            border-radius: 1rem;
            padding: 1.5rem;
            margin-bottom: 1.5rem;
        }
        
        /* Fix for Auth Modal on Mobile */
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
        }
        
        /* Fix for textarea responsiveness */
        textarea {
            min-height: 100px;
            resize: vertical;
        }
        
        /* Ensure hero section is at top on load */
        html, body {
            scroll-padding-top: 80px;
        }
        
        /* Hide order button for visitors */
        body.visitor-mode .order-button {
            display: none;
        }
        
        /* Supplier Badge */
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
    </style>
</head>
<body class="bg-slate-50 text-slate-900">

    <div id="transition-loader" class="loading-shimmer"></div>

    <!-- Login/Signup Modal Overlay (UPDATED: added password field to signup) -->
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
                <form class="space-y-4 md:space-y-5" onsubmit="handleAuth(event, 'partner')">
                    <div>
                        <label class="block text-sm font-semibold text-slate-700 mb-2">Email Address</label>
                        <input type="email" id="login-email" required placeholder="name@company.com" 
                               class="w-full px-4 md:px-5 py-3 rounded-xl border-2 border-slate-200 focus:ring-2 focus:ring-blue-500 outline-none transition text-sm md:text-base">
                    </div>
                    <div>
                        <label class="block text-sm font-semibold text-slate-700 mb-2">Password</label>
                        <input type="password" id="login-password" required placeholder="••••••••" 
                               class="w-full px-4 md:px-5 py-3 rounded-xl border-2 border-slate-200 focus:ring-2 focus:ring-blue-500 outline-none transition text-sm md:text-base">
                    </div>
                    <div class="flex items-center justify-between">
                        <label class="flex items-center">
                            <input type="checkbox" class="rounded border-slate-300 text-blue-600 focus:ring-blue-500">
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

                    <button type="button" onclick="handleAuth(event, 'visitor')" 
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

            <!-- SIGNUP FORM WITH PASSWORD FIELD (updated) -->
            <div id="signup-form" class="hidden">
                <div class="text-center mb-6 md:mb-8">
                    <h2 class="text-2xl md:text-3xl font-bold text-slate-900">Create Partner Account</h2>
                    <p class="text-slate-500 mt-2 text-sm md:text-base">Join our industrial network for exclusive access</p>
                </div>
                <form class="space-y-4 md:space-y-5" onsubmit="handleAuth(event, 'partner')">
                    <div class="grid grid-cols-2 gap-3 md:gap-4">
                        <div>
                            <label class="block text-sm font-semibold text-slate-700 mb-2">First Name</label>
                            <input type="text" required 
                                   class="w-full px-3 md:px-4 py-2.5 md:py-3 rounded-xl border-2 border-slate-200 focus:ring-2 focus:ring-blue-500 outline-none transition text-sm md:text-base">
                        </div>
                        <div>
                            <label class="block text-sm font-semibold text-slate-700 mb-2">Last Name</label>
                            <input type="text" required 
                                   class="w-full px-3 md:px-4 py-2.5 md:py-3 rounded-xl border-2 border-slate-200 focus:ring-2 focus:ring-blue-500 outline-none transition text-sm md:text-base">
                        </div>
                    </div>
                    <div>
                        <label class="block text-sm font-semibold text-slate-700 mb-2">Email</label>
                        <input type="email" required 
                               class="w-full px-3 md:px-4 py-2.5 md:py-3 rounded-xl border-2 border-slate-200 focus:ring-2 focus:ring-blue-500 outline-none transition text-sm md:text-base">
                    </div>
                    <!-- PASSWORD FIELD ADDED HERE -->
                    <div>
                        <label class="block text-sm font-semibold text-slate-700 mb-2">Password</label>
                        <input type="password" id="signup-password" required placeholder="Create a password" 
                               class="w-full px-3 md:px-4 py-2.5 md:py-3 rounded-xl border-2 border-slate-200 focus:ring-2 focus:ring-blue-500 outline-none transition text-sm md:text-base">
                    </div>
                    <div>
                        <label class="block text-sm font-semibold text-slate-700 mb-2">Company</label>
                        <input type="text" required 
                               class="w-full px-3 md:px-4 py-2.5 md:py-3 rounded-xl border-2 border-slate-200 focus:ring-2 focus:ring-blue-500 outline-none transition text-sm md:text-base">
                    </div>
                    <div>
                        <label class="block text-sm font-semibold text-slate-700 mb-2">Industry</label>
                        <select class="w-full px-3 md:px-4 py-2.5 md:py-3 rounded-xl border-2 border-slate-200 focus:ring-2 focus:ring-blue-500 outline-none transition text-sm md:text-base">
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

    <!-- Order Process Modal (unchanged) -->
    <div id="order-modal" class="fixed inset-0 bg-black/60 backdrop-blur-md hidden items-center justify-center p-4 z-50">
        <div class="bg-white w-full max-w-2xl rounded-3xl shadow-2xl overflow-hidden relative" style="max-height: 90vh; overflow-y: auto;">
            <button onclick="closeOrderModal()" class="absolute top-4 right-4 text-slate-400 hover:text-slate-700 z-10">
                <i class="fas fa-times text-2xl"></i>
            </button>
            
            <!-- Enhanced Step Indicators -->
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
                    </div>
                    
                    <div class="grid md:grid-cols-2 gap-4 md:gap-5">
                        <div class="transform transition-all duration-300 hover:scale-[1.02]">
                            <label class="block text-sm font-semibold text-slate-700 mb-2">Quantity *</label>
                            <input type="number" min="1" value="1" id="order-quantity" class="w-full px-4 md:px-5 py-3 md:py-3.5 rounded-xl form-input-enhanced focus:ring-2 focus:ring-blue-500 outline-none transition-all text-sm md:text-base">
                        </div>
                        <div class="transform transition-all duration-300 hover:scale-[1.02]">
                            <label class="block text-sm font-semibold text-slate-700 mb-2">Size / Dimensions *</label>
                            <input type="text" id="order-size" placeholder="e.g., 10-inch, DN250" class="w-full px-4 md:px-5 py-3 md:py-3.5 rounded-xl form-input-enhanced focus:ring-2 focus:ring-blue-500 outline-none transition-all text-sm md:text-base">
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
                    </div>
                    
                    <div class="transform transition-all duration-300 hover:scale-[1.02]">
                        <label class="block text-sm font-semibold text-slate-700 mb-2">Additional Specifications</label>
                        <textarea rows="3" id="order-specs" class="w-full px-4 md:px-5 py-3 md:py-3.5 rounded-xl form-input-enhanced focus:ring-2 focus:ring-blue-500 outline-none transition-all text-sm md:text-base" placeholder="Pressure rating, surface finish, coating, etc."></textarea>
                    </div>
                    
                    <button type="button" onclick="nextOrderStep(2)" class="w-full py-3 md:py-4 btn-gradient text-white font-bold rounded-xl transition-all transform hover:-translate-y-1 active:scale-95 shadow-lg hover:shadow-xl text-sm md:text-base">
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
                    <button type="button" onclick="nextOrderStep(3)" class="flex-1 py-3 md:py-3.5 btn-gradient text-white font-bold rounded-xl transition-all transform hover:-translate-y-1 active:scale-95 shadow-lg hover:shadow-xl text-sm md:text-base">
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
                        </div>
                        <div class="transform transition-all duration-300 hover:scale-[1.02]">
                            <label class="block text-sm font-semibold text-slate-700 mb-2">Last Name *</label>
                            <input type="text" id="order-lastname" required class="w-full px-4 md:px-5 py-3 md:py-3.5 rounded-xl form-input-enhanced focus:ring-2 focus:ring-blue-500 outline-none transition-all text-sm md:text-base">
                        </div>
                    </div>
                    
                    <div class="grid md:grid-cols-2 gap-4 md:gap-5">
                        <div class="transform transition-all duration-300 hover:scale-[1.02]">
                            <label class="block text-sm font-semibold text-slate-700 mb-2">Email *</label>
                            <input type="email" id="order-email" required class="w-full px-4 md:px-5 py-3 md:py-3.5 rounded-xl form-input-enhanced focus:ring-2 focus:ring-blue-500 outline-none transition-all text-sm md:text-base">
                        </div>
                        <div class="transform transition-all duration-300 hover:scale-[1.02]">
                            <label class="block text-sm font-semibold text-slate-700 mb-2">Phone *</label>
                            <input type="tel" id="order-phone" required class="w-full px-4 md:px-5 py-3 md:py-3.5 rounded-xl form-input-enhanced focus:ring-2 focus:ring-blue-500 outline-none transition-all text-sm md:text-base">
                        </div>
                    </div>
                    
                    <div class="transform transition-all duration-300 hover:scale-[1.02]">
                        <label class="block text-sm font-semibold text-slate-700 mb-2">Company *</label>
                        <input type="text" id="order-company" required class="w-full px-4 md:px-5 py-3 md:py-3.5 rounded-xl form-input-enhanced focus:ring-2 focus:ring-blue-500 outline-none transition-all text-sm md:text-base">
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
                        <button type="button" onclick="nextOrderStep(4)" class="flex-1 py-3 md:py-3.5 btn-gradient text-white font-bold rounded-xl transition-all transform hover:-translate-y-1 active:scale-95 shadow-lg hover:shadow-xl text-sm md:text-base">
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
                        Order Reference: <strong id="order-reference" class="text-blue-600">UF-ORD-${Date.now().toString().slice(-6)}</strong>
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

    <!-- Dashboard Modal (Only for Supplier Accounts) -->
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
            
            <!-- Dashboard Content (unchanged) -->
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
        <!-- Enhanced Navigation (unchanged) -->
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

        <!-- Enhanced Hero Section (unchanged) -->
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
                            <!-- Hero Image Container -->
                            <div class="hero-image-container">
                                <img src="industry.png.png" alt="Industrial Flange Manufacturing Facility" />
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

        <!-- Product Exploration Section (unchanged) -->
        <section id="catalog-access" class="bg-white border-y border-slate-200 py-12 md:py-16 overflow-hidden reveal">
            <div class="max-w-7xl mx-auto px-4">
                <div class="flex flex-col items-center gap-8 md:gap-10">
                    <div class="text-center max-w-3xl mx-auto">
                        <span class="text-blue-600 font-bold uppercase tracking-widest text-sm">Product Catalog</span>
                        <h2 class="text-3xl md:text-4xl font-bold text-slate-900 mt-2 mb-4">Explore Our Products</h2>
                        <p class="text-slate-600 text-base md:text-lg">Browse our extensive range of industrial flanges and precision components</p>
                    </div>
                    
                    <!-- Product Thumbnails Grid -->
                    <div class="w-full grid grid-cols-2 md:grid-cols-3 lg:grid-cols-4 gap-4 md:gap-6 mb-8 md:mb-12 reveal stagger-delay-1">
                        <!-- Weld Neck Flange -->
                        <div class="product-thumbnail" onclick="updateProduct('wnf')">
                            <img src="weld neck.png" alt="Weld Neck Flange" />
                        </div>
                        
                        <!-- Long Weld Neck -->
                        <div class="product-thumbnail" onclick="updateProduct('lwn')">
                            <img src="long weldneck.png" alt="Long Weld Neck Flange" />
                        </div>
                        
                        <!-- Slip-On Flange -->
                        <div class="product-thumbnail" onclick="updateProduct('slipon')">
                            <img src="slip on flange.png" alt="Slip-On Flange" />
                        </div>
                        
                        <!-- Blind Flange -->
                        <div class="product-thumbnail" onclick="updateProduct('blind')">
                            <img src="blind.png" alt="Blind Flange" />
                        </div>
                        
                        <!-- Puddle Flange -->
                        <div class="product-thumbnail" onclick="updateProduct('puddle')">
                            <img src="puddle flange.png" alt="Puddle Flange" />
                        </div>
                        
                        <!-- Plasma CNC -->
                        <div class="product-thumbnail" onclick="updateProduct('plasma')">
                            <img src="plasma cutiing.png" alt="Plasma CNC Cutting" />
                        </div>
                        
                        <!-- Profile Cutting -->
                        <div class="product-thumbnail" onclick="updateProduct('profile')">
                            <img src="images/profile-cutting.jpg" alt="Profile Cutting Services" />
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
                                <div onclick="updateProduct('wnf')" id="chip-wnf" class="flange-chip active px-3 md:px-5 py-2 md:py-2.5 rounded-full border-2 border-slate-200 bg-white text-xs md:text-sm font-semibold flex items-center gap-2">
                                    <i class="fas fa-fire"></i>Weld Neck
                                </div>
                                <div onclick="updateProduct('lwn')" id="chip-lwn" class="flange-chip px-3 md:px-5 py-2 md:py-2.5 rounded-full border-2 border-slate-200 bg-white text-xs md:text-sm font-semibold flex items-center gap-2">
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

        <!-- Product Details Section (unchanged) -->
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
                                        <img src="long weldneck.png" alt="Long Weld Neck Flange" id="product-main-image" />
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

        <!-- Detailed Technical Specifications (unchanged) -->
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

        <!-- Product Gallery Section (unchanged) -->
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
                            <img src="long weldneck.png" alt="Long Weld Neck Flange" style="object-fit: contain;">
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
                            <img src="weld neck.png" alt="Weld Neck Flange" style="object-fit: contain;">
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
                            <img src="slip on flange.png" alt="Slip-On Flange" style="object-fit: contain;">
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
                            <img src="blind.png" alt="Blind Flange" style="object-fit: contain;">
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
                            <img src="puddle flange.png" alt="Puddle Flange" style="object-fit: contain;">
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
                            <img src="plasma cutiing.png" alt="Plasma CNC Cutting" style="object-fit: contain;">
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

        <!-- "Know More" Deep Dive Section (unchanged) -->
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

        <!-- Contact Section (unchanged) -->
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

        <!-- Footer (unchanged) -->
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
        // Global Variables
        let currentUserType = 'visitor';
        let isSupplier = false;
        let isAuthenticated = false;
        let currentUser = null;
        let currentOrderStep = 1;
        let userOrders = [];
        let selectedSupplier = null;
        let currentProductKey = 'lwn';
        let chatMessages = [];
        
        // Supplier Data
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
        
        // Enhanced Authentication Management
        function toggleAuthView(view) {
            document.getElementById('login-form').classList.toggle('hidden', view !== 'login');
            document.getElementById('signup-form').classList.toggle('hidden', view !== 'signup');
        }
        
        function openAuthModal() {
            document.getElementById('auth-overlay').classList.remove('hidden');
            document.body.style.overflow = 'hidden';
        }
        
        function closeAuth() {
            document.getElementById('auth-overlay').classList.add('hidden');
            document.body.style.overflow = 'auto';
        }

        function setUserType(type) {
            currentUserType = type;
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

        function handleAuth(event, userType) {
            if (event) event.preventDefault();
            const loader = document.getElementById('transition-loader');
            loader.style.left = '0%';
            
            setTimeout(() => {
                const statusBadge = document.getElementById('user-status');
                const mobileStatus = document.getElementById('mobile-user-status');
                
                // Reset user state
                isSupplier = false;
                isAuthenticated = false;
                selectedSupplier = null;
                
                if (userType === 'visitor') {
                    // Visitor mode
                    isAuthenticated = false;
                    currentUser = { type: 'visitor' };
                    document.body.classList.add('visitor-mode');
                    
                    statusBadge.innerText = 'Visitor Mode';
                    statusBadge.className = 'px-3 py-1.5 bg-blue-50 rounded-full text-xs font-bold text-blue-600 uppercase border border-blue-100';
                    statusBadge.innerHTML = '<i class="fas fa-user mr-1"></i>Visitor';
                    
                    mobileStatus.innerText = 'Visitor Mode';
                    mobileStatus.className = 'px-3 py-2 bg-blue-50 rounded-lg text-sm font-bold text-blue-600';
                    
                    // Update UI for visitor
                    updateUIForUserType('visitor');
                } else if (userType === 'supplier' || currentUserType === 'supplier') {
                    // Supplier mode
                    isSupplier = true;
                    isAuthenticated = true;
                    currentUser = { type: 'supplier', name: 'Supplier User', id: 'SUP001' };
                    document.body.classList.remove('visitor-mode');
                    
                    statusBadge.innerText = 'Supplier';
                    statusBadge.className = 'px-3 py-1.5 bg-green-50 rounded-full text-xs font-bold text-green-600 uppercase border border-green-100';
                    statusBadge.innerHTML = '<i class="fas fa-building mr-1"></i>Supplier';
                    
                    mobileStatus.innerText = 'Supplier';
                    mobileStatus.className = 'px-3 py-2 bg-green-50 rounded-lg text-sm font-bold text-green-600';
                    
                    // Update UI for supplier
                    updateUIForUserType('supplier');
                } else {
                    // Partner mode
                    isAuthenticated = true;
                    currentUser = { type: 'partner', name: 'Partner User', id: 'PART001' };
                    document.body.classList.remove('visitor-mode');
                    
                    statusBadge.innerText = 'Partner';
                    statusBadge.className = 'px-3 py-1.5 bg-blue-50 rounded-full text-xs font-bold text-blue-600 uppercase border border-blue-100';
                    statusBadge.innerHTML = '<i class="fas fa-user-shield mr-1"></i>Partner';
                    
                    mobileStatus.innerText = 'Partner';
                    mobileStatus.className = 'px-3 py-2 bg-slate-100 rounded-lg text-sm font-bold text-slate-600';
                    
                    // Update UI for partner
                    updateUIForUserType('partner');
                    
                    // Load sample orders for partner
                    loadSampleOrders();
                }

                document.getElementById('auth-overlay').classList.add('hidden');
                document.body.classList.add('authenticated');
                document.body.style.overflow = 'auto';
                loader.style.left = '100%';
                setTimeout(() => loader.style.left = '-100%', 1200);
                initReveal();
                updateProduct('lwn');
                
                // Scroll to top to show hero section
                window.scrollTo({ top: 0, behavior: 'smooth' });
                
                if (isSupplier) {
                    setTimeout(() => {
                        showNotification('Welcome to Supplier Dashboard! Access your business analytics and manage orders.', 'success');
                    }, 500);
                } else if (userType !== 'visitor') {
                    setTimeout(() => {
                        showNotification('Welcome back! You can now connect with suppliers and place orders.', 'success');
                    }, 500);
                }
            }, 1000);
        }

        function updateUIForUserType(userType) {
            // Desktop navigation elements
            const profileBtn = document.getElementById('profile-btn');
            const dashboardBtn = document.getElementById('dashboard-btn');
            const supplierDashboardBtn = document.getElementById('supplier-dashboard-btn');
            const logoutBtn = document.getElementById('logout-btn');
            const loginBtn = document.getElementById('login-btn');
            
            // Mobile menu elements
            const mobileDashboardLink = document.getElementById('mobile-dashboard-link');
            const mobileSupplierDashboardLink = document.getElementById('mobile-supplier-dashboard-link');
            const mobileProfileLink = document.getElementById('mobile-profile-link');
            const mobileLogoutBtn = document.getElementById('mobile-logout-btn');
            const mobileLoginBtn = document.getElementById('mobile-login-btn');
            
            // Reset all
            [profileBtn, dashboardBtn, supplierDashboardBtn, logoutBtn, loginBtn,
             mobileDashboardLink, mobileSupplierDashboardLink, mobileProfileLink, mobileLogoutBtn, mobileLoginBtn]
            .forEach(el => {
                if (el) el.classList.add('hidden');
            });
            
            if (userType === 'visitor') {
                // Show login button for visitors
                if (loginBtn) loginBtn.classList.remove('hidden');
                if (mobileLoginBtn) mobileLoginBtn.classList.remove('hidden');
            } else {
                // Show logout button for authenticated users
                if (logoutBtn) logoutBtn.classList.remove('hidden');
                if (mobileLogoutBtn) mobileLogoutBtn.classList.remove('hidden');
                
                // Show profile button for all authenticated users
                if (profileBtn) profileBtn.classList.remove('hidden');
                if (mobileProfileLink) mobileProfileLink.classList.remove('hidden');
                
                if (userType === 'supplier') {
                    // Show supplier dashboard
                    if (supplierDashboardBtn) supplierDashboardBtn.classList.remove('hidden');
                    if (mobileSupplierDashboardLink) mobileSupplierDashboardLink.classList.remove('hidden');
                } else {
                    // Show partner dashboard
                    if (dashboardBtn) dashboardBtn.classList.remove('hidden');
                    if (mobileDashboardLink) mobileDashboardLink.classList.remove('hidden');
                }
            }
        }

        function logout() {
            const loader = document.getElementById('transition-loader');
            loader.style.left = '0%';
            setTimeout(() => {
                document.getElementById('auth-overlay').classList.remove('hidden');
                document.body.classList.remove('authenticated');
                document.body.classList.remove('visitor-mode');
                loader.style.left = '100%';
                setTimeout(() => loader.style.left = '-100%', 1200);
                toggleMobileMenu(false);
                closeDashboard();
                closeOrderModal();
                closeTrackingModal();
                closeChat();
                isSupplier = false;
                isAuthenticated = false;
                currentUser = null;
                selectedSupplier = null;
                userOrders = [];
                chatMessages = [];
                
                // Update UI to visitor mode
                updateUIForUserType('visitor');
                
                // Update status badges
                const statusBadge = document.getElementById('user-status');
                const mobileStatus = document.getElementById('mobile-user-status');
                statusBadge.innerText = 'Visitor Mode';
                statusBadge.className = 'px-3 py-1.5 bg-blue-50 rounded-full text-xs font-bold text-blue-600 uppercase border border-blue-100';
                statusBadge.innerHTML = '<i class="fas fa-user mr-1"></i>Visitor';
                
                mobileStatus.innerText = 'Visitor Mode';
                mobileStatus.className = 'px-3 py-2 bg-blue-50 rounded-lg text-sm font-bold text-blue-600';
                
                // Scroll to top when logging out
                window.scrollTo({ top: 0, behavior: 'smooth' });
            }, 800);
        }
        
        // Mobile Menu Toggle
        function toggleMobileMenu(forceClose) {
            const menu = document.getElementById('mobile-menu');
            const overlay = document.getElementById('mobile-menu-overlay');
            
            if (forceClose === false || (menu.classList.contains('active'))) {
                menu.classList.remove('active');
                overlay.classList.remove('active');
            } else {
                menu.classList.add('active');
                overlay.classList.add('active');
            }
        }

        // Chat Functions
        function openChat(supplier) {
            if (!isAuthenticated) {
                showNotification('Please login to chat with suppliers.', 'error');
                openAuthModal();
                return;
            }
            
            selectedSupplier = supplier;
            document.getElementById('chat-modal').classList.add('active');
            document.getElementById('chat-supplier-name').textContent = supplier.name;
            document.getElementById('chat-supplier-status').textContent = supplier.status;
            
            // Load chat messages
            loadChatMessages();
        }
        
        function closeChat() {
            document.getElementById('chat-modal').classList.remove('active');
            selectedSupplier = null;
        }
        
        function sendChatMessage() {
            const input = document.getElementById('chat-input');
            const message = input.value.trim();
            
            if (!message) return;
            
            // Add message to chat
            const timestamp = new Date().toLocaleTimeString([], {hour: '2-digit', minute:'2-digit'});
            chatMessages.push({
                id: Date.now(),
                sender: 'user',
                text: message,
                time: timestamp
            });
            
            // Clear input
            input.value = '';
            
            // Update chat display
            updateChatDisplay();
            
            // Simulate supplier response
            setTimeout(() => {
                const responses = [
                    "Thank you for your message. We'll get back to you shortly with a quotation.",
                    "Can you please share more details about your requirements?",
                    "We have this product in stock. What quantity do you need?",
                    "I can provide you with pricing within the next hour.",
                    "Would you like me to send you our catalog and pricing?"
                ];
                
                const response = responses[Math.floor(Math.random() * responses.length)];
                const responseTime = new Date().toLocaleTimeString([], {hour: '2-digit', minute:'2-digit'});
                
                chatMessages.push({
                    id: Date.now() + 1,
                    sender: 'supplier',
                    text: response,
                    time: responseTime
                });
                
                updateChatDisplay();
            }, 2000);
        }
        
        function loadChatMessages() {
            // Load existing chat messages or start new
            if (chatMessages.length === 0) {
                const timestamp = new Date().toLocaleTimeString([], {hour: '2-digit', minute:'2-digit'});
                chatMessages = [
                    {
                        id: 1,
                        sender: 'supplier',
                        text: `Hello! I'm ${selectedSupplier.name} from ${selectedSupplier.company}. How can I help you with your ${getCurrentProduct().title} requirements?`,
                        time: timestamp
                    }
                ];
            }
            
            updateChatDisplay();
        }
        
        function updateChatDisplay() {
            const chatContainer = document.getElementById('chat-messages');
            chatContainer.innerHTML = chatMessages.map(msg => `
                <div class="chat-message ${msg.sender === 'user' ? 'sent' : ''}">
                    <div class="bg-${msg.sender === 'user' ? 'blue' : 'slate'}-100 p-3 rounded-lg">
                        <p class="text-slate-800">${msg.text}</p>
                        <p class="text-xs text-slate-500 mt-1 text-right">${msg.time}</p>
                    </div>
                </div>
            `).join('');
            
            // Scroll to bottom
            chatContainer.scrollTop = chatContainer.scrollHeight;
        }
        
        // Supplier Functions
        function loadSuppliersForProduct(productKey) {
            const productName = document.getElementById('order-product').options[document.getElementById('order-product').selectedIndex].text;
            document.getElementById('selected-product-name').textContent = productName;
            
            const suppliers = supplierData[productKey] || [];
            const suppliersList = document.getElementById('suppliers-list');
            const noSuppliersMessage = document.getElementById('no-suppliers-message');
            
            if (suppliers.length === 0) {
                suppliersList.innerHTML = '';
                noSuppliersMessage.classList.remove('hidden');
                return;
            }
            
            noSuppliersMessage.classList.add('hidden');
            suppliersList.innerHTML = suppliers.map(supplier => `
                <div class="supplier-card bg-white p-4 rounded-xl border-2 border-slate-200 ${selectedSupplier?.id === supplier.id ? 'selected' : ''}" 
                     onclick="selectSupplier('${productKey}', '${supplier.id}')">
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
                                        <span class="text-slate-500 text-xs ml-1">(${supplier.reviews} reviews)</span>
                                    </div>
                                    <span class="text-xs bg-green-100 text-green-700 px-2 py-0.5 rounded">${supplier.status}</span>
                                </div>
                            </div>
                        </div>
                        <button onclick="event.stopPropagation(); openChat(${JSON.stringify(supplier).replace(/"/g, '&quot;')})" 
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
            `).join('');
        }
        
        function selectSupplier(productKey, supplierId) {
            const suppliers = supplierData[productKey] || [];
            selectedSupplier = suppliers.find(s => s.id === supplierId);
            
            // Update UI
            document.querySelectorAll('.supplier-card').forEach(card => {
                card.classList.remove('selected');
            });
            
            const selectedCard = document.querySelector(`[onclick*="${supplierId}"]`);
            if (selectedCard) {
                selectedCard.classList.add('selected');
            }
            
            // Update step 3 display
            document.getElementById('selected-supplier-display').textContent = 
                selectedSupplier ? `${selectedSupplier.name} (${selectedSupplier.company})` : 'Not selected';
        }
        
        function showAllSuppliers() {
            showNotification('Showing all available suppliers for this product', 'info');
        }

        // Dashboard Functions - Only for Supplier Accounts
        function openDashboard() {
            // Check if user is authenticated
            if (!isAuthenticated) {
                showNotification('Please login to access the dashboard.', 'error');
                openAuthModal();
                return;
            }
            
            // Check if user is a supplier
            if (!isSupplier && currentUser?.type !== 'supplier') {
                showNotification('Dashboard access is only available for supplier accounts.', 'error');
                return;
            }
            
            document.getElementById('dashboard-modal').classList.remove('hidden');
            document.body.style.overflow = 'hidden';
            initDashboardCharts();
        }
        
        function closeDashboard() {
            document.getElementById('dashboard-modal').classList.add('hidden');
            document.body.style.overflow = 'auto';
        }
        
        function switchDashboardTab(tabName) {
            // Update tab buttons
            document.querySelectorAll('#dashboard-modal .tab-button').forEach(btn => {
                btn.classList.toggle('active', btn.getAttribute('onclick').includes(tabName));
            });
            
            // Show selected tab content
            document.querySelectorAll('#dashboard-modal .tab-content').forEach(content => {
                content.classList.toggle('active', content.id === `dashboard-${tabName}`);
                content.classList.toggle('hidden', content.id !== `dashboard-${tabName}`);
            });
            
            // Initialize charts if needed
            if (tabName === 'analytics') {
                setTimeout(() => {
                    initAnalyticsCharts();
                }, 100);
            }
        }
        
        // Show Profile Function
        function showProfile() {
            if (!isAuthenticated) {
                showNotification('Please login to view your profile.', 'error');
                openAuthModal();
                return;
            }
            
            const userType = currentUser?.type || 'visitor';
            const userName = currentUser?.name || 'User';
            
            showNotification(`Welcome ${userName}! Profile page for ${userType} accounts is under development.`, 'info');
        }
        
        // Order Tracking Functions
        function openTrackingModal() {
            document.getElementById('tracking-modal').classList.remove('hidden');
            document.body.style.overflow = 'hidden';
            
            // If user is authenticated, show their orders
            if (isAuthenticated && currentUser?.type !== 'visitor') {
                showMyOrders();
            }
        }
        
        function closeTrackingModal() {
            document.getElementById('tracking-modal').classList.add('hidden');
            document.body.style.overflow = 'auto';
        }
        
        function trackOrderWithCode() {
            const orderId = document.getElementById('order-reference').textContent;
            if (orderId) {
                closeOrderModal();
                setTimeout(() => {
                    openTrackingModal();
                    document.getElementById('tracking-input').value = orderId;
                    searchOrder();
                }, 500);
            }
        }
        
        function searchOrder() {
            const orderId = document.getElementById('tracking-input').value.trim();
            if (!orderId) {
                showNotification('Please enter an order ID', 'error');
                return;
            }
            
            // Show loading state
            document.getElementById('tracking-empty').classList.add('hidden');
            document.getElementById('tracking-results').classList.add('hidden');
            document.getElementById('my-orders-section').classList.add('hidden');
            document.getElementById('tracking-loading').classList.remove('hidden');
            
            // Simulate API call
            setTimeout(() => {
                const order = findOrderById(orderId);
                if (order) {
                    displayOrderTracking(order);
                } else {
                    showNotification('Order not found. Please check your order ID.', 'error');
                    document.getElementById('tracking-loading').classList.add('hidden');
                    document.getElementById('tracking-empty').classList.remove('hidden');
                }
            }, 1000);
        }
        
        function findOrderById(orderId) {
            // Check in user orders first
            const userOrder = userOrders.find(order => 
                order.id === orderId || 
                order.reference === orderId ||
                order.id.toLowerCase().includes(orderId.toLowerCase())
            );
            
            if (userOrder) return userOrder;
            
            // Sample orders for demonstration
            const sampleOrders = [
                {
                    id: 'UF-ORD-7842',
                    reference: 'ORD-7842',
                    product: 'Weld Neck Flange',
                    productName: 'Weld Neck Flange DN50',
                    quantity: 50,
                    amount: '₹245,000',
                    date: 'Mar 15, 2024',
                    status: 'Processing',
                    estimatedDelivery: 'Mar 25, 2024',
                    customerName: 'John Doe',
                    company: 'Oil & Gas Corp',
                    contact: 'john@example.com',
                    address: '123 Industrial Park, Mumbai',
                    supplier: 'Precision Flange Co.',
                    supplierContact: 'sales@precisionflange.com',
                    supplierPhone: '+91 9876543210',
                    shippingMethod: 'Express Freight',
                    shipmentNumber: 'SHIP-789456123',
                    timeline: [
                        { step: 'Order Placed', status: 'completed', date: 'Mar 15, 2024', time: '10:30 AM', details: 'Order received and confirmed' },
                        { step: 'Payment Received', status: 'completed', date: 'Mar 15, 2024', time: '2:45 PM', details: 'Payment processed successfully' },
                        { step: 'Production Started', status: 'completed', date: 'Mar 16, 2024', time: '9:00 AM', details: 'Manufacturing in progress' },
                        { step: 'Quality Check', status: 'current', date: 'Mar 18, 2024', time: 'In progress', details: 'Undergoing final inspection' },
                        { step: 'Ready for Shipping', status: 'pending', date: 'Mar 20, 2024', time: '--', details: 'Awaiting dispatch' },
                        { step: 'Shipped', status: 'pending', date: 'Mar 22, 2024', time: '--', details: 'Will be shipped to your address' },
                        { step: 'Delivered', status: 'pending', date: 'Mar 25, 2024', time: '--', details: 'Estimated delivery date' }
                    ]
                }
            ];
            
            return sampleOrders.find(order => 
                order.id === orderId || 
                order.reference === orderId ||
                order.id.toLowerCase().includes(orderId.toLowerCase())
            );
        }
        
        function displayOrderTracking(order) {
            // Update order details
            document.getElementById('tracking-order-id').textContent = order.id;
            document.getElementById('tracking-product-name').textContent = order.productName;
            document.getElementById('tracking-status').textContent = order.status;
            document.getElementById('tracking-quantity').textContent = `${order.quantity} pieces`;
            document.getElementById('tracking-date').textContent = order.date;
            document.getElementById('tracking-delivery').textContent = order.estimatedDelivery;
            document.getElementById('tracking-amount').textContent = order.amount;
            document.getElementById('tracking-customer-name').textContent = order.customerName;
            document.getElementById('tracking-company').textContent = order.company;
            document.getElementById('tracking-contact').textContent = order.contact;
            document.getElementById('tracking-supplier').textContent = order.supplier;
            document.getElementById('tracking-supplier-contact').textContent = order.supplierContact;
            document.getElementById('tracking-supplier-phone').textContent = order.supplierPhone;
            
            // Update timeline
            const timelineContainer = document.getElementById('tracking-timeline');
            timelineContainer.innerHTML = order.timeline.map((step, index) => `
                <div class="tracking-step ${step.status === 'completed' ? 'completed' : step.status === 'current' ? 'current' : ''}">
                    <div class="tracking-step-icon ${step.status === 'completed' ? 'completed' : step.status === 'current' ? 'current' : 'pending'}">
                        <i class="fas fa-${getStepIcon(step.step)}"></i>
                    </div>
                    <div class="tracking-step-content">
                        <div class="flex flex-col md:flex-row md:items-center justify-between gap-2 mb-2">
                            <h5 class="font-bold text-slate-900">${step.step}</h5>
                            <div class="flex items-center gap-2">
                                <span class="text-sm text-slate-600">${step.date}</span>
                                <span class="text-sm text-slate-500">${step.time}</span>
                            </div>
                        </div>
                        <p class="text-slate-600 text-sm">${step.details}</p>
                    </div>
                </div>
            `).join('');
            
            // Show results
            document.getElementById('tracking-loading').classList.add('hidden');
            document.getElementById('tracking-results').classList.remove('hidden');
            document.getElementById('my-orders-section').classList.add('hidden');
        }
        
        function getStepIcon(step) {
            const icons = {
                'Order Placed': 'shopping-cart',
                'Payment Received': 'credit-card',
                'Production Started': 'cogs',
                'Quality Check': 'clipboard-check',
                'Ready for Shipping': 'box',
                'Shipped': 'truck',
                'Delivered': 'home'
            };
            return icons[step] || 'circle';
        }
        
        function showMyOrders() {
            if (!isAuthenticated || currentUser?.type === 'visitor') {
                showNotification('Please login to view your orders.', 'error');
                openAuthModal();
                return;
            }
            
            document.getElementById('tracking-results').classList.add('hidden');
            document.getElementById('tracking-empty').classList.add('hidden');
            document.getElementById('tracking-loading').classList.remove('hidden');
            document.getElementById('my-orders-section').classList.remove('hidden');
            
            // Simulate loading
            setTimeout(() => {
                const ordersList = document.getElementById('my-orders-list');
                ordersList.innerHTML = userOrders.length > 0 ? 
                    userOrders.map(order => `
                        <div class="bg-white rounded-xl p-4 border border-slate-200 hover:border-blue-300 transition">
                            <div class="flex flex-col md:flex-row md:items-center justify-between gap-3">
                                <div>
                                    <div class="flex items-center gap-3">
                                        <div class="w-10 h-10 bg-blue-100 rounded-lg flex items-center justify-center">
                                            <i class="fas fa-box text-blue-600"></i>
                                        </div>
                                        <div>
                                            <h5 class="font-bold text-slate-900">${order.id}</h5>
                                            <p class="text-sm text-slate-600">${order.productName}</p>
                                            <p class="text-xs text-slate-500">Supplier: ${order.supplier}</p>
                                        </div>
                                    </div>
                                </div>
                                <div class="flex flex-col md:items-end gap-2">
                                    <span class="px-3 py-1 bg-blue-100 text-blue-700 rounded-full text-xs font-bold">${order.status}</span>
                                    <span class="font-bold text-slate-900">${order.amount}</span>
                                    <button onclick="trackOrderById('${order.id}')" class="text-blue-600 hover:text-blue-800 text-sm font-medium">
                                        <i class="fas fa-search mr-1"></i>Track Order
                                    </button>
                                </div>
                            </div>
                        </div>
                    `).join('') :
                    `<div class="text-center py-8">
                        <i class="fas fa-box-open text-4xl text-slate-300 mb-3"></i>
                        <p class="text-slate-600">No orders found. Place your first order!</p>
                    </div>`;
                
                document.getElementById('tracking-loading').classList.add('hidden');
            }, 800);
        }
        
        function trackOrderById(orderId) {
            document.getElementById('tracking-input').value = orderId;
            searchOrder();
        }
        
        function downloadInvoice() {
            showNotification('Invoice download feature is under development.', 'info');
        }
        
        function contactSupplier() {
            showNotification('Contacting supplier... This would open your email client.', 'info');
        }
        
        function loadSampleOrders() {
            // Load sample orders for authenticated users
            userOrders = [
                {
                    id: 'UF-ORD-7842',
                    reference: 'ORD-7842',
                    product: 'Weld Neck Flange',
                    productName: 'Weld Neck Flange DN50',
                    quantity: 50,
                    amount: '₹245,000',
                    date: 'Mar 15, 2024',
                    status: 'Processing',
                    supplier: 'Precision Flange Co.'
                }
            ];
        }

        // Check Authentication Before Order
        function checkAuthBeforeOrder(productKey = null) {
            if (!isAuthenticated || currentUser?.type === 'visitor') {
                showNotification('Please login or create an account to connect with suppliers.', 'error');
                openAuthModal();
                return;
            }
            
            if (productKey) {
                openOrderModalWithProduct(productKey);
            } else {
                openOrderModal();
            }
        }

        // Order Modal Functions
        function openOrderModal() {
            // Check authentication first
            if (!isAuthenticated || currentUser?.type === 'visitor') {
                checkAuthBeforeOrder();
                return;
            }
            
            document.getElementById('order-modal').classList.remove('hidden');
            document.body.style.overflow = 'hidden';
            resetOrderSteps();
        }
        
        function openOrderModalWithProduct(productKey) {
            // Check authentication first
            if (!isAuthenticated || currentUser?.type === 'visitor') {
                checkAuthBeforeOrder(productKey);
                return;
            }
            
            openOrderModal();
            // Set the product in the order modal
            document.getElementById('order-product').value = productKey;
            loadSuppliersForProduct(productKey);
        }
        
        function closeOrderModal() {
            document.getElementById('order-modal').classList.add('hidden');
            document.body.style.overflow = 'auto';
            selectedSupplier = null;
        }

        function resetOrderSteps() {
            currentOrderStep = 1;
            updateStepIndicators();
            
            // Hide all steps
            for (let i = 1; i <= 5; i++) {
                const stepEl = document.getElementById(`order-step-${i}`);
                if (stepEl) stepEl.classList.add('hidden');
            }
            
            // Show step 1
            document.getElementById('order-step-1').classList.remove('hidden');
            
            // Reset supplier selection
            selectedSupplier = null;
            document.getElementById('selected-supplier-display').textContent = 'Not selected';
        }

        function updateStepIndicators() {
            const progress = document.getElementById('step-progress');
            const stepWidth = 100 / 4; // 5 steps, 4 transitions
            
            progress.style.width = `${(currentOrderStep - 1) * stepWidth}%`;
            
            // Update step indicators
            for (let i = 1; i <= 5; i++) {
                const indicator = document.getElementById(`step-indicator-${i}`);
                if (indicator) {
                    if (i < currentOrderStep) {
                        indicator.classList.remove('pending', 'active');
                        indicator.classList.add('completed');
                    } else if (i === currentOrderStep) {
                        indicator.classList.remove('pending', 'completed');
                        indicator.classList.add('active');
                    } else {
                        indicator.classList.remove('active', 'completed');
                        indicator.classList.add('pending');
                    }
                }
            }
        }

        function nextOrderStep(step) {
            if (step < 1 || step > 5) return;
            
            // Validate supplier selection for step 3
            if (step === 3 && !selectedSupplier) {
                showNotification('Please select a supplier before proceeding.', 'error');
                return;
            }
            
            // Update review section before moving to step 4
            if (step === 4) {
                updateReviewSection();
            }
            
            // Hide current step
            document.getElementById(`order-step-${currentOrderStep}`).classList.add('hidden');
            
            // Show new step with animation
            currentOrderStep = step;
            const nextStep = document.getElementById(`order-step-${step}`);
            nextStep.classList.remove('hidden');
            nextStep.style.animation = 'none';
            setTimeout(() => {
                nextStep.style.animation = 'slideIn 0.5s cubic-bezier(0.4, 0, 0.2, 1) forwards';
            }, 10);
            
            // Update step indicators
            updateStepIndicators();
        }

        function prevOrderStep(step) {
            nextOrderStep(step);
        }

        function updateReviewSection() {
            // Get values from form
            const productSelect = document.getElementById('order-product');
            const productText = productSelect.options[productSelect.selectedIndex].text;
            const quantity = document.getElementById('order-quantity').value;
            const materialSelect = document.getElementById('order-material');
            const materialText = materialSelect.options[materialSelect.selectedIndex].text;
            const contactMethod = document.querySelector('input[name="contactMethod"]:checked').value;
            
            // Update review section
            document.getElementById('review-product').textContent = productText;
            document.getElementById('review-supplier').textContent = selectedSupplier ? `${selectedSupplier.name} (${selectedSupplier.company})` : 'Not selected';
            document.getElementById('review-quantity').textContent = `${quantity} pieces`;
            document.getElementById('review-material').textContent = materialText;
            document.getElementById('review-contact').textContent = contactMethod.charAt(0).toUpperCase() + contactMethod.slice(1);
            
            // Update confirmation supplier
            document.getElementById('confirmation-supplier').textContent = selectedSupplier ? selectedSupplier.name : 'Supplier';
        }

        function submitOrder() {
            if (!selectedSupplier) {
                showNotification('Please select a supplier before submitting the order.', 'error');
                return;
            }
            
            // Get order data
            const orderData = {
                id: `UF-ORD-${Date.now().toString().slice(-6)}`,
                reference: `ORD-${Date.now().toString().slice(-4)}`,
                product: document.getElementById('order-product').value,
                productName: document.getElementById('order-product').options[document.getElementById('order-product').selectedIndex].text,
                quantity: document.getElementById('order-quantity').value,
                size: document.getElementById('order-size').value,
                material: document.getElementById('order-material').value,
                materialName: document.getElementById('order-material').options[document.getElementById('order-material').selectedIndex].text,
                specs: document.getElementById('order-specs').value,
                firstName: document.getElementById('order-firstname').value,
                lastName: document.getElementById('order-lastname').value,
                email: document.getElementById('order-email').value,
                phone: document.getElementById('order-phone').value,
                company: document.getElementById('order-company').value,
                address: document.getElementById('order-address').value,
                contactMethod: document.querySelector('input[name="contactMethod"]:checked').value,
                supplier: selectedSupplier,
                timestamp: new Date().toISOString(),
                status: 'Processing',
                amount: `₹${(parseInt(document.getElementById('order-quantity').value) * 5000).toLocaleString()}`
            };
            
            // Log order data
            console.log('Order submitted to supplier:', orderData);
            console.log('Supplier Details:', selectedSupplier);
            console.log('Order sent to:', selectedSupplier.email);
            console.log('Supplier will contact:', document.getElementById('order-email').value);
            
            // Add to user orders
            userOrders.unshift({
                id: orderData.id,
                reference: orderData.reference,
                product: orderData.product,
                productName: orderData.productName,
                quantity: orderData.quantity,
                amount: orderData.amount,
                date: new Date().toLocaleDateString('en-US', { month: 'short', day: 'numeric', year: 'numeric' }),
                status: orderData.status,
                supplier: selectedSupplier.name
            });
            
            // Update order reference
            document.getElementById('order-reference').textContent = orderData.id;
            
            // Show confirmation step
            nextOrderStep(5);
            
            // Simulate sending to supplier
            simulateSupplierNotification(orderData);
            
            // Show success notification
            showNotification(`Order submitted to ${selectedSupplier.name}! They will contact you shortly.`, 'success');
        }

        function simulateSupplierNotification(orderData) {
            console.log('Sending order notification to supplier...');
            console.log('Supplier Email:', orderData.supplier.email);
            console.log('Supplier Phone:', orderData.supplier.phone);
            console.log('Order Details:', {
                product: orderData.productName,
                quantity: orderData.quantity,
                material: orderData.materialName,
                customer: `${orderData.firstName} ${orderData.lastName}`,
                company: orderData.company,
                contact: orderData.email
            });
            
            setTimeout(() => {
                console.log('Supplier notified successfully!');
                console.log('Supplier will send:');
                console.log('1. Quotation to:', orderData.email);
                console.log('2. Delivery timeline');
                console.log('3. Proforma invoice');
                console.log('4. Production schedule');
            }, 1000);
        }

        // Chart Initialization
        function initDashboardCharts() {
            // Sales Chart
            const salesCtx = document.getElementById('salesChart').getContext('2d');
            new Chart(salesCtx, {
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
                    plugins: {
                        legend: {
                            display: false
                        }
                    },
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
        
        function initAnalyticsCharts() {
            // Category Chart
            const categoryCtx = document.getElementById('categoryChart').getContext('2d');
            new Chart(categoryCtx, {
                type: 'doughnut',
                data: {
                    labels: ['Weld Neck', 'Long Weld Neck', 'Blind Flange', 'Plasma CNC', 'Others'],
                    datasets: [{
                        data: [42, 30, 12, 8, 8],
                        backgroundColor: [
                            '#3b82f6',
                            '#10b981',
                            '#f59e0b',
                            '#8b5cf6',
                            '#64748b'
                        ]
                    }]
                },
                options: {
                    responsive: true,
                    maintainAspectRatio: false,
                    plugins: {
                        legend: {
                            position: 'bottom'
                        }
                    }
                }
            });
            
            // Performance Chart
            const performanceCtx = document.getElementById('performanceChart').getContext('2d');
            new Chart(performanceCtx, {
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
                    scales: {
                        y: {
                            beginAtZero: true
                        }
                    }
                }
            });
            
            // Conversion Chart
            const conversionCtx = document.getElementById('conversionChart').getContext('2d');
            new Chart(conversionCtx, {
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
                    plugins: {
                        legend: {
                            display: false
                        }
                    }
                }
            });
        }

        // Product Data with image references
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
                image: "long weldneck.png",
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
                image: "weld neck.png",
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
                image: "slip on flange.png",
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
                image: "blind.png",
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
                image: "puddle flange.png",
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
                image: "plasma cutiing.png",
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
                image: "images/profile-cutting.jpg",
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

        // Product Functions
        function downloadProductFiles() {
            const currentProduct = getCurrentProduct();
            if (currentProduct && currentProduct.title) {
                showNotification(`Preparing ${currentProduct.title} technical files for download...`, 'info');
                setTimeout(() => {
                    showNotification(`${currentProduct.title} technical files ready for download`, 'success');
                    const link = document.createElement('a');
                    link.href = '#';
                    link.download = `${currentProduct.title.replace(/\s+/g, '_')}_technical_specs.pdf`;
                    link.click();
                }, 1500);
            }
        }

        function requestCustomQuote() {
            checkAuthBeforeOrder();
            showNotification('Custom quote request form opened', 'info');
        }

        function showAllProducts() {
            document.getElementById('product-gallery').scrollIntoView({ 
                behavior: 'smooth',
                block: 'start'
            });
            showNotification('Viewing all products gallery', 'info');
        }

        function showNotification(message, type = 'info') {
            const notification = document.createElement('div');
            notification.className = `fixed top-4 right-4 z-50 px-4 md:px-6 py-2 md:py-3 rounded-lg shadow-lg text-white font-medium transform transition-all duration-300 ${type === 'success' ? 'bg-green-600' : type === 'error' ? 'bg-red-600' : 'bg-blue-600'}`;
            notification.innerHTML = `
                <div class="flex items-center gap-2 text-sm md:text-base">
                    <i class="fas fa-${type === 'success' ? 'check-circle' : type === 'error' ? 'exclamation-circle' : 'info-circle'}"></i>
                    <span>${message}</span>
                </div>
            `;
            
            document.body.appendChild(notification);
            
            setTimeout(() => {
                notification.style.transform = 'translateX(100%)';
                setTimeout(() => notification.remove(), 300);
            }, 3000);
        }

        function getCurrentProduct() {
            const activeChip = document.querySelector('.flange-chip.active');
            if (activeChip) {
                const chipId = activeChip.id.replace('chip-', '');
                return productData[chipId];
            }
            return productData.lwn;
        }

        function updateProduct(key) {
            currentProductKey = key;
            const data = productData[key] || productData.lwn;
            
            // Update active chip
            document.querySelectorAll('.flange-chip').forEach(c => c.classList.remove('active'));
            const activeChip = document.getElementById(`chip-${key}`);
            if (activeChip) activeChip.classList.add('active');

            // Update product image
            const productImage = document.getElementById('product-main-image');
            if (data.image && productImage) {
                productImage.src = data.image;
                productImage.alt = data.title;
            }

            // Update product info
            document.getElementById('current-product-name').textContent = data.title;

            // Update product details
            document.getElementById('p-title').innerText = data.title;
            document.getElementById('p-desc').innerText = data.desc;
            
            // Update features
            const featuresContainer = document.getElementById('p-features');
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

            // Update specifications
            document.getElementById('spec-title').innerText = `${data.title} - Technical Specifications`;
            renderSpecTables(data.specs);
            
            // Update suppliers list
            updateProductSuppliers(key);
            
            // Animate product card
            const productCard = document.getElementById('product-card');
            productCard.style.opacity = '0';
            productCard.style.transform = 'translateY(20px)';
            setTimeout(() => {
                productCard.style.opacity = '1';
                productCard.style.transform = 'translateY(0)';
                initReveal();
                
                document.getElementById('products').scrollIntoView({ 
                    behavior: 'smooth',
                    block: 'start'
                });
            }, 50);
            
            showNotification(`Loaded ${data.title} details`, 'success');
        }
        
        function updateProductSuppliers(productKey) {
            const suppliers = supplierData[productKey] || [];
            const suppliersList = document.getElementById('dynamic-suppliers-list');
            const productSuppliersList = document.getElementById('product-suppliers-list');
            
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
            
            // Update main suppliers list
            suppliersList.innerHTML = suppliers.slice(0, 2).map(supplier => `
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
                        <button onclick="openChat(${JSON.stringify(supplier).replace(/"/g, '&quot;')})" 
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
            `).join('');
            
            // Update product info suppliers list
            productSuppliersList.innerHTML = suppliers.slice(0, 3).map(supplier => `
                <div class="flex items-center justify-between py-2 border-b border-slate-700/50 last:border-0">
                    <div class="flex items-center gap-2">
                        <i class="fas fa-user-tie text-blue-400"></i>
                        <span>${supplier.name}</span>
                    </div>
                    <div class="flex items-center gap-2">
                        <span class="text-xs bg-green-900 text-green-300 px-2 py-0.5 rounded">${supplier.rating} ★</span>
                        <button onclick="openChat(${JSON.stringify(supplier).replace(/"/g, '&quot;')})" 
                                class="text-blue-400 hover:text-blue-300">
                            <i class="fas fa-comment"></i>
                        </button>
                    </div>
                </div>
            `).join('');
        }

        function renderSpecTables(specs) {
            const container = document.getElementById('spec-tables-container');
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

        function handleSearch(query) {
            const term = query.toLowerCase().trim();
            if (term.length < 2) return;
            
            for (const [key, data] of Object.entries(productData)) {
                if (data.title.toLowerCase().includes(term) || 
                    key.includes(term) || 
                    data.desc.toLowerCase().includes(term) ||
                    data.features.some(f => f.toLowerCase().includes(term))) {
                    updateProduct(key);
                    break;
                }
            }
        }

        function initReveal() {
            const reveals = document.querySelectorAll('.reveal');
            const observer = new IntersectionObserver((entries) => {
                entries.forEach(entry => {
                    if (entry.isIntersecting) {
                        entry.target.classList.add('active');
                    }
                });
            }, { 
                threshold: 0.1,
                rootMargin: '0px 0px -50px 0px'
            });
            reveals.forEach(r => observer.observe(r));
        }

        // Initialize
        window.onload = () => {
            setUserType('partner');
            updateProduct('lwn');
            initReveal();
            updateUIForUserType('visitor');
            
            // Ensure hero section is at top on page load
            window.scrollTo(0, 0);
            
            // Close mobile menu when clicking outside
            document.addEventListener('click', (e) => {
                const mobileMenu = document.getElementById('mobile-menu');
                const menuBtn = document.querySelector('button[onclick="toggleMobileMenu()"]');
                const overlay = document.getElementById('mobile-menu-overlay');
                
                if (mobileMenu && mobileMenu.classList.contains('active') && 
                    !mobileMenu.contains(e.target) && 
                    menuBtn && !menuBtn.contains(e.target) &&
                    overlay && overlay.contains(e.target)) {
                    toggleMobileMenu(false);
                }
            });
            
            // Close modals on escape key
            document.addEventListener('keydown', (e) => {
                if (e.key === 'Escape') {
                    const orderModal = document.getElementById('order-modal');
                    if (orderModal && !orderModal.classList.contains('hidden')) {
                        closeOrderModal();
                    }
                    const dashboardModal = document.getElementById('dashboard-modal');
                    if (dashboardModal && !dashboardModal.classList.contains('hidden')) {
                        closeDashboard();
                    }
                    const authModal = document.getElementById('auth-overlay');
                    if (authModal && !authModal.classList.contains('hidden')) {
                        closeAuth();
                    }
                    const trackingModal = document.getElementById('tracking-modal');
                    if (trackingModal && !trackingModal.classList.contains('hidden')) {
                        closeTrackingModal();
                    }
                    const chatModal = document.getElementById('chat-modal');
                    if (chatModal && chatModal.classList.contains('active')) {
                        closeChat();
                    }
                    const mobileMenu = document.getElementById('mobile-menu');
                    if (mobileMenu && mobileMenu.classList.contains('active')) {
                        toggleMobileMenu(false);
                    }
                }
            });
            
            // Initialize order modal with current product
            document.getElementById('order-product').addEventListener('change', function() {
                const selectedValue = this.value;
                if (selectedValue && selectedValue !== 'custom') {
                    loadSuppliersForProduct(selectedValue);
                    const product = productData[selectedValue];
                    if (product) {
                        document.getElementById('order-material').value = 'stainless';
                    }
                }
            });
            
            // Chat input enter key support
            document.getElementById('chat-input').addEventListener('keypress', function(e) {
                if (e.key === 'Enter') {
                    sendChatMessage();
                }
            });
        };
    </script>
</body>
</html>

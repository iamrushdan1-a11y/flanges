<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Ultimate Flange | Industrial Precision Solutions</title>
    <script src="https://cdn.tailwindcss.com"></script>
    <link href="https://fonts.googleapis.com/css2?family=Inter:wght@300;400;500;600;700;800&display=swap" rel="stylesheet">
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">
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
        
        #auth-overlay {
            display: none;
        }
        
        body.require-auth #auth-overlay {
            display: flex;
        }
        
        body.require-auth #main-content {
            filter: blur(8px);
            pointer-events: none;
        }
        
        body.visitor-mode #main-content {
            filter: blur(0);
            pointer-events: auto;
        }
        
        body.authenticated #main-content {
            filter: blur(0);
            pointer-events: auto;
        }
        
        .order-button {
            pointer-events: auto;
            cursor: pointer;
            position: relative;
            z-index: 10;
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
        
        .contact-form input:focus,
        .contact-form textarea:focus,
        .contact-form select:focus {
            box-shadow: 0 0 0 3px rgba(37, 99, 235, 0.15);
            border-color: var(--secondary-blue);
        }
        
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
        
        .input-error {
            border-color: #ef4444 !important;
        }
        
        .validation-message {
            color: #ef4444;
            font-size: 12px;
            margin-top: 4px;
            display: block;
        }
        
        .product-form {
            background: white;
            border-radius: 12px;
            padding: 20px;
            border: 1px solid #e2e8f0;
        }
        
        .product-form input,
        .product-form select,
        .product-form textarea {
            width: 100%;
            padding: 10px;
            border: 1px solid #e2e8f0;
            border-radius: 8px;
            transition: all 0.3s ease;
        }
        
        .product-form input:focus,
        .product-form select:focus,
        .product-form textarea:focus {
            border-color: #3b82f6;
            box-shadow: 0 0 0 3px rgba(59, 130, 246, 0.1);
            outline: none;
        }
        
        .product-form label {
            font-weight: 600;
            color: #475569;
            margin-bottom: 4px;
            display: block;
        }
        
        .action-button {
            padding: 8px 12px;
            border-radius: 6px;
            font-size: 0.875rem;
            font-weight: 500;
            transition: all 0.3s ease;
            cursor: pointer;
        }
        
        .action-button.edit {
            background: #dbeafe;
            color: #1e40af;
        }
        
        .action-button.edit:hover {
            background: #bfdbfe;
        }
        
        .action-button.delete {
            background: #fee2e2;
            color: #991b1b;
        }
        
        .action-button.delete:hover {
            background: #fecaca;
        }
        
        .action-button.view {
            background: #e2e8f0;
            color: #475569;
        }
        
        .action-button.view:hover {
            background: #cbd5e1;
        }
        
        .action-button.approve {
            background: #dcfce7;
            color: #166534;
        }
        
        .action-button.approve:hover {
            background: #bbf7d0;
        }
        
        .action-button.reject {
            background: #fee2e2;
            color: #991b1b;
        }
        
        .action-button.reject:hover {
            background: #fecaca;
        }
        
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
                    
                    <!-- User Type Selection -->
                    <div>
                        <label class="block text-sm font-semibold text-slate-700 mb-2">Login As</label>
                        <div class="grid grid-cols-2 gap-3">
                            <button type="button" onclick="setUserType('partner')" 
                                    class="partner-btn px-3 md:px-4 py-2.5 md:py-3 rounded-lg border-2 border-blue-200 bg-blue-50 text-blue-700 font-medium flex items-center justify-center gap-2 text-sm md:text-base">
                                <i class="fas fa-user-shield"></i>
                                Partner
                            </button>
                            <button type="button" onclick="setUserType('supplier')" 
                                    class="supplier-btn px-3 md:px-4 py-2.5 md:py-3 rounded-lg border-2 border-slate-200 hover:border-blue-200 hover:bg-blue-50 font-medium flex items-center justify-center gap-2 text-sm md:text-base">
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
                    
                    <!-- Account Type Selection for Signup -->
                    <div>
                        <label class="block text-sm font-semibold text-slate-700 mb-2">Account Type</label>
                        <div class="grid grid-cols-2 gap-3">
                            <label class="flex items-center p-3 border-2 border-blue-200 bg-blue-50 text-blue-700 rounded-lg cursor-pointer">
                                <input type="radio" name="signup-type" value="partner" checked class="mr-2">
                                <i class="fas fa-user-shield mr-2"></i>
                                Partner
                            </label>
                            <label class="flex items-center p-3 border-2 border-slate-200 hover:border-blue-200 rounded-lg cursor-pointer">
                                <input type="radio" name="signup-type" value="supplier" class="mr-2">
                                <i class="fas fa-building mr-2"></i>
                                Supplier
                            </label>
                        </div>
                    </div>
                    
                    <button type="submit" 
                            class="w-full py-3 md:py-4 bg-gradient-to-r from-blue-600 to-blue-800 text-white font-bold rounded-xl hover:from-blue-700 hover:to-blue-900 transition-all shadow-lg shadow-blue-100 text-sm md:text-base">
                        <i class="fas fa-user-plus mr-2"></i>Create Account
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

    <!-- Order Process Modal (Visible only to partners, hidden for suppliers) -->
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
                            <!-- Products will be loaded dynamically from API -->
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
                    <p class="text-slate-600 mb-4 text-sm md:text-base">Select a supplier to place your order</p>
                    
                    <div class="space-y-4" id="suppliers-list">
                        <!-- Suppliers will be loaded here dynamically -->
                    </div>
                    
                    <div id="no-suppliers-message" class="hidden text-center py-8">
                        <div class="w-16 h-16 bg-slate-100 rounded-full flex items-center justify-center mx-auto mb-4">
                            <i class="fas fa-users text-slate-400 text-2xl"></i>
                        </div>
                        <h4 class="text-lg font-bold text-slate-700 mb-2">No Suppliers Available</h4>
                        <p class="text-slate-500 max-w-md mx-auto">No suppliers are available for this product at the moment.</p>
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

    <!-- Dashboard Modal (Supplier Only) -->
    <div id="dashboard-modal" class="fixed inset-0 bg-black/60 backdrop-blur-md hidden items-center justify-center p-4 z-50">
        <div class="bg-white w-full max-w-7xl h-[90vh] rounded-3xl shadow-2xl overflow-hidden relative flex flex-col">
            <div class="px-4 md:px-8 pt-6 md:pt-8 pb-4 border-b border-slate-200">
                <div class="flex justify-between items-center">
                    <div>
                        <h2 class="text-xl md:text-3xl font-bold text-slate-900">Supplier Dashboard</h2>
                        <p class="text-slate-600 mt-1 text-sm md:text-base">Manage your products, inventory, and incoming orders</p>
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
                        <i class="fas fa-shopping-cart mr-2"></i>Incoming Orders
                    </button>
                    <button onclick="switchDashboardTab('inventory')" class="tab-button whitespace-nowrap text-sm md:text-base">
                        <i class="fas fa-boxes mr-2"></i>Manage Products
                    </button>
                    <button onclick="switchDashboardTab('customers')" class="tab-button whitespace-nowrap text-sm md:text-base">
                        <i class="fas fa-users mr-2"></i>Customers
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
                                    <h3 class="text-2xl md:text-3xl font-bold mt-2" id="dashboard-total-revenue">₹0</h3>
                                    <p class="text-sm mt-2 flex items-center">
                                        <i class="fas fa-arrow-up mr-1"></i>From completed orders
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
                                    <p class="text-sm opacity-90">Incoming Orders</p>
                                    <h3 class="text-2xl md:text-3xl font-bold mt-2" id="dashboard-incoming-orders">0</h3>
                                    <p class="text-sm mt-2 flex items-center">
                                        <i class="fas fa-clock mr-1"></i> <span id="dashboard-pending-orders">0</span> pending approval
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
                                    <p class="text-sm opacity-90">Active Products</p>
                                    <h3 class="text-2xl md:text-3xl font-bold mt-2" id="dashboard-total-products">0</h3>
                                    <p class="text-sm mt-2 flex items-center">
                                        <i class="fas fa-box mr-1"></i>In your inventory
                                    </p>
                                </div>
                                <div class="w-10 h-10 md:w-12 md:h-12 bg-white/20 rounded-lg flex items-center justify-center">
                                    <i class="fas fa-warehouse text-xl md:text-2xl"></i>
                                </div>
                            </div>
                        </div>
                        
                        <div class="stat-card">
                            <div class="flex justify-between items-start">
                                <div>
                                    <p class="text-sm opacity-90">Total Customers</p>
                                    <h3 class="text-2xl md:text-3xl font-bold mt-2" id="dashboard-total-customers">0</h3>
                                    <p class="text-sm mt-2 flex items-center">
                                        <i class="fas fa-user-plus mr-1"></i>Unique customers
                                    </p>
                                </div>
                                <div class="w-10 h-10 md:w-12 md:h-12 bg-white/20 rounded-lg flex items-center justify-center">
                                    <i class="fas fa-users text-xl md:text-2xl"></i>
                                </div>
                            </div>
                        </div>
                    </div>
                    
                    <!-- Recent Orders -->
                    <div class="dashboard-card">
                        <div class="flex justify-between items-center mb-4">
                            <h3 class="font-bold text-lg text-slate-900">Recent Incoming Orders</h3>
                            <a href="#" onclick="switchDashboardTab('orders')" class="text-blue-600 text-sm font-medium hover:text-blue-800">View All</a>
                        </div>
                        <div class="space-y-4" id="dashboard-recent-orders">
                            <div class="text-center py-4 text-slate-500">
                                No orders yet
                            </div>
                        </div>
                    </div>
                </div>
                
                <!-- Incoming Orders Tab -->
                <div id="dashboard-orders" class="tab-content hidden">
                    <div class="flex justify-between items-center mb-6">
                        <h3 class="text-xl md:text-2xl font-bold text-slate-900">Incoming Order Management</h3>
                        <div class="flex gap-2">
                            <select id="order-status-filter" class="px-3 py-2 border border-slate-300 rounded-lg text-sm" onchange="filterOrders()">
                                <option value="all">All Orders</option>
                                <option value="pending">Pending</option>
                                <option value="processing">Processing</option>
                                <option value="shipped">Shipped</option>
                                <option value="completed">Completed</option>
                            </select>
                        </div>
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
                            <tbody id="orders-table-body">
                                <tr>
                                    <td colspan="8" class="text-center py-8 text-slate-500">
                                        No orders found
                                    </td>
                                </tr>
                            </tbody>
                        </table>
                    </div>
                </div>
                
                <!-- Manage Products Tab -->
                <div id="dashboard-inventory" class="tab-content hidden">
                    <div class="flex justify-between items-center mb-6">
                        <h3 class="text-xl md:text-2xl font-bold text-slate-900">Product Management</h3>
                        <button onclick="showAddProductForm()" class="px-3 md:px-4 py-2 bg-blue-600 text-white rounded-lg hover:bg-blue-700 transition flex items-center gap-2">
                            <i class="fas fa-plus"></i> Add New Product
                        </button>
                    </div>
                    
                    <!-- Add/Edit Product Form -->
                    <div id="product-form-container" class="hidden mb-6">
                        <div class="dashboard-card">
                            <h4 class="font-bold text-lg text-slate-900 mb-4" id="product-form-title">Add New Product</h4>
                            <form id="product-form" class="space-y-4" onsubmit="saveProduct(event)">
                                <div class="grid md:grid-cols-2 gap-4">
                                    <div>
                                        <label class="block text-sm font-medium text-slate-700 mb-2">Product Name *</label>
                                        <input type="text" id="product-name" class="w-full px-3 py-2 rounded-lg border border-slate-300 focus:ring-2 focus:ring-blue-500 focus:border-blue-500 outline-none" required>
                                    </div>
                                    <div>
                                        <label class="block text-sm font-medium text-slate-700 mb-2">Product Key *</label>
                                        <input type="text" id="product-key" placeholder="e.g., lwn, wnf, custom" class="w-full px-3 py-2 rounded-lg border border-slate-300 focus:ring-2 focus:ring-blue-500 focus:border-blue-500 outline-none" required>
                                    </div>
                                </div>
                                
                                <div>
                                    <label class="block text-sm font-medium text-slate-700 mb-2">Description</label>
                                    <textarea id="product-description" rows="3" class="w-full px-3 py-2 rounded-lg border border-slate-300 focus:ring-2 focus:ring-blue-500 focus:border-blue-500 outline-none"></textarea>
                                </div>
                                
                                <div class="grid md:grid-cols-3 gap-4">
                                    <div>
                                        <label class="block text-sm font-medium text-slate-700 mb-2">Price (₹) *</label>
                                        <input type="number" id="product-price" class="w-full px-3 py-2 rounded-lg border border-slate-300 focus:ring-2 focus:ring-blue-500 focus:border-blue-500 outline-none" required>
                                    </div>
                                    <div>
                                        <label class="block text-sm font-medium text-slate-700 mb-2">Stock Quantity *</label>
                                        <input type="number" id="product-stock" class="w-full px-3 py-2 rounded-lg border border-slate-300 focus:ring-2 focus:ring-blue-500 focus:border-blue-500 outline-none" required>
                                    </div>
                                    <div>
                                        <label class="block text-sm font-medium text-slate-700 mb-2">Unit *</label>
                                        <input type="text" id="product-unit" value="pieces" class="w-full px-3 py-2 rounded-lg border border-slate-300 focus:ring-2 focus:ring-blue-500 focus:border-blue-500 outline-none" required>
                                    </div>
                                </div>
                                
                                <div class="grid md:grid-cols-2 gap-4">
                                    <div>
                                        <label class="block text-sm font-medium text-slate-700 mb-2">Category</label>
                                        <select id="product-category" class="w-full px-3 py-2 rounded-lg border border-slate-300 focus:ring-2 focus:ring-blue-500 focus:border-blue-500 outline-none">
                                            <option value="flanges">Flanges</option>
                                            <option value="fittings">Pipe Fittings</option>
                                            <option value="cutting">Cutting Services</option>
                                            <option value="custom">Custom Products</option>
                                        </select>
                                    </div>
                                    <div>
                                        <label class="block text-sm font-medium text-slate-700 mb-2">Material</label>
                                        <input type="text" id="product-material" placeholder="e.g., Carbon Steel, Stainless Steel" class="w-full px-3 py-2 rounded-lg border border-slate-300 focus:ring-2 focus:ring-blue-500 focus:border-blue-500 outline-none">
                                    </div>
                                </div>
                                
                                <div>
                                    <label class="block text-sm font-medium text-slate-700 mb-2">Specifications</label>
                                    <textarea id="product-specs" rows="2" placeholder="Size range, pressure ratings, etc." class="w-full px-3 py-2 rounded-lg border border-slate-300 focus:ring-2 focus:ring-blue-500 focus:border-blue-500 outline-none"></textarea>
                                </div>
                                
                                <div class="flex gap-3 pt-4">
                                    <button type="submit" class="px-6 py-2 bg-blue-600 text-white rounded-lg font-medium hover:bg-blue-700 transition">
                                        Save Product
                                    </button>
                                    <button type="button" onclick="cancelProductForm()" class="px-6 py-2 bg-slate-200 text-slate-700 rounded-lg font-medium hover:bg-slate-300 transition">
                                        Cancel
                                    </button>
                                </div>
                            </form>
                        </div>
                    </div>
                    
                    <div class="grid md:grid-cols-2 lg:grid-cols-3 gap-4 md:gap-6 mb-6 md:mb-8">
                        <div class="dashboard-card">
                            <div class="flex items-center justify-between">
                                <div>
                                    <div class="text-sm text-slate-500">Total Products</div>
                                    <div class="text-2xl md:text-3xl font-bold mt-1" id="dashboard-product-count">0</div>
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
                                    <div class="text-2xl md:text-3xl font-bold mt-1" id="dashboard-low-stock">0</div>
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
                                    <div class="text-2xl md:text-3xl font-bold mt-1" id="dashboard-out-of-stock">0</div>
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
                                    <th>Key</th>
                                    <th>Category</th>
                                    <th>Price</th>
                                    <th>Stock</th>
                                    <th>Unit</th>
                                    <th>Status</th>
                                    <th>Actions</th>
                                </tr>
                            </thead>
                            <tbody id="products-table-body">
                                <tr>
                                    <td colspan="8" class="text-center py-8 text-slate-500">
                                        No products added yet. Click "Add New Product" to get started.
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
                    </div>
                    
                    <div class="grid md:grid-cols-3 gap-4 md:gap-6 mb-6 md:mb-8">
                        <div class="dashboard-card">
                            <div class="flex items-center gap-4">
                                <div class="w-14 h-14 md:w-16 md:h-16 bg-blue-100 rounded-full flex items-center justify-center">
                                    <i class="fas fa-building text-blue-600 text-xl md:text-2xl"></i>
                                </div>
                                <div>
                                    <div class="text-sm text-slate-500">Total Customers</div>
                                    <div class="text-2xl md:text-3xl font-bold mt-1" id="dashboard-customer-count">0</div>
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
                                    <div class="text-2xl md:text-3xl font-bold mt-1" id="dashboard-active-customers">0</div>
                                </div>
                            </div>
                        </div>
                        <div class="dashboard-card">
                            <div class="flex items-center gap-4">
                                <div class="w-14 h-14 md:w-16 md:h-16 bg-purple-100 rounded-full flex items-center justify-center">
                                    <i class="fas fa-medal text-purple-600 text-xl md:text-2xl"></i>
                                </div>
                                <div>
                                    <div class="text-sm text-slate-500">Total Orders</div>
                                    <div class="text-2xl md:text-3xl font-bold mt-1" id="dashboard-total-orders">0</div>
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
                                    <th>Email</th>
                                    <th>Total Orders</th>
                                    <th>Total Spent</th>
                                    <th>Last Order</th>
                                    <th>Actions</th>
                                </tr>
                            </thead>
                            <tbody id="customers-table-body">
                                <tr>
                                    <td colspan="7" class="text-center py-8 text-slate-500">
                                        No customers yet
                                    </td>
                                </tr>
                            </tbody>
                        </table>
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
            <a href="#" onclick="toggleMobileMenu(); openDashboard();" id="mobile-dashboard-link" class="block text-slate-700 hover:text-blue-600 font-medium py-3 border-b border-slate-100 hidden">Supplier Dashboard</a>
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
                                <i class="fas fa-building mr-1"></i>Supplier Dashboard
                            </button>
                            <button onclick="logout()" id="logout-btn" class="text-slate-400 hover:text-red-600 transition text-xs font-bold uppercase tracking-wider hidden">
                                <i class="fas fa-sign-out-alt mr-1"></i>Logout
                            </button>
                            <button onclick="openAuthModal()" id="login-btn" class="text-slate-400 hover:text-blue-600 transition text-xs font-bold uppercase tracking-wider">
                                <i class="fas fa-sign-in-alt mr-1"></i>Login
                            </button>
                            <button onclick="checkAuthBeforeOrder()" id="order-now-btn" class="px-5 py-2.5 bg-gradient-to-r from-blue-600 to-blue-800 text-white font-semibold rounded-lg hover:from-blue-700 hover:to-blue-900 transition shadow-md order-button">
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
                            <div class="hero-image-container" id="hero-image-container">
                                <div class="img-fallback">
                                    <i class="fas fa-industry"></i>
                                </div>
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
                    
                    <!-- Product Thumbnails Grid -->
                    <div class="w-full grid grid-cols-2 md:grid-cols-3 lg:grid-cols-4 gap-4 md:gap-6 mb-8 md:mb-12 reveal stagger-delay-1" id="product-thumbnails">
                        <!-- Products will be loaded dynamically from API -->
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
                                <!-- Chips will be loaded dynamically from API -->
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
                                        <div class="img-fallback">
                                            <i class="fas fa-industry"></i>
                                        </div>
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
                                                <div class="font-medium" id="product-reference">ASMEB16.5-900-DN15</div>
                                            </div>
                                            <div>
                                                <div class="text-xs md:text-sm text-blue-300 mb-1">Standard</div>
                                                <div class="font-medium" id="product-standard">ASME B16.5</div>
                                            </div>
                                            <div>
                                                <div class="text-xs md:text-sm text-blue-300 mb-1">Nominal Diameter</div>
                                                <div class="font-medium" id="product-diameter">DN15 (1/2")</div>
                                            </div>
                                            <div>
                                                <div class="text-xs md:text-sm text-blue-300 mb-1">Pressure Rating</div>
                                                <div class="font-medium" id="product-pressure">Class 900 (150#)</div>
                                            </div>
                                        </div>
                                        
                                        <div class="mt-4 md:mt-6 pt-4 md:pt-6 border-t border-slate-700">
                                            <button onclick="checkAuthBeforeOrder()" id="product-order-btn" class="w-full py-2.5 md:py-3 bg-blue-600 text-white font-bold rounded-xl hover:bg-blue-700 transition mb-2 md:mb-3 text-sm md:text-base order-button">
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
                                </div>
                            </div>
                            <div class="flex gap-2 md:gap-3 mt-4 md:mt-0">
                                <button onclick="checkAuthBeforeOrder()" class="px-4 md:px-6 py-2.5 md:py-3 bg-gradient-to-r from-blue-600 to-blue-800 text-white rounded-lg font-bold shadow-md hover:from-blue-700 hover:to-blue-900 transition flex items-center gap-2 text-sm md:text-base order-button">
                                    <i class="fas fa-shopping-cart"></i>Order Now
                                </button>
                            </div>
                        </div>
                        <p class="text-slate-600 text-base md:text-xl leading-relaxed mb-6 md:mb-10 max-w-4xl" id="p-desc">
                            Long Weld Neck flanges are specifically designed for pressure vessel applications and high-pressure piping systems. Featuring an extended neck that provides reinforcement and stress distribution, these flanges are ideal for critical applications where reliability is paramount. Our ASME B16.5 Class 900 DN15 model represents precision engineering for demanding industrial environments.
                        </p>
                        
                        <div class="grid md:grid-cols-2 lg:grid-cols-3 gap-4 md:gap-6 mb-8 md:mb-12" id="p-features">
                            <!-- Features will be populated by JavaScript -->
                        </div>
                        
                        <!-- Additional Product Info -->
                        <div class="bg-blue-50 rounded-2xl p-4 md:p-6 mb-6 md:mb-8">
                            <h4 class="text-lg md:text-xl font-bold text-slate-900 mb-3 md:mb-4 flex items-center gap-2">
                                <i class="fas fa-cube text-blue-600"></i>Specifications
                            </h4>
                            <div class="grid md:grid-cols-2 gap-4 md:gap-6">
                                <div>
                                    <h5 class="font-bold text-slate-800 mb-2">Technical Specifications</h5>
                                    <ul class="text-slate-600 space-y-1 text-sm md:text-base" id="product-specs-list">
                                        <!-- Specs will be populated -->
                                    </ul>
                                </div>
                                <div>
                                    <h5 class="font-bold text-slate-800 mb-2">Material Options</h5>
                                    <ul class="text-slate-600 space-y-1 text-sm md:text-base" id="product-materials-list">
                                        <!-- Materials will be populated -->
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
            </div>
        </section>

        <!-- Product Gallery Section -->
        <section id="product-gallery" class="py-12 md:py-24 bg-white reveal">
            <div class="max-w-7xl mx-auto px-4">
                <div class="text-center mb-12 md:mb-16">
                    <span class="text-blue-600 font-bold uppercase tracking-widest text-sm">Product Gallery</span>
                    <h2 class="text-3xl md:text-4xl lg:text-5xl font-bold text-slate-900 mt-2 mb-4">Explore All Products</h2>
                    <p class="text-slate-600 max-w-3xl mx-auto text-base md:text-lg">Click on any product to view detailed specifications and technical information</p>
                </div>
                
                <div class="grid md:grid-cols-2 lg:grid-cols-3 gap-6 md:gap-8" id="gallery-products">
                    <!-- Products will be loaded dynamically from API -->
                </div>
                
                <div class="text-center mt-12 md:mt-16">
                    <button onclick="document.getElementById('products').scrollIntoView({behavior:'smooth'})" class="px-6 md:px-8 py-3 md:py-3.5 bg-gradient-to-r from-blue-600 to-blue-800 text-white font-bold rounded-xl hover:from-blue-700 hover:to-blue-900 transition shadow-lg text-sm md:text-base">
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
                        <ul class="space-y-2 md:space-y-3 text-slate-400 text-sm" id="footer-products">
                            <!-- Products will be loaded dynamically -->
                        </ul>
                    </div>
                    
                    <div>
                        <h4 class="font-bold text-lg mb-4 md:mb-6">Resources</h4>
                        <ul class="space-y-2 md:space-y-3 text-slate-400 text-sm">
                            <li><a href="#" onclick="document.getElementById('specifications').scrollIntoView({behavior:'smooth'}); return false;" class="hover:text-white transition">Technical Specifications</a></li>
                            <li><a href="#" onclick="document.getElementById('about').scrollIntoView({behavior:'smooth'}); return false;" class="hover:text-white transition">Material Selection Guide</a></li>
                            <li><a href="#" onclick="showAllProducts(); return false;" class="hover:text-white transition">Product Catalog</a></li>
                        </ul>
                    </div>
                    
                    <div>
                        <h4 class="font-bold text-lg mb-4 md:mb-6">Ordering Process</h4>
                        <ul class="space-y-2 md:space-y-3 text-slate-400 text-sm">
                            <li><a href="#" onclick="checkAuthBeforeOrder(); return false;" class="hover:text-white transition">Connect with Suppliers</a></li>
                            <li><a href="#" onclick="openTrackingModal(); return false;" class="hover:text-white transition">Track Order</a></li>
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
        // ========== API CONFIGURATION ==========
        // FIXED: Correct backend URL without extra backslash
const API_BASE_URL = 'https://finalbackend-production-5b1a.up.railway.app/api';
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
            authToken: null
        };

        // ========== API HELPER FUNCTIONS ==========
        async function apiRequest(endpoint, options = {}) {
        const url = endpoint.startsWith('/') ? `${API_BASE_URL}${endpoint}` : `${API_BASE_URL}/${endpoint}`;
        const headers = {
            'Content-Type': 'application/json',
            ...options.headers
        };
        
        if (appState.authToken) {
            headers['Authorization'] = `Bearer ${appState.authToken}`;
        }
        
        try {
            const response = await fetch(url, { ...options, headers });
            const contentType = response.headers.get('content-type');
            
            if (contentType && contentType.includes('application/json')) {
                const data = await response.json();
                if (!response.ok) throw new Error(data.message || 'API request failed');
                return data;
            } else {
                const text = await response.text();
                if (!response.ok) throw new Error(text || 'API request failed');
                return { message: text };
            }
        } catch (error) {
            console.error('API Error:', error);
            throw error;
        }
    }


        // ========== PRODUCT API FUNCTIONS ==========
async function getProducts() {
    // Return detailed products from reference images
    return [
        { 
            id: '1', 
            key: 'ms-plate', 
            name: 'MS Plate Flange', 
            description: 'Mild Steel Plate Flanges suitable for low to medium pressure applications. Manufactured from high-quality carbon steel plates with precision machining.', 
            price: 12500,
            stock: 100,
            unit: 'pieces',
            material: 'Carbon Steel (IS 2062, A36)',
            supplierId: 'sup1',
            standard: 'ASME B16.5 / IS 6392',
            diameter: 'DN15 to DN600 (1/2" to 24")',
            pressure: 'Class 150 to Class 900',
            features: [
                'Precision machined from high-quality MS plates',
                'Accurate bolt hole drilling as per standards',
                'Suitable for various industrial applications',
                'Cost-effective solution for piping systems'
            ],
            specs: 'Available in raised face, flat face, and ring-type joint configurations. Face finish 125-250 AARH.'
        },
        { 
            id: '2', 
            key: 'forged', 
            name: 'Forged Flange', 
            description: 'High-strength forged flanges manufactured through hot forging process for superior grain structure and mechanical properties.', 
            price: 18500,
            stock: 75,
            unit: 'pieces',
            material: 'Carbon Steel (A105), Alloy Steel (F11, F22), Stainless Steel (F304, F316)',
            supplierId: 'sup1',
            standard: 'ASME B16.5, ASME B16.47, API 6A',
            diameter: 'DN15 to DN600 (1/2" to 24")',
            pressure: 'Class 150 to Class 2500',
            features: [
                'Superior grain structure from hot forging',
                'Enhanced mechanical properties',
                'Ultrasonic tested for internal soundness',
                'Full material traceability available'
            ],
            specs: 'Manufactured through hot forging process with controlled grain flow. Heat treatment and NDT available on request.'
        },
        { 
            id: '3', 
            key: 'special-ring', 
            name: 'Special / Ring as per Drawing', 
            description: 'Custom flanges and rings manufactured as per customer drawings and specifications. Ideal for special applications and non-standard requirements.', 
            price: 22500,
            stock: 50,
            unit: 'pieces',
            material: 'Carbon Steel, Stainless Steel, Alloy Steel, Duplex, Super Duplex, Monel, Inconel, Hastelloy',
            supplierId: 'sup2',
            standard: 'As per customer specifications / drawings',
            diameter: 'As per drawing',
            pressure: 'As per design requirements',
            features: [
                'Manufactured exactly to customer drawings',
                'Wide material selection available',
                'Short lead times for custom orders',
                'In-house engineering support for design optimization'
            ],
            specs: 'Custom manufactured flanges and rings as per customer drawings. Available in all material grades with full documentation.'
        },
        { 
            id: '4', 
            key: 'weld-neck', 
            name: 'Weld Neck Flanges', 
            description: 'Standard weld neck flanges with tapered hub for high-stress applications. Ideal for high-pressure and high-temperature services.', 
            price: 14500,
            stock: 120,
            unit: 'pieces',
            material: 'Carbon Steel (A105), Stainless Steel (F304, F316), Alloy Steel',
            supplierId: 'sup1',
            standard: 'ASME B16.5, EN 1092-1, DIN',
            diameter: 'DN15 to DN600 (1/2" to 24")',
            pressure: 'Class 150 to Class 2500',
            features: [
                'Tapered hub for stress distribution',
                'Bore matching to pipe inside diameter',
                'Excellent for cyclic loading conditions',
                'Radiographic inspection available'
            ],
            specs: 'Long weld neck and standard weld neck configurations available. Full penetration weld preparation. Available in all pressure classes.'
        },
        { 
            id: '5', 
            key: 'pipes-fitting-bw-sw', 
            name: 'Pipes Fitting (B/W & S/W)', 
            description: 'Comprehensive range of pipe fittings including Butt Weld and Socket Weld fittings. Hydrolick products, Elbow, Bend, Tee, Reducer, Cap, Coupling, Union.', 
            price: 9500,
            stock: 200,
            unit: 'pieces',
            material: 'Carbon Steel, Stainless Steel, Alloy Steel',
            supplierId: 'sup2',
            standard: 'ASME B16.9, ASME B16.11, MSS SP-75',
            diameter: '1/2" to 48"',
            pressure: 'SCH 10 to SCH 160',
            features: [
                'Complete range of butt weld fittings',
                'Socket weld fittings for small bore piping',
                'Hydrolick products for hydraulic systems',
                'Elbow, Bend, Tee, Reducer, Cap, Coupling, Union'
            ],
            specs: 'Comprehensive range of pipe fittings for all industrial applications. Available in seamless and welded construction. Full material certification.'
        },
        { 
            id: '6', 
            key: 'pipes', 
            name: 'Pipes - Round & Square', 
            description: 'High-quality round and square pipes for structural and piping applications. Available in various sizes, schedules, and material grades.', 
            price: 8500,
            stock: 300,
            unit: 'meters',
            material: 'Carbon Steel, Stainless Steel, MS, GI',
            supplierId: 'sup2',
            standard: 'ASTM A53, ASTM A106, API 5L, IS 1239, IS 1161',
            diameter: '1/2" to 24" (Round), Various sizes (Square)',
            pressure: 'SCH 10 to SCH 160',
            features: [
                'Round pipes for pressure and structural applications',
                'Square pipes for structural and architectural use',
                'Seamless and ERW options available',
                'Cut to length service available'
            ],
            specs: 'Round pipes available in seamless and welded construction. Square pipes in various sizes and thicknesses. Test certificates available.'
        }
    ];
}


        // FIXED: Sample products for demo when backend is unavailable
      function getSampleProducts() {
        return [
            { id: '1', key: 'ms-plate', name: 'MS Plate Flange', description: 'Mild Steel Plate Flanges', price: 12500, stock: 100, unit: 'pieces', material: 'Carbon Steel', supplierId: 'sup1' },
            { id: '2', key: 'forged', name: 'Forged Flange', description: 'High-strength forged flanges', price: 18500, stock: 75, unit: 'pieces', material: 'Carbon Steel', supplierId: 'sup1' },
            { id: '3', key: 'special-ring', name: 'Special / Ring as per Drawing', description: 'Custom flanges as per customer drawing', price: 22500, stock: 50, unit: 'pieces', material: 'Carbon Steel', supplierId: 'sup2' },
            { id: '4', key: 'weld-neck', name: 'Weld Neck Flanges', description: 'Standard weld neck flanges', price: 14500, stock: 120, unit: 'pieces', material: 'Carbon Steel', supplierId: 'sup1' },
            { id: '5', key: 'pipes-fitting-bw-sw', name: 'Pipes Fitting (B/W & S/W)', description: 'Elbow, Bend, Tee, Reducer, Cap, Coupling, Union', price: 9500, stock: 200, unit: 'pieces', material: 'Carbon Steel', supplierId: 'sup2' },
            { id: '6', key: 'pipes', name: 'Pipes - Round & Square', description: 'Round & Square Pipes for structural applications', price: 8500, stock: 300, unit: 'meters', material: 'Carbon Steel', supplierId: 'sup2' }
        ];
    }

        async function getSupplierProducts(supplierId) {
            try {
                const data = await apiRequest(`/products/supplier/${supplierId}`);
                return data || [];
            } catch (error) {
                console.error('Failed to fetch supplier products:', error);
                return getSampleProducts().filter(p => p.supplierId === supplierId);
            }
        }

        async function saveProduct(product) {
            try {
                const method = product.id ? 'PUT' : 'POST';
                const endpoint = product.id ? `/products/${product.id}` : '/products';
                
                const data = await apiRequest(endpoint, {
                    method: method,
                    body: JSON.stringify(product)
                });
                
                return data;
            } catch (error) {
                console.error('Failed to save product:', error);
                throw error;
            }
        }

        async function deleteProduct(productId) {
            try {
                await apiRequest(`/products/${productId}`, {
                    method: 'DELETE'
                });
            } catch (error) {
                console.error('Failed to delete product:', error);
                throw error;
            }
        }

        // ========== ORDER API FUNCTIONS ==========
        async function getOrders() {
            try {
                const data = await apiRequest('/orders');
                return data || [];
            } catch (error) {
                console.error('Failed to fetch orders:', error);
                return [];
            }
        }

        async function saveOrder(order) {
            try {
                const data = await apiRequest('/orders', {
                    method: 'POST',
                    body: JSON.stringify(order)
                });
                return data;
            } catch (error) {
                console.error('Failed to save order:', error);
                throw error;
            }
        }

        async function getSupplierOrders(supplierId) {
            try {
                const data = await apiRequest(`/orders/supplier/${supplierId}`);
                return data || [];
            } catch (error) {
                console.error('Failed to fetch supplier orders:', error);
                return [];
            }
        }

        async function getCustomerOrders(customerEmail) {
            try {
                const data = await apiRequest(`/orders/customer/${encodeURIComponent(customerEmail)}`);
                return data || [];
            } catch (error) {
                console.error('Failed to fetch customer orders:', error);
                return [];
            }
        }

        async function updateOrderStatus(orderId, status) {
            try {
                const data = await apiRequest(`/orders/${orderId}/status`, {
                    method: 'PUT',
                    body: JSON.stringify({ status })
                });
                return data;
            } catch (error) {
                console.error('Failed to update order status:', error);
                throw error;
            }
        }

        // ========== AUTHENTICATION FUNCTIONS ==========
        
        function initializeAuth() {
        const token = localStorage.getItem('authToken');
        const userData = localStorage.getItem('userData');
        
        if (token && userData) {
            try {
                appState.currentUser = JSON.parse(userData);
                appState.isAuthenticated = true;
                appState.currentUserType = appState.currentUser.userType || appState.currentUser.type || 'partner';
                appState.isSupplier = (appState.currentUser.userType === 'supplier' || appState.currentUser.type === 'supplier');
                appState.authToken = token;
                
                document.body.classList.add('authenticated');
                document.body.classList.remove('visitor-mode', 'require-auth');
                document.getElementById('auth-overlay').style.display = 'none';
                
                updateUIAfterAuth();
                fetchAndUpdateProducts();
            } catch (e) {
                console.error('Failed to parse user data:', e);
                clearAuth();
            }
        } else {
            clearAuth(true);
            fetchAndUpdateProducts();
        }
    }
  function clearAuth(keepVisitorMode = false) {
        localStorage.removeItem('authToken');
        localStorage.removeItem('userData');
        
        appState.isAuthenticated = false;
        appState.currentUser = { type: 'visitor' };
        appState.currentUserType = 'visitor';
        appState.isSupplier = false;
        appState.authToken = null;
        
        if (keepVisitorMode) {
            document.body.classList.add('visitor-mode');
            document.body.classList.remove('authenticated', 'require-auth');
            document.getElementById('auth-overlay').style.display = 'none';
        } else {
            document.body.classList.add('require-auth');
            document.body.classList.remove('authenticated', 'visitor-mode');
            document.getElementById('auth-overlay').style.display = 'flex';
        }
        
        updateUIAfterAuth();
    }
         async function loginUser(event) {
        event.preventDefault();
        clearValidationErrors();
        
        const email = document.getElementById('login-email').value;
        const password = document.getElementById('login-password').value;

        if (!validateEmail(email)) {
            showFieldError('login-email', 'Please enter a valid email address');
            return;
        }
        
        if (!validateRequired(password)) {
            showFieldError('login-password', 'Password is required');
            return;
        }

        showLoading('Logging in...');

        try {
            const response = await fetch(`${API_BASE_URL}/auth/login`, {
                method: 'POST',
                headers: { 'Content-Type': 'application/json' },
                body: JSON.stringify({ email, password, userType: appState.currentUserType || 'partner' })
            });

            const data = await response.json();
            console.log('Login response:', data);

            if (response.ok && data.success) {
                const token = data.data?.token || data.token;
                const user = data.data?.user || data.user || data.data;
                
                if (!token || !user) throw new Error('Invalid response');

                localStorage.setItem('authToken', token);
                localStorage.setItem('userData', JSON.stringify(user));
                
                appState.isAuthenticated = true;
                appState.currentUser = user;
                appState.authToken = token;
                appState.isSupplier = (user.userType === 'supplier' || user.type === 'supplier');
                
                document.body.classList.add('authenticated');
                document.body.classList.remove('visitor-mode', 'require-auth');
                document.getElementById('auth-overlay').style.display = 'none';
                
                updateUIAfterAuth();
                await fetchAndUpdateProducts();
                showSuccess('login-error-container', 'Login successful!');
            } else {
                throw new Error(data.message || 'Login failed');
            }
        } catch (error) {
            console.error('Login error:', error);
            
            // Demo login
            if (email === 'partner@test.com' && password === 'password') {
                const demoUser = { id: 'demo1', email, firstName: 'Demo', lastName: 'Partner', company: 'Demo Company', userType: 'partner' };
                localStorage.setItem('authToken', 'demo-token');
                localStorage.setItem('userData', JSON.stringify(demoUser));
                appState.isAuthenticated = true;
                appState.currentUser = demoUser;
                appState.isSupplier = false;
                appState.authToken = 'demo-token';
                document.body.classList.add('authenticated');
                document.body.classList.remove('visitor-mode', 'require-auth');
                document.getElementById('auth-overlay').style.display = 'none';
                updateUIAfterAuth();
                await fetchAndUpdateProducts();
                showSuccess('login-error-container', 'Demo login successful!');
            } else if (email === 'supplier@test.com' && password === 'password') {
                const demoUser = { id: 'sup1', email, firstName: 'Demo', lastName: 'Supplier', company: 'Demo Supplier', userType: 'supplier' };
                localStorage.setItem('authToken', 'demo-token');
                localStorage.setItem('userData', JSON.stringify(demoUser));
                appState.isAuthenticated = true;
                appState.currentUser = demoUser;
                appState.isSupplier = true;
                appState.authToken = 'demo-token';
                document.body.classList.add('authenticated');
                document.body.classList.remove('visitor-mode', 'require-auth');
                document.getElementById('auth-overlay').style.display = 'none';
                updateUIAfterAuth();
                await fetchAndUpdateProducts();
                showSuccess('login-error-container', 'Demo login successful!');
            } else {
                showError('login-error-container', error.message || 'Login failed');
            }
        } finally {
            hideLoading();
        }
    }

  async function signupUser(event) {
        event.preventDefault();
        clearValidationErrors();
        
        const firstName = document.getElementById('signup-firstname')?.value || '';
        const lastName = document.getElementById('signup-lastname')?.value || '';
        const email = document.getElementById('signup-email')?.value || '';
        const password = document.getElementById('signup-password')?.value || '';
        const company = document.getElementById('signup-company')?.value || '';
        const industry = document.getElementById('signup-industry')?.value || '';
        
        const accountTypeRadios = document.querySelectorAll('input[name="signup-type"]');
        let accountType = 'partner';
        for (const radio of accountTypeRadios) if (radio.checked) accountType = radio.value;

        if (!validateRequired(firstName)) { showFieldError('signup-firstname', 'First name required'); return; }
        if (!validateRequired(lastName)) { showFieldError('signup-lastname', 'Last name required'); return; }
        if (!validateEmail(email)) { showFieldError('signup-email', 'Valid email required'); return; }
        if (!validateRequired(password) || password.length < 6) { showFieldError('signup-password', 'Password min 6 chars'); return; }
        if (!validateRequired(company)) { showFieldError('signup-company', 'Company required'); return; }

        showLoading('Creating account...');

        try {
            const response = await fetch(`${API_BASE_URL}/auth/register`, {
                method: 'POST',
                headers: { 'Content-Type': 'application/json' },
                body: JSON.stringify({ firstName, lastName, email, password, company, industry, userType: accountType })
            });

            const data = await response.json();
            console.log('Signup response:', data);

            if (response.ok) {
                showSuccess('signup-error-container', '✅ Account created! Please login.');
                document.getElementById('signup-firstname').value = '';
                document.getElementById('signup-lastname').value = '';
                document.getElementById('signup-email').value = '';
                document.getElementById('signup-password').value = '';
                document.getElementById('signup-company').value = '';
                setTimeout(() => toggleAuthView('login'), 2000);
            } else {
                showError('signup-error-container', data.message || 'Registration failed');
            }
        } catch (error) {
            console.error('Registration error:', error);
            showError('signup-error-container', error.message);
        } finally {
            hideLoading();
        }
    }


    function handleVisitor(e) {
        if(e) e.preventDefault();
        localStorage.removeItem('authToken');
        localStorage.removeItem('userData');
        appState.isAuthenticated = false;
        appState.currentUser = { type: 'visitor' };
        appState.currentUserType = 'visitor';
        appState.isSupplier = false;
        appState.authToken = null;
        document.body.classList.add('visitor-mode');
        document.body.classList.remove('authenticated', 'require-auth');
        document.getElementById('auth-overlay').style.display = 'none';
        updateUIAfterAuth();
        fetchAndUpdateProducts();
        showSuccess('login-error-container', 'Continuing as visitor');
    }
      function logout(message = 'Logged out successfully') {
        clearAuth(false);
        closeDashboard();
        closeOrderModal();
        closeTrackingModal();
        closeChat();
        fetchAndUpdateProducts();
        showSuccess('login-error-container', message);
    }

        // ========== PRODUCT FETCHING AND UPDATING ==========
        
       async function fetchAndUpdateProducts() {
        try {
            const products = await getProducts();
            updateProductChips(products);
            updateProductGallery(products);
            updateProductSelect(products);
            if (products.length > 0) updateCurrentProduct(appState.currentProductKey, products);
            updateFooterProducts(products);
            if (appState.isAuthenticated && appState.isSupplier) updateDashboardData();
        } catch (error) {
            console.error('Failed to fetch products:', error);
        }
    }

      
    function updateProductChips(products) {
        const chipsContainer = document.getElementById('suggestion-bar');
        if (!chipsContainer) return;
        if (products.length === 0) {
            chipsContainer.innerHTML = '<div class="text-slate-500">No products</div>';
            return;
        }
        chipsContainer.innerHTML = products.map(p => `
            <div onclick="updateProduct('${p.key}')" id="chip-${p.key}" class="flange-chip px-3 md:px-5 py-2 md:py-2.5 rounded-full border-2 border-slate-200 bg-white text-xs md:text-sm font-semibold flex items-center gap-2">
                <i class="fas fa-fire"></i>${p.name}
            </div>
        `).join('');
    }
  function updateProductGallery(products) {
        const gallery = document.getElementById('gallery-products');
        if (gallery) {
            if (products.length === 0) {
                gallery.innerHTML = '<div class="col-span-full text-center py-8">No products</div>';
            } else {
                gallery.innerHTML = products.map(p => `
                    <div class="gallery-product-card bg-slate-50 rounded-3xl overflow-hidden border border-slate-200">
                        <div class="p-4 md:p-6">
                            <h4 class="font-bold text-lg text-slate-900">${p.name}</h4>
                            <p class="text-slate-600 mb-3 text-sm">${p.description?.substring(0, 80)}...</p>
                            <div class="flex gap-2">
                                <button onclick="updateProduct('${p.key}')" class="flex-1 py-2 bg-blue-600 text-white rounded-lg text-xs">View</button>
                                <button onclick="checkAuthBeforeOrder('${p.key}')" class="flex-1 py-2 bg-slate-200 rounded-lg text-xs order-button">Order</button>
                            </div>
                        </div>
                    </div>
                `).join('');
            }
        }
    }

function updateProductSelect(products) {
    const select = document.getElementById('order-product');
    if (!select) {
        console.error('Product select not found');
        return;
    }
    
    console.log('Updating product select');
    select.innerHTML = '<option value="">Select Product</option>';
    
    if (products && products.length > 0) {
        products.forEach(p => {
            const option = document.createElement('option');
            option.value = p.key;
            option.textContent = p.name;
            select.appendChild(option);
        });
        console.log('Products loaded:', products.length);
    } else {
        select.innerHTML = '<option value="">No products available</option>';
    }
}


        function updateFooterProducts(products) {
        const footer = document.getElementById('footer-products');
        if (!footer) return;
        if (products.length === 0) {
            footer.innerHTML = '<li>No products</li>';
        } else {
            footer.innerHTML = products.slice(0, 5).map(p => `
                <li><a href="#" onclick="updateProduct('${p.key}'); return false;" class="hover:text-white">${p.name}</a></li>
            `).join('');
        }
    }

  

    function updateCurrentProduct(key, products) {
        const product = products.find(p => p.key === key) || products[0];
        if (!product) return;
        
        appState.currentProductKey = product.key;
        
        document.querySelectorAll('.flange-chip').forEach(c => c.classList.remove('active'));
        const activeChip = document.getElementById(`chip-${product.key}`);
        if (activeChip) activeChip.classList.add('active');
        
        document.getElementById('current-product-name').textContent = product.name;
        document.getElementById('p-title').innerText = product.name;
        document.getElementById('p-desc').innerText = product.description || 'No description';
        document.getElementById('product-reference').textContent = `${product.key}-${product.id}`;
        document.getElementById('product-standard').textContent = product.standard || 'ASME / EN / Custom';
        document.getElementById('product-diameter').textContent = product.diameter || 'Various sizes';
        document.getElementById('product-pressure').textContent = product.pressure || 'Class 150 to 2500';
        
        // Update features
        const featuresContainer = document.getElementById('p-features');
        if (featuresContainer && product.features) {
            featuresContainer.innerHTML = product.features.map(f => `
                <div class="feature-card p-4 rounded-xl">
                    <i class="fas fa-check-circle text-blue-600 mb-2"></i>
                    <p class="text-sm">${f}</p>
                </div>
            `).join('');
        }
        
        // Update specs list
        const specsList = document.getElementById('product-specs-list');
        if (specsList) {
            specsList.innerHTML = `
                <li><strong>Standard:</strong> ${product.standard}</li>
                <li><strong>Diameter:</strong> ${product.diameter}</li>
                <li><strong>Pressure:</strong> ${product.pressure}</li>
                <li><strong>Specifications:</strong> ${product.specs || 'As per standards'}</li>
            `;
        }
        
        // Update materials list
        const materialsList = document.getElementById('product-materials-list');
        if (materialsList) {
            materialsList.innerHTML = `
                <li>${product.material}</li>
                <li>Full material traceability</li>
                <li>Test certificates available</li>
                <li>Custom materials on request</li>
            `;
        }
    }
        // ========== PRODUCT MANAGEMENT (Supplier Only) ==========
        
        function showAddProductForm() {
            if (!appState.isAuthenticated || !appState.isSupplier) {
                showError('login-error-container', 'Only suppliers can add products.');
                return;
            }
            
            document.getElementById('product-form-title').textContent = 'Add New Product';
            document.getElementById('product-form').reset();
            document.getElementById('product-form-container').classList.remove('hidden');
        }

        function cancelProductForm() {
            document.getElementById('product-form-container').classList.add('hidden');
        }

        async function saveProduct(event) {
            event.preventDefault();
            
            if (!appState.isAuthenticated || !appState.isSupplier) {
                showError('dashboard-inventory .error-message', 'Only suppliers can add products.');
                return;
            }
            
            showLoading('Saving product...');
            
            try {
                const product = {
                    key: document.getElementById('product-key').value.toLowerCase().replace(/\s+/g, '-'),
                    name: document.getElementById('product-name').value,
                    description: document.getElementById('product-description').value || 'No description provided',
                    price: parseFloat(document.getElementById('product-price').value),
                    stock: parseInt(document.getElementById('product-stock').value),
                    unit: document.getElementById('product-unit').value,
                    category: document.getElementById('product-category').value,
                    material: document.getElementById('product-material').value || 'Various',
                    specs: document.getElementById('product-specs').value || 'Standard specifications',
                    features: [
                        `${document.getElementById('product-name').value} - High quality`,
                        "Precision manufactured",
                        "Industry standard compliance",
                        "Full traceability"
                    ],
                    standard: "ASME / EN / Custom",
                    diameter: "Various sizes available",
                    pressure: "As per specification",
                    supplierId: appState.currentUser.id
                };
                
                await saveProduct(product);
                cancelProductForm();
                await fetchAndUpdateProducts();
                await updateDashboardData();
                
                showSuccess('dashboard-inventory .success-message', 'Product added successfully!');
            } catch (error) {
                showError('dashboard-inventory .error-message', error.message);
            } finally {
                hideLoading();
            }
        }

        async function editProduct(productId) {
            if (!appState.isAuthenticated || !appState.isSupplier) return;
            
            try {
                const products = await getSupplierProducts(appState.currentUser.id);
                const product = products.find(p => p.id === productId);
                if (!product) return;
                
                document.getElementById('product-form-title').textContent = 'Edit Product';
                document.getElementById('product-key').value = product.key;
                document.getElementById('product-name').value = product.name;
                document.getElementById('product-description').value = product.description || '';
                document.getElementById('product-price').value = product.price || '';
                document.getElementById('product-stock').value = product.stock || '';
                document.getElementById('product-unit').value = product.unit || 'pieces';
                document.getElementById('product-category').value = product.category || 'flanges';
                document.getElementById('product-material').value = product.material || '';
                document.getElementById('product-specs').value = product.specs || '';
                
                document.getElementById('product-form-container').classList.remove('hidden');
            } catch (error) {
                console.error('Failed to load product for editing:', error);
            }
        }

        async function deleteProduct(productId) {
            if (!appState.isAuthenticated || !appState.isSupplier) return;
            
            if (confirm('Are you sure you want to delete this product?')) {
                showLoading('Deleting product...');
                try {
                    await deleteProduct(productId);
                    await fetchAndUpdateProducts();
                    await updateDashboardData();
                    showSuccess('dashboard-inventory .success-message', 'Product deleted successfully!');
                } catch (error) {
                    showError('dashboard-inventory .error-message', error.message);
                } finally {
                    hideLoading();
                }
            }
        }

        // ========== DASHBOARD FUNCTIONS (Supplier Only) ==========
        
        function openDashboard() {
            if (!appState.isAuthenticated || !appState.isSupplier) {
                showError('login-error-container', 'Only suppliers can access the dashboard.');
                openAuthModal();
                return;
            }
            
            document.getElementById('dashboard-modal').classList.remove('hidden');
            document.body.style.overflow = 'hidden';
            updateDashboardData();
        }

        function closeDashboard() {
            document.getElementById('dashboard-modal').classList.add('hidden');
            document.body.style.overflow = 'auto';
        }

        function switchDashboardTab(tabName) {
            document.querySelectorAll('#dashboard-modal .tab-button').forEach(btn => btn.classList.remove('active'));
            document.querySelectorAll('#dashboard-modal .tab-content').forEach(content => {
                content.classList.remove('active');
                content.classList.add('hidden');
            });
            
            const activeBtn = Array.from(document.querySelectorAll('#dashboard-modal .tab-button')).find(
                btn => btn.textContent.toLowerCase().includes(tabName)
            );
            if (activeBtn) activeBtn.classList.add('active');
            
            document.getElementById(`dashboard-${tabName}`).classList.add('active');
            document.getElementById(`dashboard-${tabName}`).classList.remove('hidden');
        }

        async function updateDashboardData() {
            if (!appState.isAuthenticated || !appState.isSupplier) return;
            
            try {
                const supplierId = appState.currentUser.id;
                const products = await getSupplierProducts(supplierId);
                const orders = await getSupplierOrders(supplierId);
                const customers = [...new Set(orders.map(o => o.customerEmail))];
                
                const totalRevenue = orders.filter(o => o.status === 'completed').reduce((sum, o) => sum + (o.amount || 0), 0);
                const pendingOrders = orders.filter(o => o.status === 'pending').length;
                const lowStock = products.filter(p => (p.stock || 0) < 10).length;
                const outOfStock = products.filter(p => (p.stock || 0) === 0).length;
                
                document.getElementById('dashboard-total-revenue').textContent = `₹${totalRevenue.toLocaleString()}`;
                document.getElementById('dashboard-incoming-orders').textContent = orders.length;
                document.getElementById('dashboard-pending-orders').textContent = pendingOrders;
                document.getElementById('dashboard-total-products').textContent = products.length;
                document.getElementById('dashboard-low-stock').textContent = lowStock;
                document.getElementById('dashboard-out-of-stock').textContent = outOfStock;
                document.getElementById('dashboard-total-customers').textContent = customers.length;
                document.getElementById('dashboard-product-count').textContent = products.length;
                document.getElementById('dashboard-customer-count').textContent = customers.length;
                document.getElementById('dashboard-active-customers').textContent = customers.length;
                document.getElementById('dashboard-total-orders').textContent = orders.length;
                
                // Update recent orders
                const recentOrdersEl = document.getElementById('dashboard-recent-orders');
                if (recentOrdersEl) {
                    if (orders.length === 0) {
                        recentOrdersEl.innerHTML = '<div class="text-center py-4 text-slate-500">No orders yet</div>';
                    } else {
                        recentOrdersEl.innerHTML = orders.slice(0, 4).map(o => `
                            <div class="flex items-center justify-between p-3 bg-slate-50 rounded-lg">
                                <div>
                                    <div class="font-medium">#${o.id}</div>
                                    <div class="text-sm text-slate-500">${o.productName}</div>
                                </div>
                                <div class="text-right">
                                    <div class="font-medium">₹${(o.amount || 0).toLocaleString()}</div>
                                    <span class="badge badge-${o.status === 'pending' ? 'warning' : o.status === 'processing' ? 'info' : o.status === 'completed' ? 'success' : 'danger'}">${o.status}</span>
                                </div>
                            </div>
                        `).join('');
                    }
                }
                
                // Update orders table
                const ordersTable = document.getElementById('orders-table-body');
                if (ordersTable) {
                    if (orders.length === 0) {
                        ordersTable.innerHTML = '<tr><td colspan="8" class="text-center py-8 text-slate-500">No orders found</td></tr>';
                    } else {
                        ordersTable.innerHTML = orders.map(o => `
                            <tr>
                                <td class="font-medium">#${o.id}</td>
                                <td>${o.customerName}</td>
                                <td>${o.productName}</td>
                                <td>${o.quantity}</td>
                                <td class="font-bold">₹${(o.amount || 0).toLocaleString()}</td>
                                <td><span class="badge badge-${o.status === 'pending' ? 'warning' : o.status === 'processing' ? 'info' : o.status === 'completed' ? 'success' : 'danger'}">${o.status}</span></td>
                                <td>${o.date ? new Date(o.date).toLocaleDateString() : 'N/A'}</td>
                                <td>
                                    <button onclick="updateOrderStatus('${o.id}', 'processing')" class="action-button edit mr-2">
                                        <i class="fas fa-check"></i>
                                    </button>
                                    <button onclick="updateOrderStatus('${o.id}', 'completed')" class="action-button approve mr-2">
                                        <i class="fas fa-check-double"></i>
                                    </button>
                                    <button onclick="updateOrderStatus('${o.id}', 'cancelled')" class="action-button reject">
                                        <i class="fas fa-times"></i>
                                    </button>
                                </td>
                            </tr>
                        `).join('');
                    }
                }
                
                // Update products table
                const productsTable = document.getElementById('products-table-body');
                if (productsTable) {
                    if (products.length === 0) {
                        productsTable.innerHTML = '<tr><td colspan="8" class="text-center py-8 text-slate-500">No products added yet. Click "Add New Product" to get started.</td></tr>';
                    } else {
                        productsTable.innerHTML = products.map(p => `
                            <tr>
                                <td class="font-medium">${p.name}</td>
                                <td>${p.key}</td>
                                <td>${p.category || 'N/A'}</td>
                                <td>₹${p.price || 'N/A'}</td>
                                <td>${p.stock || 0}</td>
                                <td>${p.unit || 'pieces'}</td>
                                <td><span class="badge badge-${p.stock === 0 ? 'danger' : p.stock < 10 ? 'warning' : 'success'}">${p.stock === 0 ? 'Out of Stock' : p.stock < 10 ? 'Low Stock' : 'In Stock'}</span></td>
                                <td>
                                    <button onclick="editProduct('${p.id}')" class="action-button edit mr-2">
                                        <i class="fas fa-edit"></i>
                                    </button>
                                    <button onclick="deleteProduct('${p.id}')" class="action-button delete">
                                        <i class="fas fa-trash"></i>
                                    </button>
                                </td>
                            </tr>
                        `).join('');
                    }
                }
                
                // Update customers table
                const customersTable = document.getElementById('customers-table-body');
                if (customersTable) {
                    const customerData = customers.map(email => {
                        const customerOrders = orders.filter(o => o.customerEmail === email);
                        const totalSpent = customerOrders.reduce((sum, o) => sum + (o.amount || 0), 0);
                        const lastOrder = customerOrders.sort((a, b) => new Date(b.date || 0) - new Date(a.date || 0))[0];
                        
                        return {
                            email,
                            name: customerOrders[0]?.customerName || email.split('@')[0],
                            company: customerOrders[0]?.customerCompany || 'Unknown',
                            orderCount: customerOrders.length,
                            totalSpent,
                            lastOrderDate: lastOrder && lastOrder.date ? new Date(lastOrder.date).toLocaleDateString() : 'Never'
                        };
                    });
                    
                    if (customerData.length === 0) {
                        customersTable.innerHTML = '<tr><td colspan="7" class="text-center py-8 text-slate-500">No customers yet</td></tr>';
                    } else {
                        customersTable.innerHTML = customerData.map(c => `
                            <tr>
                                <td class="font-medium">${c.name}</td>
                                <td>${c.company}</td>
                                <td>${c.email}</td>
                                <td>${c.orderCount}</td>
                                <td class="font-bold">₹${c.totalSpent.toLocaleString()}</td>
                                <td>${c.lastOrderDate}</td>
                                <td>
                                    <button onclick="contactCustomer('${c.email}')" class="action-button edit">
                                        <i class="fas fa-envelope"></i>
                                    </button>
                                </td>
                            </tr>
                        `).join('');
                    }
                }
            } catch (error) {
                console.error('Failed to update dashboard:', error);
            }
        }

        async function filterOrders() {
            await updateDashboardData();
        }

        function contactCustomer(email) {
            window.location.href = `mailto:${email}`;
        }

        async function updateOrderStatus(orderId, status) {
            try {
                await updateOrderStatus(orderId, status);
                await updateDashboardData();
                showSuccess('dashboard-orders .success-message', `Order status updated to ${status}`);
            } catch (error) {
                showError('dashboard-orders .error-message', error.message);
            }
        }

        // ========== ORDER FUNCTIONS (Partners Only) ==========
        
        function checkAuthBeforeOrder(productKey = null) {
        const userType = appState.currentUser?.userType || appState.currentUser?.type || 'visitor';
        
        if (!appState.isAuthenticated || userType === 'visitor') {
            showError('login-error-container', 'Please login to place orders.');
            openAuthModal();
            return;
        }
        
        if (userType === 'supplier') {
            showError('login-error-container', 'Suppliers cannot place orders.');
            return;
        }
        
        if (productKey) openOrderModalWithProduct(productKey);
        else openOrderModal();
    }
function openOrderModal() {
    if (!appState.isAuthenticated || appState.isSupplier) {
        checkAuthBeforeOrder();
        return;
    }
    
    console.log('Opening order modal');
    document.getElementById('order-modal').classList.remove('hidden');
    document.body.style.overflow = 'hidden';
    resetOrderSteps();
    
    // Directly load products
    getProducts().then(products => {
        updateProductSelect(products);
    });
}

     
    function openOrderModalWithProduct(productKey) {
        openOrderModal();
        document.getElementById('order-product').value = productKey;
        loadSuppliersForProduct(productKey);
    }

        function closeOrderModal() {
        document.getElementById('order-modal').classList.add('hidden');
        document.body.style.overflow = 'auto';
        appState.selectedSupplier = null;
    }
  function resetOrderSteps() {
        appState.currentOrderStep = 1;
        updateStepIndicators();
        for (let i = 1; i <= 5; i++) {
            document.getElementById(`order-step-${i}`)?.classList.add('hidden');
        }
        document.getElementById('order-step-1').classList.remove('hidden');
        appState.selectedSupplier = null;
        document.getElementById('selected-supplier-display').textContent = 'Not selected';
        clearValidationErrors();
    }

    function updateStepIndicators() {
        const progress = document.getElementById('step-progress');
        progress.style.width = `${(appState.currentOrderStep - 1) * 25}%`;
        
        for (let i = 1; i <= 4; i++) {
            const indicator = document.getElementById(`step-indicator-${i}`);
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

        function validateStep1() {
        clearValidationErrors();
        const product = document.getElementById('order-product').value;
        const quantity = document.getElementById('order-quantity').value;
        const size = document.getElementById('order-size').value;
        const material = document.getElementById('order-material').value;
        
        if (!product) { showFieldError('order-product', 'Select product'); return false; }
        if (!quantity || quantity < 1) { showFieldError('order-quantity', 'Valid quantity'); return false; }
        if (!size) { showFieldError('order-size', 'Enter size'); return false; }
        if (!material) { showFieldError('order-material', 'Select material'); return false; }
        return true;
    }

    function validateStep2() {
        if (!appState.selectedSupplier) {
            showError('order-error-container', 'Select a supplier');
            return false;
        }
        return true;
    }

    function validateStep3() {
        clearValidationErrors();
        const firstName = document.getElementById('order-firstname').value;
        const lastName = document.getElementById('order-lastname').value;
        const email = document.getElementById('order-email').value;
        const phone = document.getElementById('order-phone').value;
        const company = document.getElementById('order-company').value;
        
        if (!firstName) { showFieldError('order-firstname', 'First name required'); return false; }
        if (!lastName) { showFieldError('order-lastname', 'Last name required'); return false; }
        if (!validateEmail(email)) { showFieldError('order-email', 'Valid email'); return false; }
        if (!phone) { showFieldError('order-phone', 'Phone required'); return false; }
        if (!company) { showFieldError('order-company', 'Company required'); return false; }
        return true;
    }

     
    function validateAndNextStep(currentStep, nextStep) {
        let isValid = false;
        switch(currentStep) {
            case 1: isValid = validateStep1(); break;
            case 2: isValid = validateStep2(); break;
            case 3: isValid = validateStep3(); break;
            default: isValid = true;
        }
        if (isValid) nextOrderStep(nextStep);
    }

        
    function nextOrderStep(step) {
        if (step < 1 || step > 5) return;
        if (step === 4) updateReviewSection();
        document.getElementById(`order-step-${appState.currentOrderStep}`).classList.add('hidden');
        appState.currentOrderStep = step;
        document.getElementById(`order-step-${step}`).classList.remove('hidden');
        updateStepIndicators();
    }

         function prevOrderStep(step) {
        nextOrderStep(step);
    }



    function updateReviewSection() {
        const productSelect = document.getElementById('order-product');
        const product = productSelect.options[productSelect.selectedIndex]?.text || '-';
        const quantity = document.getElementById('order-quantity').value;
        const materialSelect = document.getElementById('order-material');
        const material = materialSelect.options[materialSelect.selectedIndex]?.text || '-';
        const contactMethod = document.querySelector('input[name="contactMethod"]:checked')?.value || 'email';
        
        document.getElementById('review-product').textContent = product;
        document.getElementById('review-supplier').textContent = appState.selectedSupplier?.name || 'Not selected';
        document.getElementById('review-quantity').textContent = `${quantity} pieces`;
        document.getElementById('review-material').textContent = material;
        document.getElementById('review-contact').textContent = contactMethod.charAt(0).toUpperCase() + contactMethod.slice(1);
        document.getElementById('confirmation-supplier').textContent = appState.selectedSupplier?.name || 'Supplier';
    }

    
    async function submitOrder() {
    if (!appState.selectedSupplier) {
        showError('order-error-container', 'Please select a supplier');
        return;
    }
    
    showLoading('Submitting order...');

    try {
        const products = await getProducts();
        const productKey = document.getElementById('order-product').value;
        const product = products.find(p => p.key === productKey);
        
        const orderId = 'ORD-' + Math.floor(100000 + Math.random() * 900000);
        document.getElementById('order-reference').textContent = orderId;
        
        const orderData = {
            orderId: orderId,
            supplierId: appState.selectedSupplier.id,
            supplierName: appState.selectedSupplier.name,
            customerEmail: document.getElementById('order-email').value,
            customerName: document.getElementById('order-firstname').value + ' ' + document.getElementById('order-lastname').value,
            customerCompany: document.getElementById('order-company').value,
            customerPhone: document.getElementById('order-phone').value,
            productKey: productKey,
            productName: product?.name || 'Product',
            quantity: parseInt(document.getElementById('order-quantity').value),
            size: document.getElementById('order-size').value,
            material: document.getElementById('order-material').value,
            specs: document.getElementById('order-specs').value,
            address: document.getElementById('order-address').value,
            contactMethod: document.querySelector('input[name="contactMethod"]:checked')?.value || 'email',
            amount: (product?.price || 0) * parseInt(document.getElementById('order-quantity').value)
        };
        
        console.log('Sending order:', orderData);
        
        const response = await fetch(`${API_BASE_URL}/orders`, {
            method: 'POST',
            headers: {
                'Content-Type': 'application/json',
                'Authorization': `Bearer ${appState.authToken}`
            },
            body: JSON.stringify(orderData)
        });
        
        // ✅ FIX: Check if response has content before parsing JSON
        const responseText = await response.text();
        console.log('Raw response:', responseText);
        
        let data;
        try {
            data = responseText ? JSON.parse(responseText) : {};
        } catch (e) {
            console.warn('Response is not JSON, using empty object');
            data = {};
        }
        
        if (response.ok) {
            // Show success message
            showSuccess('order-error-container', `✅ Order submitted to ${appState.selectedSupplier.name}!`);
            
            // Go to confirmation step
            nextOrderStep(5);
            
            // Update dashboard if supplier
            if (appState.isAuthenticated && appState.isSupplier) {
                updateDashboardData();
            }
        } else {
            throw new Error(data.message || 'Order failed with status: ' + response.status);
        }
        
    } catch (error) {
        console.error('Order error:', error);
        showError('order-error-container', error.message || 'Failed to submit order');
    } finally {
        hideLoading();
    }
}

       
    async function loadSuppliersForProduct(productKey) {
        const suppliers = [
            { id: 'sup1', name: 'Precision Flange Co.', company: 'Precision Flange Ltd', rating: 4.8, location: 'Mumbai', status: 'Online' },
            { id: 'sup2', name: 'Industrial Flange Works', company: 'Industrial Works', rating: 4.6, location: 'Delhi', status: 'Online' }
        ];
        
        const suppliersList = document.getElementById('suppliers-list');
        suppliersList.innerHTML = suppliers.map(s => `
            <div class="supplier-card bg-white p-4 rounded-xl border-2 border-slate-200 cursor-pointer" onclick="selectSupplier(this, '${s.id}', '${s.name}')">
                <div class="flex items-start gap-3">
                    <div class="w-12 h-12 bg-green-100 rounded-full flex items-center justify-center">
                        <i class="fas fa-user-tie text-green-600"></i>
                    </div>
                    <div>
                        <h4 class="font-bold">${s.name}</h4>
                        <p class="text-sm">${s.company}</p>
                        <div class="flex items-center gap-2 mt-1">
                            <i class="fas fa-star text-yellow-500 text-sm"></i>
                            <span>${s.rating}</span>
                            <span class="text-xs bg-green-100 text-green-700 px-2 py-0.5 rounded">${s.status}</span>
                        </div>
                        <div class="text-xs mt-2">📍 ${s.location}</div>
                    </div>
                </div>
            </div>
        `).join('');
    }



    function selectSupplier(element, supplierId, supplierName) {
        appState.selectedSupplier = { id: supplierId, name: supplierName };
        document.querySelectorAll('.supplier-card').forEach(c => c.classList.remove('selected'));
        element.classList.add('selected');
        document.getElementById('selected-supplier-display').textContent = supplierName;
    }

        // ========== ORDER TRACKING FUNCTIONS ==========
        
        function openTrackingModal() {
            document.getElementById('tracking-modal').classList.remove('hidden');
            document.body.style.overflow = 'hidden';
        }

        function closeTrackingModal() {
            document.getElementById('tracking-modal').classList.add('hidden');
            document.body.style.overflow = 'auto';
        }

        function trackOrderWithCode() {
            const orderRef = document.getElementById('order-reference').textContent;
            closeOrderModal();
            setTimeout(() => {
                openTrackingModal();
                document.getElementById('tracking-input').value = orderRef;
                searchOrder();
            }, 500);
        }

        async function searchOrder() {
            const orderId = document.getElementById('tracking-input').value.trim();
            if (!orderId) {
                showError('tracking-modal .error-message', 'Please enter an order ID');
                return;
            }
            
            showLoading('Searching for order...');
            
            try {
                const orders = await getOrders();
                const order = orders.find(o => o.id === orderId);
                
                // FIXED: Demo order if not found
                if (!order) {
                    // Show demo order
                    document.getElementById('tracking-empty').classList.add('hidden');
                    document.getElementById('tracking-results').classList.remove('hidden');
                    document.getElementById('my-orders-section').classList.add('hidden');
                    document.getElementById('tracking-loading').classList.add('hidden');
                    
                    document.getElementById('tracking-order-id').textContent = `#${orderId}`;
                    document.getElementById('tracking-product-name').textContent = 'MS Plate Flange';
                    document.getElementById('tracking-status').textContent = 'Processing';
                    document.getElementById('tracking-quantity').textContent = '50 pieces';
                    document.getElementById('tracking-date').textContent = new Date().toLocaleDateString();
                    document.getElementById('tracking-delivery').textContent = new Date(Date.now() + 7*24*60*60*1000).toLocaleDateString();
                    document.getElementById('tracking-amount').textContent = '₹125,000';
                    document.getElementById('tracking-customer-name').textContent = 'John Doe';
                    document.getElementById('tracking-company').textContent = 'Oil & Gas Corp';
                    document.getElementById('tracking-contact').textContent = 'john@example.com';
                    document.getElementById('tracking-supplier').textContent = 'Precision Flange Co.';
                    document.getElementById('tracking-supplier-contact').textContent = 'sales@precisionflange.com';
                    document.getElementById('tracking-supplier-phone').textContent = '+91 9876543210';
                    
                    // Update timeline
                    document.getElementById('tracking-timeline').innerHTML = `
                        <div class="tracking-step completed">
                            <div class="tracking-step-icon completed">
                                <i class="fas fa-check"></i>
                            </div>
                            <div class="tracking-step-content">
                                <p class="text-sm text-slate-500">${new Date().toLocaleString()}</p>
                                <h5 class="font-bold text-slate-900 mb-1">Order Received</h5>
                                <p class="text-slate-600">Your order has been received by the supplier.</p>
                            </div>
                        </div>
                        <div class="tracking-step current">
                            <div class="tracking-step-icon current">
                                <i class="fas fa-sync-alt"></i>
                            </div>
                            <div class="tracking-step-content">
                                <p class="text-sm text-slate-500">${new Date(Date.now() - 2*24*60*60*1000).toLocaleString()}</p>
                                <h5 class="font-bold text-slate-900 mb-1">Processing</h5>
                                <p class="text-slate-600">Your order is being processed and verified.</p>
                            </div>
                        </div>
                        <div class="tracking-step">
                            <div class="tracking-step-icon pending">
                                <i class="fas fa-cogs"></i>
                            </div>
                            <div class="tracking-step-content">
                                <p class="text-sm text-slate-500">Not started</p>
                                <h5 class="font-bold text-slate-900 mb-1">Manufacturing</h5>
                                <p class="text-slate-600">Components are being manufactured.</p>
                            </div>
                        </div>
                        <div class="tracking-step">
                            <div class="tracking-step-icon pending">
                                <i class="fas fa-truck"></i>
                            </div>
                            <div class="tracking-step-content">
                                <p class="text-sm text-slate-500">Not shipped</p>
                                <h5 class="font-bold text-slate-900 mb-1">Shipping</h5>
                                <p class="text-slate-600">Order will be shipped soon.</p>
                            </div>
                        </div>
                    `;
                    
                    hideLoading();
                    return;
                }
                
                document.getElementById('tracking-empty').classList.add('hidden');
                document.getElementById('tracking-results').classList.remove('hidden');
                document.getElementById('my-orders-section').classList.add('hidden');
                document.getElementById('tracking-loading').classList.add('hidden');
                
                document.getElementById('tracking-order-id').textContent = `#${order.id}`;
                document.getElementById('tracking-product-name').textContent = order.productName;
                document.getElementById('tracking-status').textContent = order.status ? order.status.charAt(0).toUpperCase() + order.status.slice(1) : 'Unknown';
                document.getElementById('tracking-quantity').textContent = `${order.quantity || 0} pieces`;
                document.getElementById('tracking-date').textContent = order.date ? new Date(order.date).toLocaleDateString() : 'N/A';
                document.getElementById('tracking-delivery').textContent = new Date(Date.now() + 7*24*60*60*1000).toLocaleDateString();
                document.getElementById('tracking-amount').textContent = `₹${(order.amount || 0).toLocaleString()}`;
                document.getElementById('tracking-customer-name').textContent = order.customerName || 'N/A';
                document.getElementById('tracking-company').textContent = order.customerCompany || 'N/A';
                document.getElementById('tracking-contact').textContent = order.customerEmail || 'N/A';
                document.getElementById('tracking-supplier').textContent = order.supplierName || 'N/A';
                document.getElementById('tracking-supplier-contact').textContent = 'supplier@example.com';
                document.getElementById('tracking-supplier-phone').textContent = order.customerPhone || '+91 9876543210';
                
                // Update timeline
                const steps = {
                    'pending': ['pending', 'pending', 'pending', 'pending'],
                    'processing': ['completed', 'current', 'pending', 'pending'],
                    'shipped': ['completed', 'completed', 'current', 'pending'],
                    'completed': ['completed', 'completed', 'completed', 'completed']
                }[order.status || 'pending'] || ['pending', 'pending', 'pending', 'pending'];
                
                document.getElementById('tracking-timeline').innerHTML = `
                    <div class="tracking-step ${steps[0] === 'completed' ? 'completed' : steps[0] === 'current' ? 'current' : ''}">
                        <div class="tracking-step-icon ${steps[0]}">
                            <i class="fas fa-check"></i>
                        </div>
                        <div class="tracking-step-content">
                            <p class="text-sm text-slate-500">${order.date ? new Date(order.date).toLocaleString() : 'N/A'}</p>
                            <h5 class="font-bold text-slate-900 mb-1">Order Received</h5>
                            <p class="text-slate-600">Your order has been received by the supplier.</p>
                        </div>
                    </div>
                    <div class="tracking-step ${steps[1] === 'completed' ? 'completed' : steps[1] === 'current' ? 'current' : ''}">
                        <div class="tracking-step-icon ${steps[1]}">
                            <i class="fas fa-sync-alt"></i>
                        </div>
                        <div class="tracking-step-content">
                            <p class="text-sm text-slate-500">${steps[1] !== 'pending' ? new Date(Date.now() - 2*24*60*60*1000).toLocaleString() : 'Processing soon'}</p>
                            <h5 class="font-bold text-slate-900 mb-1">Processing</h5>
                            <p class="text-slate-600">Your order is being processed and verified.</p>
                        </div>
                    </div>
                    <div class="tracking-step ${steps[2] === 'completed' ? 'completed' : steps[2] === 'current' ? 'current' : ''}">
                        <div class="tracking-step-icon ${steps[2]}">
                            <i class="fas fa-cogs"></i>
                        </div>
                        <div class="tracking-step-content">
                            <p class="text-sm text-slate-500">${steps[2] !== 'pending' ? 'In progress' : 'Not started'}</p>
                            <h5 class="font-bold text-slate-900 mb-1">Manufacturing</h5>
                            <p class="text-slate-600">Components are being manufactured.</p>
                        </div>
                    </div>
                    <div class="tracking-step ${steps[3] === 'completed' ? 'completed' : steps[3] === 'current' ? 'current' : ''}">
                        <div class="tracking-step-icon ${steps[3]}">
                            <i class="fas fa-truck"></i>
                        </div>
                        <div class="tracking-step-content">
                            <p class="text-sm text-slate-500">${steps[3] !== 'pending' ? 'Shipped' : 'Not shipped'}</p>
                            <h5 class="font-bold text-slate-900 mb-1">Shipping</h5>
                            <p class="text-slate-600">Order will be shipped soon.</p>
                        </div>
                    </div>
                `;
            } catch (error) {
                showError('tracking-modal .error-message', error.message);
            } finally {
                hideLoading();
            }
        }

        async function showMyOrders() {
            if (!appState.isAuthenticated || appState.currentUser.type === 'visitor') {
                showError('tracking-modal .error-message', 'Please login to view your orders.');
                openAuthModal();
                return;
            }
            
            showLoading('Loading your orders...');
            
            try {
                const orders = await getCustomerOrders(appState.currentUser.email);
                
                document.getElementById('tracking-results').classList.add('hidden');
                document.getElementById('tracking-empty').classList.add('hidden');
                document.getElementById('tracking-loading').classList.add('hidden');
                document.getElementById('my-orders-section').classList.remove('hidden');
                
                const ordersList = document.getElementById('my-orders-list');
                if (orders.length === 0) {
                    // FIXED: Show demo orders
                    ordersList.innerHTML = `
                        <div class="bg-white p-4 rounded-xl border border-slate-200">
                            <div class="flex justify-between items-start">
                                <div>
                                    <div class="flex items-center gap-3">
                                        <h4 class="font-bold text-slate-900">#ORD-123456</h4>
                                        <span class="badge badge-warning">pending</span>
                                    </div>
                                    <p class="text-sm text-slate-600 mt-1">MS Plate Flange - 50 pieces</p>
                                    <p class="text-xs text-slate-500 mt-1">Ordered: ${new Date().toLocaleDateString()}</p>
                                </div>
                                <div class="text-right">
                                    <p class="font-bold">₹125,000</p>
                                    <button onclick="trackOrder('ORD-123456')" class="text-sm text-blue-600 hover:text-blue-800">Track</button>
                                </div>
                            </div>
                        </div>
                        <div class="bg-white p-4 rounded-xl border border-slate-200">
                            <div class="flex justify-between items-start">
                                <div>
                                    <div class="flex items-center gap-3">
                                        <h4 class="font-bold text-slate-900">#ORD-123457</h4>
                                        <span class="badge badge-success">completed</span>
                                    </div>
                                    <p class="text-sm text-slate-600 mt-1">Forged Flange - 25 pieces</p>
                                    <p class="text-xs text-slate-500 mt-1">Ordered: ${new Date(Date.now() - 30*24*60*60*1000).toLocaleDateString()}</p>
                                </div>
                                <div class="text-right">
                                    <p class="font-bold">₹42,500</p>
                                    <button onclick="trackOrder('ORD-123457')" class="text-sm text-blue-600 hover:text-blue-800">Track</button>
                                </div>
                            </div>
                        </div>
                    `;
                } else {
                    ordersList.innerHTML = orders.map(o => `
                        <div class="bg-white p-4 rounded-xl border border-slate-200">
                            <div class="flex justify-between items-start">
                                <div>
                                    <div class="flex items-center gap-3">
                                        <h4 class="font-bold text-slate-900">#${o.id}</h4>
                                        <span class="badge badge-${o.status === 'pending' ? 'warning' : o.status === 'processing' ? 'info' : o.status === 'completed' ? 'success' : 'danger'}">${o.status}</span>
                                    </div>
                                    <p class="text-sm text-slate-600 mt-1">${o.productName} - ${o.quantity || 0} pieces</p>
                                    <p class="text-xs text-slate-500 mt-1">Ordered: ${o.date ? new Date(o.date).toLocaleDateString() : 'N/A'}</p>
                                </div>
                                <div class="text-right">
                                    <p class="font-bold">₹${(o.amount || 0).toLocaleString()}</p>
                                    <button onclick="trackOrder('${o.id}')" class="text-sm text-blue-600 hover:text-blue-800">Track</button>
                                </div>
                            </div>
                        </div>
                    `).join('');
                }
            } catch (error) {
                showError('tracking-modal .error-message', error.message);
            } finally {
                hideLoading();
            }
        }

        function trackOrder(orderId) {
            document.getElementById('tracking-input').value = orderId;
            searchOrder();
        }

        function downloadInvoice() {
            showInfo('tracking-modal .error-message', 'Invoice download feature is under development.');
        }

        function contactSupplier() {
            const supplierEmail = document.getElementById('tracking-supplier-contact').textContent;
            window.location.href = `mailto:${supplierEmail}`;
        }

        // ========== CHAT FUNCTIONS ==========
        
        function openChat(supplier) {
            if (!appState.isAuthenticated || appState.currentUser.type === 'visitor') {
                showError('login-error-container', 'Please login to chat.');
                openAuthModal();
                return;
            }
            
            appState.selectedSupplier = supplier;
            document.getElementById('chat-modal').classList.add('active');
            document.getElementById('chat-supplier-name').textContent = supplier.name;
            document.getElementById('chat-supplier-status').textContent = supplier.status || 'Online';
            loadChatMessages();
        }

        function closeChat() {
            document.getElementById('chat-modal').classList.remove('active');
        }

        function loadChatMessages() {
            const supplierId = appState.selectedSupplier?.id || 'default';
            
            if (!appState.chatMessages[supplierId]) {
                appState.chatMessages[supplierId] = [{
                    id: 1,
                    sender: 'supplier',
                    text: `Hello! How can I help you with your order?`,
                    time: new Date().toLocaleTimeString()
                }];
            }
            
            updateChatDisplay(supplierId);
        }

        function updateChatDisplay(supplierId) {
            const chatContainer = document.getElementById('chat-messages');
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
            const message = input.value.trim();
            if (!message) return;
            
            const supplierId = appState.selectedSupplier?.id || 'default';
            
            if (!appState.chatMessages[supplierId]) {
                appState.chatMessages[supplierId] = [];
            }
            
            appState.chatMessages[supplierId].push({
                id: Date.now(),
                sender: 'user',
                text: message,
                time: new Date().toLocaleTimeString()
            });
            
            input.value = '';
            updateChatDisplay(supplierId);
            
            // Simulate response
            setTimeout(() => {
                const responses = [
                    "Thank you for your message. We'll get back to you shortly.",
                    "Can you please share more details?",
                    "I'll check availability for you.",
                    "Would you like a quotation for this?"
                ];
                
                appState.chatMessages[supplierId].push({
                    id: Date.now() + 1,
                    sender: 'supplier',
                    text: responses[Math.floor(Math.random() * responses.length)],
                    time: new Date().toLocaleTimeString()
                });
                
                updateChatDisplay(supplierId);
            }, 2000);
        }

        // ========== UTILITY FUNCTIONS ==========
        
         function showLoading(message = 'Loading...') {
        document.getElementById('loading-message').textContent = message;
        document.getElementById('loading-overlay').classList.remove('hidden');
    }

         function hideLoading() {
        document.getElementById('loading-overlay').classList.add('hidden');
    }

    function showError(containerId, message) {
        const container = document.querySelector(containerId);
        if (container) {
            container.innerHTML = `<i class="fas fa-exclamation-circle"></i><span>${message}</span>`;
            container.classList.remove('hidden');
            container.className = 'error-message';
            setTimeout(() => container.classList.add('hidden'), 5000);
        } else {
            alert(message);
        }
    }

    function showSuccess(containerId, message) {
        const container = document.querySelector(containerId);
        if (container) {
            container.innerHTML = `<i class="fas fa-check-circle"></i><span>${message}</span>`;
            container.classList.remove('hidden');
            container.className = 'success-message';
            setTimeout(() => container.classList.add('hidden'), 5000);
        }
    }

        function showInfo(containerId, message) {
            const container = document.querySelector(containerId);
            if (container) {
                container.innerHTML = `<i class="fas fa-info-circle"></i><span>${message}</span>`;
                container.classList.remove('hidden');
                container.className = 'info-message';
                setTimeout(() => container.classList.add('hidden'), 3000);
            }
        }

          function validateEmail(email) {
        return /^[^\s@]+@[^\s@]+\.[^\s@]+$/.test(email);
    }

        function validateRequired(value) {
        return value && value.trim() !== '';
    }


        function clearValidationErrors() {
            document.querySelectorAll('.validation-message').forEach(el => el.classList.add('hidden'));
            document.querySelectorAll('.input-error').forEach(el => el.classList.remove('input-error'));
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

        function toggleAuthView(view) {
            document.getElementById('login-form').classList.toggle('hidden', view !== 'login');
            document.getElementById('signup-form').classList.toggle('hidden', view !== 'signup');
        }

        function openAuthModal() {
            document.body.classList.add('require-auth');
            document.body.classList.remove('visitor-mode');
            document.getElementById('auth-overlay').style.display = 'flex';
            document.body.style.overflow = 'hidden';
        }

        function closeAuth() {
            if (!appState.isAuthenticated) {
                document.body.classList.add('visitor-mode');
                document.body.classList.remove('require-auth');
            }
            document.getElementById('auth-overlay').style.display = 'none';
            document.body.style.overflow = 'auto';
        }

        function setUserType(type) {
            appState.currentUserType = type;
            const partnerBtn = document.querySelector('.partner-btn');
            const supplierBtn = document.querySelector('.supplier-btn');
            
            if (partnerBtn && supplierBtn) {
                if (type === 'partner') {
                    partnerBtn.classList.add('border-blue-200', 'bg-blue-50', 'text-blue-700');
                    partnerBtn.classList.remove('border-slate-200');
                    supplierBtn.classList.remove('border-blue-200', 'bg-blue-50', 'text-blue-700');
                    supplierBtn.classList.add('border-slate-200');
                } else {
                    supplierBtn.classList.add('border-blue-200', 'bg-blue-50', 'text-blue-700');
                    supplierBtn.classList.remove('border-slate-200');
                    partnerBtn.classList.remove('border-blue-200', 'bg-blue-50', 'text-blue-700');
                    partnerBtn.classList.add('border-slate-200');
                }
            }
        }

        function toggleMobileMenu() {
            const menu = document.getElementById('mobile-menu');
            const overlay = document.getElementById('mobile-menu-overlay');
            
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

        function showProfile() {
            if (!appState.isAuthenticated) {
                openAuthModal();
                return;
            }
            showInfo('login-error-container', 'Profile page is under development.');
        }

        async function handleSearch(query) {
            const term = query.toLowerCase().trim();
            if (term.length < 2) return;
            
            const products = await getProducts();
            const matched = products.find(p => 
                p.name.toLowerCase().includes(term) || 
                p.key.includes(term) || 
                (p.description && p.description.toLowerCase().includes(term))
            );
            
            if (matched) {
                updateProduct(matched.key);
            }
        }

        function updateProduct(key) {
            fetchAndUpdateProducts().then(() => {
                getProducts().then(products => {
                    updateCurrentProduct(key, products);
                });
            });
        }

        function showAllProducts() {
            document.getElementById('product-gallery').scrollIntoView({behavior:'smooth'});
        }

        // ========== UI UPDATE FUNCTIONS ==========
        
        function updateUIAfterAuth() {
            const statusBadge = document.getElementById('user-status');
            const mobileStatus = document.getElementById('mobile-user-status');
            const orderNowBtn = document.getElementById('order-now-btn');
            const productOrderBtn = document.getElementById('product-order-btn');
            
            if (appState.isAuthenticated && appState.currentUser.type !== 'visitor') {
                const userType = appState.currentUser.type === 'supplier' ? 'Supplier' : 'Partner';
                statusBadge.innerHTML = `<i class="fas fa-${appState.currentUser.type === 'supplier' ? 'building' : 'user-shield'} mr-1"></i>${userType}`;
                mobileStatus.innerHTML = userType;
                
                // Hide/show buttons based on user type
                document.getElementById('logout-btn')?.classList.remove('hidden');
                document.getElementById('mobile-logout-btn')?.classList.remove('hidden');
                document.getElementById('login-btn')?.classList.add('hidden');
                document.getElementById('mobile-login-btn')?.classList.add('hidden');
                document.getElementById('profile-btn')?.classList.remove('hidden');
                document.getElementById('mobile-profile-link')?.classList.remove('hidden');
                
                // Suppliers: Hide order buttons, show dashboard
                if (appState.currentUser.type === 'supplier') {
                    document.getElementById('dashboard-btn')?.classList.remove('hidden');
                    document.getElementById('mobile-dashboard-link')?.classList.remove('hidden');
                    if (orderNowBtn) orderNowBtn.style.display = 'none';
                    if (productOrderBtn) productOrderBtn.style.display = 'none';
                    document.querySelectorAll('.order-button').forEach(btn => {
                        btn.style.display = 'none';
                    });
                } else {
                    // Partners: Show order buttons, hide dashboard
                    document.getElementById('dashboard-btn')?.classList.add('hidden');
                    document.getElementById('mobile-dashboard-link')?.classList.add('hidden');
                    if (orderNowBtn) orderNowBtn.style.display = 'flex';
                    if (productOrderBtn) productOrderBtn.style.display = 'block';
                    document.querySelectorAll('.order-button').forEach(btn => {
                        btn.style.display = 'flex';
                    });
                }
            } else {
                // Visitor mode
                statusBadge.innerHTML = '<i class="fas fa-user mr-1"></i>Visitor';
                mobileStatus.innerHTML = 'Visitor';
                
                document.getElementById('logout-btn')?.classList.add('hidden');
                document.getElementById('mobile-logout-btn')?.classList.add('hidden');
                document.getElementById('login-btn')?.classList.remove('hidden');
                document.getElementById('mobile-login-btn')?.classList.remove('hidden');
                document.getElementById('profile-btn')?.classList.add('hidden');
                document.getElementById('mobile-profile-link')?.classList.add('hidden');
                document.getElementById('dashboard-btn')?.classList.add('hidden');
                document.getElementById('mobile-dashboard-link')?.classList.add('hidden');
                 
                // Visitors: Show order buttons
                if (orderNowBtn) orderNowBtn.style.display = 'flex';
                if (productOrderBtn) productOrderBtn.style.display = 'block';
                document.querySelectorAll('.order-button').forEach(btn => {
                    btn.style.display = 'flex';
                });
            }
        }

        function initReveal() {
            const observer = new IntersectionObserver((entries) => {
                entries.forEach(e => e.target.classList.toggle('active', e.isIntersecting));
            }, { threshold: 0.1 });
            document.querySelectorAll('.reveal').forEach(r => observer.observe(r));
        }

        function setupEventListeners() {
            document.addEventListener('keydown', (e) => {
                if (e.key === 'Escape') {
                    closeOrderModal();
                    closeDashboard();
                    closeAuth();
                    closeTrackingModal();
                    closeChat();
                    if (document.getElementById('mobile-menu').classList.contains('active')) {
                        toggleMobileMenu();
                    }
                }
            });
            
            document.addEventListener('click', (e) => {
                if (e.target === document.getElementById('auth-overlay')) closeAuth();
                if (e.target === document.getElementById('dashboard-modal')) closeDashboard();
                if (e.target === document.getElementById('tracking-modal')) closeTrackingModal();
                if (e.target === document.getElementById('order-modal')) closeOrderModal();
            });
            
            document.getElementById('chat-input')?.addEventListener('keypress', (e) => {
                if (e.key === 'Enter') sendChatMessage();
            });
        }

        // ========== INITIALIZATION ==========
        
        document.addEventListener('DOMContentLoaded', function() {
            initializeAuth();
            setUserType('partner');
            initReveal();
            setupEventListeners();
        });
    </script>
</body>
</html>

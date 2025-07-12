<!DOCTYPE html> 
<html lang="th"> 
<head> 
    <meta charset="UTF-8"> 
    <meta name="viewport" content="width=device-width, initial-scale=1.0"> 
    <title>GREENNOVATION LAB</title> 
    <link href="https://fonts.googleapis.com/css2?family=Kanit:wght@300;400;500;600;700&display=swap" rel="stylesheet"> 
    <script src="https://cdn.tailwindcss.com"></script> 
    <script src="https://cdn.jsdelivr.net/npm/sweetalert2@11"></script> 
    <style> 
        * { 
            margin: 0; 
            padding: 0; 
            box-sizing: border-box; 
            font-family: 'Kanit', sans-serif; 
        } 
 
        body { 
            min-height: 100vh; 
            overflow-x: hidden; 
            background-color: #f0f4f8; 
            padding-bottom: 40px; /* Space for footer */ 
            position: relative; 
        } 
 
        .home-bg { 
            background: url('https://img5.pic.in.th/file/secure-sv1/-2-75beff830336dd6f.jpg'); 
            background-size: cover; 
            background-position: center; 
            position: relative; 
            min-height: 100vh; 
            padding-bottom: 40px; /* Space for footer */ 
        } 
 
        .game-bg { 
            background: url('https://img2.pic.in.th/pic/1ca870dd67182c385bbe31e54adefcb6.jpg'); 
            background-size: cover; 
            background-position: center; 
            min-height: 100vh; 
            padding-bottom: 40px; /* Space for footer */ 
        } 
 
        .summary-bg { 
            background: linear-gradient(135deg, rgba(0,0,0,0.6), rgba(0,0,0,0.4)), url('https://img5.pic.in.th/file/secure-sv1/e4ed54acdb351e9da6ae568614cbb87f.jpg'); 
            background-size: cover; 
            background-position: center; 
            min-height: 100vh; 
            padding-bottom: 40px; /* Space for footer */ 
        } 
 
        .title-text { 
            font-size: 3.5rem; 
            font-weight: 700; 
            background: linear-gradient(135deg, #4ade80, #16a34a); 
            -webkit-background-clip: text; 
            -webkit-text-fill-color: transparent; 
            text-shadow: 0 2px 10px rgba(0,0,0,0.1); 
            letter-spacing: 1px; 
            display: inline-block; 
            animation: pulse 2s infinite; 
        } 
 
        @keyframes pulse { 
            0% { transform: scale(1); } 
            50% { transform: scale(1.05); } 
            100% { transform: scale(1); } 
        } 
 
        .btn { 
            @apply px-8 py-4 rounded-full font-semibold text-white shadow-lg transform transition-all duration-300 text-lg; 
            min-width: 260px; 
            animation: buttonPulse 3s infinite; 
        } 
 
        @keyframes buttonPulse { 
            0% { transform: scale(1); } 
            50% { transform: scale(1.03); } 
            100% { transform: scale(1); } 
        } 
 
        .btn:hover { 
            @apply shadow-xl -translate-y-1; 
            filter: brightness(1.1); 
            animation: none; 
        } 
 
        .btn:active { 
            transform: translateY(1px); 
        } 
 
        .primary-btn { 
            background: linear-gradient(135deg, #4ade80, #16a34a); 
        } 
 
        .primary-btn:hover { 
            background: linear-gradient(135deg, #16a34a, #15803d); 
        } 
 
        .secondary-btn { 
            background: linear-gradient(135deg, #60a5fa, #3b82f6); 
        } 
 
        .secondary-btn:hover { 
            background: linear-gradient(135deg, #3b82f6, #2563eb); 
        } 
 
        .tertiary-btn { 
            background-color: #8B5CF6; 
        } 
 
        .tertiary-btn:hover { 
            background-color: #7C3AED; 
        } 
 
        .success-btn { 
            background-color: #10B981; 
        } 
 
        .success-btn:hover { 
            background-color: #059669; 
        } 
 
        .card { 
            @apply rounded-3xl shadow-lg; 
            background-color: rgba(255, 255, 255, 0.8); 
            backdrop-filter: blur(5px); 
            border: 1px solid rgba(255, 255, 255, 0.5); 
        } 
 
        /* Glassmorphic card style */ 
        .glassmorphic { 
            @apply rounded-3xl shadow-xl; 
            background-color: rgba(255, 255, 255, 0.7); 
            backdrop-filter: blur(10px); 
            border: 1px solid rgba(255, 255, 255, 0.8); 
        } 
 
        .draggable { 
            cursor: grab; 
            transition: all 0.2s; 
            position: relative; 
        } 
 
        .draggable:active { 
            cursor: grabbing; 
            transform: scale(1.05); 
        } 
 
        .drop-zone { 
            position: relative; 
            min-height: 100px; 
            border-radius: 16px; 
            border: 2px dashed #ccc; 
            transition: all 0.3s; 
        } 
 
        .drop-target { 
            border: 2px dashed #3B82F6; 
            background-color: rgba(59, 130, 246, 0.1); 
        } 
 
        .timer { 
            font-size: 1.5rem; 
            font-weight: bold; 
            color: #fff; 
            background-color: #EF4444; 
            padding: 0.5rem 1rem; 
            border-radius: 12px; 
            display: flex; 
            align-items: center; 
            justify-content: center; 
            min-width: 100px; 
        } 
 
        .coin-display { 
            font-size: 1.5rem; 
            font-weight: bold; 
            color: #fff; 
            background-color: #F59E0B; 
            padding: 0.5rem 1rem; 
            border-radius: 12px; 
            display: flex; 
            align-items: center; 
            justify-content: center; 
            min-width: 120px; 
        } 
 
        .placed-organism { 
            position: absolute; 
            transition: all 0.3s; 
            z-index: 5; 
        } 
 
        .stats-card { 
            @apply bg-white rounded-lg shadow-lg p-4 mb-4; 
            border-left: 4px solid #3B82F6; 
        } 
 
        /* Updated input field style */ 
        .input-field { 
            @apply w-full px-4 py-3 rounded-lg border focus:outline-none focus:ring-2 focus:ring-green-500 focus:border-transparent text-base; 
            border: 1px solid rgba(74, 222, 128, 0.3); 
            background-color: rgba(255, 255, 255, 0.9); 
            transition: all 0.3s ease; 
            width: 100%; 
            margin: 0 auto; 
        } 
 
        .input-field:focus { 
            background-color: white; 
            box-shadow: 0 0 0 3px rgba(74, 222, 128, 0.2); 
        } 
 
        .level-container { 
            position: relative; 
            width: 100%; 
            height: 60vh; 
            overflow: hidden; 
            border-radius: 16px; 
            border: 2px solid #ccc; 
        } 
 
        .level-image { 
            width: 100%; 
            height: 100%; 
            object-fit: cover; 
        } 
 
        .organism-container { 
            @apply flex justify-start gap-4 p-4 rounded-2xl shadow-lg; 
            background-color: white; 
            overflow-x: auto; 
            white-space: nowrap; 
            -webkit-overflow-scrolling: touch; 
        } 
 
        .organism-item { 
            width: 80px; 
            height: 80px; 
            object-fit: contain; 
            padding: 8px; 
            background-color: #f3f4f6; 
            border-radius: 12px; 
            border: 1px solid #e5e7eb; 
            transition: all 0.3s; 
            flex-shrink: 0; 
        } 
 
        .organism-item:hover { 
            transform: scale(1.05); 
            border-color: #3B82F6; 
            box-shadow: 0 4px 6px rgba(0, 0, 0, 0.1); 
        } 
 
        @media (max-width: 768px) { 
            .organism-item { 
                width: 60px; 
                height: 60px; 
                padding: 4px; 
            } 
             
            .title-text { 
                font-size: 2.5rem; 
            } 
 
            .btn { 
                min-width: 220px; 
                padding: 0.75rem 1.5rem; 
            } 
             
            .button-container { 
                flex-direction: column; 
                align-items: center; 
            } 
        } 
 
        .score-highlight { 
            @apply text-4xl md:text-5xl font-bold; 
            color: #F59E0B; 
        } 
 
        .fade-in { 
            animation: fadeIn 0.5s ease-in; 
        } 
 
        @keyframes fadeIn { 
            from { opacity: 0; transform: translateY(20px); } 
            to { opacity: 1; transform: translateY(0); } 
        } 
 
        .game-header { 
            background-color: #32CD32; 
            border-radius: 20px; 
            padding: 12px 16px; 
            margin: 18px 12px 16px 12px; 
            display: flex; 
            justify-content: space-between; 
            align-items: center; 
            box-shadow: 0 4px 8px rgba(0, 0, 0, 0.1); 
            max-width: 1200px; 
            margin-left: auto; 
            margin-right: auto; 
        } 
 
        .player-info { 
            color: white; 
            font-weight: 600; 
            font-size: 1.1rem; 
            display: flex; 
            align-items: center; 
        } 
 
        .game-timer { 
            background-color: rgba(255, 255, 255, 0.25); 
            color: white; 
            font-weight: 700; 
            padding: 6px 12px; 
            border-radius: 12px; 
            display: flex; 
            align-items: center; 
            justify-content: center; 
            min-width: 90px; 
        } 
 
        .game-coins { 
            background-color: rgba(255, 255, 255, 0.25); 
            color: white; 
            font-weight: 700; 
            padding: 6px 12px; 
            border-radius: 12px; 
            display: flex; 
            align-items: center; 
            justify-content: center; 
            min-width: 90px; 
        } 
 
        .modal-content { 
            @apply bg-white rounded-3xl shadow-lg p-8; 
            animation: modalFadeIn 0.3s ease-out; 
        } 
 
        @keyframes modalFadeIn { 
            from { opacity: 0; transform: scale(0.95); } 
            to { opacity: 1; transform: scale(1); } 
        } 
 
        .confirm-btn { 
            background: linear-gradient(135deg, #4ade80, #16a34a); 
            color: white; 
            font-weight: 700; 
            padding: 16px 32px; 
            border-radius: 16px; 
            min-width: 280px; 
            font-size: 1.25rem; 
            margin: 0 auto; 
            display: block; 
            box-shadow: 0 4px 12px rgba(22, 163, 74, 0.4), 0 0 15px rgba(74, 222, 128, 0.3); 
            transform: translateY(-2px); 
            transition: all 0.3s ease; 
        } 
 
        .confirm-btn:hover { 
            transform: translateY(-4px); 
            box-shadow: 0 6px 15px rgba(22, 163, 74, 0.5), 0 0 20px rgba(74, 222, 128, 0.4); 
        } 
 
        .confirm-btn:active { 
            transform: translateY(0); 
            box-shadow: 0 2px 8px rgba(22, 163, 74, 0.3); 
        } 
 
        .summary-title { 
            font-size: 2.8rem; 
            font-weight: 700; 
            color: #3B82F6; 
            text-align: center; 
            margin-bottom: 1.5rem; 
            text-shadow: 0 2px 4px rgba(0,0,0,0.1); 
        } 
 
        .player-data-card { 
            @apply rounded-3xl p-4 mb-4; 
            background-color: rgba(219, 234, 254, 0.9); 
        } 
 
        .player-data-text { 
            @apply text-gray-800 font-medium; 
        } 
 
        .score-card { 
            @apply rounded-3xl p-4 mb-6 shadow-lg; 
            background-color: #FEF3C7; 
        } 
 
        .score-text { 
            @apply font-medium text-yellow-800; 
        } 
 
        .score-value { 
            @apply font-bold text-lg text-yellow-800; 
        } 
 
        .footer { 
            background-color: rgba(255, 255, 255, 0.5); 
            backdrop-filter: blur(5px); 
            position: fixed; 
            bottom: 0; 
            left: 0; 
            width: 100%; 
            padding: 8px 0; 
            text-align: center; 
            font-size: 0.85rem; 
            color: #4b5563; 
            z-index: 10; 
            border-top: 1px solid rgba(255, 255, 255, 0.3); 
        } 
 
        .rank-badge { 
            @apply px-3 py-1 rounded-full text-sm font-bold text-white; 
            display: inline-flex; 
            align-items: center; 
            justify-content: center; 
        } 
 
        .rank-1 { 
            background-color: #F59E0B; 
        } 
 
        .rank-2 { 
            background-color: #9CA3AF; 
        } 
 
        .rank-3 { 
            background-color: #B45309; 
        } 
 
        .rank-other { 
            background-color: #3B82F6; 
        } 
 
        .level-complete-title { 
            font-size: 2.5rem; 
            font-weight: 700; 
            color: #16a34a; 
            margin-bottom: 1rem; 
        } 
 
        .progress-container { 
            width: 100%; 
            height: 8px; 
            background-color: #e5e7eb; 
            border-radius: 4px; 
            margin: 8px 0; 
            overflow: hidden; 
        } 
 
        .progress-bar { 
            height: 100%; 
            background-color: #3B82F6; 
            border-radius: 4px; 
            transition: width 0.5s ease; 
        } 
 
        .section-title { 
            @apply text-xl font-bold mb-3 text-center; 
            color: #16a34a; 
        } 
         
        /* Updated form container */ 
        .form-container { 
            max-width: 600px; 
            width: 90%; 
            margin: 0 auto; 
            display: flex; 
            flex-direction: column; 
            gap: 1.5rem; 
        } 
         
        /* Updated home content */ 
        .home-content { 
            min-height: calc(100vh - 40px); /* Adjust for footer */ 
            display: flex; 
            flex-direction: column; 
            justify-content: center; 
            align-items: center; 
            padding: 2rem 1rem; 
            padding-bottom: 60px; /* Extra padding to ensure content doesn't get cut off */ 
            max-height: 100vh; 
            overflow-y: auto; 
        } 
         
        /* Updated button container */ 
        .button-container { 
            display: flex; 
            flex-direction: row; 
            gap: 1.5rem; 
            width: 100%; 
            margin-top: 1rem; 
            justify-content: center; 
        } 
         
        @media (max-width: 640px) { 
            .button-container { 
                flex-direction: column; 
                align-items: center; 
                gap: 1rem; 
            } 
        } 
 
        .level-complete-card { 
            background-color: white; 
            border-radius: 24px; 
            padding: 2rem; 
            text-align: center; 
            max-width: 500px; 
            width: 90%; 
            box-shadow: 0 10px 25px rgba(0, 0, 0, 0.1); 
        } 
 
        .level-complete-coins { 
            font-size: 1.5rem; 
            font-weight: 600; 
            color: #F59E0B; 
            margin-bottom: 0.5rem; 
        } 
 
        .level-complete-bonus { 
            font-size: 1.5rem; 
            font-weight: 600; 
            color: #F59E0B; 
            margin-bottom: 1.5rem; 
        } 
 
        .level-complete-message { 
            font-size: 1.25rem; 
            color: #16a34a; 
            font-weight: 500; 
            margin-bottom: 2rem; 
        } 
 
        .next-level-btn { 
            @apply px-8 py-4 rounded-2xl font-bold text-white shadow-lg transform transition-all duration-300 text-lg; 
            background: linear-gradient(135deg, #4ade80, #16a34a); 
            min-width: 220px; 
            display: inline-block; 
        } 
 
        .next-level-btn:hover { 
            @apply shadow-xl -translate-y-1; 
            background: linear-gradient(135deg, #16a34a, #15803d); 
        } 
 
        /* Updated form label */ 
        .form-label { 
            @apply block text-sm font-medium text-gray-700 mb-2; 
        } 
         
        /* Updated form group */ 
        .form-group { 
            margin-bottom: 1rem; 
            width: 100%; 
        } 
         
        .main-container { 
            min-height: calc(100vh - 40px); 
            padding-bottom: 60px; 
        } 
 
        .organisms-wrapper { 
            background-color: white; 
            border-radius: 12px; 
            padding: 12px; 
            margin: 16px 12px; 
            box-shadow: 0 4px 8px rgba(0, 0, 0, 0.1); 
            max-width: 1200px; 
            margin-left: auto; 
            margin-right: auto; 
            max-height: 300px; /* Increased height to accommodate more organisms */ 
            overflow-y: auto; 
        } 
 
        .organisms-grid { 
            display: flex; 
            flex-wrap: wrap; 
            gap: 12px; 
            justify-content: center; 
        } 
 
        .organism-item { 
            width: 90px; 
            height: 90px; 
            flex-shrink: 0; 
            display: flex; 
            align-items: center; 
            justify-content: center; 
            background-color: #f8f9fa; 
            border-radius: 12px; 
            border: 1px solid #e9ecef; 
            transition: all 0.2s ease; 
            padding: 8px; 
        } 
 
        .organism-item img { 
            max-width: 100%; 
            max-height: 100%; 
            object-fit: contain; 
        } 
 
        .organism-item:hover { 
            transform: translateY(-3px); 
            box-shadow: 0 5px 10px rgba(0, 0, 0, 0.1); 
            border-color: #4ade80; 
        } 
 
        .summary-container { 
            display: flex; 
            justify-content: center; 
            align-items: center; 
            min-height: calc(100vh - 80px); 
            padding: 20px; 
        } 
 
        .summary-box { 
            background-color: rgba(255, 255, 255, 0.9); 
            border-radius: 30px; 
            box-shadow: 0 10px 30px rgba(0, 0, 0, 0.2); 
            padding: 2.5rem; 
            width: 100%; 
            max-width: 550px; 
            backdrop-filter: blur(10px); 
            animation: fadeInUp 0.8s ease-out; 
        } 
 
        @keyframes fadeInUp { 
            from { 
                opacity: 0; 
                transform: translateY(30px); 
            } 
            to { 
                opacity: 1; 
                transform: translateY(0); 
            } 
        } 
 
        .summary-heading { 
            font-size: 2.8rem; 
            font-weight: 700; 
            color: #3B82F6; 
            text-align: center; 
            margin-bottom: 2rem; 
            text-shadow: 0 2px 4px rgba(0,0,0,0.05); 
        } 
 
        .info-row { 
            display: flex; 
            justify-content: space-between; 
            align-items: center; 
            background-color: #dbeafe; 
            padding: 0.75rem 1.5rem; 
            border-radius: 20px; 
            margin-bottom: 0.75rem; 
        } 
 
        .info-label { 
            font-weight: 600; 
            color: #1e40af; 
            font-size: 1.1rem; 
        } 
 
        .info-value { 
            font-weight: 700; 
            color: #1e3a8a; 
            font-size: 1.1rem; 
        } 
 
        .score-row { 
            display: flex; 
            justify-content: space-between; 
            align-items: center; 
            background-color: #fef3c7; 
            padding: 0.75rem 1.5rem; 
            border-radius: 20px; 
            margin-bottom: 0.75rem; 
        } 
 
        .score-label { 
            font-weight: 600; 
            color: #92400e; 
            font-size: 1.1rem; 
        } 
 
        .score-amount { 
            font-weight: 700; 
            color: #92400e; 
            font-size: 1.1rem; 
        } 
 
        .total-row { 
            display: flex; 
            justify-content: space-between; 
            align-items: center; 
            background-color: #fdba74; 
            padding: 1rem 1.5rem; 
            border-radius: 20px; 
            margin: 1.5rem 0; 
        } 
 
        .total-label { 
            font-weight: 700; 
            color: #7c2d12; 
            font-size: 1.2rem; 
        } 
 
        .total-amount { 
            font-weight: 800; 
            color: #7c2d12; 
            font-size: 1.8rem; 
        } 
 
        .summary-buttons { 
            display: flex; 
            justify-content: center; 
            gap: 1rem; 
            margin-top: 2rem; 
        } 
 
        @media (max-width: 640px) { 
            .summary-buttons { 
                flex-direction: column; 
                align-items: center; 
            } 
        } 
 
        .submit-btn { 
            background: linear-gradient(135deg, #4ade80, #16a34a); 
            color: white; 
            font-weight: 700; 
            font-size: 1.1rem; 
            padding: 0.75rem 2rem; 
            border-radius: 20px; 
            min-width: 180px; 
            text-align: center; 
            box-shadow: 0 4px 10px rgba(22, 163, 74, 0.3); 
            transition: all 0.3s ease; 
            display: flex; 
            align-items: center; 
            justify-content: center; 
        } 
 
        .submit-btn:hover { 
            transform: translateY(-3px) scale(1.03); 
            box-shadow: 0 6px 15px rgba(22, 163, 74, 0.4); 
        } 
 
        .submit-btn:active { 
            transform: translateY(1px); 
        } 
 
        .home-btn { 
            background: linear-gradient(135deg, #a855f7, #7e22ce); 
            color: white; 
            font-weight: 700; 
            font-size: 1.1rem; 
            padding: 0.75rem 2rem; 
            border-radius: 20px; 
            min-width: 180px; 
            text-align: center; 
            box-shadow: 0 4px 10px rgba(126, 34, 206, 0.3); 
            transition: all 0.3s ease; 
            display: flex; 
            align-items: center; 
            justify-content: center; 
        } 
 
        .home-btn:hover { 
            transform: translateY(-3px) scale(1.03); 
            box-shadow: 0 6px 15px rgba(126, 34, 206, 0.4); 
        } 
 
        .home-btn:active { 
            transform: translateY(1px); 
        } 
         
        .game-container { 
            padding: 0 12px; 
            max-width: 1200px; 
            margin: 0 auto; 
        } 
         
        .level-info-card { 
            margin: 0 0 16px 0; 
            border-radius: 16px; 
        } 
         
        /* Search bar for organisms */ 
        .search-container { 
            margin-bottom: 12px; 
            padding: 0 12px; 
        } 
         
        .search-input { 
            width: 100%; 
            padding: 10px 16px; 
            border-radius: 20px; 
            border: 1px solid #e5e7eb; 
            background-color: white; 
            font-size: 14px; 
            box-shadow: 0 2px 4px rgba(0,0,0,0.05); 
            transition: all 0.3s ease; 
        } 
         
        .search-input:focus { 
            outline: none; 
            border-color: #4ade80; 
            box-shadow: 0 0 0 3px rgba(74, 222, 128, 0.2); 
        } 
         
        /* Category tabs for organisms */ 
        .category-tabs { 
            display: flex; 
            overflow-x: auto; 
            gap: 8px; 
            padding: 0 12px 12px 12px; 
            scrollbar-width: none; /* Firefox */ 
        } 
         
        .category-tabs::-webkit-scrollbar { 
            display: none; /* Chrome, Safari, Edge */ 
        } 
         
        .category-tab { 
            padding: 8px 16px; 
            border-radius: 20px; 
            background-color: #f3f4f6; 
            font-size: 14px; 
            font-weight: 500; 
            white-space: nowrap; 
            cursor: pointer; 
            transition: all 0.2s ease; 
        } 
         
        .category-tab.active { 
            background-color: #4ade80; 
            color: white; 
        } 
         
        .category-tab:hover:not(.active) { 
            background-color: #e5e7eb; 
        } 
         
        /* Tooltip styles */ 
        .tooltip { 
            position: absolute; 
            top: -40px; 
            left: 50%; 
            transform: translateX(-50%); 
            background-color: rgba(255, 255, 255, 0.9); 
            color: #333; 
            padding: 5px 10px; 
            border-radius: 8px; 
            font-size: 12px; 
            font-weight: 500; 
            white-space: nowrap; 
            box-shadow: 0 2px 5px rgba(0, 0, 0, 0.15); 
            pointer-events: none; 
            opacity: 0; 
            transition: opacity 0.2s ease; 
            z-index: 100; 
        } 
         
        .draggable:hover .tooltip { 
            opacity: 1; 
        } 
         
        .placed-organism .tooltip { 
            top: -30px; 
        } 
    </style> 
</head> 
<body> 
    <!-- Home Screen - Redesigned --> 
    <div id="home-screen" class="home-bg"> 
        <div class="main-container"> 
            <div class="home-content"> 
                <!-- Section 1: Main Title (Unchanged) --> 
                <h1 class="title-text text-center mb-6">GREENNOVATION LAB</h1> 
                 
                <div class="form-container fade-in"> 
                    <!-- Section 2: Game Description (Glassmorphic) --> 
                    <div class="glassmorphic p-6 text-center"> 
                        <h2 class="text-xl font-bold text-green-600 mb-4">ยินดีต้อนรับนักจัดการสิ่งแวดล้อมตัวจิ๋ว!</h2> 
                         
                        <p class="text-base mb-4 font-medium text-gray-700"> 
                            เธอกำลังจะกลายเป็นนักจัดการสิ่งแวดล้อมตัวจิ๋ว…อย่าลืมเก็บเหรียญและโบนัสด้วยนะ! 
                        </p> 
                         
                        <p class="text-sm text-gray-700"> 
                            เกมนี้จะทดสอบความรู้ของคุณเกี่ยวกับระบบนิเวศและสิ่งแวดล้อม คุณจะต้องลากสิ่งมีชีวิตไปวางในสภาพแวดล้อมที่เหมาะสม 
                            เพื่อรับเหรียญรางวัล และยิ่งทำได้เร็วเท่าไหร่ ก็จะได้โบนัสมากขึ้นเท่านั้น! 
                        </p> 
                    </div> 
 
                    <!-- Section 3: Registration Form (Glassmorphic) --> 
                    <div class="glassmorphic p-6"> 
                        <h2 class="text-xl font-bold text-green-600 mb-4 text-center">ข้อมูลผู้เล่น</h2> 
                         
                        <form id="registration-form" class="space-y-5"> 
                            <div class="form-group"> 
                                <label for="name" class="form-label">ชื่อ-นามสกุล</label> 
                                <input type="text" id="name" name="name" required class="input-field" placeholder="กรอกชื่อ-นามสกุลของคุณ..."> 
                            </div> 
                            <div class="form-group"> 
                                <label for="number" class="form-label">เลขที่</label> 
                                <input type="text" id="number" name="number" required class="input-field" placeholder="กรอกเลขที่ของคุณ..."> 
                            </div> 
                            <div class="form-group"> 
                                <label for="school" class="form-label">โรงเรียน</label> 
                                <input type="text" id="school" name="school" required class="input-field" placeholder="กรอกชื่อโรงเรียนของคุณ..."> 
                            </div> 
                        </form> 
                    </div> 
 
                    <!-- Section 4: Buttons (Standalone) --> 
                    <div class="button-container mt-6"> 
                        <button id="start-game-btn" class="btn primary-btn"> 
                            <span class="flex items-center justify-center"> 
                                <svg class="w-5 h-5 mr-2" fill="none" stroke="currentColor" viewBox="0 0 24 24" xmlns="http://www.w3.org/2000/svg"> 
                                    <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M14.752 11.168l-3.197-2.132A1 1 0 0010 9.87v4.263a1 1 0 001.555.832l3.197-2.132a1 1 0 000-1.664z"></path> 
                                    <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M21 12a9 9 0 11-18 0 9 9 0 0118 0z"></path> 
                                </svg> 
                                เริ่มเกม 
                            </span> 
                        </button> 
                        <button id="stats-btn" class="btn secondary-btn"> 
                            <span class="flex items-center justify-center"> 
                                <svg class="w-5 h-5 mr-2" fill="none" stroke="currentColor" viewBox="0 0 24 24" xmlns="http://www.w3.org/2000/svg"> 
                                    <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M9 19v-6a2 2 0 00-2-2H5a2 2 0 00-2 2v6a2 2 0 002 2h2a2 2 0 002-2zm0 0V9a2 2 0 012-2h2a2 2 0 012 2v10m-6 0a2 2 0 002 2h2a2 2 0 002-2m0 0V5a2 2 0 012-2h2a2 2 0 012 2v14a2 2 0 01-2 2h-2a2 2 0 01-2-2z"></path> 
                                </svg> 
                                สถิตินักจัดการสิ่งแวดล้อมจิ๋ว 
                            </span> 
                        </button> 
                    </div> 
                </div> 
            </div> 
        </div> 
        <!-- Section 5: Footer (Unchanged) --> 
        <footer class="footer"> 
            พัฒนาโดย คุณครูนิติพงศ์ คงทอง โรงเรียนทรัพย์ทวี สพป.สุราษฎร์ธานี เขต 3 
        </footer> 
    </div> 
 
    <!-- Game Screen --> 
    <div id="game-screen" class="game-bg hidden"> 
        <div class="main-container"> 
            <!-- Unified Game Header --> 
            <div class="game-header"> 
                <div class="player-info"> 
                    <svg class="w-6 h-6 mr-2" fill="none" stroke="currentColor" viewBox="0 0 24 24" xmlns="http://www.w3.org/2000/svg"> 
                        <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M16 7a4 4 0 11-8 0 4 4 0 018 0zM12 14a7 7 0 00-7 7h14a7 7 0 00-7-7z"></path> 
                    </svg> 
                    <span id="player-name-display">-</span> 
                </div> 
                 
                <div class="game-timer"> 
                    <svg class="w-5 h-5 mr-2" fill="none" stroke="currentColor" viewBox="0 0 24 24" xmlns="http://www.w3.org/2000/svg"> 
                        <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M12 8v4l3 3m6-3a9 9 0 11-18 0 9 9 0 0118 0z"></path> 
                    </svg> 
                    <span id="timer">90</span> 
                </div> 
                 
                <div class="game-coins"> 
                    <svg class="w-5 h-5 mr-2" fill="none" stroke="currentColor" viewBox="0 0 24 24" xmlns="http://www.w3.org/2000/svg"> 
                        <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M12 8c-1.657 0-3 .895-3 2s1.343 2 3 2 3 .895 3 2-1.343 2-3 2m0-8c1.11 0 2.08.402 2.599 1M12 8V7m0 1v8m0 0v1m0-1c-1.11 0-2.08-.402-2.599-1M21 12a9 9 0 11-18 0 9 9 0 0118 0z"></path> 
                    </svg> 
                    <span id="coin-display">0</span> 
                </div> 
            </div> 
 
            <div class="game-container"> 
                <!-- Level Info Section --> 
                <div class="card p-4 mb-4 level-info-card"> 
                    <div id="level-badge" class="inline-block bg-blue-500 text-white px-2 py-1 rounded text-sm mb-2">ด่านที่ 1</div> 
                    <h2 class="text-xl font-bold text-blue-600 mb-2" id="level-title">ทุ่งนา</h2> 
                    <p id="level-description" class="text-gray-700 text-sm"> 
                        พื้นที่โล่งกว้างที่มนุษย์ใช้สำหรับปลูกพืช โดยเฉพาะในฤดูฝนจะมีน้ำหลากไหลเข้าท่วมบางส่วน ทำให้ดินชุ่มชื้นและเหมาะแก่การปลูกพืช 
                    </p> 
                    <div class="progress-container"> 
                        <div class="progress-bar" style="width: 12.5%;"></div> 
                    </div> 
                </div> 
 
                <!-- Game Area Section --> 
                <div class="level-container drop-zone mb-4" id="level-container"> 
                    <img id="level-image" src="https://img2.pic.in.th/pic/1-9266dd7f07a55aa0.jpg" alt="ทุ่งนา" class="level-image"> 
                    <!-- Placed organisms will appear here --> 
                </div> 
 
                <!-- Search and Category Filters --> 
                <div class="search-container"> 
                    <input type="text" id="organism-search" class="search-input" placeholder="ค้นหาสิ่งมีชีวิต..."> 
                </div> 
                 
                <div class="category-tabs" id="category-tabs"> 
                    <div class="category-tab active" data-category="all">ทั้งหมด</div> 
                    <div class="category-tab" data-category="animal">สัตว์</div> 
                    <div class="category-tab" data-category="plant">พืช</div> 
                    <div class="category-tab" data-category="aquatic">สัตว์น้ำ</div> 
                    <div class="category-tab" data-category="insect">แมลง</div> 
                    <div class="category-tab" data-category="fungi">เห็ด</div> 
                </div> 
 
                <!-- Organisms Section --> 
                <div class="organisms-wrapper"> 
                    <div class="organisms-grid" id="organism-container"> 
                        <!-- Organisms will be added here dynamically --> 
                    </div> 
                </div> 
 
                <!-- Confirm Button --> 
                <div class="flex justify-center mt-8 mb-8"> 
                    <button id="confirm-btn" class="confirm-btn"> 
                        <span class="flex items-center justify-center"> 
                            <svg class="w-6 h-6 mr-2" fill="none" stroke="currentColor" viewBox="0 0 24 24" xmlns="http://www.w3.org/2000/svg"> 
                                <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M5 13l4 4L19 7"></path> 
                            </svg> 
                            ยืนยันคำตอบ 
                        </span> 
                    </button> 
                </div> 
            </div> 
        </div> 
        <footer class="footer"> 
            พัฒนาโดย คุณครูนิติพงศ์ คงทอง โรงเรียนทรัพย์ทวี สพป.สุราษฎร์ธานี เขต 3 
        </footer> 
    </div> 
 
    <!-- Summary Screen --> 
    <div id="summary-screen" class="summary-bg hidden"> 
        <div class="summary-container"> 
            <div class="summary-box"> 
                <h2 class="summary-heading">สรุปคะแนน</h2> 
                 
                <!-- Player Information Section --> 
                <div class="mb-6"> 
                    <div class="info-row"> 
                        <div class="info-label">ชื่อ-นามสกุล:</div> 
                        <div id="summary-name" class="info-value">-</div> 
                    </div> 
                    <div class="info-row"> 
                        <div class="info-label">เลขที่:</div> 
                        <div id="summary-number" class="info-value">-</div> 
                    </div> 
                    <div class="info-row"> 
                        <div class="info-label">โรงเรียน:</div> 
                        <div id="summary-school" class="info-value">-</div> 
                    </div> 
                </div> 
                 
                <!-- Score Section --> 
                <div class="mt-6 max-h-[40vh] overflow-y-auto pr-2"> 
                    <div id="level-scores-container"> 
                        <!-- Level scores will be added here dynamically --> 
                    </div> 
                    <div class="score-row"> 
                        <div class="score-label">โบนัสเวลา:</div> 
                        <div id="time-bonus" class="score-amount">0 เหรียญ</div> 
                    </div> 
                </div> 
                 
                <!-- Total Score --> 
                <div class="total-row"> 
                    <div class="total-label">รวมเหรียญทั้งหมด:</div> 
                    <div id="total-coins" class="total-amount">0 เหรียญ</div> 
                </div> 
                 
                <!-- Action Buttons --> 
                <div class="summary-buttons"> 
                    <button id="submit-score-btn" class="submit-btn"> 
                        <svg class="w-5 h-5 mr-2" fill="none" stroke="currentColor" viewBox="0 0 24 24" xmlns="http://www.w3.org/2000/svg"> 
                            <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M9 12l2 2 4-4m6 2a9 9 0 11-18 0 9 9 0 0118 0z"></path> 
                        </svg> 
                        ส่งคะแนน 
                    </button> 
                    <button id="back-to-home-btn" class="home-btn"> 
                        <svg class="w-5 h-5 mr-2" fill="none" stroke="currentColor" viewBox="0 0 24 24" xmlns="http://www.w3.org/2000/svg"> 
                            <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M3 12l2-2m0 0l7-7 7 7M5 10v10a1 1 0 001 1h3m10-11l2 2m-2-2v10a1 1 0 01-1 1h-3m-6 0a1 1 0 001-1v-4a1 1 0 011-1h2a1 1 0 011 1v4a1 1 0 001 1m-6 0h6"></path> 
                        </svg> 
                        กลับหน้าแรก 
                    </button> 
                </div> 
            </div> 
        </div> 
        <footer class="footer"> 
            พัฒนาโดย คุณครูนิติพงศ์ คงทอง โรงเรียนทรัพย์ทวี สพป.สุราษฎร์ธานี เขต 3 
        </footer> 
    </div> 
 
    <!-- Stats Screen --> 
    <div id="stats-screen" class="home-bg hidden"> 
        <div class="main-container"> 
            <div class="container mx-auto px-4 py-8"> 
                <div class="card p-6 mb-6"> 
                    <h2 class="summary-title text-center mb-6">สถิตินักจัดการสิ่งแวดล้อมตัวจิ๋ว</h2> 
                     
                    <div id="loading-stats" class="text-center py-8"> 
                        <div class="inline-block animate-spin rounded-full h-8 w-8 border-t-2 border-b-2 border-blue-500 mb-2"></div> 
                        <p class="text-lg">กำลังโหลดข้อมูล...</p> 
                    </div> 
                     
                    <div id="stats-container" class="grid grid-cols-1 md:grid-cols-2 gap-4 max-h-[50vh] overflow-y-auto px-2"></div> 
                     
                    <div class="flex flex-col sm:flex-row justify-center mt-8 gap-4"> 
                        <button id="refresh-stats-btn" class="btn primary-btn"> 
                            <span class="flex items-center justify-center"> 
                                <svg class="w-5 h-5 mr-2" fill="none" stroke="currentColor" viewBox="0 0 24 24" xmlns="http://www.w3.org/2000/svg"> 
                                    <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M4 4v5h.582m15.356 2A8.001 8.001 0 004.582 9m0 0H9m11 11v-5h-.581m0 0a8.003 8.003 0 01-15.357-2m15.357 2H15"></path> 
                                </svg> 
                                รีเฟรชข้อมูล 
                            </span> 
                        </button> 
                        <button id="back-from-stats-btn" class="btn tertiary-btn"> 
                            <span class="flex items-center justify-center"> 
                                <svg class="w-5 h-5 mr-2" fill="none" stroke="currentColor" viewBox="0 0 24 24" xmlns="http://www.w3.org/2000/svg"> 
                                    <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M3 12l2-2m0 0l7-7 7 7M5 10v10a1 1 0 001 1h3m10-11l2 2m-2-2v10a1 1 0 01-1 1h-3m-6 0a1 1 0 001-1v-4a1 1 0 011-1h2a1 1 0 011 1v4a1 1 0 001 1m-6 0h6"></path> 
                                </svg> 
                                กลับหน้าแรก 
                            </span> 
                        </button> 
                    </div> 
                </div> 
            </div> 
        </div> 
        <footer class="footer"> 
            พัฒนาโดย คุณครูนิติพงศ์ คงทอง โรงเรียนทรัพย์ทวี สพป.สุราษฎร์ธานี เขต 3 
        </footer> 
    </div> 
 
    <!-- Level Complete Modal --> 
    <div id="level-complete-modal" class="fixed inset-0 bg-black bg-opacity-70 flex items-center justify-center z-50 hidden"> 
        <div class="level-complete-card"> 
            <h3 id="level-complete-title" class="level-complete-title"></h3> 
            <p id="level-complete-coins" class="level-complete-coins"></p> 
            <p id="level-complete-bonus" class="level-complete-bonus"></p> 
            <p id="level-complete-message" class="level-complete-message"></p> 
            <button id="level-complete-btn" class="next-level-btn"> 
                <span class="flex items-center justify-center"> 
                    <svg class="w-5 h-5 mr-2" fill="none" stroke="currentColor" viewBox="0 0 24 24" xmlns="http://www.w3.org/2000/svg"> 
                        <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M13 5l7 7-7 7M5 5l7 7-7 7"></path> 
                    </svg> 
                    ไปกันต่อ! 
                </span> 
            </button> 
        </div> 
    </div> 
 
    <script> 
        // Game data and state 
        const gameData = { 
            levels: [ 
                { 
                    id: 1, 
                    title: "ทุ่งนา", 
                    description: "พื้นที่โล่งกว้างที่มนุษย์ใช้สำหรับปลูกพืช โดยเฉพาะในฤดูฝนจะมีน้ำหลากไหลเข้าท่วมบางส่วน ทำให้ดินชุ่มชื้นและเหมาะแก่การปลูกพืช", 
                    image: "https://img2.pic.in.th/pic/1-9266dd7f07a55aa0.jpg", 
                    correctOrganisms: { 
                        grasshopper: 500, 
                        rice: 1000, 
                        water_spinach: 500, 
                        snail: 1500, 
                        heron: 2000, 
                        paddy_field_crab: 500, 
                        frog: 1000, 
                        eel: 2000, 
                        catfish: 2000, 
                        earthworm: 500, 
                        hawk: 800 
                    }, 
                    penalty: 300 
                }, 
                { 
                    id: 2, 
                    title: "สวนหลังบ้าน", 
                    description: "พื้นที่สีเขียวขนาดเล็กที่อยู่ใกล้หรือภายในบริเวณบ้าน มีทั้งส่วนที่ร่มรื่นและได้รับแสงแดด มีการปลูกต้นไม้หรือพืชต่าง ๆ เพื่อใช้ประโยชน์หรือเพิ่มความสวยงาม เป็นพื้นที่สงบที่มนุษย์ดูแลและใช้ชีวิตประจำวันร่วมด้วย", 
                    image: "https://img5.pic.in.th/file/secure-sv1/2-1999c2dc8753ffff.jpg", 
                    correctOrganisms: { 
                        grasshopper: 1000, 
                        basil: 1000, 
                        lemongrass: 1000, 
                        dog: 800, 
                        cat: 800, 
                        butterfly: 1500, 
                        snail: 1500, 
                        squirrel: 2500, 
                        frog: 500, 
                        tree_frog: 500, 
                        angel_mushroom: 1200, 
                        earthworm: 500, 
                        oriole: 500 
                    }, 
                    penalty: 300 
                }, 
                { 
                    id: 3, 
                    title: "ป่าชายเลน", 
                    description: "บริเวณที่อยู่ระหว่างแผ่นดินกับทะเล มักเป็นพื้นที่น้ำกร่อย มีลักษณะเป็นดินเลนหรือดินโคลนที่เปียกชื้นตลอดเวลา เป็นเขตแดนธรรมชาติที่เปลี่ยนแปลงตามระดับน้ำขึ้นน้ำลง และมีระบบนิเวศที่เฉพาะตัว", 
                    image: "https://img5.pic.in.th/file/secure-sv1/3-ac6e276db475b433.jpg", 
                    correctOrganisms: { 
                        mudskipper: 3500, 
                        mud_crab: 4500, 
                        mangrove: 1500, 
                        barnacle: 2500 
                    }, 
                    penalty: 300 
                }, 
                { 
                    id: 4, 
                    title: "คลองในชนบท", 
                    description: "ทางน้ำขนาดเล็กที่ไหลผ่านพื้นที่ชุมชนหรือธรรมชาติ มีน้ำใสหรือขุ่นไหลช้า บางแห่งมีตลิ่งสูงหรือลาดชัน มีดิน โคลน และพืชน้ำขึ้นตามขอบคลอง เป็นแหล่งใช้น้ำของคนในท้องถิ่น และมักเชื่อมโยงกับการดำรงชีวิตประจำวัน", 
                    image: "https://img2.pic.in.th/pic/4-61ffcac3d38e47da.jpg", 
                    correctOrganisms: { 
                        heron: 2000, 
                        freshwater_crocodile: 3000, 
                        water_hyacinth: 2500, 
                        water_spinach: 1000, 
                        catfish: 1000, 
                        hawk: 2500, 
                        python: 800 
                    }, 
                    penalty: 300 
                }, 
                { 
                    id: 5, 
                    title: "ชุมชนชนบท", 
                    description: "พื้นที่ที่มีบ้านเรือนกระจายตัว ไม่หนาแน่นเหมือนเมืองใหญ่ มีพื้นที่ธรรมชาติหลงเหลืออยู่มาก เช่น สวน ทุ่งนา หรือคลอง ผู้คนในพื้นที่มักดำเนินชีวิตอย่างเรียบง่าย และใกล้ชิดกับธรรมชาติโดยรอบ", 
                    image: "https://img5.pic.in.th/file/secure-sv1/5-91472b4d13596047.jpg", 
                    correctOrganisms: { 
                        grasshopper: 500, 
                        basil: 500, 
                        lemongrass: 500, 
                        dog: 500, 
                        cat: 500, 
                        fern: 2000, 
                        squirrel: 500, 
                        frog: 500, 
                        tree_frog: 500, 
                        termite_mushroom: 1800, 
                        angel_mushroom: 800, 
                        earthworm: 500, 
                        oriole: 1000 
                    }, 
                    penalty: 300 
                }, 
                { 
                    id: 6, 
                    title: "ชายหาด", 
                    description: "แนวพื้นที่ที่อยู่ติดกับทะเล มีลักษณะเป็นทรายละเอียดหรือก้อนหินเล็ก ๆ เรียงตัวตามแนวฝั่ง ลมพัดแรง แสงแดดจ้า น้ำทะเลมักกระทบฝั่งเป็นคลื่น มีการเปลี่ยนแปลงของระดับน้ำตลอดวัน และมีลักษณะชื้นเค็มตามสภาพของทะเล", 
                    image: "https://img2.pic.in.th/pic/6-ed00325cea930238.jpg", 
                    correctOrganisms: { 
                        starfish: 1000, 
                        sea_urchin: 1000, 
                        barnacle: 3000, 
                        sichuan_crab: 1200 
                    }, 
                    penalty: 300 
                }, 
                { 
                    id: 7, 
                    title: "สวนสาธารณะ", 
                    description: "พื้นที่สีเขียวที่จัดไว้สำหรับพักผ่อนและออกกำลังกายของผู้คนในชุมชน มีทั้งต้นไม้ ทางเดิน สนามหญ้า และแหล่งน้ำตกแต่งบางส่วน เป็นพื้นที่ที่มีการดูแลอย่างต่อเนื่อง มักตั้งอยู่ในเมืองหรือชุมชนเพื่อให้ประชาชนเข้าถึงได้ง่าย", 
                    image: "https://img5.pic.in.th/file/secure-sv1/7-18fba20b93360103.jpg", 
                    correctOrganisms: { 
                        butterfly: 2500, 
                        squirrel: 2500, 
                        dog: 2000 
                    }, 
                    penalty: 300 
                }, 
                { 
                    id: 8, 
                    title: "สวนยางพารา", 
                    description: "พื้นที่ที่มีการปลูกต้นไม้เป็นแถว ๆ อย่างเป็นระเบียบ พื้นดินมักมีใบไม้ร่วงทับถมและชื้นเล็กน้อย โดยเฉพาะในฤดูฝน สวนยางมักเงียบสงบ ไม่มีสิ่งก่อสร้างมาก และมีความเป็นธรรมชาติกึ่งเกษตร เหมาะสำหรับสิ่งมีชีวิตที่ชอบอาศัยในที่ร่ม เย็น และมีสิ่งปกคลุมพื้นดิน", 
                    image: "https://img2.pic.in.th/pic/8-852c6d2ddcf3ba7b.jpg", 
                    correctOrganisms: { 
                        bee: 1000, 
                        staghorn_fern: 1000, 
                        pitcher_plant: 1000, 
                        centipede: 1000, 
                        fern: 1500, 
                        snail: 500, 
                        frog: 800, 
                        tree_frog: 1500, 
                        termite_mushroom: 1800, 
                        angel_mushroom: 1000, 
                        earthworm: 500, 
                        hawk: 500, 
                        python: 1000 
                    }, 
                    penalty: 300 
                } 
            ], 
            organisms: { 
                // Animals 
                heron: { 
                    id: "heron", 
                    name: "นกกระยาง", 
                    image: "https://img2.pic.in.th/pic/11cc397bf223aa9a5e.png", 
                    category: "animal" 
                }, 
                mudskipper: { 
                    id: "mudskipper", 
                    name: "ปลาตีน", 
                    image: "https://img5.pic.in.th/file/secure-sv1/1b58d916c1e7b7218.png", 
                    category: "aquatic" 
                }, 
                oriole: { 
                    id: "oriole", 
                    name: "นกขมิ้น", 
                    image: "https://img5.pic.in.th/file/secure-sv1/2182f03573f389e92.png", 
                    category: "animal" 
                }, 
                snail: { 
                    id: "snail", 
                    name: "หอยทาก", 
                    image: "https://img2.pic.in.th/pic/15c1425dddc282e080.png", 
                    category: "animal" 
                }, 
                squirrel: { 
                    id: "squirrel", 
                    name: "กระรอก", 
                    image: "https://img5.pic.in.th/file/secure-sv1/20729ad23f02413bb0.png", 
                    category: "animal" 
                }, 
                catfish: { 
                    id: "catfish", 
                    name: "ปลาดุก", 
                    image: "https://img5.pic.in.th/file/secure-sv1/22e7c367b3788299db.png", 
                    category: "aquatic" 
                }, 
                frog: { 
                    id: "frog", 
                    name: "กบ", 
                    image: "https://img2.pic.in.th/pic/7e8253295e10cfd62.png", 
                    category: "animal" 
                }, 
                tree_frog: { 
                    id: "tree_frog", 
                    name: "ปาด", 
                    image: "https://img2.pic.in.th/pic/90f0a665efd3673ac.png", 
                    category: "animal" 
                }, 
                cat: { 
                    id: "cat", 
                    name: "แมว", 
                    image: "https://img2.pic.in.th/pic/2756bd00b8ade50603.png", 
                    category: "animal" 
                }, 
                starfish: { 
                    id: "starfish", 
                    name: "ปลาดาว", 
                    image: "https://img2.pic.in.th/pic/25426abe2f5f545335.png", 
                    category: "aquatic" 
                }, 
                sea_urchin: { 
                    id: "sea_urchin", 
                    name: "เม่นทะเล", 
                    image: "https://img2.pic.in.th/pic/415963a4f59a316732.png", 
                    category: "aquatic" 
                }, 
                dog: { 
                    id: "dog", 
                    name: "สุนัข", 
                    image: "https://img5.pic.in.th/file/secure-sv1/31f9e589d1b4b23ddd.png", 
                    category: "animal" 
                }, 
                mud_crab: { 
                    id: "mud_crab", 
                    name: "ปูแสม", 
                    image: "https://img2.pic.in.th/pic/3e7cd1bbdb5355b2f.png", 
                    category: "aquatic" 
                }, 
                eel: { 
                    id: "eel", 
                    name: "ปลาไหล", 
                    image: "https://img2.pic.in.th/pic/213137de76d0773cfc.png", 
                    category: "aquatic" 
                }, 
                freshwater_crocodile: { 
                    id: "freshwater_crocodile", 
                    name: "จระเข้น้ำจืด", 
                    image: "https://img2.pic.in.th/pic/2377f3df9413547bcf.png", 
                    category: "animal" 
                }, 
                paddy_field_crab: { 
                    id: "paddy_field_crab", 
                    name: "ปูนา", 
                    image: "https://img5.pic.in.th/file/secure-sv1/10b914ab5cf1e7d181.png", 
                    category: "aquatic" 
                }, 
                earthworm: { 
                    id: "earthworm", 
                    name: "ไส้เดือนดิน", 
                    image: "https://img2.pic.in.th/pic/45c6d86d3af26f567e.png", 
                    category: "animal" 
                }, 
                python: { 
                    id: "python", 
                    name: "งูเหลือม", 
                    image: "https://img2.pic.in.th/pic/44fcc609851aac5add.png", 
                    category: "animal" 
                }, 
                sichuan_crab: { 
                    id: "sichuan_crab", 
                    name: "ปูเสฉวน", 
                    image: "https://img5.pic.in.th/file/secure-sv1/48875695dc444281be.png", 
                    category: "aquatic" 
                }, 
                hawk: { 
                    id: "hawk", 
                    name: "เหยี่ยว", 
                    image: "https://img2.pic.in.th/pic/43812a5e66d70b796a.png", 
                    category: "animal" 
                }, 
                 
                // Plants 
                rice: { 
                    id: "rice", 
                    name: "ต้นข้าว", 
                    image: "https://img5.pic.in.th/file/secure-sv1/13e6aec65588305944.png", 
                    category: "plant" 
                }, 
                basil: { 
                    id: "basil", 
                    name: "ต้นโหระพา", 
                    image: "https://img2.pic.in.th/pic/2899c1b0b931870921.png", 
                    category: "plant" 
                }, 
                staghorn_fern: { 
                    id: "staghorn_fern", 
                    name: "เฟิร์นเขากวาง", 
                    image: "https://img2.pic.in.th/pic/37f3f0b8e89538a904.png", 
                    category: "plant" 
                }, 
                water_hyacinth: { 
                    id: "water_hyacinth", 
                    name: "ผักตบชวา", 
                    image: "https://img5.pic.in.th/file/secure-sv1/40c7e90d9fd9a5efac.png", 
                    category: "plant" 
                }, 
                mangrove: { 
                    id: "mangrove", 
                    name: "ต้นโกงกาง", 
                    image: "https://img2.pic.in.th/pic/59496468bf12ae6f5.png", 
                    category: "plant" 
                }, 
                lemongrass: { 
                    id: "lemongrass", 
                    name: "ต้นตะไคร้", 
                    image: "https://img5.pic.in.th/file/secure-sv1/2970e625ed6b838586.png", 
                    category: "plant" 
                }, 
                water_spinach: { 
                    id: "water_spinach", 
                    name: "ผักบุ้ง", 
                    image: "https://img2.pic.in.th/pic/32ebd1153bc11749a2.png", 
                    category: "plant" 
                }, 
                fern: { 
                    id: "fern", 
                    name: "เฟิร์น", 
                    image: "https://img5.pic.in.th/file/secure-sv1/35d490eaf6d4cc0b31.png", 
                    category: "plant" 
                }, 
                pitcher_plant: { 
                    id: "pitcher_plant", 
                    name: "ต้นหม้อข้าวหม้อแกงลิง", 
                    image: "https://img5.pic.in.th/file/secure-sv1/38b3d13324ca67f2d8.png", 
                    category: "plant" 
                }, 
                 
                // Insects 
                grasshopper: { 
                    id: "grasshopper", 
                    name: "ตั๊กแตน", 
                    image: "https://img5.pic.in.th/file/secure-sv1/16eda28245002c47b1.png", 
                    category: "insect" 
                }, 
                butterfly: { 
                    id: "butterfly", 
                    name: "ผีเสื้อ", 
                    image: "https://img5.pic.in.th/file/secure-sv1/1424696fbb02b6b1a7.png", 
                    category: "insect" 
                }, 
                bee: { 
                    id: "bee", 
                    name: "ผึ้ง", 
                    image: "https://img5.pic.in.th/file/secure-sv1/18d6ee6a91d7fd1e03.png", 
                    category: "insect" 
                }, 
                centipede: { 
                    id: "centipede", 
                    name: "ตะขาบ", 
                    image: "https://img2.pic.in.th/pic/34b1e015aa65968dcd.png", 
                    category: "insect" 
                }, 
                 
                // Aquatic 
                barnacle: { 
                    id: "barnacle", 
                    name: "เพรียง", 
                    image: "https://img5.pic.in.th/file/secure-sv1/423501a232155c7881.png", 
                    category: "aquatic" 
                }, 
                 
                // Fungi 
                termite_mushroom: { 
                    id: "termite_mushroom", 
                    name: "เห็ดโคน", 
                    image: "https://img5.pic.in.th/file/secure-sv1/469a4414c137f98ac8.png", 
                    category: "fungi" 
                }, 
                angel_mushroom: { 
                    id: "angel_mushroom", 
                    name: "เห็ดนางฟ้า", 
                    image: "https://img5.pic.in.th/file/secure-sv1/477da3ce3c55fd5ddd.png", 
                    category: "fungi" 
                } 
            }, 
            encouragements: [ 
                "เยี่ยมมาก! คุณเป็นนักจัดการสิ่งแวดล้อมที่ยอดเยี่ยม", 
                "สุดยอดไปเลย! คุณเข้าใจระบบนิเวศได้ดีมาก", 
                "เก่งมาก! คุณกำลังช่วยรักษาสมดุลของธรรมชาติ", 
                "ดีเยี่ยม! คุณมีความรู้เรื่องสิ่งแวดล้อมที่ดีมาก", 
                "ยอดเยี่ยม! คุณกำลังเป็นฮีโร่ของโลกใบนี้" 
            ] 
        }; 
 
        const gameState = { 
            currentLevel: 0, 
            timer: 90, 
            timerInterval: null, 
            coins: 0, 
            timeBonus: 0, 
            levelCoins: [0, 0, 0, 0, 0, 0, 0, 0], // Array for 8 levels 
            placedOrganisms: [], 
            playerInfo: { 
                name: "", 
                number: "", 
                school: "" 
            }, 
            currentCategory: "all", 
            searchTerm: "" 
        }; 
 
        // DOM Elements 
        const screens = { 
            home: document.getElementById("home-screen"), 
            game: document.getElementById("game-screen"), 
            summary: document.getElementById("summary-screen"), 
            stats: document.getElementById("stats-screen") 
        }; 
 
        // Show screen function 
        function showScreen(screenId) { 
            Object.keys(screens).forEach(key => { 
                screens[key].classList.add("hidden"); 
            }); 
            screens[screenId].classList.remove("hidden"); 
        } 
 
        // Initialize drag and drop functionality 
        function initDragAndDrop() { 
            const draggables = document.querySelectorAll('.draggable'); 
            const dropZone = document.querySelector('.drop-zone'); 
             
            let draggedItem = null; 
             
            draggables.forEach(draggable => { 
                draggable.addEventListener('dragstart', function(e) { 
                    draggedItem = this; 
                    setTimeout(() => { 
                        this.style.opacity = '0.5'; 
                    }, 0); 
                }); 
                 
                draggable.addEventListener('dragend', function() { 
                    this.style.opacity = '1'; 
                }); 
                 
                // Touch support 
                draggable.addEventListener('touchstart', handleTouchStart, { passive: false }); 
                draggable.addEventListener('touchmove', handleTouchMove, { passive: false }); 
                draggable.addEventListener('touchend', handleTouchEnd); 
            }); 
             
            dropZone.addEventListener('dragover', function(e) { 
                e.preventDefault(); 
                this.classList.add('drop-target'); 
            }); 
             
            dropZone.addEventListener('dragleave', function() { 
                this.classList.remove('drop-target'); 
            }); 
             
            dropZone.addEventListener('drop', function(e) { 
                e.preventDefault(); 
                this.classList.remove('drop-target'); 
                 
                if (draggedItem) { 
                    const rect = dropZone.getBoundingClientRect(); 
                    const x = (e.clientX - rect.left) / rect.width * 100; 
                    const y = (e.clientY - rect.top) / rect.height * 100; 
                     
                    placeOrganism(draggedItem.dataset.id, x, y); 
                    draggedItem = null; 
                } 
            }); 
             
            // Touch handling functions 
            let touchStartX, touchStartY; 
            let touchedItem = null; 
             
            function handleTouchStart(e) { 
                e.preventDefault(); 
                const touch = e.touches[0]; 
                touchStartX = touch.clientX; 
                touchStartY = touch.clientY; 
                touchedItem = this; 
                this.style.opacity = '0.5'; 
            } 
             
            function handleTouchMove(e) { 
                e.preventDefault(); 
                if (!touchedItem) return; 
                 
                const touch = e.touches[0]; 
                const moveX = touch.clientX; 
                const moveY = touch.clientY; 
                 
                // Visual feedback during drag 
                touchedItem.style.position = 'fixed'; 
                touchedItem.style.left = `${moveX - touchedItem.offsetWidth / 2}px`; 
                touchedItem.style.top = `${moveY - touchedItem.offsetHeight / 2}px`; 
                touchedItem.style.zIndex = '1000'; 
            } 
             
            function handleTouchEnd(e) { 
                if (!touchedItem) return; 
                 
                const touch = e.changedTouches[0]; 
                const endX = touch.clientX; 
                const endY = touch.clientY; 
                 
                // Reset styles 
                touchedItem.style.position = ''; 
                touchedItem.style.left = ''; 
                touchedItem.style.top = ''; 
                touchedItem.style.zIndex = ''; 
                touchedItem.style.opacity = '1'; 
                 
                // Check if touch ended over drop zone 
                const dropRect = dropZone.getBoundingClientRect(); 
                if ( 
                    endX >= dropRect.left &&  
                    endX <= dropRect.right &&  
                    endY >= dropRect.top &&  
                    endY <= dropRect.bottom 
                ) { 
                    const x = (endX - dropRect.left) / dropRect.width * 100; 
                    const y = (endY - dropRect.top) / dropRect.height * 100; 
                     
                    placeOrganism(touchedItem.dataset.id, x, y); 
                } 
                 
                touchedItem = null; 
            } 
        } 
 
        // Place organism in the level 
        function placeOrganism(organismId, x, y) { 
            // Check if organism is already placed 
            const existingIndex = gameState.placedOrganisms.findIndex(org => org.id === organismId); 
            if (existingIndex !== -1) { 
                // Remove existing placement 
                const existingOrg = gameState.placedOrganisms[existingIndex]; 
                const existingElement = document.getElementById(`placed-${existingOrg.id}`); 
                if (existingElement) { 
                    existingElement.remove(); 
                } 
                gameState.placedOrganisms.splice(existingIndex, 1); 
            } 
             
            // Create new placement 
            const organism = gameData.organisms[organismId]; 
            const levelContainer = document.getElementById('level-container'); 
             
            const placedElement = document.createElement('div'); 
            placedElement.className = 'placed-organism'; 
            placedElement.id = `placed-${organism.id}`; 
            placedElement.style.left = `${x}%`; 
            placedElement.style.top = `${y}%`; 
            placedElement.style.cursor = 'pointer'; 
             
            // Create image element 
            const imgElement = document.createElement('img'); 
            imgElement.src = organism.image; 
            imgElement.alt = organism.name; 
            imgElement.style.width = '80px'; 
            imgElement.style.height = '80px'; 
            imgElement.style.transform = 'translate(-50%, -50%)'; 
             
            // Create tooltip 
            const tooltip = document.createElement('div'); 
            tooltip.className = 'tooltip'; 
            tooltip.textContent = organism.name; 
             
            // Add elements to placed organism container 
            placedElement.appendChild(imgElement); 
            placedElement.appendChild(tooltip); 
             
            // Add click event to remove placement 
            placedElement.addEventListener('click', function() { 
                const index = gameState.placedOrganisms.findIndex(org => org.id === organismId); 
                if (index !== -1) { 
                    gameState.placedOrganisms.splice(index, 1); 
                    this.remove(); 
                     
                    // Make the organism available again in the container 
                    const organismElement = document.querySelector(`.draggable[data-id="${organismId}"]`); 
                    if (organismElement) { 
                        organismElement.style.display = 'flex'; 
                    } 
                } 
            }); 
             
            levelContainer.appendChild(placedElement); 
             
            // Hide the organism in the container 
            const organismElement = document.querySelector(`.draggable[data-id="${organismId}"]`); 
            if (organismElement) { 
                organismElement.style.display = 'none'; 
            } 
             
            // Add to placed organisms 
            gameState.placedOrganisms.push({ 
                id: organismId, 
                x: x, 
                y: y 
            }); 
        } 
 
        // Start game timer 
        function startTimer() { 
            clearInterval(gameState.timerInterval); 
            gameState.timer = 90; 
            updateTimerDisplay(); 
             
            gameState.timerInterval = setInterval(() => { 
                gameState.timer--; 
                updateTimerDisplay(); 
                 
                if (gameState.timer <= 0) { 
                    clearInterval(gameState.timerInterval); 
                    evaluateLevel(); 
                } 
            }, 1000); 
        } 
 
        // Update timer display 
        function updateTimerDisplay() { 
            document.getElementById('timer').textContent = gameState.timer; 
        } 
 
        // Update coin display 
        function updateCoinDisplay() { 
            document.getElementById('coin-display').textContent = `${gameState.coins}`; 
        } 
 
        // Update progress bar 
        function updateProgressBar() { 
            const progressBar = document.querySelector('.progress-bar'); 
            const totalLevels = gameData.levels.length; 
            const progress = ((gameState.currentLevel + 1) / totalLevels) * 100; 
            progressBar.style.width = `${progress}%`; 
        } 
 
        // Filter organisms based on category and search term 
        function filterOrganisms() { 
            const category = gameState.currentCategory; 
            const searchTerm = gameState.searchTerm.toLowerCase(); 
             
            const organismContainer = document.getElementById('organism-container'); 
            organismContainer.innerHTML = ''; 
             
            Object.values(gameData.organisms).forEach(organism => { 
                // Check if organism matches the current category and search term 
                const matchesCategory = category === 'all' || organism.category === category; 
                const matchesSearch = organism.name.toLowerCase().includes(searchTerm) ||  
                                     organism.id.toLowerCase().includes(searchTerm); 
                 
                if (matchesCategory && matchesSearch) { 
                    const organismDiv = document.createElement('div'); 
                    organismDiv.className = 'organism-item draggable'; 
                    organismDiv.dataset.id = organism.id; 
                    organismDiv.draggable = true; 
                     
                    // Create image element 
                    const img = document.createElement('img'); 
                    img.src = organism.image; 
                    img.alt = organism.name; 
                     
                    // Create tooltip 
                    const tooltip = document.createElement('div'); 
                    tooltip.className = 'tooltip'; 
                    tooltip.textContent = organism.name; 
                     
                    organismDiv.appendChild(img); 
                    organismDiv.appendChild(tooltip); 
                    organismContainer.appendChild(organismDiv); 
                } 
            }); 
             
            // Reinitialize drag and drop 
            initDragAndDrop(); 
        } 
 
        // Load level 
        function loadLevel(levelIndex) { 
            gameState.currentLevel = levelIndex; 
            const level = gameData.levels[levelIndex]; 
             
            // Update level info 
            document.getElementById('level-badge').textContent = `ด่านที่ ${level.id}`; 
            document.getElementById('level-title').textContent = level.title; 
            document.getElementById('level-description').textContent = level.description; 
            document.getElementById('level-image').src = level.image; 
            document.getElementById('player-name-display').textContent = gameState.playerInfo.name; 
             
            // Update progress bar 
            updateProgressBar(); 
             
            // Clear placed organisms 
            gameState.placedOrganisms = []; 
            const placedElements = document.querySelectorAll('.placed-organism'); 
            placedElements.forEach(el => el.remove()); 
             
            // Reset category and search 
            gameState.currentCategory = 'all'; 
            gameState.searchTerm = ''; 
            document.getElementById('organism-search').value = ''; 
             
            // Update category tabs 
            const categoryTabs = document.querySelectorAll('.category-tab'); 
            categoryTabs.forEach(tab => { 
                if (tab.dataset.category === 'all') { 
                    tab.classList.add('active'); 
                } else { 
                    tab.classList.remove('active'); 
                } 
            }); 
             
            // Filter and display organisms 
            filterOrganisms(); 
             
            // Start timer 
            startTimer(); 
             
            // Update coin display 
            updateCoinDisplay(); 
        } 
 
        // Evaluate level 
        function evaluateLevel() { 
            clearInterval(gameState.timerInterval); 
             
            const level = gameData.levels[gameState.currentLevel]; 
            let levelCoins = 0; 
             
            // Calculate coins based on correct organisms 
            gameState.placedOrganisms.forEach(placed => { 
                if (level.correctOrganisms[placed.id]) { 
                    levelCoins += level.correctOrganisms[placed.id]; 
                } else { 
                    levelCoins -= level.penalty; 
                } 
            }); 
             
            // Ensure coins don't go negative 
            levelCoins = Math.max(0, levelCoins); 
             
            // Calculate time bonus 
            const timeBonus = gameState.timer * 25; 
            gameState.timeBonus += timeBonus; 
             
            // Update total coins 
            gameState.levelCoins[gameState.currentLevel] = levelCoins; 
            gameState.coins += levelCoins + timeBonus; 
             
            // Get random encouragement message 
            const encouragement = gameData.encouragements[Math.floor(Math.random() * gameData.encouragements.length)]; 
             
            // Show level complete modal 
            document.getElementById('level-complete-title').textContent = "ด่านที่ " + (gameState.currentLevel + 1) + " เสร็จสิ้น!"; 
            document.getElementById('level-complete-coins').textContent = `คุณได้รับ ${levelCoins} เหรียญ`; 
            document.getElementById('level-complete-bonus').textContent = `โบนัสเวลา ${timeBonus} เหรียญ`; 
            document.getElementById('level-complete-message').textContent = encouragement; 
             
            const levelCompleteModal = document.getElementById('level-complete-modal'); 
            levelCompleteModal.classList.remove('hidden'); 
             
            // Set button action 
            document.getElementById('level-complete-btn').onclick = () => { 
                levelCompleteModal.classList.add('hidden'); 
                 
                // Move to next level or summary 
                if (gameState.currentLevel < gameData.levels.length - 1) { 
                    gameState.currentLevel++; 
                    loadLevel(gameState.currentLevel); 
                } else { 
                    showSummary(); 
                } 
            }; 
        } 
 
        // Show summary screen 
        function showSummary() { 
            showScreen('summary'); 
             
            // Update summary info 
            document.getElementById('summary-name').textContent = gameState.playerInfo.name; 
            document.getElementById('summary-number').textContent = gameState.playerInfo.number; 
            document.getElementById('summary-school').textContent = gameState.playerInfo.school; 
             
            // Update level scores 
            const levelScoresContainer = document.getElementById('level-scores-container'); 
            levelScoresContainer.innerHTML = ''; 
             
            gameState.levelCoins.forEach((coins, index) => { 
                if (index < gameData.levels.length) { 
                    const scoreRow = document.createElement('div'); 
                    scoreRow.className = 'score-row'; 
                    scoreRow.innerHTML = ` 
                        <div class="score-label">เหรียญจากด่านที่ ${index + 1}:</div> 
                        <div class="score-amount">${coins} เหรียญ</div> 
                    `; 
                    levelScoresContainer.appendChild(scoreRow); 
                } 
            }); 
             
            document.getElementById('time-bonus').textContent = gameState.timeBonus + " เหรียญ"; 
            document.getElementById('total-coins').textContent = gameState.coins + " เหรียญ"; 
        } 
 
        // Submit score to Google Sheet 
        function submitScore() { 
            const data = { 
                name: gameState.playerInfo.name, 
                number: gameState.playerInfo.number, 
                school: gameState.playerInfo.school, 
                coins: gameState.coins 
            }; 
             
            // Disable submit button to prevent multiple submissions 
            document.getElementById('submit-score-btn').disabled = true; 
            document.getElementById('submit-score-btn').innerHTML = ` 
                <div class="animate-spin rounded-full h-5 w-5 border-t-2 border-b-2 border-white mr-2"></div> 
                กำลังส่งข้อมูล... 
            `; 
             
            // Create a callback function name 
            const callbackName = 'jsonpCallback_' + new Date().getTime(); 
             
            // Create script element for JSONP request 
            const script = document.createElement('script'); 
            script.src = `https://script.google.com/macros/s/AKfycbxP_Pa9ZdFObGsLVG4wkHP3zJwGETQ36MlxetYuI0O5wbHFRj_h75AtMGsI4GzO1lIykg/exec?callback=${callbackName}&action=submit&name=${encodeURIComponent(data.name)}&number=${encodeURIComponent(data.number)}&school=${encodeURIComponent(data.school)}&coins=${data.coins}`; 
             
            // Define callback function 
            window[callbackName] = function(response) { 
                // Re-enable submit button 
                document.getElementById('submit-score-btn').disabled = false; 
                document.getElementById('submit-score-btn').innerHTML = ` 
                    <svg class="w-5 h-5 mr-2" fill="none" stroke="currentColor" viewBox="0 0 24 24" xmlns="http://www.w3.org/2000/svg"> 
                        <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M9 12l2 2 4-4m6 2a9 9 0 11-18 0 9 9 0 0118 0z"></path> 
                    </svg> 
                    ส่งคะแนน 
                `; 
                 
                if (response.success) { 
                    // Show success message with SweetAlert 
                    Swal.fire({ 
                        title: 'ส่งคะแนนสำเร็จ!', 
                        text: 'ขอบคุณที่ร่วมภารกิจพิทักษ์สิ่งแวดล้อม', 
                        icon: 'success', 
                        confirmButtonText: 'ตกลง', 
                        confirmButtonColor: '#16a34a' 
                    }).then(() => { 
                        resetGame(); 
                        showScreen('home'); 
                    }); 
                } else { 
                    // Show error message 
                    Swal.fire({ 
                        title: 'เกิดข้อผิดพลาด', 
                        text: 'ไม่สามารถส่งคะแนนได้ โปรดลองอีกครั้ง', 
                        icon: 'error', 
                        confirmButtonText: 'ตกลง', 
                        confirmButtonColor: '#EF4444' 
                    }); 
                } 
                 
                // Clean up 
                document.body.removeChild(script); 
                delete window[callbackName]; 
            }; 
             
            // Add script to document 
            document.body.appendChild(script); 
        } 
 
        // Load statistics from Google Sheet 
        function loadStatistics() { 
            document.getElementById('loading-stats').style.display = 'block'; 
            document.getElementById('stats-container').innerHTML = ''; 
             
            // Create a callback function name 
            const callbackName = 'jsonpCallback_' + new Date().getTime(); 
             
            // Create script element for JSONP request 
            const script = document.createElement('script'); 
            script.src = `https://script.google.com/macros/s/AKfycbxP_Pa9ZdFObGsLVG4wkHP3zJwGETQ36MlxetYuI0O5wbHFRj_h75AtMGsI4GzO1lIykg/exec?callback=${callbackName}&action=get`; 
             
            // Define callback function 
            window[callbackName] = function(response) { 
                document.getElementById('loading-stats').style.display = 'none'; 
                 
                if (response.success && response.data) { 
                    const statsContainer = document.getElementById('stats-container'); 
                     
                    // Sort data by coins (highest first) 
                    response.data.sort((a, b) => b.coins - a.coins); 
                     
                    // Display top entries 
                    response.data.forEach((entry, index) => { 
                        const card = document.createElement('div'); 
                        card.className = 'stats-card'; 
                         
                        let rankClass = ''; 
                        let rankBadge = ''; 
                         
                        if (index === 0) { 
                            rankClass = 'rank-1'; 
                            rankBadge = '<span class="rank-badge rank-1">อันดับ 1</span>'; 
                        } else if (index === 1) { 
                            rankClass = 'rank-2'; 
                            rankBadge = '<span class="rank-badge rank-2">อันดับ 2</span>'; 
                        } else if (index === 2) { 
                            rankClass = 'rank-3'; 
                            rankBadge = '<span class="rank-badge rank-3">อันดับ 3</span>'; 
                        } else { 
                            rankBadge = `<span class="rank-badge rank-other">อันดับ ${index + 1}</span>`; 
                        } 
                         
                        card.innerHTML = ` 
                            <div class="flex justify-between items-center mb-3"> 
                                ${rankBadge} 
                                <span class="font-bold text-blue-600 text-xl">${entry.coins} เหรียญ</span> 
                            </div> 
                            <div class="text-sm"> 
                                <p class="mb-1"><span class="font-medium">ชื่อ:</span> ${entry.name}</p> 
                                <p class="mb-1"><span class="font-medium">เลขที่:</span> ${entry.number}</p> 
                                <p><span class="font-medium">โรงเรียน:</span> ${entry.school}</p> 
                            </div> 
                        `; 
                         
                        statsContainer.appendChild(card); 
                    }); 
                     
                    if (response.data.length === 0) { 
                        statsContainer.innerHTML = '<p class="text-center py-8 text-lg">ยังไม่มีข้อมูลสถิติ</p>'; 
                    } 
                } else { 
                    document.getElementById('stats-container').innerHTML = '<p class="text-center py-8 text-lg text-red-500">ไม่สามารถโหลดข้อมูลได้ โปรดลองอีกครั้ง</p>'; 
                } 
                 
                // Clean up 
                document.body.removeChild(script); 
                delete window[callbackName]; 
            }; 
             
            // Add script to document 
            document.body.appendChild(script); 
        } 
 
        // Reset game state 
        function resetGame() { 
            gameState.currentLevel = 0; 
            gameState.timer = 90; 
            gameState.coins = 0; 
            gameState.timeBonus = 0; 
            gameState.levelCoins = [0, 0]; 
            gameState.placedOrganisms = []; 
            gameState.currentCategory = 'all'; 
            gameState.searchTerm = ''; 
            clearInterval(gameState.timerInterval); 
        } 
 
        // Event Listeners 
        document.addEventListener('DOMContentLoaded', function() { 
            // Start Game Button 
            document.getElementById('start-game-btn').addEventListener('click', function() { 
                const nameInput = document.getElementById('name'); 
                const numberInput = document.getElementById('number'); 
                const schoolInput = document.getElementById('school'); 
                 
                if (!nameInput.value || !numberInput.value || !schoolInput.value) { 
                    Swal.fire({ 
                        title: 'ข้อมูลไม่ครบถ้วน', 
                        text: 'กรุณากรอกข้อมูลให้ครบทุกช่อง', 
                        icon: 'warning', 
                        confirmButtonText: 'ตกลง', 
                        confirmButtonColor: '#16a34a' 
                    }); 
                    return; 
                } 
                 
                gameState.playerInfo = { 
                    name: nameInput.value, 
                    number: numberInput.value, 
                    school: schoolInput.value 
                }; 
                 
                resetGame(); 
                showScreen('game'); 
                loadLevel(0); 
            }); 
             
            // Stats Button 
            document.getElementById('stats-btn').addEventListener('click', function() { 
                showScreen('stats'); 
                loadStatistics(); 
            }); 
             
            // Confirm Button 
            document.getElementById('confirm-btn').addEventListener('click', evaluateLevel); 
             
            // Submit Score Button 
            document.getElementById('submit-score-btn').addEventListener('click', submitScore); 
             
            // Back to Home Button 
            document.getElementById('back-to-home-btn').addEventListener('click', function() { 
                resetGame(); 
                showScreen('home'); 
            }); 
             
            // Refresh Stats Button 
            document.getElementById('refresh-stats-btn').addEventListener('click', loadStatistics); 
             
            // Back from Stats Button 
            document.getElementById('back-from-stats-btn').addEventListener('click', function() { 
                showScreen('home'); 
            }); 
             
            // Search Input 
            document.getElementById('organism-search').addEventListener('input', function(e) { 
                gameState.searchTerm = e.target.value; 
                filterOrganisms(); 
            }); 
             
            // Category Tabs 
            document.querySelectorAll('.category-tab').forEach(tab => { 
                tab.addEventListener('click', function() { 
                    // Update active tab 
                    document.querySelectorAll('.category-tab').forEach(t => t.classList.remove('active')); 
                    this.classList.add('active'); 
                     
                    // Update current category 
                    gameState.currentCategory = this.dataset.category; 
                    filterOrganisms(); 
                }); 
            }); 
        }); 
    </script> 
</body> 
</html>

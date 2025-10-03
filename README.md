<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Elite Finance & Investment</title>
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">
    <link href="https://fonts.googleapis.com/css2?family=Exo+2:wght@300;400;500;600;700&family=Orbitron:wght@400;500;600;700&display=swap" rel="stylesheet">
    <script src="https://cdn.jsdelivr.net/npm/chart.js"></script>
    <style>
        :root {
            --primary: #6e44ff;
            --secondary: #b892ff;
            --accent: #00e5ff;
            --dark: #1a1a2e;
            --darker: #0d0d1a;
            --light: #f0f0ff;
            --success: #00ff9d;
            --warning: #ffcc00;
            --danger: #ff3860;
            --investment: #ff7d00;
            --expense: #ff3860;
            --card-bg: rgba(30, 30, 60, 0.7);
            --glow: 0 0 10px var(--accent), 0 0 20px var(--primary);
        }
        
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
            font-family: 'Exo 2', sans-serif;
        }
        
        body {
            background: linear-gradient(135deg, var(--darker) 0%, var(--dark) 70%);
            color: var(--light);
            min-height: 100vh;
            padding: 20px;
            line-height: 1.6;
        }
        
        .container {
            max-width: 1800px;
            margin: 0 auto;
        }
        
        header {
            display: flex;
            justify-content: space-between;
            align-items: center;
            padding: 20px;
            background: rgba(30, 30, 50, 0.8);
            color: var(--light);
            border-radius: 16px;
            margin-bottom: 25px;
            box-shadow: var(--glow);
            backdrop-filter: blur(10px);
            border: 1px solid var(--secondary);
        }
        
        .app-title {
            font-family: 'Orbitron', sans-serif;
            font-size: 32px;
            font-weight: 700;
            background: linear-gradient(to right, var(--accent), var(--secondary));
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
            text-shadow: 0 0 5px rgba(110, 68, 255, 0.5);
        }
        
        .currency-selector {
            display: flex;
            align-items: center;
            gap: 10px;
            background: rgba(20, 20, 40, 0.8);
            padding: 8px 16px;
            border-radius: 12px;
            border: 1px solid var(--primary);
        }
        
        select, input, button, textarea {
            padding: 12px 16px;
            border-radius: 10px;
            border: none;
            font-weight: 500;
            background: rgba(20, 20, 40, 0.8);
            color: var(--light);
            border: 1px solid var(--primary);
            transition: all 0.3s ease;
        }
        
        select:focus, input:focus, textarea:focus {
            outline: none;
            box-shadow: 0 0 0 2px var(--accent);
        }
        
        .tabs {
            display: flex;
            margin-bottom: 25px;
            border-bottom: 2px solid var(--primary);
            overflow-x: auto;
        }
        
        .tab {
            padding: 12px 24px;
            cursor: pointer;
            border-bottom: 3px solid transparent;
            transition: all 0.3s ease;
            font-weight: 600;
            color: var(--secondary);
            white-space: nowrap;
        }
        
        .tab.active {
            border-bottom: 3px solid var(--accent);
            color: var(--accent);
        }
        
        .tab-content {
            display: none;
        }
        
        .tab-content.active {
            display: block;
        }
        
        .futuristic-card {
            background: var(--card-bg);
            border-radius: 16px;
            padding: 25px;
            margin-bottom: 25px;
            box-shadow: 0 10px 30px rgba(0, 0, 0, 0.3);
            backdrop-filter: blur(10px);
            border: 1px solid var(--primary);
            position: relative;
            overflow: hidden;
        }
        
        .futuristic-card::before {
            content: '';
            position: absolute;
            top: 0;
            left: 0;
            right: 0;
            height: 5px;
            background: linear-gradient(to right, var(--primary), var(--accent));
        }
        
        .section-title {
            font-family: 'Orbitron', sans-serif;
            font-size: 24px;
            margin-bottom: 20px;
            color: var(--accent);
            padding-bottom: 12px;
            border-bottom: 2px solid var(--primary);
        }
        
        .main-content {
            display: grid;
            grid-template-columns: 1fr 1.4fr;
            gap: 30px;
        }
        
        @media (max-width: 1200px) {
            .main-content {
                grid-template-columns: 1fr;
            }
        }
        
        .stats-grid {
            display: grid;
            grid-template-columns: repeat(2, 1fr);
            gap: 20px;
            margin-top: 20px;
        }
        
        .stat-card {
            background: rgba(30, 30, 60, 0.8);
            padding: 20px;
            border-radius: 12px;
            border: 1px solid var(--primary);
            text-align: center;
        }
        
        .stat-card h3 {
            color: var(--accent);
            margin-bottom: 10px;
            font-family: 'Orbitron', sans-serif;
        }
        
        .stat-card .value {
            font-size: 24px;
            font-weight: bold;
            color: var(--success);
        }
        
        .chart-container {
            background: rgba(20, 20, 40, 0.8);
            padding: 20px;
            border-radius: 12px;
            margin-top: 20px;
            border: 1px solid var(--primary);
            height: 300px;
        }
        
        .form-group {
            margin-bottom: 18px;
        }
        
        label {
            display: block;
            margin-bottom: 8px;
            font-weight: 500;
            color: var(--secondary);
        }
        
        input, select {
            width: 100%;
            padding: 14px;
            border: 1px solid var(--primary);
            border-radius: 12px;
            font-size: 16px;
            background: rgba(10, 10, 20, 0.8);
            color: var(--light);
        }
        
        button {
            background: linear-gradient(135deg, var(--primary), var(--secondary));
            color: white;
            border: none;
            padding: 14px 24px;
            border-radius: 12px;
            cursor: pointer;
            font-size: 16px;
            font-weight: 600;
            transition: all 0.3s ease;
            width: 100%;
            text-transform: uppercase;
            letter-spacing: 1px;
        }
        
        button:hover {
            transform: translateY(-3px);
            box-shadow: 0 5px 15px rgba(110, 68, 255, 0.4);
        }
        
        .entry-list {
            max-height: 300px;
            overflow-y: auto;
            margin: 15px 0;
            padding: 10px;
            background: rgba(20, 20, 40, 0.6);
            border-radius: 10px;
            border: 1px solid var(--primary);
        }
        
        .entry-item {
            display: flex;
            justify-content: space-between;
            padding: 10px;
            border-bottom: 1px solid rgba(110, 68, 255, 0.3);
        }
        
        .entry-item:last-child {
            border-bottom: none;
        }
        
        .empty-state {
            text-align: center;
            padding: 40px 20px;
            color: var(--secondary);
        }
        
        .empty-state i {
            font-size: 48px;
            margin-bottom: 15px;
            opacity: 0.5;
        }
        
        .notification {
            position: fixed;
            top: 20px;
            right: 20px;
            padding: 15px 20px;
            border-radius: 10px;
            color: white;
            font-weight: 500;
            z-index: 10000;
            box-shadow: 0 5px 15px rgba(0,0,0,0.3);
            transform: translateX(150%);
            transition: transform 0.3s ease;
            max-width: 300px;
        }
        
        .notification.show {
            transform: translateX(0);
        }
        
        .notification.success {
            background: var(--success);
        }
        
        .notification.error {
            background: var(--danger);
        }
        
        .notification.warning {
            background: var(--warning);
            color: var(--dark);
        }
        
        .notification.info {
            background: var(--accent);
        }
        
        /* Debtors and Creditors Tab Styles */
        .debtor-form, .creditor-form {
            display: grid;
            grid-template-columns: 1fr 1fr;
            gap: 15px;
            margin-bottom: 20px;
        }
        
        .debtor-form .full-width, .creditor-form .full-width {
            grid-column: 1 / -1;
        }
        
        .debtor-item, .creditor-item {
            background: rgba(30, 30, 60, 0.8);
            padding: 16px;
            border-radius: 12px;
            margin-bottom: 12px;
            display: flex;
            justify-content: space-between;
            align-items: center;
            border: 1px solid var(--primary);
            transition: all 0.3s ease;
        }
        
        .debtor-item:hover, .creditor-item:hover {
            transform: translateX(5px);
            border-color: var(--accent);
        }
        
        .debtor-details, .creditor-details {
            flex: 1;
        }
        
        .debtor-actions, .creditor-actions {
            display: flex;
            gap: 10px;
        }
        
        .debtor-status, .creditor-status {
            padding: 4px 8px;
            border-radius: 6px;
            font-size: 12px;
            font-weight: 600;
            margin-top: 5px;
            display: inline-block;
        }
        
        .status-pending {
            background: rgba(255, 204, 0, 0.2);
            color: var(--warning);
            border: 1px solid var(--warning);
        }
        
        .status-paid {
            background: rgba(0, 255, 157, 0.2);
            color: var(--success);
            border: 1px solid var(--success);
        }
        
        .status-overdue {
            background: rgba(255, 56, 96, 0.2);
            color: var(--danger);
            border: 1px solid var(--danger);
        }
        
        .status-collected {
            background: rgba(0, 255, 157, 0.2);
            color: var(--success);
            border: 1px solid var(--success);
        }
        
        .status-outstanding {
            background: rgba(255, 204, 0, 0.2);
            color: var(--warning);
            border: 1px solid var(--warning);
        }
        
        .pay-btn, .collect-btn {
            background: rgba(0, 255, 157, 0.2);
            color: var(--success);
            border: 1px solid var(--success);
            width: auto;
        }
        
        .days-remaining {
            font-size: 12px;
            margin-top: 5px;
        }
        
        .days-high {
            color: var(--success);
        }
        
        .days-medium {
            color: var(--warning);
        }
        
        .days-low {
            color: var(--danger);
        }
        
        /* Add to existing type styles for history */
        .type-debtor {
            background: rgba(255, 119, 0, 0.2);
            color: var(--investment);
            border: 1px solid var(--investment);
        }
        
        .type-creditor {
            background: rgba(0, 229, 255, 0.2);
            color: var(--accent);
            border: 1px solid var(--accent);
        }
        
        /* All other existing styles remain the same */
        /* Savings Tab Styles */
        .savings-summary {
            display: grid;
            grid-template-columns: repeat(4, 1fr);
            gap: 15px;
            margin-bottom: 25px;
        }
        
        .savings-card {
            background: rgba(30, 30, 60, 0.8);
            border-radius: 12px;
            padding: 20px;
            text-align: center;
            border: 1px solid var(--primary);
        }
        
        .savings-card h3 {
            font-size: 14px;
            margin-bottom: 10px;
            color: var(--secondary);
        }
        
        .savings-card .value {
            font-size: 24px;
            font-weight: bold;
            color: var(--accent);
        }
        
        .savings-card .change {
            font-size: 12px;
            margin-top: 5px;
        }
        
        .savings-card .positive {
            color: var(--success);
        }
        
        .savings-card .negative {
            color: var(--danger);
        }
        
        .savings-chart-container {
            background: rgba(20, 20, 40, 0.8);
            padding: 20px;
            border-radius: 12px;
            margin-top: 20px;
            border: 1px solid var(--primary);
            height: 300px;
        }
        
        .savings-categories {
            display: grid;
            grid-template-columns: repeat(auto-fill, minmax(200px, 1fr));
            gap: 15px;
            margin-top: 20px;
        }
        
        .savings-category {
            background: rgba(30, 30, 60, 0.8);
            border-radius: 12px;
            padding: 15px;
            border: 1px solid var(--primary);
            position: relative;
        }
        
        .savings-category h3 {
            font-size: 16px;
            margin-bottom: 10px;
            color: var(--accent);
        }
        
        .savings-category .amount {
            font-size: 18px;
            font-weight: bold;
            margin-bottom: 10px;
        }
        
        .savings-category .progress {
            height: 8px;
            background: rgba(40, 40, 80, 0.8);
            border-radius: 4px;
            overflow: hidden;
        }
        
        .savings-category .progress-bar {
            height: 100%;
            background: linear-gradient(to right, var(--primary), var(--accent));
            border-radius: 4px;
        }
        
        .category-actions {
            position: absolute;
            top: 10px;
            right: 10px;
            display: flex;
            gap: 5px;
        }
        
        .category-actions button {
            width: auto;
            padding: 5px 10px;
            font-size: 12px;
        }
        
        /* Interest Calculator Styles */
        .interest-calculator {
            background: var(--card-bg);
            border-radius: 16px;
            padding: 25px;
            margin-bottom: 25px;
            box-shadow: 0 10px 30px rgba(0, 0, 0, 0.3);
            backdrop-filter: blur(10px);
            border: 1px solid var(--primary);
            position: relative;
            overflow: hidden;
        }
        
        .interest-calculator::before {
            content: '';
            position: absolute;
            top: 0;
            left: 0;
            right: 0;
            height: 5px;
            background: linear-gradient(to right, var(--primary), var(--accent));
        }
        
        .calculator-form {
            display: grid;
            grid-template-columns: 1fr 1fr;
            gap: 15px;
            margin-bottom: 20px;
        }
        
        .calculator-form .full-width {
            grid-column: 1 / -1;
        }
        
        .calculator-results {
            background: rgba(30, 30, 60, 0.8);
            border-radius: 12px;
            padding: 20px;
            margin-top: 20px;
            border: 1px solid var(--primary);
            display: none;
        }
        
        .calculator-results.show {
            display: block;
        }
        
        .result-item {
            display: flex;
            justify-content: space-between;
            margin-bottom: 10px;
            padding-bottom: 10px;
            border-bottom: 1px solid rgba(110, 68, 255, 0.3);
        }
        
        .result-item:last-child {
            border-bottom: none;
            margin-bottom: 0;
        }
        
        .result-label {
            color: var(--secondary);
        }
        
        .result-value {
            font-weight: 600;
            color: var(--accent);
        }
        
        .result-highlight {
            font-size: 18px;
            font-weight: 700;
            color: var(--success);
            text-align: center;
            margin-top: 15px;
            padding: 10px;
            background: rgba(0, 255, 157, 0.1);
            border-radius: 8px;
            border: 1px solid rgba(0, 255, 157, 0.3);
        }
        
        @keyframes fadeIn {
            from { opacity: 0; transform: translateY(10px); }
            to { opacity: 1; transform: translateY(0); }
        }
        
        /* Investments Tab Styles */
        .performance-chart-container {
            background: rgba(20, 20, 40, 0.8);
            padding: 20px;
            border-radius: 12px;
            margin-top: 20px;
            border: 1px solid var(--primary);
            height: 400px;
        }
        
        .investment-form {
            display: grid;
            grid-template-columns: 1fr 1fr;
            gap: 15px;
            margin-bottom: 20px;
        }
        
        .investment-form .full-width {
            grid-column: 1 / -1;
        }
        
        .investment-item {
            background: rgba(30, 30, 60, 0.8);
            padding: 16px;
            border-radius: 12px;
            margin-bottom: 12px;
            display: flex;
            justify-content: space-between;
            align-items: center;
            border: 1px solid var(--primary);
            transition: all 0.3s ease;
        }
        
        .investment-item:hover {
            transform: translateX(5px);
            border-color: var(--accent);
        }
        
        .investment-details {
            flex: 1;
        }
        
        .investment-actions {
            display: flex;
            gap: 10px;
        }
        
        .btn-icon {
            background: transparent;
            border: none;
            color: var(--light);
            font-size: 16px;
            cursor: pointer;
            padding: 8px;
            border-radius: 6px;
            transition: all 0.3s ease;
            width: auto;
        }
        
        .btn-icon:hover {
            background: rgba(255, 255, 255, 0.1);
            transform: translateY(-2px);
        }
        
        /* Goals Tab Styles */
        .goal-form {
            display: grid;
            grid-template-columns: 1fr 1fr;
            gap: 15px;
            margin-bottom: 20px;
        }
        
        .goal-form .full-width {
            grid-column: 1 / -1;
        }
        
        .goal-item {
            background: rgba(30, 30, 60, 0.8);
            padding: 16px;
            border-radius: 12px;
            margin-bottom: 12px;
            display: flex;
            justify-content: space-between;
            align-items: center;
            border: 1px solid var(--primary);
            transition: all 0.3s ease;
        }
        
        .goal-item:hover {
            transform: translateX(5px);
            border-color: var(--accent);
        }
        
        .goal-details {
            flex: 1;
        }
        
        .goal-actions {
            display: flex;
            gap: 10px;
        }
        
        .goal-progress {
            height: 10px;
            background: rgba(40, 40, 80, 0.8);
            border-radius: 8px;
            margin-top: 8px;
            overflow: hidden;
        }
        
        .goal-progress-bar {
            height: 100%;
            background: linear-gradient(to right, var(--primary), var(--accent));
            border-radius: 8px;
            box-shadow: 0 0 10px var(--primary);
        }
        
        .achievement-grid {
            display: grid;
            grid-template-columns: repeat(auto-fill, minmax(200px, 1fr));
            gap: 15px;
            margin-top: 20px;
        }
        
        .achievement-card {
            background: rgba(30, 30, 60, 0.8);
            border-radius: 12px;
            padding: 20px;
            text-align: center;
            border: 1px solid var(--primary);
            transition: all 0.3s ease;
            position: relative;
        }
        
        .achievement-card.unlocked {
            border-color: var(--accent);
            box-shadow: 0 0 15px rgba(0, 229, 255, 0.3);
        }
        
        .achievement-card:hover {
            transform: translateY(-5px);
        }
        
        .achievement-icon {
            font-size: 32px;
            margin-bottom: 10px;
            color: var(--accent);
        }
        
        .achievement-card.unlocked .achievement-icon {
            color: var(--success);
        }
        
        .achievement-card.locked .achievement-icon {
            color: var(--secondary);
        }
        
        .achievement-title {
            font-weight: 600;
            margin-bottom: 8px;
        }
        
        .achievement-desc {
            font-size: 12px;
            color: var(--secondary);
        }
        
        .achievement-progress {
            margin-top: 10px;
            font-size: 12px;
            color: var(--accent);
        }
        
        .achievement-actions {
            position: absolute;
            top: 10px;
            right: 10px;
            display: flex;
            gap: 5px;
        }
        
        /* Calendar Tab Styles */
        .calendar-container {
            background: var(--card-bg);
            border-radius: 16px;
            padding: 25px;
            box-shadow: 0 10px 30px rgba(0, 0, 0, 0.3);
            backdrop-filter: blur(10px);
            border: 1px solid var(--primary);
        }
        
        .calendar-header {
            display: flex;
            justify-content: space-between;
            align-items: center;
            margin-bottom: 20px;
        }
        
        .calendar-title {
            font-family: 'Orbitron', sans-serif;
            font-size: 24px;
            color: var(--accent);
        }
        
        .calendar {
            display: grid;
            grid-template-columns: repeat(7, 1fr);
            gap: 10px;
        }
        
        .calendar-day-header {
            text-align: center;
            font-weight: 600;
            padding: 12px;
            color: var(--accent);
            font-family: 'Orbitron', sans-serif;
            font-size: 14px;
            text-transform: uppercase;
            letter-spacing: 1px;
        }
        
        .calendar-day {
            height: 110px;
            border: 1px solid rgba(110, 68, 255, 0.3);
            border-radius: 12px;
            padding: 10px;
            cursor: pointer;
            transition: all 0.3s ease;
            display: flex;
            flex-direction: column;
            background: rgba(20, 20, 40, 0.6);
            position: relative;
            overflow: hidden;
        }
        
        .calendar-day:hover {
            transform: translateY(-5px);
            box-shadow: 0 5px 15px rgba(110, 68, 255, 0.4);
            border-color: var(--accent);
        }
        
        .day-number {
            align-self: flex-end;
            font-weight: 600;
            margin-bottom: 8px;
            color: var(--secondary);
            font-size: 16px;
        }
        
        .savings-amount {
            margin-top: auto;
            font-size: 14px;
            color: var(--success);
            font-weight: 500;
            text-align: center;
            background: rgba(0, 255, 157, 0.1);
            padding: 5px;
            border-radius: 8px;
            border: 1px solid rgba(0, 255, 157, 0.3);
        }
        
        .current-day {
            background: rgba(110, 68, 255, 0.2);
            border: 2px solid var(--accent);
            box-shadow: 0 0 15px rgba(0, 229, 255, 0.5);
        }
        
        .navigation-buttons {
            display: flex;
            gap: 12px;
        }
        
        .nav-btn {
            background: rgba(60, 60, 100, 0.8);
            color: var(--light);
            border: 1px solid var(--primary);
            padding: 10px 18px;
            border-radius: 10px;
            cursor: pointer;
            transition: all 0.3s ease;
            width: auto;
        }
        
        .nav-btn:hover {
            background: var(--primary);
        }
        
        /* AI Financial Advisor Tab Styles */
        .advisor-container {
            display: grid;
            grid-template-columns: 1fr 1fr;
            gap: 25px;
            margin-top: 20px;
        }
        
        @media (max-width: 1200px) {
            .advisor-container {
                grid-template-columns: 1fr;
            }
        }
        
        .risk-assessment {
            background: var(--card-bg);
            border-radius: 16px;
            padding: 25px;
            margin-bottom: 25px;
            box-shadow: 0 10px 30px rgba(0, 0, 0, 0.3);
            backdrop-filter: blur(10px);
            border: 1px solid var(--primary);
        }
        
        .risk-question {
            margin-bottom: 25px;
            padding-bottom: 15px;
            border-bottom: 1px solid rgba(110, 68, 255, 0.3);
        }
        
        .risk-options {
            display: flex;
            flex-direction: column;
            gap: 12px;
            margin-top: 15px;
        }
        
        .risk-option {
            display: flex;
            align-items: center;
            gap: 12px;
            padding: 12px 15px;
            border-radius: 10px;
            background: rgba(30, 30, 60, 0.6);
            cursor: pointer;
            transition: all 0.3s ease;
            border: 1px solid transparent;
        }
        
        .risk-option:hover {
            background: rgba(50, 50, 100, 0.6);
            border-color: var(--secondary);
        }
        
        .risk-option.selected {
            background: rgba(110, 68, 255, 0.3);
            border: 1px solid var(--primary);
            box-shadow: 0 0 10px rgba(110, 68, 255, 0.3);
        }
        
        .risk-result {
            text-align: center;
            padding: 20px;
            border-radius: 12px;
            margin-top: 25px;
            font-weight: 600;
            display: none;
        }
        
        .low-risk {
            background: rgba(0, 255, 157, 0.2);
            border: 1px solid var(--success);
            color: var(--success);
        }
        
        .medium-risk {
            background: rgba(255, 204, 0, 0.2);
            border: 1px solid var(--warning);
            color: var(--warning);
        }
        
        .high-risk {
            background: rgba(255, 56, 96, 0.2);
            border: 1px solid var(--danger);
            color: var(--danger);
        }
        
        .investment-questions {
            margin-top: 20px;
        }
        
        .investment-question {
            margin-bottom: 25px;
            padding-bottom: 15px;
            border-bottom: 1px solid rgba(110, 68, 255, 0.3);
        }
        
        .investment-options {
            display: grid;
            grid-template-columns: 1fr 1fr;
            gap: 12px;
            margin-top: 15px;
        }
        
        @media (max-width: 768px) {
            .investment-options {
                grid-template-columns: 1fr;
            }
        }
        
        .investment-option {
            padding: 15px;
            border-radius: 10px;
            background: rgba(30, 30, 60, 0.6);
            cursor: pointer;
            transition: all 0.3s ease;
            border: 1px solid transparent;
            text-align: center;
        }
        
        .investment-option:hover {
            background: rgba(50, 50, 100, 0.6);
            border-color: var(--secondary);
        }
        
        .investment-option.selected {
            background: rgba(110, 68, 255, 0.3);
            border: 1px solid var(--primary);
            box-shadow: 0 0 10px rgba(110, 68, 255, 0.3);
        }
        
        .investment-option i {
            font-size: 24px;
            margin-bottom: 10px;
            color: var(--accent);
        }
        
        .ai-response {
            background: rgba(30, 30, 60, 0.6);
            border-radius: 12px;
            padding: 20px;
            margin-top: 20px;
            border: 1px solid var(--primary);
            display: none;
        }
        
        .ai-response.show {
            display: block;
        }
        
        .ai-response-header {
            display: flex;
            align-items: center;
            gap: 10px;
            margin-bottom: 15px;
        }
        
        .ai-response-icon {
            font-size: 24px;
            color: var(--accent);
        }
        
        .ai-response-title {
            font-size: 18px;
            font-weight: 600;
            color: var(--accent);
        }
        
        .ai-response-content {
            line-height: 1.6;
        }
        
        .ai-response-content p {
            margin-bottom: 15px;
        }
        
        .ai-response-content ul {
            margin-left: 20px;
            margin-bottom: 15px;
        }
        
        .ai-response-content li {
            margin-bottom: 8px;
        }
        
        .ai-loading {
            text-align: center;
            padding: 20px;
        }
        
        .ai-loading i {
            font-size: 24px;
            color: var(--accent);
            margin-bottom: 10px;
        }
        
        .ai-loading p {
            color: var(--secondary);
        }
        
        .advisor-chat {
            margin-top: 30px;
        }
        
        .chat-container {
            background: rgba(20, 20, 40, 0.8);
            border-radius: 12px;
            border: 1px solid var(--primary);
            height: 400px;
            display: flex;
            flex-direction: column;
        }
        
        .chat-messages {
            flex: 1;
            padding: 20px;
            overflow-y: auto;
        }
        
        .chat-message {
            margin-bottom: 15px;
            padding: 12px 16px;
            border-radius: 12px;
            max-width: 80%;
        }
        
        .user-message {
            background: rgba(110, 68, 255, 0.3);
            margin-left: auto;
            border: 1px solid var(--primary);
        }
        
        .ai-message {
            background: rgba(30, 30, 60, 0.6);
            border: 1px solid var(--primary);
        }
        
        .chat-input-container {
            display: flex;
            padding: 15px;
            border-top: 1px solid rgba(110, 68, 255, 0.3);
        }
        
        .chat-input {
            flex: 1;
            margin-right: 10px;
        }
        
        .chat-send-btn {
            width: auto;
            padding: 0 20px;
        }
        
        .recommendation-grid {
            display: grid;
            grid-template-columns: repeat(auto-fill, minmax(300px, 1fr));
            gap: 20px;
            margin-top: 20px;
        }
        
        .recommendation-card {
            background: rgba(30, 30, 60, 0.6);
            border-radius: 12px;
            padding: 20px;
            border: 1px solid var(--primary);
            transition: all 0.3s ease;
        }
        
        .recommendation-card:hover {
            transform: translateY(-5px);
            box-shadow: 0 5px 15px rgba(110, 68, 255, 0.3);
        }
        
        .recommendation-title {
            font-size: 16px;
            font-weight: 600;
            color: var(--accent);
            margin-bottom: 10px;
        }
        
        .progress-bar {
            height: 8px;
            background: rgba(40, 40, 80, 0.8);
            border-radius: 4px;
            margin: 10px 0;
            overflow: hidden;
        }
        
        .progress-fill {
            height: 100%;
            background: linear-gradient(to right, var(--primary), var(--accent));
            border-radius: 4px;
        }
        
        .stat-item {
            text-align: center;
            padding: 12px;
            background: rgba(30, 30, 60, 0.6);
            border-radius: 10px;
        }
        
        .stat-value {
            font-size: 16px;
            font-weight: 600;
            color: var(--accent);
            margin-bottom: 5px;
        }
        
        .stat-label {
            font-size: 12px;
            color: var(--secondary);
        }
        
        /* Bill Tracking Tab Styles */
        .bill-form {
            display: grid;
            grid-template-columns: 1fr 1fr;
            gap: 15px;
            margin-bottom: 20px;
        }
        
        .bill-form .full-width {
            grid-column: 1 / -1;
        }
        
        .bill-item {
            background: rgba(30, 30, 60, 0.8);
            padding: 16px;
            border-radius: 12px;
            margin-bottom: 12px;
            display: flex;
            justify-content: space-between;
            align-items: center;
            border: 1px solid var(--primary);
            transition: all 0.3s ease;
        }
        
        .bill-item:hover {
            transform: translateX(5px);
            border-color: var(--accent);
        }
        
        .bill-details {
            flex: 1;
        }
        
        .bill-actions {
            display: flex;
            gap: 10px;
        }
        
        .bill-status {
            padding: 4px 8px;
            border-radius: 6px;
            font-size: 12px;
            font-weight: 600;
            margin-top: 5px;
            display: inline-block;
        }
        
        .status-pending {
            background: rgba(255, 204, 0, 0.2);
            color: var(--warning);
            border: 1px solid var(--warning);
        }
        
        .status-paid {
            background: rgba(0, 255, 157, 0.2);
            color: var(--success);
            border: 1px solid var(--success);
        }
        
        .status-overdue {
            background: rgba(255, 56, 96, 0.2);
            color: var(--danger);
            border: 1px solid var(--danger);
        }
        
        .pay-btn {
            background: rgba(0, 255, 157, 0.2);
            color: var(--success);
            border: 1px solid var(--success);
            width: auto;
        }
        
        /* History Tab Styles */
        .time-filters {
            display: flex;
            gap: 10px;
            margin-bottom: 20px;
        }
        
        .time-filter {
            padding: 8px 16px;
            background: rgba(40, 40, 80, 0.8);
            border: 1px solid var(--primary);
            border-radius: 8px;
            cursor: pointer;
            transition: all 0.3s ease;
        }
        
        .time-filter.active {
            background: var(--primary);
            color: white;
        }
        
        .export-options {
            display: flex;
            gap: 12px;
            margin-top: 20px;
        }
        
        .export-btn {
            flex: 1;
            background: linear-gradient(135deg, var(--primary), #8a6fff);
        }
        
        .export-btn:hover {
            background: linear-gradient(135deg, #8a6fff, var(--primary));
        }
        
        /* Settings Tab Styles */
        button.secondary {
            background: rgba(60, 60, 100, 0.8);
            border: 1px solid var(--primary);
        }
        
        button.secondary:hover {
            background: rgba(80, 80, 120, 0.8);
        }
        
        .digit {
            font-family: 'Orbitron', sans-serif;
        }
        
        .cyber-grid {
            position: absolute;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background-image: 
                linear-gradient(rgba(110, 68, 255, 0.1) 1px, transparent 1px),
                linear-gradient(90deg, rgba(110, 68, 255, 0.1) 1px, transparent 1px);
            background-size: 20px 20px;
            pointer-events: none;
            z-index: 0;
        }
        
        .content-wrapper {
            position: relative;
            z-index: 1;
        }
        
        /* Analytics Tab Styles */
        .analytics-grid {
            display: grid;
            grid-template-columns: repeat(2, 1fr);
            gap: 20px;
            margin-bottom: 20px;
        }
        
        @media (max-width: 768px) {
            .analytics-grid {
                grid-template-columns: 1fr;
            }
        }
        
        .analytics-card {
            background: var(--card-bg);
            border-radius: 16px;
            padding: 25px;
            box-shadow: 0 10px 30px rgba(0, 0, 0, 0.3);
            backdrop-filter: blur(10px);
            border: 1px solid var(--primary);
            position: relative;
            overflow: hidden;
        }
        
        .analytics-card::before {
            content: '';
            position: absolute;
            top: 0;
            left: 0;
            right: 0;
            height: 5px;
            background: linear-gradient(to right, var(--primary), var(--accent));
        }
        
        .analytics-chart-container {
            background: rgba(20, 20, 40, 0.8);
            padding: 20px;
            border-radius: 12px;
            margin-top: 20px;
            border: 1px solid var(--primary);
            height: 300px;
        }
        
        .analytics-stats {
            display: grid;
            grid-template-columns: repeat(3, 1fr);
            gap: 15px;
            margin-top: 20px;
        }
        
        .analytics-stat {
            background: rgba(30, 30, 60, 0.8);
            padding: 15px;
            border-radius: 12px;
            text-align: center;
            border: 1px solid var(--primary);
        }
        
        .analytics-stat .value {
            font-size: 20px;
            font-weight: bold;
            color: var(--accent);
            margin-bottom: 5px;
        }
        
        .analytics-stat .label {
            font-size: 14px;
            color: var(--secondary);
        }
        
        /* Category Management Styles */
        .category-management {
            display: grid;
            grid-template-columns: 1fr 1fr;
            gap: 20px;
            margin-bottom: 20px;
        }
        
        @media (max-width: 768px) {
            .category-management {
                grid-template-columns: 1fr;
            }
        }
        
        .achievement-management {
            display: grid;
            grid-template-columns: 1fr 1fr;
            gap: 20px;
            margin-bottom: 20px;
        }
        
        @media (max-width: 768px) {
            .achievement-management {
                grid-template-columns: 1fr;
            }
        }
        
        .history-entries {
            max-height: 500px;
            overflow-y: auto;
        }
        
        .history-entry {
            display: flex;
            justify-content: space-between;
            padding: 12px;
            border-bottom: 1px solid rgba(110, 68, 255, 0.3);
        }
        
        .history-entry:last-child {
            border-bottom: none;
        }
        
        .history-type {
            padding: 4px 8px;
            border-radius: 6px;
            font-size: 12px;
            font-weight: 600;
            margin-right: 10px;
        }
        
        .type-saving {
            background: rgba(0, 255, 157, 0.2);
            color: var(--success);
            border: 1px solid var(--success);
        }
        
        .type-investment {
            background: rgba(0, 229, 255, 0.2);
            color: var(--accent);
            border: 1px solid var(--accent);
        }
        
        .type-goal {
            background: rgba(255, 204, 0, 0.2);
            color: var(--warning);
            border: 1px solid var(--warning);
        }
        
        .type-subscription {
            background: rgba(110, 68, 255, 0.2);
            color: var(--primary);
            border: 1px solid var(--primary);
        }
        
        .type-bill {
            background: rgba(255, 56, 96, 0.2);
            color: var(--danger);
            border: 1px solid var(--danger);
        }
        
        .type-achievement {
            background: rgba(255, 119, 0, 0.2);
            color: var(--investment);
            border: 1px solid var(--investment);
        }
    </style>
</head>
<body>
    <div class="container">
        <header>
            <div class="app-title">Elite Finance & Investment</div>
            <div class="currency-selector">
                <i class="fas fa-coins"></i>
                <select id="currency-select">
                    <option value="GHS" selected>Ghana Cedis (GHS)</option>
                    <option value="USD">US Dollar (USD)</option>
                    <option value="EUR">Euro (EUR)</option>
                    <option value="GBP">British Pound (GBP)</option>
                    <option value="NGN">Nigerian Naira (NGN)</option>
                    <option value="KES">Kenyan Shilling (KES)</option>
                    <option value="ZAR">South African Rand (ZAR)</option>
                    <option value="INR">Indian Rupee (INR)</option>
                    <option value="CNY">Chinese Yuan (CNY)</option>
                    <option value="JPY">Japanese Yen (JPY)</option>
                    <option value="CAD">Canadian Dollar (CAD)</option>
                    <option value="AUD">Australian Dollar (AUD)</option>
                    <option value="CHF">Swiss Franc (CHF)</option>
                </select>
            </div>
        </header>

        <div class="tabs">
            <div class="tab active" data-tab="dashboard">Dashboard</div>
            <div class="tab" data-tab="savings">Savings</div>
            <div class="tab" data-tab="investments">Investments</div>
            <div class="tab" data-tab="goals">Goals & Achievements</div>
            <div class="tab" data-tab="subscriptions">Subscriptions</div>
            <div class="tab" data-tab="debtors">Debtors</div>
            <div class="tab" data-tab="creditors">Creditors</div>
            <div class="tab" data-tab="calendar">Financial Calendar</div>
            <div class="tab" data-tab="bills">Bill Tracking</div>
            <div class="tab" data-tab="advisor">AI Financial Advisor</div>
            <div class="tab" data-tab="analytics">Analytics</div>
            <div class="tab" data-tab="history">History</div>
            <div class="tab" data-tab="settings">Settings</div>
        </div>

        <!-- Dashboard Tab -->
        <div class="tab-content active" id="dashboard">
            <div class="main-content">
                <div class="left-column">
                    <div class="futuristic-card">
                        <div class="cyber-grid"></div>
                        <div class="content-wrapper">
                            <h2 class="section-title">Financial Overview</h2>
                            <div class="stats-grid">
                                <div class="stat-card">
                                    <h3>Total Savings</h3>
                                    <p class="value digit">GHS <span id="total-savings">0.00</span></p>
                                </div>
                                <div class="stat-card">
                                    <h3>Monthly Goal</h3>
                                    <p class="value digit">GHS <span id="monthly-goal">0.00</span></p>
                                </div>
                                <div class="stat-card">
                                    <h3>Current Month</h3>
                                    <p class="value" id="current-month">January</p>
                                </div>
                                <div class="stat-card">
                                    <h3>Goal Progress</h3>
                                    <p class="value" id="goal-progress">0%</p>
                                </div>
                            </div>
                        </div>
                    </div>

                    <div class="futuristic-card">
                        <h2 class="section-title">Recent Transactions</h2>
                        <div class="entry-list" id="recent-transactions">
                            <div class="empty-state">
                                <i class="fas fa-exchange-alt"></i>
                                <p>No recent transactions</p>
                            </div>
                        </div>
                    </div>
                </div>

                <div class="right-column">
                    <div class="chart-container">
                        <canvas id="savings-chart"></canvas>
                    </div>

                    <div class="futuristic-card">
                        <h2 class="section-title">Financial Goals</h2>
                        <div class="entry-list" id="financial-goals">
                            <div class="empty-state">
                                <i class="fas fa-bullseye"></i>
                                <p>No financial goals set</p>
                            </div>
                        </div>
                    </div>
                </div>
            </div>
        </div>

        <!-- Savings Tab -->
        <div class="tab-content" id="savings">
            <div class="futuristic-card">
                <h2 class="section-title">Savings Overview</h2>
                <div class="savings-summary">
                    <div class="savings-card">
                        <h3>Total Savings</h3>
                        <p class="value digit" id="total-savings-overview">GHS 0.00</p>
                        <p class="change positive">+5.2% from last month</p>
                    </div>
                    <div class="savings-card">
                        <h3>Monthly Goal</h3>
                        <p class="value digit" id="monthly-savings-goal">GHS 0.00</p>
                        <p class="change positive">On track</p>
                    </div>
                    <div class="savings-card">
                        <h3>Savings Rate</h3>
                        <p class="value" id="savings-rate">0%</p>
                        <p class="change negative">-2.1% from last month</p>
                    </div>
                    <div class="savings-card">
                        <h3>Emergency Fund</h3>
                        <p class="value digit" id="emergency-fund">GHS 0.00</p>
                        <p class="change positive">Fully funded</p>
                    </div>
                </div>
                
                <div class="savings-chart-container">
                    <canvas id="savings-trend-chart"></canvas>
                </div>
            </div>

            <!-- Interest Calculator -->
            <div class="interest-calculator">
                <h2 class="section-title">Savings Interest Calculator</h2>
                <p>Calculate how much your savings could grow with compound interest over time.</p>
                
                <div class="calculator-form">
                    <div class="form-group">
                        <label for="initial-amount">Initial Amount</label>
                        <input type="number" id="initial-amount" placeholder="Enter initial amount" min="0" step="0.01">
                    </div>
                    <div class="form-group">
                        <label for="monthly-contribution">Monthly Contribution</label>
                        <input type="number" id="monthly-contribution" placeholder="Enter monthly amount" min="0" step="0.01">
                    </div>
                    <div class="form-group">
                        <label for="interest-rate">Annual Interest Rate (%)</label>
                        <input type="number" id="interest-rate" placeholder="Enter interest rate" min="0" step="0.01" value="5">
                    </div>
                    <div class="form-group">
                        <label for="investment-period">Investment Period (Years)</label>
                        <input type="number" id="investment-period" placeholder="Enter years" min="1" max="100" value="10">
                    </div>
                    <div class="form-group">
                        <label for="compound-frequency">Compound Frequency</label>
                        <select id="compound-frequency">
                            <option value="1">Annually</option>
                            <option value="2">Semi-Annually</option>
                            <option value="4" selected>Quarterly</option>
                            <option value="12">Monthly</option>
                            <option value="365">Daily</option>
                        </select>
                    </div>
                    <div class="form-group full-width">
                        <button id="calculate-interest">Calculate</button>
                    </div>
                </div>
                
                <div class="calculator-results" id="calculator-results">
                    <h3 class="section-title">Projection Results</h3>
                    <div class="result-item">
                        <span class="result-label">Initial Investment:</span>
                        <span class="result-value" id="result-initial">GHS 0.00</span>
                    </div>
                    <div class="result-item">
                        <span class="result-label">Total Contributions:</span>
                        <span class="result-value" id="result-contributions">GHS 0.00</span>
                    </div>
                    <div class="result-item">
                        <span class="result-label">Total Interest Earned:</span>
                        <span class="result-value" id="result-interest">GHS 0.00</span>
                    </div>
                    <div class="result-highlight">
                        Final Balance: <span id="result-final">GHS 0.00</span>
                    </div>
                </div>
            </div>

            <div class="futuristic-card">
                <h2 class="section-title">Savings by Category</h2>
                <div class="category-management">
                    <div>
                        <h3>Add/Edit Category</h3>
                        <div class="form-group">
                            <label for="category-name">Category Name</label>
                            <input type="text" id="category-name" placeholder="Enter category name">
                        </div>
                        <div class="form-group">
                            <label for="category-target">Target Amount</label>
                            <input type="number" id="category-target" placeholder="Enter target amount">
                        </div>
                        <div class="form-group">
                            <label for="category-color">Color</label>
                            <input type="color" id="category-color" value="#6e44ff">
                        </div>
                        <div class="form-group">
                            <button id="save-category">Save Category</button>
                        </div>
                    </div>
                    <div>
                        <h3>Current Categories</h3>
                        <div class="savings-categories" id="savings-categories">
                            <!-- Categories will be populated by JavaScript -->
                        </div>
                    </div>
                </div>
            </div>

            <div class="futuristic-card">
                <h2 class="section-title">Add Savings</h2>
                <div class="form-group">
                    <label for="savings-amount-new">Amount</label>
                    <input type="number" id="savings-amount-new" placeholder="Enter amount">
                </div>
                <div class="form-group">
                    <label for="savings-category-new">Category</label>
                    <select id="savings-category-new">
                        <option value="general">General Savings</option>
                        <option value="emergency">Emergency Fund</option>
                        <option value="investment">Investment</option>
                        <option value="vacation">Vacation</option>
                        <option value="education">Education</option>
                        <option value="retirement">Retirement</option>
                    </select>
                </div>
                <div class="form-group">
                    <label for="savings-date-new">Date</label>
                    <input type="date" id="savings-date-new">
                </div>
                <div class="form-group">
                    <label for="savings-notes-new">Notes (Optional)</label>
                    <textarea id="savings-notes-new" rows="3" placeholder="Add any notes about this savings"></textarea>
                </div>
                <button id="add-savings-new">Add Savings</button>
            </div>

            <div class="futuristic-card">
                <h2 class="section-title">Recent Savings</h2>
                <div class="entry-list" id="recent-savings">
                    <div class="empty-state">
                        <i class="fas fa-piggy-bank"></i>
                        <p>No recent savings</p>
                    </div>
                </div>
            </div>
        </div>

        <!-- Investments Tab -->
        <div class="tab-content" id="investments">
            <div class="futuristic-card">
                <h2 class="section-title">Investment Portfolio</h2>
                <div class="stats-grid">
                    <div class="stat-card">
                        <h3>Total Portfolio</h3>
                        <p class="value digit" id="total-portfolio">GHS 0.00</p>
                    </div>
                    <div class="stat-card">
                        <h3>Total Return</h3>
                        <p class="value digit" id="total-return">GHS 0.00</p>
                    </div>
                    <div class="stat-card">
                        <h3>Return Rate</h3>
                        <p class="value" id="return-rate">0%</p>
                    </div>
                    <div class="stat-card">
                        <h3>Best Performer</h3>
                        <p class="value" id="best-performer">-</p>
                    </div>
                </div>
                
                <div class="performance-chart-container">
                    <canvas id="investment-performance-chart"></canvas>
                </div>
            </div>

            <div class="futuristic-card">
                <h2 class="section-title">Add Investment</h2>
                <div class="investment-form">
                    <div class="form-group">
                        <label for="investment-name">Investment Name</label>
                        <input type="text" id="investment-name" placeholder="e.g., Apple Stocks, Treasury Bonds">
                    </div>
                    <div class="form-group">
                        <label for="investment-type">Type</label>
                        <select id="investment-type">
                            <option value="stocks">Stocks</option>
                            <option value="bonds">Bonds</option>
                            <option value="real-estate">Real Estate</option>
                            <option value="crypto">Cryptocurrency</option>
                            <option value="mutual-funds">Mutual Funds</option>
                            <option value="etf">ETF</option>
                            <option value="other">Other</option>
                        </select>
                    </div>
                    <div class="form-group">
                        <label for="investment-amount">Amount Invested</label>
                        <input type="number" id="investment-amount" placeholder="Enter amount">
                    </div>
                    <div class="form-group">
                        <label for="investment-date">Date</label>
                        <input type="date" id="investment-date">
                    </div>
                    <div class="form-group">
                        <label for="investment-return">Expected Return (%)</label>
                        <input type="number" id="investment-return" placeholder="Enter expected return" step="0.01">
                    </div>
                    <div class="form-group">
                        <label for="investment-risk">Risk Level</label>
                        <select id="investment-risk">
                            <option value="low">Low</option>
                            <option value="medium">Medium</option>
                            <option value="high">High</option>
                        </select>
                    </div>
                    <div class="form-group full-width">
                        <label for="investment-notes">Notes (Optional)</label>
                        <textarea id="investment-notes" rows="3" placeholder="Add any notes about this investment"></textarea>
                    </div>
                    <div class="form-group full-width">
                        <button id="add-investment">Add Investment</button>
                    </div>
                </div>
            </div>

            <div class="futuristic-card">
                <h2 class="section-title">Your Investments</h2>
                <div class="entry-list" id="investments-list">
                    <div class="empty-state">
                        <i class="fas fa-chart-line"></i>
                        <p>No investments yet</p>
                    </div>
                </div>
            </div>
        </div>

        <!-- Goals & Achievements Tab -->
        <div class="tab-content" id="goals">
            <div class="futuristic-card">
                <h2 class="section-title">Financial Goals</h2>
                <div class="goal-form">
                    <div class="form-group">
                        <label for="goal-name">Goal Name</label>
                        <input type="text" id="goal-name" placeholder="e.g., New Car, Down Payment">
                    </div>
                    <div class="form-group">
                        <label for="goal-target">Target Amount</label>
                        <input type="number" id="goal-target" placeholder="Enter target amount">
                    </div>
                    <div class="form-group">
                        <label for="goal-deadline">Deadline</label>
                        <input type="date" id="goal-deadline">
                    </div>
                    <div class="form-group">
                        <label for="goal-category">Category</label>
                        <select id="goal-category">
                            <option value="short-term">Short Term (0-1 year)</option>
                            <option value="medium-term">Medium Term (1-5 years)</option>
                            <option value="long-term">Long Term (5+ years)</option>
                        </select>
                    </div>
                    <div class="form-group full-width">
                        <label for="goal-notes">Notes (Optional)</label>
                        <textarea id="goal-notes" rows="3" placeholder="Add any notes about this goal"></textarea>
                    </div>
                    <div class="form-group full-width">
                        <button id="add-goal">Add Goal</button>
                    </div>
                </div>
            </div>

            <div class="futuristic-card">
                <h2 class="section-title">Active Goals</h2>
                <div class="entry-list" id="active-goals">
                    <div class="empty-state">
                        <i class="fas fa-bullseye"></i>
                        <p>No active goals</p>
                    </div>
                </div>
            </div>

            <div class="futuristic-card">
                <h2 class="section-title">Achievements</h2>
                <div class="achievement-management">
                    <div>
                        <h3>Add/Edit Achievement</h3>
                        <div class="form-group">
                            <label for="achievement-name">Achievement Name</label>
                            <input type="text" id="achievement-name" placeholder="Enter achievement name">
                        </div>
                        <div class="form-group">
                            <label for="achievement-description">Description</label>
                            <textarea id="achievement-description" rows="3" placeholder="Enter achievement description"></textarea>
                        </div>
                        <div class="form-group">
                            <label for="achievement-icon">Icon Class</label>
                            <input type="text" id="achievement-icon" placeholder="e.g., fas fa-trophy" value="fas fa-trophy">
                        </div>
                        <div class="form-group">
                            <label for="achievement-target">Target Value</label>
                            <input type="number" id="achievement-target" placeholder="Enter target value">
                        </div>
                        <div class="form-group">
                            <label for="achievement-current">Current Progress</label>
                            <input type="number" id="achievement-current" placeholder="Enter current progress">
                        </div>
                        <div class="form-group">
                            <button id="save-achievement">Save Achievement</button>
                        </div>
                    </div>
                    <div>
                        <h3>Current Achievements</h3>
                        <div class="achievement-grid" id="achievements-grid">
                            <!-- Achievements will be populated by JavaScript -->
                        </div>
                    </div>
                </div>
            </div>
        </div>

        <!-- Subscriptions Tab -->
        <div class="tab-content" id="subscriptions">
            <div class="futuristic-card">
                <h2 class="section-title">Subscription Management</h2>
                <div class="stats-grid">
                    <div class="stat-card">
                        <h3>Monthly Cost</h3>
                        <p class="value digit" id="monthly-subscription-cost">GHS 0.00</p>
                    </div>
                    <div class="stat-card">
                        <h3>Yearly Cost</h3>
                        <p class="value digit" id="yearly-subscription-cost">GHS 0.00</p>
                    </div>
                    <div class="stat-card">
                        <h3>Active Subscriptions</h3>
                        <p class="value" id="active-subscriptions">0</p>
                    </div>
                    <div class="stat-card">
                        <h3>Next Renewal</h3>
                        <p class="value" id="next-renewal">-</p>
                    </div>
                </div>
            </div>

            <div class="futuristic-card">
                <h2 class="section-title">Add Subscription</h2>
                <div class="subscription-form">
                    <div class="form-group">
                        <label for="subscription-name">Service Name</label>
                        <input type="text" id="subscription-name" placeholder="e.g., Netflix, Spotify">
                    </div>
                    <div class="form-group">
                        <label for="subscription-cost">Monthly Cost</label>
                        <input type="number" id="subscription-cost" placeholder="Enter monthly cost">
                    </div>
                    <div class="form-group">
                        <label for="subscription-category">Category</label>
                        <select id="subscription-category">
                            <option value="entertainment">Entertainment</option>
                            <option value="productivity">Productivity</option>
                            <option value="utilities">Utilities</option>
                            <option value="education">Education</option>
                            <option value="health">Health & Fitness</option>
                            <option value="other">Other</option>
                        </select>
                    </div>
                    <div class="form-group">
                        <label for="subscription-renewal">Renewal Date</label>
                        <input type="date" id="subscription-renewal">
                    </div>
                    <div class="form-group">
                        <label for="subscription-status">Status</label>
                        <select id="subscription-status">
                            <option value="active">Active</option>
                            <option value="inactive">Inactive</option>
                            <option value="cancelled">Cancelled</option>
                        </select>
                    </div>
                    <div class="form-group full-width">
                        <label for="subscription-notes">Notes (Optional)</label>
                        <textarea id="subscription-notes" rows="3" placeholder="Add any notes about this subscription"></textarea>
                    </div>
                    <div class="form-group full-width">
                        <button id="add-subscription">Add Subscription</button>
                    </div>
                </div>
            </div>

            <div class="futuristic-card">
                <h2 class="section-title">Your Subscriptions</h2>
                <div class="entry-list" id="subscriptions-list">
                    <div class="empty-state">
                        <i class="fas fa-receipt"></i>
                        <p>No subscriptions yet</p>
                    </div>
                </div>
            </div>

            <div class="futuristic-card">
                <h2 class="section-title">Subscription Insights</h2>
                <div class="chart-container">
                    <canvas id="subscription-category-chart"></canvas>
                </div>
            </div>
        </div>

        <!-- Debtors Tab -->
        <div class="tab-content" id="debtors">
            <div class="futuristic-card">
                <h2 class="section-title">Debtors Management</h2>
                <div class="stats-grid">
                    <div class="stat-card">
                        <h3>Total Debt</h3>
                        <p class="value digit" id="total-debt">GHS 0.00</p>
                    </div>
                    <div class="stat-card">
                        <h3>Upcoming Payments</h3>
                        <p class="value" id="upcoming-payments">0</p>
                    </div>
                    <div class="stat-card">
                        <h3>Overdue</h3>
                        <p class="value" id="overdue-debt">GHS 0.00</p>
                    </div>
                    <div class="stat-card">
                        <h3>Next Payment</h3>
                        <p class="value" id="next-payment-date">-</p>
                    </div>
                </div>
            </div>

            <div class="futuristic-card">
                <h2 class="section-title">Add Debtor</h2>
                <div class="debtor-form">
                    <div class="form-group">
                        <label for="debtor-name">Creditor Name</label>
                        <input type="text" id="debtor-name" placeholder="Enter creditor name">
                    </div>
                    <div class="form-group">
                        <label for="debtor-amount">Amount</label>
                        <input type="number" id="debtor-amount" placeholder="Enter amount">
                    </div>
                    <div class="form-group">
                        <label for="debtor-due-date">Due Date</label>
                        <input type="date" id="debtor-due-date">
                    </div>
                    <div class="form-group">
                        <label for="debtor-category">Category</label>
                        <select id="debtor-category">
                            <option value="loan">Loan</option>
                            <option value="credit-card">Credit Card</option>
                            <option value="mortgage">Mortgage</option>
                            <option value="personal">Personal</option>
                            <option value="business">Business</option>
                            <option value="other">Other</option>
                        </select>
                    </div>
                    <div class="form-group">
                        <label for="debtor-interest">Interest Rate (%)</label>
                        <input type="number" id="debtor-interest" placeholder="Enter interest rate" step="0.01">
                    </div>
                    <div class="form-group">
                        <label for="debtor-installment">Installment Plan</label>
                        <select id="debtor-installment">
                            <option value="one-time">One-time Payment</option>
                            <option value="monthly">Monthly</option>
                            <option value="quarterly">Quarterly</option>
                            <option value="yearly">Yearly</option>
                        </select>
                    </div>
                    <div class="form-group full-width">
                        <label for="debtor-notes">Notes (Optional)</label>
                        <textarea id="debtor-notes" rows="3" placeholder="Add any notes about this debt"></textarea>
                    </div>
                    <div class="form-group full-width">
                        <button id="add-debtor">Add Debtor</button>
                    </div>
                </div>
            </div>

            <div class="futuristic-card">
                <h2 class="section-title">Upcoming Payments</h2>
                <div class="entry-list" id="upcoming-debtors">
                    <div class="empty-state">
                        <i class="fas fa-file-invoice-dollar"></i>
                        <p>No upcoming payments</p>
                    </div>
                </div>
            </div>

            <div class="futuristic-card">
                <h2 class="section-title">Debt History</h2>
                <div class="entry-list" id="debtor-history">
                    <div class="empty-state">
                        <i class="fas fa-history"></i>
                        <p>No debt history</p>
                    </div>
                </div>
            </div>
        </div>

        <!-- Creditors Tab -->
        <div class="tab-content" id="creditors">
            <div class="futuristic-card">
                <h2 class="section-title">Creditors Management</h2>
                <div class="stats-grid">
                    <div class="stat-card">
                        <h3>Total Amount Owed</h3>
                        <p class="value digit" id="total-owed">GHS 0.00</p>
                    </div>
                    <div class="stat-card">
                        <h3>Upcoming Collections</h3>
                        <p class="value" id="upcoming-collections">0</p>
                    </div>
                    <div class="stat-card">
                        <h3>Overdue</h3>
                        <p class="value" id="overdue-creditors">GHS 0.00</p>
                    </div>
                    <div class="stat-card">
                        <h3>Next Collection</h3>
                        <p class="value" id="next-collection-date">-</p>
                    </div>
                </div>
            </div>

            <div class="futuristic-card">
                <h2 class="section-title">Add Creditor</h2>
                <div class="creditor-form">
                    <div class="form-group">
                        <label for="creditor-name">Debtor Name</label>
                        <input type="text" id="creditor-name" placeholder="Enter debtor name">
                    </div>
                    <div class="form-group">
                        <label for="creditor-amount">Amount</label>
                        <input type="number" id="creditor-amount" placeholder="Enter amount">
                    </div>
                    <div class="form-group">
                        <label for="creditor-due-date">Due Date</label>
                        <input type="date" id="creditor-due-date">
                    </div>
                    <div class="form-group">
                        <label for="creditor-category">Category</label>
                        <select id="creditor-category">
                            <option value="loan">Loan</option>
                            <option value="personal">Personal</option>
                            <option value="business">Business</option>
                            <option value="investment">Investment</option>
                            <option value="other">Other</option>
                        </select>
                    </div>
                    <div class="form-group">
                        <label for="creditor-interest">Interest Rate (%)</label>
                        <input type="number" id="creditor-interest" placeholder="Enter interest rate" step="0.01">
                    </div>
                    <div class="form-group">
                        <label for="creditor-installment">Payment Plan</label>
                        <select id="creditor-installment">
                            <option value="one-time">One-time Payment</option>
                            <option value="monthly">Monthly</option>
                            <option value="quarterly">Quarterly</option>
                            <option value="yearly">Yearly</option>
                        </select>
                    </div>
                    <div class="form-group full-width">
                        <label for="creditor-notes">Notes (Optional)</label>
                        <textarea id="creditor-notes" rows="3" placeholder="Add any notes about this credit"></textarea>
                    </div>
                    <div class="form-group full-width">
                        <button id="add-creditor">Add Creditor</button>
                    </div>
                </div>
            </div>

            <div class="futuristic-card">
                <h2 class="section-title">Upcoming Collections</h2>
                <div class="entry-list" id="upcoming-creditors">
                    <div class="empty-state">
                        <i class="fas fa-hand-holding-usd"></i>
                        <p>No upcoming collections</p>
                    </div>
                </div>
            </div>

            <div class="futuristic-card">
                <h2 class="section-title">Collection History</h2>
                <div class="entry-list" id="creditor-history">
                    <div class="empty-state">
                        <i class="fas fa-history"></i>
                        <p>No collection history</p>
                    </div>
                </div>
            </div>
        </div>

        <!-- Financial Calendar Tab -->
        <div class="tab-content" id="calendar">
            <div class="calendar-container">
                <div class="calendar-header">
                    <h2 class="calendar-title">Financial Calendar - <span id="current-month-name">January</span></h2>
                    <div class="navigation-buttons">
                        <button class="nav-btn" id="prev-month"><i class="fas fa-chevron-left"></i> Previous</button>
                        <button class="nav-btn" id="next-month">Next <i class="fas fa-chevron-right"></i></button>
                    </div>
                </div>
                <div class="calendar">
                    <!-- Calendar days will be generated by JavaScript -->
                </div>
            </div>

            <div class="futuristic-card">
                <h2 class="section-title">Add Savings Entry</h2>
                <div class="form-group">
                    <label for="savings-date">Date</label>
                    <input type="date" id="savings-date">
                </div>
                <div class="form-group">
                    <label for="savings-amount">Amount</label>
                    <input type="number" id="savings-amount" placeholder="Enter amount">
                </div>
                <div class="form-group">
                    <label for="savings-category">Category</label>
                    <select id="savings-category">
                        <option value="general">General Savings</option>
                        <option value="emergency">Emergency Fund</option>
                        <option value="investment">Investment</option>
                        <option value="vacation">Vacation</option>
                        <option value="education">Education</option>
                        <option value="retirement">Retirement</option>
                    </select>
                </div>
                <div class="form-group">
                    <label for="savings-notes">Notes (Optional)</label>
                    <textarea id="savings-notes" rows="3" placeholder="Add any notes about this savings entry"></textarea>
                </div>
                <button id="add-savings">Add Savings</button>
            </div>
        </div>

        <!-- Bill Tracking Tab -->
        <div class="tab-content" id="bills">
            <div class="futuristic-card">
                <h2 class="section-title">Bill Tracking</h2>
                <div class="bill-form">
                    <div class="form-group">
                        <label for="bill-name">Bill Name</label>
                        <input type="text" id="bill-name" placeholder="Enter bill name">
                    </div>
                    <div class="form-group">
                        <label for="bill-amount">Amount</label>
                        <input type="number" id="bill-amount" placeholder="Enter amount">
                    </div>
                    <div class="form-group">
                        <label for="bill-due-date">Due Date</label>
                        <input type="date" id="bill-due-date">
                    </div>
                    <div class="form-group">
                        <label for="bill-category">Category</label>
                        <select id="bill-category">
                            <option value="utilities">Utilities</option>
                            <option value="rent">Rent/Mortgage</option>
                            <option value="insurance">Insurance</option>
                            <option value="subscription">Subscription</option>
                            <option value="loan">Loan</option>
                            <option value="other">Other</option>
                        </select>
                    </div>
                    <div class="form-group full-width">
                        <label for="bill-notes">Notes (Optional)</label>
                        <textarea id="bill-notes" rows="3" placeholder="Add any notes about this bill"></textarea>
                    </div>
                    <div class="form-group full-width">
                        <button id="add-bill">Add Bill</button>
                    </div>
                </div>
            </div>

            <div class="futuristic-card">
                <h2 class="section-title">Upcoming Bills</h2>
                <div class="entry-list" id="upcoming-bills">
                    <div class="empty-state">
                        <i class="fas fa-file-invoice-dollar"></i>
                        <p>No upcoming bills</p>
                    </div>
                </div>
            </div>

            <div class="futuristic-card">
                <h2 class="section-title">Bill History</h2>
                <div class="entry-list" id="bill-history">
                    <div class="empty-state">
                        <i class="fas fa-history"></i>
                        <p>No bill history</p>
                    </div>
                </div>
            </div>
        </div>

        <!-- AI Financial Advisor Tab -->
        <div class="tab-content" id="advisor">
            <div class="futuristic-card">
                <h2 class="section-title">AI Financial Advisor</h2>
                <p>Get personalized investment advice based on your financial goals, risk tolerance, and location.</p>
                
                <div class="form-group">
                    <label for="country-select">Select Your Country</label>
                    <select id="country-select">
                        <option value="GH" selected>Ghana</option>
                        <option value="NG">Nigeria</option>
                        <option value="KE">Kenya</option>
                        <option value="ZA">South Africa</option>
                        <option value="US">United States</option>
                        <option value="GB">United Kingdom</option>
                        <option value="CA">Canada</option>
                        <option value="AU">Australia</option>
                    </select>
                </div>

                <div class="risk-assessment">
                    <h3 class="section-title">Risk Assessment</h3>
                    <div class="risk-question">
                        <p>1. What is your investment time horizon?</p>
                        <div class="risk-options">
                            <div class="risk-option" data-value="1">
                                <input type="radio" name="time-horizon" id="time-1" style="display: none;">
                                <label for="time-1">Less than 1 year</label>
                            </div>
                            <div class="risk-option" data-value="2">
                                <input type="radio" name="time-horizon" id="time-2" style="display: none;">
                                <label for="time-2">1-3 years</label>
                            </div>
                            <div class="risk-option" data-value="3">
                                <input type="radio" name="time-horizon" id="time-3" style="display: none;">
                                <label for="time-3">3-5 years</label>
                            </div>
                            <div class="risk-option" data-value="4">
                                <input type="radio" name="time-horizon" id="time-4" style="display: none;">
                                <label for="time-4">5-10 years</label>
                            </div>
                            <div class="risk-option" data-value="5">
                                <input type="radio" name="time-horizon" id="time-5" style="display: none;">
                                <label for="time-5">More than 10 years</label>
                            </div>
                        </div>
                    </div>
                    
                    <div class="risk-question">
                        <p>2. How would you react if your investment lost 20% of its value in a short period?</p>
                        <div class="risk-options">
                            <div class="risk-option" data-value="1">
                                <input type="radio" name="reaction" id="react-1" style="display: none;">
                                <label for="react-1">Sell all investments immediately</label>
                            </div>
                            <div class="risk-option" data-value="2">
                                <input type="radio" name="reaction" id="react-2" style="display: none;">
                                <label for="react-2">Sell some investments</label>
                            </div>
                            <div class="risk-option" data-value="3">
                                <input type="radio" name="reaction" id="react-3" style="display: none;">
                                <label for="react-3">Do nothing</label>
                            </div>
                            <div class="risk-option" data-value="4">
                                <input type="radio" name="reaction" id="react-4" style="display: none;">
                                <label for="react-4">Invest more to take advantage of lower prices</label>
                            </div>
                        </div>
                    </div>
                    
                    <div class="risk-question">
                        <p>3. What percentage of your income are you willing to invest?</p>
                        <div class="risk-options">
                            <div class="risk-option" data-value="1">
                                <input type="radio" name="income-percent" id="income-1" style="display: none;">
                                <label for="income-1">Less than 5%</label>
                            </div>
                            <div class="risk-option" data-value="2">
                                <input type="radio" name="income-percent" id="income-2" style="display: none;">
                                <label for="income-2">5-10%</label>
                            </div>
                            <div class="risk-option" data-value="3">
                                <input type="radio" name="income-percent" id="income-3" style="display: none;">
                                <label for="income-3">10-20%</label>
                            </div>
                            <div class="risk-option" data-value="4">
                                <input type="radio" name="income-percent" id="income-4" style="display: none;">
                                <label for="income-4">More than 20%</label>
                            </div>
                        </div>
                    </div>
                    
                    <button id="assess-risk">Assess My Risk Profile</button>
                    
                    <div class="risk-result" id="risk-result">
                        <h3>Your Risk Profile: <span id="risk-level">Low</span></h3>
                        <p id="risk-description">Based on your answers, you have a low risk tolerance. We recommend conservative investments.</p>
                    </div>
                </div>

                <div class="investment-questions">
                    <h3 class="section-title">Investment Preferences</h3>
                    <div class="investment-question">
                        <p>What type of investments are you interested in?</p>
                        <div class="investment-options">
                            <div class="investment-option" data-value="stocks">
                                <i class="fas fa-chart-line"></i>
                                <p>Stocks</p>
                            </div>
                            <div class="investment-option" data-value="bonds">
                                <i class="fas fa-file-contract"></i>
                                <p>Bonds</p>
                            </div>
                            <div class="investment-option" data-value="real-estate">
                                <i class="fas fa-home"></i>
                                <p>Real Estate</p>
                            </div>
                            <div class="investment-option" data-value="crypto">
                                <i class="fab fa-bitcoin"></i>
                                <p>Cryptocurrency</p>
                            </div>
                            <div class="investment-option" data-value="mutual-funds">
                                <i class="fas fa-piggy-bank"></i>
                                <p>Mutual Funds</p>
                            </div>
                            <div class="investment-option" data-value="business">
                                <i class="fas fa-briefcase"></i>
                                <p>Business Ventures</p>
                            </div>
                        </div>
                    </div>
                    
                    <button id="get-advice">Get AI Investment Advice</button>
                </div>

                <div class="ai-response" id="ai-response">
                    <div class="ai-response-header">
                        <i class="fas fa-robot ai-response-icon"></i>
                        <h3 class="ai-response-title">AI Investment Advice</h3>
                    </div>
                    <div class="ai-response-content" id="ai-response-content">
                        <!-- AI response will be inserted here -->
                    </div>
                </div>
            </div>

            <div class="futuristic-card">
                <h2 class="section-title">Investment Opportunities in <span id="selected-country-name">Ghana</span></h2>
                <div class="recommendation-grid" id="investment-opportunities">
                    <!-- Investment opportunities will be populated by JavaScript -->
                </div>
            </div>

            <div class="advisor-chat">
                <h2 class="section-title">Chat with Financial Advisor</h2>
                <div class="chat-container">
                    <div class="chat-messages" id="chat-messages">
                        <div class="chat-message ai-message">
                            <p>Hello! I'm your AI Financial Advisor. How can I help you with your investment goals today?</p>
                        </div>
                    </div>
                    <div class="chat-input-container">
                        <input type="text" class="chat-input" id="chat-input" placeholder="Ask me about investments...">
                        <button class="chat-send-btn" id="chat-send"><i class="fas fa-paper-plane"></i></button>
                    </div>
                </div>
            </div>
        </div>

        <!-- Analytics Tab -->
        <div class="tab-content" id="analytics">
            <div class="futuristic-card">
                <h2 class="section-title">Financial Analytics</h2>
                <div class="analytics-grid">
                    <div class="analytics-card">
                        <h3 class="section-title">Savings Trends</h3>
                        <div class="analytics-chart-container">
                            <canvas id="savings-analytics-chart"></canvas>
                        </div>
                        <div class="analytics-stats">
                            <div class="analytics-stat">
                                <div class="value" id="avg-monthly-saving">GHS 0.00</div>
                                <div class="label">Avg Monthly Saving</div>
                            </div>
                            <div class="analytics-stat">
                                <div class="value" id="savings-growth">0%</div>
                                <div class="label">Savings Growth</div>
                            </div>
                            <div class="analytics-stat">
                                <div class="value" id="savings-consistency">0%</div>
                                <div class="label">Consistency</div>
                            </div>
                        </div>
                    </div>
                    <div class="analytics-card">
                        <h3 class="section-title">Expense Analysis</h3>
                        <div class="analytics-chart-container">
                            <canvas id="expense-analytics-chart"></canvas>
                        </div>
                        <div class="analytics-stats">
                            <div class="analytics-stat">
                                <div class="value" id="largest-expense">GHS 0.00</div>
                                <div class="label">Largest Expense</div>
                            </div>
                            <div class="analytics-stat">
                                <div class="value" id="expense-trend">0%</div>
                                <div class="label">Expense Trend</div>
                            </div>
                            <div class="analytics-stat">
                                <div class="value" id="savings-ratio">0%</div>
                                <div class="label">Savings Ratio</div>
                            </div>
                        </div>
                    </div>
                </div>
            </div>

            <div class="futuristic-card">
                <h2 class="section-title">Investment Performance</h2>
                <div class="analytics-grid">
                    <div class="analytics-card">
                        <h3 class="section-title">Portfolio Allocation</h3>
                        <div class="analytics-chart-container">
                            <canvas id="portfolio-allocation-chart"></canvas>
                        </div>
                    </div>
                    <div class="analytics-card">
                        <h3 class="section-title">Risk vs Return</h3>
                        <div class="analytics-chart-container">
                            <canvas id="risk-return-chart"></canvas>
                        </div>
                    </div>
                </div>
            </div>

            <div class="futuristic-card">
                <h2 class="section-title">Financial Health Score</h2>
                <div class="analytics-grid">
                    <div class="analytics-card">
                        <h3 class="section-title">Overall Score</h3>
                        <div style="text-align: center; padding: 20px;">
                            <div style="font-size: 48px; font-weight: bold; color: var(--accent); margin-bottom: 10px;" id="financial-score">75</div>
                            <div style="font-size: 18px; color: var(--secondary);">Good Financial Health</div>
                            <div class="progress-bar" style="margin: 20px auto; width: 80%;">
                                <div class="progress-fill" style="width: 75%"></div>
                            </div>
                        </div>
                    </div>
                    <div class="analytics-card">
                        <h3 class="section-title">Key Metrics</h3>
                        <div class="analytics-stats">
                            <div class="analytics-stat">
                                <div class="value" id="emergency-fund-score">8/10</div>
                                <div class="label">Emergency Fund</div>
                            </div>
                            <div class="analytics-stat">
                                <div class="value" id="debt-score">7/10</div>
                                <div class="label">Debt Management</div>
                            </div>
                            <div class="analytics-stat">
                                <div class="value" id="savings-score">6/10</div>
                                <div class="label">Savings Rate</div>
                            </div>
                            <div class="analytics-stat">
                                <div class="value" id="investment-score">9/10</div>
                                <div class="label">Investment</div>
                            </div>
                            <div class="analytics-stat">
                                <div class="value" id="budget-score">8/10</div>
                                <div class="label">Budgeting</div>
                            </div>
                            <div class="analytics-stat">
                                <div class="value" id="goal-score">7/10</div>
                                <div class="label">Goal Progress</div>
                            </div>
                        </div>
                    </div>
                </div>
            </div>
        </div>

        <!-- History Tab -->
        <div class="tab-content" id="history">
            <div class="futuristic-card">
                <h2 class="section-title">Activity History</h2>
                <div class="time-filters">
                    <div class="time-filter active" data-filter="all">All Time</div>
                    <div class="time-filter" data-filter="month">This Month</div>
                    <div class="time-filter" data-filter="year">This Year</div>
                    <div class="time-filter" data-filter="week">This Week</div>
                </div>
                <div class="history-entries" id="activity-history">
                    <div class="empty-state">
                        <i class="fas fa-history"></i>
                        <p>No activity history</p>
                    </div>
                </div>
            </div>

            <div class="futuristic-card">
                <h2 class="section-title">Export Data</h2>
                <div class="export-options">
                    <button class="export-btn" id="export-csv"><i class="fas fa-file-csv"></i> Export as CSV</button>
                    <button class="export-btn" id="export-pdf"><i class="fas fa-file-pdf"></i> Export as PDF</button>
                </div>
            </div>
        </div>

        <!-- Settings Tab -->
        <div class="tab-content" id="settings">
            <div class="futuristic-card">
                <h2 class="section-title">App Settings</h2>
                <div class="form-group">
                    <label for="monthly-target">Monthly Savings Target</label>
                    <input type="number" id="monthly-target" placeholder="Enter monthly target">
                </div>
                <div class="form-group">
                    <label for="savings-reminder">Savings Reminder</label>
                    <select id="savings-reminder">
                        <option value="disabled">Disabled</option>
                        <option value="daily">Daily</option>
                        <option value="weekly" selected>Weekly</option>
                        <option value="monthly">Monthly</option>
                    </select>
                </div>
                <div class="form-group">
                    <label for="theme">Theme</label>
                    <select id="theme">
                        <option value="dark" selected>Dark</option>
                        <option value="light">Light</option>
                        <option value="auto">Auto</option>
                    </select>
                </div>
                <button id="save-settings">Save Settings</button>
            </div>

            <div class="futuristic-card">
                <h2 class="section-title">Data Management</h2>
                <div class="form-group">
                    <button class="secondary" id="backup-data"><i class="fas fa-download"></i> Backup Data</button>
                </div>
                <div class="form-group">
                    <button class="secondary" id="restore-data"><i class="fas fa-upload"></i> Restore Data</button>
                </div>
                <div class="form-group">
                    <button class="secondary" id="reset-data"><i class="fas fa-trash"></i> Reset All Data</button>
                </div>
            </div>
        </div>
    </div>

    <!-- Notification -->
    <div class="notification" id="notification">
        <span id="notification-text">This is a notification</span>
    </div>

    <script>
        // App Data
        let appData = {
            currency: 'GHS',
            monthlyTarget: 1000,
            savings: [],
            investments: [],
            goals: [],
            subscriptions: [],
            bills: [],
            debtors: [],
            creditors: [],
            achievements: {
                firstSaver: { id: 'firstSaver', name: 'First Saver', description: 'Save your first GHS 100', icon: 'fas fa-seedling', target: 100, current: 100, unlocked: true },
                consistentSaver: { id: 'consistentSaver', name: 'Consistent Saver', description: 'Save for 30 consecutive days', icon: 'fas fa-calendar-check', target: 30, current: 30, unlocked: true },
                mountainMover: { id: 'mountainMover', name: 'Mountain Mover', description: 'Save GHS 10,000 in total', icon: 'fas fa-mountain', target: 10000, current: 4500, unlocked: false },
                goalCrusher: { id: 'goalCrusher', name: 'Goal Crusher', description: 'Complete 5 financial goals', icon: 'fas fa-gem', target: 5, current: 2, unlocked: false },
                diversifiedInvestor: { id: 'diversifiedInvestor', name: 'Diversified Investor', description: 'Invest in 3 different asset classes', icon: 'fas fa-chart-pie', target: 3, current: 1, unlocked: false },
                financialGuardian: { id: 'financialGuardian', name: 'Financial Guardian', description: 'Build a 6-month emergency fund', icon: 'fas fa-shield-alt', target: 6, current: 1.5, unlocked: false }
            },
            savingsCategories: {
                emergency: { id: 'emergency', name: 'Emergency Fund', target: 2000, current: 1500, color: '#00e5ff' },
                vacation: { id: 'vacation', name: 'Vacation', target: 2000, current: 800, color: '#00ff9d' },
                education: { id: 'education', name: 'Education', target: 10000, current: 2300, color: '#ffc400' },
                retirement: { id: 'retirement', name: 'Retirement', target: 50000, current: 5600, color: '#ff3860' }
            },
            activityHistory: [],
            settings: {
                savingsReminder: 'weekly',
                theme: 'dark'
            },
            riskProfile: 'low',
            investmentPreferences: []
        };

        // DOM Elements
        const tabs = document.querySelectorAll('.tab');
        const tabContents = document.querySelectorAll('.tab-content');
        const currencySelect = document.getElementById('currency-select');
        const notification = document.getElementById('notification');
        const notificationText = document.getElementById('notification-text');
        
        // Interest Calculator Elements
        const initialAmount = document.getElementById('initial-amount');
        const monthlyContribution = document.getElementById('monthly-contribution');
        const interestRate = document.getElementById('interest-rate');
        const investmentPeriod = document.getElementById('investment-period');
        const compoundFrequency = document.getElementById('compound-frequency');
        const calculateInterestBtn = document.getElementById('calculate-interest');
        const calculatorResults = document.getElementById('calculator-results');
        const resultInitial = document.getElementById('result-initial');
        const resultContributions = document.getElementById('result-contributions');
        const resultInterest = document.getElementById('result-interest');
        const resultFinal = document.getElementById('result-final');
        
        // Dashboard elements
        const totalSavingsEl = document.getElementById('total-savings');
        const monthlyGoalEl = document.getElementById('monthly-goal');
        const currentMonthEl = document.getElementById('current-month');
        const goalProgressEl = document.getElementById('goal-progress');
        const recentTransactionsList = document.getElementById('recent-transactions');
        
        // Savings tab elements
        const savingsAmountNew = document.getElementById('savings-amount-new');
        const savingsCategoryNew = document.getElementById('savings-category-new');
        const savingsDateNew = document.getElementById('savings-date-new');
        const savingsNotesNew = document.getElementById('savings-notes-new');
        const addSavingsNewBtn = document.getElementById('add-savings-new');
        const recentSavingsList = document.getElementById('recent-savings');
        const totalSavingsOverview = document.getElementById('total-savings-overview');
        const monthlySavingsGoal = document.getElementById('monthly-savings-goal');
        const savingsRate = document.getElementById('savings-rate');
        const emergencyFund = document.getElementById('emergency-fund');
        
        // Category management elements
        const categoryName = document.getElementById('category-name');
        const categoryTarget = document.getElementById('category-target');
        const categoryColor = document.getElementById('category-color');
        const saveCategoryBtn = document.getElementById('save-category');
        const savingsCategoriesList = document.getElementById('savings-categories');
        
        // Investments tab elements
        const investmentName = document.getElementById('investment-name');
        const investmentType = document.getElementById('investment-type');
        const investmentAmount = document.getElementById('investment-amount');
        const investmentDate = document.getElementById('investment-date');
        const investmentReturn = document.getElementById('investment-return');
        const investmentRisk = document.getElementById('investment-risk');
        const investmentNotes = document.getElementById('investment-notes');
        const addInvestmentBtn = document.getElementById('add-investment');
        const investmentsList = document.getElementById('investments-list');
        const totalPortfolio = document.getElementById('total-portfolio');
        const totalReturn = document.getElementById('total-return');
        const returnRate = document.getElementById('return-rate');
        const bestPerformer = document.getElementById('best-performer');
        
        // Goals tab elements
        const goalName = document.getElementById('goal-name');
        const goalTarget = document.getElementById('goal-target');
        const goalDeadline = document.getElementById('goal-deadline');
        const goalCategory = document.getElementById('goal-category');
        const goalNotes = document.getElementById('goal-notes');
        const addGoalBtn = document.getElementById('add-goal');
        const activeGoalsList = document.getElementById('active-goals');
        const achievementsGrid = document.getElementById('achievements-grid');
        
        // Achievement management elements
        const achievementName = document.getElementById('achievement-name');
        const achievementDescription = document.getElementById('achievement-description');
        const achievementIcon = document.getElementById('achievement-icon');
        const achievementTarget = document.getElementById('achievement-target');
        const achievementCurrent = document.getElementById('achievement-current');
        const saveAchievementBtn = document.getElementById('save-achievement');
        
        // Subscriptions tab elements
        const subscriptionName = document.getElementById('subscription-name');
        const subscriptionCost = document.getElementById('subscription-cost');
        const subscriptionCategory = document.getElementById('subscription-category');
        const subscriptionRenewal = document.getElementById('subscription-renewal');
        const subscriptionStatus = document.getElementById('subscription-status');
        const subscriptionNotes = document.getElementById('subscription-notes');
        const addSubscriptionBtn = document.getElementById('add-subscription');
        const subscriptionsList = document.getElementById('subscriptions-list');
        const monthlySubscriptionCost = document.getElementById('monthly-subscription-cost');
        const yearlySubscriptionCost = document.getElementById('yearly-subscription-cost');
        const activeSubscriptions = document.getElementById('active-subscriptions');
        const nextRenewal = document.getElementById('next-renewal');
        
        // Debtors tab elements
        const debtorName = document.getElementById('debtor-name');
        const debtorAmount = document.getElementById('debtor-amount');
        const debtorDueDate = document.getElementById('debtor-due-date');
        const debtorCategory = document.getElementById('debtor-category');
        const debtorInterest = document.getElementById('debtor-interest');
        const debtorInstallment = document.getElementById('debtor-installment');
        const debtorNotes = document.getElementById('debtor-notes');
        const addDebtorBtn = document.getElementById('add-debtor');
        const upcomingDebtorsList = document.getElementById('upcoming-debtors');
        const debtorHistoryList = document.getElementById('debtor-history');
        const totalDebt = document.getElementById('total-debt');
        const upcomingPayments = document.getElementById('upcoming-payments');
        const overdueDebt = document.getElementById('overdue-debt');
        const nextPaymentDate = document.getElementById('next-payment-date');
        
        // Creditors tab elements
        const creditorName = document.getElementById('creditor-name');
        const creditorAmount = document.getElementById('creditor-amount');
        const creditorDueDate = document.getElementById('creditor-due-date');
        const creditorCategory = document.getElementById('creditor-category');
        const creditorInterest = document.getElementById('creditor-interest');
        const creditorInstallment = document.getElementById('creditor-installment');
        const creditorNotes = document.getElementById('creditor-notes');
        const addCreditorBtn = document.getElementById('add-creditor');
        const upcomingCreditorsList = document.getElementById('upcoming-creditors');
        const creditorHistoryList = document.getElementById('creditor-history');
        const totalOwed = document.getElementById('total-owed');
        const upcomingCollections = document.getElementById('upcoming-collections');
        const overdueCreditors = document.getElementById('overdue-creditors');
        const nextCollectionDate = document.getElementById('next-collection-date');
        
        // Calendar tab elements
        const savingsDate = document.getElementById('savings-date');
        const savingsAmount = document.getElementById('savings-amount');
        const savingsCategory = document.getElementById('savings-category');
        const savingsNotes = document.getElementById('savings-notes');
        const addSavingsBtn = document.getElementById('add-savings');
        const calendar = document.querySelector('.calendar');
        const prevMonthBtn = document.getElementById('prev-month');
        const nextMonthBtn = document.getElementById('next-month');
        const currentMonthName = document.getElementById('current-month-name');
        
        // Bill Tracking tab elements
        const billName = document.getElementById('bill-name');
        const billAmount = document.getElementById('bill-amount');
        const billDueDate = document.getElementById('bill-due-date');
        const billCategory = document.getElementById('bill-category');
        const billNotes = document.getElementById('bill-notes');
        const addBillBtn = document.getElementById('add-bill');
        const upcomingBillsList = document.getElementById('upcoming-bills');
        const billHistoryList = document.getElementById('bill-history');
        
        // AI Financial Advisor tab elements
        const countrySelect = document.getElementById('country-select');
        const riskOptions = document.querySelectorAll('.risk-option');
        const assessRiskBtn = document.getElementById('assess-risk');
        const riskResult = document.getElementById('risk-result');
        const riskLevel = document.getElementById('risk-level');
        const riskDescription = document.getElementById('risk-description');
        const investmentOptions = document.querySelectorAll('.investment-option');
        const getAdviceBtn = document.getElementById('get-advice');
        const aiResponse = document.getElementById('ai-response');
        const aiResponseContent = document.getElementById('ai-response-content');
        const selectedCountryName = document.getElementById('selected-country-name');
        const chatMessages = document.getElementById('chat-messages');
        const chatInput = document.getElementById('chat-input');
        const chatSendBtn = document.getElementById('chat-send');
        
        // Analytics tab elements
        const savingsAnalyticsChart = document.getElementById('savings-analytics-chart');
        const expenseAnalyticsChart = document.getElementById('expense-analytics-chart');
        const portfolioAllocationChart = document.getElementById('portfolio-allocation-chart');
        const riskReturnChart = document.getElementById('risk-return-chart');
        const avgMonthlySaving = document.getElementById('avg-monthly-saving');
        const savingsGrowth = document.getElementById('savings-growth');
        const savingsConsistency = document.getElementById('savings-consistency');
        const largestExpense = document.getElementById('largest-expense');
        const expenseTrend = document.getElementById('expense-trend');
        const savingsRatio = document.getElementById('savings-ratio');
        const financialScore = document.getElementById('financial-score');
        const emergencyFundScore = document.getElementById('emergency-fund-score');
        const debtScore = document.getElementById('debt-score');
        const savingsScore = document.getElementById('savings-score');
        const investmentScore = document.getElementById('investment-score');
        const budgetScore = document.getElementById('budget-score');
        const goalScore = document.getElementById('goal-score');
        
        // History tab elements
        const activityHistoryList = document.getElementById('activity-history');
        const timeFilters = document.querySelectorAll('.time-filter');
        const exportCsvBtn = document.getElementById('export-csv');
        const exportPdfBtn = document.getElementById('export-pdf');
        
        // Settings tab elements
        const monthlyTargetInput = document.getElementById('monthly-target');
        const savingsReminderSelect = document.getElementById('savings-reminder');
        const themeSelect = document.getElementById('theme');
        const saveSettingsBtn = document.getElementById('save-settings');
        const backupDataBtn = document.getElementById('backup-data');
        const restoreDataBtn = document.getElementById('restore-data');
        const resetDataBtn = document.getElementById('reset-data');

        // Current date
        let currentDate = new Date();
        let currentMonth = currentDate.getMonth();
        let currentYear = currentDate.getFullYear();

        // Initialize the app
        function initApp() {
            // Set current date in forms
            const today = new Date().toISOString().split('T')[0];
            savingsDateNew.value = today;
            investmentDate.value = today;
            subscriptionRenewal.value = today;
            savingsDate.value = today;
            billDueDate.value = today;
            goalDeadline.value = today;
            debtorDueDate.value = today;
            creditorDueDate.value = today;
            
            // Set current month name
            currentMonthName.textContent = getMonthName(currentMonth);
            currentMonthEl.textContent = getMonthName(currentMonth);
            
            // Load saved data from localStorage
            loadData();
            
            // Generate calendar
            generateCalendar(currentMonth, currentYear);
            
            // Update all tabs
            updateDashboard();
            updateSavingsTab();
            updateInvestmentsTab();
            updateGoalsTab();
            updateSubscriptionsTab();
            updateDebtorsTab();
            updateCreditorsTab();
            updateBillsList();
            updateAnalyticsTab();
            updateHistoryTab();
            
            // Set up event listeners
            setupEventListeners();
            
            // Show notification
            showNotification('Welcome to Elite Finance & Investment! Your financial companion for success.', 'success');
        }

        // Set up event listeners
        function setupEventListeners() {
            // Tab navigation
            tabs.forEach(tab => {
                tab.addEventListener('click', () => {
                    const tabId = tab.getAttribute('data-tab');
                    switchTab(tabId);
                });
            });
            
            // Currency change
            currencySelect.addEventListener('change', () => {
                appData.currency = currencySelect.value;
                updateDashboard();
                updateSavingsTab();
                updateInvestmentsTab();
                updateDebtorsTab();
                updateCreditorsTab();
                updateAnalyticsTab();
                saveData();
            });
            
            // Interest Calculator
            calculateInterestBtn.addEventListener('click', calculateInterest);
            
            // Savings tab
            addSavingsNewBtn.addEventListener('click', addSavingsNew);
            
            // Category management
            saveCategoryBtn.addEventListener('click', saveCategory);
            
            // Investments tab
            addInvestmentBtn.addEventListener('click', addInvestment);
            
            // Goals tab
            addGoalBtn.addEventListener('click', addGoal);
            
            // Achievement management
            saveAchievementBtn.addEventListener('click', saveAchievement);
            
            // Subscriptions tab
            addSubscriptionBtn.addEventListener('click', addSubscription);
            
            // Debtors tab
            addDebtorBtn.addEventListener('click', addDebtor);
            
            // Creditors tab
            addCreditorBtn.addEventListener('click', addCreditor);
            
            // Calendar tab
            addSavingsBtn.addEventListener('click', addSavings);
            prevMonthBtn.addEventListener('click', () => {
                currentMonth--;
                if (currentMonth < 0) {
                    currentMonth = 11;
                    currentYear--;
                }
                generateCalendar(currentMonth, currentYear);
            });
            
            nextMonthBtn.addEventListener('click', () => {
                currentMonth++;
                if (currentMonth > 11) {
                    currentMonth = 0;
                    currentYear++;
                }
                generateCalendar(currentMonth, currentYear);
            });
            
            // Bill Tracking tab
            addBillBtn.addEventListener('click', addBill);
            
            // AI Financial Advisor tab
            riskOptions.forEach(option => {
                option.addEventListener('click', () => {
                    const radio = option.querySelector('input[type="radio"]');
                    radio.checked = true;
                    
                    // Update UI
                    const parent = option.parentElement;
                    const options = parent.querySelectorAll('.risk-option');
                    options.forEach(opt => opt.classList.remove('selected'));
                    option.classList.add('selected');
                });
            });
            
            assessRiskBtn.addEventListener('click', assessRisk);
            
            investmentOptions.forEach(option => {
                option.addEventListener('click', () => {
                    option.classList.toggle('selected');
                });
            });
            
            getAdviceBtn.addEventListener('click', getInvestmentAdvice);
            
            countrySelect.addEventListener('change', () => {
                const selectedOption = countrySelect.options[countrySelect.selectedIndex];
                selectedCountryName.textContent = selectedOption.text;
                updateInvestmentOpportunities();
            });
            
            chatSendBtn.addEventListener('click', sendChatMessage);
            chatInput.addEventListener('keypress', (e) => {
                if (e.key === 'Enter') {
                    sendChatMessage();
                }
            });
            
            // History tab
            timeFilters.forEach(filter => {
                filter.addEventListener('click', () => {
                    timeFilters.forEach(f => f.classList.remove('active'));
                    filter.classList.add('active');
                    const timeFilter = filter.getAttribute('data-filter');
                    filterActivityHistory(timeFilter);
                });
            });
            
            exportCsvBtn.addEventListener('click', exportToCsv);
            exportPdfBtn.addEventListener('click', exportToPdf);
            
            // Settings tab
            saveSettingsBtn.addEventListener('click', saveSettings);
            backupDataBtn.addEventListener('click', backupData);
            restoreDataBtn.addEventListener('click', restoreData);
            resetDataBtn.addEventListener('click', resetData);
        }

        // Interest Calculator Function
        function calculateInterest() {
            const principal = parseFloat(initialAmount.value) || 0;
            const monthlyDeposit = parseFloat(monthlyContribution.value) || 0;
            const annualRate = parseFloat(interestRate.value) || 0;
            const years = parseInt(investmentPeriod.value) || 1;
            const compoundsPerYear = parseInt(compoundFrequency.value) || 1;
            
            if (principal <= 0 && monthlyDeposit <= 0) {
                showNotification('Please enter at least an initial amount or monthly contribution.', 'error');
                return;
            }
            
            if (annualRate <= 0) {
                showNotification('Please enter a positive interest rate.', 'error');
                return;
            }
            
            // Calculate compound interest with regular contributions
            const ratePerPeriod = annualRate / 100 / compoundsPerYear;
            const totalPeriods = years * compoundsPerYear;
            
            // Future value of initial investment
            const futureValuePrincipal = principal * Math.pow(1 + ratePerPeriod, totalPeriods);
            
            // Future value of monthly contributions
            // Convert monthly contributions to match compounding frequency
            const contributionsPerPeriod = monthlyDeposit * (12 / compoundsPerYear);
            let futureValueContributions = 0;
            
            if (contributionsPerPeriod > 0) {
                futureValueContributions = contributionsPerPeriod * 
                    ((Math.pow(1 + ratePerPeriod, totalPeriods) - 1) / ratePerPeriod);
            }
            
            const finalBalance = futureValuePrincipal + futureValueContributions;
            const totalContributions = principal + (monthlyDeposit * 12 * years);
            const totalInterest = finalBalance - totalContributions;
            
            // Update UI with results
            resultInitial.textContent = `${getCurrencySymbol()}${principal.toFixed(2)}`;
            resultContributions.textContent = `${getCurrencySymbol()}${(monthlyDeposit * 12 * years).toFixed(2)}`;
            resultInterest.textContent = `${getCurrencySymbol()}${totalInterest.toFixed(2)}`;
            resultFinal.textContent = `${getCurrencySymbol()}${finalBalance.toFixed(2)}`;
            
            calculatorResults.classList.add('show');
            
            showNotification('Interest calculation completed!', 'success');
        }

        // Switch between tabs
        function switchTab(tabId) {
            // Hide all tab contents
            tabContents.forEach(content => {
                content.classList.remove('active');
            });
            
            // Show selected tab content
            document.getElementById(tabId).classList.add('active');
            
            // Update active tab
            tabs.forEach(tab => {
                tab.classList.remove('active');
                if (tab.getAttribute('data-tab') === tabId) {
                    tab.classList.add('active');
                }
            });
            
            // Update specific tabs when activated
            if (tabId === 'analytics') {
                updateAnalyticsTab();
            } else if (tabId === 'history') {
                updateHistoryTab();
            } else if (tabId === 'debtors') {
                updateDebtorsTab();
            } else if (tabId === 'creditors') {
                updateCreditorsTab();
            }
        }

        // Update Dashboard
        function updateDashboard() {
            // Calculate total savings
            const totalSavings = appData.savings.reduce((sum, saving) => sum + saving.amount, 0);
            totalSavingsEl.textContent = totalSavings.toFixed(2);
            
            // Update monthly goal
            monthlyGoalEl.textContent = appData.monthlyTarget.toFixed(2);
            
            // Calculate goal progress
            const currentMonthSavings = getCurrentMonthSavings();
            const progress = (currentMonthSavings / appData.monthlyTarget) * 100;
            goalProgressEl.textContent = `${Math.min(progress, 100).toFixed(1)}%`;
            
            // Update recent transactions
            updateRecentTransactions();
            
            // Update savings chart
            updateSavingsChart();
        }

        // Get savings for current month
        function getCurrentMonthSavings() {
            const now = new Date();
            const currentMonth = now.getMonth();
            const currentYear = now.getFullYear();
            
            return appData.savings
                .filter(saving => {
                    const savingDate = new Date(saving.date);
                    return savingDate.getMonth() === currentMonth && 
                           savingDate.getFullYear() === currentYear;
                })
                .reduce((sum, saving) => sum + saving.amount, 0);
        }

        // Update recent transactions
        function updateRecentTransactions() {
            // Clear current list
            recentTransactionsList.innerHTML = '';
            
            // Get recent savings (last 5)
            const recentSavings = [...appData.savings]
                .sort((a, b) => new Date(b.date) - new Date(a.date))
                .slice(0, 5);
            
            if (recentSavings.length === 0) {
                recentTransactionsList.innerHTML = `
                    <div class="empty-state">
                        <i class="fas fa-exchange-alt"></i>
                        <p>No recent transactions</p>
                    </div>
                `;
                return;
            }
            
            recentSavings.forEach(saving => {
                const transactionItem = document.createElement('div');
                transactionItem.className = 'entry-item';
                
                transactionItem.innerHTML = `
                    <div class="transaction-info">
                        <div class="transaction-date">${formatDate(new Date(saving.date))}</div>
                        <div class="transaction-category">${saving.category}</div>
                    </div>
                    <div class="transaction-amount">${getCurrencySymbol()}${saving.amount.toFixed(2)}</div>
                `;
                
                recentTransactionsList.appendChild(transactionItem);
            });
        }

        // Update savings chart
        function updateSavingsChart() {
            const ctx = document.getElementById('savings-chart').getContext('2d');
            
            // Generate sample data for the chart
            const months = ['Jan', 'Feb', 'Mar', 'Apr', 'May', 'Jun'];
            const savingsData = months.map(() => Math.floor(Math.random() * 2000) + 500);
            
            if (window.savingsChartInstance) {
                window.savingsChartInstance.destroy();
            }
            
            window.savingsChartInstance = new Chart(ctx, {
                type: 'line',
                data: {
                    labels: months,
                    datasets: [{
                        label: 'Savings',
                        data: savingsData,
                        borderColor: '#00e5ff',
                        backgroundColor: 'rgba(0, 229, 255, 0.1)',
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
                            grid: {
                                color: 'rgba(255, 255, 255, 0.1)'
                            },
                            ticks: {
                                color: '#b0b0b0'
                            }
                        },
                        x: {
                            grid: {
                                color: 'rgba(255, 255, 255, 0.1)'
                            },
                            ticks: {
                                color: '#b0b0b0'
                            }
                        }
                    }
                }
            });
        }

        // Update Savings Tab
        function updateSavingsTab() {
            // Calculate total savings
            const totalSavings = appData.savings.reduce((sum, saving) => sum + saving.amount, 0);
            totalSavingsOverview.textContent = `${getCurrencySymbol()}${totalSavings.toFixed(2)}`;
            
            // Update monthly goal
            monthlySavingsGoal.textContent = `${getCurrencySymbol()}${appData.monthlyTarget.toFixed(2)}`;
            
            // Calculate savings rate (simplified)
            const savingsRateValue = (totalSavings / (appData.monthlyTarget * 12)) * 100;
            savingsRate.textContent = `${savingsRateValue.toFixed(1)}%`;
            
            // Calculate emergency fund (simplified)
            const emergencyFundValue = appData.savings
                .filter(saving => saving.category === 'emergency')
                .reduce((sum, saving) => sum + saving.amount, 0);
            emergencyFund.textContent = `${getCurrencySymbol()}${emergencyFundValue.toFixed(2)}`;
            
            // Update recent savings
            updateRecentSavings();
            
            // Update savings chart
            updateSavingsTrendChart();
            
            // Update savings categories
            updateSavingsCategories();
            
            // Update calendar category dropdown
            updateCalendarCategoryDropdown();
        }

        // Add new savings (for Savings tab)
        function addSavingsNew() {
            const amount = parseFloat(savingsAmountNew.value);
            const category = savingsCategoryNew.value;
            const date = savingsDateNew.value;
            const notes = savingsNotesNew.value;
            
            if (isNaN(amount) || amount <= 0 || !date) {
                showNotification('Please enter a valid amount and date.', 'error');
                return;
            }
            
            const newSaving = {
                id: Date.now().toString(),
                amount: amount,
                category: category,
                date: date,
                notes: notes
            };
            
            appData.savings.push(newSaving);
            
            // Update category current amount
            if (appData.savingsCategories[category]) {
                appData.savingsCategories[category].current += amount;
            }
            
            // Add to activity history
            addActivityHistory('saving', `Added ${getCurrencySymbol()}${amount.toFixed(2)} to ${category} savings`);
            
            saveData();
            
            // Update UI
            updateSavingsTab();
            updateDashboard();
            updateAnalyticsTab();
            updateHistoryTab();
            
            // Reset form
            savingsAmountNew.value = '';
            savingsNotesNew.value = '';
            
            showNotification('Savings added successfully!', 'success');
        }

        // Update recent savings list
        function updateRecentSavings() {
            // Clear current list
            recentSavingsList.innerHTML = '';
            
            // Get recent savings (last 5)
            const recentSavings = [...appData.savings]
                .sort((a, b) => new Date(b.date) - new Date(a.date))
                .slice(0, 5);
            
            if (recentSavings.length === 0) {
                recentSavingsList.innerHTML = `
                    <div class="empty-state">
                        <i class="fas fa-piggy-bank"></i>
                        <p>No recent savings</p>
                    </div>
                `;
                return;
            }
            
            recentSavings.forEach(saving => {
                const savingsItem = document.createElement('div');
                savingsItem.className = 'entry-item';
                
                savingsItem.innerHTML = `
                    <div class="savings-info">
                        <div class="savings-date">${formatDate(new Date(saving.date))}</div>
                        <div class="savings-category">${saving.category}</div>
                    </div>
                    <div class="savings-amount">${getCurrencySymbol()}${saving.amount.toFixed(2)}</div>
                `;
                
                recentSavingsList.appendChild(savingsItem);
            });
        }

        // Update savings trend chart
        function updateSavingsTrendChart() {
            const ctx = document.getElementById('savings-trend-chart').getContext('2d');
            
            // Generate sample data for the chart
            const months = ['Jan', 'Feb', 'Mar', 'Apr', 'May', 'Jun', 'Jul', 'Aug', 'Sep', 'Oct', 'Nov', 'Dec'];
            const savingsData = months.map(() => Math.floor(Math.random() * 2000) + 500);
            
            if (window.savingsTrendChartInstance) {
                window.savingsTrendChartInstance.destroy();
            }
            
            window.savingsTrendChartInstance = new Chart(ctx, {
                type: 'line',
                data: {
                    labels: months,
                    datasets: [{
                        label: 'Savings',
                        data: savingsData,
                        borderColor: '#00e5ff',
                        backgroundColor: 'rgba(0, 229, 255, 0.1)',
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
                            grid: {
                                color: 'rgba(255, 255, 255, 0.1)'
                            },
                            ticks: {
                                color: '#b0b0b0'
                            }
                        },
                        x: {
                            grid: {
                                color: 'rgba(255, 255, 255, 0.1)'
                            },
                            ticks: {
                                color: '#b0b0b0'
                            }
                        }
                    }
                }
            });
        }

        // Update savings categories
        function updateSavingsCategories() {
            // Clear current list
            savingsCategoriesList.innerHTML = '';
            
            // Get all categories
            const categories = Object.values(appData.savingsCategories);
            
            if (categories.length === 0) {
                savingsCategoriesList.innerHTML = `
                    <div class="empty-state">
                        <i class="fas fa-folder"></i>
                        <p>No savings categories</p>
                    </div>
                `;
                return;
            }
            
            categories.forEach(category => {
                const progressPercentage = (category.current / category.target) * 100;
                
                const categoryItem = document.createElement('div');
                categoryItem.className = 'savings-category';
                categoryItem.style.borderColor = category.color;
                
                categoryItem.innerHTML = `
                    <div class="category-actions">
                        <button class="btn-icon edit-category-btn" data-id="${category.id}">
                            <i class="fas fa-edit"></i>
                        </button>
                        <button class="btn-icon delete-category-btn" data-id="${category.id}">
                            <i class="fas fa-trash"></i>
                        </button>
                    </div>
                    <h3>${category.name}</h3>
                    <p class="amount">${getCurrencySymbol()}${category.current.toFixed(2)}</p>
                    <div class="progress">
                        <div class="progress-bar" style="width: ${progressPercentage}%; background: ${category.color}"></div>
                    </div>
                    <p class="progress-text">${progressPercentage.toFixed(0)}% of target (${getCurrencySymbol()}${category.target.toFixed(2)})</p>
                `;
                
                savingsCategoriesList.appendChild(categoryItem);
            });
            
            // Add event listeners for edit and delete buttons
            document.querySelectorAll('.edit-category-btn').forEach(btn => {
                btn.addEventListener('click', function() {
                    const id = this.getAttribute('data-id');
                    editCategory(id);
                });
            });
            
            document.querySelectorAll('.delete-category-btn').forEach(btn => {
                btn.addEventListener('click', function() {
                    const id = this.getAttribute('data-id');
                    deleteCategory(id);
                });
            });
        }

        // Save category
        function saveCategory() {
            const name = categoryName.value;
            const target = parseFloat(categoryTarget.value);
            const color = categoryColor.value;
            
            if (!name || isNaN(target) || target <= 0) {
                showNotification('Please enter a valid name and target amount.', 'error');
                return;
            }
            
            // Create new category
            const id = name.toLowerCase().replace(/\s+/g, '-');
            appData.savingsCategories[id] = {
                id: id,
                name: name,
                target: target,
                current: 0,
                color: color
            };
            
            // Update the Financial Calendar category dropdown
            updateCalendarCategoryDropdown();
            
            showNotification('Category added successfully!', 'success');
            
            saveData();
            updateSavingsTab();
            
            // Reset form
            categoryName.value = '';
            categoryTarget.value = '';
            categoryColor.value = '#6e44ff';
        }

        // Update the Financial Calendar category dropdown
        function updateCalendarCategoryDropdown() {
            // Clear existing options except the default ones
            const calendarCategorySelect = document.getElementById('savings-category');
            
            // Keep the default options
            const defaultOptions = Array.from(calendarCategorySelect.options).filter(option => 
                ['general', 'emergency', 'investment', 'vacation', 'education', 'retirement'].includes(option.value)
            );
            
            // Clear the dropdown
            calendarCategorySelect.innerHTML = '';
            
            // Add back the default options
            defaultOptions.forEach(option => {
                calendarCategorySelect.appendChild(option);
            });
            
            // Add the custom categories
            Object.values(appData.savingsCategories).forEach(category => {
                // Skip if it's already in the default options
                if (!defaultOptions.some(option => option.value === category.id)) {
                    const option = document.createElement('option');
                    option.value = category.id;
                    option.textContent = category.name;
                    calendarCategorySelect.appendChild(option);
                }
            });
        }

        // Edit category
        function editCategory(id) {
            const category = appData.savingsCategories[id];
            if (!category) return;
            
            // Populate form with category data
            categoryName.value = category.name;
            categoryTarget.value = category.target;
            categoryColor.value = category.color;
            
            showNotification('Category loaded for editing.', 'info');
        }

        // Delete category
        function deleteCategory(id) {
            if (confirm('Are you sure you want to delete this category? This action cannot be undone.')) {
                delete appData.savingsCategories[id];
                saveData();
                updateSavingsTab();
                updateCalendarCategoryDropdown();
                
                showNotification('Category deleted successfully!', 'success');
            }
        }

        // Update Investments Tab
        function updateInvestmentsTab() {
            // Calculate total portfolio value
            const totalPortfolioValue = appData.investments.reduce((sum, investment) => sum + investment.amount, 0);
            totalPortfolio.textContent = `${getCurrencySymbol()}${totalPortfolioValue.toFixed(2)}`;
            
            // Calculate total return
            const totalReturnValue = appData.investments.reduce((sum, investment) => {
                const returnAmount = (investment.amount * investment.expectedReturn) / 100;
                return sum + returnAmount;
            }, 0);
            totalReturn.textContent = `${getCurrencySymbol()}${totalReturnValue.toFixed(2)}`;
            
            // Calculate return rate
            const returnRateValue = totalPortfolioValue > 0 ? (totalReturnValue / totalPortfolioValue) * 100 : 0;
            returnRate.textContent = `${returnRateValue.toFixed(2)}%`;
            
            // Find best performer
            if (appData.investments.length > 0) {
                const bestInvestment = appData.investments.reduce((best, current) => {
                    return current.expectedReturn > best.expectedReturn ? current : best;
                });
                bestPerformer.textContent = bestInvestment.name;
            } else {
                bestPerformer.textContent = '-';
            }
            
            // Update investments list
            updateInvestmentsList();
            
            // Update investment performance chart
            updateInvestmentPerformanceChart();
        }

        // Add new investment
        function addInvestment() {
            const name = investmentName.value;
            const type = investmentType.value;
            const amount = parseFloat(investmentAmount.value);
            const date = investmentDate.value;
            const expectedReturn = parseFloat(investmentReturn.value);
            const risk = investmentRisk.value;
            const notes = investmentNotes.value;
            
            if (!name || isNaN(amount) || amount <= 0 || !date || isNaN(expectedReturn)) {
                showNotification('Please fill in all required fields with valid values.', 'error');
                return;
            }
            
            const newInvestment = {
                id: Date.now().toString(),
                name: name,
                type: type,
                amount: amount,
                date: date,
                expectedReturn: expectedReturn,
                risk: risk,
                notes: notes
            };
            
            appData.investments.push(newInvestment);
            
            // Add to activity history
            addActivityHistory('investment', `Added ${getCurrencySymbol()}${amount.toFixed(2)} investment in ${name}`);
            
            saveData();
            
            // Update UI
            updateInvestmentsTab();
            updateAnalyticsTab();
            updateHistoryTab();
            
            // Reset form
            investmentName.value = '';
            investmentAmount.value = '';
            investmentReturn.value = '';
            investmentNotes.value = '';
            
            showNotification('Investment added successfully!', 'success');
        }

        // Update investments list
        function updateInvestmentsList() {
            // Clear current list
            investmentsList.innerHTML = '';
            
            if (appData.investments.length === 0) {
                investmentsList.innerHTML = `
                    <div class="empty-state">
                        <i class="fas fa-chart-line"></i>
                        <p>No investments yet</p>
                    </div>
                `;
                return;
            }
            
            appData.investments.forEach(investment => {
                const investmentItem = document.createElement('div');
                investmentItem.className = 'investment-item';
                
                const expectedReturnAmount = (investment.amount * investment.expectedReturn) / 100;
                
                investmentItem.innerHTML = `
                    <div class="investment-details">
                        <div class="investment-name">${investment.name}</div>
                        <div class="investment-type">${investment.type} • ${investment.risk} risk</div>
                        <div class="investment-date">Invested on ${formatDate(new Date(investment.date))}</div>
                    </div>
                    <div class="investment-amounts">
                        <div class="investment-amount">${getCurrencySymbol()}${investment.amount.toFixed(2)}</div>
                        <div class="investment-return">+${getCurrencySymbol()}${expectedReturnAmount.toFixed(2)} (${investment.expectedReturn}%)</div>
                    </div>
                    <div class="investment-actions">
                        <button class="btn-icon edit-btn" data-id="${investment.id}">
                            <i class="fas fa-edit"></i>
                        </button>
                        <button class="btn-icon delete-btn" data-id="${investment.id}">
                            <i class="fas fa-trash"></i>
                        </button>
                    </div>
                `;
                
                investmentsList.appendChild(investmentItem);
            });
            
            // Add event listeners for edit and delete buttons
            document.querySelectorAll('.investment-item .edit-btn').forEach(btn => {
                btn.addEventListener('click', function() {
                    const id = this.getAttribute('data-id');
                    editInvestment(id);
                });
            });
            
            document.querySelectorAll('.investment-item .delete-btn').forEach(btn => {
                btn.addEventListener('click', function() {
                    const id = this.getAttribute('data-id');
                    deleteInvestment(id);
                });
            });
        }

        // Edit investment
        function editInvestment(id) {
            // Find the investment
            const investment = appData.investments.find(inv => inv.id === id);
            if (!investment) return;
            
            // Populate form with investment data
            investmentName.value = investment.name;
            investmentType.value = investment.type;
            investmentAmount.value = investment.amount;
            investmentDate.value = investment.date;
            investmentReturn.value = investment.expectedReturn;
            investmentRisk.value = investment.risk;
            investmentNotes.value = investment.notes;
            
            // Remove the investment from the list
            deleteInvestment(id, false);
            
            showNotification('Investment loaded for editing.', 'info');
        }

        // Delete investment
        function deleteInvestment(id, showNotification = true) {
            appData.investments = appData.investments.filter(inv => inv.id !== id);
            saveData();
            updateInvestmentsTab();
            
            if (showNotification) {
                showNotification('Investment deleted successfully!', 'success');
            }
        }

        // Update investment performance chart
        function updateInvestmentPerformanceChart() {
            const ctx = document.getElementById('investment-performance-chart').getContext('2d');
            
            // Generate sample data for the chart
            const months = ['Jan', 'Feb', 'Mar', 'Apr', 'May', 'Jun', 'Jul', 'Aug', 'Sep', 'Oct', 'Nov', 'Dec'];
            const portfolioValues = [];
            let currentValue = 10000; // Starting value
            
            for (let i = 0; i < months.length; i++) {
                // Simulate market fluctuations
                const change = (Math.random() - 0.5) * 0.1; // -5% to +5%
                currentValue = currentValue * (1 + change);
                portfolioValues.push(currentValue);
            }
            
            if (window.investmentPerformanceChartInstance) {
                window.investmentPerformanceChartInstance.destroy();
            }
            
            window.investmentPerformanceChartInstance = new Chart(ctx, {
                type: 'line',
                data: {
                    labels: months,
                    datasets: [{
                        label: 'Portfolio Value',
                        data: portfolioValues,
                        borderColor: '#00e5ff',
                        backgroundColor: 'rgba(0, 229, 255, 0.1)',
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
                            beginAtZero: false,
                            grid: {
                                color: 'rgba(255, 255, 255, 0.1)'
                            },
                            ticks: {
                                color: '#b0b0b0',
                                callback: function(value) {
                                    return getCurrencySymbol() + value.toFixed(0);
                                }
                            }
                        },
                        x: {
                            grid: {
                                color: 'rgba(255, 255, 255, 0.1)'
                            },
                            ticks: {
                                color: '#b0b0b0'
                            }
                        }
                    }
                }
            });
        }

        // Update Goals Tab
        function updateGoalsTab() {
            // Update active goals
            updateActiveGoals();
            
            // Update achievements
            updateAchievements();
        }

        // Add new goal
        function addGoal() {
            const name = goalName.value;
            const target = parseFloat(goalTarget.value);
            const deadline = goalDeadline.value;
            const category = goalCategory.value;
            const notes = goalNotes.value;
            
            if (!name || isNaN(target) || target <= 0 || !deadline) {
                showNotification('Please fill in all required fields with valid values.', 'error');
                return;
            }
            
            const newGoal = {
                id: Date.now().toString(),
                name: name,
                target: target,
                current: 0,
                deadline: deadline,
                category: category,
                notes: notes,
                completed: false
            };
            
            appData.goals.push(newGoal);
            
            // Add to activity history
            addActivityHistory('goal', `Created new goal: ${name} (${getCurrencySymbol()}${target.toFixed(2)})`);
            
            saveData();
            
            // Update UI
            updateGoalsTab();
            updateAnalyticsTab();
            updateHistoryTab();
            
            // Reset form
            goalName.value = '';
            goalTarget.value = '';
            goalDeadline.value = '';
            goalNotes.value = '';
            
            showNotification('Goal added successfully!', 'success');
        }

        // Update active goals list
        function updateActiveGoals() {
            // Clear current list
            activeGoalsList.innerHTML = '';
            
            // Get active goals (not completed)
            const activeGoals = appData.goals.filter(goal => !goal.completed);
            
            if (activeGoals.length === 0) {
                activeGoalsList.innerHTML = `
                    <div class="empty-state">
                        <i class="fas fa-bullseye"></i>
                        <p>No active goals</p>
                    </div>
                `;
                return;
            }
            
            activeGoals.forEach(goal => {
                const goalItem = document.createElement('div');
                goalItem.className = 'goal-item';
                
                const progressPercentage = (goal.current / goal.target) * 100;
                const daysRemaining = calculateDaysRemaining(goal.deadline);
                
                let daysClass = 'days-high';
                if (daysRemaining < 30) {
                    daysClass = 'days-low';
                } else if (daysRemaining < 90) {
                    daysClass = 'days-medium';
                }
                
                goalItem.innerHTML = `
                    <div class="goal-details">
                        <div class="goal-name">${goal.name}</div>
                        <div class="goal-target">${getCurrencySymbol()}${goal.current.toFixed(2)} / ${getCurrencySymbol()}${goal.target.toFixed(2)}</div>
                        <div class="goal-progress">
                            <div class="goal-progress-bar" style="width: ${progressPercentage}%"></div>
                        </div>
                        <div class="days-remaining ${daysClass}">${daysRemaining} days remaining</div>
                    </div>
                    <div class="goal-actions">
                        <button class="btn-icon add-funds-btn" data-id="${goal.id}">
                            <i class="fas fa-plus"></i>
                        </button>
                        <button class="btn-icon edit-btn" data-id="${goal.id}">
                            <i class="fas fa-edit"></i>
                        </button>
                        <button class="btn-icon delete-btn" data-id="${goal.id}">
                            <i class="fas fa-trash"></i>
                        </button>
                    </div>
                `;
                
                activeGoalsList.appendChild(goalItem);
            });
            
            // Add event listeners for buttons
            document.querySelectorAll('.goal-item .add-funds-btn').forEach(btn => {
                btn.addEventListener('click', function() {
                    const id = this.getAttribute('data-id');
                    addFundsToGoal(id);
                });
            });
            
            document.querySelectorAll('.goal-item .edit-btn').forEach(btn => {
                btn.addEventListener('click', function() {
                    const id = this.getAttribute('data-id');
                    editGoal(id);
                });
            });
            
            document.querySelectorAll('.goal-item .delete-btn').forEach(btn => {
                btn.addEventListener('click', function() {
                    const id = this.getAttribute('data-id');
                    deleteGoal(id);
                });
            });
        }

        // Add funds to a goal
        function addFundsToGoal(id) {
            const goal = appData.goals.find(g => g.id === id);
            if (!goal) return;
            
            const amount = parseFloat(prompt(`How much would you like to add to "${goal.name}"?`, "0"));
            
            if (isNaN(amount) || amount <= 0) {
                showNotification('Please enter a valid amount.', 'error');
                return;
            }
            
            goal.current += amount;
            
            // Check if goal is completed
            if (goal.current >= goal.target) {
                goal.completed = true;
                showNotification(`Congratulations! You've completed your goal: ${goal.name}`, 'success');
                
                // Add to activity history
                addActivityHistory('goal', `Completed goal: ${goal.name}`);
            } else {
                // Add to activity history
                addActivityHistory('goal', `Added ${getCurrencySymbol()}${amount.toFixed(2)} to goal: ${goal.name}`);
            }
            
            saveData();
            updateGoalsTab();
            updateAnalyticsTab();
            updateHistoryTab();
            
            showNotification(`Added ${getCurrencySymbol()}${amount.toFixed(2)} to your goal.`, 'success');
        }

        // Edit goal
        function editGoal(id) {
            // Find the goal
            const goal = appData.goals.find(g => g.id === id);
            if (!goal) return;
            
            // Populate form with goal data
            goalName.value = goal.name;
            goalTarget.value = goal.target;
            goalDeadline.value = goal.deadline;
            goalCategory.value = goal.category;
            goalNotes.value = goal.notes;
            
            // Remove the goal from the list
            deleteGoal(id, false);
            
            showNotification('Goal loaded for editing.', 'info');
        }

        // Delete goal
        function deleteGoal(id, showNotification = true) {
            appData.goals = appData.goals.filter(g => g.id !== id);
            saveData();
            updateGoalsTab();
            
            if (showNotification) {
                showNotification('Goal deleted successfully!', 'success');
            }
        }

        // Update achievements
        function updateAchievements() {
            // Clear current grid
            achievementsGrid.innerHTML = '';
            
            // Get all achievements
            const achievements = Object.values(appData.achievements);
            
            // Create achievement cards
            achievements.forEach(achievement => {
                const progressPercentage = (achievement.current / achievement.target) * 100;
                const isUnlocked = achievement.unlocked || achievement.current >= achievement.target;
                
                if (achievement.current >= achievement.target && !achievement.unlocked) {
                    achievement.unlocked = true;
                    // Add to activity history
                    addActivityHistory('achievement', `Unlocked achievement: ${achievement.name}`);
                }
                
                const achievementCard = document.createElement('div');
                achievementCard.className = `achievement-card ${isUnlocked ? 'unlocked' : 'locked'}`;
                
                achievementCard.innerHTML = `
                    <div class="achievement-actions">
                        <button class="btn-icon edit-achievement-btn" data-id="${achievement.id}">
                            <i class="fas fa-edit"></i>
                        </button>
                        <button class="btn-icon delete-achievement-btn" data-id="${achievement.id}">
                            <i class="fas fa-trash"></i>
                        </button>
                    </div>
                    <div class="achievement-icon">
                        <i class="${achievement.icon}"></i>
                    </div>
                    <div class="achievement-title">${achievement.name}</div>
                    <div class="achievement-desc">${achievement.description}</div>
                    ${!isUnlocked ? `<div class="achievement-progress">${progressPercentage.toFixed(0)}% complete</div>` : ''}
                `;
                
                achievementsGrid.appendChild(achievementCard);
            });
            
            // Add event listeners for edit and delete buttons
            document.querySelectorAll('.edit-achievement-btn').forEach(btn => {
                btn.addEventListener('click', function() {
                    const id = this.getAttribute('data-id');
                    editAchievement(id);
                });
            });
            
            document.querySelectorAll('.delete-achievement-btn').forEach(btn => {
                btn.addEventListener('click', function() {
                    const id = this.getAttribute('data-id');
                    deleteAchievement(id);
                });
            });
        }

        // Save achievement
        function saveAchievement() {
            const name = achievementName.value;
            const description = achievementDescription.value;
            const icon = achievementIcon.value;
            const target = parseFloat(achievementTarget.value);
            const current = parseFloat(achievementCurrent.value);
            
            if (!name || !description || !icon || isNaN(target) || isNaN(current)) {
                showNotification('Please fill in all fields with valid values.', 'error');
                return;
            }
            
            // Create new achievement
            const id = name.toLowerCase().replace(/\s+/g, '');
            appData.achievements[id] = {
                id: id,
                name: name,
                description: description,
                icon: icon,
                target: target,
                current: current,
                unlocked: current >= target
            };
            
            showNotification('Achievement added successfully!', 'success');
            
            saveData();
            updateGoalsTab();
            updateHistoryTab();
            
            // Reset form
            achievementName.value = '';
            achievementDescription.value = '';
            achievementIcon.value = 'fas fa-trophy';
            achievementTarget.value = '';
            achievementCurrent.value = '';
        }

        // Edit achievement
        function editAchievement(id) {
            const achievement = appData.achievements[id];
            if (!achievement) return;
            
            // Populate form with achievement data
            achievementName.value = achievement.name;
            achievementDescription.value = achievement.description;
            achievementIcon.value = achievement.icon;
            achievementTarget.value = achievement.target;
            achievementCurrent.value = achievement.current;
            
            showNotification('Achievement loaded for editing.', 'info');
        }

        // Delete achievement
        function deleteAchievement(id) {
            if (confirm('Are you sure you want to delete this achievement? This action cannot be undone.')) {
                delete appData.achievements[id];
                saveData();
                updateGoalsTab();
                
                showNotification('Achievement deleted successfully!', 'success');
            }
        }

        // Update Subscriptions Tab
        function updateSubscriptionsTab() {
            // Calculate monthly cost
            const monthlyCost = appData.subscriptions
                .filter(sub => sub.status === 'active')
                .reduce((sum, sub) => sum + sub.cost, 0);
            monthlySubscriptionCost.textContent = `${getCurrencySymbol()}${monthlyCost.toFixed(2)}`;
            
            // Calculate yearly cost
            const yearlyCost = monthlyCost * 12;
            yearlySubscriptionCost.textContent = `${getCurrencySymbol()}${yearlyCost.toFixed(2)}`;
            
            // Count active subscriptions
            const activeSubsCount = appData.subscriptions.filter(sub => sub.status === 'active').length;
            activeSubscriptions.textContent = activeSubsCount;
            
            // Find next renewal
            const activeSubs = appData.subscriptions.filter(sub => sub.status === 'active');
            if (activeSubs.length > 0) {
                const nextRenewalDate = activeSubs.reduce((earliest, current) => {
                    return new Date(current.renewalDate) < new Date(earliest.renewalDate) ? current : earliest;
                });
                nextRenewal.textContent = formatDate(new Date(nextRenewalDate.renewalDate));
            } else {
                nextRenewal.textContent = '-';
            }
            
            // Update subscriptions list
            updateSubscriptionsList();
            
            // Update subscription category chart
            updateSubscriptionCategoryChart();
        }

        // Add new subscription
        function addSubscription() {
            const name = subscriptionName.value;
            const cost = parseFloat(subscriptionCost.value);
            const category = subscriptionCategory.value;
            const renewalDate = subscriptionRenewal.value;
            const status = subscriptionStatus.value;
            const notes = subscriptionNotes.value;
            
            if (!name || isNaN(cost) || cost <= 0 || !renewalDate) {
                showNotification('Please fill in all required fields with valid values.', 'error');
                return;
            }
            
            const newSubscription = {
                id: Date.now().toString(),
                name: name,
                cost: cost,
                category: category,
                renewalDate: renewalDate,
                status: status,
                notes: notes
            };
            
            appData.subscriptions.push(newSubscription);
            
            // Add to activity history
            addActivityHistory('subscription', `Added ${name} subscription (${getCurrencySymbol()}${cost.toFixed(2)}/month)`);
            
            saveData();
            
            // Update UI
            updateSubscriptionsTab();
            updateAnalyticsTab();
            updateHistoryTab();
            
            // Reset form
            subscriptionName.value = '';
            subscriptionCost.value = '';
            subscriptionRenewal.value = '';
            subscriptionNotes.value = '';
            
            showNotification('Subscription added successfully!', 'success');
        }

        // Update subscriptions list
        function updateSubscriptionsList() {
            // Clear current list
            subscriptionsList.innerHTML = '';
            
            if (appData.subscriptions.length === 0) {
                subscriptionsList.innerHTML = `
                    <div class="empty-state">
                        <i class="fas fa-receipt"></i>
                        <p>No subscriptions yet</p>
                    </div>
                `;
                return;
            }
            
            appData.subscriptions.forEach(subscription => {
                const subscriptionItem = document.createElement('div');
                subscriptionItem.className = 'subscription-item';
                
                const daysRemaining = calculateDaysRemaining(subscription.renewalDate);
                
                let statusClass = '';
                if (subscription.status === 'active') {
                    statusClass = 'status-active';
                } else if (subscription.status === 'cancelled') {
                    statusClass = 'status-cancelled';
                } else {
                    statusClass = 'status-inactive';
                }
                
                subscriptionItem.innerHTML = `
                    <div class="subscription-details">
                        <div class="subscription-name">${subscription.name}</div>
                        <div class="subscription-category">${subscription.category} • <span class="${statusClass}">${subscription.status}</span></div>
                        <div class="subscription-renewal">Renews on ${formatDate(new Date(subscription.renewalDate))}</div>
                    </div>
                    <div class="subscription-cost">
                        <div class="subscription-amount">${getCurrencySymbol()}${subscription.cost.toFixed(2)}/month</div>
                        <div class="days-remaining ${daysRemaining < 7 ? 'days-low' : daysRemaining < 30 ? 'days-medium' : 'days-high'}">${daysRemaining} days</div>
                    </div>
                    <div class="subscription-actions">
                        <button class="renew-btn" data-id="${subscription.id}">
                            <i class="fas fa-sync-alt"></i> Renew
                        </button>
                        <button class="cancel-btn" data-id="${subscription.id}">
                            <i class="fas fa-times"></i> Cancel
                        </button>
                    </div>
                `;
                
                subscriptionsList.appendChild(subscriptionItem);
            });
            
            // Add event listeners for buttons
            document.querySelectorAll('.subscription-item .renew-btn').forEach(btn => {
                btn.addEventListener('click', function() {
                    const id = this.getAttribute('data-id');
                    renewSubscription(id);
                });
            });
            
            document.querySelectorAll('.subscription-item .cancel-btn').forEach(btn => {
                btn.addEventListener('click', function() {
                    const id = this.getAttribute('data-id');
                    cancelSubscription(id);
                });
            });
        }

        // Renew subscription
        function renewSubscription(id) {
            const subscription = appData.subscriptions.find(sub => sub.id === id);
            if (!subscription) return;
            
            // Extend renewal date by 1 month
            const currentDate = new Date(subscription.renewalDate);
            currentDate.setMonth(currentDate.getMonth() + 1);
            subscription.renewalDate = currentDate.toISOString().split('T')[0];
            
            // Add to activity history
            addActivityHistory('subscription', `Renewed ${subscription.name} subscription`);
            
            saveData();
            updateSubscriptionsTab();
            updateHistoryTab();
            
            showNotification('Subscription renewed for 1 month.', 'success');
        }

        // Cancel subscription
        function cancelSubscription(id) {
            const subscription = appData.subscriptions.find(sub => sub.id === id);
            if (!subscription) return;
            
            subscription.status = 'cancelled';
            
            // Add to activity history
            addActivityHistory('subscription', `Cancelled ${subscription.name} subscription`);
            
            saveData();
            updateSubscriptionsTab();
            updateHistoryTab();
            
            showNotification('Subscription cancelled.', 'success');
        }

        // Update subscription category chart
        function updateSubscriptionCategoryChart() {
            const ctx = document.getElementById('subscription-category-chart').getContext('2d');
            
            // Calculate costs by category
            const categories = ['entertainment', 'productivity', 'utilities', 'education', 'health', 'other'];
            const categoryCosts = categories.map(category => {
                return appData.subscriptions
                    .filter(sub => sub.category === category && sub.status === 'active')
                    .reduce((sum, sub) => sum + sub.cost, 0);
            });
            
            if (window.subscriptionCategoryChartInstance) {
                window.subscriptionCategoryChartInstance.destroy();
            }
            
            window.subscriptionCategoryChartInstance = new Chart(ctx, {
                type: 'doughnut',
                data: {
                    labels: ['Entertainment', 'Productivity', 'Utilities', 'Education', 'Health', 'Other'],
                    datasets: [{
                        data: categoryCosts,
                        backgroundColor: [
                            '#00e5ff',
                            '#00ff9d',
                            '#ffc400',
                            '#ff3860',
                            '#8c52ff',
                            '#ff6b9d'
                        ],
                        borderWidth: 0
                    }]
                },
                options: {
                    responsive: true,
                    maintainAspectRatio: false,
                    plugins: {
                        legend: {
                            position: 'bottom',
                            labels: {
                                color: '#b0b0b0',
                                font: {
                                    size: 12
                                }
                            }
                        }
                    }
                }
            });
        }

        // Debtors tab functions
        function updateDebtorsTab() {
            // Calculate total debt
            const totalDebtAmount = appData.debtors
                .filter(debtor => debtor.status !== 'paid')
                .reduce((sum, debtor) => sum + debtor.amount, 0);
            totalDebt.textContent = `${getCurrencySymbol()}${totalDebtAmount.toFixed(2)}`;
            
            // Count upcoming payments
            const upcomingPaymentsCount = appData.debtors
                .filter(debtor => debtor.status === 'pending' && !isOverdue(debtor.dueDate))
                .length;
            upcomingPayments.textContent = upcomingPaymentsCount;
            
            // Calculate overdue debt
            const overdueDebtAmount = appData.debtors
                .filter(debtor => debtor.status === 'pending' && isOverdue(debtor.dueDate))
                .reduce((sum, debtor) => sum + debtor.amount, 0);
            overdueDebt.textContent = `${getCurrencySymbol()}${overdueDebtAmount.toFixed(2)}`;
            
            // Find next payment date
            const pendingDebtors = appData.debtors.filter(debtor => debtor.status === 'pending');
            if (pendingDebtors.length > 0) {
                const nextPayment = pendingDebtors.reduce((earliest, current) => {
                    return new Date(current.dueDate) < new Date(earliest.dueDate) ? current : earliest;
                });
                nextPaymentDate.textContent = formatDate(new Date(nextPayment.dueDate));
            } else {
                nextPaymentDate.textContent = '-';
            }
            
            // Update debtors lists
            updateDebtorsList();
        }

        function addDebtor() {
            const name = debtorName.value;
            const amount = parseFloat(debtorAmount.value);
            const dueDate = debtorDueDate.value;
            const category = debtorCategory.value;
            const interest = parseFloat(debtorInterest.value) || 0;
            const installment = debtorInstallment.value;
            const notes = debtorNotes.value;
            
            if (!name || isNaN(amount) || amount <= 0 || !dueDate) {
                showNotification('Please enter a valid name, amount, and due date.', 'error');
                return;
            }
            
            const newDebtor = {
                id: Date.now().toString(),
                name: name,
                amount: amount,
                dueDate: dueDate,
                category: category,
                interest: interest,
                installment: installment,
                notes: notes,
                status: 'pending',
                paidDate: null
            };
            
            appData.debtors.push(newDebtor);
            
            // Add to activity history
            addActivityHistory('debtor', `Added debt to ${name} (${getCurrencySymbol()}${amount.toFixed(2)})`);
            
            saveData();
            
            // Update UI
            updateDebtorsTab();
            updateHistoryTab();
            
            // Reset form
            debtorName.value = '';
            debtorAmount.value = '';
            debtorDueDate.value = '';
            debtorInterest.value = '';
            debtorNotes.value = '';
            
            showNotification('Debtor added successfully!', 'success');
        }

        function updateDebtorsList() {
            // Clear current lists
            upcomingDebtorsList.innerHTML = '';
            debtorHistoryList.innerHTML = '';
            
            // Get current date
            const now = new Date();
            const today = new Date(now.getFullYear(), now.getMonth(), now.getDate());
            
            // Separate debtors into upcoming and history
            const upcomingDebtors = [];
            const debtorHistory = [];
            
            appData.debtors.forEach(debtor => {
                const dueDate = new Date(debtor.dueDate);
                
                if (debtor.status === 'paid') {
                    debtorHistory.push(debtor);
                } else if (dueDate >= today) {
                    upcomingDebtors.push(debtor);
                } else {
                    // Overdue debtors
                    upcomingDebtors.push(debtor);
                }
            });
            
            // Sort upcoming debtors by due date
            upcomingDebtors.sort((a, b) => new Date(a.dueDate) - new Date(b.dueDate));
            
            // Sort debtor history by paid date (most recent first)
            debtorHistory.sort((a, b) => new Date(b.paidDate) - new Date(a.paidDate));
            
            // Display upcoming debtors
            if (upcomingDebtors.length === 0) {
                upcomingDebtorsList.innerHTML = `
                    <div class="empty-state">
                        <i class="fas fa-file-invoice-dollar"></i>
                        <p>No upcoming payments</p>
                    </div>
                `;
            } else {
                upcomingDebtors.forEach(debtor => {
                    const debtorItem = document.createElement('div');
                    debtorItem.className = 'debtor-item';
                    
                    // Calculate days remaining
                    const dueDate = new Date(debtor.dueDate);
                    const timeDiff = dueDate.getTime() - today.getTime();
                    const daysRemaining = Math.ceil(timeDiff / (1000 * 3600 * 24));
                    
                    let statusClass = 'status-pending';
                    let statusText = 'Pending';
                    
                    if (daysRemaining < 0) {
                        statusClass = 'status-overdue';
                        statusText = 'Overdue';
                    }
                    
                    debtorItem.innerHTML = `
                        <div class="debtor-details">
                            <h3>${debtor.name}</h3>
                            <p>${getCurrencySymbol()}${debtor.amount.toFixed(2)} • Due: ${formatDate(dueDate)}</p>
                            <div class="debtor-status ${statusClass}">${statusText}</div>
                            ${daysRemaining < 0 ? `<div class="days-remaining days-low">${Math.abs(daysRemaining)} days overdue</div>` : 
                              `<div class="days-remaining ${daysRemaining <= 7 ? 'days-low' : daysRemaining <= 14 ? 'days-medium' : 'days-high'}">${daysRemaining} days remaining</div>`}
                        </div>
                        <div class="debtor-actions">
                            ${debtor.status !== 'paid' ? `<button class="pay-btn" data-debtor-id="${debtor.id}">Mark Paid</button>` : ''}
                            <button class="btn-icon edit-btn" data-debtor-id="${debtor.id}">
                                <i class="fas fa-edit"></i>
                            </button>
                            <button class="btn-icon delete-btn" data-debtor-id="${debtor.id}">
                                <i class="fas fa-trash"></i>
                            </button>
                        </div>
                    `;
                    
                    upcomingDebtorsList.appendChild(debtorItem);
                });
            }
            
            // Display debtor history
            if (debtorHistory.length === 0) {
                debtorHistoryList.innerHTML = `
                    <div class="empty-state">
                        <i class="fas fa-history"></i>
                        <p>No debt history</p>
                    </div>
                `;
            } else {
                debtorHistory.forEach(debtor => {
                    const debtorItem = document.createElement('div');
                    debtorItem.className = 'debtor-item';
                    
                    debtorItem.innerHTML = `
                        <div class="debtor-details">
                            <h3>${debtor.name}</h3>
                            <p>${getCurrencySymbol()}${debtor.amount.toFixed(2)} • Paid: ${formatDate(new Date(debtor.paidDate))}</p>
                            <div class="debtor-status status-paid">Paid</div>
                        </div>
                        <div class="debtor-actions">
                            <button class="btn-icon edit-btn" data-debtor-id="${debtor.id}">
                                <i class="fas fa-edit"></i>
                            </button>
                            <button class="btn-icon delete-btn" data-debtor-id="${debtor.id}">
                                <i class="fas fa-trash"></i>
                            </button>
                        </div>
                    `;
                    
                    debtorHistoryList.appendChild(debtorItem);
                });
            }
            
            // Add event listeners to debtor actions
            document.querySelectorAll('.pay-btn').forEach(btn => {
                btn.addEventListener('click', (e) => {
                    const debtorId = e.target.getAttribute('data-debtor-id');
                    markDebtorAsPaid(debtorId);
                });
            });
            
            document.querySelectorAll('.debtor-actions .edit-btn').forEach(btn => {
                btn.addEventListener('click', (e) => {
                    const debtorId = e.target.getAttribute('data-debtor-id');
                    // editDebtor(debtorId);
                    showNotification('Edit debtor functionality would be implemented here.', 'info');
                });
            });
            
            document.querySelectorAll('.debtor-actions .delete-btn').forEach(btn => {
                btn.addEventListener('click', (e) => {
                    const debtorId = e.target.getAttribute('data-debtor-id');
                    deleteDebtor(debtorId);
                });
            });
        }

        function markDebtorAsPaid(debtorId) {
            const debtorIndex = appData.debtors.findIndex(d => d.id === debtorId);
            
            if (debtorIndex === -1) {
                showNotification('Debtor not found.', 'error');
                return;
            }
            
            appData.debtors[debtorIndex].status = 'paid';
            appData.debtors[debtorIndex].paidDate = new Date().toISOString().split('T')[0];
            
            // Add to activity history
            addActivityHistory('debtor', `Paid ${appData.debtors[debtorIndex].name} (${getCurrencySymbol()}${appData.debtors[debtorIndex].amount.toFixed(2)})`);
            
            saveData();
            
            updateDebtorsTab();
            updateHistoryTab();
            
            showNotification('Debt marked as paid!', 'success');
        }

        function deleteDebtor(debtorId) {
            const debtorIndex = appData.debtors.findIndex(d => d.id === debtorId);
            
            if (debtorIndex === -1) {
                showNotification('Debtor not found.', 'error');
                return;
            }
            
            appData.debtors.splice(debtorIndex, 1);
            saveData();
            
            updateDebtorsTab();
            
            showNotification('Debtor deleted successfully!', 'success');
        }

        // Creditors tab functions
        function updateCreditorsTab() {
            // Calculate total amount owed
            const totalOwedAmount = appData.creditors
                .filter(creditor => creditor.status !== 'collected')
                .reduce((sum, creditor) => sum + creditor.amount, 0);
            totalOwed.textContent = `${getCurrencySymbol()}${totalOwedAmount.toFixed(2)}`;
            
            // Count upcoming collections
            const upcomingCollectionsCount = appData.creditors
                .filter(creditor => creditor.status === 'outstanding' && !isOverdue(creditor.dueDate))
                .length;
            upcomingCollections.textContent = upcomingCollectionsCount;
            
            // Calculate overdue creditors
            const overdueCreditorsAmount = appData.creditors
                .filter(creditor => creditor.status === 'outstanding' && isOverdue(creditor.dueDate))
                .reduce((sum, creditor) => sum + creditor.amount, 0);
            overdueCreditors.textContent = `${getCurrencySymbol()}${overdueCreditorsAmount.toFixed(2)}`;
            
            // Find next collection date
            const outstandingCreditors = appData.creditors.filter(creditor => creditor.status === 'outstanding');
            if (outstandingCreditors.length > 0) {
                const nextCollection = outstandingCreditors.reduce((earliest, current) => {
                    return new Date(current.dueDate) < new Date(earliest.dueDate) ? current : earliest;
                });
                nextCollectionDate.textContent = formatDate(new Date(nextCollection.dueDate));
            } else {
                nextCollectionDate.textContent = '-';
            }
            
            // Update creditors lists
            updateCreditorsList();
        }

        function addCreditor() {
            const name = creditorName.value;
            const amount = parseFloat(creditorAmount.value);
            const dueDate = creditorDueDate.value;
            const category = creditorCategory.value;
            const interest = parseFloat(creditorInterest.value) || 0;
            const installment = creditorInstallment.value;
            const notes = creditorNotes.value;
            
            if (!name || isNaN(amount) || amount <= 0 || !dueDate) {
                showNotification('Please enter a valid name, amount, and due date.', 'error');
                return;
            }
            
            const newCreditor = {
                id: Date.now().toString(),
                name: name,
                amount: amount,
                dueDate: dueDate,
                category: category,
                interest: interest,
                installment: installment,
                notes: notes,
                status: 'outstanding',
                collectedDate: null
            };
            
            appData.creditors.push(newCreditor);
            
            // Add to activity history
            addActivityHistory('creditor', `Added credit from ${name} (${getCurrencySymbol()}${amount.toFixed(2)})`);
            
            saveData();
            
            // Update UI
            updateCreditorsTab();
            updateHistoryTab();
            
            // Reset form
            creditorName.value = '';
            creditorAmount.value = '';
            creditorDueDate.value = '';
            creditorInterest.value = '';
            creditorNotes.value = '';
            
            showNotification('Creditor added successfully!', 'success');
        }

        function updateCreditorsList() {
            // Clear current lists
            upcomingCreditorsList.innerHTML = '';
            creditorHistoryList.innerHTML = '';
            
            // Get current date
            const now = new Date();
            const today = new Date(now.getFullYear(), now.getMonth(), now.getDate());
            
            // Separate creditors into upcoming and history
            const upcomingCreditors = [];
            const creditorHistory = [];
            
            appData.creditors.forEach(creditor => {
                const dueDate = new Date(creditor.dueDate);
                
                if (creditor.status === 'collected') {
                    creditorHistory.push(creditor);
                } else if (dueDate >= today) {
                    upcomingCreditors.push(creditor);
                } else {
                    // Overdue creditors
                    upcomingCreditors.push(creditor);
                }
            });
            
            // Sort upcoming creditors by due date
            upcomingCreditors.sort((a, b) => new Date(a.dueDate) - new Date(b.dueDate));
            
            // Sort creditor history by collected date (most recent first)
            creditorHistory.sort((a, b) => new Date(b.collectedDate) - new Date(a.collectedDate));
            
            // Display upcoming creditors
            if (upcomingCreditors.length === 0) {
                upcomingCreditorsList.innerHTML = `
                    <div class="empty-state">
                        <i class="fas fa-hand-holding-usd"></i>
                        <p>No upcoming collections</p>
                    </div>
                `;
            } else {
                upcomingCreditors.forEach(creditor => {
                    const creditorItem = document.createElement('div');
                    creditorItem.className = 'creditor-item';
                    
                    // Calculate days remaining
                    const dueDate = new Date(creditor.dueDate);
                    const timeDiff = dueDate.getTime() - today.getTime();
                    const daysRemaining = Math.ceil(timeDiff / (1000 * 3600 * 24));
                    
                    let statusClass = 'status-outstanding';
                    let statusText = 'Outstanding';
                    
                    if (daysRemaining < 0) {
                        statusClass = 'status-overdue';
                        statusText = 'Overdue';
                    }
                    
                    creditorItem.innerHTML = `
                        <div class="creditor-details">
                            <h3>${creditor.name}</h3>
                            <p>${getCurrencySymbol()}${creditor.amount.toFixed(2)} • Due: ${formatDate(dueDate)}</p>
                            <div class="creditor-status ${statusClass}">${statusText}</div>
                            ${daysRemaining < 0 ? `<div class="days-remaining days-low">${Math.abs(daysRemaining)} days overdue</div>` : 
                              `<div class="days-remaining ${daysRemaining <= 7 ? 'days-low' : daysRemaining <= 14 ? 'days-medium' : 'days-high'}">${daysRemaining} days remaining</div>`}
                        </div>
                        <div class="creditor-actions">
                            ${creditor.status !== 'collected' ? `<button class="collect-btn" data-creditor-id="${creditor.id}">Mark Collected</button>` : ''}
                            <button class="btn-icon edit-btn" data-creditor-id="${creditor.id}">
                                <i class="fas fa-edit"></i>
                            </button>
                            <button class="btn-icon delete-btn" data-creditor-id="${creditor.id}">
                                <i class="fas fa-trash"></i>
                            </button>
                        </div>
                    `;
                    
                    upcomingCreditorsList.appendChild(creditorItem);
                });
            }
            
            // Display creditor history
            if (creditorHistory.length === 0) {
                creditorHistoryList.innerHTML = `
                    <div class="empty-state">
                        <i class="fas fa-history"></i>
                        <p>No collection history</p>
                    </div>
                `;
            } else {
                creditorHistory.forEach(creditor => {
                    const creditorItem = document.createElement('div');
                    creditorItem.className = 'creditor-item';
                    
                    creditorItem.innerHTML = `
                        <div class="creditor-details">
                            <h3>${creditor.name}</h3>
                            <p>${getCurrencySymbol()}${creditor.amount.toFixed(2)} • Collected: ${formatDate(new Date(creditor.collectedDate))}</p>
                            <div class="creditor-status status-collected">Collected</div>
                        </div>
                        <div class="creditor-actions">
                            <button class="btn-icon edit-btn" data-creditor-id="${creditor.id}">
                                <i class="fas fa-edit"></i>
                            </button>
                            <button class="btn-icon delete-btn" data-creditor-id="${creditor.id}">
                                <i class="fas fa-trash"></i>
                            </button>
                        </div>
                    `;
                    
                    creditorHistoryList.appendChild(creditorItem);
                });
            }
            
            // Add event listeners to creditor actions
            document.querySelectorAll('.collect-btn').forEach(btn => {
                btn.addEventListener('click', (e) => {
                    const creditorId = e.target.getAttribute('data-creditor-id');
                    markCreditorAsCollected(creditorId);
                });
            });
            
            document.querySelectorAll('.creditor-actions .edit-btn').forEach(btn => {
                btn.addEventListener('click', (e) => {
                    const creditorId = e.target.getAttribute('data-creditor-id');
                    // editCreditor(creditorId);
                    showNotification('Edit creditor functionality would be implemented here.', 'info');
                });
            });
            
            document.querySelectorAll('.creditor-actions .delete-btn').forEach(btn => {
                btn.addEventListener('click', (e) => {
                    const creditorId = e.target.getAttribute('data-creditor-id');
                    deleteCreditor(creditorId);
                });
            });
        }

        function markCreditorAsCollected(creditorId) {
            const creditorIndex = appData.creditors.findIndex(c => c.id === creditorId);
            
            if (creditorIndex === -1) {
                showNotification('Creditor not found.', 'error');
                return;
            }
            
            appData.creditors[creditorIndex].status = 'collected';
            appData.creditors[creditorIndex].collectedDate = new Date().toISOString().split('T')[0];
            
            // Add to activity history
            addActivityHistory('creditor', `Collected from ${appData.creditors[creditorIndex].name} (${getCurrencySymbol()}${appData.creditors[creditorIndex].amount.toFixed(2)})`);
            
            saveData();
            
            updateCreditorsTab();
            updateHistoryTab();
            
            showNotification('Credit marked as collected!', 'success');
        }

        function deleteCreditor(creditorId) {
            const creditorIndex = appData.creditors.findIndex(c => c.id === creditorId);
            
            if (creditorIndex === -1) {
                showNotification('Creditor not found.', 'error');
                return;
            }
            
            appData.creditors.splice(creditorIndex, 1);
            saveData();
            
            updateCreditorsTab();
            
            showNotification('Creditor deleted successfully!', 'success');
        }

        // Calendar functions
        function generateCalendar(month, year) {
            // Clear calendar
            calendar.innerHTML = '';
            
            // Add day headers
            const dayHeaders = ['Sun', 'Mon', 'Tue', 'Wed', 'Thu', 'Fri', 'Sat'];
            dayHeaders.forEach(day => {
                const dayHeader = document.createElement('div');
                dayHeader.className = 'calendar-day-header';
                dayHeader.textContent = day;
                calendar.appendChild(dayHeader);
            });
            
            // Get first day of month
            const firstDay = new Date(year, month, 1).getDay();
            
            // Get number of days in month
            const daysInMonth = new Date(year, month + 1, 0).getDate();
            
            // Add empty cells for days before first day of month
            for (let i = 0; i < firstDay; i++) {
                const emptyDay = document.createElement('div');
                emptyDay.className = 'calendar-day empty';
                calendar.appendChild(emptyDay);
            }
            
            // Add days of month
            for (let day = 1; day <= daysInMonth; day++) {
                const dayElement = document.createElement('div');
                dayElement.className = 'calendar-day';
                
                // Check if this is the current day
                const today = new Date();
                if (day === today.getDate() && month === today.getMonth() && year === today.getFullYear()) {
                    dayElement.classList.add('current-day');
                }
                
                // Day number
                const dayNumber = document.createElement('div');
                dayNumber.className = 'day-number';
                dayNumber.textContent = day;
                dayElement.appendChild(dayNumber);
                
                // Check for savings on this day
                const savingsForDay = getSavingsForDay(day, month, year);
                if (savingsForDay.length > 0) {
                    const total = savingsForDay.reduce((sum, saving) => sum + saving.amount, 0);
                    
                    const savingsAmount = document.createElement('div');
                    savingsAmount.className = 'savings-amount';
                    savingsAmount.textContent = `${getCurrencySymbol()}${total.toFixed(2)}`;
                    dayElement.appendChild(savingsAmount);
                }
                
                calendar.appendChild(dayElement);
            }
            
            // Update month name
            currentMonthName.textContent = getMonthName(month);
        }

        // Get savings for a specific day
        function getSavingsForDay(day, month, year) {
            return appData.savings.filter(saving => {
                const savingDate = new Date(saving.date);
                return savingDate.getDate() === day && 
                       savingDate.getMonth() === month && 
                       savingDate.getFullYear() === year;
            });
        }

        // Add savings (for Calendar tab)
        function addSavings() {
            const date = savingsDate.value;
            const amount = parseFloat(savingsAmount.value);
            const category = savingsCategory.value;
            const notes = savingsNotes.value;
            
            if (!date || isNaN(amount) || amount <= 0) {
                showNotification('Please enter a valid date and amount.', 'error');
                return;
            }
            
            const newSaving = {
                id: Date.now().toString(),
                date: date,
                amount: amount,
                category: category,
                notes: notes
            };
            
            appData.savings.push(newSaving);
            
            // Update category current amount
            if (appData.savingsCategories[category]) {
                appData.savingsCategories[category].current += amount;
            }
            
            // Add to activity history
            addActivityHistory('saving', `Added ${getCurrencySymbol()}${amount.toFixed(2)} to ${category} savings`);
            
            saveData();
            
            // Update UI
            generateCalendar(currentMonth, currentYear);
            updateDashboard();
            updateSavingsTab();
            updateAnalyticsTab();
            updateHistoryTab();
            
            // Reset form
            savingsAmount.value = '';
            savingsNotes.value = '';
            
            showNotification('Savings entry added successfully!', 'success');
        }

        // Bill Tracking functions
        function addBill() {
            const name = billName.value;
            const amount = parseFloat(billAmount.value);
            const dueDate = billDueDate.value;
            const category = billCategory.value;
            const notes = billNotes.value;
            
            if (!name || isNaN(amount) || amount <= 0 || !dueDate) {
                showNotification('Please enter a valid name, amount, and due date.', 'error');
                return;
            }
            
            const newBill = {
                id: Date.now().toString(),
                name: name,
                amount: amount,
                dueDate: dueDate,
                category: category,
                notes: notes,
                status: 'pending',
                paidDate: null
            };
            
            appData.bills.push(newBill);
            
            // Add to activity history
            addActivityHistory('bill', `Added ${name} bill (${getCurrencySymbol()}${amount.toFixed(2)})`);
            
            saveData();
            
            // Update UI
            updateBillsList();
            updateHistoryTab();
            
            // Reset form
            billName.value = '';
            billAmount.value = '';
            billDueDate.value = '';
            billNotes.value = '';
            
            showNotification('Bill added successfully!', 'success');
        }

        // Update bills list
        function updateBillsList() {
            // Clear current lists
            upcomingBillsList.innerHTML = '';
            billHistoryList.innerHTML = '';
            
            // Get current date
            const now = new Date();
            const today = new Date(now.getFullYear(), now.getMonth(), now.getDate());
            
            // Separate bills into upcoming and history
            const upcomingBills = [];
            const billHistory = [];
            
            appData.bills.forEach(bill => {
                const dueDate = new Date(bill.dueDate);
                
                if (bill.status === 'paid') {
                    billHistory.push(bill);
                } else if (dueDate >= today) {
                    upcomingBills.push(bill);
                } else {
                    // Overdue bills
                    bill.status = 'overdue';
                    upcomingBills.push(bill);
                }
            });
            
            // Sort upcoming bills by due date
            upcomingBills.sort((a, b) => new Date(a.dueDate) - new Date(b.dueDate));
            
            // Sort bill history by paid date (most recent first)
            billHistory.sort((a, b) => new Date(b.paidDate) - new Date(a.paidDate));
            
            // Display upcoming bills
            if (upcomingBills.length === 0) {
                upcomingBillsList.innerHTML = `
                    <div class="empty-state">
                        <i class="fas fa-file-invoice-dollar"></i>
                        <p>No upcoming bills</p>
                    </div>
                `;
            } else {
                upcomingBills.forEach(bill => {
                    const billItem = document.createElement('div');
                    billItem.className = 'bill-item';
                    
                    // Calculate days remaining
                    const dueDate = new Date(bill.dueDate);
                    const timeDiff = dueDate.getTime() - today.getTime();
                    const daysRemaining = Math.ceil(timeDiff / (1000 * 3600 * 24));
                    
                    let statusClass = 'status-pending';
                    let statusText = 'Pending';
                    
                    if (bill.status === 'overdue') {
                        statusClass = 'status-overdue';
                        statusText = 'Overdue';
                    } else if (bill.status === 'paid') {
                        statusClass = 'status-paid';
                        statusText = 'Paid';
                    }
                    
                    billItem.innerHTML = `
                        <div class="bill-details">
                            <h3>${bill.name}</h3>
                            <p>${getCurrencySymbol()}${bill.amount.toFixed(2)} • Due: ${formatDate(dueDate)}</p>
                            <div class="bill-status ${statusClass}">${statusText}</div>
                            ${bill.status === 'overdue' ? `<div class="days-remaining days-low">${Math.abs(daysRemaining)} days overdue</div>` : 
                              bill.status === 'pending' ? `<div class="days-remaining ${daysRemaining <= 7 ? 'days-low' : daysRemaining <= 14 ? 'days-medium' : 'days-high'}">${daysRemaining} days remaining</div>` : ''}
                        </div>
                        <div class="bill-actions">
                            ${bill.status !== 'paid' ? `<button class="pay-btn" data-bill-id="${bill.id}">Mark Paid</button>` : ''}
                            <button class="btn-icon edit-btn" data-bill-id="${bill.id}">
                                <i class="fas fa-edit"></i>
                            </button>
                            <button class="btn-icon delete-btn" data-bill-id="${bill.id}">
                                <i class="fas fa-trash"></i>
                            </button>
                        </div>
                    `;
                    
                    upcomingBillsList.appendChild(billItem);
                });
            }
            
            // Display bill history
            if (billHistory.length === 0) {
                billHistoryList.innerHTML = `
                    <div class="empty-state">
                        <i class="fas fa-history"></i>
                        <p>No bill history</p>
                    </div>
                `;
            } else {
                billHistory.forEach(bill => {
                    const billItem = document.createElement('div');
                    billItem.className = 'bill-item';
                    
                    billItem.innerHTML = `
                        <div class="bill-details">
                            <h3>${bill.name}</h3>
                            <p>${getCurrencySymbol()}${bill.amount.toFixed(2)} • Paid: ${formatDate(new Date(bill.paidDate))}</p>
                            <div class="bill-status status-paid">Paid</div>
                        </div>
                        <div class="bill-actions">
                            <button class="btn-icon edit-btn" data-bill-id="${bill.id}">
                                <i class="fas fa-edit"></i>
                            </button>
                            <button class="btn-icon delete-btn" data-bill-id="${bill.id}">
                                <i class="fas fa-trash"></i>
                            </button>
                        </div>
                    `;
                    
                    billHistoryList.appendChild(billItem);
                });
            }
            
            // Add event listeners to bill actions
            document.querySelectorAll('.pay-btn').forEach(btn => {
                btn.addEventListener('click', (e) => {
                    const billId = e.target.getAttribute('data-bill-id');
                    markBillAsPaid(billId);
                });
            });
            
            document.querySelectorAll('.bill-actions .edit-btn').forEach(btn => {
                btn.addEventListener('click', (e) => {
                    const billId = e.target.getAttribute('data-bill-id');
                    // editBill(billId);
                    showNotification('Edit bill functionality would be implemented here.', 'info');
                });
            });
            
            document.querySelectorAll('.bill-actions .delete-btn').forEach(btn => {
                btn.addEventListener('click', (e) => {
                    const billId = e.target.getAttribute('data-bill-id');
                    deleteBill(billId);
                });
            });
        }

        // Mark bill as paid
        function markBillAsPaid(billId) {
            const billIndex = appData.bills.findIndex(b => b.id === billId);
            
            if (billIndex === -1) {
                showNotification('Bill not found.', 'error');
                return;
            }
            
            appData.bills[billIndex].status = 'paid';
            appData.bills[billIndex].paidDate = new Date().toISOString().split('T')[0];
            
            // Add to activity history
            addActivityHistory('bill', `Paid ${appData.bills[billIndex].name} bill (${getCurrencySymbol()}${appData.bills[billIndex].amount.toFixed(2)})`);
            
            saveData();
            
            updateBillsList();
            updateHistoryTab();
            
            showNotification('Bill marked as paid!', 'success');
        }

        // Delete bill
        function deleteBill(billId) {
            const billIndex = appData.bills.findIndex(b => b.id === billId);
            
            if (billIndex === -1) {
                showNotification('Bill not found.', 'error');
                return;
            }
            
            appData.bills.splice(billIndex, 1);
            saveData();
            
            updateBillsList();
            
            showNotification('Bill deleted successfully!', 'success');
        }

        // AI Financial Advisor functions
        function assessRisk() {
            // Get selected answers
            const timeHorizon = document.querySelector('input[name="time-horizon"]:checked');
            const reaction = document.querySelector('input[name="reaction"]:checked');
            const incomePercent = document.querySelector('input[name="income-percent"]:checked');
            
            if (!timeHorizon || !reaction || !incomePercent) {
                showNotification('Please answer all risk assessment questions.', 'error');
                return;
            }
            
            // Calculate risk score (simplified)
            const timeScore = parseInt(timeHorizon.value);
            const reactionScore = parseInt(reaction.value);
            const incomeScore = parseInt(incomePercent.value);
            
            const totalScore = timeScore + reactionScore + incomeScore;
            
            // Determine risk level
            let riskLevelText, riskDescriptionText, riskClass;
            
            if (totalScore <= 6) {
                riskLevelText = 'Low';
                riskDescriptionText = 'Based on your answers, you have a low risk tolerance. We recommend conservative investments like bonds, fixed deposits, and money market funds.';
                riskClass = 'low-risk';
                appData.riskProfile = 'low';
            } else if (totalScore <= 9) {
                riskLevelText = 'Medium';
                riskDescriptionText = 'Based on your answers, you have a medium risk tolerance. We recommend a balanced portfolio with a mix of stocks, bonds, and real estate.';
                riskClass = 'medium-risk';
                appData.riskProfile = 'medium';
            } else {
                riskLevelText = 'High';
                riskDescriptionText = 'Based on your answers, you have a high risk tolerance. We recommend growth-oriented investments like stocks, cryptocurrencies, and venture capital.';
                riskClass = 'high-risk';
                appData.riskProfile = 'high';
            }
            
            // Update UI
            riskLevel.textContent = riskLevelText;
            riskDescription.textContent = riskDescriptionText;
            riskResult.className = `risk-result ${riskClass}`;
            riskResult.style.display = 'block';
            
            saveData();
            
            showNotification('Risk assessment completed!', 'success');
        }

        function getInvestmentAdvice() {
            // Get selected investment preferences
            const selectedOptions = document.querySelectorAll('.investment-option.selected');
            
            if (selectedOptions.length === 0) {
                showNotification('Please select at least one investment preference.', 'error');
                return;
            }
            
            const preferences = Array.from(selectedOptions).map(option => option.getAttribute('data-value'));
            appData.investmentPreferences = preferences;
            
            // Get selected country
            const countryCode = countrySelect.value;
            const countryName = countrySelect.options[countrySelect.selectedIndex].text;
            
            // Show loading state
            aiResponseContent.innerHTML = `
                <div class="ai-loading">
                    <i class="fas fa-robot"></i>
                    <p>AI is analyzing your preferences and generating personalized advice...</p>
                </div>
            `;
            aiResponse.classList.add('show');
            
            // Simulate AI processing (in a real app, this would be an API call)
            setTimeout(() => {
                generateInvestmentAdvice(countryName, preferences);
            }, 2000);
        }

        function generateInvestmentAdvice(countryName, preferences) {
            let advice = `
                <h4>Personalized Investment Advice for ${countryName}</h4>
                <p>Based on your <strong>${appData.riskProfile} risk tolerance</strong> and interest in <strong>${preferences.join(', ')}</strong>, here are my recommendations:</p>
                
                <h5>Recommended Investment Strategy</h5>
                <ul>
            `;
            
            if (appData.riskProfile === 'low') {
                advice += `
                    <li><strong>Allocation:</strong> 70% Fixed Income, 20% Real Estate, 10% Stocks</li>
                    <li><strong>Focus:</strong> Capital preservation with moderate growth</li>
                    <li><strong>Time Horizon:</strong> Short to medium term (1-5 years)</li>
                `;
            } else if (appData.riskProfile === 'medium') {
                advice += `
                    <li><strong>Allocation:</strong> 50% Stocks, 30% Fixed Income, 20% Real Estate</li>
                    <li><strong>Focus:</strong> Balanced growth with some risk</li>
                    <li><strong>Time Horizon:</strong> Medium to long term (3-7 years)</li>
                `;
            } else {
                advice += `
                    <li><strong>Allocation:</strong> 70% Stocks, 20% Cryptocurrency, 10% Venture Capital</li>
                    <li><strong>Focus:</strong> High growth with acceptance of volatility</li>
                    <li><strong>Time Horizon:</strong> Long term (5+ years)</li>
                `;
            }
            
            advice += `</ul>`;
            
            // Add specific recommendations based on preferences
            advice += `<h5>Specific Recommendations</h5><ul>`;
            
            if (preferences.includes('stocks')) {
                advice += `<li>Consider investing in blue-chip companies in ${countryName} with strong fundamentals and consistent dividend payments.</li>`;
            }
            
            if (preferences.includes('bonds')) {
                advice += `<li>Government bonds in ${countryName} offer stable returns with lower risk, suitable for conservative investors.</li>`;
            }
            
            if (preferences.includes('real-estate')) {
                advice += `<li>Real estate investment trusts (REITs) in ${countryName} provide exposure to property markets without direct ownership.</li>`;
            }
            
            if (preferences.includes('crypto')) {
                advice += `<li>For cryptocurrency, consider established coins like Bitcoin and Ethereum, but limit exposure to 5-10% of your portfolio.</li>`;
            }
            
            if (preferences.includes('mutual-funds')) {
                advice += `<li>Diversified mutual funds in ${countryName} offer professional management and instant diversification.</li>`;
            }
            
            if (preferences.includes('business')) {
                advice += `<li>Consider angel investing in promising startups in ${countryName}, but be prepared for high risk and illiquidity.</li>`;
            }
            
            advice += `</ul>`;
            
            // Add next steps
            advice += `
                <h5>Next Steps to Financial Freedom</h5>
                <ol>
                    <li><strong>Start Small:</strong> Begin with what you can afford to lose and gradually increase investments.</li>
                    <li><strong>Diversify:</strong> Spread your investments across different asset classes to reduce risk.</li>
                    <li><strong>Educate Yourself:</strong> Continuously learn about investment strategies and market trends.</li>
                    <li><strong>Monitor Regularly:</strong> Review your portfolio quarterly and rebalance as needed.</li>
                    <li><strong>Think Long-Term:</strong> Avoid emotional decisions based on short-term market fluctuations.</li>
                </ol>
                
                <p>Remember, the path to financial freedom is a marathon, not a sprint. Stay disciplined, be patient, and make informed decisions.</p>
            `;
            
            // Update UI
            aiResponseContent.innerHTML = advice;
            
            showNotification('AI investment advice generated!', 'success');
        }

        function updateInvestmentOpportunities() {
            // In a real app, this would fetch real data based on the selected country
            // For this demo, we'll just update the country name
            const countryName = countrySelect.options[countrySelect.selectedIndex].text;
            selectedCountryName.textContent = countryName;
            
            showNotification(`Investment opportunities updated for ${countryName}`, 'success');
        }

        function sendChatMessage() {
            const message = chatInput.value.trim();
            
            if (!message) {
                return;
            }
            
            // Add user message to chat
            const userMessage = document.createElement('div');
            userMessage.className = 'chat-message user-message';
            userMessage.innerHTML = `<p>${message}</p>`;
            chatMessages.appendChild(userMessage);
            
            // Clear input
            chatInput.value = '';
            
            // Scroll to bottom
            chatMessages.scrollTop = chatMessages.scrollHeight;
            
            // Simulate AI response (in a real app, this would be an API call)
            setTimeout(() => {
                generateChatResponse(message);
            }, 1000);
        }

        function generateChatResponse(userMessage) {
            let response = '';
            
            // Simple keyword-based responses (in a real app, this would be more sophisticated)
            if (userMessage.toLowerCase().includes('hello') || userMessage.toLowerCase().includes('hi')) {
                response = 'Hello! How can I help you with your financial goals today?';
            } else if (userMessage.toLowerCase().includes('investment') || userMessage.toLowerCase().includes('invest')) {
                response = 'I can help you with investment advice. Have you completed the risk assessment questionnaire? That would help me provide more personalized recommendations.';
            } else if (userMessage.toLowerCase().includes('savings') || userMessage.toLowerCase().includes('save')) {
                response = 'Saving money is a great habit! I recommend setting a monthly savings goal and tracking your progress in the Financial Calendar.';
            } else if (userMessage.toLowerCase().includes('debt') || userMessage.toLowerCase().includes('loan')) {
                response = 'Managing debt is important for financial health. Consider prioritizing high-interest debts first and creating a repayment plan.';
            } else if (userMessage.toLowerCase().includes('budget') || userMessage.toLowerCase().includes('budgeting')) {
                response = 'Budgeting is key to financial success. Track your income and expenses, and allocate funds to different categories based on your priorities.';
            } else if (userMessage.toLowerCase().includes('retirement') || userMessage.toLowerCase().includes('pension')) {
                response = 'It\'s never too early to plan for retirement. Consider contributing to retirement accounts and investing in long-term growth assets.';
            } else {
                response = 'I understand you\'re asking about financial matters. For more specific advice, please provide more details or use the risk assessment and investment recommendation features.';
            }
            
            // Add AI message to chat
            const aiMessage = document.createElement('div');
            aiMessage.className = 'chat-message ai-message';
            aiMessage.innerHTML = `<p>${response}</p>`;
            chatMessages.appendChild(aiMessage);
            
            // Scroll to bottom
            chatMessages.scrollTop = chatMessages.scrollHeight;
        }

        // Analytics Tab functions
        function updateAnalyticsTab() {
            // Update savings analytics
            updateSavingsAnalytics();
            
            // Update expense analytics
            updateExpenseAnalytics();
            
            // Update portfolio allocation
            updatePortfolioAllocation();
            
            // Update risk vs return
            updateRiskReturn();
            
            // Update financial health score
            updateFinancialHealthScore();
        }

        function updateSavingsAnalytics() {
            const ctx = document.getElementById('savings-analytics-chart').getContext('2d');
            
            // Generate sample data for the chart
            const months = ['Jan', 'Feb', 'Mar', 'Apr', 'May', 'Jun'];
            const savingsData = months.map(() => Math.floor(Math.random() * 2000) + 500);
            
            if (window.savingsAnalyticsChartInstance) {
                window.savingsAnalyticsChartInstance.destroy();
            }
            
            window.savingsAnalyticsChartInstance = new Chart(ctx, {
                type: 'bar',
                data: {
                    labels: months,
                    datasets: [{
                        label: 'Savings',
                        data: savingsData,
                        backgroundColor: '#00e5ff',
                        borderColor: '#00e5ff',
                        borderWidth: 1
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
                            grid: {
                                color: 'rgba(255, 255, 255, 0.1)'
                            },
                            ticks: {
                                color: '#b0b0b0'
                            }
                        },
                        x: {
                            grid: {
                                color: 'rgba(255, 255, 255, 0.1)'
                            },
                            ticks: {
                                color: '#b0b0b0'
                            }
                        }
                    }
                }
            });
            
            // Update stats
            const totalSavings = appData.savings.reduce((sum, saving) => sum + saving.amount, 0);
            const avgMonthly = totalSavings / 6; // Assuming 6 months of data
            avgMonthlySaving.textContent = `${getCurrencySymbol()}${avgMonthly.toFixed(2)}`;
            
            savingsGrowth.textContent = '+12.5%';
            savingsConsistency.textContent = '85%';
        }

        function updateExpenseAnalytics() {
            const ctx = document.getElementById('expense-analytics-chart').getContext('2d');
            
            // Generate sample data for the chart
            const categories = ['Housing', 'Food', 'Transport', 'Entertainment', 'Utilities', 'Other'];
            const expenseData = categories.map(() => Math.floor(Math.random() * 1000) + 100);
            
            if (window.expenseAnalyticsChartInstance) {
                window.expenseAnalyticsChartInstance.destroy();
            }
            
            window.expenseAnalyticsChartInstance = new Chart(ctx, {
                type: 'doughnut',
                data: {
                    labels: categories,
                    datasets: [{
                        data: expenseData,
                        backgroundColor: [
                            '#00e5ff',
                            '#00ff9d',
                            '#ffc400',
                            '#ff3860',
                            '#8c52ff',
                            '#ff6b9d'
                        ],
                        borderWidth: 0
                    }]
                },
                options: {
                    responsive: true,
                    maintainAspectRatio: false,
                    plugins: {
                        legend: {
                            position: 'bottom',
                            labels: {
                                color: '#b0b0b0',
                                font: {
                                    size: 12
                                }
                            }
                        }
                    }
                }
            });
            
            // Update stats
            largestExpense.textContent = `${getCurrencySymbol()}850.00`;
            expenseTrend.textContent = '-5.2%';
            savingsRatio.textContent = '32%';
        }

        function updatePortfolioAllocation() {
            const ctx = document.getElementById('portfolio-allocation-chart').getContext('2d');
            
            // Generate sample data for the chart
            const types = ['Stocks', 'Bonds', 'Real Estate', 'Crypto', 'Cash'];
            const allocationData = types.map(() => Math.floor(Math.random() * 40) + 10);
            
            // Normalize to 100%
            const total = allocationData.reduce((sum, value) => sum + value, 0);
            const normalizedData = allocationData.map(value => (value / total) * 100);
            
            if (window.portfolioAllocationChartInstance) {
                window.portfolioAllocationChartInstance.destroy();
            }
            
            window.portfolioAllocationChartInstance = new Chart(ctx, {
                type: 'pie',
                data: {
                    labels: types,
                    datasets: [{
                        data: normalizedData,
                        backgroundColor: [
                            '#00e5ff',
                            '#00ff9d',
                            '#ffc400',
                            '#ff3860',
                            '#8c52ff'
                        ],
                        borderWidth: 0
                    }]
                },
                options: {
                    responsive: true,
                    maintainAspectRatio: false,
                    plugins: {
                        legend: {
                            position: 'bottom',
                            labels: {
                                color: '#b0b0b0',
                                font: {
                                    size: 12
                                }
                            }
                        }
                    }
                }
            });
        }

        function updateRiskReturn() {
            const ctx = document.getElementById('risk-return-chart').getContext('2d');
            
            // Generate sample data for the chart
            const investments = [
                { name: 'Stocks', risk: 7, return: 9 },
                { name: 'Bonds', risk: 3, return: 4 },
                { name: 'Real Estate', risk: 5, return: 6 },
                { name: 'Crypto', risk: 9, return: 12 },
                { name: 'Cash', risk: 1, return: 1 }
            ];
            
            if (window.riskReturnChartInstance) {
                window.riskReturnChartInstance.destroy();
            }
            
            window.riskReturnChartInstance = new Chart(ctx, {
                type: 'scatter',
                data: {
                    datasets: [{
                        label: 'Investments',
                        data: investments.map(inv => ({
                            x: inv.risk,
                            y: inv.return,
                            name: inv.name
                        })),
                        backgroundColor: '#00e5ff',
                        borderColor: '#00e5ff',
                        pointRadius: 8,
                        pointHoverRadius: 10
                    }]
                },
                options: {
                    responsive: true,
                    maintainAspectRatio: false,
                    plugins: {
                        legend: {
                            display: false
                        },
                        tooltip: {
                            callbacks: {
                                label: function(context) {
                                    const point = investments[context.dataIndex];
                                    return `${point.name}: Risk ${point.risk}/10, Return ${point.return}%`;
                                }
                            }
                        }
                    },
                    scales: {
                        y: {
                            title: {
                                display: true,
                                text: 'Expected Return (%)',
                                color: '#b0b0b0'
                            },
                            beginAtZero: true,
                            grid: {
                                color: 'rgba(255, 255, 255, 0.1)'
                            },
                            ticks: {
                                color: '#b0b0b0'
                            }
                        },
                        x: {
                            title: {
                                display: true,
                                text: 'Risk Level (1-10)',
                                color: '#b0b0b0'
                            },
                            beginAtZero: true,
                            grid: {
                                color: 'rgba(255, 255, 255, 0.1)'
                            },
                            ticks: {
                                color: '#b0b0b0'
                            }
                        }
                    }
                }
            });
        }

        function updateFinancialHealthScore() {
            // Calculate financial health score (simplified)
            const totalSavings = appData.savings.reduce((sum, saving) => sum + saving.amount, 0);
            const emergencyFundValue = appData.savingsCategories.emergency ? appData.savingsCategories.emergency.current : 0;
            const monthlyIncome = 5000; // Example monthly income
            
            // Emergency fund score (target: 3-6 months of expenses)
            const emergencyFundMonths = emergencyFundValue / (monthlyIncome * 0.6); // Assuming 60% of income as expenses
            const emergencyFundScore = Math.min(10, Math.floor(emergencyFundMonths / 0.6));
            
            // Debt score (simplified - lower debt is better)
            const debtScore = 8;
            
            // Savings rate score
            const savingsRate = (totalSavings / (monthlyIncome * 12)) * 100;
            const savingsScore = Math.min(10, Math.floor(savingsRate / 5));
            
            // Investment score
            const totalInvestments = appData.investments.reduce((sum, inv) => sum + inv.amount, 0);
            const investmentRatio = totalInvestments / (totalSavings + totalInvestments);
            const investmentScore = Math.min(10, Math.floor(investmentRatio * 20));
            
            // Budgeting score (simplified)
            const budgetScore = 8;
            
            // Goal progress score
            const completedGoals = appData.goals.filter(goal => goal.completed).length;
            const totalGoals = appData.goals.length;
            const goalProgress = totalGoals > 0 ? (completedGoals / totalGoals) * 100 : 0;
            const goalScore = Math.min(10, Math.floor(goalProgress / 10));
            
            // Overall score
            const overallScore = Math.round(
                (emergencyFundScore + debtScore + savingsScore + investmentScore + budgetScore + goalScore) / 6
            );
            
            // Update UI
            financialScore.textContent = overallScore;
            emergencyFundScore.textContent = `${emergencyFundScore}/10`;
            debtScore.textContent = `${debtScore}/10`;
            savingsScore.textContent = `${savingsScore}/10`;
            investmentScore.textContent = `${investmentScore}/10`;
            budgetScore.textContent = `${budgetScore}/10`;
            goalScore.textContent = `${goalScore}/10`;
        }

        // History Tab functions
        function updateHistoryTab() {
            updateActivityHistory();
        }

        function updateActivityHistory() {
            // Clear current list
            activityHistoryList.innerHTML = '';
            
            // Get activity history
            const activities = [...appData.activityHistory]
                .sort((a, b) => new Date(b.timestamp) - new Date(a.timestamp));
            
            if (activities.length === 0) {
                activityHistoryList.innerHTML = `
                    <div class="empty-state">
                        <i class="fas fa-history"></i>
                        <p>No activity history</p>
                    </div>
                `;
                return;
            }
            
            activities.forEach(activity => {
                const historyEntry = document.createElement('div');
                historyEntry.className = 'history-entry';
                
                let typeClass = '';
                switch(activity.type) {
                    case 'saving':
                        typeClass = 'type-saving';
                        break;
                    case 'investment':
                        typeClass = 'type-investment';
                        break;
                    case 'goal':
                        typeClass = 'type-goal';
                        break;
                    case 'subscription':
                        typeClass = 'type-subscription';
                        break;
                    case 'bill':
                        typeClass = 'type-bill';
                        break;
                    case 'achievement':
                        typeClass = 'type-achievement';
                        break;
                    case 'debtor':
                        typeClass = 'type-debtor';
                        break;
                    case 'creditor':
                        typeClass = 'type-creditor';
                        break;
                    default:
                        typeClass = 'type-saving';
                }
                
                historyEntry.innerHTML = `
                    <div class="history-info">
                        <span class="history-type ${typeClass}">${activity.type.toUpperCase()}</span>
                        <span class="history-description">${activity.description}</span>
                    </div>
                    <div class="history-date">${formatDate(new Date(activity.timestamp))}</div>
                `;
                
                activityHistoryList.appendChild(historyEntry);
            });
        }

        function filterActivityHistory(timeFilter) {
            // In a real app, this would filter the activity history based on the selected time period
            // For this demo, we'll just show a message
            showNotification(`Activity history filtered to: ${timeFilter}`, 'success');
        }

        function addActivityHistory(type, description) {
            const activity = {
                id: Date.now().toString(),
                type: type,
                description: description,
                timestamp: new Date().toISOString()
            };
            
            appData.activityHistory.push(activity);
            
            // Keep only the last 100 activities to prevent storage issues
            if (appData.activityHistory.length > 100) {
                appData.activityHistory = appData.activityHistory.slice(-100);
            }
            
            saveData();
        }

        function exportToCsv() {
            // Create CSV content
            let csvContent = "Type,Description,Date\n";
            
            appData.activityHistory.forEach(activity => {
                csvContent += `"${activity.type}","${activity.description}","${formatDate(new Date(activity.timestamp))}"\n`;
            });
            
            // Create download link
            const blob = new Blob([csvContent], { type: 'text/csv' });
            const url = URL.createObjectURL(blob);
            const a = document.createElement('a');
            a.href = url;
            a.download = 'elite-finance-history.csv';
            document.body.appendChild(a);
            a.click();
            document.body.removeChild(a);
            URL.revokeObjectURL(url);
            
            showNotification('CSV file downloaded successfully!', 'success');
        }

        function exportToPdf() {
            // In a real app, this would generate a PDF report with activity history
            // For this demo, we'll just show a message
            showNotification('PDF export functionality would be implemented here.', 'info');
        }

        // Settings tab functions
        function saveSettings() {
            const monthlyTarget = parseFloat(monthlyTargetInput.value);
            const savingsReminder = savingsReminderSelect.value;
            const theme = themeSelect.value;
            
            if (!isNaN(monthlyTarget) && monthlyTarget > 0) {
                appData.monthlyTarget = monthlyTarget;
            }
            
            appData.settings.savingsReminder = savingsReminder;
            appData.settings.theme = theme;
            
            saveData();
            updateDashboard();
            updateSavingsTab();
            updateAnalyticsTab();
            
            showNotification('Settings saved successfully!', 'success');
        }

        function backupData() {
            // Create backup data
            const backup = {
                appData: appData,
                timestamp: new Date().toISOString()
            };
            
            // Create download link
            const blob = new Blob([JSON.stringify(backup, null, 2)], { type: 'application/json' });
            const url = URL.createObjectURL(blob);
            const a = document.createElement('a');
            a.href = url;
            a.download = 'elite-finance-backup.json';
            document.body.appendChild(a);
            a.click();
            document.body.removeChild(a);
            URL.revokeObjectURL(url);
            
            showNotification('Data backup downloaded successfully!', 'success');
        }

        function restoreData() {
            // In a real app, this would upload and restore a backup file
            // For this demo, we'll just show a message
            showNotification('Data restore functionality would be implemented here.', 'info');
        }

        function resetData() {
            if (confirm('Are you sure you want to reset all data? This action cannot be undone.')) {
                // Reset app data
                appData = {
                    currency: 'GHS',
                    monthlyTarget: 1000,
                    savings: [],
                    investments: [],
                    goals: [],
                    subscriptions: [],
                    bills: [],
                    debtors: [],
                    creditors: [],
                    achievements: {
                        firstSaver: { id: 'firstSaver', name: 'First Saver', description: 'Save your first GHS 100', icon: 'fas fa-seedling', target: 100, current: 100, unlocked: true },
                        consistentSaver: { id: 'consistentSaver', name: 'Consistent Saver', description: 'Save for 30 consecutive days', icon: 'fas fa-calendar-check', target: 30, current: 30, unlocked: true },
                        mountainMover: { id: 'mountainMover', name: 'Mountain Mover', description: 'Save GHS 10,000 in total', icon: 'fas fa-mountain', target: 10000, current: 4500, unlocked: false },
                        goalCrusher: { id: 'goalCrusher', name: 'Goal Crusher', description: 'Complete 5 financial goals', icon: 'fas fa-gem', target: 5, current: 2, unlocked: false },
                        diversifiedInvestor: { id: 'diversifiedInvestor', name: 'Diversified Investor', description: 'Invest in 3 different asset classes', icon: 'fas fa-chart-pie', target: 3, current: 1, unlocked: false },
                        financialGuardian: { id: 'financialGuardian', name: 'Financial Guardian', description: 'Build a 6-month emergency fund', icon: 'fas fa-shield-alt', target: 6, current: 1.5, unlocked: false }
                    },
                    savingsCategories: {
                        emergency: { id: 'emergency', name: 'Emergency Fund', target: 2000, current: 1500, color: '#00e5ff' },
                        vacation: { id: 'vacation', name: 'Vacation', target: 2000, current: 800, color: '#00ff9d' },
                        education: { id: 'education', name: 'Education', target: 10000, current: 2300, color: '#ffc400' },
                        retirement: { id: 'retirement', name: 'Retirement', target: 50000, current: 5600, color: '#ff3860' }
                    },
                    activityHistory: [],
                    settings: {
                        savingsReminder: 'weekly',
                        theme: 'dark'
                    },
                    riskProfile: 'low',
                    investmentPreferences: []
                };
                
                // Reset UI
                saveData();
                generateCalendar(currentMonth, currentYear);
                updateDashboard();
                updateSavingsTab();
                updateInvestmentsTab();
                updateGoalsTab();
                updateSubscriptionsTab();
                updateDebtorsTab();
                updateCreditorsTab();
                updateBillsList();
                updateAnalyticsTab();
                updateHistoryTab();
                
                showNotification('All data has been reset.', 'success');
            }
        }

        // Utility functions
        function getMonthName(month) {
            const months = [
                'January', 'February', 'March', 'April', 'May', 'June',
                'July', 'August', 'September', 'October', 'November', 'December'
            ];
            return months[month];
        }

        function formatDate(date) {
            return date.toLocaleDateString('en-US', {
                year: 'numeric',
                month: 'long',
                day: 'numeric'
            });
        }

        function getCurrencySymbol() {
            // In a real app, this would return the actual currency symbol
            // For this demo, we'll just return the currency code
            return `${appData.currency} `;
        }

        function showNotification(message, type) {
            notificationText.textContent = message;
            notification.className = `notification ${type} show`;
            
            setTimeout(() => {
                notification.classList.remove('show');
            }, 3000);
        }

        function calculateDaysRemaining(dateString) {
            const targetDate = new Date(dateString);
            const today = new Date();
            const timeDiff = targetDate.getTime() - today.getTime();
            return Math.ceil(timeDiff / (1000 * 3600 * 24));
        }

        function isOverdue(dateString) {
            const today = new Date();
            today.setHours(0, 0, 0, 0);
            const dueDate = new Date(dateString);
            return dueDate < today;
        }

        // Data persistence
        function saveData() {
            localStorage.setItem('elite-finance-data', JSON.stringify(appData));
        }

        function loadData() {
            const savedData = localStorage.getItem('elite-finance-data');
            if (savedData) {
                appData = JSON.parse(savedData);
                
                // Update UI with loaded data
                currencySelect.value = appData.currency;
                monthlyTargetInput.value = appData.monthlyTarget;
                savingsReminderSelect.value = appData.settings.savingsReminder;
                themeSelect.value = appData.settings.theme;
            }
        }

        // Initialize the app when the page loads
        document.addEventListener('DOMContentLoaded', initApp);
    </script>
</body>
</html>

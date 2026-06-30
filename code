<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Smart Budget Planner</title>
    <style>
        :root {
            --primary: #4361ee;
            --primary-light: #4895ef;
            --success: #2ec4b6;
            --warning: #ff9f1c;
            --danger: #e71d36;
            --dark: #212529;
            --gray: #6c757d;
            --light: #f8f9fa;
            --border: #dee2e6;
            --card-bg: #ffffff;
            --bg: #f4f7f6;
            
            --border-radius: 12px;
            --shadow: 0 4px 12px rgba(0, 0, 0, 0.05);
            --transition: all 0.3s ease;
        }

        * {
            box-sizing: border-box;
            margin: 0;
            padding: 0;
            font-family: 'Segoe UI', Roboto, Helvetica, Arial, sans-serif;
        }

        body {
            background-color: var(--bg);
            color: var(--dark);
            line-height: 1.6;
            padding: 20px;
        }

        .container {
            max-width: 1000px;
            margin: 0 auto;
            display: flex;
            flex-direction: column;
            gap: 20px;
        }

        .card {
            background: var(--card-bg);
            border-radius: var(--border-radius);
            padding: 24px;
            box-shadow: var(--shadow);
        }

        header.card {
            display: flex;
            justify-content: space-between;
            align-items: center;
            flex-wrap: wrap;
            gap: 15px;
        }

        h1 {
            font-size: 1.5rem;
            color: var(--primary);
            margin: 0;
        }

        .income-group {
            display: flex;
            align-items: center;
            gap: 10px;
        }

        .income-group label {
            font-weight: 600;
        }

        input[type="number"] {
            padding: 10px 15px;
            border: 1px solid var(--border);
            border-radius: 8px;
            font-size: 1rem;
            width: 150px;
            outline: none;
            transition: var(--transition);
        }

        input[type="number"]:focus {
            border-color: var(--primary);
            box-shadow: 0 0 0 3px rgba(67, 97, 238, 0.15);
        }

        /* Layout Grid */
        .grid-layout {
            display: grid;
            grid-template-columns: 1fr 1fr;
            gap: 20px;
        }

        @media (max-width: 768px) {
            .grid-layout {
                grid-template-columns: 1fr;
            }
        }

        /* Summary Dashboard */
        .summary-dashboard {
            display: flex;
            flex-direction: column;
            gap: 20px;
        }

        .stat-cards {
            display: grid;
            grid-template-columns: 1fr 1fr;
            gap: 15px;
        }

        .stat-card {
            background: var(--light);
            padding: 15px;
            border-radius: 10px;
            text-align: center;
            border: 1px solid var(--border);
        }

        .stat-card.highlight {
            background: rgba(46, 196, 182, 0.1);
            border-color: var(--success);
        }
        
        .stat-card.alert {
            background: rgba(231, 29, 54, 0.1);
            border-color: var(--danger);
            color: var(--danger);
        }

        .stat-title {
            font-size: 0.85rem;
            text-transform: uppercase;
            letter-spacing: 0.5px;
            color: var(--gray);
            margin-bottom: 5px;
        }

        .stat-card.alert .stat-title, 
        .stat-card.highlight .stat-title {
            color: inherit;
        }

        .stat-value {
            font-size: 1.5rem;
            font-weight: 700;
        }

        /* Main Progress Bar */
        .progress-container {
            margin-top: 10px;
        }
        
        .progress-header {
            display: flex;
            justify-content: space-between;
            margin-bottom: 8px;
            font-weight: 600;
        }

        .progress-bar-bg {
            height: 12px;
            background: var(--border);
            border-radius: 6px;
            overflow: hidden;
            position: relative;
        }

        .progress-fill {
            height: 100%;
            background: var(--primary);
            border-radius: 6px;
            transition: width 0.3s ease, background-color 0.3s ease;
        }

        .alert-message {
            color: var(--danger);
            font-size: 0.9rem;
            font-weight: 600;
            margin-top: 10px;
            display: none;
            align-items: center;
            gap: 5px;
        }

        /* Categories Section */
        .category-item {
            margin-bottom: 20px;
        }

        .category-header {
            display: flex;
            justify-content: space-between;
            align-items: center;
            margin-bottom: 8px;
        }

        .category-name {
            font-weight: 500;
        }

        .category-controls {
            display: flex;
            align-items: center;
            gap: 15px;
        }

        input[type="range"] {
            flex-grow: 1;
            accent-color: var(--primary);
            cursor: pointer;
        }

        .category-input {
            width: 100px;
            padding: 5px 10px;
        }

        /* History Section */
        .history-header {
            display: flex;
            justify-content: space-between;
            align-items: center;
            margin-bottom: 20px;
        }

        .btn {
            background: var(--primary);
            color: white;
            border: none;
            padding: 10px 20px;
            border-radius: 8px;
            font-weight: 600;
            cursor: pointer;
            transition: var(--transition);
        }

        .btn:hover {
            background: var(--primary-light);
            transform: translateY(-1px);
        }
        
        .btn.saved {
            background: var(--success);
        }

        .chart-container {
            display: flex;
            align-items: flex-end;
            height: 250px;
            gap: 15px;
            padding-top: 20px;
            overflow-x: auto;
            border-bottom: 1px solid var(--border);
            padding-bottom: 10px;
        }

        .chart-empty {
            width: 100%;
            height: 100%;
            display: flex;
            align-items: center;
            justify-content: center;
            color: var(--gray);
            font-style: italic;
        }

        .month-col {
            display: flex;
            flex-direction: column;
            align-items: center;
            gap: 8px;
            min-width: 60px;
        }

        .bar-group {
            display: flex;
            align-items: flex-end;
            gap: 4px;
            height: 200px;
            width: 100%;
            justify-content: center;
        }

        .bar {
            width: 20px;
            border-radius: 4px 4px 0 0;
            position: relative;
            transition: height 0.5s ease;
        }

        .bar.inc { background: var(--success); }
        .bar.exp { background: var(--primary); }
        .bar.exp.over { background: var(--danger); }

        .bar:hover::after {
            content: attr(data-val);
            position: absolute;
            top: -25px;
            left: 50%;
            transform: translateX(-50%);
            background: var(--dark);
            color: white;
            font-size: 0.75rem;
            padding: 3px 6px;
            border-radius: 4px;
            white-space: nowrap;
            pointer-events: none;
            z-index: 10;
        }

        .month-label {
            font-size: 0.8rem;
            color: var(--gray);
            font-weight: 600;
        }

        .legend {
            display: flex;
            justify-content: center;
            gap: 15px;
            margin-top: 15px;
            font-size: 0.85rem;
            color: var(--gray);
        }

        .legend-item {
            display: flex;
            align-items: center;
            gap: 5px;
        }

        .legend-color {
            width: 12px;
            height: 12px;
            border-radius: 2px;
        }
    </style>
</head>
<body>

<div class="container">
    <!-- Header -->
    <header class="card">
        <h1>Smart Budget Planner</h1>
        <div class="income-group">
            <label for="monthly-income">Monthly Income ($):</label>
            <input type="number" id="monthly-income" value="5000" min="0" step="100">
        </div>
    </header>

    <!-- Main Content Grid -->
    <div class="grid-layout">
        
        <!-- Left Column: Categories -->
        <div class="card" id="categories-panel">
            <h2 style="margin-bottom: 20px; font-size: 1.2rem;">Expenses</h2>
            <div id="categories-container">
                <!-- Categories injected via JS -->
            </div>
        </div>

        <!-- Right Column: Dashboard -->
        <div class="card summary-dashboard">
            <h2 style="font-size: 1.2rem;">Overview</h2>
            
            <div class="stat-cards">
                <div class="stat-card">
                    <div class="stat-title">Total Expenses</div>
                    <div class="stat-value" id="val-expenses">$0</div>
                </div>
                <div class="stat-card" id="card-remaining">
                    <div class="stat-title">Remaining</div>
                    <div class="stat-value" id="val-remaining">$0</div>
                </div>
                <div class="stat-card highlight" id="card-savings">
                    <div class="stat-title">Savings Rate</div>
                    <div class="stat-value" id="val-rate">0%</div>
                </div>
            </div>

            <div class="progress-container">
                <div class="progress-header">
                    <span>Budget Utilized</span>
                    <span id="val-percent">0%</span>
                </div>
                <div class="progress-bar-bg">
                    <div class="progress-fill" id="progress-bar"></div>
                </div>
                <div class="alert-message" id="alert-overspent">
                    ⚠️ You have exceeded your monthly income!
                </div>
            </div>
        </div>
    </div>

    <!-- Bottom Section: History -->
    <div class="card">
        <div class="history-header">
            <h2 style="font-size: 1.2rem;">Budget History</h2>
            <button class="btn" id="btn-save">Save Month</button>
        </div>
        
        <div class="chart-container" id="chart-container">
            <div class="chart-empty" id="chart-empty">
                Save a month to see your trend history here.
            </div>
            <!-- Bars injected via JS -->
        </div>
        
        <div class="legend" id="chart-legend" style="display: none;">
            <div class="legend-item">
                <div class="legend-color" style="background: var(--success);"></div> Income
            </div>
            <div class="legend-item">
                <div class="legend-color" style="background: var(--primary);"></div> Expenses
            </div>
            <div class="legend-item">
                <div class="legend-color" style="background: var(--danger);"></div> Overspent
            </div>
        </div>
    </div>
</div>

<script>
    // --- Application State ---
    const state = {
        income: 5000,
        categories: [
            { id: 'housing', name: 'Housing & Rent', value: 1500, max: 4000 },
            { id: 'food', name: 'Food & Groceries', value: 600, max: 2000 },
            { id: 'transport', name: 'Transportation', value: 300, max: 1500 },
            { id: 'utilities', name: 'Utilities & Bills', value: 250, max: 1000 },
            { id: 'entertainment', name: 'Entertainment', value: 200, max: 1000 },
            { id: 'health', name: 'Healthcare', value: 150, max: 1000 },
            { id: 'misc', name: 'Miscellaneous', value: 100, max: 1000 }
        ],
        history: [] // { monthLabel, income, expenses }
    };

    // --- DOM Elements ---
    const els = {
        incomeInput: document.getElementById('monthly-income'),
        catContainer: document.getElementById('categories-container'),
        valExpenses: document.getElementById('val-expenses'),
        valRemaining: document.getElementById('val-remaining'),
        valRate: document.getElementById('val-rate'),
        valPercent: document.getElementById('val-percent'),
        progressBar: document.getElementById('progress-bar'),
        cardRemaining: document.getElementById('card-remaining'),
        cardSavings: document.getElementById('card-savings'),
        alertOverspent: document.getElementById('alert-overspent'),
        btnSave: document.getElementById('btn-save'),
        chartContainer: document.getElementById('chart-container'),
        chartEmpty: document.getElementById('chart-empty'),
        chartLegend: document.getElementById('chart-legend')
    };

    // --- Formatters ---
    const formatCurrency = (num) => new Intl.NumberFormat('en-US', { style: 'currency', currency: 'USD', maximumFractionDigits: 0 }).format(num);
    const getMonthName = () => {
        const d = new Date();
        // Shift month forward by the number of history items to simulate time passing for the demo
        d.setMonth(d.getMonth() + state.history.length);
        return d.toLocaleDateString('en-US', { month: 'short', year: '2-digit' });
    };

    // --- Initialization ---
    function init() {
        // Event Listeners
        els.incomeInput.addEventListener('input', (e) => {
            state.income = parseFloat(e.target.value) || 0;
            updateDashboard();
        });

        els.btnSave.addEventListener('click', saveMonth);

        // Initial Renders
        renderCategories();
        updateDashboard();
    }

    // --- UI Rendering logic ---
    function renderCategories() {
        els.catContainer.innerHTML = '';
        
        state.categories.forEach((cat, index) => {
            const div = document.createElement('div');
            div.className = 'category-item';
            
            div.innerHTML = `
                <div class="category-header">
                    <span class="category-name">${cat.name}</span>
                    <span class="category-val" id="disp-${cat.id}">${formatCurrency(cat.value)}</span>
                </div>
                <div class="category-controls">
                    <input type="range" id="range-${cat.id}" min="0" max="${cat.max}" step="10" value="${cat.value}">
                    <input type="number" class="category-input" id="num-${cat.id}" min="0" step="10" value="${cat.value}">
                </div>
            `;
            els.catContainer.appendChild(div);

            // Bind Events
            const range = document.getElementById(`range-${cat.id}`);
            const num = document.getElementById(`num-${cat.id}`);
            const disp = document.getElementById(`disp-${cat.id}`);

            const syncValues = (val) => {
                let parsed = parseFloat(val) || 0;
                if(parsed < 0) parsed = 0;
                
                cat.value = parsed;
                range.value = parsed;
                num.value = parsed;
                disp.innerText = formatCurrency(parsed);
                updateDashboard();
            };

            range.addEventListener('input', (e) => syncValues(e.target.value));
            num.addEventListener('input', (e) => syncValues(e.target.value));
        });
    }

    function updateDashboard() {
        const totalExpenses = state.categories.reduce((sum, cat) => sum + cat.value, 0);
        const remaining = state.income - totalExpenses;
        const utilizedPercent = state.income > 0 ? (totalExpenses / state.income) * 100 : 0;
        const savingsRate = state.income > 0 && remaining > 0 ? (remaining / state.income) * 100 : 0;
        
        const isOverspent = remaining < 0;

        // Update Text Values
        els.valExpenses.innerText = formatCurrency(totalExpenses);
        els.valRemaining.innerText = formatCurrency(remaining);
        els.valRate.innerText = savingsRate.toFixed(1) + '%';
        els.valPercent.innerText = utilizedPercent.toFixed(1) + '%';

        // Update Progress Bar
        els.progressBar.style.width = Math.min(utilizedPercent, 100) + '%';
        
        // Handle Alerts and Colors
        if (isOverspent) {
            els.progressBar.style.backgroundColor = 'var(--danger)';
            els.cardRemaining.classList.add('alert');
            els.cardRemaining.classList.remove('highlight');
            els.cardSavings.style.opacity = '0.5';
            els.alertOverspent.style.display = 'flex';
        } else {
            // Safe zone logic (yellow if >80%, green/blue otherwise)
            els.progressBar.style.backgroundColor = utilizedPercent > 80 ? 'var(--warning)' : 'var(--primary)';
            els.cardRemaining.classList.remove('alert');
            els.cardRemaining.classList.add('highlight');
            els.cardSavings.style.opacity = '1';
            els.alertOverspent.style.display = 'none';
        }
    }

    function saveMonth() {
        const totalExpenses = state.categories.reduce((sum, cat) => sum + cat.value, 0);
        
        // Push current snapshot to history
        state.history.push({
            monthLabel: getMonthName(),
            income: state.income,
            expenses: totalExpenses
        });

        // UI Feedback on button
        const originalText = els.btnSave.innerText;
        els.btnSave.innerText = "Saved ✓";
        els.btnSave.classList.add('saved');
        
        setTimeout(() => {
            els.btnSave.innerText = originalText;
            els.btnSave.classList.remove('saved');
        }, 1500);

        renderHistory();
    }

    function renderHistory() {
        if (state.history.length === 0) return;
        
        els.chartEmpty.style.display = 'none';
        els.chartLegend.style.display = 'flex';

        // Find max value to scale the bars correctly based on container height
        const maxVal = Math.max(...state.history.map(d => Math.max(d.income, d.expenses)));
        
        let html = '';
        state.history.forEach(data => {
            // Calculate percentage heights relative to the highest overall value ever recorded
            const incHeight = (data.income / maxVal) * 100;
            const expHeight = (data.expenses / maxVal) * 100;
            const isOver = data.expenses > data.income;
            const expClass = isOver ? 'bar exp over' : 'bar exp';

            html += `
                <div class="month-col">
                    <div class="bar-group">
                        <div class="bar inc" style="height: ${incHeight}%;" data-val="Inc: ${formatCurrency(data.income)}"></div>
                        <div class="${expClass}" style="height: ${expHeight}%;" data-val="Exp: ${formatCurrency(data.expenses)}"></div>
                    </div>
                    <div class="month-label">${data.monthLabel}</div>
                </div>
            `;
        });

        els.chartContainer.innerHTML = html;
        
        // Auto-scroll to the right so newest entry is visible
        els.chartContainer.scrollLeft = els.chartContainer.scrollWidth;
    }

    // Run app
    init();

</script>
</body>
</html>

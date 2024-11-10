<!DOCTYPE html>
<html>
<head>
    <meta charset="UTF-8">
    <title>Budget Tracker</title>
    <script src="https://cdnjs.cloudflare.com/ajax/libs/Chart.js/3.7.0/chart.min.js"></script>
    <!-- Add date range picker -->
    <script src="https://cdnjs.cloudflare.com/ajax/libs/moment.js/2.29.1/moment.min.js"></script>
    <style>
        body {
            font-family: -apple-system, system-ui, sans-serif;
            max-width: 1400px;
            margin: 20px auto;
            padding: 20px;
            background: #f5f5f5;
        }
        .container {
            background: white;
            padding: 20px;
            border-radius: 8px;
            box-shadow: 0 2px 4px rgba(0,0,0,0.1);
        }
        .header-controls {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(200px, 1fr));
            gap: 20px;
            margin-bottom: 20px;
        }
        .stats-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(200px, 1fr));
            gap: 20px;
            margin: 20px 0;
        }
        .stat-card {
            background: #f8f9fa;
            padding: 15px;
            border-radius: 8px;
            text-align: center;
        }
        .stat-value {
            font-size: 24px;
            font-weight: bold;
            margin: 10px 0;
        }
        .transaction-row {
            display: grid;
            grid-template-columns: 100px 1fr 100px 200px 100px;
            gap: 10px;
            padding: 8px;
            border-bottom: 1px solid #eee;
            align-items: center;
        }
        .charts {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(400px, 1fr));
            gap: 20px;
            margin: 20px 0;
        }
        .chart-container {
            background: white;
            padding: 20px;
            border-radius: 8px;
            box-shadow: 0 2px 4px rgba(0,0,0,0.1);
            min-height: 300px;
        }
        select, button, input {
            padding: 8px;
            border: 1px solid #ddd;
            border-radius: 4px;
            background: white;
        }
        button {
            background: #007bff;
            color: white;
            border: none;
            cursor: pointer;
        }
        button:hover { background: #0056b3; }
        .expense { color: #dc3545; }
        .income { color: #28a745; }
        .recurring { background-color: #fff3cd; }
        .filters {
            display: flex;
            gap: 10px;
            margin: 10px 0;
            flex-wrap: wrap;
        }
        .tab-container {
            margin: 20px 0;
        }
        .tab-buttons {
            display: flex;
            gap: 10px;
            margin-bottom: 10px;
        }
        .tab-button {
            padding: 8px 16px;
            background: #f8f9fa;
            border: none;
            border-radius: 4px;
            color: #333;
            cursor: pointer;
        }
        .tab-button.active {
            background: #007bff;
            color: white;
        }
        .insights {
            background: #f8f9fa;
            padding: 15px;
            border-radius: 8px;
            margin: 20px 0;
        }
        .insight-item {
            margin: 10px 0;
            padding: 10px;
            background: white;
            border-radius: 4px;
            border-left: 4px solid #007bff;
        }
    </style>
</head>
<body>
    <div class="container">
        <h1>Advanced Budget Tracker</h1>
        
        <div class="header-controls">
            <div>
                <input type="file" id="csvFile" accept=".csv">
                <button onclick="processFile()">Load Statement</button>
            </div>
            <div>
                <select id="dateFilter" onchange="filterTransactions()">
                    <option value="all">All Time</option>
                    <option value="thisMonth">This Month</option>
                    <option value="lastMonth">Last Month</option>
                    <option value="last3Months">Last 3 Months</option>
                </select>
            </div>
            <div>
                <button onclick="exportData()">Export Analysis</button>
                <button onclick="saveCategories()">Save Categories</button>
            </div>
        </div>

        <div class="stats-grid">
            <div class="stat-card">
                <div>Total Expenses</div>
                <div id="totalExpenses" class="stat-value expense">$0</div>
            </div>
            <div class="stat-card">
                <div>Average Daily Spend</div>
                <div id="avgDailySpend" class="stat-value">$0</div>
            </div>
            <div class="stat-card">
                <div>Top Category</div>
                <div id="topCategory" class="stat-value">-</div>
            </div>
            <div class="stat-card">
                <div>Recurring Expenses</div>
                <div id="recurringTotal" class="stat-value expense">$0</div>
            </div>
        </div>

        <div class="tab-container">
            <div class="tab-buttons">
                <button class="tab-button active" onclick="showTab('charts')">Charts</button>
                <button class="tab-button" onclick="showTab('transactions')">Transactions</button>
                <button class="tab-button" onclick="showTab('insights')">Insights</button>
            </div>
        </div>

        <div id="chartsTab">
            <div class="charts">
                <div class="chart-container">
                    <canvas id="expensesPieChart"></canvas>
                </div>
                <div class="chart-container">
                    <canvas id="categoryBarChart"></canvas>
                </div>
                <div class="chart-container">
                    <canvas id="trendLineChart"></canvas>
                </div>
                <div class="chart-container">
                    <canvas id="weekdaySpendingChart"></canvas>
                </div>
            </div>
        </div>

        <div id="transactionsTab" style="display: none;">
            <div class="filters">
                <input type="text" id="searchInput" placeholder="Search transactions..." oninput="filterTransactions()">
                <select id="categoryFilter" onchange="filterTransactions()">
                    <option value="all">All Categories</option>
                </select>
                <select id="amountFilter" onchange="filterTransactions()">
                    <option value="all">All Amounts</option>
                    <option value="under20">Under $20</option>
                    <option value="20to50">$20 - $50</option>
                    <option value="50to100">$50 - $100</option>
                    <option value="over100">Over $100</option>
                </select>
                <label>
                    <input type="checkbox" id="recurringOnly" onchange="filterTransactions()">
                    Recurring Only
                </label>
            </div>
            <div id="transactions"></div>
        </div>

        <div id="insightsTab" style="display: none;">
            <div class="insights" id="insightsList">
                <!-- Insights will be populated here -->
            </div>
        </div>
    </div>

    <script>
        let transactions = [];
        let charts = {};
        let savedCategories = JSON.parse(localStorage.getItem('savedCategories') || '{}');

        // Enhanced categories with subcategories
        const categories = {
            'Income': ['Salary', 'Transfers In', 'Refunds', 'Other Income'],
            'Transfers': ['Internal Transfer', 'Savings', 'Investments'],
            'Food & Dining': ['Groceries', 'Restaurants', 'Coffee & Cafes', 'Food Delivery'],
            'Transportation': ['Fuel', 'Public Transport', 'Parking', 'Vehicle Maintenance'],
            'Shopping': ['Clothing', 'Electronics', 'Home Goods', 'Online Shopping'],
            'Bills & Utilities': ['Power', 'Internet', 'Phone', 'Insurance'],
            'Health': ['Medical', 'Pharmacy', 'Fitness', 'Personal Care'],
            'Entertainment': ['Movies', 'Sports', 'Games', 'Hobbies'],
            'Home': ['Rent/Mortgage', 'Hardware', 'Maintenance', 'Furniture'],
            'Pets': ['Food', 'Vet', 'Supplies', 'Care'],
            'Education': ['Tuition', 'Books', 'Courses', 'Supplies'],
            'Personal': ['Gifts', 'Charity', 'Personal Care'],
            'Travel': ['Flights', 'Accommodation', 'Activities'],
            'Alcohol & Bars': ['Bars', 'Liquor Stores'],
            'Fees & Interest': ['Bank Fees', 'Interest', 'Late Fees']
        };

        function processFile() {
            const file = document.getElementById('csvFile').files[0];
            if (!file) {
                alert('Please select a file first.');
                return;
            }

            const reader = new FileReader();
            reader.onload = function(e) {
                parseTransactions(e.target.result);
                initializeDisplay();
                analyzeTransactions();
            };
            reader.readAsText(file);
        }

        function parseTransactions(csv) {
            const lines = csv.split('\n');
            transactions = [];
            
            for (let i = 1; i < lines.length; i++) {
                if (!lines[i].trim()) continue;
                
                const [date, description, amount, balance] = lines[i].split(',');
                if (!date || !amount) continue;

                const parsedAmount = parseFloat(amount);
                const category = autoCategorizeTransaction(description);
                const isRecurring = detectRecurring(description);
                
                transactions.push({
                    date: date,
                    description: description,
                    amount: parsedAmount,
                    category: category,
                    isRecurring: isRecurring
                });
            }
        }

        function autoCategorizeTransaction(description) {
            // Use saved categories first
            const saved = savedCategories[description];
            if (saved) return saved;

            description = description.toLowerCase();
            
            // Enhanced categorization rules
            const rules = [
                { pattern: /transfer|tfr/i, category: 'Transfers' },
                { pattern: /coffee|cafe|weta/i, category: 'Food & Dining' },
                { pattern: /pak n save|countdown|new world|woolworths|fresh/i, category: 'Food & Dining' },
                { pattern: /pet|vet/i, category: 'Pets' },
                { pattern: /liquor|brew|bar/i, category: 'Alcohol & Bars' },
                { pattern: /mitre 10|hardware|bunnings/i, category: 'Home' },
                { pattern: /loan|interest|fee/i, category: 'Fees & Interest' },
                { pattern: /z |mobil|fuel|gas/i, category: 'Transportation' },
                { pattern: /medical|pharmacy|doctor|health/i, category: 'Health' },
                { pattern: /movie|cinema|netflix/i, category: 'Entertainment' },
                { pattern: /power|electricity|water|internet/i, category: 'Bills & Utilities' }
            ];

            for (const rule of rules) {
                if (rule.pattern.test(description)) {
                    return rule.category;
                }
            }

            return 'Uncategorized';
        }

        function detectRecurring(description) {
            // Pattern matching for common recurring payments
            const recurringPatterns = [
                /loan/i,
                /insurance/i,
                /power/i,
                /internet/i,
                /netflix/i,
                /spotify/i
            ];

            return recurringPatterns.some(pattern => pattern.test(description));
        }

        function analyzeTransactions() {
            // Calculate basic stats
            updateStats();
            
            // Generate insights
            generateInsights();
            
            // Update all charts
            updateCharts();
        }

        function updateStats() {
            const stats = calculateStats();
            
            document.getElementById('totalExpenses').textContent = 
                formatCurrency(stats.totalExpenses);
            document.getElementById('avgDailySpend').textContent = 
                formatCurrency(stats.averageDailySpend);
            document.getElementById('topCategory').textContent = 
                stats.topCategory;
            document.getElementById('recurringTotal').textContent = 
                formatCurrency(stats.recurringTotal);
        }

        function calculateStats() {
            let totalExpenses = 0;
            let categoryTotals = {};
            let recurringTotal = 0;
            
            transactions.forEach(t => {
                if (t.amount < 0) {
                    totalExpenses += Math.abs(t.amount);
                    categoryTotals[t.category] = (categoryTotals[t.category] || 0) + Math.abs(t.amount);
                    if (t.isRecurring) {
                        recurringTotal += Math.abs(t.amount);
                    }
                }
            });

            const topCategory = Object.entries(categoryTotals)
                .sort((a, b) => b[1] - a[1])[0][0];

            const uniqueDays = new Set(transactions.map(t => t.date)).size;
            const averageDailySpend = totalExpenses / uniqueDays;

            return {
                totalExpenses,
                averageDailySpend,
                topCategory,
                recurringTotal
            };
        }

        function generateInsights() {
            const insights = [];
            
            // Analyze spending patterns
            const weekdaySpending = analyzeWeekdaySpending();
            const highestSpendingDay = Object.entries(weekdaySpending)
                .sort((a, b) => b[1] - a[1])[0];
                
            insights.push({
                type: 'pattern',
                message: `Your highest spending day is ${highestSpendingDay[0]} 
                         with an average of ${formatCurrency(highestSpendingDay[1])}`
            });

            // Find large transactions
            const largeTransactions = transactions
                .filter(t => t.amount < -100)
                .sort((a, b) => a.amount - b.amount);
                
            if (largeTransactions.length > 0) {
                insights.push({
                    type: 'alert',
                    message: `Your largest expense was ${formatCurrency(Math.abs(largeTransactions[0].amount))} 
                             at ${largeTransactions[0].description}`
                });
            }

           ```javascript
            // Continuing generateInsights function...
            
            // Analyze recurring expenses
            const recurringExpenses = transactions
                .filter(t => t.isRecurring && t.amount < 0);
                
            if (recurringExpenses.length > 0) {
                insights.push({
                    type: 'info',
                    message: `You have ${recurringExpenses.length} recurring expenses totaling 
                             ${formatCurrency(Math.abs(recurringExpenses.reduce((sum, t) => sum + t.amount, 0)))} per month`
                });
            }

            // Category spending analysis
            const categorySpending = {};
            transactions.forEach(t => {
                if (t.amount < 0) {
                    categorySpending[t.category] = (categorySpending[t.category] || 0) + Math.abs(t.amount);
                }
            });

            const topCategories = Object.entries(categorySpending)
                .sort((a, b) => b[1] - a[1])
                .slice(0, 3);

            insights.push({
                type: 'summary',
                message: `Your top spending categories are: 
                         ${topCategories.map(([cat, amount]) => 
                             `${cat} (${formatCurrency(amount)})`).join(', ')}`
            });

            // Analyze daily patterns
            const dailyAverage = calculateDailyAverage();
            const highSpendingDays = transactions
                .filter(t => t.amount < -dailyAverage * 2)
                .length;

            if (highSpendingDays > 0) {
                insights.push({
                    type: 'alert',
                    message: `You had ${highSpendingDays} days with spending more than 
                             double your daily average of ${formatCurrency(dailyAverage)}`
                });
            }

            // Update insights display
            const insightsList = document.getElementById('insightsList');
            insightsList.innerHTML = insights.map(insight => `
                <div class="insight-item ${insight.type}">
                    ${insight.message}
                </div>
            `).join('');
        }

        function calculateDailyAverage() {
            const expenses = transactions
                .filter(t => t.amount < 0)
                .reduce((sum, t) => sum + Math.abs(t.amount), 0);
            const uniqueDays = new Set(transactions.map(t => t.date)).size;
            return expenses / uniqueDays;
        }

        function analyzeWeekdaySpending() {
            const weekdayTotals = {};
            const weekdayCounts = {};
            
            transactions.forEach(t => {
                if (t.amount < 0) {
                    const weekday = moment(t.date).format('dddd');
                    weekdayTotals[weekday] = (weekdayTotals[weekday] || 0) + Math.abs(t.amount);
                    weekdayCounts[weekday] = (weekdayCounts[weekday] || 0) + 1;
                }
            });

            // Calculate averages
            Object.keys(weekdayTotals).forEach(day => {
                weekdayTotals[day] = weekdayTotals[day] / weekdayCounts[day];
            });

            return weekdayTotals;
        }

        function updateCharts() {
            updatePieChart();
            updateBarChart();
            updateTrendLineChart();
            updateWeekdaySpendingChart();
        }

        function formatCurrency(amount) {
            return '$' + amount.toFixed(2);
        }

        function saveCategories() {
            localStorage.setItem('savedCategories', JSON.stringify(savedCategories));
            alert('Categories saved successfully!');
        }

        function exportData() {
            const analysis = {
                summary: calculateStats(),
                categoryTotals: calculateCategoryTotals(),
                insights: generateInsightsSummary(),
                transactions: transactions
            };

            const blob = new Blob([JSON.stringify(analysis, null, 2)], 
                                {type: 'application/json'});
            const url = URL.createObjectURL(blob);
            const a = document.createElement('a');
            a.href = url;
            a.download = 'budget-analysis.json';
            a.click();
        }

        function showTab(tabName) {
            // Hide all tabs
            document.getElementById('chartsTab').style.display = 'none';
            document.getElementById('transactionsTab').style.display = 'none';
            document.getElementById('insightsTab').style.display = 'none';

            // Show selected tab
            document.getElementById(tabName + 'Tab').style.display = 'block';

            // Update active button
            document.querySelectorAll('.tab-button').forEach(btn => {
                btn.classList.remove('active');
            });
            event.target.classList.add('active');
        }

        // Initialize the application
        function initializeDisplay() {
            populateCategoryFilter();
            filterTransactions();
            analyzeTransactions();
        }

        // Add event listeners when the document loads
        document.addEventListener('DOMContentLoaded', function() {
            // Initialize empty charts
            updateCharts();
        });
    </script>
</body>
</html>

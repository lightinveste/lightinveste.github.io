<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Light Invest - Smart Investment Platform</title>
    <link href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.0.0/css/all.min.css" rel="stylesheet">
    <link href="style.css" rel="stylesheet">
</head>
<body>
    <!-- Navigation -->
    <nav class="navbar" id="navbar">
        <div class="nav-container">
            <div class="nav-brand">
                <i class="fas fa-chart-line"></i>
                <span>Light Invest</span>
            </div>
            <div class="nav-menu" id="nav-menu">
                <a href="#" class="nav-link" data-page="dashboard">Dashboard</a>
                <a href="#" class="nav-link" data-page="investments">Investments</a>
                <a href="#" class="nav-link" data-page="p2p">P2P Trading</a>
                <a href="#" class="nav-link" data-page="subscription">Premium</a>
                <a href="#" class="nav-link" data-page="profile">Profile</a>
                <a href="#" class="nav-link admin-only" data-page="admin" style="display: none;">Admin</a>
                <button class="btn btn-outline" id="logout-btn">Logout</button>
            </div>
            <div class="nav-toggle" id="nav-toggle">
                <span></span>
                <span></span>
                <span></span>
            </div>
        </div>
    </nav>

    <!-- Main Content -->
    <main class="main-content">
        <!-- Auth Pages -->
        <div class="page" id="auth-page">
            <div class="auth-container">
                <div class="auth-card">
                    <div class="auth-header">
                        <h1><i class="fas fa-chart-line"></i> Light Invest</h1>
                        <p>Smart Investment Platform</p>
                    </div>
                    
                    <!-- Login Form -->
                    <form id="login-form" class="auth-form">
                        <h2>Welcome Back</h2>
                        <div class="form-group">
                            <label for="login-identifier">Email, Phone, or Username</label>
                            <input type="text" id="login-identifier" required>
                        </div>
                        <div class="form-group">
                            <label for="login-password">6-Digit Password</label>
                            <input type="password" id="login-password" maxlength="6" pattern="[0-9]{6}" required>
                        </div>
                        <button type="submit" class="btn btn-primary">Login</button>
                        <p class="auth-switch">Don't have an account? <a href="#" id="show-signup">Sign Up</a></p>
                    </form>

                    <!-- Signup Form -->
                    <form id="signup-form" class="auth-form" style="display: none;">
                        <h2>Create Account</h2>
                        <div class="form-group">
                            <label for="signup-username">Username</label>
                            <input type="text" id="signup-username" required>
                        </div>
                        <div class="form-group">
                            <label for="signup-email">Email (Optional)</label>
                            <input type="email" id="signup-email">
                        </div>
                        <div class="form-group">
                            <label for="signup-phone">Phone Number (Optional)</label>
                            <input type="tel" id="signup-phone">
                        </div>
                        <div class="form-group">
                            <label for="signup-password">6-Digit Password</label>
                            <input type="password" id="signup-password" maxlength="6" pattern="[0-9]{6}" required>
                        </div>
                        <button type="submit" class="btn btn-primary">Sign Up</button>
                        <p class="auth-switch">Already have an account? <a href="#" id="show-login">Login</a></p>
                    </form>
                </div>
            </div>
        </div>

        <!-- Dashboard Page -->
        <div class="page" id="dashboard-page" style="display: none;">
            <div class="page-header">
                <h1>Dashboard</h1>
                <div class="user-balance">
                    <span>Balance: </span>
                    <span class="balance-amount" id="user-balance">₦0.00</span>
                </div>
            </div>
            
            <div class="dashboard-grid">
                <div class="card">
                    <div class="card-header">
                        <h3><i class="fas fa-wallet"></i> Account Overview</h3>
                    </div>
                    <div class="card-body">
                        <div class="stat-grid">
                            <div class="stat-item">
                                <span class="stat-label">Total Balance</span>
                                <span class="stat-value" id="total-balance">₦0.00</span>
                            </div>
                            <div class="stat-item">
                                <span class="stat-label">Active Investments</span>
                                <span class="stat-value" id="active-investments">0</span>
                            </div>
                            <div class="stat-item">
                                <span class="stat-label">Total Earned</span>
                                <span class="stat-value" id="total-earned">₦0.00</span>
                            </div>
                            <div class="stat-item">
                                <span class="stat-label">Premium Status</span>
                                <span class="stat-value" id="premium-status">Free</span>
                            </div>
                        </div>
                    </div>
                </div>

                <div class="card">
                    <div class="card-header">
                        <h3><i class="fas fa-chart-line"></i> Recent Investments</h3>
                    </div>
                    <div class="card-body">
                        <div id="recent-investments">
                            <p class="empty-state">No investments yet</p>
                        </div>
                    </div>
                </div>

                <div class="card">
                    <div class="card-header">
                        <h3><i class="fas fa-exchange-alt"></i> Recent P2P Activity</h3>
                    </div>
                    <div class="card-body">
                        <div id="recent-p2p">
                            <p class="empty-state">No P2P activity yet</p>
                        </div>
                    </div>
                </div>
            </div>
        </div>

        <!-- Investments Page -->
        <div class="page" id="investments-page" style="display: none;">
            <div class="page-header">
                <h1>Investments</h1>
                <button class="btn btn-primary" id="create-investment-btn">
                    <i class="fas fa-plus"></i> New Investment
                </button>
            </div>

            <div class="investment-plans" id="investment-plans">
                <!-- Investment plans will be loaded here -->
            </div>

            <div class="card">
                <div class="card-header">
                    <h3>My Investments</h3>
                </div>
                <div class="card-body">
                    <div id="user-investments">
                        <p class="empty-state">No investments yet</p>
                    </div>
                </div>
            </div>
        </div>

        <!-- P2P Trading Page -->
        <div class="page" id="p2p-page" style="display: none;">
            <div class="page-header">
                <h1>P2P Trading</h1>
                <button class="btn btn-primary" id="create-p2p-order-btn">
                    <i class="fas fa-plus"></i> Create Order
                </button>
            </div>

            <div class="p2p-tabs">
                <button class="tab-btn active" data-tab="marketplace">Marketplace</button>
                <button class="tab-btn" data-tab="my-orders">My Orders</button>
                <button class="tab-btn" data-tab="my-transactions">My Transactions</button>
            </div>

            <div class="tab-content">
                <div class="tab-pane active" id="marketplace-tab">
                    <div class="p2p-filters">
                        <select id="order-type-filter">
                            <option value="">All Orders</option>
                            <option value="deposit">Deposit Orders</option>
                            <option value="withdraw">Withdraw Orders</option>
                        </select>
                    </div>
                    <div id="p2p-marketplace">
                        <p class="empty-state">No orders available</p>
                    </div>
                </div>

                <div class="tab-pane" id="my-orders-tab">
                    <div id="my-p2p-orders">
                        <p class="empty-state">No orders yet</p>
                    </div>
                </div>

                <div class="tab-pane" id="my-transactions-tab">
                    <div id="my-p2p-transactions">
                        <p class="empty-state">No transactions yet</p>
                    </div>
                </div>
            </div>
        </div>

        <!-- Subscription Page -->
        <div class="page" id="subscription-page" style="display: none;">
            <div class="page-header">
                <h1>Premium Subscription</h1>
            </div>

            <div class="subscription-status" id="subscription-status">
                <!-- Current subscription status -->
            </div>

            <div class="subscription-plans" id="subscription-plans">
                <!-- Subscription plans will be loaded here -->
            </div>
        </div>

        <!-- Profile Page -->
        <div class="page" id="profile-page" style="display: none;">
            <div class="page-header">
                <h1>Profile</h1>
            </div>

            <div class="card">
                <div class="card-header">
                    <h3>Personal Information</h3>
                </div>
                <div class="card-body">
                    <form id="profile-form">
                        <div class="form-group">
                            <label for="profile-username">Username</label>
                            <input type="text" id="profile-username" required>
                        </div>
                        <div class="form-group">
                            <label for="profile-email">Email</label>
                            <input type="email" id="profile-email">
                        </div>
                        <div class="form-group">
                            <label for="profile-phone">Phone Number</label>
                            <input type="tel" id="profile-phone">
                        </div>
                        <button type="submit" class="btn btn-primary">Update Profile</button>
                    </form>
                </div>
            </div>
        </div>

        <!-- Admin Page -->
        <div class="page" id="admin-page" style="display: none;">
            <div class="page-header">
                <h1>Admin Dashboard</h1>
            </div>

            <div class="admin-stats" id="admin-stats">
                <!-- Admin statistics -->
            </div>

            <div class="admin-tabs">
                <button class="tab-btn active" data-tab="users">Users</button>
                <button class="tab-btn" data-tab="investments">Investments</button>
                <button class="tab-btn" data-tab="p2p-transactions">P2P Transactions</button>
                <button class="tab-btn" data-tab="activities">Activities</button>
            </div>

            <div class="tab-content">
                <div class="tab-pane active" id="users-tab">
                    <div id="admin-users">
                        <!-- Users list -->
                    </div>
                </div>

                <div class="tab-pane" id="investments-tab">
                    <div id="admin-investments">
                        <!-- Investments list -->
                    </div>
                </div>

                <div class="tab-pane" id="p2p-transactions-tab">
                    <div id="admin-p2p-transactions">
                        <!-- P2P transactions list -->
                    </div>
                </div>

                <div class="tab-pane" id="activities-tab">
                    <div id="admin-activities">
                        <!-- Activities list -->
                    </div>
                </div>
            </div>
        </div>
    </main>

    <!-- Modals -->
    <div class="modal" id="investment-modal">
        <div class="modal-content">
            <div class="modal-header">
                <h3>Create Investment</h3>
                <button class="modal-close">&times;</button>
            </div>
            <div class="modal-body">
                <form id="investment-form">
                    <div class="form-group">
                        <label for="investment-plan">Investment Plan</label>
                        <select id="investment-plan" required>
                            <option value="">Select Plan</option>
                            <option value="1.5_weekly">1.5% Weekly Plan</option>
                            <option value="0.7_weekly">0.7% Weekly Plan</option>
                        </select>
                    </div>
                    <div class="form-group">
                        <label for="investment-amount">Amount (₦)</label>
                        <input type="number" id="investment-amount" min="1000" required>
                    </div>
                    <div class="form-group">
                        <label for="investment-months">Lock Period (Months)</label>
                        <input type="number" id="investment-months" min="1" required>
                    </div>
                    <div class="investment-preview" id="investment-preview">
                        <!-- Investment preview -->
                    </div>
                    <button type="submit" class="btn btn-primary">Create Investment</button>
                </form>
            </div>
        </div>
    </div>

    <div class="modal" id="p2p-order-modal">
        <div class="modal-content">
            <div class="modal-header">
                <h3>Create P2P Order</h3>
                <button class="modal-close">&times;</button>
            </div>
            <div class="modal-body">
                <form id="p2p-order-form">
                    <div class="form-group">
                        <label for="p2p-order-type">Order Type</label>
                        <select id="p2p-order-type" required>
                            <option value="">Select Type</option>
                            <option value="deposit">Deposit (Buy e-naira)</option>
                            <option value="withdraw">Withdraw (Sell e-naira)</option>
                        </select>
                    </div>
                    <div class="form-group">
                        <label for="p2p-order-amount">Amount (₦)</label>
                        <input type="number" id="p2p-order-amount" min="1" required>
                    </div>
                    <button type="submit" class="btn btn-primary">Create Order</button>
                </form>
            </div>
        </div>
    </div>

    <!-- Loading Spinner -->
    <div class="loading" id="loading" style="display: none;">
        <div class="spinner"></div>
    </div>

    <!-- Toast Notifications -->
    <div class="toast-container" id="toast-container"></div>

    <script src="script.js"></script>
</body>
</html>


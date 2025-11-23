Login -> Register -> View Balance Page -> Transfer Page -> Funds Page -> Bank Statement Page

----------------------------------------------------------------------------------------------------------------------------
common variable names (from the files you provided)

Session keys (used to pass user between pages)

$_SESSION['user_id']
$_SESSION['username']
$_SESSION['full_name']
$_SESSION['role']
Request parameter names

POST: username (index.php -> $_POST['username'])
POST: password (index.php -> $_POST['password'])
GET: aid (View_Balance.php links -> transfer.php?aid=..., statement.php?aid=...)
Shared resource variable

$pdo (from db_connect.php required by other pages)
----------------------------------------------------------------------------------------------------------------------------
// Session keys
define('SESSION_USER_ID',   'user_id');
define('SESSION_USERNAME',  'username');
define('SESSION_FULL_NAME', 'full_name');
define('SESSION_ROLE',      'role');

// Request parameter names
define('PARAM_USERNAME', 'username'); // $_POST['username']
define('PARAM_PASSWORD', 'password'); // $_POST['password']
define('PARAM_ACCOUNT_ID', 'aid');    // $_GET['aid']

// Shared resource name (DB variable provided by db_connect.php)
define('DB_PDO_VAR', 'pdo'); // keep $pdo in db_connect.php, require it

// Application
define('APP_NAME', 'Banking System (Group 9)');

// Optional: secure session start (call before session_start())
function start_secure_session(): void {
    $secure = !empty($_SERVER['HTTPS']) && $_SERVER['HTTPS'] !== 'off';
    session_set_cookie_params([
        'lifetime' => 0,
        'path' => '/',
        'domain' => '',
        'secure' => $secure,
        'httponly' => true,
        'samesite' => 'Lax',
    ]);
    if (session_status() === PHP_SESSION_NONE) {
        session_start();
----------------------------------------------------------------------------------------------------------------------------

User 1 (100-5-2100):
ali123
password1234

User 2 (100-4-4154):
wern1234
password1234

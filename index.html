<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Notification Terminal</title>
    <!-- FIXED: Valid CDN link for Supabase JS Library -->
    <script src="https://cdn.jsdelivr.net/npm/@supabase/supabase-js@2"></script>
    <style>
        body { font-family: sans-serif; background: #121214; color: #fff; display: flex; justify-content: center; align-items: center; min-height: 100vh; margin: 0; }
        .box { background: #202024; padding: 30px; border-radius: 8px; width: 100%; max-width: 360px; box-sizing: border-box; box-shadow: 0 8px 24px rgba(0,0,0,0.5); }
        h2 { margin: 0 0 10px 0; color: #00b37e; font-size: 20px; text-align: center; }
        p { color: #a8a8b3; font-size: 13px; line-height: 1.5; margin-bottom: 20px; text-align: center; }
        .input-group { margin-bottom: 15px; }
        label { display: block; font-size: 12px; margin-bottom: 5px; color: #e1e1e6; }
        input, select, textarea { width: 100%; padding: 12px; background: #121214; border: 1px solid #29292e; border-radius: 4px; color: #fff; box-sizing: border-box; font-size: 14px; }
        textarea { height: 70px; resize: none; }
        button { width: 100%; padding: 12px; background: #00875f; color: #fff; border: none; border-radius: 4px; font-weight: bold; cursor: pointer; font-size: 14px; }
        button:hover { background: #00b37e; }
        .hidden { display: none; }
        .nav-btn { background: #29292e; margin-top: 10px; }
        .nav-btn:hover { background: #323238; }
        .checkbox-container { display: flex; align-items: flex-start; gap: 10px; margin-bottom: 15px; }
        .checkbox-container input { width: auto; margin-top: 3px; }
    </style>
</head>
<body>

    <!-- PORTAL A: Friend's Sign-In and Authorization -->
    <div id="authPortal" class="box">
        <h2>Member Access</h2>
        <p>Sign in to configure device sync settings.</p>
        
        <div class="input-group">
            <label>Google Username / ID</label>
            <input type="text" id="loginUser" placeholder="e.g., friend_google_name">
        </div>

        <div class="checkbox-container">
            <input type="checkbox" id="termsCheck">
            <label for="termsCheck">I explicitly agree to the terms of policy allowing this platform to register and dispatch custom web notifications directly to this browser profile.</label>
        </div>
        
        <button onclick="grantAccessAndRegister()">Sign In & Authorize</button>
        <button class="nav-btn" onclick="toggleScreen('panel')">Open Admin Control Panel</button>
    </div>

    <!-- PORTAL B: Your Dispatch Control Panel -->
    <div id="adminPanel" class="box hidden">
        <h2>Control Terminal</h2>
        <p>Target active profiles on the cloud framework.</p>
        
        <div class="input-group">
            <label>Target Google Username</label>
            <input type="text" id="targetUser" placeholder="Type friend's username">
        </div>

        <div class="input-group">
            <label>Notification Engine Profile</label>
            <select id="notifStyle">
                <option value="Chrome Notification">Chrome Notification Format</option>
                <option value="Profile Update">User Profile Format</option>
                <option value="System Alert">System Alert Format</option>
            </select>
        </div>

        <div class="input-group">
            <label>Custom Payload Message</label>
            <textarea id="msgBody" placeholder="Type message payload..."></textarea>
        </div>

        <button onclick="dispatchRemoteNotification()">Transmit Web Notification</button>
        <button class="nav-btn" onclick="toggleScreen('auth')">← Back to Member Login</button>
    </div>

    <script>
        // FIXED: Replaced string domain with protocol structure
        const supabaseUrl = 'https://uwaecevqyciqvfutlgem.supabase.co'; 
        const supabaseKey = 'sb_publishable_7xYysbmwhFfLZ4lVBoKUvw_gf3rw3zM';
        
        // FIXED: Corrected reference initialization format
        const supabase = window.supabase.createClient(supabaseUrl, supabaseKey);

        // Friend Registers & Authorizes Permissions
        async function grantAccessAndRegister() {
            const username = document.getElementById('loginUser').value.trim().toLowerCase();
            const checked = document.getElementById('termsCheck').checked;

            if (!username) return alert('Enter a valid username profile.');
            if (!checked) return alert('You must check the agreement box to accept policies.');

            const permission = await Notification.requestPermission();
            if (permission !== 'granted') return alert('System notifications denied by browser architecture.');

            // Upsert a record to notify the db this profile is ready
            const { error } = await supabase.from('user_tokens').upsert([
                { username: username, last_signal: new Date().toISOString(), message: "", format: "" }
            ], { onConflict: 'username' });

            if (error) {
                return alert('Database error: ' + error.message);
            }

            alert(`Access Verified! Browser profile registered under target: ${username}`);
            
            // FIXED: Live database listener tracks modifications to trigger actions remotely
            supabase.channel('custom-filter-channel')
            .on('postgres_changes', { event: 'UPDATE', schema: 'public', table: 'user_tokens', filter: `username=eq.${username}` }, (payload) => {
                if (payload.new && payload.new.message) {
                    new Notification(payload.new.format || "Alert", {
                        body: payload.new.message
                    });
                }
            })
            .subscribe();
        }

        // Fetch Data and Fire Alert
        async function dispatchRemoteNotification() {
            const target = document.getElementById('targetUser').value.trim().toLowerCase();
            const format = document.getElementById('notifStyle').value;
            const message = document.getElementById('msgBody').value.trim();

            if (!target || !message) return alert('Please input targeting credentials and messages.');

            // FIXED: Updates table variables to pass information live down to the subscriber client
            const { error } = await supabase
                .from('user_tokens')
                .update({ message: message, format: format, last_signal: new Date().toISOString() })
                .eq('username', target);

            if (error) {
                return alert(`Active link error: ${error.message}`);
            }

            alert(`Signal transmitted to database infrastructure for user: ${target}`);
        }

        function toggleScreen(screen) {
            if(screen === 'panel') {
                document.getElementById('authPortal').classList.add('hidden');
                document.getElementById('adminPanel').classList.remove('hidden');
            } else {
                document.getElementById('adminPanel').classList.add('hidden');
                document.getElementById('authPortal').classList.remove('hidden');
            }
        }
    </script>
</body>
</html>

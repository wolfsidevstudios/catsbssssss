<script lang="ts">
  import Login from './lib/Login.svelte';
  import Dashboard from './lib/Dashboard.svelte';

  let isLoggedIn = $state(false);
  let loggedInUser = $state<{ email: string; name: string; } | null>(null);

  function handleLoginSuccess(event: CustomEvent<{ email: string; name: string; }>) {
    loggedInUser = event.detail;
    isLoggedIn = true;
  }

  function handleLogout() {
    isLoggedIn = false;
    loggedInUser = null;
  }
</script>

<main class="min-h-screen bg-gray-100 flex items-center justify-center p-4">
  {#if isLoggedIn}
    <Dashboard on:logout={handleLogout} user={loggedInUser} />
  {:else}
    <Login on:loginSuccess={handleLoginSuccess} />
  {/if}

  <div style="position: fixed; bottom: 16px; right: 16px; background: rgba(255, 255, 255, 0.7); backdrop-filter: blur(10px); -webkit-backdrop-filter: blur(10px); padding: 6px 12px; border-radius: 9999px; font-size: 12px; color: #333; border: 1px solid rgba(0, 0, 0, 0.1); box-shadow: 0 2px 10px rgba(0,0,0,0.1); z-index: 1000;">Built with ⚡️ Silo</div>
</main>

<script lang="ts">
  let email = $state('');
  let password = $state('');
  let errorMessage = $state('');

  function handleSubmit() {
    errorMessage = ''; // Clear previous errors

    if (!email.trim() || !password.trim()) {
      errorMessage = 'Please enter both email and password.';
      return;
    }

    // Simulate API call or authentication
    console.log('Attempting login with:', { email, password });

    // In a real app, you'd send this to a server and handle the response
    // For now, just log and clear fields on success, or show an error.
    if (email === 'user@example.com' && password === 'password123') {
      alert('Login successful! (Simulated)');
      email = '';
      password = '';
    } else {
      errorMessage = 'Invalid email or password.';
    }
  }
</script>

<div class="w-full max-w-md bg-white p-8 rounded-lg shadow-lg">
  <h2 class="text-3xl font-bold text-center text-gray-800 mb-6">Login</h2>
  
  <form onsubmit|preventDefault={handleSubmit} class="space-y-6">
    <div>
      <label for="email" class="block text-sm font-medium text-gray-700">Email address</label>
      <input
        type="email"
        id="email"
        name="email"
        autocomplete="email"
        required
        bind:value={email}
        class="mt-1 block w-full px-4 py-2 border border-gray-300 rounded-md shadow-sm focus:ring-indigo-500 focus:border-indigo-500 sm:text-sm"
        placeholder="you@example.com"
      />
    </div>

    <div>
      <label for="password" class="block text-sm font-medium text-gray-700">Password</label>
      <input
        type="password"
        id="password"
        name="password"
        autocomplete="current-password"
        required
        bind:value={password}
        class="mt-1 block w-full px-4 py-2 border border-gray-300 rounded-md shadow-sm focus:ring-indigo-500 focus:border-indigo-500 sm:text-sm"
        placeholder="••••••••"
      />
    </div>

    {#if errorMessage}
      <p class="text-red-600 text-sm">{errorMessage}</p>
    {/if}

    <div>
      <button
        type="submit"
        class="w-full flex justify-center py-2 px-4 border border-transparent rounded-md shadow-sm text-sm font-medium text-white bg-indigo-600 hover:bg-indigo-700 focus:outline-none focus:ring-2 focus:ring-offset-2 focus:ring-indigo-500"
      >
        Sign in
      </button>
    </div>
  </form>
</div>

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

<div class="w-full max-w-md bg-white p-8 rounded-xl shadow-2xl border border-gray-200">
  <h1 class="text-4xl font-extrabold text-center text-gray-900 mb-8">Welcome Back!</h1>
  
  <form onsubmit|preventDefault={handleSubmit} class="space-y-6">
    <div>
      <label for="email" class="block text-sm font-medium text-gray-700 mb-1">Email address</label>
      <input
        type="email"
        id="email"
        name="email"
        autocomplete="email"
        required
        bind:value={email}
        class="mt-1 block w-full px-4 py-2.5 border border-gray-300 rounded-lg shadow-sm focus:ring-indigo-500 focus:border-indigo-500 sm:text-base transition duration-150 ease-in-out"
        placeholder="you@example.com"
      />
    </div>

    <div>
      <label for="password" class="block text-sm font-medium text-gray-700 mb-1">Password</label>
      <input
        type="password"
        id="password"
        name="password"
        autocomplete="current-password"
        required
        bind:value={password}
        class="mt-1 block w-full px-4 py-2.5 border border-gray-300 rounded-lg shadow-sm focus:ring-indigo-500 focus:border-indigo-500 sm:text-base transition duration-150 ease-in-out"
        placeholder="••••••••"
      />
    </div>

    {#if errorMessage}
      <p class="text-red-700 text-sm font-medium bg-red-100 p-3 rounded-lg border border-red-200">{errorMessage}</p>
    {/if}

    <div class="flex items-center justify-between text-sm">
      <div class="flex items-center">
        <input id="remember-me" name="remember-me" type="checkbox" class="h-4 w-4 text-indigo-600 focus:ring-indigo-500 border-gray-300 rounded">
        <label for="remember-me" class="ml-2 block text-gray-900">
          Remember me
        </label>
      </div>
      <div class="text-sm">
        <a href="#" class="font-medium text-indigo-600 hover:text-indigo-500">
          Forgot your password?
        </a>
      </div>
    </div>

    <div>
      <button
        type="submit"
        class="w-full flex justify-center py-3 px-4 border border-transparent rounded-lg shadow-md text-base font-semibold text-white bg-gradient-to-r from-indigo-600 to-purple-700 hover:from-indigo-700 hover:to-purple-800 focus:outline-none focus:ring-2 focus:ring-offset-2 focus:ring-indigo-500 transition duration-150 ease-in-out"
      >
        Sign in
      </button>
    </div>
  </form>

  <div class="mt-8 text-center text-sm text-gray-600">
    Don't have an account?
    <a href="#" class="font-medium text-indigo-600 hover:text-indigo-500">Sign up</a>
  </div>
</div>
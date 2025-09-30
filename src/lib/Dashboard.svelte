<script lang="ts">
  import { createEventDispatcher } from 'svelte';

  const dispatch = createEventDispatcher();

  export let user: { email: string; name: string; } | null;

  type UserSchema = { id: string; name: string; email: string; };

  // Simulated data conforming to the 'users' database schema
  const users: UserSchema[] = [
    { id: 'a1b2c3d4-e5f6-7890-1234-567890abcdef', name: 'Alice Smith', email: 'alice@example.com' },
    { id: 'b2c3d4e5-f6a7-8901-2345-67890abcdef0', name: 'Bob Johnson', email: 'bob@example.com' },
    { id: 'c3d4e5f6-a7b8-9012-3456-7890abcdef01', name: 'Charlie Brown', email: 'charlie@example.com' },
    { id: 'd4e5f6a7-b8c9-0123-4567-890abcdef012', name: 'Diana Prince', email: 'diana@example.com' },
  ];

  function handleLogout() {
    dispatch('logout');
  }
</script>

<div class="w-full max-w-2xl bg-white p-8 rounded-xl shadow-2xl border border-gray-200">
  <div class="flex justify-between items-center mb-6">
    <h1 class="text-3xl font-extrabold text-gray-900">Welcome, {user?.name || 'Guest'}!</h1>
    <button
      on:click={handleLogout}
      class="py-2 px-4 border border-transparent rounded-lg shadow-sm text-sm font-medium text-white bg-red-600 hover:bg-red-700 focus:outline-none focus:ring-2 focus:ring-offset-2 focus:ring-red-500 transition duration-150 ease-in-out"
    >
      Logout
    </button>
  </div>

  <h2 class="text-2xl font-bold text-gray-800 mb-4">Registered Users (Simulated from DB Schema)</h2>

  <div class="overflow-x-auto">
    <table class="min-w-full divide-y divide-gray-200">
      <thead class="bg-gray-50">
        <tr>
          <th scope="col" class="px-6 py-3 text-left text-xs font-medium text-gray-500 uppercase tracking-wider">ID</th>
          <th scope="col" class="px-6 py-3 text-left text-xs font-medium text-gray-500 uppercase tracking-wider">Name</th>
          <th scope="col" class="px-6 py-3 text-left text-xs font-medium text-gray-500 uppercase tracking-wider">Email</th>
        </tr>
      </thead>
      <tbody class="bg-white divide-y divide-gray-200">
        {#each users as dbUser (dbUser.id)}
          <tr>
            <td class="px-6 py-4 whitespace-nowrap text-sm text-gray-500">{dbUser.id.substring(0, 8)}...</td>
            <td class="px-6 py-4 whitespace-nowrap text-sm font-medium text-gray-900">{dbUser.name}</td>
            <td class="px-6 py-4 whitespace-nowrap text-sm text-gray-500">{dbUser.email}</td>
          </tr>
        {/each}
      </tbody>
    </table>
  </div>
</div>
<script>

	export let name;

	let users;
onMount(async () => {
  const response = await fetch('http://localhost:8092/cliente');
  users = await response.json();
});


</script>

<main>
	<h1>Hello {name}!</h1>
	<p>Visit the <a href="https://svelte.dev/tutorial">Svelte tutorial</a> to learn how to build Svelte apps.</p>

	{#each users as user}
    <div class="user-card">
      <h2>{user.firstName} {user.lastName}</h2>
      <p>Email: {user.email}</p>
      <p>Region: {user.region.name}</p>
    </div>
  {/each}
</main>

<style>
	.user-card {
    border: 1px solid #ddd;
    padding: 1em;
    margin-bottom: 1em;
  }

	main {
		text-align: center;
		padding: 1em;
		max-width: 240px;
		margin: 0 auto;
	}

	h1 {
		color: #ff3e00;
		text-transform: uppercase;
		font-size: 4em;
		font-weight: 100;
	}

	@media (min-width: 640px) {
		main {
			max-width: none;
		}
	}
</style>
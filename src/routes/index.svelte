<script>
	const menu = [
		"Mercado",
		"Terbregsehof",
		"Postzegel Penthouse",
		"Republica",
		"Schelfhorst",
		"De Har"
	]
</script>

<svelte:head>
	<title>Loer menu</title>
</svelte:head>

<h1>Menu</h1>

<ul>
	{#each menu as item}
		<li>
			<a href="{item}">{item}</a>
		</li>
	{/each}
</ul>

<style>
	ul {
		list-style: none;
		padding: 0;
		font-size: 4em;
		text-align: center;
	}
	ul a {
		text-decoration: none;
		position: relative;
		transform: translateX(-10%);
	}
	ul a:before {
		content: "";
		position: absolute;
		bottom: .2em;
		left: -100vw;
		height: 2px;
		width: 98vw;
		background: #000;
	}
	ul a:after {
		content: "";
		position: absolute;
		bottom: .2em;
		right: -100vw;
		height: 2px;
		width: 98vw;
		background: #000;
	}
</style>
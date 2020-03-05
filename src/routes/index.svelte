<script>
	import { slide } from 'svelte/transition';
	import { quintOut } from 'svelte/easing';

	let font_size = 16 * 4;
	function getWidth (count) {
		var width  = font_size * count * .8;
		var playArea = window.innerWidth - width;
		return (playArea * Math.random()) - playArea/2;
	}
	const menu = [
		{
			name: "Mercado"
		},
		{
			name: "Terbregsehof"
		},
		{
			name: "Postzegel Penthouse"
		},
		{
			name: "Republica"
		},
		{
			name: "Schelfhorst"
		},
		{
			name: "De Har"
		}
	];
	for ( let i in menu ) {
		var item = menu[i];
		menu[i].width = getWidth(item['name'].length);
	}


</script>

<svelte:head>
	<title>Loer menu</title>
</svelte:head>

<h1>Menu</h1>

<ul>
	{#each menu as item, index}
		<li>
			<a
				in:slide="{{delay: 0, duration: 300, easing: quintOut }}"
				href="{item.name}"
				style="transform: translateX({item.width}px)">
					{item.name}
			</a>
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
		display: inline-block;
	}
	ul a:before,
	ul a:after {
		content: "";
		position: absolute;
		bottom: .2em;
		right: -100vw;
		height: 2px;
		width: 98vw;
		background: #000;
	}
	ul a:before {
		left: -100vw;
		width: 98vw;
	}
	ul a:after {
		right: -100vw;
		width: 98vw;
	}
	li {
		overflow: hidden;
	}
</style>
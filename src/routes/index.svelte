<script>
	import { fly } from 'svelte/transition';
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

<div class="content">
	<ul>
		{#each menu as item, index}
			<li in:fly="{{
				delay: 50*index + 50,
				duration: 400,
				y: 100,
				easing: quintOut
				}}">
				<a href="/office"
					style="transform: translateX({item.width}px); animation-delay:{50*index + 50}ms;" >
						{item.name}
				</a>
			</li>
		{/each}
	</ul>
</div>

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
		white-space: nowrap;
	}
	ul a:before,
	ul a:after {
		content: "";
		position: absolute;
		bottom: .2em;
		height: 2px;
		width: 98vw;
		background: #000;
		animation: width-in 1s backwards;
		animation-delay: inherit;
	}
	ul a:before { left: 100%; }
	ul a:after { right: 100%; }
	li { overflow: hidden; }
	@keyframes width-in {
		0% {
			width: 0;
		}
	}	
</style>
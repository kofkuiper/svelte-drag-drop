<script lang="ts">
	import DragDrop from '$lib/components/DragDrop.svelte';

	let items = [
		'https://andrewhawkes.github.io/codepen-assets/steam-game-cards/game_1.jpg',
		'https://andrewhawkes.github.io/codepen-assets/steam-game-cards/game_2.jpg',
		'https://andrewhawkes.github.io/codepen-assets/steam-game-cards/game_3.jpg',
		'https://andrewhawkes.github.io/codepen-assets/steam-game-cards/game_4.jpg'
	];
</script>

<DragDrop bind:items />

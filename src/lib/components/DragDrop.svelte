<script lang="ts">
	import { createEventDispatcher } from 'svelte';

	export let items: string[] = [];
	const dispatch = createEventDispatcher();

	type EventType = Event & { dataTransfer?: any; target?: any };

	function setDraggedIndex(e: EventType) {
		e.dataTransfer.setData('draggedParentIndex', e.target.dataset.index);
	}
	function onDragStart(e: EventType) {
		dispatch('onDragStart', e);
		setDraggedIndex(e);
	}
	function onDrag(e: EventType) {
		dispatch('onDrag', e);
	}
	function onDragend(e: EventType) {
		dispatch('onDragend', e);
	}
	function onDragEnter(e: EventType) {
		e.preventDefault();
		dispatch('onDragEnter', e);
	}
	function onDragOver(e: EventType) {
		e.preventDefault();
		dispatch('onDragOver', e);
	}
	function onDragLeave(e: EventType) {
		dispatch('onDragLeave', e);
	}
	function onDrop(e: EventType) {
		e.preventDefault();
		dispatch('onDrop', e);
		onDropped(e);
	}

	function onDropped(e: EventType) {
		const from = e.dataTransfer.getData('draggedParentIndex');
		const to = e.target.dataset.index;
		if (from != to) {
			sortItems(from, to);
		}
	}

	function sortItems(fromIndex: number, toIndex: number) {
		const tempFrom = items[fromIndex];
		items[fromIndex] = items[toIndex];
		items[toIndex] = tempFrom;
	}
</script>

<div class="main">
	<div class="l-container">
		{#each items as item, index}
			<!-- svelte-ignore a11y-no-static-element-interactions -->
			<div
				data-index={index}
				class="b-game-card"
				on:dragstart={onDragStart}
				on:drag={onDrag}
				on:dragend={onDragend}
				draggable="true"
				on:dragenter={onDragEnter}
				on:dragover={onDragOver}
				on:dragleave={onDragLeave}
				on:drop={onDrop}
			>
				<div
					data-index={index}
					id={index.toString()}
					class="b-game-card__cover"
					style="background-image: url({item});"
				></div>
			</div>
		{/each}
	</div>
</div>

<style>
	* {
		margin: 0;
		padding: 0;
		box-sizing: border-box;
	}

	.main {
		display: flex;
		justify-content: center;
		align-items: center;
		min-height: 100vh;
		background: #ffffff;
	}

	.l-container {
		display: grid;
		grid-template-columns: repeat(4, 1fr);
		grid-gap: 30px;
		width: 100%;
		max-width: 1200px;
		padding: 30px;
	}
	@media screen and (max-width: 760px) {
		.l-container {
			grid-template-columns: repeat(2, 1fr);
		}
	}

	.b-game-card {
		position: relative;
		z-index: 1;
		width: 100%;
		padding-bottom: 150%;
		perspective: 1000px;
	}
	.b-game-card__cover {
		position: absolute;
		z-index: 1;
		top: 0;
		left: 0;
		width: 100%;
		height: 100%;
		overflow: hidden;
		background-image: linear-gradient(120deg, #f6d365 0%, #fda085 100%);
		background-size: cover;
		perspective-origin: 50% 50%;
		transform-style: preserve-3d;
		transform-origin: top center;
		will-change: transform;
		transform: skewX(0.001deg);
		transition: transform 0.35s ease-in-out;
	}
	.b-game-card__cover::after {
		display: block;
		content: '';
		position: absolute;
		z-index: 100;
		top: 0;
		left: 0;
		width: 100%;
		height: 120%;
		background: linear-gradient(
			226deg,
			rgba(255, 255, 255, 0.4) 0%,
			rgba(255, 255, 255, 0.4) 35%,
			rgba(255, 255, 255, 0.2) 42%,
			rgba(255, 255, 255, 0) 60%
		);
		transform: translateY(-20%);
		will-change: transform;
		transition: transform 0.65s cubic-bezier(0.18, 0.9, 0.58, 1);
	}
	.b-game-card:hover .b-game-card__cover {
		transform: rotateX(7deg) translateY(-6px);
	}
	.b-game-card:hover .b-game-card__cover::after {
		transform: translateY(0%);
	}
	.b-game-card::before {
		display: block;
		content: '';
		position: absolute;
		top: 5%;
		left: 5%;
		width: 90%;
		height: 90%;
		background: rgba(0, 0, 0, 0.5);
		box-shadow: 0 6px 12px 12px rgba(0, 0, 0, 0.4);
		will-change: opacity;
		transform-origin: top center;
		transform: skewX(0.001deg);
		transition:
			transform 0.35s ease-in-out,
			opacity 0.5s ease-in-out;
	}
	.b-game-card:hover::before {
		opacity: 0.6;
		transform: rotateX(7deg) translateY(-6px) scale(1.05);
	}
</style>

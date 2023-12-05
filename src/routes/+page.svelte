<script lang="ts">
	import DragDrop from '$lib/components/DragDrop.svelte';
	let items = [
		'https://images.unsplash.com/photo-1700730025710-58ff304c1c8b?crop=entropy&cs=tinysrgb&fit=max&fm=jpg&ixid=MnwxfDB8MXxyYW5kb218MHx8fHx8fHx8MTcwMTc4MTEyMA&ixlib=rb-4.0.3&q=80&w=1080',
		'https://images.unsplash.com/photo-1692736933712-c757798b689b?crop=entropy&cs=tinysrgb&fit=max&fm=jpg&ixid=MnwxfDB8MXxyYW5kb218MHx8fHx8fHx8MTcwMTc4MTExNw&ixlib=rb-4.0.3&q=80&w=1080',
		'https://images.unsplash.com/photo-1700442546454-0a73f2ff6625?crop=entropy&cs=tinysrgb&fit=max&fm=jpg&ixid=MnwxfDB8MXxyYW5kb218MHx8fHx8fHx8MTcwMTc4MTExNA&ixlib=rb-4.0.3&q=80&w=1080',
		'https://images.unsplash.com/photo-1693634293922-b91d1a2a7c28?crop=entropy&cs=tinysrgb&fit=max&fm=jpg&ixid=MnwxfDB8MXxyYW5kb218MHx8fHx8fHx8MTcwMTc4MTE4Ng&ixlib=rb-4.0.3&q=80&w=1080',
		'https://images.unsplash.com/photo-1699903577109-b9072c4b87b4?crop=entropy&cs=tinysrgb&fit=max&fm=jpg&ixid=MnwxfDB8MXxyYW5kb218MHx8fHx8fHx8MTcwMTc4MTIwMA&ixlib=rb-4.0.3&q=80&w=1080',
		'https://images.unsplash.com/photo-1697617279806-f151d25022ba?crop=entropy&cs=tinysrgb&fit=max&fm=jpg&ixid=MnwxfDB8MXxyYW5kb218MHx8fHx8fHx8MTcwMTc4MTIxMQ&ixlib=rb-4.0.3&q=80&w=1080',
		'https://images.unsplash.com/photo-1698859858637-9aa64302f629?crop=entropy&cs=tinysrgb&fit=max&fm=jpg&ixid=MnwxfDB8MXxyYW5kb218MHx8fHx8fHx8MTcwMTc4MTIyMg&ixlib=rb-4.0.3&q=80&w=1080',
		'https://images.unsplash.com/photo-1682173051316-86ad29c08b6a?crop=entropy&cs=tinysrgb&fit=max&fm=jpg&ixid=MnwxfDB8MXxyYW5kb218MHx8fHx8fHx8MTcwMTc4MTIzMw&ixlib=rb-4.0.3&q=80&w=1080'
	];
	type EventType = Event & { dataTransfer?: any; target?: any };

	// Handle Drag & Drop events
	function onDragStart(e: EventType) {
		console.log('onDragStart: ', e);
	}
	function onDrag(e: EventType) {
		console.log('onDrag: ', e);
	}
	function onDragEnd(e: EventType) {
		console.log('onDragEnd: ', e);
	}
	function onDragEnter(e: EventType) {
		console.log('onDragEnter: ', e);
	}
	function onDragOver(e: EventType) {
		console.log('onDragOver: ', e);
	}
	function onDragLeave(e: EventType) {
		console.log('onDragLeave: ', e);
	}
	function onDrop(e: EventType) {
		console.log('onDrop: ', e);
	}
</script>

<div class="terminal-loader">
	<div class="terminal-header">
		<div class="terminal-title">Install</div>
		<div class="terminal-controls">
			<div class="control close"></div>
			<div class="control minimize"></div>
			<div class="control maximize"></div>
		</div>
	</div>
	<div style="margin-top: 1.5em;">
		<h2>Svelte Drag Drop</h2>
		<span>🚀https://github.com/kofkuiper/svelte-drag-drop</span>
	</div>
	<div class="text">npm i svelte-drag-drop</div>
</div>

<DragDrop
	bind:items
	on:onDragStart={(e) => onDragStart(e.detail)}
	on:onDrag={(e) => onDrag(e.detail)}
	on:onDragEnd={(e) => onDragEnd(e.detail)}
	on:onDragEnter={(e) => onDragEnter(e.detail)}
	on:onDragOver={(e) => onDragOver(e.detail)}
	on:onDragLeave={(e) => onDragLeave(e.detail)}
	on:onDrop={(e) => onDrop(e.detail)}
/>

<style>
	@keyframes blinkCursor {
		50% {
			border-right-color: transparent;
		}
	}

	@keyframes typeAndDelete {
		0%,
		10% {
			width: 0;
		}
		45%,
		55% {
			width: 14em;
		} /* adjust width based on content */
		90%,
		100% {
			width: 0;
		}
	}

	.terminal-loader {
		border: 0.1em solid #333;
		background-color: #1a1a1a;
		color: #0f0;
		font-family: 'Courier New', Courier, monospace;
		font-size: 1em;
		padding: 1.5em 1em;
		width: 34em;
		margin: 100px auto;
		box-shadow: 0 4px 8px rgba(0, 0, 0, 0.2);
		border-radius: 4px;
		position: relative;
		overflow: hidden;
		box-sizing: border-box;
	}

	.terminal-header {
		position: absolute;
		top: 0;
		left: 0;
		right: 0;
		height: 1.5em;
		background-color: #333;
		border-top-left-radius: 4px;
		border-top-right-radius: 4px;
		padding: 0 0.4em;
		box-sizing: border-box;
	}

	.terminal-controls {
		float: right;
	}

	.control {
		display: inline-block;
		width: 0.6em;
		height: 0.6em;
		margin-left: 0.4em;
		border-radius: 50%;
		background-color: #777;
	}

	.control.close {
		background-color: #e33;
	}

	.control.minimize {
		background-color: #ee0;
	}

	.control.maximize {
		background-color: #0b0;
	}

	.terminal-title {
		float: left;
		line-height: 1.5em;
		color: #eee;
	}

	.text {
		display: inline-block;
		white-space: nowrap;
		overflow: hidden;
		border-right: 0.2em solid green; /* Cursor */
		animation:
			typeAndDelete 6s steps(50) infinite,
			blinkCursor 1s step-end infinite alternate;
		margin-top: 1.5em;
	}
</style>

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

# Svelte Drag Drop

This component is designed to effortlessly showcase a dynamic list of items, primarily images, allowing users to easily reorder them via intuitive drag-and-drop functionality.

Utilizing this component is a breeze—simply set the 'items' prop, and you're good to go! 

## :rocket: Installation
You can install the `@kuiper/svelte-drag-drop` component from npm by running the following command:
```
$ npm install @kuiper/svelte-drag-drop
```

## Demo [https://svelte-drag-drop.vercel.app]

https://github.com/kofkuiper/svelte-drag-drop/assets/104291370/eed53dd0-fd17-48ae-ae3c-db2827b0bb96


## :fire: Usage
### Basic usage example
```ts
<script lang="ts">
	import { DragDrop } from '@kuiper/svelte-drag-drop';
	let items = [
		'https://images.unsplash.com/photo-1700730025710-58ff304c1c8b?crop=entropy&cs=tinysrgb&fit=max&fm=jpg&ixid=MnwxfDB8MXxyYW5kb218MHx8fHx8fHx8MTcwMTc4MTEyMA&ixlib=rb-4.0.3&q=80&w=1080',
        ...
	];
</script>


<DragDrop bind:items/>
```

### Handle events example

```ts
<script lang="ts">
	import { DragDrop } from '@kuiper/svelte-drag-drop';
	let items = [
		'https://images.unsplash.com/photo-1700730025710-58ff304c1c8b?crop=entropy&cs=tinysrgb&fit=max&fm=jpg&ixid=MnwxfDB8MXxyYW5kb218MHx8fHx8fHx8MTcwMTc4MTEyMA&ixlib=rb-4.0.3&q=80&w=1080',
        ...
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

```

## :tada: Props
- `items`: images list (required)
- (optional)
  - `onDragStart`: The user starts dragging an element or text selection.
  - `onDrag`: An element or text selection is being dragged (every 350ms).
  - `onDragEnd`: A drag operation is being ended (by releasing a mouse button or hitting the escape key).
  - `onDragEnter`: A dragged element or text selection enters a valid drop target.
  - `onDragOver`: An element or text selection is being dragged over a valid drop target (every 350ms).
  - `onDragLeave`: A dragged element or text selection leaves a valid drop target.
  - `onDrop`: An element is dropped on a valid drop target.

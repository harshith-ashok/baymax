<script lang="ts">
	import '../app.css';
	import favicon from '$lib/assets/favicon.svg';

	let { children } = $props();
</script>

<svelte:head>
	<link rel="icon" href={favicon} />
</svelte:head>

<div class="flex h-screen">
	<ul class="menu w-56 rounded-box bg-base-200">
		<li><a>Item 1</a></li>
		<li><a>Item 2</a></li>
		<li><a>Item 3</a></li>
	</ul>
	<div class="flex-1">
		{@render children?.()}
	</div>
</div>

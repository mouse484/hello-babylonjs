<script lang="ts" generics="T extends keyof typeof MeshBuilder">
	import { Mesh, MeshBuilder } from '@babylonjs/core';
	import { onMount } from 'svelte';

	export let type: T;
	export let options: Parameters<(typeof MeshBuilder)[T]>;

	onMount(() => {
		const builder = MeshBuilder[type] as (...options: unknown[]) => Mesh;
		builder(...options);
	});
</script>

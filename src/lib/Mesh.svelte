<script lang="ts" generics="T extends keyof typeof MeshBuilder">
	import { Mesh, MeshBuilder } from '@babylonjs/core';
	import { onMount } from 'svelte';

	export let type: T;
	export let options: Parameters<(typeof MeshBuilder)[T]>;
	export let exec: ((mesh: Mesh) => void) | null = null;

	onMount(() => {
		const builder = MeshBuilder[type] as (...options: unknown[]) => Mesh;
		const mesh = builder(...options);
		exec?.(mesh);
	});
</script>

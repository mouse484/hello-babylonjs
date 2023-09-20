<script lang="ts">
	import ArcRotateCamera from '$lib/ArcRotateCamera.svelte';
	import Audio from '$lib/Audio.svelte';
	import Babylon from '$lib/Babylon.svelte';
	import HemisphericLight from '$lib/HemisphericLight.svelte';
	import Mesh from '$lib/Mesh.svelte';
</script>

<Babylon let:scene let:canvas>
	<ArcRotateCamera
		{scene}
		{canvas}
		camera={{ alpha: -Math.PI / 2, beta: Math.PI / 2.5, radius: 15, target: [0, 0, 0] }}
	/>
	<HemisphericLight {scene} vector={[1, 1, 0]} />
	<Audio {scene} path="/audio/OnandOn.mp3" options={{ loop: true, autoplay: true, volume: 0.1 }} />
	<Mesh
		type="CreateBox"
		options={['box']}
		exec={(mesh) => {
			mesh.position.y = 0.5;
		}}
	/>
	<Mesh type="CreateGround" options={['ground', { width: 10, height: 10 }]} />
</Babylon>

<script lang="ts">
	const pages = Object.entries(import.meta.glob('./**/+page.svelte')).map(([name]) =>
		name.replace('/+page.svelte', '').slice(1)
	);
</script>

<ul>
	{#each pages as page}
		<li>
			<a href={page}>{page}</a>
		</li>
	{/each}
</ul>

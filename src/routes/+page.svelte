<script lang="ts">
	import Clock from '$lib/components/Clock.svelte';
	import { PUBLIC_COMMIT_SHA as version } from '$env/static/public';

	let time = $state<Date>(new Date());

	$effect(() => {
		const interval = setInterval(() => {
			time = new Date();
		}, 1000);

		return () => clearInterval(interval);
	});
</script>

<div class="clock-container">
	<Clock {time} />
	<div class="version">{version}</div>
</div>

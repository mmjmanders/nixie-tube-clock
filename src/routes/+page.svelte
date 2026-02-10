<script lang="ts">
	import Clock from '$lib/components/Clock.svelte';

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
</div>

<script lang="ts">
	const { time }: { time: Date } = $props();

	const [hourLeft, hourRight] = $derived(
		String(time.getHours()).padStart(2, '0').split('').map(Number)
	);
	const [minuteLeft, minuteRight] = $derived(
		String(time.getMinutes()).padStart(2, '0').split('').map(Number)
	);
</script>

<div class="clock">
	<div class="digit">
		{#await import(`../assets/Nixie ${hourLeft}.svg?raw`) then { default: svg }}
			{@html svg}
		{/await}
	</div>
	<div class="digit">
		{#await import(`../assets/Nixie ${hourRight}.svg?raw`) then { default: svg }}
			{@html svg}
		{/await}
	</div>
	<div class="digit">
		{#await import(`../assets/Nixie ${minuteLeft}.svg?raw`) then { default: svg }}
			{@html svg}
		{/await}
	</div>
	<div class="digit">
		{#await import(`../assets/Nixie ${minuteRight}.svg?raw`) then { default: svg }}
			{@html svg}
		{/await}
	</div>
</div>

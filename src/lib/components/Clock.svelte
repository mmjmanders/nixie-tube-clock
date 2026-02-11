<script lang="ts">
	const { time }: { time: Date } = $props();

	const [hours, minutes] = $derived(time.toLocaleTimeString().split(':'));
	const [hourLeft, hourRight] = $derived(hours.split('').map(Number));
	const [minuteLeft, minuteRight] = $derived(minutes.split('').map(Number));

	const hourLeftSvg = $derived(
		import(`../assets/Nixie ${hourLeft}.svg?raw`).then((m) => m.default)
	);
	const hourRightSvg = $derived(
		import(`../assets/Nixie ${hourRight}.svg?raw`).then((m) => m.default)
	);
	const minuteLeftSvg = $derived(
		import(`../assets/Nixie ${minuteLeft}.svg?raw`).then((m) => m.default)
	);
	const minuteRightSvg = $derived(
		import(`../assets/Nixie ${minuteRight}.svg?raw`).then((m) => m.default)
	);
</script>

<div class="clock">
	<div class="digit">
		{#await hourLeftSvg then svg}
			{@html svg}
		{/await}
	</div>
	<div class="digit">
		{#await hourRightSvg then svg}
			{@html svg}
		{/await}
	</div>
	<div class="digit">
		{#await minuteLeftSvg then svg}
			{@html svg}
		{/await}
	</div>
	<div class="digit">
		{#await minuteRightSvg then svg}
			{@html svg}
		{/await}
	</div>
</div>

<script lang="ts">
	const { time }: { time: Date } = $props();

	const [hours, minutes] = $derived(time.toLocaleTimeString().split(':'));
	const [hourLeft, hourRight] = $derived(hours.split('').map(Number));
	const [minuteLeft, minuteRight] = $derived(minutes.split('').map(Number));
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

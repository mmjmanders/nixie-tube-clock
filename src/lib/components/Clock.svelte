<script lang="ts">
	const getNixieSvg = (num: number): string => {
		return new URL(`../assets/Nixie ${num}.svg`, import.meta.url).href;
	};

	const { time }: { time: Date } = $props();

	const [hours, minutes] = $derived(time.toLocaleTimeString().split(':'));
	const [hourLeft, hourRight] = $derived(hours.split('').map(Number));
	const [minuteLeft, minuteRight] = $derived(minutes.split('').map(Number));
</script>

<div class="clock">
	<div class="digit">
		<img alt={hourLeft.toString()} src={getNixieSvg(hourLeft)} />
	</div>
	<div class="digit">
		<img alt={hourRight.toString()} src={getNixieSvg(hourRight)} />
	</div>
	<div class="digit">
		<img alt={minuteLeft.toString()} src={getNixieSvg(minuteLeft)} />
	</div>
	<div class="digit">
		<img alt={minuteRight.toString()} src={getNixieSvg(minuteRight)} />
	</div>
</div>

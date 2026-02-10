<script lang="ts">
	import nixie0 from '$lib/assets/Nixie 0.svg?raw';
	import nixie1 from '$lib/assets/Nixie 1.svg?raw';
	import nixie2 from '$lib/assets/Nixie 2.svg?raw';
	import nixie3 from '$lib/assets/Nixie 3.svg?raw';
	import nixie4 from '$lib/assets/Nixie 4.svg?raw';
	import nixie5 from '$lib/assets/Nixie 5.svg?raw';
	import nixie6 from '$lib/assets/Nixie 6.svg?raw';
	import nixie7 from '$lib/assets/Nixie 7.svg?raw';
	import nixie8 from '$lib/assets/Nixie 8.svg?raw';
	import nixie9 from '$lib/assets/Nixie 9.svg?raw';

	let time = $state<Date>(new Date());

	$effect(() => {
		const interval = setInterval(() => {
			time = new Date();
		}, 1000);

		return () => clearInterval(interval);
	});

	const [hours, minutes] = $derived(time.toLocaleTimeString().split(':'));
	const [hourLeft, hourRight] = $derived(hours.split('').map(Number));
	const [minuteLeft, minuteRight] = $derived(minutes.split('').map(Number));

	const nixies = [nixie0, nixie1, nixie2, nixie3, nixie4, nixie5, nixie6, nixie7, nixie8, nixie9];
</script>

<div class="clock">
	<div class="digit">{@html nixies[hourLeft]}</div>
	<div class="digit">{@html nixies[hourRight]}</div>
	<div class="digit">{@html nixies[minuteLeft]}</div>
	<div class="digit">{@html nixies[minuteRight]}</div>
</div>

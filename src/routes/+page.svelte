<script lang="ts">
	import nixie0 from '$lib/assets/Nixie 0.svg';
	import nixie1 from '$lib/assets/Nixie 1.svg';
	import nixie2 from '$lib/assets/Nixie 2.svg';
	import nixie3 from '$lib/assets/Nixie 3.svg';
	import nixie4 from '$lib/assets/Nixie 4.svg';
	import nixie5 from '$lib/assets/Nixie 5.svg';
	import nixie6 from '$lib/assets/Nixie 6.svg';
	import nixie7 from '$lib/assets/Nixie 7.svg';
	import nixie8 from '$lib/assets/Nixie 8.svg';
	import nixie9 from '$lib/assets/Nixie 9.svg';

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
	<div class="digit"><img alt={hourLeft.toString()} src={nixies[hourLeft]} /></div>
	<div class="digit"><img alt={hourRight.toString()} src={nixies[hourRight]} /></div>
	<div class="digit"><img alt={minuteLeft.toString()} src={nixies[minuteLeft]} /></div>
	<div class="digit"><img alt={minuteRight.toString()} src={nixies[minuteRight]} /></div>
</div>

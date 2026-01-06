<script>
	import { onMount } from 'svelte';

	let currentTime = new Date();
	let timeString = '';

	function updateTime() {
		currentTime = new Date();
		const hours = String(currentTime.getHours()).padStart(2, '0');
		const minutes = String(currentTime.getMinutes()).padStart(2, '0');
		const seconds = String(currentTime.getSeconds()).padStart(2, '0');
		timeString = `${hours}:${minutes}:${seconds}`;
	}

	onMount(() => {
		updateTime();
		const interval = setInterval(updateTime, 1000);
		return () => clearInterval(interval);
	});
</script>

<div class="card-base p-4 text-center">
	<div class="text-sm text-neutral-400 mb-2 transition">Current Time</div>
	<div class="font-mono text-3xl font-bold text-[var(--primary)] transition">{timeString}</div>
	<div class="text-xs text-neutral-400 mt-2 transition">
		{currentTime.toLocaleDateString('id-ID', {
			weekday: 'long',
			year: 'numeric',
			month: 'long',
			day: 'numeric'
		})}
	</div>
</div>

<style>
</style>

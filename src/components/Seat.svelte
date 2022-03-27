<script lang="ts">
	import { createEventDispatcher } from 'svelte';
	import type { SeatStatus } from '$lib/seat.types';

	const dispatch = createEventDispatcher();

	export let id = '';
	export let status: SeatStatus = 'available';
	export let size = 16;
	export let label: string | undefined = '';

	const getSeatColor = (status: SeatStatus) => {
		if (status === 'occupied') {
			return '#ffffff';
		}

		if (status === 'selected') {
			return '#6feaf6';
		}

		if (status === 'available') {
			return '#444451';
		}
	};

	const onClick = () => {
		dispatch('click', { id, status });
	};
</script>

<div
	style="background-color: {getSeatColor(status)}; width: {size}px; height: {size}px;"
	class="rounded-t-full cursor-pointer transition-all hover:scale-110 flex justify-center items-center"
	on:click={onClick}
>
	{#if label}
		<span>{label}</span>
	{/if}
</div>

<style>
</style>

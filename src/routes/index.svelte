<script lang="ts" context="module">
</script>

<script lang="ts">
	import type { SeatStatus } from '$lib/seat.types';
	import Seat from '../components/Seat.svelte';

	const movies = [
		{ name: 'Avengers: Endgame ($10)', price: 10 },
		{ name: 'Joker ($12)', price: 12 },
		{ name: 'Toy Story 4 ($8)', price: 8 },
		{ name: 'The Lion King ($9)', price: 9 }
	];
	let selectedMovie = movies[0];
	let seatPrice = 10;
	let occupiedSeats: string[] = ['3', '4', '21', '22', '23', '24', '35', '47'];
	let selectedSeats: string[] = [];
	$: selectedSeatsCount = selectedSeats.length;
	$: totalPrice = selectedSeats.length * seatPrice;
	$: {
		console.log(selectedSeats);
	}

	const onMovieChanged = (e: any) => (seatPrice = e.target.value);

	const getSeatStatus = (
		id: string,
		occupiedSeats: string[],
		selectedSeats: string[]
	): SeatStatus => {
		const isOccupied = occupiedSeats.includes(id);
		if (isOccupied) {
			return 'occupied';
		}

		const isSelected = selectedSeats.includes(id);
		if (isSelected) {
			return 'selected';
		}

		return 'available';
	};

	const onSeatClicked = (event: CustomEvent) => {
		const { id, status } = event.detail;
		if (status === 'occupied') {
			return;
		}

		if (status === 'selected') {
			selectedSeats = selectedSeats.filter((seatId) => seatId !== id);
			return;
		}

		// Seat is available
		selectedSeats = [...selectedSeats, id];
	};
</script>

<div
	style="background-color: #242333; height: 100vh;"
	class="text-white flex flex-col flex-nowrap justify-center items-center"
>
	<div class="mb-4 flex items-center">
		<p class="mr-4">Pick a movie:</p>

		<select
			class="px-2 py-1 rounded-md text-black"
			value={selectedMovie.price}
			on:change={onMovieChanged}
		>
			{#each movies as item}
				<option value={item.price}>{item.name}</option>
			{/each}
		</select>
	</div>

	<div
		class="my-4 px-8 py-1 rounded-md w-min flex gap-8 justify-center"
		style="background-color: rgba(0, 0, 0, 0.1);"
	>
		<div class="flex items-center gap-2">
			<Seat status="available" /> <span>Available</span>
		</div>

		<div class="flex items-center gap-2">
			<Seat status="selected" /> <span>Selected</span>
		</div>

		<div class="flex items-center gap-2">
			<Seat status="occupied" /> <span>Occupied</span>
		</div>
	</div>

	<div class="w-min" style="perspective: 1000px;">
		<div
			class="w-64 aspect-video bg-white shadow-lg shadow-white"
			style="transform: rotateX(-60deg); "
		/>
	</div>

	<div class="flex flex-row flex-nowrap justify-center">
		<div class="mr-4 grid grid-cols-2 gap-2">
			<Seat
				id="1"
				status={getSeatStatus('1', occupiedSeats, selectedSeats)}
				on:click={onSeatClicked}
			/>
			<Seat
				id="2"
				status={getSeatStatus('2', occupiedSeats, selectedSeats)}
				on:click={onSeatClicked}
			/>
			<Seat
				id="3"
				status={getSeatStatus('3', occupiedSeats, selectedSeats)}
				on:click={onSeatClicked}
			/>
			<Seat
				id="4"
				status={getSeatStatus('4', occupiedSeats, selectedSeats)}
				on:click={onSeatClicked}
			/>
			<Seat
				id="5"
				status={getSeatStatus('5', occupiedSeats, selectedSeats)}
				on:click={onSeatClicked}
			/>
			<Seat
				id="6"
				status={getSeatStatus('6', occupiedSeats, selectedSeats)}
				on:click={onSeatClicked}
			/>
			<Seat
				id="7"
				status={getSeatStatus('7', occupiedSeats, selectedSeats)}
				on:click={onSeatClicked}
			/>
			<Seat
				id="8"
				status={getSeatStatus('8', occupiedSeats, selectedSeats)}
				on:click={onSeatClicked}
			/>
			<Seat
				id="9"
				status={getSeatStatus('9', occupiedSeats, selectedSeats)}
				on:click={onSeatClicked}
			/>
			<Seat
				id="10"
				status={getSeatStatus('10', occupiedSeats, selectedSeats)}
				on:click={onSeatClicked}
			/>
			<Seat
				id="11"
				status={getSeatStatus('11', occupiedSeats, selectedSeats)}
				on:click={onSeatClicked}
			/>
			<Seat
				id="12"
				status={getSeatStatus('12', occupiedSeats, selectedSeats)}
				on:click={onSeatClicked}
			/>
		</div>

		<div class="grid grid-cols-4 gap-2">
			<Seat
				id="13"
				status={getSeatStatus('13', occupiedSeats, selectedSeats)}
				on:click={onSeatClicked}
			/>
			<Seat
				id="14"
				status={getSeatStatus('14', occupiedSeats, selectedSeats)}
				on:click={onSeatClicked}
			/>
			<Seat
				id="15"
				status={getSeatStatus('15', occupiedSeats, selectedSeats)}
				on:click={onSeatClicked}
			/>
			<Seat
				id="16"
				status={getSeatStatus('16', occupiedSeats, selectedSeats)}
				on:click={onSeatClicked}
			/>
			<Seat
				id="17"
				status={getSeatStatus('17', occupiedSeats, selectedSeats)}
				on:click={onSeatClicked}
			/>
			<Seat
				id="18"
				status={getSeatStatus('18', occupiedSeats, selectedSeats)}
				on:click={onSeatClicked}
			/>
			<Seat
				id="19"
				status={getSeatStatus('19', occupiedSeats, selectedSeats)}
				on:click={onSeatClicked}
			/>
			<Seat
				id="20"
				status={getSeatStatus('20', occupiedSeats, selectedSeats)}
				on:click={onSeatClicked}
			/>
			<Seat
				id="21"
				status={getSeatStatus('21', occupiedSeats, selectedSeats)}
				on:click={onSeatClicked}
			/>
			<Seat
				id="22"
				status={getSeatStatus('22', occupiedSeats, selectedSeats)}
				on:click={onSeatClicked}
			/>
			<Seat
				id="23"
				status={getSeatStatus('23', occupiedSeats, selectedSeats)}
				on:click={onSeatClicked}
			/>
			<Seat
				id="24"
				status={getSeatStatus('24', occupiedSeats, selectedSeats)}
				on:click={onSeatClicked}
			/>
			<Seat
				id="25"
				status={getSeatStatus('25', occupiedSeats, selectedSeats)}
				on:click={onSeatClicked}
			/>
			<Seat
				id="26"
				status={getSeatStatus('26', occupiedSeats, selectedSeats)}
				on:click={onSeatClicked}
			/>
			<Seat
				id="27"
				status={getSeatStatus('27', occupiedSeats, selectedSeats)}
				on:click={onSeatClicked}
			/>
			<Seat
				id="28"
				status={getSeatStatus('28', occupiedSeats, selectedSeats)}
				on:click={onSeatClicked}
			/>
			<Seat
				id="29"
				status={getSeatStatus('29', occupiedSeats, selectedSeats)}
				on:click={onSeatClicked}
			/>
			<Seat
				id="30"
				status={getSeatStatus('30', occupiedSeats, selectedSeats)}
				on:click={onSeatClicked}
			/>
			<Seat
				id="31"
				status={getSeatStatus('31', occupiedSeats, selectedSeats)}
				on:click={onSeatClicked}
			/>
			<Seat
				id="32"
				status={getSeatStatus('32', occupiedSeats, selectedSeats)}
				on:click={onSeatClicked}
			/>
			<Seat
				id="33"
				status={getSeatStatus('33', occupiedSeats, selectedSeats)}
				on:click={onSeatClicked}
			/>
			<Seat
				id="34"
				status={getSeatStatus('34', occupiedSeats, selectedSeats)}
				on:click={onSeatClicked}
			/>
			<Seat
				id="35"
				status={getSeatStatus('35', occupiedSeats, selectedSeats)}
				on:click={onSeatClicked}
			/>
			<Seat
				id="36"
				status={getSeatStatus('36', occupiedSeats, selectedSeats)}
				on:click={onSeatClicked}
			/>
		</div>

		<div class="ml-4 grid grid-cols-2 gap-2">
			<Seat
				id="37"
				status={getSeatStatus('37', occupiedSeats, selectedSeats)}
				on:click={onSeatClicked}
			/>
			<Seat
				id="38"
				status={getSeatStatus('38', occupiedSeats, selectedSeats)}
				on:click={onSeatClicked}
			/>
			<Seat
				id="39"
				status={getSeatStatus('39', occupiedSeats, selectedSeats)}
				on:click={onSeatClicked}
			/>
			<Seat
				id="40"
				status={getSeatStatus('40', occupiedSeats, selectedSeats)}
				on:click={onSeatClicked}
			/>
			<Seat
				id="41"
				status={getSeatStatus('41', occupiedSeats, selectedSeats)}
				on:click={onSeatClicked}
			/>
			<Seat
				id="42"
				status={getSeatStatus('42', occupiedSeats, selectedSeats)}
				on:click={onSeatClicked}
			/>
			<Seat
				id="43"
				status={getSeatStatus('43', occupiedSeats, selectedSeats)}
				on:click={onSeatClicked}
			/>
			<Seat
				id="44"
				status={getSeatStatus('44', occupiedSeats, selectedSeats)}
				on:click={onSeatClicked}
			/>
			<Seat
				id="45"
				status={getSeatStatus('45', occupiedSeats, selectedSeats)}
				on:click={onSeatClicked}
			/>
			<Seat
				id="46"
				status={getSeatStatus('46', occupiedSeats, selectedSeats)}
				on:click={onSeatClicked}
			/>
			<Seat
				id="47"
				status={getSeatStatus('47', occupiedSeats, selectedSeats)}
				on:click={onSeatClicked}
			/>
			<Seat
				id="48"
				status={getSeatStatus('48', occupiedSeats, selectedSeats)}
				on:click={onSeatClicked}
			/>
		</div>
	</div>

	<p class="mt-16 text-center text-lg">
		You have selected
		<span style="color: #6feaf6;">{selectedSeatsCount}</span>
		seats for a price of $<span style="color: #6feaf6;">{totalPrice}</span>
	</p>
</div>

<style>
</style>

<script>
import { each } from 'svelte/internal';
import AddPlayer from './components/AddPlayer.svelte';
	import Navbar from './components/Navbar.svelte'
	import Player from './components/Player.svelte'

	let players = [
		{
			name: "John Doe",
			points: "53"
		},
		{
			name: "Sara Fier",
			points: "73"
		},
		{
			name: "Williams Smith",
			points: "48"
		},
	]

	const addPlayer = e => {
		const newPlayer = e.detail;
		if(newPlayer.name === "") alert("Name can not be empty")
		else if (players.filter(player => player.name === newPlayer.name).length > 0) alert("Player already exists")
		else players = [...players, newPlayer]
	}

	const removePlayer = e => {
		players = players.filter(player => player.name !== e.detail)
	}

</script>

<Navbar/>
<div class="container">
	<AddPlayer on:addplayer={addPlayer} />
	<div class="grid-3 px-2">
		{#if players.length > 0}
				{#each players as player}
					<Player name={player.name} points={player.points} on:removePlayer={removePlayer} />
				{/each}
				{:else}
					No players added
				{/if}
	</div>
</div>

<style>

</style>
<script>
	import { createEventDispatcher } from "svelte";
	const dispatch = createEventDispatcher()

  	export let name;
		export let points;
		let show = false
  
	const addPoint = () => points++
	const removePoint = () => points--
	const toggleShow = () => show = !show

	const handleDelete =() => dispatch('removePlayer', name)
</script>

<div class="col-4">
		<div class="card">
			<h1>{name}</h1>
			<h3>Score: {points}</h3>
			<span class="btn btn-small" on:click="{toggleShow}">{#if show} - {:else} + {/if}</span>
			<span class="btn btn-small btn-danger" on:click="{handleDelete}">X</span>
			{#if show}
				<input type="number" bind:value="{points}">
				<div class="btn" on:click="{addPoint}">+1</div>
				<div class="btn btn-dark" on:click="{removePoint}">-1</div>
			{/if}
		</div>
	</div>
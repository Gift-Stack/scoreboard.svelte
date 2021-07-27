<script>
  import { createEventDispatcher } from 'svelte'

  const dispatch = createEventDispatcher()

  let player = {
    name: "",
    points: 0
  }

  const handleAddPlayer = e => {
    e.preventDefault()
    dispatch("addplayer", player)
    player = {
      name: "",
      points: 0
    }
  }
</script>

<form class="grid-3" on:submit="{handleAddPlayer}">
  <input type="text" name="name" placeholder="Player Name" bind:value="{player.name}">
  <input type="number" name="points" placeholder="Player Points" bind:value="{player.points}">
  <input type="submit" value="Add Player" class="btn btn-primary" />
</form>
<script>
import GameCard from "./GameCard.svelte";
import Cell from "@smui/layout-grid/src/Cell.svelte";
export let  games;
</script>
{#each games as game, i}
<div class="card">
    <GameCard  currentgame={game} />
</div>
{/each}
<style>
    .card {
padding-bottom: 20px;
    }
</style>
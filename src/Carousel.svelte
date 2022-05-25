<script>
    import Icon from "@iconify/svelte";
    import Carousel from "svelte-carousel";
    import GameCard from "./GameCard.svelte";
    import { Cell } from "@smui/layout-grid";
    export let games;
</script>

<Carousel
    particlesToShow={3}
    particlesToScroll={1}
    let:showPrevPage
    let:showNextPage
>
    <div
        slot="prev"
        on:click={showPrevPage}
        class="custom-arrow custom-arrow-prev"
    >
        <Icon
            icon="akar-icons:arrow-right-thick"
            class="arrows"
            color="#06df45"
            height={80}
            rotate={2}
        />
    </div>
    {#each games as game, i}
        <Cell span={4}>
            <GameCard currentgame={game} />
        </Cell>
    {/each}
    <div
        slot="next"
        on:click={showNextPage}
        class="custom-arrow custom-arrow-prev"
    >
        <Icon
            icon="akar-icons:arrow-right-thick"
            class="arrows"
            color="#06df45"
            height={80}
        />
    </div>
</Carousel>

<style>
    :global(.arrows) {

        padding-top: 25vh;
        margin: auto;
        cursor: pointer;
    }
</style>

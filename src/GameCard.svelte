<script>
    import Button, { Label } from "@smui/button";
    export let currentgame;
</script>

<div class="game-card">
    <h2>{currentgame.Name}</h2>
    <div class="image-temp">
        <img
            src={currentgame.Img}
            alt={`arcage image for ${currentgame.Name}`}
        />
    </div>
    <hr />
    <div class="card-content">
        <p>{currentgame.Description}</p>

        <Button
            href={currentgame.PlayLink}
            touch
            variant="raised"
            class="smui-button"
        >
            <Label>Play Now</Label>
        </Button>
        <br />
        <Button
            color="primary"
            href={currentgame.SourceCode}
            touch
            target="_blank"
        >
            <Label>View Source Code</Label>
        </Button>
    </div>
    <!-- <div class="deploy">
        <div class="deploy-thinky">
            <img src="images/thinky.png" alt="thinky" />
        </div>
        <p>Deploy to Fathym</p>
    </div> -->
</div>

<style>
    /*GAME CARDS*/
    :global(.smui-button) {
        margin: 10px;
        padding: 20px;
    }
    .game-card {
        border-style: solid;
        border-color: #00ffff;
        margin: 10px;
        border-radius: 25px;
        background-color: #221d36;
        height: 70vh;
    }
    .game-card h2 {
        text-align: center;
        color: #ff298e;
        font-family: "Press Start 2p";
        padding-top: 5px;
    }
    .card-content {
        height: 10vh;
        display: flex;
        flex-direction: column;
        justify-content: center;
        align-items: center;
        align-content: center;
        margin-left: 10px;
        margin-right: 10px;
    }
    .image-temp {
        display: flex;
        flex-direction: column;
        justify-content: center;
        align-items: center;
        align-content: center;
        width: 100%;
    }

    .image-temp img {
        max-width: 50%;
        border-radius: 25px;
    }
    .game-card p {
        font-family: "Press Start 2p";
        text-align: center;
        font-size: 20px;
        padding-left: 30px;
        padding-right: 30px;
        line-height: 30px;
    }

    hr {
		margin: 50px;
        padding:10px;
		border: 0;
		border-top: 1px solid #ff298e;
	}

    @media (max-width: 800px) {
        /* GAME CARD*/
        .image-temp img {
            padding-top: 5px;
        }
        :global(.smui-button) {
            padding: 5px;
        }
        .game-card {
        height: 80vh;
        }
        .game-card p {
        font-family: "Press Start 2p";
        text-align: center;
        font-size: 15px;
        padding-left: 10px;
        padding-right: 10px;
        line-height: 20px;
    }
    }
</style>

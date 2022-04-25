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
    <hr/>
    <div class="card-content">
        <p>{currentgame.Description}</p>
        <!-- <div class="deploy">
        <div class="deploy-thinky">
            <img src="images/thinky.png" alt="thinky" />
        </div>
        <p>Deploy to Fathym</p>
    </div> -->
    </div>
    <div class="card-buttons">
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
</div>

<style>
    /*GAME CARDS*/
    .game-card {
        border-style: solid;
        border-color: #00ffff;
        margin: 10px;
        border-radius: 25px;
        background-color: #221d36;
        overflow: hidden;
    }
    .game-card h2 {
        text-align: center;
        color: #ff298e;
        font-size: 20px;
        font-family: "Press Start 2p";
        padding-top: 5px;
    }
    .card-content {
        display: flex;
        height: 15vh;
        flex-direction: column;
        justify-content: center;
        align-items: center;
        align-content: center;
        margin-left: 3px;
        margin-right: 3px;
        overflow: hidden;
    }
    .card-buttons {
        display: flex;
        flex-direction: column;
        justify-content: center;
        align-items: center;
        align-content: center;
        padding-bottom: 20px;
    }
    .image-temp {
        display: flex;
        flex-direction: column;
        justify-content: center;
        align-items: center;
        align-content: center;
        width: 100%;
        padding-bottom: 20px;
    }

    .image-temp img {
        max-width: 50%;
        border-radius: 25px;
    }
    .game-card p {
        font-family: "Press Start 2p";
        text-align: center;
        font-size: 15px;
        padding-left: 15px;
        padding-right: 15px;
        line-height: 20px;
    }

    hr {
        border: 0;
        width:70%;
        padding-top: 10px;
        border-top: 3px solid #ff298e;
    }

    @media (max-width: 800px) {
        /* GAME CARD*/
        .image-temp img {
            padding-top: 5px;
            padding-bottom: 0px;
        }
        :global(.smui-button) {
            padding: 5px;
        }
        .game-card {
            height: 75vh;
        }
        .game-card p {
            font-family: "Press Start 2p";
            text-align: center;
            font-size: 15px;
            padding-left: 10px;
            padding-right: 10px;
            line-height: 20px;
        }
        hr{
            display: none;
        }
    }
</style>

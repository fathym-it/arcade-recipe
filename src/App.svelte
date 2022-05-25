<script lang="ts">
	import Button, { Label } from "@smui/button";
	import LayoutGrid, { Cell } from "@smui/layout-grid";
	import { onMount } from "svelte";
	import Carousel from "./Carousel.svelte";
	import MobileCarousel from "./MobileCarousel.svelte";

	export class Game {
		public Description: string;

		public Name: string;

		public PlayLink: string;

		public SourceCode: string;

		public Img: string;
	}
	let mobile = false;
	onMount(() => {
		if (window.screen.width < 600) {
			mobile = true;
		}
	});
	export let games: Game[] = [
		{
			Name: "2048",
			Description: `A simple, fast numbers game. Can you get it to read 2048?`,
			PlayLink: "https://arcade.fathym.com/2048",
			SourceCode: "https://github.com/fathym-arcade/2048",
			Img: "images/2048.png",
		},
		{
			Name: "Hextris",
			Description: "Inspired by Tetris. How far can you go?",
			PlayLink: "https://arcade.fathym.com/hextris",
			SourceCode: "https://github.com/fathym-arcade/hextris",
			Img: "images/hextris.png",
		},
		{
			Name: "Clumsy Bird",
			Description: `Flap your wings through the obstacles...If you can!`,
			PlayLink: "https://arcade.fathym.com/clumsy-bird",
			SourceCode: "https://github.com/fathym-arcade/clumsy-bird",
			Img: "images/clumsybird.png",
		},
		{
			Name: "Pacman Canvas",
			Description: "Eat those dots, dodge ghosts, have fun!",
			PlayLink: "https://arcade.fathym.com/pacman-canvas",
			SourceCode: "https://github.com/fathym-arcade/pacman-canvas",
			Img: "images/pacman.png",
		},
		{
			Name: "Astray",
			Description: "Don't be led astray by this fun-styled maze game.",
			PlayLink: "https://arcade.fathym.com/astray",
			SourceCode: "https://github.com/fathym-arcade/astray",
			Img: "images/astray.png",
		},
	];

	var pattern = [
		"ArrowUp",
		"ArrowUp",
		"ArrowDown",
		"ArrowDown",
		"ArrowLeft",
		"ArrowRight",
		"ArrowLeft",
		"ArrowRight",
		"b",
		"a",
	];
	let current = 0;
	var keyHandler = function (event) {
		// If the key isn't in the pattern, or isn't the current key in the pattern, reset
		if (pattern.indexOf(event.key) < 0 || event.key !== pattern[current]) {
			current = 0;
			return;
		}

		// Update how much of the pattern is complete
		current++;

		// If complete, alert and reset
		if (pattern.length === current) {
			current = 0;
			var audio = new Audio("music/NeonDreams.mp3");
			audio.play();
		}
	};
	document.addEventListener("keydown", keyHandler, false);
</script>

<body>
	<link
		href="https://fonts.googleapis.com/css2?family=Syne:wght@400;700&display=swap"
		rel="stylesheet"
	/>
	<link
		href="https://fonts.googleapis.com/css?family=Press Start 2P"
		rel="stylesheet"
	/>
	<link rel="preconnect" href="https://fonts.googleapis.com" />
	<link rel="preconnect" href="https://fonts.gstatic.com" />

	<section class="hero">
		<div class="header">
			<div class="imageContainer">
				<img
					class="headImage"
					src="https://www.fathym.com/assets/images/fathym-arcade.png"
					alt="Fathym Arcade"
				/>
			</div>
		</div>
		{#if mobile}
			<MobileCarousel {games} />
		{:else}
			<Carousel {games} />
		{/if}
	</section>

	<div class="copy">
		<div class="copy-content">
			<h1>Welcome to the Fathym Arcade</h1>
			<h3>
				At Fathym, we're serious about building businesses. <br /> We're
				focused on cloud-hosting as well as bringing powerful products
				to the world. <br />
				We're earnestly pushing toward a better and brighter technological
				future.
			</h3>
			<h2>But we also know how to get down.</h2>
			<img
				class="office"
				src="images/officeDance.gif"
				alt="dancing gif"
			/>
			<p>
				That's part of the reason we brought you the Fathym Arcade. To
				be able to go and play a bunch of fun, entertaining games for
				free right on our website. From there, we give developers an
				easy way to add those games to their dashboard within our new
				<a
					href="https://www.fathym.com/blog/articles/2022/march/2022-03-02-introducing-fathyms-social-ui"
					target="_blank">Social UI</a
				>.
			</p>
			<p>
				Besides being fun, the Fathym Arcade is a perfect way for us to
				show off our micro frontends architecture.
			</p>
			<Button
				href="https://www.fathym.com/"
				touch
				variant="raised"
				color="secondary"
				class="smui-button"
				target="_blank"
			>
				<Label>Get started for free</Label>
			</Button>
			<div>
				<h1>What are micro frontends?</h1>
				<div class="micro-frontends">
					<LayoutGrid>
						<Cell span={6}>
							<div class="micro-cell">
								<p>
									Simply, it's the breaking down of the
									frontend into individual, autonomous,
									smaller frontends.
								</p>
							</div>
						</Cell>
						<Cell span={6}>
							<div class="micro-img">
								<div class="img-overlay-wrap">
									<img
										class="im"
										src="images/routes.png"
										alt="routes example"
									/>
								</div>
							</div>
						</Cell>
						<Cell span={6}>
							<div class="micro-img">
								<div class="img-overlay-wrap">
									<img
										class="im"
										src="images/npmgit.png"
										alt="github and npm logos"
									/>
								</div>
							</div>
						</Cell>
						<Cell span={6}>
							<div class="micro-cell">
								<p>
									We build micro frontends using code
									repositories, specifically GitHub and NPM.
									Because these games are open-source, with
									their code stashed in open repos, we were
									able to plug and play.
								</p>
							</div>
						</Cell>
					</LayoutGrid>
				</div>

				<div class="invite">
					<p>
						In that way, we're utilizing no code and low code to
						<a
							href="https://www.fathym.com/blog/articles/2022/february/2022-02-23-flashup-use-case-redwood-crystals"
							target="_blank">flashup a website</a
						> in minutes rather than days, weeks or months.
					</p>
					<p>
						<strong>We're inviting you</strong> not only kick off
						your own arcade, with whichever games you like - you're
						not limited to what we have here - and you can do it for
						free by
						<a
							href="https://auth.fathym.com/fathymcloudprd.onmicrosoft.com/oauth2/v2.0/authorize?p=b2c_1_sign_up_sign_in&client_id=98f014f1-2547-4bcc-a583-3edc8f1190f2&redirect_uri=https%3A%2F%2Fwww.fathym.com%2F.oauth%2FB2C_1_SIGN_UP_SIGN_IN&response_type=id_token&scope=openid%20profile&response_mode=form_post&nonce=637834734966522963.MDA2ZDYxOTItZGRlZC00ZThlLTljMDQtZWI2NjJjMGMwNGJkZGVlZDJhZTUtMzkwYy00YzRkLWFhM2EtYTg2MzNlOTg0ZTQ3&state=CfDJ8BT8DPlcRT5GtKCFsQK09aEmVzIY8-N_F9FXgI_B_52lEKWZIJUUEUoGJQtl6s4sxQkHzzjwjm3d0L8hMNfXrPXsDdzjkwMAmHjTYB0i7N-PdtaxNq02TLWnbQ9u5uj7KQM8WP5OQWqBfLn4SflkflbkWTICnNOjVqJONWlEnPL527zeJ7fkO7nh_V011DMjuAcmXkuIuwpsr2nTCeHBG_BzDncz5sGitKDUriHhK2f3Z-RY2lEoFzAeaq7KPoCa8hlfGgCAWF35YU8aFdb_mHCF-77QGxM2ei3fl7OQ2_jrsYNwNZY7vsSKwfGjvZHhUyfwEfsCuECJ_9VEjMnaduw&x-client-SKU=ID_NETSTANDARD2_0&x-client-ver=6.11.1.0"
							target="_blank">signing up</a
						> for free to Fathym today.
					</p>
				</div>
				<Button
					href="https://www.fathym.com/"
					touch
					variant="raised"
					color="secondary"
					target="_blank"
				>
					<Label>Get started for free</Label>
				</Button>
			</div>
		</div>
		<div class="copy-content">
			<div class="thank">
				<h1>Thank you to all the content creators!</h1>

				<h2>
					Star any of the source code repos of the games you love.
				</h2>

				<p>
					Big thanks to <a
						href="https://superdevresources.com/open-source-html5-games/"
						target="_blank">Kanishk Kunal</a
					>
					for curating a list of games that we were able to bring into
					the Fathym Arcade to kick us off.
				</p>
			</div>
		</div>
	</div>

	<div class="footer">
		<hr />
		<div class="footer-logo">
			<img src="images/logo.svg" alt="fathym logo" />
		</div>
		<div>Copyright 2022 Fathym. All rights reserved</div>
	</div>
</body>

<style>
	:global(body) {
		/* this will apply to <body> */
		margin: 0;
		padding: 0;
		background-color: #030e16;
		color: white;
	}
	:root {
		--mdc-theme-primary: #ff298e;
		--mdc-theme-secondary: #00ffff;
	}
	.hero {
		background-image: url("data:image/svg+xml,%3csvg xmlns='http://www.w3.org/2000/svg' version='1.1' xmlns:xlink='http://www.w3.org/1999/xlink' xmlns:svgjs='http://svgjs.com/svgjs' width='1440' height='578' preserveAspectRatio='none' viewBox='0 0 1440 578'%3e%3cg mask='url(%26quot%3b%23SvgjsMask1946%26quot%3b)' fill='none'%3e%3crect width='1440' height='578' x='0' y='0' fill='url(%23SvgjsLinearGradient1947)'%3e%3c/rect%3e%3cpath d='M1440 0L951.24 0L1440 205.77z' fill='rgba(255%2c 255%2c 255%2c .1)'%3e%3c/path%3e%3cpath d='M951.24 0L1440 205.77L1440 337.67L870.06 0z' fill='rgba(255%2c 255%2c 255%2c .075)'%3e%3c/path%3e%3cpath d='M870.06 0L1440 337.67L1440 474.03000000000003L532.31 0z' fill='rgba(255%2c 255%2c 255%2c .05)'%3e%3c/path%3e%3cpath d='M532.31 0L1440 474.03000000000003L1440 514.87L468.75999999999993 0z' fill='rgba(255%2c 255%2c 255%2c .025)'%3e%3c/path%3e%3cpath d='M0 578L343.39 578L0 530.51z' fill='rgba(0%2c 0%2c 0%2c .1)'%3e%3c/path%3e%3cpath d='M0 530.51L343.39 578L876.35 578L0 428.09z' fill='rgba(0%2c 0%2c 0%2c .075)'%3e%3c/path%3e%3cpath d='M0 428.09000000000003L876.35 578L1224.85 578L0 348.27000000000004z' fill='rgba(0%2c 0%2c 0%2c .05)'%3e%3c/path%3e%3cpath d='M0 348.27L1224.85 578L1292.6299999999999 578L0 252.45999999999998z' fill='rgba(0%2c 0%2c 0%2c .025)'%3e%3c/path%3e%3c/g%3e%3cdefs%3e%3cmask id='SvgjsMask1946'%3e%3crect width='1440' height='578' fill='white'%3e%3c/rect%3e%3c/mask%3e%3clinearGradient x1='14.97%25' y1='137.28%25' x2='85.03%25' y2='-37.28%25' gradientUnits='userSpaceOnUse' id='SvgjsLinearGradient1947'%3e%3cstop stop-color='%230e2a47' offset='0'%3e%3c/stop%3e%3cstop stop-color='rgba(59%2c 0%2c 101%2c 1)' offset='1'%3e%3c/stop%3e%3c/linearGradient%3e%3c/defs%3e%3c/svg%3e");
		background-repeat: no-repeat;
		background-size: cover;
		height: 100vh;
	}
	/*HEADER IMAGE*/
	.imageContainer {
		height: 15vh;
		width: 15vh;
	}

	.hero img {
		width: 90%;
		max-width: 450px;
	}
	.header {
		display: flex;
		justify-content: center;
		flex-direction: column;
		align-items: center;
		align-content: center;
		padding-bottom: 30px;
		margin-top: -40px;
		width: 100%;
	}
	.headImage {
		width: 50px;
		height: auto;
		padding-top: 40px;
	}
	/*COPY CONTENT*/

	.copy {
		padding-top: 30vh;
		background-image: url("../images/bbburst.svg");
		background-color: #030e16;
		background-repeat: no-repeat;
		background-size: cover;
		display: flex;
		justify-content: center;
		align-items: center;
		flex-direction: column;
		text-align: center;
	}
	.copy p {
		font-family: "Syne", sans-serif;
		font-size: 40px;
		width: 70%;
		text-align: left;
	}
	.copy-content {
		display: flex;
		justify-content: center;
		flex-direction: column;
		align-items: center;
		background-color: #221d36;
		width: 70%;
		border-radius: 25px;
		padding-bottom: 100px;
		margin-bottom: 100px;
	}

	a{
		color: #ff298e;
	}

	/*MICRO FRONTEND*/
	.micro-frontends {
		width: 100%;
		display: flex;
		flex-direction: row;
		justify-content: center;
		align-items: center;
		align-content: center;
	}
	.micro-frontends p {
		width: 90%;
	}
	.micro-img {
		height: 500px;
		display: flex;
		justify-content: center;
		align-items: center;
	}

	.img-overlay-wrap {
		margin: 40px;
		padding: 40px;
		height: 30vh;
		transition: transform 150ms ease-in-out;
		background-image: url("../images/nnneon.svg");
	}

	.micro-img img {
		height: 100%;
		width: auto;
	}
	.micro-cell {
		margin-top: 50px;
		background-color: #030e16;
		box-shadow: 10px 10px 8px black;
		border-radius: 25px;
		min-width: 80%;
		display: flex;
		justify-content: center;
		align-items: center;
		flex-direction: column;
		min-height: 30vh;
		overflow: hidden;
	}
	.thank {
		padding-top: 0px;
		display: flex;
		flex-direction: column;
		justify-content: center;
		align-items: center;
	}
	.thank p {
		text-align: center;
	}
	/*HEADER IMAGE*/

	.invite {
		display: flex;
		justify-content: center;
		flex-direction: column;
		align-items: center;
		width: 100%;
		text-align: center;
	}
	.invite p {
		text-align: center;
	}

	.copy-content h1 {
		font-size: 4vw;
		color: #ff298e;
	}

	.copy-content h3 {
		font-size: 1vw;
	}

	hr {
		margin: 50px;
		border: 0;
		border-top: 1px solid #ff298e;
	}

	@media (min-width: 640px) {
		body {
			max-width: none;
		}
	}

	.footer {
		padding-top: 50px;
		color: darkgray;
		display: flex;
		justify-content: center;
		align-items: center;
		align-content: center;
		flex-direction: column;
		padding-bottom: 80px;
	}
	.footer-logo {
		width: 10vw;
	}

	/*PHONE*/
	@media (max-width: 1000px) {
		/*top logo*/
		.imageContainer {
			height: 10vh;
			width: 10vh;
			padding-bottom: 30px;
		}
		.hero img {
			width: 100%;
			max-width: 450px;
		}

		.hero {
			height: auto;
		}

		/*fathym content*/
		.copy-content {
			width: 90%;
		}
		.copy-content h1 {
			font-size: 40px;
		}
		.copy-content h2 {
			font-size: 20px;
		}
		.copy-content h3 {
			font-size: 15px;
		}
		.copy-content p {
			font-size: 20px;
			width: 90%;
		}
		.office {
			max-width: 80%;
		}
		/*Mirco Frontends*/
		.micro-frontends {
			width: 100%;
			display: flex;
			flex-direction: column;
			justify-content: center;
			align-items: center;
			align-content: center;
		}
		.micro-frontends p {
			width: 90%;
		}
		.micro-img {
			height: 20vh;
			display: flex;
			justify-content: center;
			align-items: center;
			padding-top: 80px;
			padding-bottom: 80px;
		}
		.micro-img img {
			height: 100%;
			width: auto;
		}
		.micro-cell {
			background-color: #030e16;
			box-shadow: 10px 10px 8px black;
			border-radius: 25px;
			width: 100%;
			display: flex;
			justify-content: center;
			align-items: center;
			flex-direction: column;
			height: 25vh;
		}
	}
</style>

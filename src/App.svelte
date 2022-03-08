<script lang="ts">
	import Button, { Label } from '@smui/button';
	import Card from '@smui/card';
	import LayoutGrid, { Cell } from '@smui/layout-grid';

	export class Game {
		public Description: string;
		
		public Name: string;
		
		public PlayLink: string;
		
		public SourceCode: string;
	}

	export let games: Game[] = [{
		Name: '2048',
		Description: `A small clone of 1024, based on Saming's 2048 (also a clone).`,
		PlayLink: './2048',
		SourceCode: 'https://github.com/fathym-arcade/2048'
	}, {
		Name: 'Hextris',
		Description: 'An addictive puzzle game inspired by Tetris.',
		PlayLink: './hextris',
		SourceCode: 'https://github.com/fathym-arcade/hextris'
	}, {
		Name: 'Clumsy Bird',
		Description: `A MelonJS made 'Flappy Bird' clone.`,
		PlayLink: './clumsy-bird',
		SourceCode: 'https://github.com/fathym-arcade/clumsy-bird'
	}, {
		Name: 'Pacman Canvas',
		Description: 'A pacman game built with HTML5 canvas',
		PlayLink: './pacman-canvas',
		SourceCode: 'https://github.com/fathym-arcade/pacman-canvas'
	}, {
		Name: 'Astray',
		Description: 'A WebGL maze game built with Three.js and Box2dWeb.',
		PlayLink: './astray',
		SourceCode: 'https://github.com/fathym-arcade/astray'
	}];
</script>

<main>
	<section class="hero">
		<h1>Fathym Arcade</h1>
	
		<img src="https://www.fathym.com/assets/images/fathym-arcade.png" alt="Fathym Arcade" />
	</section>

	<section>
		<LayoutGrid>
			{#each games as game, i}
			  <Cell>
				<Card padded>
					<h2 class="demo-cell">{game.Name}</h2>

					<p>{game.Description}</p>

					<div>
						<Button href={game.PlayLink} touch variant="raised">
							<Label>Play Now</Label>
						</Button>

						<Button href={game.SourceCode} touch target="_blank">
							<Label>View Source Code</Label>
						</Button>
					</div>
				</Card>
			  </Cell>
			{/each}
		  </LayoutGrid>
	</section>
</main>

<style>
	main {
		text-align: center;
		padding: 1em;
		max-width: 240px;
		margin: 0 auto;
	}

	.hero h1 { 
		text-transform: uppercase;
		font-size: 4em;
		font-weight: 100;
	}

	.hero img {
		width: 90%;
		max-width: 450px;
	}

	@media (min-width: 640px) {
		main {
			max-width: none;
		}
	}
</style>
<div class="intro">
	<div>
		<h1>Jump into Oracle Pools</h1>
		<p>
			Explore, run, and launch decentralized oracles on the <a href="https://ergoplatform.org"
				>Ergo</a
			>
			blockchain, or simply learn more about oracle pools.
		</p>
	</div>
</div>

<div class="gallery">
	<a href="/#">
		<div>
			<h2>Explore</h2>
			<p>Inspect existing pools or find oracles to recruit for a new pool.</p>
		</div>
	</a>
	<a href="/#">
		<div>
			<h2>Run</h2>
			<p>Join a pool or register to become an oracle operator.</p>
		</div>
	</a>
	<a href="/#">
		<div>
			<h2>Launch</h2>
			<p>Configure and launch a pool for your dapp.</p>
		</div>
	</a>
	<a href="/#">
		<div>
			<h2>Learn</h2>
			<p>Understand how oracle pools work and what to look out for when using them.</p>
		</div>
	</a>
</div>

<style>
	.intro {
		display: flex;
		flex-direction: column;
		justify-content: center;
		margin: 5rem 0 5rem 0;
	}
	.intro h1 {
		font-size: 2.5em;
	}
	.gallery {
		display: grid;
		grid-template-columns: 1fr;
		grid-auto-rows: 1fr;
		column-gap: 2em;
		row-gap: 2em;
		margin-bottom: 5em;
	}
	@media (min-width: 560px) {
		.gallery {
			grid-template-columns: repeat(2, 1fr);
		}
	}
	@media (min-width: 900px) {
		.gallery {
			grid-template-columns: repeat(3, 1fr);
		}
	}
	@media (min-width: 1024px) {
		.gallery {
			grid-template-columns: repeat(4, 1fr);
		}
	}
	.gallery a {
		text-decoration: none;
		color: var(--text-color);
	}
	.gallery a div {
		border: 1px solid gray;
		border-radius: 5px;
		padding: 1em 1em;
		height: calc(100% - 2em);
	}
</style>

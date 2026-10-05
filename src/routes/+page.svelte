<script lang="ts">
	import { ArrowUpRight, Mail } from '@lucide/svelte';
	import { site } from '#lib/site.ts';
	import Header from '#lib/components/Header.svelte';

	const ticker = Array.from({ length: 6 }, () => 'Something bigger comes out');
</script>

<svelte:head>
	<title>{site.title}</title>
	<meta name="description" content={site.description} />
	<link rel="canonical" href={site.url} />
	<meta property="og:type" content="website" />
	<meta property="og:url" content={site.url} />
	<meta property="og:title" content={site.title} />
	<meta property="og:description" content={site.description} />
	<meta property="og:image" content="{site.url}/yusuf.png" />
	<meta name="twitter:card" content="summary_large_image" />
</svelte:head>

<div class="screen">
	<Header />

	<main class="hero container">
		<div class="copy">
			<p class="eyebrow">
				<span>{site.tagline}</span>
				<span class="rule" aria-hidden="true"></span>
				<span>{new Date().getFullYear()}</span>
			</p>

			<h1>
				Something bigger
				<span>is coming.</span>
			</h1>

			<p class="lede">
				We're building something new at <strong>somdvps.org</strong>. It isn't ready yet, but it's close. Until it
				lands, this is where to find us.
			</p>

			<div class="actions">
				<a class="btn btn-primary btn-lg" href="mailto:{site.email}">
					<Mail size={18} aria-hidden="true" />
					Email us
				</a>
				<a class="btn btn-lg" href={site.portfolio} target="_blank" rel="noopener">
					{site.founder}'s portfolio
					<ArrowUpRight size={18} aria-hidden="true" />
				</a>
			</div>

			<dl class="meta">
				<div>
					<dt>Email</dt>
					<dd><a href="mailto:{site.email}">{site.email}</a></dd>
				</div>
				<div>
					<dt>Portfolio</dt>
					<dd><a href={site.portfolio} target="_blank" rel="noopener">{site.portfolioLabel}</a></dd>
				</div>
			</dl>
		</div>

		<figure class="portrait">
			<span class="word" aria-hidden="true">{site.name}</span>
			<img src="/yusuf.png" alt="{site.founder}, seated in a black suit, black-and-white portrait" width="450" height="554" />
		</figure>
	</main>

	<div class="ticker" aria-hidden="true">
		<div class="track">
			{#each [0, 1] as _}
				<div class="run">
					{#each ticker as line}
						<span>{line}</span><span class="star">✦</span>
					{/each}
				</div>
			{/each}
		</div>
	</div>
</div>

<style>
	/* Header, hero and ticker share one viewport — nothing to scroll. */
	.screen {
		display: grid;
		grid-template-rows: auto minmax(0, 1fr) auto;
		height: 100svh;
		overflow: hidden;
	}

	/* ---------- Hero ---------- */
	.hero {
		display: grid;
		grid-template-columns: minmax(0, 1.1fr) minmax(0, 0.9fr);
		gap: clamp(24px, 4vw, 64px);
		max-width: 1360px;
		min-height: 0;
	}
	.copy {
		align-self: center;
		padding-block: 3vh;
	}

	/* Plain editorial line: label, hairline, year */
	.eyebrow {
		display: flex;
		align-items: center;
		gap: 16px;
		max-width: 34rem;
		font-size: 0.85rem;
		font-weight: 500;
		color: var(--ink-2);
		font-variant-numeric: tabular-nums;
		animation: rise 0.7s var(--ease) both;
	}
	.rule {
		flex: 1;
		height: 1px;
		background: var(--line-strong);
	}

	h1 {
		margin-top: clamp(16px, 3.5vh, 28px);
		font-size: clamp(2.8rem, min(7.5vw, 11vh), 7rem);
		font-weight: 600;
		line-height: 0.92;
		letter-spacing: -0.05em;
		animation: rise 0.8s 0.08s var(--ease) both;
	}
	h1 span {
		display: block;
		color: var(--muted);
	}

	.lede {
		max-width: 46ch;
		margin-top: clamp(16px, 3.5vh, 28px);
		font-size: clamp(1rem, 1.3vw, 1.15rem);
		line-height: 1.6;
		color: var(--ink-2);
		animation: rise 0.8s 0.16s var(--ease) both;
	}
	.lede strong {
		font-weight: 600;
		color: var(--ink);
	}

	.actions {
		display: flex;
		flex-wrap: wrap;
		gap: 10px;
		margin-top: clamp(20px, 4.5vh, 36px);
		animation: rise 0.8s 0.24s var(--ease) both;
	}
	.btn-lg {
		height: 52px;
		padding: 0 24px;
		font-size: 0.98rem;
	}

	.meta {
		display: flex;
		flex-wrap: wrap;
		gap: 16px 48px;
		margin: clamp(24px, 5vh, 48px) 0 0;
		padding-top: clamp(16px, 3vh, 24px);
		border-top: 1px solid var(--line);
		animation: rise 0.8s 0.32s var(--ease) both;
	}
	.meta dt {
		font-size: 0.78rem;
		font-weight: 500;
		color: var(--muted);
	}
	.meta dd {
		margin: 2px 0 0;
		font-weight: 500;
	}
	.meta a {
		text-decoration: underline;
		text-decoration-color: var(--line-strong);
		text-underline-offset: 4px;
		transition: text-decoration-color 0.15s;
	}
	.meta a:hover {
		text-decoration-color: var(--ink);
	}

	/* ---------- Portrait ---------- */
	.portrait {
		position: relative;
		min-height: 0;
		animation: fade 1.1s 0.2s var(--ease) both;
	}
	.word {
		position: absolute;
		top: 17%;
		left: 50%;
		translate: -50% 0;
		font-size: clamp(4rem, min(10vw, 17vh), 10rem);
		font-weight: 700;
		letter-spacing: -0.06em;
		line-height: 1;
		color: transparent;
		-webkit-text-stroke: 1.5px var(--line-strong);
		white-space: nowrap;
		user-select: none;
	}
	/* The top quarter of the cutout is empty, so the photo can stand taller than its column
	   and spill sideways; raise --portrait-scale to make it bigger. */
	.portrait {
		--portrait-scale: 1.18;
	}
	.portrait img {
		position: absolute;
		bottom: 0;
		left: 50%;
		translate: -50% 0;
		width: auto;
		height: calc(100% * var(--portrait-scale));
		max-width: none;
		pointer-events: none;
		filter: grayscale(1) contrast(1.04);
	}
	/* The cutout is mostly black — give it a faint halo so it doesn't sink into the dark page */
	:global(:root[data-theme='dark']) .portrait img {
		filter: grayscale(1) contrast(1.04) drop-shadow(0 0 28px rgb(255 255 255 / 0.14));
	}

	/* ---------- Ticker ---------- */
	.ticker {
		overflow: hidden;
		background: var(--ink);
		color: var(--bg);
	}
	.track {
		display: flex;
		width: max-content;
		animation: marquee 40s linear infinite;
	}
	.run {
		display: flex;
		align-items: center;
		flex: none;
	}
	.run span {
		padding: clamp(10px, 1.6vh, 15px) 0;
		font-size: clamp(1.05rem, min(2vw, 3.2vh), 1.6rem);
		font-weight: 600;
		letter-spacing: -0.035em;
		white-space: nowrap;
	}
	.run .star {
		padding-inline: 0.9em;
		font-size: clamp(0.75rem, 1.2vw, 1rem);
		opacity: 0.55;
	}

	/* ---------- Motion ---------- */
	@keyframes rise {
		from {
			opacity: 0;
			transform: translateY(14px);
		}
	}
	@keyframes fade {
		from {
			opacity: 0;
			transform: translateX(18px);
		}
	}
	@keyframes marquee {
		to {
			transform: translateX(-50%);
		}
	}
	@media (prefers-reduced-motion: reduce) {
		.track {
			animation: none;
		}
	}

	/* ---------- Responsive ---------- */
	@media (max-width: 900px) {
		.hero {
			grid-template-columns: 1fr;
			grid-template-rows: auto minmax(0, 1fr);
			gap: 0;
		}
		.copy {
			padding-block: 2vh 0;
		}
		.meta {
			display: none;
		}
		.portrait {
			min-height: 200px;
		}
		.word {
			top: 12%;
		}
	}
	@media (max-width: 480px) {
		.lede {
			font-size: 0.95rem;
		}
		.btn-lg {
			height: 46px;
			padding: 0 18px;
			font-size: 0.92rem;
		}
	}
	/* Very short screens can't fit everything; let them scroll rather than clip */
	@media (max-height: 560px), (max-width: 900px) and (max-height: 640px) {
		.screen {
			height: auto;
			min-height: 100svh;
			overflow: visible;
		}
		.portrait {
			min-height: 320px;
		}
	}
</style>

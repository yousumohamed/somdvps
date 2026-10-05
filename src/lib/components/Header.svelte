<script lang="ts">
	import { ArrowUpRight } from '@lucide/svelte';
	import { site } from '../site';
	import ThemeToggle from './ThemeToggle.svelte';
</script>

<header class="site-header">
	<div class="container inner">
		<a href="/" class="brand" aria-label="{site.name} — home">
			<span class="name">{site.name}</span>
		</a>

		<nav aria-label="Primary">
			<a href="mailto:{site.email}" class="nav-link">Contact</a>
			<a href={site.portfolio} class="nav-link portfolio" target="_blank" rel="noopener">
				Portfolio <ArrowUpRight size={14} strokeWidth={2.2} aria-hidden="true" />
			</a>
			<ThemeToggle />
			<a class="btn btn-primary btn-sm contact" href="mailto:{site.email}">Get in touch</a>
		</nav>
	</div>
</header>

<style>
	.site-header {
		position: sticky;
		top: 0;
		z-index: 40;
		height: var(--header-h);
		background: color-mix(in srgb, var(--bg) 88%, transparent);
		backdrop-filter: saturate(1.4) blur(14px);
		-webkit-backdrop-filter: saturate(1.4) blur(14px);
	}
	.inner {
		height: 100%;
		display: flex;
		align-items: center;
		justify-content: space-between;
		gap: 20px;
	}
	.brand {
		display: inline-flex;
		align-items: center;
		font-weight: 700;
		font-size: 1.15rem;
		letter-spacing: -0.02em;
	}
	nav {
		display: flex;
		align-items: center;
		gap: 4px;
	}
	.nav-link {
		display: inline-flex;
		align-items: center;
		gap: 3px;
		padding: 8px 12px;
		border-radius: 999px;
		font-size: 0.9rem;
		font-weight: 500;
		color: var(--muted);
		transition: color 0.15s;
	}
	.nav-link:hover {
		color: var(--ink);
	}
	.contact {
		margin-left: 8px;
	}

	@media (max-width: 560px) {
		.portfolio,
		.contact {
			display: none;
		}
	}
</style>

<script>
	import "@fontsource-variable/inter";
	import "#lib/styles/global.scss";
	import { afterNavigate } from "$app/navigation";
	import rfLogo from "#lib/assets/rf.svg";
	import eventLogo from "#lib/assets/logo.svg";
	import avatar from "#lib/assets/fl.svg";
	import searchIcon from "#lib/assets/search.svg";

	let { children } = $props();
	let menuOpen = $state(false);

	afterNavigate(() => {
		menuOpen = false;
	});
</script>

<svelte:window
	onkeydown={(event) => {
		if (event.key === "Escape") menuOpen = false;
	}}
/>

<svelte:head>
	<link rel="icon" href={rfLogo} />
</svelte:head>

<div class="app">
	<aside class="sidebar">
		<div class="rail">
			<div class="rail-top">
				<a class="logo-tile" href="https://www.rainfocus.com/">
					<img src={rfLogo} alt="RainFocus" width="32" height="32" />
				</a>
				<div class="event-tile">
					<img
						src={eventLogo}
						alt="RainFocus Summit"
						width="32"
						height="32"
					/>
				</div>
				<button
					class="menu-button"
					type="button"
					aria-label="Menu"
					aria-expanded={menuOpen}
					aria-controls="site-nav"
					onclick={() => (menuOpen = !menuOpen)}
				>
					<svg
						width="24"
						height="24"
						viewBox="0 0 24 24"
						aria-hidden="true"
					>
						<path
							d="M3 6h18v2H3zm0 5h18v2H3zm0 5h18v2H3z"
							fill="currentColor"
						/>
					</svg>
				</button>
			</div>

			<div class="user-tile">
				<img src={avatar} alt="User avatar" width="32" height="32" />
			</div>
		</div>

		<nav class="nav" class:open={menuOpen} id="site-nav">
			<p class="event-name">RainFocus Summit</p>
			<p class="event-details">Lehi, UT • December 15th</p>

			<label class="search-field">
				<img src={searchIcon} alt="" width="16" height="16" />
				<input type="search" placeholder="Search" aria-label="Search" />
			</label>

			<ul>
				<li>
					<a class="nav-item" href="/guide">
						<span class="nav-icon"></span>
						Guide
					</a>
				</li>
				<li>
					<a class="nav-item active" href="/attendees">
						<span class="nav-icon"></span>
						Attendees
					</a>
					<ul class="sub-list">
						<li><a href="/attendees">Attendees</a></li>
						<li><a href="/attendees/types">Attendee types</a></li>
						<li><a href="/attendees/packages">Packages</a></li>
						<li><a href="/attendees/reg-codes">Reg codes</a></li>
						<li><a href="/attendees/discounts">Discounts</a></li>
					</ul>
				</li>
				<li>
					<a class="nav-item" href="/content">
						<span class="nav-icon"></span>
						Content
					</a>
				</li>
				<li>
					<a class="nav-item" href="/exhibitors">
						<span class="nav-icon"></span>
						Exhibitors
					</a>
				</li>
			</ul>
		</nav>
	</aside>

	{#if menuOpen}
		<button
			class="backdrop"
			type="button"
			aria-label="Close menu"
			onclick={() => (menuOpen = false)}
		></button>
	{/if}

	<main class="main">
		{@render children()}
	</main>
</div>

<style lang="scss">
	.app {
		display: flex;
		height: 100vh;
		height: 100dvh;
	}

	.sidebar {
		display: flex;
		flex-shrink: 0;
	}

	.rail {
		display: flex;
		flex-direction: column;
		justify-content: space-between;
		align-items: center;
		width: 63px;
		padding: 11px 0;
		border: 1px solid var(--color-border);
	}

	.logo-tile {
		display: block;
		padding: 8px 0 24px 12px;
	}

	.event-tile {
		padding: 4px 8px 8px;

		img {
			border-radius: 4px;
		}
	}

	.user-tile {
		padding: 4px 8px;
	}

	.menu-button,
	.backdrop {
		display: none;
	}

	.nav {
		width: 215px;
		padding: 12px 8px;
		border-right: 1px solid var(--color-border);
	}

	.event-name {
		padding: 8px 8px 12px;
		font-size: 14px;
		font-weight: 600;
		line-height: 18.2px;
		color: var(--color-text-header);
	}

	.event-details {
		padding: 0 8px 12px;
		font-size: 10px;
		font-weight: 500;
		line-height: 18.2px;
		color: var(--color-black);
	}

	.search-field {
		display: flex;
		align-items: center;
		gap: 4px;
		height: 24px;
		margin: 0 8px 12px;
		padding: 4px;
		border-radius: 4px;
		background: var(--color-input-bg);

		input {
			flex: 1;
			min-width: 0;
			appearance: none;
			border: none;
			padding: 0;
			background: none;
			font-size: 10px;
			font-weight: 600;
			line-height: 10px;
			color: var(--color-text-header);
		}

		input::placeholder {
			color: var(--color-g5);
			opacity: 1;
		}
	}

	.nav-item {
		display: flex;
		align-items: center;
		gap: 12px;
		padding: 8px 12px;
		border-radius: 8px;
		font-size: 14px;
		font-weight: 600;
		line-height: 18.2px;
		color: var(--color-g4);

		&.active {
			background: var(--color-grape-8);
			color: var(--color-grape);
		}
	}

	.nav-icon {
		flex-shrink: 0;
		width: 24px;
		height: 24px;
		border-radius: 50%;
		background: currentColor;
	}

	.sub-list {
		padding: 4px 12px 12px 48px;

		a {
			display: block;
			padding: 8px 0;
			font-size: 14px;
			font-weight: 600;
			line-height: 14px;
			color: var(--color-g4);
		}
	}

	.main {
		flex: 1;
		overflow-y: auto;
		padding: 40px 48px;
	}

	@media (max-width: 1023px) {
		.menu-button {
			display: grid;
			place-items: center;
			width: 48px;
			height: 40px;
			border: 0;
			border-radius: 8px;
			background: none;
			color: var(--color-g4);
			cursor: pointer;

			&[aria-expanded="true"] {
				background: var(--color-grape-8);
				color: var(--color-grape);
			}
		}

		.nav {
			display: none;
			position: fixed;
			top: 0;
			bottom: 0;
			left: 63px;
			z-index: 2;
			overflow-y: auto;
			background: var(--color-white);

			&.open {
				display: block;
			}
		}

		.backdrop {
			display: block;
			position: fixed;
			inset: 0 0 0 63px;
			z-index: 1;
			border: 0;
			background: rgba(0, 0, 0, 0.3);
		}
	}

	@media (max-width: 599px) {
		.main {
			padding: 24px 16px;
		}
	}
</style>

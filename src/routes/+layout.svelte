<script>
	import "@fontsource-variable/inter";
	import "#lib/styles/global.scss";
	import rfLogo from "#lib/assets/rf.svg";
	import eventLogo from "#lib/assets/logo.svg";
	import avatar from "#lib/assets/fl.svg";
	import searchIcon from "#lib/assets/search.svg";

	let { children } = $props();
</script>

<svelte:head>
	<link rel="icon" href={rfLogo} />
</svelte:head>

<!-- App shell: same on every page -->
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
			</div>

			<div class="user-tile">
				<img src={avatar} alt="User avatar" width="32" height="32" />
			</div>
		</div>
		<nav class="nav">
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
					<!-- "active" is hard-coded to match the design. -->
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
	<main class="main">
		{@render children()}
	</main>
</div>

<style lang="scss">
	.app {
		display: flex;
		height: 100vh;
	}

	.sidebar {
		display: flex;
		flex-shrink: 0; // keep its width when the window gets narrow
	}

	.nav {
		width: 215px;
		padding: 12px 8px;
		border-right: 1px solid var(--color-border);
	}

	.main {
		flex: 1; // take up all remaining space
		overflow-y: auto; // scroll inside the main when content is taller than the window
		padding: 40px 48px;
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

	.event-name {
		padding: 8px 8px 12px; // top, sides, bottom
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
		align-items: center; // circle and label centred on one line
		gap: 12px;
		padding: 8px 12px; // 8 + 24px circle + 8 = Figma's 40px height
		border-radius: 8px;
		font-size: 14px;
		font-weight: 600;
		line-height: 18.2px;
		color: var(--color-g4);

		// Compiles to ".nav-item.active".
		&.active {
			background: var(--color-grape-8);
			color: var(--color-grape);
		}
	}
	.nav-icon {
		flex-shrink: 0; // never squash the circle
		width: 24px;
		height: 24px;
		border-radius: 50%; // a square with 50% radius is a circle
		background: currentColor; // follows the label's colour
	}

	.sub-list {
		// 48 left = 12 padding + 24 circle + 12 gap, so links line up with the labels.
		padding: 4px 12px 12px 48px;

		a {
			display: block; // the whole row is clickable, not just the words
			padding: 8px 0; // 8 + 14 line + 8 = Figma's 30px height
			font-size: 14px;
			font-weight: 600;
			line-height: 14px;
			color: var(--color-g4);
		}
	}
</style>

<script>
	import { page } from '$app/stores';
	import "../app.css";

	let isMenuOpen = false;
	let pagesWithNavbar = ["/", "/about", "/contact", "/profile", "/apartment"];

	function toggleMenu() {
		isMenuOpen = !isMenuOpen;
	}

	function logOut() {
		window.location.href = '/';
	}
</script>

<svelte:head>
	<link rel="preconnect" href="https://fonts.googleapis.com">
	<link rel="preconnect" href="https://fonts.gstatic.com" crossorigin="anonymous">
	<link href="https://fonts.googleapis.com/css2?family=Poppins:wght@100;400;700&display=swap" rel="stylesheet">
	<link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.0.0-beta3/css/all.min.css">
</svelte:head>

{#if $page.url.pathname && pagesWithNavbar.includes($page.url.pathname)}
	<div class="navbar">
		<a href="/" class="mr-auto font-bold logo">Apateu</a>
		<button class="burger" on:click={toggleMenu} aria-label="Toggle navigation" aria-expanded={isMenuOpen}>
			<div class="line"></div>
			<div class="line"></div>
			<div class="line"></div>
		</button>
		<div class={`navbar-links ${isMenuOpen ? 'open' : ''}`}>
			<a href="/">Apartment</a>
			<a href="/about">About</a>
			<a href="/contact">Contact</a>
		</div>
	</div>
{/if}

<main class="main-content">
	<slot></slot>
</main>

<style>
	:global(body) {
		font-family: 'Poppins', sans-serif;
		margin: 0;
		padding: 0;
		background-color: #DBDBDB;
		display: flex;
		flex-direction: column;
		min-height: 100vh;
	}

	.navbar {
		display: flex;
		align-items: center;
		justify-content: space-between;
		flex-wrap: wrap;
		background-color: #515739;
		padding: 0.5rem 1.5rem;
		box-shadow: 0 2px 4px rgba(0, 0, 0, 0.1);
		width: 100%;
		position: relative;
	}

	.navbar a {
		color: #ffffff;
		text-decoration: none;
		padding: 0.25rem 0.75rem;
		font-size: 0.9rem;
		transition: transform 0.2s, color 0.2s, background-color 0.3s, box-shadow 0.3s;
		border-radius: 5px;
	}

	.navbar .logo {
		font-size: 1.2rem;
		font-weight: bold;
		transition: transform 0.2s, color 0.2s;
	}

	.navbar a:hover {
		color: #ffffff;
		transform: scale(1.05);
		background-color: #7a8357;
		box-shadow: 0px 4px 8px rgba(0, 0, 0, 0.2);
	}

	.burger {
		display: none;
		flex-direction: column;
		cursor: pointer;
		background: none;
		border: none;
		position: absolute;
		top: 0.5rem;
		right: 1.5rem;
	}

	.line {
		width: 20px;
		height: 2px;
		background-color: #ffffff;
		margin: 3px 0;
		transition: 0.3s;
	}

	.main-content {
		flex: 1;
		padding: 2rem;
		display: flex;
		flex-direction: column;
		justify-content: center;
	}

	@media (max-width: 768px) {
		.navbar {
			flex-direction: column;
			align-items: flex-start;
		}

		.burger {
			display: flex;
			top: 1rem;
			right: 1.5rem;
		}

		.navbar-links {
			display: none;
			flex-direction: column;
			width: 100%;
		}

		.navbar-links.open {
			display: flex;
		}

		.navbar a {
			width: 100%;
			text-align: left;
			padding: 1rem;
		}
	}

	@media (max-width: 480px) {
		.navbar .logo {
			font-size: 1.1rem;
		}

		.main-content {
			padding: 1rem;
		}
	}
</style>
<script>
	import "../app.css";

	let isMenuOpen = false;

	function toggleMenu() {
		isMenuOpen = !isMenuOpen;
	}
</script>

<svelte:head>
	<link rel="preconnect" href="https://fonts.googleapis.com">
	<link rel="preconnect" href="https://fonts.gstatic.com" crossorigin="anonymous">
	<link href="https://fonts.googleapis.com/css2?family=Poppins:wght@100;400;700&display=swap" rel="stylesheet">
</svelte:head>

<div class="navbar">
	<a href="/" class="mr-auto font-bold logo">Apateu</a>
	<button class="burger" on:click={toggleMenu} aria-label="Toggle navigation" aria-expanded={isMenuOpen}>
		<div class="line"></div>
		<div class="line"></div>
		<div class="line"></div>
	</button>
	<div class={`navbar-links ${isMenuOpen ? 'open' : ''}`}>
		<a href="/apartment">Apartment</a>
		<a href="/about">About</a>
		<a href="/contact">Contact</a>
	</div>
</div>

<main class="main-content">
	<slot></slot>
</main>

<style>
	:global(body) {
		font-family: 'Poppins', sans-serif;
		margin: 0;
		padding: 0;
		background-color: #DBDBDB;
		background-image: url('/image/background.png');
		background-size: 125%;
		background-position: center -150px;
		background-repeat: no-repeat;
		background-attachment: fixed;
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
		transition: transform 0.2s, color 0.2s;
		border-radius: 5px;
	}

	.navbar .logo {
		font-size: 1.2rem;
		font-weight: bold;
		transition: transform 0.2s, color 0.2s;
	}

	.navbar a:hover {
		color: #DF6630;
		transform: scale(1.1);
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

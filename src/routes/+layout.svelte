<script lang="ts">
	import '../app.css';
   import routes from '$lib/routes';
    import { onNavigate } from '$app/navigation';
    import {page} from '$app/stores'
	let menuOpen = false;

   let currentPage = $page.route.id

	const toggleMenu = () => {
		menuOpen = !menuOpen;
	};

   $: {
    currentPage = $page.route.id;
  }
   const closeMenu = () => {
      menuOpen = false
   }

   const navLinkData = [
      {
         path: routes.home,
         label: 'Home',
         number: 0
      },
      {
         path: routes.destination,
         label: 'Destination',
         number: 1
      },
      {
         path: routes.crew,
         label: 'Crew',
         number: 2
      }
   ]

   onNavigate(() => closeMenu())
</script>

<header>
	<nav class="nav">
		<img src="./assets/logo.svg" alt="logos" class="logo" />

		<hr class="nav-hr" />
		<ul class={`nav-items ${menuOpen && 'open'}`}>
         {#each navLinkData as {path, number, label} }
            
			<li>
				<a href={path} class={`${currentPage === path && 'active'}`}>
					<span> 0{number} </span> {label}
				</a>
			</li>
         {/each}
		</ul>
		<button class="menu-btn" on:click={toggleMenu}>
			<img
				src={menuOpen ? './assets/icon-close.svg' : './assets/icon-hamburger.svg'}
				alt="menu-btn"
			/>
		</button>
	</nav>
</header>

<main>
	<slot />
</main>

<style>
	header {
		width: 100%;
	}

	nav {
		display: flex;
		justify-content: space-between;
		align-items: center;
		gap: 1.5rem;
		padding: 1rem 0 0 2rem;
	}

	main {
		padding: 1rem 1.5rem;
	}

	.logo {
		height: 48px;
		width: 48px;
	}

	hr {
		background: rgb(var(--color-white));
		opacity: 0.25;
		width: 100%;
		z-index: 1;
	}

   .active {
      border-bottom: 2px solid rgb(var(--color-white));
      padding-bottom: 8px;
   }

	.nav-items {
		display: flex;
		list-style: none;
		background-color: rgba(255, 255, 255, 0.04);
		backdrop-filter: blur(40.7742px);
		gap: 40px;
		padding: 0 4rem;
		margin-left: -4rem;
		width: 100%;
		justify-content: center;
		font-size: 16px;
	}

	.nav-items > li {
		padding: 1rem 0;
	}
	@media screen and (max-width: 56.25em) {
		nav {
			padding: 1rem 1.5rem;
		}

		.nav-items {
			position: fixed;
			top: 0;
			right: 0;
			padding: 5rem 1rem;
         justify-content: flex-start;
			font-size: 1.5rem;
         flex-direction: column;
			width: 85%;
			height: 100vh;
			transform: translateX(100%);
         transition: transform 0.2s ease-in-out;
			z-index: 2;
         padding: 7rem 3rem;
         background: rgba(0, 0, 0, 0.3);
		}
      

		.nav-items.open::after {
			content: '';
			background: rgba(0, 0, 0, 0.7);
			backdrop-filter: blur(50px);
			width: 50%;
			height: 100%;
			position: fixed;
			top: 0;
			left: -50%;
			z-index: -1;
		}

		.nav-items.open {
			transform: translateX(0);
		}

		hr {
			display: none;
		}

		.nav-items > li {
			margin-bottom: 1rem;
		}

		.menu-btn {
			z-index: 3;
		}
	}

	@media screen and (min-width: 56.25em) {
		.menu-btn {
			display: none;
		}
	}
</style>

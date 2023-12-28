<svelte:head>
	<title>Home | Space Tourism App</title>
	<meta name="description" content="Product Page Description" />
</svelte:head>
<div class="main-container">
	<picture>
		<source media="(min-width: 900px)" srcset="./assets/home/background-home-desktop.jpg" />
		<img src="./assets/home/background-home-mobile.jpg" alt="background-img" class='bg-image' />
	</picture>

	<div class="home_description">
		<p class="home_header_text">so you want to travel to</p>
		<h1>Space</h1>
		<p class="home_description_text">
			Let’s face it; if you want to go to space, you might as well genuinely go to outer space and
			not hover kind of on the edge of it. Well sit back, and relax because we’ll give you a truly
			out of this world experience!
		</p>
	</div>
	<div class="home_sub-container">
		<div class="explore">
			<p class="explore-text">EXPLORE</p>
		</div>
	</div>
</div>

<style>

   .home_header_text {
      font-size: 25px;
      text-transform: uppercase;
   }

   h1 {
      font-size: 40px;
      margin: 1rem 0;
   }

   .home_sub-container {
      background-color: rgb(var(--color-white));
      color: rgb(var(--color-primary));
      max-width: 300px;
      width: 100%;
      height: 300px;
      border-radius: 50%;
      display: grid;
      place-items: center;
      margin: 2rem auto;
   }
   
	.explore-text {
      color: var(--black);
		font-size: 32px;
	}
   
	.home_sub-container {
      position: relative;
	}
   </style>

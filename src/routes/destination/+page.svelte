<script lang="ts">
	const destinationData = [
		{
			img: './assets/destination/image-moon.png',
			name: 'moon',
			description:
				'See our planet as you’ve never seen it before. A perfect relaxing trip away to help regain perspective and come back refreshed. While you’re there, take in some history by visiting the Luna 2 and Apollo 11 landing sites.',
			distance: '384,500 KM',
			travelTime: '3 DAYS'
		},
		{
			img: './assets/destination/image-mars.png',
			name: 'mars',
			description:
				'Don’t forget to pack your hiking boots. You’ll need them to tackle Olympus Mons, the tallest planetary mountain in our solar system. It’s two and a half times the size of Everest!',
			distance: '225 MILL KM',
			travelTime: '9 MONTHS'
		},
		{
			img: './assets/destination/image-europa.png',
			name: 'europa',
			description:
				'The smallest of the four Galilean moons orbiting Jupiter, Europa is a winter lover’s dream. With an icy surface, it’s perfect for a bit of ice skating, curling, hockey, or simple relaxation in your snug wintery cabin.',
			distance: '628 MILL. KM',
			travelTime: '3 YEARS'
		},
		{
			img: './assets/destination/image-titan.png',
			name: 'titan',
			description:
				'The only moon known to have a dense atmosphere other than Earth, Titan is a home away from home (just a few hundred degrees colder!). As a bonus, you get striking views of the Rings of Saturn.',
			distance: '1.6 BIL. KM',
			travelTime: '7 YEARS'
		}
	];

	let activeIndex = 0;
	let activeDestination = destinationData[activeIndex];

   $: {
      activeDestination = destinationData[activeIndex]
   }
</script>

<svelte:head>
	<title>Destination</title>
	<meta name="description" content="Destination page" />
</svelte:head>

<div class="main-container">
	<picture>
		<source
			media="(min-width: 900px)"
			srcset="./assets/destination/background-destination-desktop.jpg"
		/>
		<img
			src="./assets/destination/background-destination-mobile.jpg"
			alt="background-img"
			class="bg-image"
		/>
	</picture>

	<div>
		<h1 class="page-header-text"><span>01 </span>Pick your Destination</h1>
		<img src={activeDestination.img} alt={activeDestination.name} />
	</div>

	<div class="destination-data-container">
		<ul class="destinations_text">
			{#each destinationData as data, index}
				<li>
					<button
						class={`destination-btn ${activeIndex === index && 'active'}`}
						on:click={() => activeIndex = index}>{data.name}</button
					>
				</li>
			{/each}
		</ul>
		<p class="title-text">{activeDestination.name}</p>
		<p>{activeDestination.description}</p>

		<hr />

		<div class="destination_data_description_container">
			<div class="destination_data">
				<p class="data_header">Avg. Distance</p>
				<p class="data_details">{activeDestination.distance}</p>
			</div>
			<div class="destination_data">
				<p class="data_header">Est. travel time</p>
				<p class="data_details">{activeDestination.travelTime}</p>
			</div>
		</div>
	</div>
</div>

<style>
	.destination-data-container {
		margin: 0 auto;
	}
	.destinations_text {
		display: flex;
		justify-content: center;
		margin: 1.5rem 0;
		width: 100%;
		gap: 2rem;
	}

	.destination-btn {
		color: inherit;
		text-transform: capitalize;
      padding-bottom: 8px;
	}

   .destination-btn.active {
      border-bottom: 2px solid rgb(var(--color-white));
   }

	.title-text {
		font-weight: 700;
		font-size: 40px;
		text-transform: uppercase;
	}

	hr {
		background: rgb(var(--color-white));
		opacity: 0.25;
		width: 100%;
		z-index: 1;
		margin-top: 3rem;
	}

	.destination_data_description_container {
		padding: 1rem 0;
		text-transform: uppercase;
	}

	.data_header {
		color: rgb(var(--color-primary));
	}

	.data_details {
		font-size: 28px;
		font-family: var(--header-font);
	}

   @media screen and (min-width: 400px) {
      .destination_data_description_container {
         display: flex;
         gap: 80px;
         text-transform: uppercase;
      }
   }

	@media screen and (min-width: 900px) {
		.destinations_text {
			justify-content: flex-start;
		}
	}

</style>

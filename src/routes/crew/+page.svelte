<script lang="ts">
	const crewData = [
		{
			role: 'commander',
			name: 'DOUGLAS HURLEY',
			bio: 'Douglas Gerald Hurley is an American engineer, former Marine Corps pilot and former NASA astronaut. He launched into space for the third time as commander of Crew Dragon Demo-2.',
			image: './assets/crew/image-douglas-hurley.png'
		},
		{
			role: 'MISSION SPECIALIST',
			name: 'MARK SHUTTLEWORTH',
			bio: 'Mark Richard Shuttleworth is the founder and CEO of Canonical, the company behind the Linux-based Ubuntu operating system. Shuttleworth became the first South African to travel to space as a space tourist.',
			image: './assets/crew/image-mark-shuttleworth.png'
		},
		{
			role: 'PILOT',
			name: 'VICTOR GLOVER',
			bio: 'Pilot on the first operational flight of the SpaceX Crew Dragon to the International Space Station. Glover is a commander in the U.S. Navy where he pilots an F/A-18.He was a crew member of Expedition 64, and served as a station systems flight engineer.',
			image: './assets/crew/image-victor-glover.png'
		},
		{
			role: 'FLIGHT ENGINEER',
			name: 'ANOUSHEH ANSARI',
			bio: 'Anousheh Ansari is an Iranian American engineer and co-founder of Prodea Systems. Ansari was the fourth self-funded space tourist, the first self-funded woman to fly to the ISS, and the first Iranian in space.',
			image: './assets/crew/image-anousheh-ansari.png'
		}
	];
	let activeIndex = 0;
	let activeCrew = crewData[activeIndex];

	const updateSelectedCrewMember = (index: number) => {
		activeIndex = index;
		activeCrew = crewData[activeIndex];
	};
</script>

<svelte:head>
	<title>Crew | Space Tourism App</title>
	<meta name="description" content="Crew Information page" />
</svelte:head>

<div class="main-container">
	<picture>
		<source media="(min-width: 900px)" srcset="./assets/crew/background-crew-desktop.jpg" />
		<img src="./assets/crew/background-crew-mobile.jpg" alt="background-img" class="bg-image" />
	</picture>

	<div>
		<h1 class="page-header-text"><span>02 </span>MEET YOUR CREW</h1>

		<div class="crew_profile">
			<h3 class="crew_rank">COMMANDER</h3>
			<h2 class="crew_member_name">Douglas Hurley</h2>
			<p class="crew_member_description">
				Douglas Gerald Hurley is an American engineer, former Marine Corps pilot and former NASA
				astronaut. He launched into space for the third time as commander of Crew Dragon Demo-2.
			</p>
		</div>

		<div class="crew-pagination">
			{#each crewData as _, index}
				<button 
               class={`${activeIndex === index && 'active'}`}
               on:click={() => updateSelectedCrewMember(index)}
            ></button>
			{/each}
		</div>
	</div>

	<div>
		<div class="crewImageContainer">
			<img src={activeCrew.image} alt={activeCrew.name} />
		</div>
	</div>
</div>

<style>
	.crewImageContainer {
		max-width: 500px;
		width: 100%;
		margin: 0 auto;
	}

	.crewImageContainer > img {
		aspect-ratio: 1;
		object-fit: contain;
	}

	.crew_rank {
		font-size: 32px;
		color: rgb(var(--color-primary));
		text-transform: uppercase;
	}

	.crew_member_name {
		font-size: 56px;
		text-transform: uppercase;
		margin-top: 2rem;
	}

	.crew_member_description {
		color: rgb(var(--color-tertiary));
		font-size: 18px;
		width: 80%;
	}

	.crew-pagination {
		display: flex;
		gap: 20px;
		margin-bottom: 3rem;
      margin-top: 2rem;
	}

	.crew-pagination > button {
		width: 15px;
		height: 15px;
		border-radius: 50%;
		background: rgb(var(--color-primary), 0.8);
	}

   .crew-pagination > button.active {
      background-color: rgb(var(--color-white));
   }

   @media screen and (max-width: 900px) {
      .crew_member_description {
         width: 100%;
      }

      .crew-pagination {
         justify-content: center;
      }

      .crew-pagination > button {
         height: 20px;
         width: 20px;
      }
   }
</style>

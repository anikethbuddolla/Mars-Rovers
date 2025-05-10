<script>
	import { photoResults } from '$lib/stores';
	let photos = [];
	photoResults.subscribe((data) => (photos = data));
</script>

<span style="display: inline-block; width: 100%; text-align: center;">
	<h1 class="heading-container">Results</h1>
</span>


{#if photos.length === 0}
	<p>No photos found.</p>
{:else}
	<div class="photo-grid">
		{#each photos as photo}
			<div class="photo-card">
				<img src={photo.img_src} alt="" />
				<p>
					Rover: {photo.rover?.name} <br />
					Camera: {photo.camera?.full_name} <br />
					Date: {photo.earth_date}
				</p>
			</div>
		{/each}
	</div>
{/if}

<style>
	.photo-grid {
		display: grid;
		grid-template-columns: repeat(3, 1fr);
		gap: 1.5em;
	}

	.photo-card img {
		width: 100%;
		height: auto;
		display: block;
		border-radius: 8px;
	}

	.photo-card {
		background: #fffbe7;
		padding: 1em;
		border-radius: 10px;
		border: 1px solid #f9d423;
		box-sizing: border-box;
		transition: transform 0.2s ease;
	}

	.photo-card:hover {
		transform: scale(1.02);
	}

	h1, h2, h3 {
    font-family: 'Orbitron', sans-serif;
    letter-spacing: 1px;
	padding: 1rem;          
    border-radius: 8px;     
    display: inline-block;   
    margin: 10 auto;
  }

</style>

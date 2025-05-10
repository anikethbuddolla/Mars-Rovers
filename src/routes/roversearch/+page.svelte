<script>
  import { photoResults } from '$lib/stores';
  import { goto } from '$app/navigation';

  const roverOptions = [
    { value: 'all', name: 'All Rovers' },
    { value: 'perseverance', name: 'Perseverance' },
    { value: 'curiosity', name: 'Curiosity' },
    { value: 'opportunity', name: 'Opportunity' },
    { value: 'spirit', name: 'Spirit' }
  ];

  const cameraOptions = [
    { value: 'all', name: 'All Cameras' },
    { value: 'FHAZ', name: 'Front Hazard Avoidance Camera' },
    { value: 'RHAZ', name: 'Rear Hazard Avoidance Camera' },
    { value: 'MAST', name: 'Mast Camera' },
    { value: 'CHEMCAM', name: 'Chemistry and Camera Complex' },
    { value: 'MAHLI', name: 'Mars Hand Lens Imager' },
    { value: 'MARDI', name: 'Mars Descent Imager' },
    { value: 'NAVCAM', name: 'Navigation Camera' },
    { value: 'PANCAM', name: 'Panoramic Camera' },
    { value: 'MINITES', name: 'Miniature Thermal Emission Spectrometer' }
  ];

  let selectedRover = 'all';
  let selectedCamera = 'all';
  let startDate = '';
  let endDate = '';

  function getLast7Days() {
    const today = new Date();
    const lastWeek = new Date(today);
    lastWeek.setDate(today.getDate() - 6);
    return {
      start: lastWeek.toISOString().split('T')[0],
      end: today.toISOString().split('T')[0]
    };
  }

  async function fetchPhotos() {
    let allPhotos = [];
    let rovers =
      selectedRover === 'all'
        ? ['perseverance', 'curiosity', 'opportunity', 'spirit']
        : [selectedRover];

    if (!startDate && !endDate) {
      for (const rover of rovers) {
        let url = `https://api.nasa.gov/mars-photos/api/v1/rovers/${rover}/latest_photos?api_key=${import.meta.env.VITE_NASA_API_KEY}`;
        if (selectedCamera !== 'all') {
          url += `&camera=${selectedCamera}`;
        }
        const res = await fetch(url);
        const data = await res.json();
        allPhotos = allPhotos.concat(data.latest_photos || []);
      }
      photoResults.set(allPhotos);
      goto('/results');
      return;
    }

    let { start, end } = { start: startDate, end: endDate };
    for (const rover of rovers) {
      let url = `https://api.nasa.gov/mars-photos/api/v1/rovers/${rover}/photos?api_key=${import.meta.env.VITE_NASA_API_KEY}`;
      url += `&earth_date=${end}`;
      if (selectedCamera !== 'all') {
        url += `&camera=${selectedCamera}`;
      }
      const res = await fetch(url);
      const data = await res.json();
      allPhotos = allPhotos.concat(data.photos || []);
    }
    photoResults.set(allPhotos);
    goto('/results');
  }
</script>


<h1 class="page-title">Mars Rover Photo Search</h1>


<form on:submit|preventDefault={fetchPhotos} class="form-container">
  <label class="form-label">
    Rover:
    <select bind:value={selectedRover} class="input-field">
      {#each roverOptions as rover}
        <option value={rover.value}>{rover.name}</option>
      {/each}
    </select>
  </label>

  <label class="form-label">
    Camera:
    <select bind:value={selectedCamera} class="input-field">
      {#each cameraOptions as camera}
        <option value={camera.value}>{camera.name}</option>
      {/each}
    </select>
  </label>

  <label class="form-label">
    Start Date:
    <input type="date" bind:value={startDate} class="input-field" />
  </label>

  <label class="form-label">
    End Date:
    <input type="date" bind:value={endDate} class="input-field" />
  </label>

  <button type="submit" class="submit-button">Search</button>
</form>


<p class="info-text">
  If you leave everything blank, you'll get the most recent photos from all rovers and all cameras
  (last 7 days).
</p>

<style>
  
  html, body {
    margin: 0;
    padding: 0;
    height: 100%;
    background: linear-gradient(135deg, #2a2a2a, #0e0e0e); 
    color: #ffffff;
    font-family: 'Arial', sans-serif;
  }

  h1.page-title {
    text-align: center;
    font-size: 3rem;
    color: #f26a5e; 
    margin-top: -0.0001rem;
    text-shadow: 2px 2px 5px rgba(0, 0, 0, 0.7);
  }

  
  .form-container {
    background-color: rgba(0, 0, 0, 0.7); 
    padding: 2rem;
    border-radius: 12px;
    box-shadow: 0px 4px 10px rgba(0, 0, 0, 0.5);
    max-width: 600px;
    margin: 3rem auto;
  }


  .form-label {
    display: block;
    font-size: 1.2rem;
    margin-bottom: 0.5rem;
    color: #ccc;
  }

  .input-field {
    width: 100%;
    padding: 0.8rem;
    border: 2px solid #4a4a4a;
    border-radius: 6px;
    font-size: 1rem;
    margin-bottom: 1.5rem;
    background-color: #333;
    color: #fff;
  }

  .input-field:focus {
    border-color: #f9a825; 
    outline: none;
  }

  .submit-button {
    background-color: #f26a5e; 
    color: white;
    padding: 1rem 2rem;
    border-radius: 8px;
    border: none;
    font-size: 1.2rem;
    cursor: pointer;
    transition: background-color 0.3s;
  }

  .submit-button:hover {
    background-color: #c4564b; 
  }

 
  .info-text {
    font-size: 1.4rem;
    color: #bbb;
    text-align: center;
    margin-top: 2rem;
	padding-top: 2rem;
  }
</style>

<script>
	
</script>

<nav class="top-nav">
  <a href="/">Home</a>
  <a href="/roversearch">RoverSearch</a>
</nav>

<main class="backgroundcolor">
	<slot />
</main>

<style>

.backgroundcolor {
	background: linear-gradient(to right, #3d2f27, #a4754f);
	height: 100vh;
    margin: 0;
    padding: 0;
}

.top-nav {
  position: sticky;
  top: 0;
  z-index: 1000;
  background: linear-gradient(to right, #1a1a1a, #111);
  padding: 1.5rem 3rem; 
  display: flex;
  gap: 3rem; 
  justify-content: flex-start;
  align-items: center;
  box-shadow: 0 2px 10px rgba(0, 0, 0, 0.4);
  font-family: 'Orbitron', sans-serif;
}

.top-nav a {
  color: #ff6f61;
  text-decoration: none;
  font-weight: bold;
  font-size: 1.2rem; 
  letter-spacing: 0.8px;
  transition: color 0.3s, transform 0.2s;
}

.top-nav a:hover {
  color: #ff3c2f;
  transform: scale(1.05);
}

.top-nav a:active {
  color: #fff;
}




	
	:global(h1),
	:global(h2),
	:global(h3) {
		color: #ff4e50;
	}

	
	:global(button) {
		background: #f9d423; 
		color: #fff; 
		border: none; 
		border-radius: 6px; 
		padding: 0.5em 1em; 
		font-size: 1em; 
		cursor: pointer; 
	}

	
	:global(button:hover) {
		background: #ff4e50;
	}
</style>

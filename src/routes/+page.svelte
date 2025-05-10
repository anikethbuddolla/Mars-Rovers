<script>

</script>


<div class="background-div">
  <div class="gray-box">
    <h1>Welcome<br>to the<br>Mars Rover</h1>
    <p>We display photos that are taken by the <br>Mars' Rovers</p>
  </div>
  <div class="scroll-down">
    <span>▼</span>
  </div>
</div>


<section class="info-section">
  <div class="content">
    <h2>Meet Perseverance</h2>
    <p>
      NASA's most advanced Mars rover is on a quest to uncover the secrets of ancient life.
      It traverses the dusty terrain of the Jezero Crater with cutting-edge instruments and a tiny helicopter by its side.
    </p>
  </div>
</section>


<section class="highlight-section">
  <div class="card">
    <h3>The Search for Ancient Life</h3>
    <p>Perseverance is searching for signs of ancient microbial life on Mars.</p>
  </div>
  <div class="card">
    <h3>Sample Collection</h3>
    <p>Drilling, caching, and storing pieces of Mars for a future return to Earth.</p>
  </div>
  <div class="card">
    <h3>Ingenuity</h3>
    <p>The first aircraft to fly on another world — a true Martian sidekick.</p>
  </div>
</section>


<footer class="footer">
  <h2>Ready to explore Mars?</h2>
  <p>Discover stunning views from the Red Planet and learn about the mission.</p>
  <a href="/roversearch" class="launch-button">Launch the Gallery</a>
</footer>

<style>
  
  @import url('https://fonts.googleapis.com/css2?family=Orbitron:wght@500&family=Roboto&display=swap');

  * {
    box-sizing: border-box;
    font-family: 'Roboto', sans-serif;
    scroll-behavior: smooth;
  }

  h1, h2, h3 {
    font-family: 'Orbitron', sans-serif;
    letter-spacing: 1px;
  }

  
  .background-div {
    position: relative;
    width: 100%;
    height: 100vh;
    background-image: url("rover.jpg");
    background-size: cover;
    background-position: center;
    background-repeat: no-repeat;
    overflow: hidden;
  }

  .gray-box {
    position: absolute;
    top: 0;
    left: 0;
    height: 100%;
    width: 50%;
    background: linear-gradient(
      to right,
      rgba(20, 20, 20, 0.95) 0%,
      rgba(50, 50, 50, 0.85) 60%,
      rgba(50, 50, 50, 0.3) 90%,
      rgba(50, 50, 50, 0) 100%
    );
    color: #fff;
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: flex-start;
    padding: 3rem;
  }

  .gray-box h1 {
    font-size: 5.5rem;
    margin: 0;
    color: #ff6f61;
  }

  .gray-box p {
    font-size: 1.4rem;
    color: #ddd;
    padding-top: 1.5rem;
    max-width: 90%;
  }

  .scroll-down {
    position: absolute;
    bottom: 30px;
    left: 50%;
    transform: translateX(-50%);
    font-size: 2rem;
    color: #ff6f61;
    animation: bounce 2s infinite;
  }

  @keyframes bounce {
    0%, 100% { transform: translateX(-50%) translateY(0); }
    50% { transform: translateX(-50%) translateY(10px); }
  }

  
.info-section {
  background: linear-gradient(to right, #5c1c0b, #7a2f16, #a34527);
  color: #fff;
  padding: 6rem 2rem;
  text-align: center;
}


  .info-section h2 {
    font-size: 2.8rem;
    margin-bottom: 1rem;
    color: #b63e2f;
  }

  .info-section p {
    max-width: 700px;
    margin: 0 auto;
    font-size: 1.2rem;
    line-height: 1.8;
  }

  
  .highlight-section {
    display: flex;
    flex-wrap: wrap;
    gap: 2rem;
    padding: 5rem 2rem;
    justify-content: center;
    background: linear-gradient(to right, #1a1a1a, #111);
    color: white;
  }

  .card {
    background: #2b2b2b;
    border: 1px solid #444;
    border-radius: 16px;
    padding: 2rem;
    width: 280px;
    box-shadow: 0 10px 30px rgba(255, 111, 97, 0.2);
    text-align: center;
    transition: transform 0.3s ease, box-shadow 0.3s ease;
  }

  .card:hover {
    transform: translateY(-8px);
    box-shadow: 0 15px 40px rgba(255, 111, 97, 0.4);
  }

  .card h3 {
    margin-bottom: 1rem;
    color: #ff6f61;
  }

  .card p {
    font-size: 1rem;
    line-height: 1.6;
    color: #ddd;
  }

  
  .footer {
    background: #000;
    color: #eee;
    text-align: center;
    padding: 5rem 2rem;
  }

  .footer h2 {
    font-size: 2.5rem;
    margin-bottom: 1rem;
    color: #ff6f61;
  }

  .footer p {
    font-size: 1.2rem;
    margin-bottom: 2rem;
    color: #ccc;
  }

  .footer a {
    background: #ff6f61;
    border: none;
    padding: 1rem 2rem;
    font-size: 1rem;
    color: white;
    border-radius: 8px;
    cursor: pointer;
    transition: background 0.3s ease, transform 0.2s;
  }

  .footer button:hover {
    background: #ff3c2f;
    transform: scale(1.05);
  }
</style>

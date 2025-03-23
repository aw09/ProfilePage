<script>
  import { onMount } from 'svelte';

  const messages = [
    'Hello . . .',
    'I am Agung Wicaksono',
    'I am a Backend Developer'
  ];

  let currentMessageIndex = 0;
  let displayedText = '';
  let currentCharIndex = 0;

  function typeText() {
    if (currentCharIndex < messages[currentMessageIndex].length) {
      displayedText += messages[currentMessageIndex][currentCharIndex];
      currentCharIndex++;
      setTimeout(typeText, 100);
    } else {
      setTimeout(() => {
        displayedText = '';
        currentCharIndex = 0;
        currentMessageIndex = (currentMessageIndex + 1) % messages.length;
        typeText();
      }, 2000);
    }
  }

  onMount(() => {
    typeText();
  });
</script>

<main>
  <div class="container">
    <h1>{displayedText}</h1>
    <div class="social-links">
      <a href="https://github.com/aw09" target="_blank" rel="noopener">GitHub</a>
      <a href="https://www.linkedin.com/in/agungw9" target="_blank" rel="noopener">LinkedIn</a>
    </div>
  </div>
</main>

<style>
  :global(body) {
    margin: 0;
    background-color: #1a1a1a;
    color: #ffffff;
    font-family: 'Inter', sans-serif;
  }

  main {
    height: 100vh;
    display: flex;
    justify-content: center;
    align-items: center;
    text-align: center;
  }

  .container {
    padding: 2rem;
  }

  h1 {
    font-size: 2.5rem;
    margin-bottom: 2rem;
    min-height: 3.75rem;
  }

  .social-links {
    display: flex;
    gap: 1rem;
    justify-content: center;
  }

  a {
    color: #64ffda;
    text-decoration: none;
    padding: 0.5rem 1rem;
    border: 1px solid #64ffda;
    border-radius: 4px;
    transition: all 0.3s ease;
  }

  a:hover {
    background-color: rgba(100, 255, 218, 0.1);
  }
</style>
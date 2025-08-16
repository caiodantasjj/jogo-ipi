<script lang="ts">
  import { onMount } from "svelte";

  // Funções recebidas via props para troca de telas
  export let aoSelecionarDificuldade: (nivel: 'facil' | 'medio' | 'dificil') => void;
  export let aoAbrirSobre: () => void;

  // Estado de dificuldade selecionada
  let dificuldade: 'facil' | 'medio' | 'dificil' | '' = '';

  // Inicia o jogo caso uma dificuldade tenha sido escolhida
  function jogar() {
    if (!dificuldade) {
      alert("Escolha uma dificuldade antes de jogar!");
      return;
    }
    aoSelecionarDificuldade(dificuldade);
  }

  // Gera um grid de letras aleatórias para o fundo
  function generateWordGrid() {
    const grid = document.getElementById('wordGrid');
    const letters = 'ABCDEFGHIJKLMNOPQRSTUVWXYZ';
    for (let i = 0; i < 64; i++) {
      const cell = document.createElement('div');
      cell.className = 'grid-cell';
      cell.textContent = letters[Math.floor(Math.random() * letters.length)];
      grid.appendChild(cell);
    }
  }

  // Executa após o carregamento do componente
  onMount(() => {
    generateWordGrid();

    const difficultySelect = document.getElementById('difficultySelect') as HTMLSelectElement;
    const playButton = document.getElementById('playButton') as HTMLButtonElement;

    // Habilita/desabilita botão de jogar conforme seleção
    difficultySelect.addEventListener('change', function() {
      playButton.disabled = !this.value;
    });
  });
</script>

<!-- Padrão de fundo -->
<div class="bg-pattern">
  <div class="bg-shape bg-shape-1"></div>
  <div class="bg-shape bg-shape-2 square"></div>
  <div class="bg-shape bg-shape-3"></div>
  <div class="bg-shape bg-shape-4 square"></div>
  <div class="bg-shape bg-shape-5"></div>
  <div class="bg-shape bg-shape-6 square"></div>

  <!-- Grade de obj aleatórios para efeito visual -->
  <div class="word-grid" id="wordGrid"></div>
</div>

<!-- Conteúdo principal -->
<div class="container">

  <!-- Logo e título -->
  <div class="logo">
    <h1>CAÇA</h1>
    <h1>PALAVRAS</h1>
    <div class="logo-subtitle">
      <span>Encontre as palavras escondidas!</span>
    </div>
  </div>

  <!-- Controles do jogo -->
  <div class="game-controls">
    
    <!-- Seleção de dificuldade -->
    <div class="difficulty-section">
      <label class="difficulty-label">Escolha o seu nível de desafio</label>
      <div class="select-wrapper">
        <select class="select" id="difficultySelect" bind:value={dificuldade}>
          <option value="">Selecione a dificuldade</option>
          <option value="facil">🟢 Fácil - 12x12 Grid</option>
          <option value="medio">🟡 Médio - 12x12 Grid</option>
          <option value="dificil">🔴 Difícil - 12x12 Grid</option>
        </select>
        <span class="select-arrow">▼</span>
      </div>
    </div>

    <!-- Botão jogar -->
    <button class="play-button" id="playButton" disabled on:click={jogar}>
      🎮 JOGAR! 🎮
    </button>

    <!-- Botão sobre -->
    <button class="about-button" id="aboutButton" on:click|preventDefault={aoAbrirSobre}>
      Sobre o jogo
    </button>
  </div>

  <!-- Texto de incentivo -->
  <div class="fun-stats">
    <p>Desafie-se a encontrar todas as palavras escondidas!</p>
    <p class="subtitle">As palavras podem ser horizontais, verticais ou diagonais</p>
  </div>
</div>

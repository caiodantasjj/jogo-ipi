<script lang="ts">
  export let aoVoltar: () => void;
</script>

<!-- Padrão de fundo -->
<div class="bg-pattern">
    <div class="bg-shape bg-shape-1"></div>
    <div class="bg-shape bg-shape-2 square"></div>
    <div class="bg-shape bg-shape-3"></div>
    <div class="bg-shape bg-shape-4 square"></div>
    <div class="bg-shape bg-shape-5"></div>
    <div class="bg-shape bg-shape-6 square"></div>
</div>

<!-- Conteúdo principal -->
<div class="container-sobre">
    <!-- Cabeçalho -->
    <div class="header">
        <h1>SOBRE O CAÇA PALAVRAS</h1>
        <p class="header-subtitle">Descubra a história por trás da nossa aventura de caça-palavras</p>
    </div>

    <!-- Visão geral do projeto -->
    <div class="content-card">
        <h2>O que é o Caça Palavras</h2>
        <p>Este jogo de Caça-Palavras foi desenvolvido como parte de um projeto acadêmico, proposto pelo professor Alan, na disciplina de Desenvolvimento de Aplicações Web, no Instituto Federal de Pernambuco – Campus Igarassu.</p>
        
        <div class="highlight-box">
            <p>O objetivo foi criar um jogo ...</p>
        </div>
    </div>

    <!-- Filosofia de design -->
    <div class="content-card">
        <h2>Autores:</h2>
        <ul>
            <li>Caio</li>
            <li>Elioenai</li>
            <li>Randson</li>
            <li>Eloísa</li>
            <li>Kevelin</li>
        </ul>
        <p>Com colaboração e orientação do professor Alan.</p>
    </div>

    <!-- Chamada para ação -->
    <div class="content-card" style="text-align: center;">
        <h2>Pronto para jogar?</h2>
        <p>Experimente você mesmo a diferença do Caça Palavras. Desafie sua mente, aprecie o belo design e descubra por que nossa abordagem no desenvolvimento web cria jogos melhores para todos.</p>
        
        <a href="#" class="nav-button" on:click|preventDefault={aoVoltar}>← Voltar ao jogo</a>
    </div>
</div>

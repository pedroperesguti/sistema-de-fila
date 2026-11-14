# Circuito Faísca: plano do jogo

Jogo de corrida de kart **mobile**, jogado no navegador do celular (sem instalar nada), contra 7 bots.

## Por que web e não app nativo
Todo o desenvolvimento e o teste acontecem pelo celular: o jogo abre por um link. Um app de loja (Android/iOS) exigiria computador para compilar. Mais tarde dá para empacotar a mesma base (Capacitor ou PWA) se for preciso publicar na Google Play.

## Stack
- HTML + JavaScript em um único arquivo (`jogo/circuito-faisca.html`; `index.html` é a versão com cabeçalho completo)
- Three.js 0.160 (3D low-poly) via CDN
- Física arcade própria (sem motor de física)

## O que já está pronto (MVP)
- Pista em spline fechada (~1066 m) com zebras, terra, muro, árvores e pórtico de chegada
- Física arcade: aceleração automática, aderência lateral, terra reduz velocidade, drift com carga (azul/laranja) e turbo
- 7 bots com IA:
  - seguem uma linha de corrida (pure pursuit) que corta por dentro das curvas
  - controlam a velocidade pela curvatura à frente (frenagem antecipada)
  - desviam e ultrapassam karts mais lentos
  - personalidade (ruído, viés de linha, agressividade)
  - rubber-banding leve por dificuldade
  - recuperação (ré quando presos; reposiciona se ficarem presos ou na contramão)
- Dificuldades Fácil, Médio e Difícil
- Corrida de 3 voltas: checkpoints anti-atalho, ranking ao vivo, melhor volta, resultado e recorde salvo no aparelho
- Controles de toque: botões ◀ ▶ ou "arrastar"; FREIO/ré; DRIFT; ajuda na direção opcional; teclado no PC
- HUD: posição, volta, tempo, minimapa, velocímetro e barra de carga do drift
- Som de motor e efeitos (Web Audio), vibração, pausa automática ao sair do app

## Testes feitos
Simulação sem tela de corridas completas (o jogador em piloto automático), 2 por dificuldade: todos os 8 karts terminam as 3 voltas, sem respawns nem batidas no muro. Corrida de ~2 min.

## Próximos passos
1. Ajustar a sensação dos controles a partir do teste no celular
2. Itens originais (turbo, mancha de óleo, escudo)
3. Mais pistas e modo campeonato
4. Escolha de kart/cor
5. PWA (ícone na tela inicial, offline) e, se quiser, versão na Google Play

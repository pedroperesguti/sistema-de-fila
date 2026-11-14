# Circuito Faísca: plano do jogo

Jogo de corrida de kart **mobile**, jogado no navegador do celular (sem instalar nada), contra 7 bots.

## Por que web e não app nativo
Todo o desenvolvimento e o teste acontecem pelo celular: o jogo abre por um link. Um app de loja (Android/iOS) exigiria computador para compilar. Mais tarde dá para empacotar a mesma base (Capacitor ou PWA) se for preciso publicar na Google Play.

## Stack
- HTML + JavaScript em um único arquivo (`jogo/circuito-faisca.html`; `index.html` é a versão com cabeçalho completo)
- Three.js 0.160 (3D low-poly) via CDN
- Física de kart própria, em unidades reais (sem motor de física)

## O que já está pronto (MVP)
- Pista em spline fechada (~1066 m) com zebras, terra, muro, árvores e pórtico de chegada
- Física realista (sem drift nem turbo):
  - kart 125cc: 165 kg, ~9,5 kW, máxima ~104 km/h, arrasto aerodinâmico e resistência de rolagem
  - pneus com limite de aderência (~1,4 G) no círculo de atrito: frear em curva tira aderência lateral
  - direção em modelo de bicicleta; entrar rápido demais faz o kart sair de frente
  - grama/brita: pouca aderência e muita resistência
  - freio ~1,1 G, ré lenta, batidas no muro tiram quase toda a velocidade
- 7 bots com IA:
  - seguem uma linha de corrida (pure pursuit) que corta por dentro das curvas
  - controlam a velocidade pela curvatura à frente (frenagem antecipada)
  - desviam e ultrapassam karts mais lentos
  - personalidade (ruído, viés de linha, agressividade)
  - sem trapaça (sem rubber-banding): mesmo kart do jogador; a dificuldade muda o quanto exploram o pneu e onde freiam
  - recuperação (ré quando presos; reposiciona se ficarem presos ou na contramão)
- Dificuldades Fácil, Médio e Difícil
- Corrida de 3 voltas: checkpoints anti-atalho, ranking ao vivo, melhor volta, resultado e recorde salvo no aparelho
- Controles de toque: botões ◀ ▶ ou "arrastar"; ACELERAR e FREIO/ré; opções "acelerar sozinho" e "ajuda na direção"; teclado no PC
- HUD: posição, volta, tempo, minimapa, velocímetro e medidor de aderência (G, derrapando, saindo de frente)
- Som de motor e efeitos (Web Audio), vibração, pausa automática ao sair do app

## Testes feitos
Simulação sem tela de corridas completas (o jogador em piloto automático), 2 por dificuldade: todos os 8 karts terminam as 3 voltas, sem respawns nem batidas no muro. Voltas de ~41 s (Difícil) a ~46 s (Fácil); corrida de ~2 min 15 s.

## Próximos passos
1. Ajustar a sensação dos controles a partir do teste no celular
2. Mais realismo: pista emborrachada, desgaste e temperatura dos pneus, peso do piloto
3. Mais pistas e modo campeonato
4. Escolha de kart/cor
5. PWA (ícone na tela inicial, offline) e, se quiser, versão na Google Play

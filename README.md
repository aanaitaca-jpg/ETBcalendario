

<html lang="pt-BR">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>📅 Calendário Editorial Maio — Escape Time Brasil</title>
<link href="https://fonts.googleapis.com/css2?family=Bebas+Neue&family=Rajdhani:wght@400;600;700&family=Space+Mono:wght@400;700&display=swap" rel="stylesheet">
<style>
  :root {
    --red: #E8001D;
    --red-dark: #A3001A;
    --gold: #FFB800;
    --dark: #0A0A0A;
    --dark2: #121212;
    --dark3: #1A1A1A;
    --dark4: #222222;
    --gray: #888;
    --white: #F5F5F0;
    --done-bg: #0d2a1a;
    --done-border: #1f6b38;
    --done-text: #4ade80;
  }

  * { margin: 0; padding: 0; box-sizing: border-box; }

  body {
    background: var(--dark);
    color: var(--white);
    font-family: 'Rajdhani', sans-serif;
    min-height: 100vh;
    overflow-x: hidden;
  }

  /* HEADER */
  header {
    background: var(--dark2);
    border-bottom: 3px solid var(--red);
    padding: 24px 32px;
    display: flex;
    align-items: center;
    gap: 20px;
    position: sticky;
    top: 0;
    z-index: 100;
    box-shadow: 0 4px 40px rgba(232,0,29,0.2);
  }

  .logo-area { display: flex; flex-direction: column; }
  .logo-area .brand {
    font-family: 'Bebas Neue', sans-serif;
    font-size: 2rem;
    color: var(--red);
    letter-spacing: 3px;
    line-height: 1;
  }
  .logo-area .sub {
    font-size: 0.75rem;
    color: var(--gray);
    letter-spacing: 4px;
    text-transform: uppercase;
    font-family: 'Space Mono', monospace;
  }

  .header-stats {
    margin-left: auto;
    display: flex;
    gap: 24px;
    align-items: center;
  }

  .stat-box {
    text-align: center;
    background: var(--dark3);
    border: 1px solid var(--dark4);
    padding: 8px 16px;
    border-radius: 4px;
  }
  .stat-box .num {
    font-family: 'Bebas Neue', sans-serif;
    font-size: 1.8rem;
    line-height: 1;
  }
  .stat-box .lbl {
    font-size: 0.65rem;
    color: var(--gray);
    letter-spacing: 2px;
    text-transform: uppercase;
  }
  #countDone .num { color: var(--done-text); }
  #countPending .num { color: var(--gold); }
  #countTotal .num { color: var(--red); }

  /* PROGRESS BAR */
  .progress-bar-wrap {
    background: var(--dark3);
    border-bottom: 1px solid #222;
    padding: 10px 32px;
    display: flex;
    align-items: center;
    gap: 16px;
  }
  .progress-label {
    font-size: 0.7rem;
    color: var(--gray);
    letter-spacing: 2px;
    font-family: 'Space Mono', monospace;
    white-space: nowrap;
  }
  .progress-track {
    flex: 1;
    height: 6px;
    background: var(--dark4);
    border-radius: 3px;
    overflow: hidden;
  }
  .progress-fill {
    height: 100%;
    background: linear-gradient(90deg, var(--red), var(--gold));
    border-radius: 3px;
    transition: width 0.5s ease;
    width: 0%;
  }
  .progress-pct {
    font-family: 'Bebas Neue', sans-serif;
    font-size: 1rem;
    color: var(--gold);
    min-width: 40px;
    text-align: right;
  }

  /* FILTERS */
  .filters {
    padding: 20px 32px;
    display: flex;
    gap: 10px;
    flex-wrap: wrap;
    align-items: center;
  }
  .filter-label {
    font-size: 0.7rem;
    color: var(--gray);
    letter-spacing: 3px;
    font-family: 'Space Mono', monospace;
    margin-right: 4px;
  }
  .filter-btn {
    background: var(--dark3);
    border: 1px solid #333;
    color: var(--gray);
    padding: 6px 16px;
    font-family: 'Rajdhani', sans-serif;
    font-size: 0.85rem;
    font-weight: 600;
    letter-spacing: 1px;
    cursor: pointer;
    border-radius: 2px;
    text-transform: uppercase;
    transition: all 0.2s;
  }
  .filter-btn:hover { border-color: var(--red); color: var(--white); }
  .filter-btn.active { background: var(--red); border-color: var(--red); color: #fff; }

  /* GRID */
  .grid {
    display: grid;
    grid-template-columns: repeat(auto-fill, minmax(340px, 1fr));
    gap: 20px;
    padding: 0 32px 40px;
  }

  /* CARD */
  .card {
    background: var(--dark2);
    border: 1px solid #2a2a2a;
    border-radius: 6px;
    overflow: hidden;
    transition: transform 0.2s, border-color 0.2s, box-shadow 0.2s;
    position: relative;
  }
  .card:hover {
    transform: translateY(-4px);
    border-color: #444;
    box-shadow: 0 12px 40px rgba(0,0,0,0.5);
  }
  .card.done {
    border-color: var(--done-border) !important;
    background: var(--done-bg);
  }
  .card.done:hover {
    box-shadow: 0 12px 40px rgba(31,107,56,0.2);
  }
  .card.hidden { display: none; }

  /* DONE STAMP */
  .done-stamp {
    display: none;
    position: absolute;
    top: 12px;
    right: 12px;
    background: var(--done-text);
    color: #000;
    font-family: 'Space Mono', monospace;
    font-size: 0.6rem;
    font-weight: 700;
    padding: 3px 8px;
    border-radius: 2px;
    letter-spacing: 2px;
    z-index: 5;
  }
  .card.done .done-stamp { display: block; }

  /* CARD IMAGE AREA */
  .card-image-area {
    background: var(--dark3);
    height: 180px;
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: center;
    position: relative;
    overflow: hidden;
    border-bottom: 1px solid #2a2a2a;
  }
  .card-image-area::before {
    content: '';
    position: absolute;
    inset: 0;
    background: linear-gradient(135deg, rgba(232,0,29,0.05) 0%, transparent 60%);
  }
  .card-image-icon {
    font-size: 3.5rem;
    margin-bottom: 8px;
    display: block;
    filter: grayscale(0.3);
  }
  .card-image-label {
    font-size: 0.65rem;
    color: var(--gray);
    letter-spacing: 3px;
    text-transform: uppercase;
    font-family: 'Space Mono', monospace;
  }
  .card-image-prompt {
    font-size: 0.7rem;
    color: #555;
    text-align: center;
    padding: 0 16px;
    margin-top: 4px;
    font-style: italic;
  }

  /* CARD HEADER */
  .card-header {
    padding: 14px 16px 10px;
    display: flex;
    align-items: flex-start;
    gap: 12px;
  }
  .day-badge {
    background: var(--red);
    color: #fff;
    font-family: 'Bebas Neue', sans-serif;
    font-size: 1.4rem;
    line-height: 1;
    padding: 4px 10px;
    border-radius: 3px;
    flex-shrink: 0;
    min-width: 46px;
    text-align: center;
  }
  .card.done .day-badge { background: var(--done-text); color: #000; }
  .card-meta { flex: 1; }
  .card-weekday {
    font-size: 0.65rem;
    color: var(--gold);
    letter-spacing: 3px;
    text-transform: uppercase;
    font-family: 'Space Mono', monospace;
  }
  .card-theme {
    font-family: 'Bebas Neue', sans-serif;
    font-size: 1.1rem;
    color: var(--white);
    letter-spacing: 1px;
    line-height: 1.2;
    margin-top: 2px;
  }

  /* CARD BODY */
  .card-body { padding: 0 16px 12px; }

  .section-label {
    font-size: 0.6rem;
    letter-spacing: 3px;
    text-transform: uppercase;
    font-family: 'Space Mono', monospace;
    margin-bottom: 5px;
    margin-top: 10px;
  }
  .section-label.red { color: var(--red); }
  .section-label.gold { color: var(--gold); }
  .section-label.green { color: var(--done-text); }

  .cta-text {
    font-size: 1rem;
    font-weight: 700;
    color: var(--white);
    line-height: 1.4;
    border-left: 3px solid var(--red);
    padding-left: 10px;
  }
  .card.done .cta-text { border-color: var(--done-text); }

  .caption-box {
    background: var(--dark3);
    border-radius: 4px;
    padding: 10px;
    font-size: 0.82rem;
    color: #ccc;
    line-height: 1.6;
    white-space: pre-wrap;
    word-break: break-word;
  }
  .hashtags {
    color: #4a9eff;
    font-size: 0.78rem;
    margin-top: 6px;
    line-height: 1.7;
    word-break: break-word;
  }
  .hashtags .cta-hash {
    color: var(--gold);
    font-weight: 700;
    display: block;
    margin-top: 4px;
    font-size: 0.85rem;
  }

  /* CHECKBOX */
  .card-footer {
    padding: 10px 16px 14px;
    border-top: 1px solid #2a2a2a;
    display: flex;
    align-items: center;
    gap: 10px;
  }
  .card.done .card-footer { border-color: #1f3a28; }

  .check-label {
    display: flex;
    align-items: center;
    gap: 10px;
    cursor: pointer;
    user-select: none;
    flex: 1;
  }
  .check-label input[type="checkbox"] { display: none; }
  .check-box {
    width: 22px;
    height: 22px;
    border: 2px solid #444;
    border-radius: 3px;
    display: flex;
    align-items: center;
    justify-content: center;
    transition: all 0.2s;
    flex-shrink: 0;
  }
  .check-label:hover .check-box { border-color: var(--red); }
  .card.done .check-box {
    background: var(--done-text);
    border-color: var(--done-text);
  }
  .check-box .tick { display: none; font-size: 13px; }
  .card.done .check-box .tick { display: block; }

  .check-text {
    font-size: 0.8rem;
    color: var(--gray);
    font-family: 'Space Mono', monospace;
    letter-spacing: 1px;
  }
  .card.done .check-text { color: var(--done-text); }

  /* SECTION HEADERS */
  .week-header {
    padding: 20px 32px 8px;
    display: flex;
    align-items: center;
    gap: 16px;
  }
  .week-header .week-label {
    font-family: 'Bebas Neue', sans-serif;
    font-size: 1.5rem;
    color: var(--red);
    letter-spacing: 3px;
  }
  .week-header::after {
    content: '';
    flex: 1;
    height: 1px;
    background: linear-gradient(90deg, #333 0%, transparent 100%);
  }

  /* FOOTER */
  footer {
    text-align: center;
    padding: 24px;
    border-top: 1px solid #1a1a1a;
    color: #444;
    font-size: 0.7rem;
    letter-spacing: 2px;
    font-family: 'Space Mono', monospace;
  }

  @media (max-width: 600px) {
    header { padding: 16px; flex-wrap: wrap; }
    .grid { grid-template-columns: 1fr; padding: 0 16px 32px; }
    .filters { padding: 12px 16px; }
    .week-header { padding: 16px 16px 6px; }
    .progress-bar-wrap { padding: 10px 16px; }
    .header-stats { gap: 10px; }
    .stat-box { padding: 6px 10px; }
  }
</style>
</head>
<body>

<header>
  <div style="font-size:2rem; line-height:1;">🔐</div>
  <div class="logo-area">
    <div class="brand">ESCAPE TIME BRASIL</div>
    <div class="sub">Calendário Editorial · Maio 2025 · Reels</div>
  </div>
  <div class="header-stats">
    <div class="stat-box" id="countDone"><div class="num">0</div><div class="lbl">Feitos</div></div>
    <div class="stat-box" id="countPending"><div class="num">27</div><div class="lbl">Pendentes</div></div>
    <div class="stat-box" id="countTotal"><div class="num">27</div><div class="lbl">Total</div></div>
  </div>
</header>

<div class="progress-bar-wrap">
  <span class="progress-label">PROGRESSO</span>
  <div class="progress-track"><div class="progress-fill" id="progressFill"></div></div>
  <span class="progress-pct" id="progressPct">0%</span>
</div>

<div class="filters">
  <span class="filter-label">FILTRAR:</span>
  <button class="filter-btn active" onclick="filter('all', this)">Todos (27)</button>
  <button class="filter-btn" onclick="filter('pending', this)">Pendentes</button>
  <button class="filter-btn" onclick="filter('done', this)">Concluídos</button>
</div>

<div id="postsContainer"></div>

<footer>ESCAPE TIME BRASIL — CALENDÁRIO EDITORIAL MAIO 2025 — FORMATO REELS</footer>

<script>
const STORAGE_KEY = 'escapetime_maio2025_v2';

// Dia 5 = Segunda, 6 = Terça, 7 = Quarta, 8 = Quinta, 9 = Sexta, 10 = Sábado, 11 = Domingo...
const weekdayMap = {
  5:'Segunda',6:'Terça',7:'Quarta',8:'Quinta',9:'Sexta',10:'Sábado',11:'Domingo',
  12:'Segunda',13:'Terça',14:'Quarta',15:'Quinta',16:'Sexta',17:'Sábado',18:'Domingo',
  19:'Segunda',20:'Terça',21:'Quarta',22:'Quinta',23:'Sexta',24:'Sábado',25:'Domingo',
  26:'Segunda',27:'Terça',28:'Quarta',29:'Quinta',30:'Sexta',31:'Sábado'
};

const posts = [
  {
    day: 5, icon: '🔐', theme: 'Segunda: O Desafio Começa Agora',
    imageDesc: 'Porta de escape room misteriosa com countdown',
    cta: 'Você tem coragem de entrar numa sala e descobrir se consegue escapar em 60 minutos? 🕐',
    caption: `Segunda-feira com adrenalina? Aqui sim! 🔐\n\nNa Escape Time Brasil, a diversão começa quando a porta fecha. Equipe unida, raciocínio afiado e adrenalina nos 60 minutos mais intensos da sua vida.\n\nCada sala é uma história diferente. Cada desafio, uma experiência única. Será que você tem o que é preciso para escapar?`,
    hashtags: `#EscapeTimeBrasil #EscapeRoom #JogosDeFuga #SãoPaulo #AventuraEmSP #DesafioEmEquipe #EscapeRoomSP #ExperiênciaÚnica #Maio2025`
  },
  {
    day: 6, icon: '🎭', theme: 'Spotlight: Jogos Mortais',
    imageDesc: 'Cenografia da sala Jogos Mortais, estilo sombrio',
    cta: 'Quer jogar um jogo? Mas atenção: aqui as regras são diferentes…',
    caption: `🎭 SALA EM DESTAQUE: JOGOS MORTAIS\n\nInspirando no universo mais sombrio do cinema, essa sala vai testar não só seu raciocínio, mas também seus nervos.\n\nCom cenografia imersiva e desafios que parecem reais, você vai questionar tudo que sabe sobre trabalho em equipe.\n\nNível de dificuldade: INTENSO. Coragem necessária: MUITA.`,
    hashtags: `#EscapeTimeBrasil #JogosMortais #EscapeRoom #SalaDeEscape #TerroreAventura #EscapeRoomSP #ExperiênciaImersiva #Saw`
  },
  {
    day: 7, icon: '💪', theme: 'Work Hard, Escape Harder',
    imageDesc: 'Pessoa resolvendo código em painel futurista',
    cta: 'Seu time é unido no trabalho? Prove isso aqui — onde a pressão é real!',
    caption: `O melhor team building da cidade não acontece em sala de reunião. 💪\n\nAcontece quando a pressão bate, o relógio corre e só a comunicação real salva o grupo.\n\nEscape Time é o lugar onde líderes se revelam e equipes se fortalecem. Ideal pra empresas que querem resultados de verdade.`,
    hashtags: `#EscapeTimeBrasil #TeamBuilding #EscapeRoomCorporativo #EquipeUnida #DinâmicaDeGrupo #EscapeRoomEmpresa #LiderançaNaPrática #EscapeRoom`
  },
  {
    day: 8, icon: '🌙', theme: 'Noite de Mistério',
    imageDesc: 'Corredor escuro com uma luz no final, atmosfera noir',
    cta: 'O que acontece quando as luzes piscam e o relógio começa? Você não vai querer perder!',
    caption: `Noite de quinta e a agenda tá vazia? Que tal preencher com muita adrenalina? 🌙\n\nNossas salas têm atmosfera cinematográfica. Cada detalhe foi pensado pra você se sentir dentro de um filme.\n\nVenha com quem você confia — porque lá dentro, confiança é tudo.`,
    hashtags: `#EscapeTimeBrasil #NoiteDeEscape #EscapeRoomNoturno #AventuraNoturna #EscapeRoomSP #JogosDeEscape #MistérioEAdrenalina #SãoPaulo`
  },
  {
    day: 9, icon: '🏆', theme: 'Você Consegue Escapar?',
    imageDesc: 'Trofeu estilizado com chave de escape',
    cta: 'Apenas 40% das equipes conseguem escapar. Sua turma vai ser a exceção?',
    caption: `A estatística não mente: escapar não é pra qualquer um. 🏆\n\nMas pra quem consegue, a sensação é inesquecível. Aquele grito de vitória quando a última fechadura abre… não tem preço.\n\nPrepara a equipe, vem pra Escape Time e prova que vocês têm o que é preciso!`,
    hashtags: `#EscapeTimeBrasil #Vitória #EscapeRoom #DesafioCumprido #JogosDeFuga #EscapeRoomSP #SensaçãoDeVitória #AventuraEmSP`
  },
  {
    day: 10, icon: '🎯', theme: 'Sábado de Ação Total',
    imageDesc: 'Closeup de mãos resolvendo mecanismo secreto',
    cta: 'Sábado pedindo emoção? A gente tem 60 minutos de pura intensidade esperando por você!',
    caption: `Qual é o nível de dificuldade que você topa? 🎯\n\nTemos salas pra todos os perfis — do iniciante curioso ao veteran que acha que sabe tudo (spoiler: a gente muda isso).\n\nEscolhe sua sala, monta seu time e aparece. A experiência mais intensa de SP tá te esperando!`,
    hashtags: `#EscapeTimeBrasil #SábadoDeAção #EscapeRoom #NíveisDeDesafio #JogosDeFuga #EscapeRoomBrasil #DivertidoEmSP #AventuraSP`
  },
  {
    day: 11, icon: '🌅', theme: 'Domingo Diferente',
    imageDesc: 'Grupo sorrindo com foto na saída da sala — celebrando',
    cta: 'Domingo diferente começa com uma boa história pra contar na segunda!',
    caption: `Imagina chegar na segunda com essa história: "Escapamos do Asylum em 47 minutos!" 🌅\n\nNossa missão é criar memórias que durem mais que um fim de semana.\n\nReserva agora — domingos estão voando! Link na bio.`,
    hashtags: `#EscapeTimeBrasil #DomingoDeAventura #EscapeRoom #MemóriasInesquecíveis #DiversãoGarantida #EscapeRoomSP #ExperiênciaÚnica #SãoPauloTemTudo`
  },
  {
    day: 12, icon: '🔑', theme: 'A Chave Está Com Você',
    imageDesc: 'Chave antiga em close, fundo escuro dramático',
    cta: 'A chave pra sair não é física. É o seu raciocínio — você está preparado?',
    caption: `Em cada sala, existe uma chave. Mas ela nunca está onde você espera. 🔑\n\nA Escape Time foi construída pra te desafiar de formas que você nunca imaginou. Pistas ocultas, mecanismos únicos, narrativas envolventes.\n\nÉ mais que um jogo. É uma jornada.`,
    hashtags: `#EscapeTimeBrasil #EscapeRoom #AChaveDaFuga #PistasEEnigmas #JogosDeFuga #EscapeRoomSP #ImerssãoTotal #BrooklimSP`
  },
  {
    day: 13, icon: '🎬', theme: 'Cinema Não, Escape Sim!',
    imageDesc: 'Comparativo: tela de cinema vs. porta de escape room',
    cta: 'Por que assistir quando você pode VIVER a história?',
    caption: `Cinema é passivo. Escape Room é você dentro da história! 🎬\n\nCada sala da Escape Time tem roteiro, cenografia e desafios pensados como uma experiência cinematográfica — só que você é o protagonista.\n\nEsquece o capim. Aqui a emoção é real e o final depende de você.`,
    hashtags: `#EscapeTimeBrasil #EscapeVsCinema #EscapeRoom #ProtagonistaDaHistória #ExperiênciaImersiva #JogosDeFuga #EscapeRoomSP #DivertidoEmSP`
  },
  {
    day: 14, icon: '❤️', theme: 'Date Night Épico',
    imageDesc: 'Casal dentro de sala temática, expressão de surpresa e diversão',
    cta: 'Jantar a dois é bonito mas escape room a dois é ÉPICO!',
    caption: `Cansou do roteiro jantar + cinema? 😏\n\nUm escape room a dois é a melhor forma de descobrir se o crush aguenta pressão — e se vocês se entendem quando o bicho pega!\n\nDate diferente, história pra contar e risadas garantidas. Vem!`,
    hashtags: `#EscapeTimeBrasil #DateNight #NamoradoNoEscape #CaféComAdrenalina #EscapeRoomCasal #DiversãoADois #EscapeRoomSP #RomanceCom60Min`
  },
  {
    day: 15, icon: '🎉', theme: 'Meio de Mês: Check-in Especial',
    imageDesc: 'Confete e número 15 estilizado com chaves ao redor',
    cta: 'Metade de maio e você ainda não veio pra Escape Time? Isso é urgente!',
    caption: `Meio de maio já! 🎉 Quantas aventuras você teve até agora?\n\nSe a resposta for "poucas", a gente tem a solução. Múltiplas salas, diferentes níveis de dificuldade, experiências que ficam na memória.\n\nNão termina esse mês sem uma visita. Promete?`,
    hashtags: `#EscapeTimeBrasil #MeioDeMaio #EscapeRoom #CheckInDeAventura #JogosDeFuga #EscapeRoomSP #Maio2025 #SãoPaulo`
  },
  {
    day: 16, icon: '🚀', theme: 'Spotlight: Missão Espacial',
    imageDesc: 'Cenário espacial futurista com painéis de controle',
    cta: 'Você tem o que é preciso para salvar a humanidade em 60 minutos?',
    caption: `🚀 SALA EM DESTAQUE: MISSÃO ESPACIAL — RESGATE NA LUA\n\nA tripulação está em perigo. Os sistemas falharam. A missão é sua agora.\n\nCom tecnologia de ponta e cenografia impressionante, essa sala vai fazer você sentir que realmente está no espaço.\n\nFácil? Não. Inesquecível? Garantido.`,
    hashtags: `#EscapeTimeBrasil #MissãoEspacial #EscapeRoom #NaLua #EscapeRoomFuturista #ExperiênciaEspacial #EscapeRoomSP #Sci-FiEscape`
  },
  {
    day: 17, icon: '🧩', theme: 'Sábado de Quebra-Cabeça',
    imageDesc: 'Mão montando puzzle, vista aérea dramática',
    cta: 'Sábado é dia de testar o limite do seu cérebro. Você aceita o desafio?',
    caption: `Nada de tela, nada de passividade. Sábado na Escape Time é ATIVO! 🧩\n\nSeu cérebro vai trabalhar como nunca. Conexões, raciocínio lateral, comunicação sob pressão.\n\nO melhor: você vai se divertir tanto que nem vai perceber como é estimulante!`,
    hashtags: `#EscapeTimeBrasil #SábadoInteligente #EscapeRoom #QuebragAcabeça #JogosDeFuga #CérebroEmAção #EscapeRoomSP #DivertidoESaudável`
  },
  {
    day: 18, icon: '🏰', theme: 'Domingo Medieval',
    imageDesc: 'Sala Quarto 66, estética templária, tochas e pedras',
    cta: 'Volte no tempo sem sair de SP — os Templários guardam segredos que só você pode descobrir!',
    caption: `Os segredos templários esperam por você no Quarto 66! 🏰\n\nCom atmosfera medieval, desafios históricos e uma narrativa envolvente, essa sala é pra quem quer muito mais que um game comum.\n\nO mistério tem séculos de idade. A sua solução: 60 minutos.`,
    hashtags: `#EscapeTimeBrasil #Quarto66 #EscapeRoomMedieval #Templários #JogosDeFuga #EscapeRoomSP #HistóriaeAventura #ExperiênciaImersiva`
  },
  {
    day: 19, icon: '📱', theme: 'Segunda com Propósito',
    imageDesc: 'Grupo mostrando foto de vitória, estilo selfie pós-escape',
    cta: 'Planejar a semana é ótimo. Mas planejar uma aventura no meio semana é melhor ainda!',
    caption: `Segunda de olho no calendário da semana! 📱\n\nQue tal já marcar aquela aventura? Temos horários de terça a domingo, diurnos e noturnos.\n\nFácil de agendar, difícil de esquecer. Reserva pelo site ou pelo WhatsApp! 🔗`,
    hashtags: `#EscapeTimeBrasil #PlanejeSuaAventura #EscapeRoom #AgendeSeuEscape #JogosDeFuga #EscapeRoomSP #ReserveAgora #AventuraSP`
  },
  {
    day: 20, icon: '😱', theme: 'Spotlight: Asylum',
    imageDesc: 'Corredor sombrio do Asylum, estética horror',
    cta: 'Você entra num asilo de madrugada? Se a resposta for sim… bem-vindo!',
    caption: `😱 SALA EM DESTAQUE: ASYLUM — O ASILO DOS FAMINTOS\n\nEssa não é pra quem tem coração fraco. O Asylum vai te colocar em uma situação que você nunca imaginou estar.\n\nCenografia perturbadora. Atmosfera sufocante. Adrenalina real.\n\nNível: apenas 10% das equipes escapam. Você aceita esse desafio?`,
    hashtags: `#EscapeTimeBrasil #Asylum #EscapeRoomHorror #AsiloDosHorrores #JogosDeFuga #Adrenalina #EscapeRoomSP #Arrepiante`
  },
  {
    day: 21, icon: '🌟', theme: 'Quarta de Destaque',
    imageDesc: 'Hall da Escape Time com as portas das salas ao fundo',
    cta: 'Já são 6 salas diferentes pra você escolher. Qual é a sua?',
    caption: `Alcatraz, Missão Espacial, Quarto 66, Asylum, Jogos Mortais, Museu dos Horrores… 🌟\n\nCada sala é um universo diferente com sua própria história, desafios e nível de dificuldade.\n\nJá visitou alguma? Comenta qual foi a sua experiência! Já fizemos as 6?`,
    hashtags: `#EscapeTimeBrasil #TodasAsSalas #EscapeRoom #JogosDeFuga #EscapeRoomSP #SeisSalas #QualÉASua #ExperiênciaImersiva`
  },
  {
    day: 22, icon: '🔥', theme: 'Quinta de Fogo',
    imageDesc: 'Chamas estilizadas com silhueta escapando',
    cta: 'A sala está "pegando fogo" — figurativamente. Você consegue manter a calma?',
    caption: `Manter a cabeça fria quando o desafio esquenta. Essa é a habilidade mais valiosa no Escape Room. 🔥\n\nE também na vida real.\n\nVenha treinar sua resiliência, foco e inteligência emocional numa experiência que parece um filme. Que mais pode te oferecer isso?`,
    hashtags: `#EscapeTimeBrasil #InteligênciaEmocional #EscapeRoom #FocoEPressão #JogosDeFuga #SoftSkills #EscapeRoomSP #DesenvolvimentoPessoal`
  },
  {
    day: 23, icon: '🎊', theme: 'Aniversário? Vem Pra Cá!',
    imageDesc: 'Festa de aniversário dentro de sala temática, balões temáticos',
    cta: 'Anniversário diferente? Escape Room + festa na Escape Time é a combinação perfeita!',
    caption: `Cansou de festa no salão de sempre? 🎊\n\nA Escape Time oferece uma experiência de aniversário inesquecível! Venha com seus amigos, encare um desafio épico e celebre cada segundo.\n\nPersonalizamos a experiência pro seu evento. Fala com a gente!`,
    hashtags: `#EscapeTimeBrasil #AniversárioNoEscape #FestaDiferente #AniversárioEmSP #EscapeRoomFesta #CelebraçãoÚnica #EscapeRoomSP #AniverEscape`
  },
  {
    day: 24, icon: '🏄', theme: 'Sábado de Aventura',
    imageDesc: 'Time em posição de início dentro de sala, olhando relógio',
    cta: 'O relógio zerou. A sala está trancada. O desafio começa. Você está pronto?',
    caption: `Aquele sábado que começa com coração na garganta e termina com a melhor risada da semana. 🏄\n\nNa Escape Time, cada segunda é uma emoção. Cada pista descoberta, uma vitória parcial. Cada escape completo, uma história épica.\n\nReserva esse final de semana!`,
    hashtags: `#EscapeTimeBrasil #SábadoÉpico #EscapeRoom #HistóriaÉpica #JogosDeFuga #EscapeRoomBrasil #DivertidoEmSP #AventuraGarantida`
  },
  {
    day: 25, icon: '🌿', theme: 'Domingo Verde',
    imageDesc: 'Família jovem em cena divertida, câmera de segurança de sala',
    cta: 'Domingo sem tela, com aventura real. Isso se chama qualidade de tempo!',
    caption: `Tem coisa mais gostosa que um domingo bem aproveitado? 🌿\n\nNa Escape Time, o domingo vira uma memória. Aquela foto na saída com todo mundo sorrindo, o orgulho de ter superado um desafio juntos.\n\nVenha criar memórias que ficam!`,
    hashtags: `#EscapeTimeBrasil #DomingoSemTela #EscapeRoom #QualidadeDeVida #DomingoComPropósito #EscapeRoomSP #MemóriasDeFamília #Brooklin`
  },
  {
    day: 26, icon: '🎓', theme: 'Spotlight: Escola',
    imageDesc: 'Crianças em sala de escape temática educacional',
    cta: 'Aprender nunca foi tão emocionante. O Escape Time School chegou!',
    caption: `🎓 ESCAPE TIME SCHOOL\n\nImagina aprender história, ciência ou lógica dentro de um escape room? Isso existe e é na Escape Time!\n\nExperiências educativas gamificadas que desenvolvem raciocínio crítico, trabalho em equipe e comunicação.\n\nIdeal pra escolas, instituições e grupos de jovens. Muda o jogo na educação!`,
    hashtags: `#EscapeTimeBrasil #EscapeTimeSchool #EducaçãoImersiva #GamificaçãoNaEducação #EscapeRoomEscola #AprendizagemAtiva #EscapeRoomSP #EduGameBR`
  },
  {
    day: 27, icon: '⏰', theme: 'Contagem Regressiva',
    imageDesc: 'Relógio digital mostrando 00:07 com expressão de urgência',
    cta: '7 segundos. 1 código. É agora ou nunca. Você treinaria pra esse momento?',
    caption: `7 segundos no relógio. Uma última pista na mão. E o código ainda não foi encontrado. ⏰\n\nEssa sensação de pressão extrema que só o Escape Room proporciona.\n\nQuando foi a última vez que você sentiu seus sentidos aguçados assim? Vem resgatar isso.`,
    hashtags: `#EscapeTimeBrasil #ContagemRegressiva #EscapeRoom #Adrenalina #60Minutos #JogosDeFuga #EscapeRoomSP #MomentoEpico`
  },
  {
    day: 28, icon: '🎪', theme: 'Quarta de Novidades',
    imageDesc: 'Teaser de nova sala, detalhes misteriosos sem revelar tema',
    cta: 'Alguém falou em novidades? 👀 Segue a gente pra ser o primeiro a saber!',
    caption: `Algo está chegando na Escape Time Brasil… 🎪\n\nNão vamos contar ainda. Mas pode ter certeza: vai ser épico.\n\nAtiva o sininho aqui e fica de olho nas nossas redes. Quem avisa primeiro ganha um bônus especial!`,
    hashtags: `#EscapeTimeBrasil #Novidades #TeaseEscapeRoom #BreakingNews #EscapeRoomSP #NovidadeQueVem #AtivaOSininho #Maio2025`
  },
  {
    day: 29, icon: '🔓', theme: 'Quinta da Libertação',
    imageDesc: 'Cadeado aberto em close, luz dramática',
    cta: 'Libertação não é fuga. É conquista. Venha conquistar a sua!',
    caption: `Quando a última fechadura abre, não é só a porta que se liberta. É você. 🔓\n\nA sensação de ter resolvido todos os enigmas, de ter trabalhado em equipe sob pressão e ter conseguido…\n\nÉ difícil descrever. É impossível esquecer. Vem sentir.`,
    hashtags: `#EscapeTimeBrasil #Libertação #EscapeRoom #SensaçãoDeConquista #JogosDeFuga #EscapeRoomSP #ÉpicaConquista #VenhaEscapar`
  },
  {
    day: 30, icon: '🥳', theme: 'Pré-Feriado: Intensidade Total',
    imageDesc: 'Fila animada na entrada da Escape Time, clima festivo',
    cta: 'Véspera de feriado aqui é pré-game da adrenalina. Reserva enquanto tem vaga!',
    caption: `Sexta antes do feriado? Melhor hora pra marcar aquela aventura! 🥳\n\nNossas salas costumam lotar nos feriados — então corre pra garantir o seu horário.\n\nVenha com a galera e começa o feriadão do jeito certo: com muita energia e memórias inesquecíveis!`,
    hashtags: `#EscapeTimeBrasil #PréFeriado #EscapeRoom #FeriadãoEmSP #JogosDeFuga #EscapeRoomSP #GaranteOSeuHorário #DivertidoEmSP`
  },
  {
    day: 31, icon: '🏁', theme: 'Último Dia de Maio: Encerra em Alta!',
    imageDesc: 'Banner de fim de mês, chave dourada, confete',
    cta: 'Maio quase acaba. Você ainda tem tempo de criar a melhor memória do mês. E aí?',
    caption: `Último dia de maio! 🏁\n\nMas a aventura não termina aqui. A Escape Time está aqui todos os dias, esperando por você.\n\nJunho começa com muita coisa nova. Segue a gente e não perde nenhuma novidade.\n\nObrigado por cada visita, cada sorriso e cada escape épico esse mês. Até o próximo desafio!`,
    hashtags: `#EscapeTimeBrasil #FechaMaio #EscapeRoom #AteJunho #JogosDeFuga #EscapeRoomSP #ObrigadoMaio #ContinuaAventura`
  }
];

function loadState() {
  try {
    const saved = localStorage.getItem(STORAGE_KEY);
    return saved ? JSON.parse(saved) : {};
  } catch { return {}; }
}

function saveState(state) {
  try { localStorage.setItem(STORAGE_KEY, JSON.stringify(state)); } catch {}
}

let state = loadState();

function updateStats() {
  const done = Object.values(state).filter(v => v).length;
  const total = 27;
  const pending = total - done;
  document.getElementById('countDone').querySelector('.num').textContent = done;
  document.getElementById('countPending').querySelector('.num').textContent = pending;
  const pct = Math.round((done / total) * 100);
  document.getElementById('progressFill').style.width = pct + '%';
  document.getElementById('progressPct').textContent = pct + '%';
}

function toggleCard(day) {
  state[day] = !state[day];
  saveState(state);
  const card = document.querySelector(`.card[data-day="${day}"]`);
  if (state[day]) card.classList.add('done');
  else card.classList.remove('done');
  updateStats();
}

function filter(type, btn) {
  document.querySelectorAll('.filter-btn').forEach(b => b.classList.remove('active'));
  btn.classList.add('active');
  document.querySelectorAll('.card').forEach(card => {
    const isDone = card.classList.contains('done');
    if (type === 'all') card.classList.remove('hidden');
    else if (type === 'done') card.classList.toggle('hidden', !isDone);
    else if (type === 'pending') card.classList.toggle('hidden', isDone);
  });
  document.querySelectorAll('.week-header').forEach(h => h.style.display = '');
}

function renderPosts() {
  const container = document.getElementById('postsContainer');
  const weeks = [
    { label: 'SEMANA 1 · 05 – 11/05', days: [5,6,7,8,9,10,11] },
    { label: 'SEMANA 2 · 12 – 18/05', days: [12,13,14,15,16,17,18] },
    { label: 'SEMANA 3 · 19 – 25/05', days: [19,20,21,22,23,24,25] },
    { label: 'SEMANA 4 · 26 – 31/05', days: [26,27,28,29,30,31] }
  ];

  weeks.forEach(week => {
    const wh = document.createElement('div');
    wh.className = 'week-header';
    wh.innerHTML = `<span class="week-label">${week.label}</span>`;
    container.appendChild(wh);

    const grid = document.createElement('div');
    grid.className = 'grid';

    week.days.forEach(dayNum => {
      const p = posts.find(x => x.day === dayNum);
      if (!p) return;
      const isDone = !!state[dayNum];
      const wd = weekdayMap[dayNum];

      const card = document.createElement('div');
      card.className = 'card' + (isDone ? ' done' : '');
      card.dataset.day = dayNum;

      card.innerHTML = `
        <div class="done-stamp">✓ PUBLICADO</div>
        <div class="card-image-area">
          <span class="card-image-icon">${p.icon}</span>
          <span class="card-image-label">Sugestão de Imagem / Vídeo</span>
          <span class="card-image-prompt">${p.imageDesc}</span>
        </div>
        <div class="card-header">
          <div class="day-badge">${String(dayNum).padStart(2,'0')}</div>
          <div class="card-meta">
            <div class="card-weekday">${wd} · ${String(dayNum).padStart(2,'0')}/05/2025</div>
            <div class="card-theme">${p.theme}</div>
          </div>
        </div>
        <div class="card-body">
          <div class="section-label red">🎯 GANCHO / CTA</div>
          <div class="cta-text">${p.cta}</div>

          <div class="section-label gold">📝 LEGENDA DO REEL</div>
          <div class="caption-box">${p.caption}<div class="hashtags">${p.hashtags.split(' ').join(' ')}<span class="cta-hash">E aí, vai encarar?! 🔐</span></div></div>
        </div>
        <div class="card-footer">
          <label class="check-label" onclick="toggleCard(${dayNum})">
            <input type="checkbox" ${isDone ? 'checked' : ''}>
            <div class="check-box"><span class="tick">✓</span></div>
            <span class="check-text">${isDone ? 'PUBLICADO' : 'MARCAR COMO PUBLICADO'}</span>
          </label>
        </div>
      `;

      grid.appendChild(card);
    });

    container.appendChild(grid);
  });
}

renderPosts();
updateStats();
</script>
</body>
</html>

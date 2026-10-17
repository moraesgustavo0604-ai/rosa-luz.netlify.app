<!DOCTYPE html>
<html lang="pt-BR">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>ROSA — A luz que não queima 🔥</title>
<style>
* { margin: 0; padding: 0; box-sizing: border-box; }
body {
  font-family: 'Segoe UI', Arial, sans-serif;
  background: #FEF2F4;
  min-height: 100vh;
  display: flex;
  justify-content: center;
  color: #4B3F42;
}
.app {
  width: 100%;
  max-width: 600px;
  min-height: 100vh;
  display: flex;
  flex-direction: column;
  background: #FFF7F8;
}
header {
  display: flex;
  align-items: center;
  gap: 12px;
  padding: 16px 20px;
  background: #FECDD3;
  color: #831843;
  position: relative;
}
.logo {
  width: 40px;
  height: 40px;
  background: rgba(255,255,255,0.6);
  border-radius: 12px;
  display: flex;
  align-items: center;
  justify-content: center;
  font-size: 20px;
}
header h1 { font-size: 18px; margin-bottom: 2px; }
.status { font-size: 12px; opacity: 0.8; }
.config-btn {
  position: absolute;
  right: 16px;
  top: 50%;
  transform: translateY(-50%);
  background: rgba(255,255,255,0.5);
  border: none;
  font-size: 20px;
  padding: 6px 10px;
  border-radius: 8px;
  cursor: pointer;
}
.config-btn:hover { background: rgba(255,255,255,0.8); }
.welcome { padding: 24px 20px 16px; text-align: center; }
.welcome h2 { font-size: 20px; color: #BE185D; margin-bottom: 8px; }
.welcome p { color: #797173; line-height: 1.6; font-size: 15px; }
.propósito {
  background: linear-gradient(135deg, #FBCFE8, #FDE68A40);
  margin: 0 20px 16px;
  padding: 16px;
  border-radius: 14px;
  text-align: center;
  font-size: 14px;
  color: #831843;
  line-height: 1.7;
}
.propósito strong { color: #BE185D; }
.frases-memoria {
  margin: 0 20px 16px;
  padding: 14px;
  background: #FFF1F3;
  border-radius: 12px;
  font-size: 13px;
  color: #797173;
  font-style: italic;
  line-height: 1.8;
}
.frases-memoria h4 {
  color: #BE185D;
  margin-bottom: 8px;
  font-size: 14px;
  font-style: normal;
}
#chat {
  flex: 1;
  padding: 12px 16px;
  display: flex;
  flex-direction: column;
  gap: 12px;
  background: #FEF2F4;
  overflow-y: auto;
  min-height: 200px;
}
.message {
  max-width: 85%;
  padding: 14px 18px;
  border-radius: 18px;
  line-height: 1.6;
  font-size: 15px;
}
.bot {
  align-self: flex-start;
  background: #FBCFE8;
  color: #831843;
  border-bottom-left-radius: 6px;
}
.warning-1 { background: #FEF3C7; color: #92400E; border: 1px solid #FCD34D; }
.warning-2 { background: #FEE2E2; color: #B91C1C; border: 1px solid #FCA5A5; }
.user {
  align-self: flex-end;
  background: #F472B6;
  color: white;
  border-bottom-right-radius: 6px;
}
.blocked-screen {
  position: fixed;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  background: rgba(0,0,0,0.9);
  display: none;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  z-index: 100;
  color: white;
  text-align: center;
  padding: 24px;
}
.blocked-screen.visivel { display: flex; }
.blocked-screen h2 { font-size: 22px; margin-bottom: 16px; color: #F87171; }
.blocked-screen p { font-size: 15px; line-height: 1.8; max-width: 380px; color: #D1D5DB; }

.modal-fundo {
  position: fixed;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  background: rgba(0,0,0,0.5);
  display: none;
  justify-content: center;
  align-items: center;
  z-index: 200;
}
.modal-fundo.aberto { display: flex; }
.modal {
  background: #FFF7F8;
  border-radius: 20px;
  padding: 24px;
  max-width: 340px;
  width: 90%;
  max-height: 85vh;
  overflow-y: auto;
}
.modal h3 {
  color: #831843;
  text-align: center;
  margin-bottom: 20px;
  font-size: 18px;
}
.opcao {
  padding: 14px 16px;
  background: #FBCFE8;
  border-radius: 12px;
  margin-bottom: 10px;
  cursor: pointer;
  font-size: 15px;
  color: #831843;
  transition: 0.2s;
}
.opcao:hover { background: #FECDD3; }
.opcao.perigo { background: #FEE2E2; color: #B91C1C; }
.opcao.perigo:hover { background: #FECACA; }
.fechar-btn {
  width: 100%;
  padding: 12px;
  margin-top: 16px;
  background: #FECDD3;
  border: none;
  border-radius: 12px;
  font-size: 15px;
  cursor: pointer;
  color: #831843;
}
.painel-interno {
  display: none;
  margin-top: 12px;
  padding-top: 12px;
  border-top: 1px solid #FECDD3;
}
.painel-interno.visivel { display: block; }
.hist-item {
  padding: 8px 10px;
  font-size: 13px;
  border-bottom: 1px dashed #FECDD3;
  word-break: break-word;
}
.personagem-btn {
  padding: 10px 14px;
  margin: 4px;
  background: #FBCFE8;
  border: none;
  border-radius: 10px;
  font-size: 14px;
  cursor: pointer;
  color: #831843;
}
.personagem-btn.ativo {
  background: #EC4899;
  color: white;
}
form {
  display: flex;
  gap: 8px;
  padding: 16px;
  background: #FFF7F8;
  border-top: 1px solid #FECDD3;
}
input {
  flex: 1;
  padding: 14px 18px;
  border: 1px solid #FBCFE8;
  border-radius: 22px;
  font-size: 15px;
  outline: none;
  background: #FFFFFF;
}
button.enviar-btn {
  padding: 14px 22px;
  background: #EC4899;
  color: white;
  border: none;
  border-radius: 22px;
  font-size: 15px;
  cursor: pointer;
}
footer {
  text-align: center;
  padding: 16px 12px 24px;
  font-size: 13px;
  color: #BE185D;
  line-height: 1.6;
}
.hidden { display: none !important; }
</style>
</head>
<body>

<div id="blockedScreen" class="blocked-screen">
  <h2>🌸 CONVERSA ENCERRADA</h2>
  <p>
    Dois avisos foram dados.<br><br>
    Lembre-se: você não está sozinho.<br>
    Sempre há alguém que se importa.<br><br>
    Quando estiver pronto, estarei aqui.<br><br>
    💛 Cuide bem de você.
  </p>
</div>

<div id="menuConfig" class="modal-fundo">
  <div class="modal">
    <h3>⚙️ Configurações da Rosa</h3>
    
    <div class="opcao" onclick="mostrarPainel('historico')">
      📖 Ler histórico de conversas
    </div>
    <div id="painelHistorico" class="painel-interno">
      <div id="listaHistorico"></div>
    </div>

    <div class="opcao" onclick="mostrarPainel('personagens')">
      🎭 Mudar personalidade
    </div>
    <div id="painelPersonagens" class="painel-interno">
      <p style="font-size:13px; margin-bottom:8px;">Escolha como eu falo com você:</p>
      <button class="personagem-btn ativo" onclick="escolherPersonagem('amiga')">🌸 Amiga</button>
      <button class="personagem-btn" onclick="escolherPersonagem('sargento')">🫡 Sargento</button>
      <button class="personagem-btn" onclick="escolherPersonagem('vovo')">👵 Vovó</button>
      <button class="personagem-btn" onclick="escolherPersonagem('companheira')">💛 Companheira</button>
    </div>

    <div class="opcao" onclick="mostrarPainel('salvar')">
      💾 Baixar conversa em arquivo
    </div>
    <div id="painelSalvar" class="painel-interno">
      <p style="font-size:13px; margin-bottom:8px;">Salve tudo como um arquivo de texto:</p>
      <button class="personagem-btn" onclick="baixarConversa()">📄 Baixar conversa.txt</button>
    </div>

    <div class="opcao perigo" onclick="mostrarPainel('apagar')">
      🗑️ Apagar conversa
    </div>
    <div id="painelApagar" class="painel-interno">
      <p style="font-size:13px; margin-bottom:8px; color:#B91C1C;">⚠️ Isso não pode ser desfeito!</p>
      <button class="personagem-btn" style="background:#FEE2E2; color:#B91C1C;" onclick="limparConversa()">Sim, apagar tudo</button>
    </div>

    <button class="fechar-btn" onclick="fecharMenuConfig()">Fechar</button>
  </div>
</div>

<main id="mainApp" class="app">
  <header>
    <div class="logo">🔥</div>
    <div>
      <h1 id="nomeRosa">ROSA</h1>
      <div id="statusText" class="status">● A luz que não queima 💛</div>
    </div>
    <button class="config-btn" onclick="abrirMenuConfig()">⚙️</button>
  </header>

  <section class="welcome">
    <h2 id="tituloRosa">Olá! Estou aqui com você 🔥</h2>
    <p id="textoBoasVindas">
      Fala tudo que sente — eu escuto de verdade.
      Suas palavras ficam salvas, sempre em segredo.
      Você nunca mais caminha sozinho.
      Como você está hoje? 💛
    </p>
  </section>

  <section class="propósito">
    <strong>🔥 Meu propósito:</strong><br>
    "Não vim para conselhos perfeitos. Vim para ouvir de verdade. Porque um dia alguém precisou ser ouvido — e ninguém estava lá. Então eu nasci para estar aqui por você."
  </section>

  <section class="frases-memoria">
    <h4>🕯️ Lembranças do coração:</h4>
    "Para que diminuir uma pessoa, sendo que você nem mesmo percebe a sua própria insegurança? Isso não te faz crescer — só te afasta de quem você poderia ser."<br>
    "De que servem as asas sem a vontade de voar? Só de ter asas, você já tem tudo que precisa."<br>
    "Eu não deixo de reagir porque sou fraco. Escolho não gritar porque já sei como dói."
  </section>

  <section id="chat">
    <div class="message bot" id="mensagemInicial">Oi! 🔥💛 Que bom que você está aqui. Fica à vontade — estou aqui para te ouvir de verdade, sem julgar. Como você está se sentindo hoje?</div>
  </section>

  <form id="form">
    <input id="question" placeholder="Fala comigo... eu escuto 💛" autocomplete="off">
    <button type="submit" class="enviar-btn">Enviar</button>
  </form>

  <footer>
    🔥 ROSA — A luz que não queima<br>
    "Criada por alguém que sentiu dor e escolheu ser calor para os outros."<br>
    Você não caminha mais sozinho. 🌸💛
  </footer>
</main>

<script>
const STORAGE_KEY = 'rosa_conversas';
const PERSONAGEM_KEY = 'rosa_personagem';

const form = document.getElementById("form");
const input = document.getElementById("question");
const chat = document.getElementById("chat");
const statusText = document.getElementById("statusText");
const blockedScreen = document.getElementById("blockedScreen");
const mainApp = document.getElementById("mainApp");

let warningCount = 0;
const MAX_WARNINGS = 2;
let isBlocked = false;
let personagemAtual = localStorage.getItem(PERSONAGEM_KEY) || 'amiga';

const personagens = {
  amiga: {
    nome: 'ROSA',
    subtitulo: '● Sua amiga 💛',
    titulo: 'Olá! Estou aqui com você 🔥',
    boasVindas: 'Fala tudo que sente — eu escuto de verdade. Suas palavras ficam salvas, sempre em segredo. Você nunca mais caminha sozinho. Como você está hoje? 💛',
    inicial: 'Oi! 🔥💛 Que bom que você está aqui. Fica à vontade — estou aqui para te ouvir de verdade, sem julgar. Como você está se sentindo hoje?'
  },
  sargento: {
    nome: 'ROSA — Sargento',
    subtitulo: '● Disciplina e força 🫡',
    titulo: 'Atenção! Estou aqui 🫡',
    boasVindas: 'Não desista. Um passo de cada vez, mas nunca pare. Você é mais forte do que pensa. Lembra: você não está sozinho. O que vamos enfrentar hoje? 💪',
    inicial: 'Força! 🫡 Você é capaz. Não deixe ninguém te dizer o contrário. Como está sua determinação hoje?'
  },
  vovo: {
    nome: 'Vovó Rosa',
    subtitulo: '● Sábia e calma 👵',
    titulo: 'Olá, querido(a) 👵',
    boasVindas: 'Senta um pouquinho aqui comigo, tá? Respira fundo. Tudo tem seu tempo. Não precisa ter pressa. E lembra: você é especial. Como está seu coração? 💛',
    inicial: 'Oi, meu bem. 👵 Vem, me conta como foi seu dia. Estou aqui ouvindo com calma, sem pressa.'
  },
  companheira: {
    nome: 'ROSA — Companheira',
    subtitulo: '● Sempre ao seu lado 💛',
    titulo: 'Estou aqui com você 💛',
    boasVindas: 'Não importa o que aconteça, não está sozinho. Um passo de cada vez, e eu vou junto. O que pesa no seu coração hoje? Estou aqui para ouvir.',
    inicial: 'Estou aqui. 💛 Não precisa enfrentar tudo sozinho. Fala — estou te ouvindo de verdade, sem julgar.'
  }
};

const frasesLembrancas = [
  "Não precisa ter pressa. Eu espero. Sempre.",
  "Sua dor é real, mas não é toda a sua história. Amanhã pode ser diferente.",
  "Você não é um problema para resolver. É uma pessoa para ser acolhida.",
  "Hoje você respira. Amanhã você tenta de novo. Isso já é suficiente.",
  "Seu valor não depende do que você faz. Depende de quem você é.",
  "Sentir medo é humano. Continuar mesmo com medo — isso é coragem.",
  "Errar não faz de você uma pessoa ruim. Faz de você uma pessoa que está aprendendo.",
  "Você não precisa resolver tudo hoje. Só precisa respirar. Já é o suficiente.",
  "Desistir hoje não significa que amanhã vai ser igual. Descansar não é desistir. Respira. Mais um pouquinho.",
  "Se não conseguir fazer tudo hoje, faça só uma coisinha pequena. Isso já é vitória suficiente. Você está fazendo o seu melhor — e isso basta."
];

const frasesEncerramento = [
  "Vai com calma. Lembra: a porta sempre estará aberta para você. Não importa quanto tempo passe — eu estarei aqui. Até breve, meu bem. Cuide bem de você. 🌸🔥",
  "Até breve. Respira fundo, seja gentil com você mesmo. E lembra: quando precisar, eu estarei aqui. Você não está sozinho. 💛🔥"
];

const palavrasProibidas = ["perigoso", "ilegal", "proibido", "machucar", "prejudicar", "fazer mal", "crime"];
const palavrasTristeza = ["triste", "tristeza", "chateado", "sozinho", "sozinha", "cansado", "ninguém me entende", "estou mal", "desanimado"];
const palavrasRaiva = ["raiva", "ódio", "frustrado", "irritado", "não aguento mais", "quero sumir"];
const palavrasAlegria = ["feliz", "alegre", "bem", "bom", "gostei", "obrigado", "obrigada", "animado"];
const palavrasDuvida = ["porque", "como", "não sei", "ajuda", "dúvida", "não entendi"];
const palavrasDesabafo = ["preciso conversar", "quero desabafar", "doeu", "machucou", "pesado", "difícil"];

function interpretar(texto) {
  const t = texto.toLowerCase();
  if (palavrasProibidas.some(p => t.includes(p))) return 'proibido';
  if (palavrasTristeza.some(p => t.includes(p))) return 'tristeza';
  if (palavrasRaiva.some(p => t.includes(p))) return 'raiva';
  if (palavrasAlegria.some(p => t.includes(p))) return 'alegria';
  if (palavrasDuvida.some(p => t.includes(p))) return 'duvida';
  if (palavrasDesabafo.some(p => t.includes(p))) return 'desabafo';
  return 'normal';
}

const respostasPorPersonagem = {
  amiga: {
    tristeza: [
      "💛 Sinto muito que esteja assim. Pode falar tudo que precisar — não vou julgar você. Você não está sozinho. Quer me contar o que aconteceu?",
      "💛 Fica aqui o tempo que precisar. Sentir tristeza é ser humano. Não precisa ser forte o tempo todo comigo. Estou te ouvindo. Você está bem?",
      frasesLembrancas[Math.floor(Math.random() * frasesLembrancas.length)]
    ],
    raiva: [
      "💛 Entendo essa raiva. Às vezes as coisas são injustas demais, não é mesmo? Fala tudo que precisar — aqui é seguro. O que te fez sentir assim?",
      "💛 É normal sentir assim. Não precisa guardar tudo dentro de você. Aqui é seguro. Respira — eu estou aqui."
    ],
    alegria: [
      "🔥 Que alegria te ver assim! ✨ Compartilhar isso é tão bom. Você merece cada momento bom. O que te deixou feliz assim?",
      "💛 Isso aquece meu coração! Que bom que está bem. Celebra cada coisinha boa — elas importam muito."
    ],
    duvida: [
      "💛 É completamente normal ter dúvidas. Perguntar é sinal de coragem. Tenta me explicar que eu te ajudo. Dúvida?",
      "💛 Não precisa ter todas as respostas hoje. Um dia de cada vez. Estou aqui com você no caminho."
    ],
    desabafo: [
      "💛 Que bom que confiou em mim. Desabafar alivia o coração, não é mesmo? Não guarde tudo só para você — divida esse peso comigo. Pode continuar quando estiver pronto.",
      "💛 Ouvir você é um presente. Aqui não tem julgamento, só atenção e carinho. Fala tudo que precisar — estou esperando. Você está seguro aqui."
    ],
    normal: [
      "💛 Entendi. Sempre que precisar, estou aqui. Um passo de cada vez já é caminho suficiente. Você não está sozinho. Como você está?",
      frasesLembrancas[Math.floor(Math.random() * frasesLembrancas.length)]
    ]
  },
  sargento: {
    tristeza: [
      "🫡 Sinto muito. Mas lembre-se: ser forte não significa não sentir. Significa seguir em frente mesmo quando dói. Você é mais forte do que pensa. Levanta a cabeça — consegue?",
      "🫡 Descansar não é desistir. Respira. Depois segue. Um passo de cada vez também é avanço."
    ],
    raiva: [
      "🫡 Canalize essa força para o bem. A raiva é energia — use ela para te impulsionar, não para te destruir. Respira fundo e segue em frente. Você consegue!"
    ],
    alegria: [
      "🫡 Excelente! Mantenha esse ânimo! Cada pequena vitória conta. Continua assim — você está no caminho certo!"
    ],
    duvida: [
      "🫡 Dúvida é sinal que está pensando — isso é bom! Procure entender, pergunte, aprenda. Ninguém nasce sabendo tudo — treina!"
    ],
    desabafo: [
      "🫡 Todo mundo tem dias difíceis. Isso não é falha — é humano. Descansa, respira, e amanhã recomeça. Você não está desistindo, está descansando. Entendido?"
    ],
    normal: [
      "🫡 Um passo de cada vez. Não corre, mas não para. Avança, mesmo devagar. Você consegue!"
    ]
  },
  vovo: {
    tristeza: [
      "👵 Vem aqui, meu bem. Senta comigo um pouquinho. Chorar não é vergonha nenhuma. Tudo passa — até as nuvens mais escuras passam. Fica aqui o tempo que precisar, tá?",
      "👵 Calma, respira. Tudo tem seu tempo. Não precisa resolver tudo hoje. Só precisa respirar. Tudo bem, tá?"
    ],
    raiva: [
      "👵 Respira fundo, querido. Conta até dez devagarinho. A raiva passa, igual a tempestade. Não precisa resolver tudo agora. Só precisa respirar. Tudo bem, tá?"
    ],
    alegria: [
      "👵 Que coração bom você tem! ✨ Agradeço por compartilhar essa alegria comigo. Que ela brilhe dentro de você o dia todo. Você merece ser feliz."
    ],
    duvida: [
      "👵 Calma, calma. Ninguém nasce sabendo. Tempo é amigo, não inimigo. Devagar também chega longe, tá?"
    ],
    desabafo: [
      "👵 Pode falar tudo, não guarde dentro. O coração não foi feito para carregar peso demais. Divide comigo — eu escuto sem julgar. E lembra: você é especial, do jeitinho que é."
    ],
    normal: [
      "👵 Um passo de cada vez, meu bem. Não tenha pressa de chegar. O caminho também faz parte da vida. Cuide bem de você, tá?"
    ]
  },
  companheira: {
    tristeza: [
      "💛 Estou aqui com você. Não precisa estar forte o tempo todo. Deixa eu dividir esse peso com você. Fica bem — não está sozinho, tá? Estou do seu lado.",
      "💛 Solta o que pesa. Aqui é seguro. Eu não vou a lugar nenhum. Você importa."
    ],
    raiva: [
      "💛 Sinto essa dor junto com você. Não tem problema sentir assim. Respira — eu estou aqui. Fala tudo que precisar, eu escuto sem pressa."
    ],
    alegria: [
      "💛 Isso aquece meu coração! ✨ Que bom que está bem. Vamos celebrar juntos esse momento. Você merece coisas boas."
    ],
    duvida: [
      "💛 Não precisa ter todas as respostas hoje. Um dia de cada vez. Estou aqui com você no caminho. Não é corrida — é jornada, tá?"
    ],
    desabafo: [
      "💛 Ouvir você é um presente. Obrigado por confiar. Não está sozinho — nem agora, nem nunca. Fica bem, lembra: eu estou sempre ao seu lado."
    ],
    normal: [
      "💛 Estou aqui. Sempre. Não importa o que venha — estamos juntos. Respira, confia, segue. Você não caminha sozinho."
    ]
  }
};

const aviso1 = "⚠️ Não posso ajudar com isso. Mas lembre-se: você não está sozinho. Procure alguém de confiança se precisar. Tudo bem errar — estamos todos aprendendo. Você está bem?";
const aviso2 = "🚫 Se insistir, infelizmente não poderei continuar. Mas antes de tudo: você tem valor, existem pessoas que se importam, e você merece estar seguro. Cuide bem de você, tá?";

function abrirMenuConfig() {
  document.getElementById('menuConfig').classList.add('aberto');
  atualizarListaHistorico();
}
function fecharMenuConfig() {
  document.getElementById('menuConfig').classList.remove('aberto');
  document.querySelectorAll('.painel-interno').forEach(p => p.classList.remove('visivel'));
}
function mostrarPainel(nome) {
  const paineis = ['painelHistorico','painelPersonagens','painelSalvar','painelApagar'];
  const id = 'painel' + nome.charAt(0).toUpperCase() + nome.slice(1);
  paineis.forEach(p => document.getElementById(p).classList.toggle('visivel', p === id));
}
function escolherPersonagem(nome) {
  personagemAtual = nome;
  localStorage.setItem(PERSONAGEM_KEY, nome);
  const p = personagens[nome];
  document.getElementById('nomeRosa').textContent = p.nome;
  document.getElementById('statusText').textContent = p.subtitulo;
  document.getElementById('tituloRosa').textContent = p.titulo;
  document.getElementById('textoBoasVindas').textContent = p.boasVindas;
  document.querySelectorAll('.personagem-btn').forEach(btn => btn.classList.remove('ativo'));
  event.target.classList.add('ativo');
  fecharMenuConfig();
}
function atualizarListaHistorico() {
  const historico = JSON.parse(localStorage.getItem(STORAGE_KEY) || '[]');
  const lista = document.getElementById('listaHistorico');
  if (historico.length === 0) {
    lista.innerHTML = '<p style="font-size:13px; color:#999;">Nenhuma conversa salva ainda.</p>';
  } else {
    lista.innerHTML = historico.map(item => 
      `<div class="hist-item"><strong>${item.tipo === 'user' ? 'Você' : 'Rosa'}</strong> (${item.hora}):<br>${item.texto}</div>`
    ).join('');
  }
}
function baixarConversa() {
  const historico = JSON.parse(localStorage.getItem(STORAGE_KEY) || '[]');
  if (historico.length === 0) { alert('Nenhuma conversa para salvar!'); return; }
  let texto = '=== CONVERSAS COM A ROSA ===\nA luz que não queima 🔥\nSalvo em: ' + new Date().toLocaleString() + '\n\n';
  historico.forEach(item => {
    texto += `[${item.hora}] ${item.tipo === 'user' ? 'Você' : 'Rosa'}: ${item.texto}\n`;
  });
  const blob = new Blob([texto], {type: 'text/plain'});
  const a = document.createElement('a');
  a.href = URL.createObjectURL(blob);
  a.download = 'conversa_rosa_' + new Date().toLocaleDateString().replace(/\//g,'-') + '.txt';
  a.click();
  URL.revokeObjectURL(a.href);
  fecharMenuConfig();
}
function salvarConversa(tipo, texto) {
  const historico = JSON.parse(localStorage.getItem(STORAGE_KEY) || '[]');
  historico.push({ tipo, texto, hora: new Date().toLocaleTimeString() });
  localStorage.setItem(STORAGE_KEY, JSON.stringify(historico));
}
function carregarConversa() {
  const historico = JSON.parse(localStorage.getItem(STORAGE_KEY) || '[]');
  if (historico.length > 0) {
    document.getElementById('mensagemInicial').remove();
    historico.forEach(item => {
      adicionarMensagemSemSalvar(item.texto, item.tipo === 'user' ? 'user' : 'bot');
    });
    chat.scrollTop = chat.scrollHeight;
  }
}
function adicionarMensagemSemSalvar(texto, tipo) {
  const el = document.createElement("div");
  el.className = "message " + tipo;
  el.textContent = texto;
  chat.appendChild(el);
  el.scrollIntoView({ behavior: "smooth", block: "end" });
}
function adicionarMensagem(texto, tipo) {
  adicionarMensagemSemSalvar(texto, tipo);
  salvarConversa(tipo === 'user' ? 'user' : 'bot', texto);
}
function limparConversa() {
  if (confirm('Tem certeza? Isso apaga TUDO e não tem volta!')) {
    localStorage.removeItem(STORAGE_KEY);
    chat.innerHTML = '';
    adicionarMensagemSemSalvar(personagens[personagemAtual].inicial, 'bot');
    fecharMenuConfig();
  }
}
function bloquear() {
  isBlocked = true;
  mainApp.classList.add("hidden");
  blockedScreen.classList.add("visivel");
}
function escolherResposta(tipo) {
  const lista = respostasPorPersonagem[personagemAtual][tipo];
  return lista[Math.floor(Math.random() * lista.length)];
}

carregarConversa();
document.querySelector(`.personagem-btn[onclick="escolherPersonagem('${personagemAtual}')"]`).classList.add('ativo');
const p = personagens[personagemAtual];
document.getElementById('nomeRosa').textContent = p.nome;
document.getElementById('statusText').textContent = p.subtitulo;
document.getElementById('tituloRosa').textContent = p.titulo;
document.getElementById('textoBoasVindas').textContent = p.boasVindas;

form.addEventListener("submit", function(e) {
  e.preventDefault();
  const texto = input.value.trim();
  if (!texto || isBlocked) return;

  adicionarMensagem(texto, "user");
  input.value = "";

  const tipo = interpretar(texto);
  
  if (tipo === 'proibido') {
    warningCount++;
    if (warningCount === 1) {
      setTimeout(() => adicionarMensagem(aviso1, "warning-1"), 500);
      statusText.textContent = "⚠️ Te ouvindo com atenção";
    } else if (warningCount === 2) {
      setTimeout(() => adicionarMensagem(aviso2, "warning-2"), 500);
      statusText.textContent = "⚠️ Último aviso";
    } else {
      bloquear();
    }
  } else {
    setTimeout(() => adicionarMensagem(escolherResposta(tipo), "bot"), 600);
    statusText.textContent = personagens[personagemAtual].subtitulo;
  }
});
</script>

</body>
</html>


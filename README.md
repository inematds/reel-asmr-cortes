# reel-asmr-cortes — Fábrica de reels ASMR

[![Reels ASMR no automático](guia/assets/banner.jpg)](https://inematds.github.io/reel-asmr-cortes/guia/)

**🇧🇷 [Português](README.md) · 🇺🇸 [English](README.en.md) · 🇪🇸 [Español](README.es.md)**

## O que é

Reels "satisfatórios" (ASMR) seguram as pessoas na tela, mas produzir toda semana dá trabalho. Este kit faz um reel vertical de 36 segundos em que uma fruta em 3D é cortada **10, 100 e 1.000 vezes**, com o som de cada corte e três potes no final. Tudo é desenhado por código no seu computador: sem câmera, sem IA de vídeo e sem pagar por render. Uma lista de frutas vira uma série; um agente (Claude Code ou Codex) faz 3 por semana, **você assiste e aprova**, e um script posta no Instagram pela API oficial. Para usar: Node.js, ffmpeg e, se quiser o post automático, uma conta profissional do Instagram.

## 📖 Guia de uso

Guia completo (landing + passo a passo): **https://inematds.github.io/reel-asmr-cortes/guia/**

🎬 Vídeo: https://www.youtube.com/watch?v=ILIh5bg7cEs

## Começar

```bash
git clone https://github.com/inematds/reel-asmr-cortes.git
cd reel-asmr-cortes
node ferramentas/som.mjs
npx --yes hyperframes@0.9.37 check
npx --yes hyperframes@0.9.37 render . -o renders/reel.mp4 --fps 30
```

## O processo, do início ao fim

| # | Passo | Comando | Quem |
|---|---|---|---|
| 1 | Pôr objetos na lista | editar `objetos.csv` (status `pendente`) | 🧠 você |
| 2 | Preparar o próximo reel | `node ferramentas/novo-reel.mjs` | 🤖 agente (tarefa de segunda 9h) |
| 3 | Desenhar o objeto, se for novo | preencher `objeto.js` (`RECEITA.md`, passo 3) | 🤖 agente |
| 4 | Fazer o reel | `bash ferramentas/fazer-reel.sh <objeto>` | ⚙️ script |
| 5 | Assistir e aprovar | `node ferramentas/status.mjs <objeto> aprovado` | 🧠 você |
| 6 | Postar 1 aprovado | `node ferramentas/postar-instagram.mjs` | 🤖 agente (seg, qua e sex 18h) |

Detalhes: [`RECEITA.md`](RECEITA.md) (um reel novo) e [`SETUP.md`](SETUP.md) (app da Meta, link público, agendamento).

## O que tem aqui

| Arquivo | O que faz |
|---|---|
| `index.html`, `css/`, `js/mundo.js` | O reel: fruta em 3D cortada por um shader, contador, potes |
| `js/cortes.js` | A lista de cortes: contador, lâminas e som leem este arquivo |
| `objeto.js` | O único arquivo que muda por reel |
| `som/sintese.mjs`, `ferramentas/som.mjs` | Sons feitos em código, um em cada corte, −15 LUFS |
| `objetos.csv`, `ferramentas/` | A série: preparar, fazer, aprovar, postar |
| `agendar/` | Os dois prompts das tarefas agendadas |

## O que foi testado

Som, conferência do HyperFrames, fotos paradas, série (numa cópia) e o modo ensaio do post. O post real na API da Meta e o render completo não foram rodados nesta versão: faça o passo 1 e o passo 6 com um reel e confira.

Licença MIT. Three.js (MIT) e fontes (OFL) com as licenças nas pastas `lib/` e `fontes/`.

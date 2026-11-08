# Caçador de Céu e Inferno — protótipo

RPG de turnos em pixel art (Phaser 3 + TypeScript + Vite).

## Rodar

```bash
npm install
npm run dev      # abre o jogo no navegador
npm run sim      # simula uma batalha no terminal (sem navegador)
npm run build    # build de produção
```

Controles: setas + ENTER/ESPAÇO, ESC volta; mouse/toque também funciona.

## Estrutura

```
src/
  main.ts            configuração do Phaser (320x180, pixel art, escala FIT)
  config.ts          resolução, paleta, estilo de texto
  core/rewards.ts    multiplicador de XP/gold por diferença de nível
  data/              personagens, inimigos, habilidades (dados, não lógica)
  battle/            BattleManager (lógica pura, sem Phaser) + simulate.ts
  scenes/            BootScene (sprites provisórios), BattleScene (UI)
```

## O que já funciona

- Fila de turnos por velocidade, rodadas, defender, energia
- Elementos sagrado/profano com fraqueza e resistência
- Dano determinístico (sem sorteio)
- Intenção dos inimigos telegrafada no topo da tela
- Recompensas com a regra de nível (monstro fraco = 0 XP/gold)
- Lógica de batalha separada da tela (reaproveitável em Android/PC)

## Próximos passos

1. Cura (Seraphine) e alvo em aliados
2. Mapa de exploração com Tiled + névoa de exploração (WorldState)
3. Salvamento em slots (localStorage) e penalidade de morte
4. Chefe com memória (BossMemory) e armas cruzadas
5. Arte real, fonte bitmap e áudio

Os números de dano/HP são provisórios e estão fáceis demais para o alvo "souls-like".

## Publicar no GitHub Pages

1. Suba os arquivos do projeto (sem `node_modules`) para um repositório, na branch `main`.
2. No GitHub: Settings > Pages > Source: **GitHub Actions**.
3. A cada push, `.github/workflows/deploy.yml` roda o build e publica o jogo.

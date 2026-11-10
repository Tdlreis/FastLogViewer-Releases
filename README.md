# FastLogViewer

[![Versão](https://img.shields.io/github/v/release/Tdlreis/FastLogViewer-Releases?label=vers%C3%A3o)](https://github.com/Tdlreis/FastLogViewer-Releases/releases/latest)
[![Downloads](https://img.shields.io/github/downloads/Tdlreis/FastLogViewer-Releases/total?label=downloads)](https://github.com/Tdlreis/FastLogViewer-Releases/releases)
![Windows 10/11 64 bits](https://img.shields.io/badge/Windows-10%20%7C%2011%20(64%20bits)-0078D6)

**Visualizador de logs de voo ArduPilot feito para não deixar você esperando.**

O FastLogViewer abre o `.bin` do cartão SD e o `.tlog` da estação de solo em segundos, mesmo
em voos de mais de uma hora, e deixa você navegar por milhões de pontos com a fluidez de um
editor de vídeo. Foi pensado para quem analisa voo todo dia: pilotos, engenheiros e equipes
de manutenção de drones e aviões.

### ⬇️ [Baixar o FastLogViewer 0.9.0](https://github.com/Tdlreis/FastLogViewer-Releases/releases/download/v0.9.0/FastLogViewer-Setup-0.9.0.exe)

`FastLogViewer-Setup-0.9.0.exe` · 66 MB · publicado em 10/11/2026 · [novidades](#novidades-da-versão-090)

---

## Por que usar

**Rápido de verdade.** Um `.bin` de 440 MB e 68 minutos abre em menos de 2 segundos; um
`.tlog` de 730 MB, em cerca de 3. As curvas são desenhadas pela placa de vídeo e só com os
pontos que cabem na tela, então zoom e arrasto continuam fluidos com dez curvas e mais de um
milhão de amostras.

**Gráficos do jeito que você pensa.**
- Arraste na horizontal para dar zoom no tempo, na vertical para o eixo Y, na diagonal para
  uma caixa. `Ctrl+Z` desfaz qualquer coisa: zoom, curvas, cores, escalas e painéis.
- Várias escalas no mesmo painel, com o zero alinhado entre elas.
- A legenda mostra o valor no cursor e o mínimo, o máximo e a média do trecho visível.
- Faixas coloridas com os modos de voo e marcas com os eventos e erros do log. Um clique leva
  o gráfico até lá.
- Gráficos prontos (atitude, altitude, bateria, vibração, GPS, EKF, servos, rádio...) e os
  seus, que você salva, exporta e manda para a equipe.

**Contas sem sair do programa.** Escreva expressões direto na caixa ƒx:
`ATT.DesRoll - ATT.Roll`, `sqrt(IMU.AccX**2 + IMU.AccY**2)`, `integral(BAT.Curr) / 3600`
(Ah consumidos), `deriv(smooth(BARO.Alt, 1))` (razão de subida sem ruído). Linhas de
tendência linear, polinomial ou exponencial com R², e exportação para CSV que abre direto
no Excel.

**Mapa 2D e 3D.** A trajetória colorida pelo modo de voo, sobre satélite ou ruas (com cache
para usar sem internet), sincronizada com o cursor do gráfico. Camadas com home, raio do RTL,
missão, cerca, pontos de rally, trocas de modo e eventos, todas lidas do próprio log. No 3D,
a altitude com exagero ajustável.

**Vibração e espectro.** FFT com média de Welch e espectrograma no tempo, a partir das
curvas ou do batch sampler da IMU. O programa avisa quando a taxa de amostragem ou os filtros
do controle escondem a vibração real e mostra o que configurar no ArduPilot para medir certo.

**Campos de estação de solo.** Tempo armado e de voo, distância e rumo para o home, altura,
waypoint atual e distância percorrida, calculados como numa estação de solo e disponíveis
como qualquer outro campo.

**Assistente de IA.** Conecte o Claude (ou outro assistente com MCP) e peça a análise em
linguagem natural: ele abre os gráficos, dá zoom no trecho certo e marca os achados no
próprio FastLogViewer enquanto conversa com você.

**Sempre atualizado.** Ao abrir, o programa avisa quando há versão nova, mostra o que mudou
e se atualiza com um clique, reabrindo no mesmo log. Cada atualização é assinada
digitalmente e conferida antes de instalar.

## Instalação

1. Baixe o [`FastLogViewer-Setup-0.9.0.exe`](https://github.com/Tdlreis/FastLogViewer-Releases/releases/download/v0.9.0/FastLogViewer-Setup-0.9.0.exe).
2. Execute. Ele instala em *Arquivos de Programas*, cria o atalho no menu Iniciar e aparece em
   *Abrir com* para arquivos `.bin` e `.tlog`.
3. Pronto: daqui em diante as atualizações chegam pelo próprio programa.

> **O Windows mostrou "O Windows protegeu o computador"?** O instalador ainda não tem
> assinatura de código da Microsoft. Clique em **Mais informações** e depois em
> **Executar assim mesmo**.

**Sem acesso de administrador?** Rode pelo Prompt de Comando, na pasta do download:

```
FastLogViewer-Setup-0.9.0.exe /CURRENTUSER
```

Para remover: *Configurações > Aplicativos > FastLogViewer > Desinstalar*. O desinstalador
apaga também as configurações e o cache de mapas.

## Primeiros passos

- Arraste um `.bin` ou `.tlog` para a janela, ou use **Abrir log** (`Ctrl+O`).
- Clique num campo da lista **Campos** para plotar; digite no filtro para achar
  (`att roll`, `bat volt`, `vibe`).
- Escolha um **Gráfico pronto** para começar com os gráficos mais comuns.
- `F1` abre a ajuda com todos os atalhos de mouse e teclado.

## Novidades da versão 0.9.0

## Destaques
- Play no mapa: o cursor anda sozinho de 0,25x a 100x, com gráficos, mapa e barra de status acompanhando.
- Linhas de direção no mapa mostram proa, rumo do GPS e para onde a navegação quer ir.
- Nova aba *Rádio (RC)* mostra os sticks e as chaves do controle em tempo real.

## Novidades
- Botão ▶ no mapa (ou `Espaço`) para tocar o log; clique ou arraste na linha do tempo para pular ou procurar.
- Linhas que saem do avião no mapa, ativáveis em *Camadas*, funcionando em 2D e 3D, para `.bin` e `.tlog`.
- Aba *Rádio (RC)* com os dois sticks, rastro do último segundo e escolha de acelerador em *Modo 1* ou *Modo 2*.
- A aba *Rádio (RC)* mostra a chave de modo de voo, chaves com função, RSSI e LQ, e avisa sobre failsafe, falta de sinal ou override do MAVLink.

## Melhorias
- O zero no eixo Y agora é ajustado por painel, e o programa lembra a última escolha para painéis novos.
- O marcador do avião no mapa virou um ponto azul, com as linhas de direção saindo dele.

As versões anteriores, com as novidades de cada uma e o SHA-256 do instalador, estão em
[Releases](https://github.com/Tdlreis/FastLogViewer-Releases/releases).

---

Desenvolvido pela GlobalDrones. Este repositório guarda só os instaladores e as atualizações
do FastLogViewer.

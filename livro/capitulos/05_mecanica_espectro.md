# A Mecânica do Espectro

> *Autovalores não são propriedades dos números,*  
> *mas dos operadores.*  
> — John von Neumann

## Recapitulação operacional

Nos capítulos anteriores, foi construído um operador determinístico *M* a partir do sinal aritmético ∆π(*x*) e de uma mudança explícita de escala logarítmica.

Esse operador foi introduzido como objeto geométrico e visual, sem qualquer análise espectral.

O objetivo deste capítulo é **descrever formalmente** os elementos básicos da análise espectral aplicada ao operador *M* , em um regime completamente controlado.

Nada novo será introduzido. Apenas ferramentas necessárias serão definidas.

## Um domínio finito e controlado

Antes de avançar para escalas grandes, é instrutivo trabalhar em um domínio pequeno, onde todos os objetos possam ser inspecionados diretamente.

Neste capítulo, fixamos:

> *N* = 32,

e consideramos o domínio discreto *x* ∈ {1, 2, . . . , 32}.

Essa escolha não possui significado teórico. Ela permite apenas que todos os componentes do operador sejam explicitamente calculados e examinados.

## Preparação dos dados de entrada

O **Notebook 05** (`05_mecanica_espectro.ipynb`) inicia gerando, para cada *x* ≤ 32:
- o valor do sinal aritmético ∆π(*x*);
- o valor correspondente de ln(*x*).

[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/costaalv/descobrindo_caos/blob/main/notebooks/05_mecanica_espectro.ipynb)

Esses dados constituem os únicos insumos do operador. Nenhuma filtragem, suavização ou normalização adicional é aplicada.

## Construção explícita do operador

Com os vetores ∆π(*x*) e ln(*x*) definidos, o operador *M* é construído diretamente pela fórmula:

> *M*ᵢⱼ = cos(Δπ(*x*ᵢ) · ln(*x*ⱼ)) + cos(Δπ(*x*ⱼ) · ln(*x*ᵢ)).

Para *N* = 32, isso resulta em uma matriz real, simétrica, de dimensão 32 × 32.

O mapa de calor apresentado no **Notebook 5** permite visualizar a organização interna do operador nesse regime finito.

Nenhuma interpretação é associada a essa visualização. Ela apenas confirma que o operador está bem definido e estruturalmente não trivial.

## Autovalores e autovetores: definições mínimas

Seja *M* uma matriz real e simétrica.

Um número real λ é chamado autovalor de *M* se existir um vetor não nulo *v* tal que:

> *Mv* = λ*v*.

O vetor *v* correspondente é chamado autovetor.

Esses objetos não são introduzidos como analogias físicas. Eles constituem a decomposição canônica de operadores simétricos em espaços reais.

## O espectro do operador em dimensão finita

O **Notebook 05** calcula explicitamente:
- o conjunto completo de autovalores de *M*;
- os autovetores associados.

Para *N* = 32, o espectro é discreto e finito. Todos os autovalores são reais, como garantido pela simetria do operador.

A ordenação desses autovalores e a inspeção dos autovetores permitem verificar que:
- o operador admite uma base espectral completa;
- diferentes modos espectrais correspondem a diferentes padrões de distribuição nos índices *i*.

Neste ponto, nenhuma estatística é calculada. Nenhuma regularidade é postulada.

## Limites do regime finito

A análise em *N* = 32 não tem como objetivo revelar leis universais. Ela serve para:
- fixar definições;
- validar a construção do operador;
- estabelecer o vocabulário espectral que será usado adiante.

O comportamento relevante do espectro não se manifesta plenamente em domínios tão pequenos.

Para isso, será necessário estudar:
- a variação do espectro com o tamanho do domínio;
- a dependência em relação à escala inicial *X*₀.

## Delimitação do escopo

Neste capítulo:
- o operador *M* foi diagonalizado explicitamente;
- autovalores e autovetores foram definidos e calculados;
- nenhuma estatística espectral foi analisada;
- nenhuma hipótese universal foi formulada.

O operador permanece o mesmo. A mudança ocorrerá apenas no regime de observação.

## Ponto de repouso

Até aqui:
- a análise espectral foi introduzida formalmente;
- o operador foi estudado em dimensão finita;
- todas as ferramentas necessárias estão definidas.

No próximo capítulo, essas ferramentas serão aplicadas sistematicamente a domínios crescentes, permitindo observar como o espectro do operador responde à mudança de escala.

Nada será assumido. Tudo será medido.

---

[⬅ Capítulo Anterior](./04_operador_M.md) | [Sumário](../../index.md) | [Próximo Capítulo](./06_regimes_de_escala_e_estatisticas_espectrais.md)

# Reconhecimento de uma Classe Universal

> *A matemática possui uma adequação inexplicável*  
> *às estruturas da natureza.*  
> *— Eugene P. Wigner*

## O que muda ao atravessar a fronteira

Até aqui, o procedimento foi estritamente construtivo.

Um sinal aritmético foi definido, uma mudança de escala foi fixada e um operador determinístico *M* foi construído por simetrização explícita. Em seguida, o espectro desse operador foi medido e um protocolo estatístico completo foi estabelecido.

O ponto decisivo é que nada disso requereu hipóteses probabilísticas, amostragem estocástica ou modelos aleatórios. O operador permaneceu o mesmo. O que variou foi apenas o regime de observação.

Ao iniciar esta parte do livro, ocorre uma mudança de estatuto: as estatísticas medidas deixam de ser apenas registros descritivos e passam a ser confrontadas com classes espectrais conhecidas.

Essa comparação não introduz novos objetos. Ela introduz apenas um vocabulário de reconhecimento.

## Classes espectrais como padrões de referência

Em análise espectral, certas famílias de operadores exibem comportamentos estatísticos robustos, estáveis e recorrentes. Quando um espectro apresenta assinaturas estatísticas estáveis sob variações de tamanho e escala, diz-se que ele é compatível com uma classe universal.

Duas classes de referência serão usadas neste capítulo:

- a classe *não correlacionada*, associada a espectros cujos espaçamentos se comportam como variáveis aproximadamente independentes (frequentemente modelada por uma lei exponencial);
- a classe *correlacionada com repulsão local*, associada a espectros com supressão de espaçamentos muito pequenos e rigidez estatística global (cujo protótipo é o *Ensemble Ortogonal Gaussiano*, GOE).

A introdução dessas classes não é uma hipótese sobre *M*. Ela é um instrumento para interpretar medições já realizadas.

## A primeira assinatura: repulsão de níveis

Consideremos a distribuição empírica *P(s)* dos espaçamentos normalizados, definida no capítulo anterior.

O **Notebook 07** (`07_autovalores_reconhecimento_GOE.ipynb`) permite observar que, para valores suficientemente grandes de *N* e para escalas iniciais elevadas *X*₀, a densidade empírica passa a apresentar uma característica determinante: a probabilidade de espaçamentos muito pequenos torna-se fortemente suprimida.

[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/costaalv/descobrindo_caos/blob/main/notebooks/07_autovalores_reconhecimento_GOE.ipynb)

Em termos descritivos, *P(s)* aproxima-se de uma forma que:

- é aproximadamente nula em *s* = 0;
- cresce a partir de 0 até um máximo em *s* > 0;
- decai para espaçamentos maiores.

Esse padrão não é compatível com espectros não correlacionados.  
Ele é a assinatura mínima de repulsão local entre autovalores.

## A estatística escalar e o valor de referência

A razão entre espaçamentos adjacentes,

> rᵢ = min(sᵢ, sᵢ₊₁) / max(sᵢ, sᵢ₊₁),

produz um número médio ⟨r⟩ que resume o grau de correlação local do espectro.

O ponto crítico é que, para classes universais, ⟨r⟩ assume valores característicos.

Em particular, para o GOE, a literatura estabelece um valor de referência aproximadamente constante:

> ⟨r⟩\_GOE ≈ 0.5359

enquanto para espectros não correlacionados o valor típico é substancialmente menor:

> ⟨r⟩\_nc ≈ 0.386

Ao aplicar o protocolo do **Notebook 07** ao operador *M*, observa-se que, em regimes adequados de *N* e *X*₀, o valor medido de ⟨r⟩ aproxima-se sistematicamente do valor de referência do GOE.

Essa aproximação é robusta sob variações moderadas de parâmetros do protocolo (bulk, janela logarítmica e perturbações numéricas mínimas), indicando que não se trata de uma coincidência localizada.

## Rigidez global do espectro

A repulsão local entre níveis é apenas uma parte da assinatura universal.

Uma segunda característica, independente, é a rigidez estatística: a flutuação do número de autovalores em intervalos espectrais cresce de forma muito mais lenta do que em espectros não correlacionados.

A variância numérica Σ²(L), definida no capítulo anterior, mede exatamente essa flutuação.

O **Notebook 07** demonstra que, para regimes em que *P(s)* apresenta supressão em *s* = 0 e ⟨r⟩ se aproxima do valor de referência do GOE, a curva empírica de Σ²(L) abandona o crescimento linear (Σ²(L) ∼ L) — característico de sistemas do tipo Poisson — para assumir um **crescimento logarítmico** (Σ²(L) ∼ ln L).

Essa transição constitui uma evidência robusta da rigidez espectral do operador *M*. Ela indica que os níveis não apenas se repelem localmente, mas preservam correlações de longo alcance que estabilizam a estrutura do sistema.

Duas estatísticas independentes — local (*P(s)*) e global (Σ²) — convergem, assim, para o reconhecimento da mesma classe universal.

## Determinismo e universalidade

Há um aspecto que merece ser explicitado.

O GOE é tradicionalmente introduzido como um ensemble aleatório de matrizes simétricas reais. A universalidade observada nesse contexto refere-se ao fato de que muitas famílias de operadores, sob condições amplas, exibem as mesmas estatísticas no bulk espectral.

No presente trabalho, o operador *M* não é aleatório. Ele é construído deterministicamente a partir de uma função aritmética elementar e de uma mudança de escala fixa.

O ponto observado aqui é, portanto, mais restrito e mais concreto:

> um operador determinístico, construído exclusivamente a partir de contagem de primos e simetrização, pode exibir estatísticas espectrais compatíveis com a classe universal do GOE.

Nada além disso é reivindicado.

O que esta observação estabelece é um fato experimental: a classe universal pode emergir sem que qualquer aleatoriedade externa seja injetada no procedimento.

## Parâmetros do protocolo e estabilidade do fenômeno

Para evitar que o reconhecimento da classe universal dependa de escolhas arbitrárias, é necessário explicitar quais parâmetros do protocolo afetam o resultado e em que sentido.

No **Notebook 07**, três parâmetros exercem papel dominante:

- `span`, que controla a extensão da janela logarítmica e, portanto, a variabilidade interna do sinal amostrado;
- `jitter`, que introduz uma perturbação numérica mínima, reduzindo efeitos artificiais de alinhamento;
- `alpha`, que define o bulk analisado, minimizando efeitos de borda.

O fenômeno relevante não é a obtenção de um valor exato em uma configuração única, mas a estabilidade qualitativa das assinaturas (repulsão local, valor de ⟨r⟩ e rigidez) sob variações moderadas desses parâmetros.

Quando essa estabilidade se observa, o reconhecimento de classe deixa de ser uma coincidência e passa a ser um diagnóstico.

## Delimitação do que foi reconhecido

É essencial manter a distinção entre três níveis:

1. **Construtivo** — *M* foi definido por uma expressão explícita e determinística.
2. **Observacional** — estatísticas espectrais foram medidas em regimes grandes de *N* e em escalas elevadas *X*₀.
3. **Classificatório** — as assinaturas medidas foram comparadas com padrões universais conhecidos.

O terceiro nível não altera os dois primeiros. Ele apenas nomeia um comportamento observado.

Neste capítulo, o comportamento reconhecido é o pertencimento estatístico do espectro do operador *M*, em regimes adequados, à classe universal do GOE.

## Ponto de repouso

Até aqui:

- o protocolo estatístico foi aplicado ao espectro do operador *M* em regimes ampliados;
- múltiplas estatísticas independentes apontaram para a mesma classe espectral;
- o comportamento observado foi identificado como compatível com a classe GOE;
- nenhum novo objeto foi introduzido e nenhuma hipótese adicional foi assumida.

No próximo capítulo, investigaremos como esse diagnóstico se comporta sob varreduras sistemáticas de escala e sob modificações controladas do operador, delimitando as condições mínimas para a emergência da universalidade observada.

---

[⬅ Capítulo Anterior](./06_regimes_de_escala_e_estatisticas_espectrais.md) | [Sumário](../../index.md) | [Próximo Capítulo](./08_lente_descoberta.md)

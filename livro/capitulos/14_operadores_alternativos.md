# 14. Onde Mora o Caos? — Testando Operadores Alternativos

> *Se você arrasta uma rede com malha de cinco centímetros no mar,*  
> *a sua conclusão será que não existem peixes menores que cinco centímetros.*  
> *Mas isso é um fato sobre os peixes do mar, ou sobre a sua rede?*  
> — Arthur Eddington

## A última dúvida

Os capítulos anteriores estabeleceram um resultado forte: ao observar o sinal aritmético dos primos na escala logarítmica, o espectro do operador construído exibe, de forma robusta, estatísticas de correlação espectral indistinguíveis, no *bulk*, daquelas associadas à classe GOE, enquanto a observação linear conduz sistematicamente ao regime de Poisson.

No entanto, uma dúvida legítima permanece.

O operador central deste trabalho foi definido, até aqui, por um *kernel de cosseno*, da forma

$$
M_{ij} \propto \cos(f_i \cdot \log x_j) + \cos(f_j \cdot \log x_i),
$$

onde $f_i = \Delta_\pi(x_i)$.

É natural perguntar se a dualidade observada, Poisson na escala linear e GOE na escala logarítmica, é uma propriedade intrínseca do sistema aritmético, ou se poderia ser um artefato específico da escolha funcional do kernel.

Em outras palavras:

*o caos reside nos primos, ou no operador que escolhemos para observá-los?*

Este capítulo é dedicado a enfrentar essa questão de forma direta.

## A troca do instrumento

O cosseno não é uma função arbitrária. Ele surge naturalmente como a parte real de uma fase complexa:

$$
\cos(\theta) = \text{Re}(e^{i\theta}).
$$

Uma generalização imediata, portanto, consiste em abandonar a projeção real e trabalhar diretamente com a fase complexa completa.

Introduzimos assim um operador alternativo, definido por um *kernel de fase*:

$$
M'_{ij} = e^{i \cdot f_i \cdot \log x_j}.
$$

Esse operador não é simétrico real, mas carrega a mesma informação estrutural fundamental: a interação entre o sinal aritmético $f_i$ e a escala logarítmica de $x_j$.

A motivação deste teste é simples e rigorosa: se a estatística GOE observada anteriormente for consequência da interação profunda entre o sinal dos primos e a escala de observação, e não da forma particular do cosseno, então a substituição do kernel não deve destruir o fenômeno.

## Hipótese operacional

A hipótese testada neste capítulo pode ser formulada de maneira objetiva:

> Se a dualidade Poisson/GOE for estrutural, então operadores alternativos, construídos a partir da mesma informação aritmética e observados nas mesmas escalas, devem exibir o mesmo comportamento estatístico.

Em particular, esperamos observar:

- estatística de Poisson na escala linear;
- estatística compatível com GOE na escala logarítmica;
- estabilidade desses resultados sob a troca do kernel.

## O laboratório de operadores

O **Notebook 14** (`14_operadores_alternativos.ipynb`) [![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/costaalv/descobrindo_caos/blob/main/notebooks/14_operadores_alternativos.ipynb) implementa este teste de forma controlada.

Foi introduzido um seletor que permite alternar entre o *kernel de cosseno* e o *kernel de fase*, mantendo inalterados:

- o sinal aritmético $\Delta_\pi(x)$;
- os regimes de observação (linear e logarítmico);
- o protocolo estatístico aplicado ao espectro.

Essa abordagem garante que qualquer diferença observada seja atribuível exclusivamente à forma do operador — e não a mudanças colaterais no método.

## Resultado: invariância estatística

O resultado do experimento é inequívoco.

A substituição do kernel de cosseno pelo kernel de fase **não altera** o diagnóstico estatístico:

- na escala linear, o espectro permanece compatível com Poisson;
- na escala logarítmica, o espectro continua exibindo repulsão de níveis, rigidez global e valores de referência compatíveis com GOE.

Essa invariância não é trivial. Ela demonstra que a dualidade estatística observada não é um artefato funcional, mas uma propriedade robusta do sistema subjacente.

## Onde o caos realmente reside

O teste com operadores alternativos permite agora localizar com precisão a origem do fenômeno.

O caos observado:

- não reside na forma específica do kernel;
- não é criado pelo operador;
- não depende de uma escolha funcional delicada.

Ele emerge da combinação de dois elementos fundamentais:

1. a estrutura aritmética intrínseca do sinal $\Delta_\pi(x)$;
2. a observação desse sinal na escala logarítmica natural dos primos.

O operador atua apenas como um instrumento de leitura. Trocar o instrumento não altera a música.

Embora o operador de fase seja complexo, as estatísticas observadas coincidem com aquelas previamente identificadas no regime ortogonal, indicando que a classe estatística relevante é determinada pela estrutura do sinal e não pela representação escolhida.

---

## Ponto de repouso

Até aqui, foi examinada de forma sistemática a dependência do fenômeno em relação à forma específica do operador. Verificou-se que kernels funcionalmente distintos conduzem ao mesmo diagnóstico estatístico, e que a dualidade entre regimes do tipo Poisson e GOE permanece invariável sob essa substituição.

Com isso, a origem do comportamento observado pôde ser isolada com clareza: ela não reside em detalhes formais da construção, mas na interação entre o sinal aritmético dos primos e a escala de observação adotada.

Este capítulo encerra, portanto, a investigação sobre possíveis artefatos operacionais.

Nos capítulos seguintes, o foco se desloca das causas para as consequências dessa robustez. Investigaremos o que é efetivamente universal, quais perturbações podem ser introduzidas sem destruir o regime observado e quais limites naturais emergem da própria estrutura identificada.

---

[$\gets$ Capítulo Anterior](./13_varreduras_escala.md) | [Sumário](../../index.md) | [Próximo Capítulo $\to$](./15_alturas_estratosfericas.md)

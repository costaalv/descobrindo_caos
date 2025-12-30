# Confidencialidade — cifrar e decifrar

## Cifragem

A demonstração prossegue com o verbo **cifrar**, executado em modo total.

Na CIP, a cifragem utiliza uma matriz associada ao **índice espectral ímpar** do SDK. Blocos do próprio arquivo são projetados nessa base para gerar um fluxo determinístico de cifragem.

Não existem chaves privadas persistentes, segredos humanos ou parâmetros externos envolvidos no processo.

Ao final da operação, o sistema produz automaticamente:

- o artefato cifrado;
- a chave correspondente;
- a auditoria da operação.

Esses elementos são organizados de forma determinística na estrutura interna `.cip`.

A cifragem não é uma camada opaca. Ela produz artefatos explícitos, rastreáveis e auditáveis.

## Decifragem e reversibilidade

Na etapa de **decifrar**, o arquivo original é reconstruído integralmente a partir:

- do artefato cifrado;
- da chave CIP correspondente.

A demonstração confirma a **reversibilidade exata** do processo.

No notebook, uma comparação **byte a byte** entre:

- o arquivo original;
- o arquivo decifrado

confirma igualdade estrita de conteúdo.

A decifragem não produz uma aproximação semântica nem uma reconstrução tolerante. Ela reconstitui exatamente o artefato original, sem perda, compressão ou ajuste.

## Leitura operacional da camada de confidencialidade

A camada de confidencialidade demonstrada no notebook `01_cip_demo.ipynb` pode ser resumida em um fato observável:

1. o ciclo completo de cifragem e decifragem preserva exatamente o conteúdo original.

Esse fato não é apresentado como premissa, mas como **verificação empírica direta**.

O leitor executa:

- `cifrar` sobre um arquivo em modo total;
- `decifrar` utilizando a chave correspondente;
- uma comparação byte a byte entre entrada e saída.

O resultado confirma igualdade integral dos conteúdos.

Do ponto de vista do protocolo, essa reversibilidade estabelece dois pontos adicionais:

- **Determinismo operacional**  
  Para um par consistente (artefato cifrado, chave CIP), o resultado da decifragem é único, reprodutível e independente de plataforma.

- **Encadeamento auditável**  
  Confidencialidade e integridade não são dissociadas. O artefato cifrado e sua chave são produzidos com auditoria explícita, permitindo inspeção posterior, rastreabilidade e reprodução da operação.

A validade da camada de confidencialidade não decorre de argumento teórico, mas da possibilidade de execução direta e verificação objetiva.

# Interoperabilidade Estrutural entre SDKs

## Verificação cruzada com chaves externas

O notebook `02_cip_demo_interop.ipynb` demonstra uma propriedade central do protocolo: a **interoperabilidade estrutural** entre chaves emitidas por SDKs distintos.

No experimento, o mesmo arquivo público é assinado em ambientes diferentes:

- uma chave é gerada em Linux, por um SDK associado ao índice espectral **IDX 18**;
- outra chave é gerada em Windows, por um SDK associado ao índice espectral **IDX 20**.

Ambas as chaves são verificadas com sucesso por um único binário CIP local, executado em ambiente neutro (Google Colab), associado a um índice espectral distinto (**IDX 0**).

## Papel do índice espectral (IDX)

Cada índice espectral define uma **base harmônica própria**, resultando em chaves estruturalmente distintas para o mesmo arquivo.

Essa diversidade é intencional.

Quando a chave verificada é externa ao SDK local, a CIP utiliza a **matriz espectral embutida na própria chave**. O verificador local atua apenas como executor determinístico da estrutura descrita na chave, e não como árbitro dependente de ambiente.

O IDX altera a forma da assinatura, não o critério de validade.

## Rejeição consistente sob corrupção mínima

Ao introduzir uma corrupção mínima no arquivo, a alteração de um único bit, ambas as chaves (Linux IDX 18 e Windows IDX 20) rejeitam o arquivo corrompido quando verificadas pelo mesmo binário local.

Esse resultado evidencia que a decisão de integridade depende exclusivamente da coerência estrutural entre:

- o conteúdo do arquivo;
- a base harmônica (IDX);
- a estrutura matricial registrada na chave.

Sistema operacional, compilador ou ambiente de execução não interferem no resultado.

## Encadeamento com o corpo do livro

Este apêndice não amplia o argumento matemático apresentado nos capítulos anteriores. Ele cumpre outra função: mostrar que a estrutura identificada é **operável, interoperável e verificável de forma cruzada**.

O leitor não é convidado a acreditar. É convidado a executar, alterar, quebrar e verificar novamente.

Se o protocolo funciona, ele se sustenta por execução direta. Se não funcionasse, nenhuma formulação teórica o salvaria.

## Régua única como condição de existência do protocolo

A interoperabilidade demonstrada neste apêndice não é um efeito colateral da implementação. Ela decorre de uma condição estrutural fundamental: a existência de uma **régua única e universal**.

Na Cifra de Integridade Primal (CIP), a régua espectral:

- não é ajustável;
- não é negociável;
- não depende de contexto institucional.

Os diferentes índices espectrais não introduzem réguas distintas. Eles definem apenas **bases harmônicas diferentes**, todas compatíveis com a mesma régua estrutural.

Se réguas distintas fossem permitidas, a interoperabilidade se perderia imediatamente.

> A decisão de integridade é universal ou não é.

É essa unicidade que permite que:

- um arquivo assinado em um ambiente seja verificado em outro;
- chaves geradas por SDKs distintos sejam aceitas pelo mesmo verificador;
- a decisão de integridade independa de sistema operacional ou fornecedor.

## Deslocamento de confiança e natureza pública do protocolo

Este apêndice técnico transforma uma tese matemática em uma **prova de conceito tecnológica verificável**.

A CIP não compete com mecanismos clássicos de hash ou criptografia por desempenho. Seu foco é outro.

Enquanto soluções convencionais operam sobre **confiança delegada**, comitês, autoridades certificadoras e consenso institucional, a CIP opera sobre **confiança demonstrada**.

Se a matemática que a fundamenta falhar, a própria estrutura aritmética falha. Essa é a definição de uma confiança implacável.

## Notebooks como prova de soberania

A escolha por notebooks autoexecutáveis não é pedagógica, mas estrutural.

Ela demonstra que o protocolo é:

- leve;
- autocontido;
- independente de fornecedores;
- verificável por qualquer parte interessada.

A matemática que fundamenta a CIP não pode ser sequestrada. Isso confere ao protocolo um caráter de **soberania técnica**.

## Bem público e sustentabilidade mínima

A CIP não propõe um produto, mas uma régua pública de integridade.

Por essa razão:

- seu uso é irrestrito e gratuito no setor público;
- no setor privado, sua sustentabilidade é garantida por uma contribuição simbólica:
  **R$ 0,01 por operação que efetivamente gera valor**.

As operações de **assinar** e **cifrar** são sempre gratuitas. As operações de **verificar** e **decifrar** sustentam o ecossistema de forma mínima e transparente.

Essa escolha não é mercadológica. Ela é estrutural.

Este apêndice encerra a obra não como promessa, mas como demonstração executável: a integridade pode ser uma propriedade matemática objetiva,
e não um acordo social frágil.

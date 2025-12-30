# Apêndice Técnico — Demonstração Operacional da CIP

## Demonstração Operacional do Protocolo CIP

A **Cifra de Integridade Primal (CIP)** é um protocolo público de integridade e confidencialidade digital baseado exclusivamente em estrutura matemática.  
Este apêndice não introduz novos conceitos teóricos. Seu objetivo é **demonstrar, por execução direta e reprodutível**, que os princípios desenvolvidos ao longo do livro podem ser aplicados em um protocolo computacional real, determinístico e auditável.

A demonstração é inteiramente operacional:  
o leitor é convidado a executar os experimentos, observar os resultados e verificar sua reprodutibilidade.

Não são utilizadas chaves privadas, segredos computacionais, infraestrutura de certificação ou pressupostos institucionais.  
Todas as operações decorrem exclusivamente da estrutura interna dos arquivos e das matrizes espectrais associadas ao SDK utilizado.

## Ambiente de demonstração

A demonstração é acompanhada por dois notebooks executáveis, que constituem o laboratório empírico do apêndice:

- **`01_cip_demo.ipynb`**  
  Demonstra o funcionamento operacional dos quatro verbos do protocolo:
  **assinar**, **verificar**, **cifrar** e **decifrar**.

- **`02_cip_demo_interop.ipynb`**  
  Demonstra a interoperabilidade estrutural da CIP entre chaves emitidas por SDKs distintos, associados a diferentes índices espectrais (IDX).

Ambos os notebooks:

- são executáveis em ambiente controlado (Google Colab);
- utilizam o binário CIP em C++;
- não incorporam mecanismo de contagem de operações;
- executam exclusivamente operações determinísticas do protocolo.

O binário atua apenas como executor do método descrito ao longo do livro.  
Nenhum ajuste empírico, treinamento, heurística ou parâmetro oculto é utilizado.

## Escopo da demonstração

A demonstração está organizada em três blocos operacionais independentes:

1. **Integridade**  
   Assinatura estrutural de arquivos e verificação binária de integridade  
   (verbos **assinar** e **verificar**).

2. **Confidencialidade**  
   Cifragem e decifragem reversível de arquivos  
   (verbos **cifrar** e **decifrar**).

3. **Interoperabilidade estrutural**  
   Verificação e decifragem cruzadas entre SDKs distintos, sem quebra de integridade.

Cada bloco é demonstrado por execução direta, com observação explícita dos resultados esperados e dos casos de falha.

O objetivo não é demonstrar desempenho ou segurança por obscuridade,  
mas evidenciar que a estrutura espectral desenvolvida no corpo do livro sustenta um protocolo funcional, verificável e independente de plataforma.

Nos capítulos seguintes do apêndice, cada bloco é apresentado separadamente, com foco exclusivo na operação observável e em seus resultados.

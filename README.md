# Template de Pac-Man em C — Programação II

Material de apoio ao Trabalho Prático 1, Etapa 1, da disciplina de Programação II da UFES. O repositório reúne interfaces em C, casos de entrada e saída, objetos compilados de referência e um corretor em Bash para uma simulação de Pac-Man.

Este é o template da atividade: a implementação do aluno deve ser adicionada em `Respostas/<Nome>/`. Não há arquivos `.c` de solução neste repositório.

## Conteúdo

| Caminho | Finalidade |
| --- | --- |
| [`Includes/tMapa.h`](Includes/tMapa.h) | Mapa, paredes, comidas e acesso aos túneis |
| [`Includes/tPacman.h`](Includes/tPacman.h) | Personagem, histórico de movimentos, trilha e estatísticas |
| [`Includes/tPosicao.h`](Includes/tPosicao.h) | Coordenadas, cópia e comparação de posições |
| [`Includes/tMovimento.h`](Includes/tMovimento.h) | Direções e registro de ações significativas |
| [`Includes/tTunel.h`](Includes/tTunel.h) | Acessos e deslocamento por túneis |
| [`Casos/`](Casos/) | 30 casos com `mapa.txt`, `entrada.txt` e respostas em `saida/` |
| [`Gabarito-obj/`](Gabarito-obj/) | Objetos compilados de referência para composição das avaliações |
| [`correcao.sh`](correcao.sh) | Compilação, execução dos casos, comparação de resultados e avaliação de memória |
| [`pontuacao.txt`](pontuacao.txt) | Pesos por módulo e por arquivo de saída |

As interfaces exercitam structs, ponteiros, matrizes, alocação dinâmica, cópia de estruturas e separação de responsabilidades em módulos C. Os comentários dos headers descrevem os contratos esperados.

## Preparar uma implementação

Use Linux ou WSL com Bash 4+, GCC, GNU `getopt`, GNU Coreutils (`timeout`) e `bc`. A avaliação de memória usa Valgrind. Os objetos de referência versionados são ELF de 64 bits para x86-64; outras plataformas podem exigir os objetos adequados fornecidos pela disciplina.

Na raiz do repositório:

```bash
mkdir -p Respostas/SeuNome
```

Coloque nessa pasta os arquivos `.c` e `.h` da sua solução, incluindo `main.c`, respeitando as interfaces e o enunciado. Depois execute:

```bash
bash correcao.sh
```

O corretor cria `Resultados/`, `Resultado.csv` e `log.txt`. Ele compila módulos separadamente e combina partes da solução com os objetos de referência. Por isso, este template não possui um comando de build independente de uma implementação.

Para conferir apenas a sintaxe do script, sem compilar nem executar soluções:

```bash
bash -n correcao.sh
```

### Opções do corretor

Os nomes abaixo são os aceitos pelo script; as duas primeiras opções **desativam** verificações:

| Opção | Efeito |
| --- | --- |
| `--valgrind` | Executa sem a análise do Valgrind |
| `--resultados` | Ignora a avaliação dos resultados |
| `--interfacefixa` | Usa as interfaces de `Includes/` na correção |
| `--professor` | Regenera o material de referência a partir de `Gabarito-src/` |

O modo `--professor` depende de fontes que não estão no repositório e recria objetos, interfaces e saídas de referência. Não é necessário para executar a correção de uma solução de aluno.

## Exemplo de caso

O [caso 01](Casos/01/) contém um [mapa](Casos/01/mapa.txt) e uma [sequência de comandos](Casos/01/entrada.txt), com movimentos `w`, `a`, `s` e `d`. Suas [saídas de referência](Casos/01/saida/) incluem o estado do tabuleiro, a inicialização, a trilha, o resumo, o ranking e as estatísticas.

O corretor passa o diretório do caso como argumento ao programa e também redireciona `entrada.txt` para a entrada padrão. Consulte o enunciado para o contrato completo de leitura e de geração dos arquivos.

## Origem e limites

Este repositório preserva material didático de Programação II. O histórico versionado identifica Cezar Gobbo no desenvolvimento do corretor; as interfaces, os casos e os objetos de gabarito são apresentados como recursos da disciplina, não como implementação autoral do proprietário desta cópia.

O README original direcionava aos [exercícios gerais de Programação II da UFES](https://github.com/prog-II-ufes/exercicios-gerais), com instruções complementares, e informava que o enunciado completo estava no Classroom. Dúvidas sobre critérios e enunciado devem ser encaminhadas aos monitores ou professores.

A sintaxe Bash do corretor foi verificada. A correção completa depende de uma solução em `Respostas/`, das ferramentas listadas e de compatibilidade com os objetos fornecidos; não foi executada nesta revisão documental.

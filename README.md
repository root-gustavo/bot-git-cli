# LENA IA CLI

## Comando Inicial:
```bash
lena <mensagem> --<comando>
```
## Comandos:

| Comando    | Descrição                         |
| ---------- | --------------------------------- |
| `--branch` | Gera nomes de branch              |
| `--commit` | Gera sugestões de commit          |
| `--pr`     | Gera título e descrição da branch |

## Funcionamento Inicial:

* Escrita da IA completamente em inglês
* Quando ela gerar um nome de branch, vai perguntar se você está satisfeito: `(Y) ou (N)`

  * Se não estiver satisfeito, ela irá refazer a sugestão até gerar uma boa opção
  * Se a sugestão for útil, ela será salva em `JSON`, adicionando à **memória da IA** para que aprenda e melhore futuras recomendações
* Para `PRs`, ela vai sugerir título e descrição do pull request:

  * Vai detectar em qual branch você está e analisar o nome da branch
  * Vai também verificar todos os commits do branch para aumentar a precisão da sugestão

## Modelo da IA

* `MPT-7B-Instruct` - (light version)
## O que ela será?

* Um arquivo `.exe` gerado com `PyInstaller`
* Armazenará a **memória da IA** em `JSON`
* Permitirá o uso dos comandos da IA via terminal
* Disponibilizará descrição de funcionamento com `--help`

## Customização de estilo de commit e branch

- Lena permitirá configurar prefixos de commit e branch, como feat/, fix/, chore/, garantindo consistência no padrão do projeto.
- Essa funcionalidade funciona de forma similar a ferramentas que obrigam o uso de prefixos, mas integrada diretamente na IA, mantendo a flexibilidade e automação.

## Memória da IA

* Lena mantém **memória separada em três arquivos JSON**:

  * `memory_commits.json` > histórico de commits aprovados
  * `memory_branches.json` > histórico de nomes de branch aprovados
  * `memory_prs.json` > histórico de títulos e descrições de PR aprovados
  
* Cada comando carrega **apenas a memória relevante**, garantindo rapidez e eficiência.
* Essa separação permite que Lena **aprenda de forma incremental**, mesmo em projetos com muitos commits, gerando sugestões mais precisas e consistentes.
* Mantém os arquivos leves e organizados, facilitando manutenção e futuras melhorias.
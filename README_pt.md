<h1 align="center">OpenAI Codex CLI</h1>
<p align = "Center"> agente de codificação leve que é executado no seu terminal </p>

<p align = "Center"> <code> npm i -g @openai/codex </code> </p>

! [Codex Demo GIF usando: Codex "Explique esta base de código para mim"] (./. Github/Demo.gif)

----

<tahtands>
<summary> <strong> ÍNDER </strong> </summary>

<!-Inicie o TOC->

-[Isenção de Tecnologia Experimental] (#Experimental-Technology-Disclaimer)
- [Quickstart] (#QuickStart)
- [Por que Codex?] (#Why-Codex)
-[Modelo de Segurança e Permissões] (#Modelo de Segurança-Permissões)
-[Detalhes de sandboxing da plataforma] (#plataforma-sandboxing-details)
- [Requisitos do sistema] (#requisitos de sistema)
- [Referência da CLI] (#cli-reference)
-[Memory & Project Docs] (#Memory-Project-Docs)
-[modo não interativo / IC] (#não interativo-modo CI)
-[Rastreio / registro verboso] (#Rasting-Verbose-Logging)
- [Receitas] (#Receitas)
- [Instalação] (#Instalação)
- [Guia de configuração] (#Configuration-Guide)
-[Parâmetros básicos de configuração] (#parâmetros básicos de configuração)
-[Configuração personalizada do provedor de IA] (#Configuração personalizada-AI-Provider)
- [Configuração da história] (#Configuração do History)
- [Exemplos de configuração] (#Exemplos de configuração)
-[Exemplo de configuração completa] (#Exemplo de configuração completa)
- [Instruções personalizadas] (#Instrução personalizada)
-[Configuração das variáveis do ambiente] (#Environment-Variables-Setup)
- [FAQ] (#FAQ)
-[Uso de retenção de dados zero (ZDR) (#Zero-Data-retention-ZDR-Usage)
-[Codex Open Source Fund] (#Codex-Open Source-Fund)
- [contribuindo] (#contribuindo)
- [Fluxo de trabalho de desenvolvimento] (#Development-WorkFlow)
-[GIT GAYS com Husky] (#Git-Hooks-With-Husky)
- [Debugging] (#depuração)
-[Escrevendo alterações de código de alto impacto] (#escrevi-o-altíssimo-código-código)
-[Abrindo uma solicitação de tração] (#Abertura-a-Pull-Request)
- [Processo de revisão] (#revisão-processo)
- [Valores da comunidade] (#valores comunitários)
- [Obtendo ajuda] (#obtendo help)
-[Contrato de licença colaboradora (CLA)] (#colaborador-licencie-cla-CLA)
- [Correções rápidas] (#Fixes Quicks)
- [liberando `codex`] (#liberação-codex)
-[Opções de construção alternativas] (#opções alternativas-build)
-[Nix Flake Development] (#Nix-Flake-Desenvolvment)
-[Segurança e AI Responsável] (#Security-Responsible-AI)
- [Licença] (#Licença)

<!-final Toc->

</tafits>

----

## Isenção de responsabilidade experimental de tecnologia

O CodEx CLI é um projeto experimental sob desenvolvimento ativo. Ainda não está estável, pode conter bugs, recursos incompletos ou sofrer mudanças de quebra. Estamos construindo -o ao ar livre com a comunidade e bem -vindo:

- Relatórios de bug
- solicitações de recursos
- Puxe solicitações
- Boas vibrações

Ajude -nos a melhorar arquivando problemas ou enviando PRs (consulte a seção abaixo para contribuir)!

## QuickStart

Instale globalmente:

`` `shell
npm install -g @openai/codex
`` `

Em seguida, defina sua chave da API do OpenAI como uma variável de ambiente (pule isso ao usar um servidor local):

`` `shell
Exportar OpenAI_API_KEY = "Your-Api-Key-Here"
`` `

> ** NOTA: ** Este comando define a chave apenas para sua sessão de terminal atual. Você pode adicionar a linha `export` ao arquivo de configuração do seu shell (por exemplo,` ~/.zshrc`), mas recomendamos a configuração da sessão. ** Dica: ** Você também pode colocar sua chave da API em um arquivo `.env` na raiz do seu projeto:
>
> `` `Env
> Openai_api_key = Your-Api-Key-Here
> `` `
>
> A CLI carregará automaticamente variáveis de `.env` (via` dotenv/config`).

Se você estiver executando um servidor local compatível com o OpenAI, você pode pular a chave da API e
Use a bandeira `--Local` ou especifique um terminal personalizado com` --api-Base`:

`` `shell
Codex -Local
# ou
Codex-API-BASE http: // localhost: 11434/v1
`` `

Alternativamente, defina `codex_api_base` em seu ambiente para configurar o padrão
endpoint.

<tahtands>
<summary> <strong> use <code>-provedor </code> para usar outros modelos </strong> </summary>

> O Codex também permite que você use outros fornecedores que suportem a API de conclusão de bate -papo do OpenAI. Você pode definir o provedor no arquivo de configuração ou usar o sinalizador `--provider`. As opções possíveis para `--provider` são:
>
> - Openai (padrão)
> - OpenRouter
> - Azure
> - Gêmeos
> - Ollama
> - Mistral
> - Deepseek
> -
> - грач
> - Arceai
> - Qualquer outro provedor que seja compatível com a API Openai
>
> Se você usar um provedor que não seja o OpenAI, precisará definir a chave da API para o provedor no arquivo de configuração ou na variável de ambiente como:
>
> `` `shell
> exportar <vidos> _api_key = "your-api-Key-here"
> `` `
>
> Se você usar um provedor não listado acima, também deverá definir o URL base para o provedor:
>
> `` `shell
> Exportar <vidos> _base_url = "https: // your-provider-api-Base-url"
> `` `

> Ao executar um servidor local, você pode usar `codex_api_base` com o sinalizador`--Local`.

</tafits>
<br />

Execute interativamente:

`` `shell
códice
`` `

Ou execute com um prompt como entrada (e opcionalmente no modo `completo automático '):

`` `shell
Codex "Explique esta base de código para mim"
`` `

`` `shell
Codex-Modo de aprovação Full-AUTO "Crie o aplicativo mais extravagante
`` `

É isso - o codex vai andaime um arquivo, executá -lo dentro de uma caixa de areia, instalar qualquer
falta de dependências e mostre o resultado ao vivo. Aprovar as mudanças e
Eles estarão comprometidos com o seu diretório de trabalho.

----

## por que códice?

Codex CLI é construído para desenvolvedores que já ** vivem no terminal ** e desejam
Raciocínio no nível do chatgpt ** Plus ** O poder de realmente executar código, manipular
arquivos e iterate - tudo em controle de versão. Em suma, é _Chatringado
Desenvolvimento_ que entende e executa seu repositório.

- ** Configuração zero ** - Traga sua chave da API OpenAI e ela apenas funciona!
-** Aprovação automática completa, enquanto segura ** Executando a execução da rede deficiente e com o Directory Sandboxed
- ** Multimodal ** - Passe em capturas de tela ou diagramas para implementar recursos ✨

E é ** de código aberto ** para que você possa ver e contribuir para a forma como ele se desenvolve!

----

Modelo de segurança e permissões

Codex permite que você decida _ quanto muita autonomia_ o agente recebe e a política de aprovação automática via
`-sinalizador de modos de aprovação` (ou o prompt interativo de integração):

| Modo | O que o agente pode fazer sem perguntar | Ainda requer aprovação |
| --------------------------- | --------------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------- |
| ** sugestão ** <br> (padrão) | <li> Leia qualquer arquivo no repo | <li> ** All ** Arquivo grava/patches <li> ** qualquer ** comandos do shell arbitrário (além de ler arquivos) |
| ** Edição automática ** | <li> Leia ** e ** Aplicar gravações do Patch em arquivos | <li> ** todos os comandos ** shell |
| ** Auto completo ** | <li> Leia/gravação Arquivos <li> Execute os comandos do shell (rede desativada, grava limitada ao seu Workdir) | - |

Em ** Auto completo ** todo comando é executado ** Rede deficiente ** e confinado ao
Diretório de trabalho atual (além de arquivos temporários) para defesa em profundidade. Códice
também mostrará um aviso/confirmação se você começar em ** edit automático ** ou
** Full-AUTO ** enquanto o diretório não é rastreado por git, então você sempre tem um
rede de segurança.

Em breve: você poderá a lista de permissões específicas da lista
A rede permitiu, uma vez confiante em salvaguardas adicionais.

Detalhes de sandboxing da plataforma ###

O mecanismo de endurecimento que o Codex usa depende do seu sistema operacional:

- ** MacOS 12+** - Os comandos são embrulhados com ** Apple Seatbelt ** (`Sandbox -ExeC`).

- tudo é colocado em uma prisão somente leitura, exceto por um pequeno conjunto de
raízes graváveis (`$ pwd`,` $ tmpdir`, `~/.codex`, etc.).
- A rede de saída é fodidamente bloqueada_ por padrão - mesmo se um processo infantil
tenta 'curl' em algum lugar que falhará.

- ** Linux ** - Não há caixa de areia por padrão.
Recomendamos o uso do Docker para Sandboxing, onde o Codex se lançam dentro de um ** mínimo
imagem de contêiner ** e monta seu repo _read/write_ no mesmo caminho. UM
O script de firewall `iptables '/ipset' personalizado nega toda a saída, exceto o
API OPENAI. Isso lhe dá corridas determinísticas e reproduzíveis sem precisar
raiz no host. Você pode usar o script [`run_in_container.sh`] (./ codex-cli/scripts/run_in_container.sh) para configurar a caixa de areia.

----

## requisitos do sistema

| Requisito | Detalhes |
| ----------------------------- | --------------------------------------------------------------- |
| Sistemas operacionais | MacOS 12+, Ubuntu 20.04+/Debian 10+ ou Windows 11 ** via wsl2 ** |
| Node.js | ** 22 ou mais recente ** (LTS recomendado) |
| Git (opcional, recomendado) | 2.23+ para ajudantes de relações públicas embutidas |
| Ram | Mínimo de 4 GB (8-GB recomendado) |

> Nunca execute `sudo npm install -g`; Corrija as permissões NPM.

----

## CLI Referência

| Comando | Propósito | Exemplo |
| -------------------------------------- | ------------------------------------- | -------------------------------------- |
| `codex` | REPLETIVO INTERATIVO | `codex` |
| `codex" ... "` | Prompt inicial para repl interativo | `codex" corrigir erros de fiapos "` |
| `codex -q" ... "` | "Modo silencioso não interativo | `codex -q --json" explicou utils.ts "` |
| `Conclusão do Codex <Bash \ | Zsh \ | FISH>` | Script de conclusão da concha de impressão | `Codex Conclusão Bash` |

Sinalizadores de teclas: `--model/-m`,` --Approv-Mode/-a`, `--quiet/-q`,` --notify`, `--local` e` --api-Base`.

----

## Memória e documentos do projeto

Você pode fornecer instruções e orientações extras do Codex usando os arquivos `agents.md`. O Codex procura os arquivos `agents.md` nos seguintes locais e os mescla de cima para baixo:

1. `~/.Codex/agents.md` - orientação global pessoal
2. `Agents.md` no Repo Root - Notas de projeto compartilhadas
3. `Agents.md` no atual diretório de trabalho - sub -folder/especificações de recursos

Desative o carregamento desses arquivos com `--no-project-doc` ou a variável de ambiente` codex_disable_project_doc = 1`.

----

## modo não interativo / CI

Execute o codex sem cabeça em pipelines. Exemplo do github Ação Etapa:

`` `yaml
- Nome: Atualizar Changelog via códice
Run: |
npm install -g @openai/codex
Exportar OpenAI_API_KEY = "$ {{Secrets.openai_key}}"
Codex -um edit auto -edit -"Atualize Changelog para o próximo lançamento"
`` `

Defina `codex_quiet_mode = 1` para silenciar o ruído interativo da interface da interface.

## Rasting / Loging Verbose

Definir a variável de ambiente `Debug = true` imprime a solicitação completa da API e os detalhes da resposta:

`` `shell
Debug = Codex verdadeiro
`` `

----

## receitas

Abaixo estão alguns exemplos de tamanho de mordida que você pode copiar. Substitua o texto em cotações por sua própria tarefa. Consulte o [Guia de Promotamento] (https://github.com/openai/codex/blob/main/codex-cli/examples/prompting_guide.md) para obter mais dicas e padrões de uso.

| ✨ | O que você digita | O que acontece |
| --- | ------------------------------------------------------------------------------- | -------------------------------------------------------------------------- |
| 1 | `codex" Refactor o componente do painel para reagir ganchos "` | O Codex reescreve o componente da classe, executa `npm test` e mostra o diff.   |
| 2 | `codex" geram migrações SQL para adicionar uma tabela de usuários "` | Infina o seu ORM, cria arquivos de migração e os executa em um banco de dados de caixa de areia. |
| 3 | `Codex" Write Unit Testes para utils/date.ts "` | Gera testes, os executa e itera até que eles passem.              |
| 4 | `codex" Rename de granel *.jpeg -> *.jpg com git mv "` | Renomeia com segurança os arquivos e atualiza as importações/usos.                           |
| 5 | `codex" Explique o que este regex faz: ^(? =.*[a-z]). {8,} $ "` | Produz uma explicação humana passo a passo.                                  |
| 6 | `Codex" revise cuidadosamente este repo e propõe 3 PRs bem escopidos de alto impacto "` | Sugere PRs impactantes na base de código atual.                            |
| 7 | `Codex" Procure vulnerabilidades e crie um relatório de revisão de segurança "` | Encontra e explica bugs de segurança.                                          |

----

## Instalação

<Detalhes abertos>
<summary> <strong> do npm (recomendado) </strong> </summary>

`` `BASH
npm install -g @openai/codex
# ou
Yarn Global Add @Openai/Codex
# ou
bun install -g @openai/codex
# ou
pnpm add -g @openai/codex
`` `

</tafits>

<tahtands>
<summary> <strong> construir a partir da fonte </strong> </summary>

`` `BASH
# Clone o repositório e navegue até o pacote da CLI
Git clone https://github.com/openai/codex.git
CD Codex/Codex-Cli

# Enable Corepack
Corepack Ativar

# Instale dependências e construa
Instalação do PNPM
Build PNPM

# Linux-somente: Baixe binários de sandbox pré-construído (requer GH e ZSTD).
./scripts/install_native_deps.sh

# Obtenha o uso e as opções
Node ./dist/cli.js --help

# Execute a CLI construída localmente diretamente
Node ./dist/cli.js

# Ou vincular o comando globalmente para conveniência
Link pnpm
`` `

</tafits>

----

Guia de configuração ##

Os arquivos de configuração do Codex podem ser colocados no diretório `~/.codex/`, suportando os formatos YAML e JSON.

### parâmetros básicos de configuração

| Parâmetro | Tipo | Padrão | Descrição | Opções disponíveis |
| --------------------- | ------- | ---------- | ---------------------------------- | ---------------------------------------------------------------------------------------------- |
| `Model` | string | `O4-mini` | Modelo AI para usar | Qualquer nome de modelo que suporta API OpenAI |

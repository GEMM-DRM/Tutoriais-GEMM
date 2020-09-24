# UNIX Shell
Em este tutorial 🗒, você vai entrar na "telinha preta" 🖥 e vai aprender e exercitar alguns comandos básicos e indispensáveis.

## Colaboradores

* 👩🏻‍💻👩🏻‍🔬 MSc. Kelly J. Hidalgo Martinez
Microbióloga
Doutoranda em Genética e Biologia Molecular
Instituto de Biologia - UNICAMP
📱 Whastapp: +5519981721510
📧 Email: khidalgo@javeriana.edu.co

* 👨🏻‍💻👨🏻‍🔬 Victor Borin Centurion
Biomédico
Doutorando em Genética e Biologia Molecular
Instituto de Biologia - UNICAMP
📱 Whastapp: +5519982349780
📧 Email: vborincenturion@yahoo.com.br

* 👨🏻‍💻👨🏻‍🔬 Dr. Tiago Palladino Delforno
Biólogo
📧  Email: tiago.palladino@gmail.com


---

# Introdução
O shell Unix é uma ferramenta muito poderosa que permite que as pessoas façam coisas complexas com apenas algumas teclas. O uso do shell é fundamental para o uso de uma ampla variedade de ferramentas ⚒ de bioinformática 🖥. Este tutorial 🗒 vai servir para você fazer um uso eficaz desses recursos.

#### Importante
* Se você já conhece e entende os conceitos de **arquivo** 📄 e **pasta** 📁 , está pronto para iniciar este tutorial 🗒
* Sempre que você veja uma caixa como esta, é para você digitar na linha de  e oprimir [enter] :keyboard: para **rodar**.
```coffeescript=
comando
```
As vezes pode ser a saída do comando, o que se espera que você obtenha depois de escrever o comando e dar enter :keyboard:(rodar)
```coffeescript=
output
```
# Vamos lá :beginner: 

## Ingressar no servidor

- **Se você é aluno e/ou pesquisador do GEMM**, lembre que se você estiver **fora** das instalações do UNICAMP, você terá que se conectar na VPN. Como se faz isso? 🔗 [Aqui as instruções](https://www.ccuec.unicamp.br/ccuec/servicos/acesso_remoto_vpn)

- Se você é do time **Linux** ou **MacOS**: Abrir um terminal.

 *Linux*
![](https://i.imgur.com/xyX1M8T.png)

*MacOS*
![](https://i.imgur.com/d4W2xXE.png)


Escreva `ssh -x usuário@xxx.xxx.xx.xxx` 
substituindo `usuário` com seu nome de usuário e os "x" com o endereço que foram enviados no seu email depois de solicitado o acesso no servidor do GEMM. Dê enter. A continuação digite sua senha, vai parecer que não está escrevendo, mas acredite está escrevendo sim, dê enter. 
![](https://i.imgur.com/zchADD8.png)

se você não faz parte do **GEMM** então ingresse ao servidor que você tiver acesso ou se for rodar no sua maquina é só abrir o terminal. 
 
- Se é do time **Windows** abrir o **Putty**
   ![](https://i.imgur.com/mRkH25w.jpg)
    * Na caixinha "Host Name (or IP address)" coloque o endereço IP do servidor e na caixa port o número 22.
    * Clique em Open
    * Voilá! a famosa tela preta 👏🏼
![](https://i.imgur.com/lqLURRZ.png)
   * Em login as: coloque seu nome de `usuário` pro o servidor e enter
   * Deve aparecer assim:
   ![](https://i.imgur.com/44jyiHR.png)
   * Digite sua senha (não se poreocupe vai parecer que não está escrevendo, mas acredite que sim) e dê enter
   * Agora você está conectado remotamente no servidor
   ![](https://i.imgur.com/1Vq5RZr.png)

## Linha de comando
A linha de comando fala pro computador que o que tem que fazer.
A parte do sistema operativo encarregado do gerenciamento dos arquivos 📄 e diretorios (ou pastas) 📁 se chama **file system**. Ele organiza seus dados em **arquivos** 📄, que contêm informações e **diretórios** 📁, que contêm arquivos 📄 ou outros diretórios 📁. 
Há muitos comandos freqüentemente usados para criar, inspecionar 👀, renomear e excluir arquivos 📄 e diretórios 📁. Vamos começar a mexer com eles. 

### pwd (Print Working Directory)
Os diretórios 📁 são como lugares. Sempre que você está usando o shell, está em algum lugar **(Diretório)** 📁 de seu computador 💻, chamado **diretório de trabalho atual**. Os comandos somente lêem e gravam arquivos no diretório de trabalho atual, portanto, é **importante** :exclamation: saber onde você está antes de executar um comando. `pwd` mostra onde você está.
**Entrada**
```coffeescript=
pwd
```
**Saída**
```coffeescript=
/data/usuário
```
Para entender a organização de nosso servidor 🖥, dê uma olhada 👀 na figura. As pastas 📁 dados e análises é um exemplo de como você poderia organizar seus arquivos 📄 e diretórios 📁.
No topo da figura, está o **root directory**, que armazena tudo no nosso servidor 🖥. O simbolo dele é `/` 
⛔️**Não**⛔️ está permitido "passear" pelos outros diretórios, diferentes ao seu. 

Significa que você está dentro de sua pasta 📁 (`usuário`) que sua vez está dentro da pasta 📁 `/data`. E também sabemos que `/data` está armazenada dentro do **diretório raiz** 📁 `/`. Então o **caminho** a sua pasta é `/data/usuário`
![](https://i.imgur.com/VuRonXp.png)
 Não se confunda com o `/`. Tem dois significados, quando aparece na frente de um arquivo o diretório 📁, significa que aquilo está dentro do **diretório raiz**. Mas quando ele está dentro do **caminho**, só é um separador 👌🏼.


### Sintaxes da linha de comando
```coffeescript=
comando [opção] [arquivo]
```
O comando é separado das opções (ou argumentos, flags) e do arquivo 📄 por um espaço. Os argumentos podem mudar o comportamento do comando. E o arquivo 📄 fala pro comando sobre o que vai a operar (p.e. arquivos 📄 e diretórios 📁). As vezes argumentos e o arquivo 📄 são chamados de **parâmetros**. Um comando pode ter mais de um argumento e/ou arquivos 📄 e também poderia não ter nemhum dos dois. As opções usualmente tem um traço e uma letra (p.e. -h) ou dois traços e uma palavra (p.e. --help), **sem** espaço entre o(s) traço(s) e a letra/palavra. Vamos ver com exemplos práticos.
**Importante:**:exclamation: a linguagem usada no UNIX é sensível a letras maiúsculas e minúsculas, é um erro comúm. **Fique atento sempre**:exclamation:

### ls (listar)
Con o comando `ls` você pode ver (listar) o que tem dentro do **diretório atual de trabalho** 📁 
**Entrada**
```coffeescript=
ls
```
**Saída**
```coffeescript=

```
No nosso exemplo não tem nenhum elemento. Mas tranquil@ ✋🏼 vamos criar 📁 e arquivos 📄 daqui a pouco. 

Vocẽ pode usar o **argumento** `-F` para "falar" pro `ls` que indique o que é cada elemento. `/` significa que é uma 📁, o`*` qué um executável e se não tiver simbolo nenhum significa é uma arquivo 📄 plano.

O ***flag*** 🚩 `--help` 🆘 é bem importante:exclamation:, e ele pode ser usado em **qualquer** comando. Ele mostra mais informação sobre o comando, e como usar ele 🤙🏼.

**Entrada**
```coffeescript=
ls --help
```
**Saída**
```coffeescript=
Uso: ls [OPÇÃO]... [ARQUIVO]...
Lista informações sobre os ARQUIVOs (no diretório atual por padrão).
Lista as entradas em ordem alfabética se não for usada nenhuma opção -cftuvSUX
nem --sort.

Argumentos obrigatórios para opções longas também o são para opções curtas.
  -a, --all                  não ignora entradas começando com .
  -A, --almost-all           não lista as entradas implícitas . e ..
      --author               com -l, emite o autor de cada arquivo
  -b, --escape               emite escapes no estilo C para caracteres não-
                               gráficos
      --block-size=TAM       o tamanho considera blocos de TAM bytes; exemplo:
                               "--block-size=M" emite tamanhos em unidades de
                               1.048.576 bytes; veja o formato de TAM abaixo
  -B, --ignore-backups       não lista as entradas implícitas terminadas com ~
  -c                         com -lt: ordena por, e mostra, ctime (hora da
                               última modificação da informação de estado do
                               arquivo);
                               com -l: mostra o ctime e ordena por nome
                               demais casos: ordena por ctime
  -C                         lista as entradas em colunas
      --color[=QUANDO]       controla se usa cores para distinguir os tipos de
                               arquivo. QUANDO pode ser "never" (nunca),
                               "always" (sempre) ou "auto" (automaticamente)
  -d, --directory            lista os diretório em si, e não seu conteúdo
  -D, --dired                gera a saída projetada para modo "dired" do Emacs
  -f                         não ordena, habilita -aU, desabilita -ls --color
  -F, --classify             anexa indicador (um dos */=>@|) às entradas
      --file-type            similar, exceto que não anexa "*"
      --format=PALAVRA       "across" -x, "commas" -m, "horizontal" -x,
                               "long" -l, "single-column" -1,
                               "verbose" -l, "vertical" -C
      --full-time            o mesmo que -l --time-style=full-iso
  -g                         o mesmo que -l, mas não lista o dono
      --group-directories-first
                             lista os diretórios antes de listar os arquivos;
                               pode ser ampliado com a opção --sort, mas o uso
                               de --sort=none (-U) desabilita o agrupamento de
                               diretórios
  -G, --no-group             em lista longa (-l), não emite os nomes de grupo
  -h, --human-readable       com -l, e/ou -s, emite os tamanhos inteligível
                               para humanos (por exemplo, 1K 234M 2G)
      --si                   similar, mas usa potências de 1000, e não de 1024
  -H, --dereference-command-line
                             segue os links simbólicos listados na linha de
                               comando
      --dereference-command-line-symlink-to-dir
                             segue todo link simbólico da linha de comando
                               que apontar para um diretório
      --hide=PADRÃO          não lista entradas implícitas que coincidam com o
                               PADRÃO em sintaxe shell (ignorado quando se usa
                               -a ou -A)
      --hyperlink[=QUANDO]   nomes de arquivos de hyperlink; QUANDO pode ser
                             "always" (padrão), "auto" ou "never"
      --indicator-style=PALAVRA
                             anexa o indicador de tipo no estilo PALAVRA
                               para os nomes das entradas:
                               "none" (nenhum, padrão), "slash" (-p),
                               "file-type" (--file-type), "classify" (-F)
  -i, --inode                emite o número de índice de cada arquivo
  -I, --ignore=PADRÃO        não lista as entradas implícitas que coincidam
                               com o PADRÃO (em sintaxe shell)
  -k, --kibibytes            por padrão, blocos de 1024 bytes para uso do disco
  -l                         usa o formato de lista longa
  -L, --dereference          quando mostrar informações de um link simbólico,
                               mostra as do arquivo a quem ela referencia, e
                               não do arquivo tipo link em si
  -m                         preenche toda a largura com uma lista de entradas
                               separadas por vírgula
  -n, --numeric-uid-gid      como -l, mas lista usuário e grupo em números ID
  -N, --literal              emite nomes de entrada sem apas
  -o                         como -l, mas não lista informações sobre o grupo
  -p, --indicator-style=slash
                             anexa o indicador / aos diretórios
  -q, --hide-control-chars   emite ? em vez de caracteres não gráficos
      --show-control-chars   emite caracteres não gráficos como são (padrão
                               a menos que o programa seja o "ls" e a saída
                               seja um terminal)
  -Q, --quote-name           coloca os nomes das entradas entre aspas
      --quoting-style=PALAVRA
                             usa estilo de citação PALAVRA para os nomes das
                               entradas:
                               literal, locale, shell, shell-always,
                               shell-escape, shell-escape-always, c, escape
  -r, --reverse              inverte a ordem na ordenação
  -R, --recursive            lista os subdiretórios recursivamente
  -s, --size                 emite o tamanho de cada arquivo, em blocos
  -S                         ordena por tamanho de arquivo (maior primeiro)
      --sort=PALAVRA         ordena por PALAVRA em vez de pelo nome: none (-U),
                               size (-S), time (-t), version (-v),
                               extension (-X)
      --time=PALAVRA         com -l, mostra a hora como PALAVRA em vez do
                               horário de modificação: atime ou access ou
                               use (-u); ctime ou status (-c); também usa
                               o horário especificado como chave de ordenação
                               se --sort=time (mais novo primeiro)
      --time-style=ESTILO    com -l, mostra os horários usando o estilo ESTILO:
                               full-iso, long-iso, iso, locale ou +FORMATO;
                               FORMATO é interpretado como em "date"; se for
                               FORMATO1<newline>FORMATO2, FORMATO1 se aplica a
                               arquivos não recentes, e FORMATO2 aos recentes;
                               se ESTILO tem como prefixo "posix-", ESTILO
                               só faz efeito fora da localidade POSIX
  -t                         ordena pelo horário de modificação
                               (mais novos primeiro)
  -T, --tabsize=COLS         presume paradas de tabulação a cada COLS em vez
                               de 8
  -u                         com -lt: mostra e ordena por horário de acesso
                               com -l: mostra o horário de acesso e ordena
                               por nome; demais casos: ordena por horário
                               de acesso
  -U                         não ordena; lista na ordem do diretório
  -v                         ordem natural de números (de versão) com texto
  -w, --width=COLS           define largura saída com COLS. 0 significa
                               sem limite
  -x                         lista as entradas por linha em vez de por coluna
  -X                         ordena por ordem alfabética das extensões das
                               entradas
  -Z, --context              emite qualquer contexto de segurança de cada
                               arquivo
  -1                         lista um arquivo por linha. Com -q ou -b, evita \n
      --help     mostra esta ajuda e sai
      --version  informa a versão e sai

O argumento TAM é uma unidade opcional e inteiro (exemplo: 10K é 10*1024).
As unidades são K,M,G,T,P,E,Z,Y (vezes 1024) ou KB,MB,... (vezes 1000).

O uso de cor para distinguir tipos de arquivos é desabilitado por padrão e
com --color=never.  Com --color=auto, ls emite códigos de cor apenas quando
a saída padrão está conectada a um terminal.  A variável de ambiente LS_COLORS
pode alterar as configurações.  Use o comando dircolors configurá-la.

Status de saída:
 0 se OK;
 1 se problemas menores (ex.: sem acesso ao subdiretório);
 2 se sérios problemas (ex.: sem acesso ao argumento de linha de comando).

Página de ajuda do GNU coreutils: <http://www.gnu.org/software/coreutils/>
Relate erros de tradução do ls: <http://translationproject.org/team/pt_BR.html>
Documentação completa em: <http://www.gnu.org/software/coreutils/ls>
ou disponível localmente via: info "(coreutils) ls invocation"
```
Outro **flag** 🚩 interessante é: `ls -l`, que lista o conteúdo da pasta 📁 com informações extras, como as permisões, o tamanho, a data 📅 e hora 🕙 de criação, e o nome de cada um dos elementos. 

### mkdir (Make Dir)
Você já aprendeu a explorar 📁 e arquivos 📄, agora vai aprender como se criam eles. O comando `mkdir` serve para criar 📁. Vamos criar várias 📁📁
**Entrada**
```coffeescript=
mkdir dados
mkdir análises
mkdir tutorial
ls
```
**Saída**
```coffeescript=
análises/    dados/    tutorial/
```

#### *Tip* 💁🏻‍♀️ 
* Não 🚫 use espaços nos nomes de suas 📁 ou arquivos 📄 (p.e. ~~coleta 2020~~). Sempre separe as palavras com `-` ou `_` (p.e. `coleta_2020` ou `coleta-2020` 👍🏼)
* Não 🚫 comece nomes com `-`
* Dê para seus elementos nomes facíes de lembrar e escrever e que no possível descrevam o que contém.
* Não use caracteres espaciais :face_with_symbols_on_mouth: 
### cd (Change Directory)
O comando `cd` serve para trocar de **diretório atual de trabalho** 📁.
**Entrada**
```coffeescript=
cd dados/
```
Com isso você indicou pra 💻 que você quer estar agora dentro da 📁 `/data/usuário/dados`
**Entrada**
```coffeescript=
cd ..
```
O `..` significa a 📁 ***pai*** **do diretório atual de trabalho**. Confire com:
**Entrada**
```coffeescript=
pwd
```
**Saída**
```coffeescript=
/data/usuário
```
Agora entre na  📁 `análises/` e crie outra 📁 chamada `coleta_2020`, confira com `ls`
```coffeescript=
## Troque de pasta
cd análises/
## Crie a nova pasta
mkdir coleta_2020
## Confira
ls
```
**Saída**
```coffeescript=
coleta_2020/
```
**Entrada**
```coffeescript=
## Troque de pasta
cd coleta_2020/
```
Agora verifique onde você está com `pwd`, depois volte para sua 📁 `/data/usuário` 
**Entrada**
```coffeescript=
## Onde estou?
pwd
```
**Saída**
```coffeescript=
/data/análises/coleta_2020/
```
Por último volte para a 📁`/data/usuário` com `cd` em uma linha só. Lembre-se que os `..` significa 📁 pai do **diretório atual de trabalho**
**Entrada**
```coffeescript=
## Volte para duas pastas acima
cd ../../
## Confira
pwd
```
**Saída**
```coffeescript=
/data/usuário/
```

#### *Tip* 💁🏻‍♀️ 
Você pode usar a tecla Tab :keyboard: para autocompletar as palavras. Assim, economiza tempo ⏳, e evita erros de escrita, porque o 💻 só vai completar nomes que existam no 📁 **diretório atual de trabalho**. 
Só tem que escrever as primeiras letras da palavra, p.e col:
**Entrada**
```coffeescript=
## Troque de pasta
cd análises/col
```
Oprima :keyboard: [Tab]. Automaticamente se não existir nemhum outro elemento que comece por col, vai ser completada a palavra coleta_2020.
**Saída**
```coffeescript=
cd análises/coleta_2020
```
Se existir outro elemento que comece com col (p.e. coleta_2020, coleta_2019), você pode oprimir duas vezes Tab :keyboard: e o 💻 vai mostrar as palavras com aquele começo.
**Entrada**
```coffeescript=
## Troque de pasta
cd análises/col
```
Oprima [Tab][Tab]
**Saída**
```coffeescript=
coleta_2020    coleta_2019
```
**Entrada**
```coffeescript=
## Troque de pasta
cd análises/coleta_2020
## Confira
pwd
```
**Saída**
```coffeescript=
/data/usuário/coleta_2020
```
### nano (editor de texto)
Agora você vai criar um arquivo 📄 `test.txt` dentro da 📁 `tutorial/`.
**Entrada**
```coffeescript=
## Troque de pasta
cd tutorial/
## Abra o editor de texto nano 
nano test.txt
```
Ai você vai escrever: `Este é um test` [enter] :keyboard: `Este é um test`
![](https://i.imgur.com/vvL7YG7.png)
[Ctrl + o] para gravar. Na linha branca embaixo o editor de texto pergunta se quer manter o nome que você deu no começo `test.txt`. [Enter] para confirmar. [Ctrl + x] para sair.

Agora confira que o arquivo 📄 `test.txt` foi criado com o comando `ls`.
**Entrada**
```coffeescript=
## Confira
ls
```
**Saída**
```coffeescript=
test.txt
```
Se você quiser entrar de novo no arquivo 📄 `test.txt` e modificá-lo deve usar de novo o comando `nano test.txt`.
### mv (move)
O comando `mv` serve para mover arquivos 📄 de uma 📁 a outra 📁. Mas **dependendo dos argumentos** pode também mudar os nomes dos elementos.
Para mover um arquivo de uma 📁 a outra 📁 o comando genérico é: `mv arquivo.txt novapasta/arquivo.txt`. Em nosso exemplo:
**Entrada**
```coffeescript=
## Movimente o arquivo
mv test.txt ../dados/test.txt
## Confira
ls
```
**Saída**
```coffeescript=
 
```
Então, leia o comando assim: mover o arquivo `test.txt` para a 📁 `/data/usuário/dados`. 
Usou `../`, porque você estava dentro da  📁`/data/usuário/tutorial/` e precisava voltar para 📁 `/data/usuário/` (📁 pai da `tutorial/`) para continuar o caminho pra 📁 `dados/`.

Agora use o comando `mv` para trocar o nome do arquivo 📄 `test.txt` por `prova.txt`. Comando genêrico `mv nomedoarquivo.txt novonomedoarquivo.txt`
**Entrada**
```coffeescript=
## Troque de pasta
cd ../dados/
## Confira
ls
```
**Saída**
```coffeescript=
test.txt
```
**Entrada**
```coffeescript=
## Mude o nome do arquivo
mv test.txt prova.txt
## Confira
ls
```
**Saída**
```coffeescript=
prova.txt
```
### cp (copy)
O comando `cp` é similar ao `mv`, mas ele cópia o arquivo 📄 ao invés de mover ele
Agora vai copiar o arquivo `/data/usuário/dados/prova.txt` na pasta `/data/usuário/análises/`. **ATENCÃO:exclamation:! Vai fazer isso desde sua** 📁 **inicial** `/data/usuário/`. Comando genêrico `cp diretorio/nomedoarquivo.txt novodiretorio/nomedoarquivo.txt`
**Entrada**
```coffeescript=
## Onde estou?
pwd
```
**Saída**
```coffeescript=
/data/usuário/dados/
```
Percebeu que tem que voltar uma pasta?? Você pode sozinho... Lembre do comando!
Não esqueça o **tip** 💁🏻‍♀️  de usar [Tab]
**Entrada**
```coffeescript=
## Cópiar o arquivo
cp dados/prova.txt dados/análises/
##Confira
ls dados/
```
**Saída**
```coffeescript=
prova.txt
```
**Entrada**
```coffeescript=
## Listar
ls análises/
```
**Saída**
```coffeescript=
prova.txt
```
Você pode usar o comando `cp` para copiar vários arquivos 📄📄em uma linha de comando só. 
**comando genérico**
```coffeescript=
## Cópiar os arquivos
cp arquivo1.txt arquivo2.txt arquivo3.txt pasta/
```

### rm (remove)
Com o comando `rm` você pode remover arquivos 📄 e/ou 📁. **CUIDADO!!**:exclamation: **PRECAUÇÃO**:exclamation: este comando não tem volta atrás, uma vez você oprima [enter] não tem como recuperar o arquivo 📄 ou 📁, então revise e pense bem antes de rodar este comando. Comando genêrico `rm diretorio/nomedoarquivo.txt`
Você vai deletar o arquivo `prova.txt` da pasta 📁`/data/usuário/dados`. Lembre ou confira sua localização.
**Entrada**
```coffeescript=
## Remover
rm dados/prova.txt
## Confira
ls
```
**Saída**
```coffeescript=

```
Para eliminar uma 📁 você precisa do **flag** 🚩`-r`. Elimine a 📁 `dados/`
```coffeescript=
## Remover a pasta
rm -r dados/
```
 
### Outros comandos
Para os seguintes comandos vamos criar dois novos arquivo de texto 📄📄 chamados `cidademaravilhosa.txt` e `paistropical.txt`, neles vamos copiar as letra de cada música. Clique em 🎵🎶 ["Cidade Maravilhosa"](https://www.letras.mus.br/marchinhas-de-carnaval/497940/)🎵🎶 e em :musical_note:  ["Pais Tropical"](https://www.letras.mus.br/jorge-ben-jor/46647/)🎵🎶 para obter as letras. Crie os arquivos de texto 📄. 
**Entrada**

```coffeescript=
## Trocar de pasta
cd tutorial/
##Abrir o editor de texto nano
nano cidademaravilhosa.txt
```
**Entrada**
```coffeescript=
## Abrir o editor de texto nano
nano paistropical.txt
```
Copia o texto da letra. O comando de teclas :keyboard: [Ctrl + V] não funciona no terminal de Linux. Use [Ctrl + Shift + V].
![](https://i.imgur.com/rQmDWZQ.png)
Grava e fecha o editor de texto. Confere
**Entrada**
```coffeescript=
## Listar
ls
```
**Saída**
```coffeescript=
cidademaravilhosa.txt    paistropical.txt
```
### less
Com este comando você pode imprimir na tela o conteudo de um arquivo 📄 que cabe em uma tela só
**Entrada**
```coffeescript=
less cidademaravilhosa.txt
```
**Saída**
![](https://i.imgur.com/7pVE8Y0.png)
### head
Mostra as primeira 10 linhas do arquivo
**Entrada**
```coffeescript=
head cidademaravilhosa.txt
```
**Saída**
![](https://i.imgur.com/gpT88jR.png)
### tail
Mostra as últimas 10 linhas do arquivo
**Entrada**
```coffeescript=
tail cidademaravilhosa.txt
```
**Saída**
![](https://i.imgur.com/5VmI58h.png)
Se você quiser aumentar o número de linhas que esses dois ultimos comandos mostram você pode adicionar um argumento com o número de linhas que quer imprimir na tela
**Entrada**
```coffeescript=
## Últimas 20 linhas
tail -20 cidademaravilhosa.txt
## Primeiras 20 linhas
head -20 cidademaravilhosa.txt
```

### cat 
Este comando serve para juntar dos 📄 📄 arquivos num só. Muito útil para juntar arquivos 📄 `.fasta` com sequencias. (Tranquilo disso vamos aprender depois 🤓).
**Entrada**
```coffeescript=
## Concatenar
cat cidademaravilhosa.txt paistropical.txt > mpb_brasileiro.txt
## Confira
ls
```
**Saída**
```coffeescript=
cidademaravilhosa.txt    mpb_brasileiro.txt    paistropical.txt
```
Assim, você vai criar um novo arquivo 📄  chamado `mpb_brasileiro.txt` que tem a letra da 🎵🎶"Cidade maravilhosa"🎵🎶 seguido da letra de 🎵🎶"Pais tropical 🎵🎶
### wc (Word count)
Este comando serve para contar as linhas, palavras ou caracteres dos arquivos 📄.
**Entrada**
```coffeescript=
## Contar linhas, palavras e caracteres
wc mpb_brasileiro.txt
```
**Saída**
```coffeescript=
146    472    2863    mpb_brasileiro.txt
```
Então, o arquivo 📄 `mpb_brasileiro.txt` tem 146 linhas, 472 palavras e 2863 caracteres.
### grep
Com o `grep` você pode procurar um padrão dentro de um arquivo 📄. Por exemplo num arquivo 📄 de sequencias `.fasta` cada sequencia começa com o simbolo `>` ou poderia procurar uma sequência de nucleótideos especifica (p.e. atcttgca)
**Comando genêrico**
```coffeescript=
grep '>' arquivo.fasta
```

No nosso arquivo `mpb_brasileiro.txt`
**Entrada**
```coffeescript=
grep -B1 -A1'Cidade' mpb_brasileiro.txt
```
**Saída**
![](https://i.imgur.com/WSMOxu9.png)

Leia o comando assim, procura e imprime uma linha antes e uma linha depois do "query" no arquivo 📄 `mpb_brasileiro.txt`

Com `grep` você também pode contar qualquer "query". Por exemplo o caracter `>`, sempre está iniciando uma sequência em um arquivo 📄 `.fasta`, contando o número de vezes que `>` aparece você poderá souber o número de sequências no ser arquivo 📄.
No nosso exemplo:
```coffeescript=
grep -c "Cidade" mpb_brasileiro.txt
```
**Saída**
```coffeescript=
13
```

### find
Com o comando `find` você pode procurar arquivos : 📄 com uma palavra dada.
**Entrada**
```coffeescript=
## Procurar
find . -name “*.txt”
```
Leia o comando assim: procurar no **diretório atual de trabalho** 📁 qualquer arquivo 📄  que termine com `.txt`. O simbolo `*` significa qualquer caracter. Se você escrever `mpb*`, o 💻 vai entender que você está interesado em qualquer elemento que comece com "mpb".
**Saída**
```coffeescript=
./cidademaravilhosa.txt
./mpb_brasileiro.txt
./paistropical.txt
```
**Entrada**
```coffeescript=
## Trocar de pasta
cd ..
## Onde estou?
pwd
```
**Saída**
```coffeescript=
/data/usuário
```
Você poderia procurar a palavra em qualquer pasta 📁 do pc modificando o comando assim
```coffeescript=
## Procurar
find -name "*.txt"
```
**Saída**
```coffeescript=
./tutorial/cidademaravilhosa.txt
./tutorial/mpb_brasileiro.txt
./tutorial/paistropical.txt
```
### wget
O comando `wget` serve para fazer download the arquivos 📄 na web e armazenar no 📁 **diretório atual de trabalho**
O comando genêrico é:
```coffeescript=
## Descarregar
wget https://enderecoweb.com.br
```
### gzip
Este comando é para compactar e descompactar arquivos 📄.
O comando genêrico é:
```coffeescript=
## Comprimir
gzip filename
```
O arquivo 📄 de saida será `filename.gz`.
Para descompactar o comando genêrico é:
```coffeescript=
## Descomprimir
gzip -d filename.gz
```
## Resumão

| Comando | Ação                                              |
| ------- | ------------------------------------------------- |
| ls      | Listar os elementos de um diretório               |
| mkdir   | criar uma pasta 📁                                   |
| mv      | mover ou renomear elementos                       |
| cp      | copiar arquivos 📄                                    |
| rm      | remover arquivos ou pastas                        |
| cat     | concatenar arquivos                               |
| less    | imprime o conteúdo de um arquivo na tela          |
| head    | Imprime as primeiras 10 linhas de um arquivo 📄     |
| tail    | Imprime as últimas 10 linhas de um arquivo 📄        |
| cd      | Trocar de diretório de atual de trabalho 📁         |
| find    | Procura arquivos  📄                                 |
| grep    | Procura padrões dentro dos arquivos 📄                |
| wc      | conta caracteres, palavras e linhas de um arquivo 📄 |
| kill    | para procesos                                     |

Convido você a testar seu aprendizado com o seguinte [test](https://github.com/GEMM-DRM/Tutoriais-GEMM/blob/master/TEST_UNIX_SHELL.md) 

**FIM** :sparkle: 

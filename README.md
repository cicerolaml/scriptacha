# acha

Script Perl simples que busca recursivamente, em todos os arquivos de texto de uma pasta e de suas subpastas, por uma ou mais palavras (ou trechos de texto) informadas na linha de comando. Imprime o caminho de cada arquivo em que pelo menos uma das palavras foi encontrada.

## Como funciona

1. Percorre recursivamente o diretório atual usando o comando `find`.
2. Para cada arquivo encontrado, verifica se é um arquivo de texto (arquivos binários são ignorados automaticamente).
3. Abre e lê o arquivo linha a linha.
4. Assim que encontra qualquer uma das palavras passadas como argumento em uma linha, imprime o nome do arquivo e passa para o próximo, sem continuar lendo o restante dele.

## Requisitos

- Perl 5 (já vem instalado por padrão na maioria dos sistemas Unix/Linux/macOS)
- Utilitário `find`, disponível em qualquer sistema Unix-like

## Instalação

```bash
git clone <url-do-seu-repositorio>
cd acha
chmod +x acha
```

Opcionalmente, coloque o script em uma pasta do seu `PATH` (por exemplo `~/bin` ou `/usr/local/bin`) para poder chamá-lo de qualquer lugar:

```bash
cp acha ~/bin/
```

## Uso

```bash
./acha palavra1 [palavra2 ...]
```

O script busca a partir do diretório atual (`.`), então rode-o de dentro da pasta que deseja pesquisar.

### Exemplos

Buscar arquivos que contenham "TODO" ou "FIXME":

```bash
./acha TODO FIXME
```

Buscar arquivos que mencionem um nome de função:

```bash
./acha minhaFuncao
```

## Limitações

- A busca é feita por substring simples (não é case-insensitive e não usa expressões regulares).
- Não filtra por extensão de arquivo — analisa todo arquivo identificado como texto pelo Perl (`-T`).
- Arquivos que não podem ser abertos (por permissão, por exemplo) são reportados no `stderr` e ignorados.


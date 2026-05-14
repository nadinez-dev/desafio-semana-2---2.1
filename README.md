# desafio-semana-2---2.1 (questão 1)
<br>

<br>
Questão: Usando as tabelas de origem, projete um star schema com 1 tabela de fatos e
4 tabelas de dimensão.
<br>
O que você precisa definir: <br>
• Qual é o processo de negócio que a tabela de fatos vai representar? <br>
• Qual é o grain — o que cada linha da tabela de fatos representa? <br>
• Quais colunas vão para a tabela de fatos e quais vão para as dimensões? <br>
• Quais atributos de cada dimensão têm valor analítico real? <br>

<br>

## Objetivo

O objetivo deste desafio é projetar um modelo dimensional no formato Star Schema para a plataforma fictícia de streaming de música SoundData.

O modelo foi construído para permitir análises sobre:

Comportamento dos usuários.
Desempenho de artistas.
Popularidade de músicas.
Padrões temporais de consumo.
Distribuição geográfica das reproduções.

## Grain
Cada linha da tabela fato representa uma reprodução individual de uma faixa.

Cada linha da tabela fato_plays representa uma reprodução individual de uma faixa por um usuário em um instante específico.
<br>
Uma linha representa uma reprodução de uma música por um usuário em um instante específico.
<br>
Isso significa que:

Uma execução da música = uma linha.
Não há agregação prévia.
Cada registro corresponde ao menor nível de detalhe disponível.


## Tabela Fato

fato_plays

Armazena os eventos de reprodução.

Coluna	Descrição <br>
sk_play	Chave substituta da fato <br>
sk_usuario	FK para dim_usuario <br>
sk_track	FK para dim_track <br>
sk_artista	FK para dim_artista <br>
sk_data	FK para dim_data <br>
duracao_seg	Quantidade de segundos ouvidos <br>
dispositivo	Tipo de dispositivo utilizado <br>
pais_play	País de origem da reprodução <br>

## Dimensões

### dim_usuario <br>
Representa o ouvinte.
 <br>
Coluna <br>
sk_usuario <br>
usuario_id <br>
plano <br>
faixa_etaria <br>
pais <br>
cidade <br>
dt_inicio <br>
dt_fim <br>
is_current <br>

### dim_track <br>
Representa a música.
 <br>
Coluna <br>
sk_track <br>
track_id <br>
titulo <br>
album <br>
genero <br>
duracao_total_seg <br>
explicit <br>
dt_inicio <br>
dt_fim <br>
is_current <br>

### dim_artista <br>
 Representa o artista.
 <br>
Coluna <br>
sk_artista <br>
artista_id <br>
nome <br>
pais_origem <br>
genero_prim <br>
gravadora <br>
dt_inicio <br>
dt_fim <br>
is_current <br>

### dim_data <br>
Representa a dimensão temporal.
 <br>
Coluna <br>
sk_data <br>
data_completa <br>
ano <br>
trimestre <br>
mes <br>
nome_mes <br>
dia_semana <br>
nome_dia <br>
hora <br>
fim_de_semana  <br>

# TV Make

**Sinalização digital interna: o que cada setor publica, passando nas TVs da empresa.**

Os setores enviam imagens e vídeos. Cada TV mostra a sequência do seu local, com tempo de tela por setor e horários especiais que entram na hora marcada.

> Este repositório é uma vitrine. O sistema roda na rede interna da empresa; o código e os dados são privados.
> As telas abaixo são de um ambiente de demonstração, com conteúdo fictício.

## As telas

<img src="docs/telas/01-o-que-esta-passando.png" alt="O que está passando: TVs ligadas, duração da volta completa, os conteúdos na ordem em que passam e o que ficou fora do ar" width="880">

**O que está passando.** A volta completa de cada local, as TVs ligadas e, quando algo não entra, o motivo.

<table>
<tr>
<td width="50%"><img src="docs/telas/02-meus-conteudos.png" alt="Meus conteúdos: o setor vê o tempo de tela usado e a ordem dos seus conteúdos"><br>
<b>Meus conteúdos</b><br>
Cada setor vê quanto do seu tempo de tela já usou e arrasta para mudar a ordem.</td>
<td width="50%"><img src="docs/telas/06-na-tv.png" alt="A TV exibindo um comunicado em tela cheia"><br>
<b>Na TV</b><br>
O player é uma página web: roda no navegador da TV ou num Fire TV/Android TV.</td>
</tr>
<tr>
<td><img src="docs/telas/04-tvs.png" alt="TVs: lista das TVs cadastradas e formulário para cadastrar uma TV nova pelo código"><br>
<b>TVs</b><br>
A TV mostra um código de 6 letras; o admin cadastra o código, dá um nome e escolhe o local.</td>
<td><img src="docs/telas/03-setores.png" alt="Setores: tempo de tela padrão, cor e regras opcionais de cada setor"><br>
<b>Setores</b><br>
Tempo de tela padrão, cor e regras opcionais: horário, dias e limite de conteúdos ativos.</td>
</tr>
</table>

<img src="docs/telas/05-agenda-da-semana.png" alt="Agenda da semana: quando cada setor e cada horário especial aparecem, dia a dia" width="880">

**Agenda da semana.** Quando cada setor e cada horário especial aparecem nas TVs, dia a dia.

## Como a TV decide o que passa

- **Volta:** os setores na ordem definida pelo admin. Dentro de cada um, só entram as mídias aprovadas, prontas e válidas agora (data, dia da semana e horário), até completar o tempo do setor.
- Setor sem mídia é pulado, e o tempo que sobra encolhe a volta.
- **Programação nova só entra quando o item atual termina:** nenhum vídeo é cortado no meio.
- **Horários especiais** interrompem na hora marcada, passam e a volta retoma de onde parou.
- **Sem rede**, a TV continua com a última programação guardada.

## Papéis

- **Admin:** ordem e tempo dos setores, pessoas e permissões, TVs, horários especiais, agenda e o que só gera aviso ou bloqueia a publicação.
- **Setor:** envia imagens e vídeos e define duração, validade, dias, horários e som; ordena a própria sequência.
- Permissões por pessoa: publica direto, depende de aprovação, aprova, cria horários especiais.

## Por baixo

- Python, FastAPI e SQLAlchemy, com SQLite (pronto para Postgres) e páginas em Jinja2.
- Vídeos convertidos para H.264 1080p e miniaturas geradas com ffmpeg, em segundo plano.
- Player em JavaScript ES5, com duas camadas e transição suave, para funcionar em navegadores de TV antigos.
- Proteções: CSRF por Origin/Referer, limite de tamanho do envio, sessão com expiração e acesso controlado às mídias.

---

Projeto desenvolvido para uso interno corporativo. Publicado como vitrine técnica, sem código de produção e sem dados reais.

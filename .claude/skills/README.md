# Instagram agent — 13 skills

Pack de 13 skills de Claude para operar una cuenta de Instagram. Instaladas
en este repo bajo `.claude/skills/`, así que Claude Code las carga
automáticamente en cualquier sesión abierta sobre `INVENTARIO`.

Origen: https://github.com/Jakeschincariol/instagram-agent-skill
(Jake Schincariol, licencia MIT — ver `LICENSE` en esta carpeta).
Copiadas sin modificar.

## Los 13 comandos

| comando | qué hace |
| --- | --- |
| `/ig-reel` | Una idea → Reel: 3 ganchos sacados de 26 fórmulas, puntuados, guion, texto en pantalla y beat sheet cronometrado. |
| `/ig-viral` | Busca qué está funcionando en tu nicho, lo ordena por múltiplo sobre la mediana de cada cuenta y arma el swipe file. |
| `/ig-caption` | El caption, con linter: muestra los 125 caracteres que el feed enseña antes del "... más". |
| `/ig-carousel` | Carrusel: portada que gana el swipe, copy slide por slide y los archivos 1080x1350. |
| `/ig-story` | La secuencia de historias del día, qué sticker hace cada trabajo y el embudo al DM. |
| `/ig-profile` | Puntúa el perfil sobre 100 con una rúbrica de 12 partes y reescribe lo que pierde puntos. |
| `/ig-plan` | La semana: qué publicar, en qué formato, cuándo y con qué 10 cuentas interactuar. |
| `/ig-human` | El humanizador: quita em dashes, slop y caracteres invisibles, y puntúa con 5 checks. |
| `/ig-comment` | Comentarios en posts de otros. Nueve tipos, elegidos según lo que el post sea. |
| `/ig-reply` | El hilo bajo tus propios posts, ordenado por keyword / lead / sustancia / pregunta / apoyo / ruido. |
| `/ig-dm` | Entrega por keyword, primer mensaje, pitch de colaboración y dos seguimientos. |
| `/ig-repurpose` | Un video, podcast o newsletter → una semana de reels y carruseles. |
| `/ig-audit` | Post-mortem de lo ya publicado, ordenado por múltiplo de outlier y envíos por alcance. |

## Las 6 herramientas Python

Sin dependencias, sin red, nada sube a ningún lado. Verificadas en este repo
con Python 3.13:

```bash
python3 ig-reel/hookscore.py hooks.txt                 # rankea ganchos
python3 ig-reel/beats.py script.txt --target 30        # cronometra el guion
python3 ig-caption/caption.py caption.txt --keywords "term1,term2"
python3 ig-human/humanize.py draft.txt --report        # limpia y muestra cambios
python3 ig-human/detect.py draft.txt                   # puntúa, 5 checks
python3 ig-viral/swipe.py captured.tsv                 # ranking por outlier
```

`ig-viral/swipe.py` importa `hookscore` desde `../ig-reel`, así que las
carpetas tienen que quedar hermanas. No muevas una sola.

## Paso pendiente: voice.md

Todas las skills leen `~/.claude/instagram/voice.md`. La plantilla vacía está
versionada en este repo en `.claude/instagram/voice.md`. Llenala (10 minutos,
o pasale a Claude tres de tus propios reels y pedile "escribí mi voice.md con
esto") y copiala al home:

```bash
mkdir -p ~/.claude/instagram && cp .claude/instagram/voice.md ~/.claude/instagram/voice.md
```

En sesiones de Claude Code en la nube el contenedor arranca limpio, así que ese
`cp` hay que repetirlo por sesión (o mantener la versión llena en el repo, que
es lo que esta carpeta permite).

## Lo que no hacen

Ninguna publica en Instagram. Redactan y te dejan un bloque listo para copiar;
publicás vos. Automatizar publicaciones, comentarios o DMs por navegador o
herramientas de terceros viola los Términos de Instagram y bloquea cuentas.
`/ig-viral` lee, no scrapea. Los 5 checks de `/ig-human` son heurísticas
locales, no APIs de detección.

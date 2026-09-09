# JUPAC PICTURES — como mexer, subir e gravar na tag

## O que veio na pasta

```
index.html      ← o site principal (HTML + CSS + JS num arquivo só)
terco.html      ← página separada, só com o guia do terço
fotos/          ← as 9 imagens já cortadas e comprimidas
LEIA-ME.md      ← este arquivo
```

**Importante:** ao subir o site (Vercel, GitHub Pages etc.), suba os dois arquivos `.html` juntos com a pasta `fotos/` — o botão "Abrir o guia do terço" do site principal depende do `terco.html` estar do lado dele.

Site inteiro com fotos: **~560 KB**. Abre em menos de 1 segundo no 4G.
Para testar agora: dê dois cliques no `index.html`.

---

## 1. Como editar

Abra o `index.html` no Bloco de Notas (ou VS Code) e procure por:

```
⭐ EDITE AQUI ⭐
```

Está lá em cima. Tudo do site sai desse bloco — **você nunca precisa mexer em mais nada.**

**Regra única:** troque só o que está entre `"aspas"`. Não apague vírgulas, chaves `{ }` nem colchetes `[ ]`.

### Trocar a foto de alguém

1. Corte a foto em **4:5 vertical** (ex.: 800 × 1000 px)
2. Comprima em **squoosh.app** até ficar abaixo de 150 KB
3. Salve na pasta `fotos/` com nome sem acento nem espaço — ex.: `celine.jpg`
4. Se manteve o mesmo nome do arquivo, pronto. Se mudou, ajuste a linha `foto:` da pessoa.

### Trocar uma citação

```js
frase:"Minha vocação é o amor.",  autor:"Santa Teresinha do Menino Jesus",
```

### Trocar a função

`funcao:"Ator"` · `"Atriz"` · `"Coordenação"`
Quem tem `coord:true` na linha ganha a etiqueta em vermelho. Se mudar de coordenador para ator, apague o `coord:true,`.

### Trocar os horários (agenda da semana)

No `index.html`, bloco `AGENDA`:

```js
const AGENDA = [
  { emoji:"🙏", evento:"Terço",        quando:"Sexta-feira, à noite" },
  { emoji:"🤝", evento:"Pós-encontro", quando:"Sexta-feira, às 17h" },
  { emoji:"🎬", evento:"Encontro",     quando:"Sábado, às 17h" }
];
```

Essa lista aparece na faixa logo abaixo do topo e de novo no rodapé — muda em um lugar só. Pode adicionar ou remover linhas se a agenda mudar.

### Trocar as orações de quem tá começando

Bloco `ORACOES_INICIANTES`, no `index.html`. Cada uma tem `titulo` e `texto` — copie um bloco inteiro (de `{` até `},`) pra adicionar uma oração nova.

### Editar o passo a passo do terço

Isso agora fica em **`terco.html`** (página separada, pro site principal não ficar comprido). Abra esse arquivo e procure `⭐ EDITE AQUI ⭐` lá dentro.

Bloco `TERCO_PASSOS` — cada linha é um passo, na ordem em que aparece na tela. Bloco `MISTERIOS` — quem tem `destaque:true` ganha a borda dourada (hoje é sexta → Dolorosos). Bloco `TERCO_QUANDO` — o texto do horário do terço em grupo. Se o dia do terço mudar, ajuste os três: `TERCO_QUANDO` aqui, o `destaque:true` de `MISTERIOS` aqui, e a linha do "Terço" em `AGENDA` no `index.html`.

### Trocar as equipes (do encontro e de fora)

Dois blocos no `index.html`: `EQUIPES` (as que atuam no dia do encontro — Ordem, Luz, Capela, Secretaria, Música, Recepção, Cozinha, Coordenação) e `EQUIPES_FORA` (as que atuam durante a semana — Social, Liturgia, Mídia). Cada uma tem `nome`, `dep` (a linha pequena embaixo do nome) e `txt`. Ícone é o campo `icone` — os disponíveis estão listados em `ICONES_EQ` no JS, mais abaixo no arquivo.

### Ligar a galeria de fotos

Ela está **desligada** e some sozinha do site. Para ligar, ponha as fotos em `fotos/` e liste:

```js
const GALERIA = ["fotos/ensaio1.jpg","fotos/ensaio2.jpg","fotos/ensaio3.jpg"];
```

### Trocar a oração

Linha `const ORACAO = "..."` — a que está lá é rascunho meu. Troque pela de vocês.

---

## 2. A cor que aparece conforme você rola

No celular não existe "passar o mouse", então quem acende as fotos é a **rolagem**: quanto mais perto do meio da tela o card está, mais colorido ele fica. Parece um holofote descendo pela lista. No computador, passar o mouse continua funcionando também.

Se quiser ajustar a intensidade, procure no JS por `const plato`:

```js
const plato = alt * 0.18;   // zona central: cor cheia
const fim   = alt * 0.48;   // além disso: preto e branco
```

- Efeito **mais forte** (fica cinza por mais tempo): diminua o `plato` para `0.12`
- Efeito **mais suave** (quase sempre colorido): aumente para `0.28`

Quem tiver "reduzir movimento" ligado no celular vê todas as fotos coloridas direto, sem efeito nenhum.

---

## 3. Subir na internet

### Vercel (mais rápido)

1. Entre em **vercel.com** e faça login com Google
2. Na tela inicial, **arraste a pasta inteira** (com `index.html` e `fotos/` dentro)
3. Sai uma URL tipo `jupac.vercel.app`
4. Em *Settings → Domains* dá pra encurtar o nome

### GitHub Pages

1. Crie um repositório **público** chamado `jupac`
2. *Add file → Upload files* → arraste tudo
3. *Settings → Pages → Source: main / root*
4. Sai `seuusuario.github.io/jupac`

> **URL curta importa.** Quanto menor, melhor pra NFC e pra QR code.

---

## 4. Gravar a tag NFC

**Comprar:** adesivo **NTAG215**. Compre um pacote de 10 — você vai querer colar em vários lugares.

**Gravar:**

1. Baixe o app **NFC Tools** (Android ou iPhone, gratuito)
2. Aba **Gravar** → *Adicionar um registro* → **URL/URI**
3. Cole a URL do site
4. *Gravar* → encoste a tag atrás do celular
5. Depois de testar, **bloqueie a tag** no próprio app — senão qualquer um regrava

**Teste em um iPhone e num Android antes do encontro.** iPhone do XS pra cima lê sozinho com a tela ligada; os mais antigos precisam do atalho de NFC na Central de Controle.

**Onde colar:** atrás do crachá de cada integrante · no cartaz da entrada · na mesa da Secretaria.

**Gere também um QR code** da mesma URL e ponha no cartaz. NFC é o charme, QR é o que garante que todo mundo consegue.

---

## 5. O que ainda dá pra melhorar

**Foto da Celine** — a que você mandou é de casal, e o corte precisou fechar bastante nela. Ficou levemente borrada (o preto e branco disfarça, mas dá pra notar). Uma foto sozinha dela resolve na hora: é só substituir `fotos/celine.jpg`.

**Imagem de prévia do WhatsApp** — hoje ela usa a foto do elenco. Quando quiser algo sob medida, gere uma imagem 1200 × 630 px e troque a linha `og:image`.

**Contador regressivo** — se marcarem data de apresentação, é rápido de acrescentar.

---

## 6. Detalhes técnicos (caso alguém pergunte)

- Zero dependências, zero build. É HTML puro.
- Fontes vêm do Google Fonts; se a internet falhar, o site usa as fontes do celular e continua legível.
- Respeita "reduzir movimento" do sistema.
- Todos os botões têm no mínimo 44 × 44 px (padrão de toque).
- Se uma foto não carregar, o card mostra as iniciais em dourado no lugar — nunca fica um buraco.
- Se o JavaScript falhar, o conteúdo continua legível; só perde os efeitos.
- O efeito de cor só recalcula os cards que estão na tela, em `requestAnimationFrame` — não trava celular fraco.
- Não usa nenhum armazenamento do navegador nem cookie. Nada de banner de consentimento.

**Atenção:** o site é público. Se tiver menor de idade em alguma foto, vale ter o ok dos responsáveis antes de publicar.

# Amplia

Upscaling de imagens com IA, **inteiramente no navegador** — sem enviar nada
para um servidor, sem cadastro e sem custo.

🔗 **App:** https://wallasace.github.io/amplia

## Como funciona

`index.html` é uma página única, sem build, que roda o modelo de
super-resolução [ESRGAN](https://github.com/xinntao/ESRGAN) direto no seu
navegador usando [TensorFlow.js](https://www.tensorflow.org/js) através da
biblioteca [UpscalerJS](https://github.com/thekevinscott/UpscalerJS).

- **A imagem nunca sai do seu computador.** Todo o processamento (inferência
  do modelo) acontece localmente, via WebGL/CPU do seu navegador.
- **Os modelos de IA** (arquivos `.json`/`.bin`, de ~1 MB a ~28 MB conforme a
  qualidade escolhida) são baixados de uma CDN pública (jsDelivr) na primeira
  vez que são usados e ficam em cache do navegador depois disso.
- Três níveis de qualidade (modelos ESRGAN "slim", "medium" e "thick") e
  escala de 2× ou 4×. "Máxima qualidade" é o melhor resultado que dá pra obter
  rodando dentro de uma aba de navegador.
- Imagens grandes são processadas em blocos (patches) automaticamente, então
  não trava a aba nem estoura a memória.

## Rodando localmente

Não precisa de build nem de instalar nada — é HTML puro:

```bash
python3 -m http.server 8080
# depois abra http://localhost:8080
```

Ou simplesmente abra o `index.html` direto no navegador.

## Limites e alternativas

Este app roda inteiramente na CPU/GPU do navegador, então há um teto de
qualidade/velocidade que um modelo web consegue entregar. Se você precisa do
teto mais alto possível de qualidade (e tem uma GPU dedicada), ferramentas
nativas como o [Upscayl](https://github.com/upscayl/upscayl) (gratuito, open
source, usa Real-ESRGAN via Vulkan) tendem a superar qualquer coisa que rode
dentro de uma aba — mas exigem instalação.

## Stack

- HTML/CSS/JS puro (sem framework, sem bundler)
- [TensorFlow.js](https://www.tensorflow.org/js)
- [UpscalerJS](https://github.com/thekevinscott/UpscalerJS) + modelos ESRGAN
  ([`@upscalerjs/esrgan-slim`](https://www.npmjs.com/package/@upscalerjs/esrgan-slim),
  [`esrgan-medium`](https://www.npmjs.com/package/@upscalerjs/esrgan-medium),
  [`esrgan-thick`](https://www.npmjs.com/package/@upscalerjs/esrgan-thick))
- Publicado com GitHub Pages

## Licença

Código deste repositório sob [MIT](LICENSE). As bibliotecas e modelos usados
(TensorFlow.js, UpscalerJS, modelos ESRGAN) mantêm suas próprias licenças
open source.

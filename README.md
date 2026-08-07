# Repete — Loop Trainer

App de treino de listening: toca áudio/vídeo em blocos fixos, repete em loop até você mandar avançar, guarda suas anotações, compara com a transcrição real e tem um modo de leitura bilíngue (inglês/português).

## Arquivos

```
repete-app/
├── index.html       ← o app inteiro (não precisa de servidor backend)
├── manifest.json     ← permite "instalar" como app no celular
├── sw.js              ← service worker (funciona offline depois de aberto uma vez)
└── icons/
    ├── icon-16.png
    ├── icon-32.png
    ├── icon-180.png   ← usado pelo iPhone
    ├── icon-192.png
    └── icon-512.png
```

## Deploy no Vercel

1. Crie uma conta em vercel.com (pode entrar com GitHub).
2. Se ainda não tiver, suba esta pasta para um repositório no GitHub (ou use `vercel deploy` direto pela CLI, sem precisar do GitHub).
3. No painel do Vercel, clique em **Add New → Project**, selecione o repositório (ou arraste a pasta se estiver usando o deploy manual por drag-and-drop).
4. Não precisa configurar build command nem output directory — é um site estático puro. Deixe em branco ou marque "Other".
5. Clique em **Deploy**. Em ~30 segundos você tem uma URL tipo `repete-app.vercel.app`.

## Deploy no Netlify

1. Crie uma conta em netlify.com.
2. Na tela inicial, arraste a pasta `repete-app` inteira (com index.html, manifest.json, sw.js e icons/) direto para a área de "Deploy manually".
3. Pronto — o Netlify te dá uma URL tipo `repete-app.netlify.app` na hora.

Qualquer um dos dois funciona igual, já que é só HTML/CSS/JS estático — sem backend.

## Instalar no celular

### Android (Chrome)
1. Abra a URL do site publicado.
2. Toque no menu (⋮) no canto superior direito.
3. Toque em **"Instalar app"** ou **"Adicionar à tela inicial"**.
4. O ícone aparece na tela inicial e abre em tela cheia, sem barra de navegador.

### iPhone (Safari)
1. Abra a URL do site publicado **no Safari** (o "Adicionar à Tela de Início" só funciona pelo Safari, não pelo Chrome no iPhone).
2. Toque no ícone de compartilhar (o quadrado com a seta pra cima).
3. Role para baixo e toque em **"Adicionar à Tela de Início"**.
4. O app aparece com o ícone REPETE e abre em tela cheia, como um app nativo.

## Sobre o link do YouTube

O modo YouTube depende do player embutido do Google. Ele deve funcionar normalmente quando você acessa pelo Safari/Chrome de verdade ou pelo app já instalado — os problemas de carregamento que você teve antes eram específicos do navegador embutido dentro do app do Claude, não do código em si. De qualquer forma, os modos de upload de áudio e vídeo local não dependem disso e funcionam sempre.

## Sobre os dados salvos (anotações, progresso, tempo estudado)

O app usa `localStorage`/armazenamento do navegador — os dados ficam salvos **naquele navegador/aparelho específico**, atrelados ao arquivo (nome + tamanho) ou ao ID do vídeo do YouTube. Isso significa:
- Se você reabrir o mesmo vídeo do YouTube ou o mesmo arquivo de áudio/vídeo, seu progresso volta.
- Os dados não sincronizam entre celular e computador automaticamente — cada instalação guarda os seus próprios dados.
- Limpar os dados do navegador/app apaga o progresso salvo.

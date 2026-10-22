# Como colocar o site da Descarpro no GitHub e no Netlify

## 1. Baixar e extrair os arquivos

Baixe o arquivo `descarpro-site.zip` que acompanha estas instruções e extraia-o no computador. Depois de extrair, confirme que a pasta `descarpro` contém `package.json`, `pnpm-lock.yaml`, `netlify.toml`, `client/` e as imagens dentro de `client/public/images/`.

O ZIP contém o código-fonte e as imagens do site; não inclui `node_modules`, arquivos `.env` nem o histórico interno do projeto. O arquivo `.env` não deve ser enviado ao GitHub.

## 2. Criar um repositório privado no GitHub

1. Acesse [github.com/new](https://github.com/new) e entre na conta pessoal desejada. Confira o avatar no canto superior direito para ter certeza de que está usando essa conta.
2. Dê um nome ao repositório, por exemplo `descarpro-site`, e selecione **Private**.
3. Não marque as opções para criar README, `.gitignore` ou licença: os arquivos do site já estão na pasta local.
4. Clique em **Create repository** e copie a URL HTTPS apresentada, no formato `https://github.com/SEU_USUARIO/descarpro-site.git`.

Se o computador ainda não tiver Git, instale Git for Windows em [git-scm.com/download/win](https://git-scm.com/download/win).

## 3. Enviar os arquivos pelo PowerShell

Abra o PowerShell. Se extraiu o ZIP dentro da pasta Downloads, execute:

```powershell
cd "$HOME\Downloads\descarpro"
git init -b main
git add .
git commit -m "Primeira versão da landing page Descarpro"
git remote add origin https://github.com/SEU_USUARIO/descarpro-site.git
git push -u origin main
```

Na linha `git remote add`, substitua `SEU_USUARIO` pelo usuário da sua conta e ajuste `descarpro-site` caso tenha escolhido outro nome. Se o Git pedir nome e e-mail para o commit, configure-os somente nesta pasta:

```powershell
git config user.name "Seu nome"
git config user.email "seu-email-do-GitHub"
```

Depois repita os comandos `git commit` e `git push`. Ao autenticar no GitHub, use a janela de autenticação oficial que aparecer; não compartilhe senha ou token em conversa.

## 4. Publicar no Netlify

1. Entre em [app.netlify.com](https://app.netlify.com/) e escolha **Add new site** / **Import an existing project**.
2. Conecte o GitHub, autorize o Netlify para acessar o repositório privado e selecione `descarpro-site`.
3. A configuração `netlify.toml` já define o build e a pasta publicada. Se o painel pedir esses valores, use:
   - Build command: `npx --yes pnpm@10.18.0 install --frozen-lockfile && npx --yes pnpm@10.18.0 build:static`
   - Publish directory: `dist/public`
   - Node.js: `20`
4. Publique primeiro no endereço temporário do Netlify e confira o site, os links e as imagens.
5. No painel do site, adicione `www.descarpro.com.br` em **Domain management**. Siga os registros DNS que o Netlify mostrar e configure-os no serviço onde o domínio está registrado. Os valores de DNS dependem da configuração que o Netlify apresentar; não copie registros genéricos.
6. Aguarde a validação do DNS e a emissão do HTTPS pelo Netlify. Só então compartilhe o domínio.

## 5. Atualizar o site depois

Edite os arquivos, salve as alterações e, no PowerShell dentro da pasta do site, execute:

```powershell
git add .
git commit -m "Descrever a alteração"
git push
```

O Netlify detectará o novo envio e fará outro build. Antes da publicação, confira informações de contato e confirme o horário de atendimento que ficou fora da primeira versão.
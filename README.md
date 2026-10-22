# Descarpro — descartáveis e higiene

Landing page estática em português brasileiro para a Descarpro. O conteúdo principal está no HTML inicial e é servido sem depender de JavaScript, o que mantém os textos úteis para compartilhamento e indexação. A identidade usa azul-marinho, verde e fundo claro inspirados na logo fornecida pelo cliente.

## Desenvolvimento local

Requer Node.js 20 e pnpm 10.18.0.

```bash
pnpm install --frozen-lockfile
pnpm dev:static
```

Para gerar os arquivos estáticos:

```bash
pnpm build:static
```

O site compilado fica em `dist/public/`. O comando `pnpm dev` é o servidor do starter com backend; para esta página sem banco ou servidor, use `pnpm dev:static`.

## Publicação no Netlify

A configuração já está definida em `netlify.toml`:

- Comando de build: `npx --yes pnpm@10.18.0 install --frozen-lockfile && npx --yes pnpm@10.18.0 build:static`
- Diretório publicado: `dist/public`
- Node.js: 20

Conecte o repositório GitHub ao Netlify e confirme esses valores nas configurações de build. Depois, adicione `www.descarpro.com.br` como domínio personalizado no painel do Netlify e conclua a validação DNS no registrador onde o domínio está gerenciado. Os passos e registros DNS exatos dependem do painel de domínio. Antes de publicar, confira os contatos e a versão final do conteúdo.

## Informações que ficaram de fora

O horário anotado no questionário como 7h às 17h não foi publicado porque ainda precisa ser confirmado como horário de atendimento de segunda a sexta. A lista de produtos apresentada é inicial e contém somente os itens informados pelo cliente. O prazo de entrega está indicado como sob consulta. O site não anuncia preço de fábrica nem fabricação própria.

Os dados de contato apresentados são os informados/aprovados pelo cliente: WhatsApp (16) 99757-6820, Instagram @descarpro e e-mail descarprocomercial@hotmail.com. O nome empresarial aparece no rodapé.

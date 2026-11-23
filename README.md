# Organiza

App pessoal de organização: agenda, metas de dinheiro, peso e dieta, trabalhos (empresa e doceria) e lista de compras.
Os dados ficam salvos no Supabase e sincronizam em tempo real entre o computador e o celular.

## 1. Criar o banco no Supabase

1. Crie uma conta grátis em https://supabase.com e clique em **New project**. Escolha um nome, uma senha para o banco e a região **South America (São Paulo)**.
2. Quando o projeto terminar de criar, abra **SQL Editor > New query**, cole todo o conteúdo do arquivo `supabase.sql` e clique em **Run**.
3. Abra **Project Settings > Data API** (ou **API**) e copie a **Project URL**.
4. Abra **Project Settings > API Keys** e copie a chave **publishable** (ou a **anon public**, na aba de chaves legadas).
   Nunca use a chave **secret** / **service_role** no app.

## 2. Colocar as chaves no app

No `index.html`, perto do começo, troque:

```js
const SUPABASE_URL='COLE_AQUI_A_PROJECT_URL';
const SUPABASE_ANON_KEY='COLE_AQUI_A_CHAVE_ANON_OU_PUBLISHABLE';
```

pelos valores copiados. Essas duas informações podem ficar públicas no GitHub: quem protege os dados são as regras do `supabase.sql`, que deixam cada pessoa ver apenas os próprios registros.

## 3. Publicar no GitHub Pages

1. Crie um repositório no GitHub (por exemplo `organiza`) e envie os arquivos `index.html`, `supabase.sql` e `README.md`.
2. No repositório, vá em **Settings > Pages**, em **Source** escolha **Deploy from a branch**, branch **main**, pasta **/ (root)**, e salve.
3. Em um ou dois minutos o app fica disponível em `https://SEU-USUARIO.github.io/organiza/`.

## 4. Ajustar o login no Supabase

1. Em **Authentication > URL Configuration**, coloque em **Site URL** o endereço do GitHub Pages, por exemplo `https://SEU-USUARIO.github.io/organiza/`.
   Coloque o mesmo endereço em **Redirect URLs**. Sem isso, os links de confirmação e de acesso por e-mail não voltam para o app.
2. Opcional: para não precisar confirmar o e-mail ao criar a conta, desative **Authentication > Sign In / Providers > Email > Confirm email**.

## 5. Usar

Abra o link no computador e no celular e entre com o mesmo e-mail e senha.
O que você adicionar em um aparelho aparece no outro em poucos segundos.

Dica para o celular: abra o link e use **Adicionar à tela de início** para ter um ícone como se fosse um aplicativo.

## Observações

- Se você esquecer a senha, use **Esqueci a senha / entrar com link por e-mail** na tela de login.
- O plano grátis do Supabase pausa projetos que ficam uma semana sem uso. Se isso acontecer, entre no painel do Supabase e clique em **Restore**; os dados continuam lá.
- O recurso "Criar com IA" da versão do claude.ai não está nesta versão, porque exigiria uma chave de API guardada num servidor. A barra de busca (Ctrl+K) e todo o resto funcionam normalmente.

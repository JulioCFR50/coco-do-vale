# 🥥 Coco do Vale — Guia de Deploy

## Contas de demonstração (já cadastradas)

| Perfil | E-mail | Senha |
|---|---|---|
| Desenvolvedor | dev@cocodovale.com.br | Dev@2025 |
| Superintendente | sup@cocodovale.com.br | Sup@2025 |

---

## Opção 1 — Publicar na Vercel (Recomendado, gratuito)

### Passo a passo

1. Acesse https://vercel.com e crie uma conta gratuita com seu e-mail.
2. No painel da Vercel, clique em **"Add New → Project"**.
3. Escolha **"Deploy without Git"** (ou suba para GitHub antes, opção abaixo).
4. Arraste a pasta `coco-do-vale/` para a área de upload.
5. Clique em **Deploy**.
6. Em ~30 segundos o site estará no ar com um link público tipo:
   `https://coco-do-vale.vercel.app`

### Com domínio próprio (ex: portal.cocodovale.com.br)
- No painel da Vercel → **Settings → Domains**
- Adicione seu domínio e aponte o DNS conforme instruído.

---

## Opção 2 — GitHub Pages (gratuito)

1. Crie um repositório no GitHub chamado `coco-do-vale`.
2. Faça upload do arquivo `index.html` na raiz do repositório.
3. Vá em **Settings → Pages → Source: main / root**.
4. Aguarde ~1 minuto. O site ficará em:
   `https://SEU-USUARIO.github.io/coco-do-vale`

---

## Opção 3 — Servidor próprio (Apache/Nginx)

### Apache (Linux — Ubuntu/Debian)
```bash
# 1. Instalar o Apache
sudo apt update && sudo apt install apache2 -y

# 2. Copiar o arquivo para o servidor
sudo cp index.html /var/www/html/index.html

# 3. Reiniciar o Apache
sudo systemctl restart apache2

# 4. Acessar pelo IP do servidor
http://SEU-IP/
```

### Nginx
```bash
# 1. Instalar o Nginx
sudo apt update && sudo apt install nginx -y

# 2. Copiar o arquivo
sudo cp index.html /var/www/html/index.html

# 3. Reiniciar
sudo systemctl restart nginx
```

---

## Opção 4 — Netlify (arrastar e soltar, gratuito)

1. Acesse https://netlify.com e crie uma conta.
2. Na página inicial, arraste a **pasta `coco-do-vale/`** para a área indicada.
3. O site fica no ar em segundos com link público.
4. Domínio customizado disponível nas configurações.

---

## ⚠️ Importante: banco de dados real

O site atual usa **localStorage do navegador** para salvar usuários e projetos. Isso significa:
- Os dados ficam salvos apenas no computador do usuário.
- Para um ambiente corporativo com múltiplos usuários, será necessário adicionar um backend.

### Próximos passos recomendados para produção

| O que precisa | Solução sugerida |
|---|---|
| Usuários e senhas persistentes | Supabase (gratuito) ou Firebase Auth |
| Projetos salvos em servidor | Supabase Database ou MongoDB Atlas |
| E-mail corporativo obrigatório | Regra no backend validando o domínio |
| Upload de thumbnails | Supabase Storage ou Cloudinary |
| Incorporar Power BI real | Power BI Embedded API (requer licença Pro) |

Se quiser o próximo passo (backend real), peça ao Claude para adicionar integração com Supabase.

---

## Estrutura de arquivos

```
coco-do-vale/
└── index.html   ← arquivo único, tudo incluso
```

O site inteiro está em um único arquivo HTML — sem dependências, sem build, sem npm.
Basta hospedar o `index.html`.

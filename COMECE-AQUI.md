# Comece aqui

Esta pasta já é o repositório https://github.com/israpatricio/site-trafega, com tudo pronto para enviar.

## 1. Abrir no Claude Code

No Terminal:

```
cd ~/Claude/site-trafega
claude
```

O Claude Code lê o `CLAUDE.md` sozinho e já sabe o que é o site e quais são as regras.

## 2. Enviar para o GitHub

Peça para o Claude Code: "dá push na main".

Ou faça você mesmo no Terminal:

```
cd ~/Claude/site-trafega
git push origin main
```

Se o Terminal pedir login do GitHub, use `gh auth login` (GitHub CLI) e tente de novo.

## 3. Ligar o site ao repositório (uma vez só)

Peça para o Claude Code: "segue o PUBLICAR-NO-SERVIDOR.md". Ele precisa da extensão Claude in Chrome para mexer no Portainer.

Até esse passo ser feito, o site no ar continua sendo a versão publicada em 13/11 às 19h51. Ela é igual a esta, então ninguém vê diferença.

## 4. Depois disso

Para trocar texto: edite o `index.html` pelo GitHub (veja o README) ou peça ao Claude Code. Cada push entra no site em cerca de 1 minuto.

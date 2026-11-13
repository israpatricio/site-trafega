# Ligar este repositório ao site (fazer uma vez só)

Objetivo: o servidor puxa este repositório a cada minuto e o nginx serve a página e as imagens direto dele. Depois disso, publicar é só dar push na `main`.

Antes de começar, o repositório precisa ter `index.html`, `img/` e `fontes/` na `main` (confira em https://github.com/israpatricio/site-trafega).

## 1. Esconder a pasta .git do público

O repositório é clonado dentro da pasta que o nginx serve. A pasta `.git` não tem nada secreto (o repositório é público), mas não precisa ficar acessível pelo site.

- No Portainer, abra Configs, copie o conteúdo de `site_nginx_v1` e crie `site_nginx_v2` igual, com esta linha a mais dentro do bloco `server` do domínio principal:
  `location ~ /\.git { deny all; return 404; }`

## 2. Editar a stack "site"

Em Stacks › site › Editor:

1. Troque `source: site_nginx_v1` por `source: site_nginx_v2` e declare `site_nginx_v2` como `external: true` no fim.
2. No serviço `web`, apague as linhas de `site_landing_v3` (index.html) e de todas as `site_img_*_v1` (imagens). Mantenha quiz, privacidade e os PDFs de materiais.
3. Ainda no serviço `web`, acrescente:

```yaml
    volumes:
      - site_repo:/usr/share/nginx/landing
```

4. Acrescente um serviço novo, no mesmo nível de `web`:

```yaml
  sync:
    image: alpine/git:latest
    entrypoint: ["/bin/sh", "-c"]
    command:
      - |
        cd /site
        while true; do
          if [ -d .git ]; then
            git fetch -q --depth 1 origin main && git reset -q --hard origin/main
          else
            git clone -q --depth 1 https://github.com/israpatricio/site-trafega . || true
          fi
          sleep 60
        done
    volumes:
      - site_repo:/site
    deploy:
      replicas: 1
```

5. No fim do arquivo, declare o volume:

```yaml
volumes:
  site_repo:
```

6. Clique em "Update the stack".

## 3. Conferir

- Espere 1 a 2 minutos e abra https://agenciatrafega.com.br com a página recarregada sem cache.
- Confira: textos, as 14 imagens, as fontes (títulos em Archivo Black), o mar animado no topo, o clique do WhatsApp e /privacidade.html.
- Abra https://agenciatrafega.com.br/.git/config: tem que dar 404.
- Teste uma edição pequena no GitHub e veja se aparece no site em até 1 minuto.

## Se der errado

Volte a stack para o arquivo anterior: `site_nginx_v1`, as linhas de `site_landing_v3` e `site_img_*_v1` de volta, sem `volumes` e sem o serviço `sync`. Todas as configs antigas continuam guardadas no Swarm.

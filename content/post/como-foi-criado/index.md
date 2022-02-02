+++
author = "Hugo Authors"
title = "Como esse site foi feito?"
date = "2021-09-11"
description = "Git Ops usando cloud build, Hugo e Firebase"
categories = [
    "Cloud Build"
]
tags = [
    "Cloud Build",
    "WebDev"
]
image = "astro_cloud.png"
+++

Como escolhemos o framework do site? <!--more-->Para facilitar a tarefa, utilizamos um framework chamado Hugo. Escrito em Go, Hugo é um gerador de sites estáticos de código aberto disponível sob a licença Apache 2.0. Hugo oferece suporte aos tipos de arquivo de dados TOML, YAML e JSON, arquivos de conteúdo Markdown e HTML e usa códigos de acesso para gerar conteúdo estático, html, css e javascript.

Alguns requisitos que queríamos:

1. Não precisar utilizar código nas postagens
2. Utilizar um conteúdo estático que possa ser hospedado sem servidor
3. Um pipeline GitOps que possa compilar scripts e lidar com autenticação

Dessa maneira chegamos na seguinte solução

1. A base e layout são feitos com hugo
2. O commit no Cloud Source Repositories dispara um evento do Cloud Build
3. O pipeline instala as dependências do hugo e do firebase
4. O pipeline compila o site e hospeda no Firebase
5. O site é disponibilizado sem que ninguém precise mexer em código ou instalar absolutamente nada localmente

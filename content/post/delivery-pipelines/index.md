+++
author = "Hugo Authors"
title = "Delivery Pipelines"
date = "2022-02-02"
description = "GitOps com ferramentas Google Cloud"
categories = [
    "Google Cloud"
]
tags = [
    "Kubernetes", "GitOps"
]
image = "astro_cowboy.png"
+++
# GitOps

Na última edição da Kubecon, um dos temas mais abordados foi a adoção do GitOps como um paradigma mais contemporâneo e homogênio do que abordagens DevOps tradicionais. A prática também é apontada pela [thenewstack.io](https://thenewstack.io/5-cloud-native-trends-to-watch-out-for-in-2022/) como uma das tendências de desenvolvimento nativas de nuvem para 2022.

Primeiro vamos definir o que é GitOps:

GitOps é um um modelo operacional para Kubernetes e outras tecnologias nativas da nuvem que fornece um conjunto de práticas recomendadas que unificam a implantação, o gerenciamento e o monitoramento de clusters e aplicativos em contêineres.

A prática também trata de garantir que o Git seja sua fonte de verdade, pelo menos para o estado desejado para nossas intenções, não necessariamente para o que algo é, mas para o que queremos que algo seja, como o estado das aplicações ou comportamento de um cluster.


Enquanto o GitOps se parece muito com Infraestrutura como Código, o GitOps pode ser considerado uma extensão do IaC. É um estilo declarativo de IaC para a era nativa da nuvem, combinando orquestração, observabilidade, infraestrutura declarativa como código, contêineres, infraestrutura imutável e melhores práticas de DevOps.

Os três componentes principais da prática:
* GitOps
  * Infraestrutura como código: O IaC descreve como a configuração da infraestrutura é mantida como código. Como o GitOps utiliza um repositório Git como a "fonte única da verdade", você pode usar o Git para rastrear alterações de gerenciamento de código, bem como um repositório Git (que é uma pasta .git), que acompanha todas as alterações feitas em um projeto.

  * Merge Requests: permitem que as equipes trabalhem juntas por meio de revisões e comentários. Também é aqui que as aprovações podem ocorrer. O GitOps aproveita os Merge Requests para revisões de código, além de funcionar como um log de auditoria onde todos os responsáveis ​​e revisores são indicados.

  * CI/CD: Para automatizar as atualizações na infraestrutura, o GitOps utiliza um fluxo de trabalho Git com um pipeline de CI/CD que realiza a alteração quando um novo código é mesclado. A automação do GitOps também substitui qualquer desvio de configuração, alterações manuais e/ou erros, garantindo que o ambiente convirja no estado conforme definido no Git.

  # Como isso se reflete na prática utilizando o Google Cloud?

  Triggers do Cloud Build são acionados quando existe um merge em determinada ramificação do repositório. O serviço gerenciado builda o container, analisa vulnerabilidades e faz o registro do mesmo.

  Existe também, a possibilidade de parametrizar testes executados durante o build, automatizar tags e também utilizar diferentes "builders". Além do Docker podemos optar pelo gradle, maven, bazel, kaniko etc.

  A ferramenta [Cloud Deploy](https://cloud.google.com/deploy#all-features) permite a criação de "delivery pipelines". Um arquivo declara os clusteres alvo (de staging para prod, por exemplo), um ou mais arquivos detalham a implementação do serviço nos clusteres e o que mais me deixou satisfeito foi a incorporação do skaffold que mantem o pipeline imutável ou isolando as alterações inerentes ao pipe e não do código.

{{< youtube Il8FlhR9jKM >}}

  



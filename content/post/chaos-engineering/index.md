+++
author = "Thiago Gil"
title = "Engenharia do Caos"
date = "2021-11-25"
description = "Como testar resiliência de forma contínua (e ainda economizar)"
categories = [
    "Google Cloud"
]
tags = [
    "Chaos Engineering", "FinOps", "GKE"
]
image = "astro_closed.png"
+++

Chaos Engineering enquanto você economiza recursos? <!--more-->
O GCP tem instâncias preemptivas. Como os data centers são construídos para demandas de pico, muitas vezes (sazonalidade, hora do dia, dia da semana) há uma grande quantidade de capacidade de servidor ociosa e sobressalente. As instâncias preemptivas oferecem esses servidores ociosos a um preço de lista reduzido para maximizar a utilização dos datacenters do GCP. 

As instâncias preemptivas têm as seguintes características:

1. Não é garantido que eles estejam disponíveis.
2. Eles vivem no máximo 24 horas e são encerrados automaticamente.
3. Eles podem ser rescindidos antes de 24 horas com aviso prévio de 30 segundos.
4. As instâncias são até 80% mais baratas quando comparadas aos preços sob demanda.
5. SSDs, TPUs e GPUs locais anexados a instâncias preemptivas também têm grandes descontos.
6. Não há leilão e não há capacidade de estender a vida útil além de 24 horas, ao contrário das Instâncias Spot.
7. O preço das instâncias preemptivas é conhecido com antecedência.

As instâncias preemptivas têm uma grande reputação de economia de custos, mas péssimas em termos de confiabilidade. Os engenheiros imploram para não usar instâncias preemptivas para que possam se concentrar em escrever recursos em vez de lidar com problemas de confiabilidade "artificiais". “Por que não podemos simplesmente pagar por instâncias de preço total e executar tudo de forma confiável?”, “Eu tenho um prazo para entregar este recurso e não tenho tempo para isso.” eles dizem ... Deixe-me dizer a você. Não há nada artificial sobre os problemas de confiabilidade que você enfrenta ao executar instâncias preemptivas. Instâncias preemptivas apenas tornam a falha uma ocorrência diária garantida, que teria acontecido de qualquer maneira. As instâncias de VM precisam de manutenção periódica, os servidores físicos travam, o GCP apresenta interrupções. Pagar mais não vai impedir que esses eventos aconteçam, mas quando eles acontecerem, você estará despreparado, pois estava se escondendo dos fracassos, não os procurando.

Espere aí, o que isso tem a ver com Engenharia do Caos? A engenharia do caos é a disciplina de fazer experimentos em um sistema de software em produção para construir confiança na capacidade do sistema de resistir a condições turbulentas e inesperadas. As primeiras ferramentas no domínio da Chaos Engineering eram muito focadas em falhas no nível da instância. A maturação levou ao caos na rede, IAM e até mesmo exclusões aleatórias de recursos no Kubernetes.

Instâncias preemptivas podem atuar como uma ferramenta fundamental da Engenharia do Caos e um excelente ponto de partida. Eu sei que muitos de vocês desejam experimentar a Engenharia do Caos, mas é um argumento difícil de fazer.

Compare isso

> Ei, vou gastar valioso tempo de engenharia e dinheiro em produtos da Chaos Engineering para quebrar coisas (sim, quebre com mais frequência do que já fazemos) para que possamos ter um futuro mais confiável.


Com isso

> Ei, existe uma maneira de economizar até 80% em nossas instâncias caras e, ao mesmo tempo, tornar nossa infraestrutura e aplicativos mais confiáveis ​​ao mesmo tempo.
﻿# messaging-springboot

Este é um projeto de introdução à mensageria com Kafka e Spring seguindo a [videoaula](https://www.youtube.com/watch?v=97TF2xZgAhU) da [Giuliana Bezerra](https://github.com/giuliana-bezerra).


 # Introdução
Para compreender o conceito de mensageria, é fundamental entender o contexto dos sistemas distribuídos, especialmente em ***arquiteturas de microsserviços***. Nestes ambientes, a coordenação eficiente entre serviços é essencial para garantir operações fluidas.

# Exemplo de Aplicação
Imagine um cenário de um e-commerce, onde a realização de um pedido aciona serviços como inventário, pagamento e entrega. A dependência entre esses serviços é evidente: um contratempo em qualquer um deles pode comprometer o processo inteiro de realização do pedido.

# Problema da Indisponibilidade Temporária
Para contornar problemas de indisponibilidade temporária, surge a mensageria. Antes de o serviço de pedidos acionar outros serviços, introduz-se um intermediário, o ***Message Broker***. Este componente recebe eventos do serviço de pedidos e os distribui para os demais. Se um serviço torna-se momentaneamente indisponível, o Message Broker realiza tentativas de reenvio (***retry***) para acionar o serviço.

# Modelo Publish/Subscribe
O sistema adota o modelo ***publish/subscribe***, onde um serviço publica um evento e outros serviços se inscrevem para consumi-lo. Essa abordagem garante desacoplamento e escalabilidade, uma vez que cada serviço pode operar de maneira independente.

Ao implementar esse sistema, mesmo ocorra uma falha temporária em um serviço específico, apenas uma parte da operação é prejudicada, evitando falhas totais e garantindo a continuidade das operações.

# Detalhes do Message Broker
Exemplos comuns de Message Brokers incluem ***RabbitMQ***, ***Apache Kafka*** e ***AWS SNS/SQS***. O Message Broker não apenas facilita a distribuição de eventos, mas também oferece recursos como políticas de retry e backoff, fortalecendo a resiliência do sistema.

Essa abordagem não só melhora a confiabilidade do sistema, mas também contribui para a manutenção da integridade operacional em ambientes dinâmicos e distribuídos.

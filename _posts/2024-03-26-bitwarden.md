---
layout: post
title: Uma introdução informal ao Bitwarden (PT-BR)
date: 2024-03-26 21:35:00-0300
description: Entenda porque usar um gerenciador de senhas
tags: cybersecurity
giscus_comments: false
related_posts: false
thumbnail: assets/img/bitwarden_logo.png
---

Obs: *Este é um artigo que eu escrevi pra enviar às pessoas dos meus círculos sociais, porque como todo usuário de Bitwarden eu constantemente recomendo às pessoas que usem Bitwarden - não um gerenciador de senhas qualquer, o **Bitwarden**. Isto não é e nunca pretendeu ser uma descrição completa de gerenciadores de senha, mas sim uma apresentação informal ao tema.*

Obs2: Isso vai precisar de revisão no futuro

Então você caiu na minha armadilha e decidiu se aventurar no mundo dos gerenciadores de senha. Parabéns, sua vida está a poucos passos de se tornar melhor. Antes de explicar como realmente usar esse negócio, eu vou lhe contar os motivos de querer usar, e como funciona. Se você quiser, pode pular lá pro final.

# Problemas da vida sem gerenciador de senha
Se você não usa um gerenciador de senha, eu vejo três opções pra a sua vida digital:

1. Você usa entre uma e três senhas pra todos os sites e apps que acessa. Esse é o caso da maiorias das pessoas (juro)
2. Você usa mais senhas, mas não tem uma distinta pra cada site que acessa. Esse é um caso menos comum.
3. Você tem um sistema pra gerar uma senha a partir do serviço (por exemplo, manipulando o endereço do site ou informações sobre o serviço que ele presta). Eu já vi alguém que não era eu fazendo isso, então estou incluindo aqui pra caso você também faça.

## 1: menos de 3 senhas pra tudo - caso mais comum e pior caso
Esse é o jeito menos seguro de usar a internet. Se um site onde você tem cadastro sofre um vazamento de informações (o que é **muito** comum), a primeira coisa que pessoas mal-intencionadas vão fazer é pegar essas informações e tentar usar em outros sites. Então se você, por exemplo, usa o mesmo email e senha no Facebook e no Twitter, e o Twitter tem as contas vazadas, alguém provavelmente vai pegar seu email e senha do Twitter (que vazaram) e tentar usar no Facebook, e aí a pessoa vai ter acesso à sua conta do Facebook. Isso é terrível.

## 2: mesmo que o anterior, mas com mais senhas
Se você se enquadra na categoria 2, você pode até acreditar que está em mais segurança do que as pessoas da categoria 1, mas a realidade é que as chances de se dar mal são altíssimas do mesmo jeito. É melhor, mas não ajuda tanto assim.

## 3: você usa um sistema
Se você usa um sistema pra gerar senhas, você é nerd o suficiente pra saber que já passou da hora de usar um gerenciador de senhas.

A ideia do sistema é fazer uma função em cima do site/app pra obter a senha. Por exemplo, um sistema muito simples seria inverter o nome do site. Aí sua senha do Twitter seria rettiwT.

Usar um sistema é horrível. Imagine que vazaram a sua conta do Twitter, e agora o mundo inteiro sabe que sua senha é rettiwT. Você precisa mudar a senha, mas se você mudar a senha vai ter que ser pra uma que não faz parte do sistema, e aí o seu sistema deixa de funcionar. Além disso, se o sistema é confortável o suficiente pra você conseguir gerar uma senha de cabeça, ter acesso a poucas senhas já deve revelar um padrão, e aí basta reunir algumas (em vez de uma, como nos casos anteriores) contas vazadas pra a pessoa maliciosa conseguir acessar suas contas.

## Não é só sobre a quantidade de senhas
Suas senhas são horríveis. Provavelmente você usa uma senha baseada em algum aspecto ou interesse seu (`starwars`), ou simplesmente um padrão ridículo (tipo `123456`). A senha de um amigo meu costumava ser `[nome dele]sk8`. Ele fez isso porque era uma criança. Não tome as decisões que essa criança tomava. Hoje em dia existem ferramentas muito eficazes pra fazer um perfil seu e adivinhar sua senha baseado em informações sobre a sua vida, então não importa o que você faça, se a senha vier da sua cabeça, ela é enviesada.

## Uma nota sobre ouvir teclas
Se você procurar na internet, vai ver que existem vírus que ouvem você digitando e calculam as teclas pressionadas pra descobrir sua senha. Tecnicamente um gerenciador de senhas resolve esse problema também, mas em teoria existiriam outras soluções pra fugir disso. Eu não me importo com esse problema.

# Como gerenciadores de senha funcionam
Um gerenciador de senhas, essencialmente, é uma caixa preta que contém todas as suas informações de login por você. Geralmente isso inclui uma ferramenta pra gerar senhas aleatórias de tamanho arbitrário e também uma ferramenta de auto-preencher (aí você não precisa copiar as senhas do gerenciador pra o site onde quer logar).

A graça disso é que você pode ter senhas muito grandes e completamente aleatórias, uma pra cada site, e aí se algum site tiver as informações vazadas isso não afeta nenhuma das suas outras contas. Você só precisa lembrar da senha que usa no gerenciador de senhas, e ele lembra das outras por você.

# Mas e se vazarem as informações do meu gerenciador de senhas?
Uma coisa que eu não revelei antes porque queria que você caísse na armadilha didática de fazer essa pergunta é que o único jeito de vazarem a sua senha é se ela for guardada em texto simples, isto é, sem ser criptografada. Uma senha criptografada parece um bando de lixo - abaixo eu coloquei um exemplo de criptografia da senha `senha`:

```
U2FsdGVkX1/SGXg12MFWD0VHZc759C1k+NLloiMU2KY=
```

Se a sua senha criptografada vazar, ninguém consegue usar ela, a menos que o site que você usa estiver usando uma criptografia muito antiga (que é um problema muito real!)

Nesse momento você talvez diga: "mas Raul, então não é só todos os sites da internet usarem sempre um algoritmo moderno de criptografia?" E a resposta é sim, mas eu te prometo que sempre vai ter um site ruim/antigo/mal feito/com um problema novo que  ninguém descobriu ainda. Então nos sobra uma solução: vamos deixar todas as nossas senhas em **um site** que use sempre um algoritmo moderno de criptografia. Essa é a ideia do gerenciador de senhas.

Se você usar qualquer gerenciador de senhas decente, as senhas vão estar cifradas no banco de dados deles. Resumindo, isso de vazarem informações não é um problema.

# Como o Bitwarden é melhor do que o resto
O Bitwarden é código aberto. Isso significa que tem milhares de nerds de segurança da informação que ficam inspecionando o código pra garantir que funciona direito. Ele está presente em basicamente qualquer sistema operacional pra dispositivos móveis ou computadores, e tem uma comunidade amigável. Por fim, ele é de graça pra uso pessoal. É o melhor que você pode pedir.

# Usando o Bitwarden
Basicamente, você vai [criar uma conta](https://vault.bitwarden.com/#/register?layout=default) (não crie ainda! eu vou explicar uma coisa lá embaixo sobre escolher sua senha do bitwarden), baixar o aplicativo de celular, e instalar a extensão no seu navegador do computador (firefox, edge, chrome, etc). Links pra todas essas coisas estão disponíveis [aqui](https://bitwarden.com/download/).

Depois é só usar: você usa o *vault* pra encontrar suas contas salvas e salvar novas contas, e o gerador pra gerar senhas aleatórias. 

<div class="row">
    <div class="col">
        {% include figure.html path="assets/img/bitwarden_ss.png" class="img-fluid rounded z-depth-1" zoomable=true %}
    </div>
</div>
<div class="caption">
Algumas coisas da interface do Bitwarden
</div>

## Escolhendo uma senha para o seu gerenciador de senhas
Antes de você criar uma conta, você precisa escolher uma boa senha. Siga minhas instruções e vai dar tudo certo:

1. Procure um gerador de palavras aleatórias na internet. Qualquer um serve, por exemplo, o primeiro resultado na minha pesquisa foi [esse aqui](https://www.palavrasaleatorias.com). 
2. Gere uma lista de palavras aleatórias e escolha entre 3 e 5, que juntas tenham pelo menos uns 16 caracteres. Seguindo o exemplo, digamos que as palavras foram `manusear`, `amor` e `demolir`
3. Junte elas em um palavrão só: `manusearamordemolir`
4. Insira pontuação e caracteres especiais no meio das palavras: `manuse!aramo,rdemoli1r`. Nesse ponto, a graça é quebrar a palavra pra evitar ataques de dicionário, que ficam tentando usar palavras comuns e suas variações pra descobrir sua senha (por exemplo, `demolir`, `d3m0l1r`,`DEMOLIR`)
5.  Pronto, você tem uma senha!

## E se eu morrer e ninguém da minha família tiver acesso às minhas contas porque eu fui obcecado por segurança da informação?
Quebre sua senha em duas metades e entregue elas pra duas pessoas de confiança que não têm contato. Diga que se algum dia você morrer, a outra pessoa tem a outra metade.

# Uma nota sobre segurança da informação
Não existe segurança completa, existem graus de segurança. Alguém com motivação e recursos suficientes sempre vai conseguir obter as suas senhas. Por exemplo, a pessoa pode invadir sua casa e plantar uma câmera apontada para o seu teclado, e ver tudo que você digita, ou simplesmente te sequestrar e torturar até você revelar as suas senhas. É conhecimento geral que muitos governos do mundo inserem vulnerabilidades em chips utilizados nos celulares e computadores comerciais. Mas aí vem a seguinte consideração: se você está fugindo da ABIN, não sou eu que vou conseguir te ajudar. Boa sorte.

Um gerenciador de senhas é a melhor solução que nós temos atualmente para controle de credenciais num cenário casual. Não é perfeito, mas funciona muito bem, e com certeza muito melhor do que manter as senhas na sua cabeça.

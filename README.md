# Análise de Sentimentos
 
Este projeto realiza a análise de sentimentos de textos e tweets utilizando a biblioteca SpaCy e o pacote SpacyTextBlob. O objetivo é identificar a polaridade do texto, que pode variar de -1 (avaliação negativa) a 1 (avaliação positiva).

## Passos para Execução

### Passo 1: Instalando as Bibliotecas

Primeiro, atualize o `pip`, `setuptools`, e `wheel`, e instale o SpaCy e o SpacyTextBlob:

```bash
    !pip install -U pip setuptools wheel
    !pip install -U spacy
    !python -m spacy download en_core_web_sm
    !pip install spacytextblob
```
### Passo 2: Importando Bibliotecas e Recarregando o Ambiente

Importe as bibliotecas necessárias e recarregue o ambiente:

```python
    import pkg_resources
    import imp
    imp.reload(pkg_resources)

    import spacy
    from spacytextblob.spacytextblob import SpacyTextBlob
```
### Passo 3: Definindo o Modelo e a Pipeline

Carregue o modelo SpaCy e adicione o pipeline SpacyTextBlob:

```python
    nlp = spacy.load('en_core_web_sm')
    nlp.add_pipe('spacytextblob')
```
### Passo 4: Análise de um Texto Inicial 

Defina um texto e analise a polaridade:

```python
    user_input = 'This is a wonderful campsite. I loved the serenity and the birds chirping in the morning.'
    doc = nlp(user_input)
```
### Passo 5: Exibindo o Resultado da Análise

Defina um texto e exiba a polaridade:

```python
    input_polarity = doc._.polarity

    sentiment = {
        'score': input_polarity
    }
    print(sentiment)
```
### Passo 6: Definindo a Lista de Tweets a Serem Analisados

Defina uma lista de tweets para análise:

```python
    tweets = [
        "Bayer Leverkusen goalkeeper Bernd Leno will not be going to Napoli. His agent Uli Ferber to Bild: I can confirm that there were negotiations with Napoli, which we have broken off. Napoli is not an option. Atletico Madrid and Arsenal are the other strong rumours. #B04 #AFC",
        "Gary Speed v Blackburn at St James in 2001/02 anyone? #NUFC #BEL #JAP #WorldCup",
        "@ChelseaFC Don't make him regret it and start him over Hoofiz",
        "@LiverpoolFF @AnfieldEdition He's a liar, made up. I've unfollowed him as loads of others have. Pure blagger. #LFC",
        "@theesk @Everton Didn't realise Kenwright is due to leave at the end of the month. In all seriousness could you see him being interested in us?",
        "@hasanshahbaz19 @LFC My knowledge has decreased somewhat in the past few seasons",
        "Report: Linked with #Everton and #Wolves, Italians set to sign £4.5m-rated winger",
        "Am seeing tweets that there’s been a fall out @Everton between the money men... I’m presuming it’s just a quiet news day or some kopite with nothing better to do! @ALANMYERSMEDIA",
        "@LFC @officialAL20 @IntChampionsCup @ManUtd Expect loads of excuses after tonight’s game",
        "@MartinDiamond17 @azryahmad @Baren_D @Mathewlewis1997 @iamheinthu @DiMarzio @Alissonbecker @LFC @SkySportsNews @SkySport @OfficialASRoma I’m just fine I have your fanbase angry over stating facts should ask them hun. Xo",
        "What a weekend of football results! @ManUtd @Glentoran @RangersFC &amp; Hearts ????",
        "@ChelseaFC For the first time in a long while, my heart was relaxed while watching Chelsea. Really enjoyed it today. Come on, CHELSEA!!!",
        "@ChelseaFC @CesarAzpi What a fantastic signing worth every single penny ??",
        "Pogba scores, Pogba assists. But tomorrow papers won't be telling you this, instead they will tell you how he'll end up at Juve because he's unhappy, frustrated, have grudges with Mourinho and so on and so forth #mufc",
        "@WestHamUtd we need to keep @CH14_ and get @HirvingLozano70 to compliment",
        "@kevdev9 @Everton Shouldn’t be happening! Needs to stay away with his venomous attitude until he is sold!",
        "@brfootball @aguerosergiokun @ManCity What a genius. Pep taking winning mentality with him, conquering league after league. Baller",
        "@HMZ0709  Can we get a RT for our #lfc Mo Salah Liverpool Enamel Pin Badge"
    ]
```
### Passo 7: Analisando os Tweets

Para analisar a lista de tweets, execute o seguinte código:

```python
    for item in tweets:
        doc = nlp(item)
        input_polarity = doc._.polarity
        sentiment = {
            'tweet': item,
            'score': input_polarity
        }
        print(sentiment)
```

The dataset consists of the articles published by NOS which is one of the biggest news organizations in the Netherlands. Here we have intended to create a Deep Neural Network classification
model which classifies the news Articles into corresponding topics. There were over 100 categories which were transformd to 10 basis fequency along with Others category.

The first process was text preprocessing, i.e- removing stopwords and HTML tags and punctuations, dealing with **contractions** and lemmatization using **Spacy**(nl_core_news_sm) model.

We used **RobBERT** Dutch embeddings for each of the words and when the classifer was initially created, it gave an accuracy of 56%. 
After that, we intended to apply **Heirarachial attention Model** on the articles. It works as follows:- 

First a representation of a sentence is learnt given the words basis attention mechanism. Hence this Attention Layer represents a sentence with learned attention weights on words.
The second Attention layer learns representation of a paragraph from the learned attention weights of sentences. 

Attention mechanism improved the accuracy from **56%** to **72%**.

After creating that model, using the learned sentence attention weights for a paragraph, we also created a summary for each of the news articles using the 4 most high weighted sentences. 

For ex:- This is the complete news article:- 


Oekraïne heeft de strategie aangepast van het tegenoffensief in het zuiden en oosten van het land. Volgens militair analisten richt het leger zich nu met name op het uitputten van de Russische troepen in plaats van een grote, geconcentreerde aanval op één plek langs het front. De strategie is terug te zien in herhaaldelijke aanvallen, ver achter de frontlinies. De plannen zijn noodgedwongen aangepast vanwege de grote verliezen aan het begin van het tegenoffensief, dat begin juni van start ging. "In de eerste weken trokken de troepen naar voren, maar dat ging gepaard met grote verliezen", zegt veiligheidsdeskundige Maria Avdeeva van de Oekraïense European Expert Association. Volgens The New York Times raakte zo'n 20 procent van de ingezette wapens beschadigd of vernietigd, waaronder westerse tanks en pantservoertuigen. Daartegenover stond vrij beperkte terreinwinst: zo'n 300 vierkante kilometer. Deze gebieden heeft Oekraïne in de afgelopen anderhalve maand bevrijd: Oekraïne opereert voorzichtiger dan Rusland, ziet brigadegeneraal Han Bouwmeester, hoogleraar militair-operationele wetenschappen bij de Nederlandse Defensie Academie. "Oekraïne is voorzichtig met hun mensen en materieel. Die wil je niet klakkeloos een mijnenveld insturen." In de eerste weken van het tegenoffensief hebben de Oekraïense strijdkrachten gezocht naar zwakke punten in de verdediging, maar die lijken er niet te zijn; de linies blijken sterk voor het Oekraïense leger, dat geen luchtoverwicht heeft en kampt met een dreigend munitietekort. "Doordat Oekraïne moest wachten op wapenleveranties, kon Rusland de verdediging op orde brengen", zegt Avdeeva. "Er zijn meervoudige linies opgezet en er liggen heel veel mijnen." Zo ziet de Russische verdediging eruit: Met name de mijnen maken het maken van een grote doorbraak lastig. Oekraïense genietroepen beschikken over onvoldoende middelen om een weg te banen in de velden vol explosieven. Volgens The Washington Post heeft Kyiv zo'n 15 procent van de gevraagde ontmijningsmiddelen van het Westen ontvangen. In de tussentijd verlegt Oekraïne de focus op het 'slijten' en uitputten van de vijandelijke troepen. Dat gebeurt bijvoorbeeld met eigen troepenverplaatsingen, zegt oud-Commandant Landstrijdkrachten Mart de Kruif. "Oekraïne heeft kortere logistieke lijnen, dus het kan sneller troepen verplaatsen van zuid naar noord. Rusland moet meer werk verrichten om eenheden te verschuiven, en dat werkt uitputtend." Belangrijker zijn de gerichte aanvallen achter het front, ziet Avdeeva. Munitiedepots, aanvoerlijnen en oefenterreinen zijn doelwit van talloze aanvallen in de afgelopen weken. "Wat Rusland als veilig gebied beschouwde, wordt nu aangevallen met langeafstandsraketten", aldus de analist. Neem de strategisch belangrijke Krimbrug, of een hotel aan de kust waar een Russische topcommandant werd uitgeschakeld. De doelen 'in de diepte' zouden Rusland op de lange termijn in de problemen kunnen brengen. "Alles wat je achter het front uitschakelt, verschijnt niet meer aan het front", zegt Bouwmeester. Dat geldt voor materieel, maar ook voor reservisten die uitgeputte militairen moeten vervangen. De slijtage moet ertoe leiden dat de Russische verdediging uiteindelijk zwaktes gaat vertonen. "Als ergens het moreel breekt, kun je daar toehappen", zegt De Kruif. Oekraïne lijkt de middelen te hebben om alsnog met de grote 'push' te komen, denkt Bouwmeester. "Er zouden negen tot twaalf gevechtsbrigades getraind zijn, waarvan er vier tot zes zijn ingezet. Er zijn nog eenheden achter de hand dus." Bij de uitputtingsstrategie speelt tijd een belangrijke rol. "Er bestond in Oekraïne en het buitenland het misverstand dat het tegenoffensief een snelle operatie zou zijn", zegt Avdeeva. "Maar dit is echt anders dan de bevrijding van de regio Charkiv en de stad Cherson." In dit overzicht zie je met welk tempo gebied werd bezet of bevrijd in de afgelopen maanden: Die tijd is alleen schaars. Iedere dag oorlog maakt het land meer kapot, ook financieel. Daarom had Kyiv liever een grote doorbraak aan het front geforceerd, zegt Avdeeva. "Rusland gebruikt de tijd ondertussen om meer wapens en drones te kopen en produceren", zegt Avdeeva. Oud-Commandant De Kruif ziet daarentegen een snelle toename van westerse wapenproductie. "Als dat echt op stoom komt, produceert het Westen meer dan Rusland."


**Summary:-**

'Oekraïne heeft de strategie aangepast van het tegenoffensief in het zuiden en oosten van het land.', '"In de eerste weken trokken de troepen naar voren, maar dat ging gepaard met grote verliezen", zegt veiligheidsdeskundige Maria Avdeeva van de Oekraïense European Expert Association.', 'Deze gebieden heeft Oekraïne in de afgelopen anderhalve maand bevrijd: Oekraïne opereert voorzichtiger dan Rusland, ziet brigadegeneraal Han Bouwmeester, hoogleraar militair-operationele wetenschappen bij de Nederlandse Defensie Academie.', 'In de eerste weken van het tegenoffensief hebben de Oekraïense strijdkrachten gezocht naar zwakke punten in de verdediging, maar die lijken er niet te zijn; de linies blijken sterk voor het Oekraïense leger, dat geen luchtoverwicht heeft en kampt met een dreigend munitietekort.'

In English, this translated to:- 
Ukraine has adjusted the strategy of the counter-offensive in the south and east of the country.', '"In the first weeks the troops moved forward, but this was accompanied by high losses," says security expert Maria Avdeeva of the Ukrainian European Expert Association .', 'Ukraine has liberated these areas in the past month and a half: Ukraine operates more cautiously than Russia, sees Brigadier General Han Bouwmeester, professor of military-operational sciences at the Dutch Defense Academy.', 'In the first weeks of the counter-offensive, the Ukrainian armed forces looked for weak points in the defense, but there appear to be none; the lines appear to be strong for the Ukrainian army, which has no air superiority and is facing a looming ammunition shortage.



# Slide Notes - Workshop Update (19 februari 2026)

## Slide 1 - Afstudeerupdate: Interaction Generator voor Recommender Systems
Doel: in 20-30 seconden kaderen wat je komt laten zien.

Spreeknotities:
"Vandaag geef ik een korte update van mijn afstudeerwerk over het genereren van synthetische gebruikersinteracties voor recommender systems. Ik loop kort door de context, de literatuurkloof, mijn eerste onderzoeksvraag en de voorgestelde methode. Ik wil vooral feedback ophalen op de evaluatie-aanpak."

Overgang:
"Eerst heel kort waarom dit probleem nu relevant is."

## Slide 2 - Korte context van het onderzoeksgebied
Doel: uitleggen waarom statische evaluatie niet genoeg is.

Spreeknotities:
"Veel recommender systems worden nog geëvalueerd op statische logs, terwijl gedrag in de praktijk dynamisch en feedback-gedreven is. Als een model aanbevelingen verandert, veranderen gebruikersreacties mee, en dus ook toekomstige trainingsdata. Daarom hebben we synthetische interactielogs nodig die sessies, acties en timing bevatten. In mijn setting is arrival-generatie al aanwezig; het ontbrekende en nu centrale stuk is interaction generation."

Tier-link:
- Tier 1/Tier 2 benadrukken recurrente feedback loops als kern van simulatie-realiteit (o.a. Stavinova, SIREN, T-RECS).

Overgang:
"Dan waar mijn werk in het bredere synthetic-data landschap valt."

## Slide 3 - Synthetic data landscape -> focus op RS
Doel: van brede surveys naar RS-specifiek probleem vernauwen.

Spreeknotities:
"In de brede synthetic-data literatuur ligt de focus vaak op schaarste, privacy en algemene utility-evaluatie. In RS is een aparte simulatie-substroom ontstaan, met eigen problemen rond validatie en reproduceerbaarheid. Voor mijn thesis betekent dit: ik wil niet alleen een next-item voorspeller bouwen, maar een model dat complete interactielogs kan genereren voor training en evaluatie."

Tier-link:
- Tier 2 paper 6 (Abufadda): brede motivatie rond data-schaarste/privacy.
- Tier 2 paper 7 (Jordon): utility/fidelity/privacy als evaluatiekader.
- Tier 2 paper 8 (Lu): moderne modelmix incl. autoregressieve benaderingen.

Overgang:
"Vervolgens laat ik de belangrijkste RS-simulatie-aanpakken zien."

## Slide 4 - Bestaande RS-simulatie aanpakken
Doel: laten zien dat je het veld inhoudelijk beheerst en een lege plek ziet.

Spreeknotities:
"De Stavinova-survey laat zien dat er veel typen simulators naast elkaar bestaan: framework-gedreven platforms zoals SIREN en T-RECS, process-based modellen zoals Accordion, en meer datasetgeneratoren zoals DataGenCARS en Jakomin. Elk type heeft sterke punten: bijvoorbeeld lange-termijn dynamiek of controle over scenario’s. Maar er is geen duidelijke convergentie naar één dominante interaction-generator architectuur voor RS."

Tier-link:
- Tier 1 paper 1 (Stavinova): taxonomie + quality-control gat.
- Tier 2 paper 1 (SIREN): lange-termijn effectsimulatie.
- Tier 2 paper 2 (T-RECS): modulair, reproduceerbaar simulatiekader.
- Tier 1 paper 2 (Accordion): continue-tijd en visit-dynamiek.
- Tier 1 papers 5-6 (Jakomin, DataGenCARS): controleerbare generatoren, minder rijke sequence-modellering.

Overgang:
"En precies daar zit de kernkloof die ik wil adresseren."

## Slide 5 - Literatuurkloof (kern)
Doel: centrale probleemdefinitie scherp formuleren.

Spreeknotities:
"Mijn kernobservatie is dat twee literatuurstromen parallel zijn gegroeid. RS-simulatiepapers genereren data, maar gebruiken nauwelijks transformer-gebaseerde sequence-modellen. Tegelijk laat sequential recommendation juist sterke sequence-capaciteit zien, maar vooral voor predictie in plaats van log-generatie. Dus: de modellen die sequenties goed begrijpen, worden nog niet systematisch ingezet als simulator van interacties."

Tier-link:
- Tier 1 paper 1 (Stavinova): benoemt heterogeniteit en gebrek aan standaardisatie.
- Tier 1/2 methodepapers: veel dynamiekmodellen, weinig transformer-centrisch genereren.

Overgang:
"Op basis daarvan is dit mijn eerste onderzoeksvraag."

## Slide 6 - Eerste draft onderzoeksvraag
Doel: onderzoekbaar en vergelijkbaar formuleren.

Spreeknotities:
"Mijn eerste draft RQ is: hoe en in welke mate kan een autoregressieve transformer realistische synthetische interactielogs genereren voor training en evaluatie van recommender systems? De expliciete subvraag is of dit beter werkt dan regel/statistische en GAN-gebaseerde alternatieven. Mijn werkhypothese: betere sequentiële fideliteit én betere downstream utility."

Praktische afbakening die je mondeling kunt toevoegen:
- "Realistisch" operationaliseren via fidelity-metrics en validiteitsregels.
- "Beter" operationaliseren via baselinevergelijking op identieke evaluatiepipeline.

Overgang:
"Dan kort hoe de voorgestelde methode eruit ziet."

## Slide 7 - Voorgestelde methode: multi-head autoregressieve transformer
Doel: de methode controleerbaar en technisch concreet maken.

Spreeknotities:
"Per tijdstap genereert het model een volledige tuple: user, session, action, item, delta-t en context. Met een multi-head opzet splits ik de conditionele structuur op: eerst actie, daarna item gegeven actie en historie, en daarna timing gegeven actie+item+historie. Dat maakt causale generatie expliciet en maakt constraints afdwingbaar, bijvoorbeeld dat purchase niet zonder eerdere view of cart kan."

Tier-link:
- Tier 1/2 tonen dat bestaande simulatoren vaak sterk zijn in deelaspecten (tijd, scenario, feedback), maar minder in één unified sequence-generator voor rijke event-tuples.

Overgang:
"Waarom ik AR-transformers als hoofdroute kies, en niet GAN als primaire aanpak:"

## Slide 8 - Waarom AR-transformer i.p.v. GAN als hoofdroute?
Doel: architectuurkeuze verdedigen met literatuur.

Spreeknotities:
"Voor dit type data - discrete event tokens met volgorde en afhankelijkheden - sluit autoregressieve generatie natuurlijk aan. In GAN-literatuur zien we bekende risico’s zoals mode collapse en instabiele training, en dat kan juist gedragsdiversiteit schaden. Daarnaast bieden AR-modellen betere controllability via prefix-conditioning en step-wise likelihoods, wat de vergelijking met baselines en ablaties transparanter maakt."

Tier-link:
- Tier 3 paper 1 (Creswell): mode collapse/instabiliteit als structurele GAN-uitdaging.
- Tier 2 paper 9 (Figueira): zelfde stabiliteitsproblemen + evaluatiecomplexiteit.
- Tier 2 paper 8 (Lu): autoregressieve modellen expliciet relevant voor sequentiële data.

Overgang:
"Tot slot: waar ik nu sta en welke feedback ik zoek."

## Slide 9 - Labomgeving + eerste indruk + next steps
Doel: status + concrete feedbackvraag.

Spreeknotities:
"Mijn eerste indruk is dat de literatuurbasis sterk genoeg is om gericht te bouwen en te vergelijken. De eerstvolgende stappen zijn: baseline set vastleggen, fidelity-metrics implementeren, en downstream RS-evaluatie uitvoeren. De belangrijkste feedback die ik vandaag zoek: welke minimale metriekset moet ik volgens jullie rapporteren zodat een interaction simulator inhoudelijk overtuigend is?"

Concreet feedbackkader dat je kunt benoemen:
- Fidelity: marginals + sequence/statetransition checks + temporal realism.
- Utility: train-on-synthetic, test-on-real prestaties en ranking-stabiliteit.
- Validity: rule-violation rate van gegenereerde eventlogica.

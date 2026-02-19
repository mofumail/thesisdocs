# Workshop Update Slides (NL)
## Slide 1: Afstudeerupdate: Interaction Generator voor Recommender Systems
Expert Workshop PvA tips + Projectvoorstel
19 februari 2026
Beau
**Spreeknotities:**
Doel in 1 zin: stand van zaken en voorgestelde onderzoeksrichting tonen.
Timing: ~30 sec.

## Slide 2: 1) Korte context van het onderzoeksgebied
- Recommender systems worden meestal geëvalueerd met statische data, terwijl gedrag dynamisch is.
- Voor realistische evaluatie is synthetische interactiedata nodig (sessies, acties, timing).
- In onze setting: component (1) arrivals bestaat al; component (2) interaction generation moet verbeterd worden.
**Spreeknotities:**
Noem kort waarom dit relevant is voor robustere RS-evaluatie en training. Timing: ~60 sec.

## Slide 3: 2) Synthetic data landscape -> focus op RS
- Breed synthetic-data kader: surveys [1], [19], [21].
- Binnen RS: simulatie als aparte subliteratuur met eigen evaluatieproblemen.
- Doel voor deze thesis: interacties niet alleen voorspellen, maar volledige logs genereren.
**Spreeknotities:**
Houd dit hoog-over; details komen op volgende slides. Timing: ~60 sec.
**Referenties op deze slide:**
- [1] M. Abufadda and K. Mansour, "A Survey of Synthetic Data Generation for Machine Learning," ACIT, 2021. https://doi.org/10.1109/ACIT53391.2021.9677302
- [19] J. Jordon et al., "Synthetic Data—What, why and how?" arXiv:2205.03257, 2022. http://arxiv.org/abs/2205.03257
- [21] Y. Lu et al., "Machine Learning for Synthetic Data Generation: A Review," arXiv:2302.04062, 2024. http://arxiv.org/abs/2302.04062

## Slide 4: 3) Bestaande RS-simulatie aanpakken
- Anchor: Stavinova survey [25] over synthetic-data simulators voor RS.
- Frameworks/simulators: SIREN [4], T-RECS [22], Accordion [24].
- Generators: DataGenCARS [13], Jakomin [18], plus GAN-richtingen.
- Conclusie: veel methodes, maar geen duidelijke convergentie op één dominante aanpak.
**Spreeknotities:**
Laat zien dat je het veld kent en waar de variatie zit. Timing: ~75 sec.
**Referenties op deze slide:**
- [25] E. Stavinova et al., "Synthetic Data-Based Simulators for Recommender Systems: A Survey," arXiv:2206.11338, 2022. http://arxiv.org/abs/2206.11338
- [4] D. Bountouridis et al., "SIREN: A Simulation Framework for Understanding the Effects of Recommender Systems in Online News Environments," FAT*, 2019. https://doi.org/10.1145/3287560.3287583
- [22] E. Lucherini et al., "T-RECS: A Simulation Tool to Study the Societal Impact of Recommender Systems," arXiv:2107.08959, 2021. http://arxiv.org/abs/2107.08959
- [24] J. McInerney et al., "Accordion: A Trainable Simulator for Long-Term Interactive Systems," RecSys, 2021. https://doi.org/10.1145/3460231.3474259
- [13] M. del Carmen Rodríguez-Hernández et al., "DataGenCARS: A generator of synthetic data for the evaluation of context-aware recommendation systems," Pervasive and Mobile Computing, 2017. https://doi.org/10.1016/j.pmcj.2016.09.020
- [18] M. Jakomin, T. Curk, and Z. Bosnić, "Generating inter-dependent data streams for recommender systems," Simulation Modelling Practice and Theory, 2018. https://doi.org/10.1016/j.simpat.2018.07.013

## Slide 5: 4) Literatuurkloof (kern)
- RS-simulatie literatuur en sequential recommendation literatuur zijn parallel ontwikkeld.
- Simulatiepapers genereren data, maar gebruiken vrijwel geen transformer-gebaseerde sequentiemodellen.
- Sequential recommendation papers (SASRec/BERT4Rec/BST) tonen sterke sequence-modellering, maar focussen op predictie i.p.v. generatie.
- Kloof: de modellen die gebruikerssequenties het best begrijpen, worden niet ingezet om die interacties te simuleren.
**Spreeknotities:**
Gebruik deze slide als centrale probleemdefinitie. Timing: ~75 sec.
**Referenties op deze slide:**
- [25] E. Stavinova et al., "Synthetic Data-Based Simulators for Recommender Systems: A Survey," arXiv:2206.11338, 2022. http://arxiv.org/abs/2206.11338

## Slide 6: 5) Eerste draft onderzoeksvraag
- Hoe en in welke mate kan een autoregressieve transformer realistische synthetische gebruikersinteractielogs genereren voor training en evaluatie van recommender systems?
- Subvraag: presteert dit beter dan regel/statistische en GAN-gebaseerde alternatieven?
- Werkhypothese: betere sequentiële fideliteit + betere downstream utility.
**Spreeknotities:**
Noem dat dit een eerste formulering is en feedback welkom is. Timing: ~60 sec.

## Slide 7: 6) Voorgestelde methode: multi-head autoregressieve transformer
- Te genereren tuple per tijdstap: (user_id, session_id, action_type, item_id, Δt, context_t).
- Head A: p(action_t | history)
- Head B: p(item_t | action_t, history)
- Head C: p(Δt_t | action_t, item_t, history)
- Voordeel: causal sequence generation + constraints (bv. geen purchase zonder eerdere view/cart).
**Spreeknotities:**
Dit is je methodeslide: maak het concreet en controleerbaar. Timing: ~90 sec.

## Slide 8: 7) Waarom AR-transformer i.p.v. GAN als hoofdroute?
- Discrete outputs: interactiedata is token-achtig (action/item), AR-modellen zijn hiervoor natuurlijk.
- Stabiliteit/diversiteit: minder gevoelig voor mode collapse dan GAN-training in deze context [11], [16].
- Controllability: prefix-conditioning en expliciete validiteitsregels tijdens generatie.
- Evaluatie: expliciete likelihood per stap maakt vergelijking en ablatie helderder.
**Spreeknotities:**
Koppel expliciet aan je gekozen probleemtype (structured event logs). Timing: ~75 sec.
**Referenties op deze slide:**
- [11] A. Creswell et al., "Generative Adversarial Networks: An Overview," IEEE Signal Processing Magazine, 2018. https://doi.org/10.1109/MSP.2017.2765202
- [16] A. Figueira and B. Vaz, "Survey on Synthetic Data Generation, Evaluation Methods and GANs," Mathematics, 2022. https://doi.org/10.3390/math10152733

## Slide 9: 8) Labomgeving + eerste indruk + next steps
- Labomgeving/dagelijkse routine: [kort mondeling toe te lichten].
- Eerste indruk: sterke basis in literatuur en duidelijke modelrichting.
- Volgende stappen: baselinevergelijking, fidelity-metrics, downstream RS-evaluatie.
- Feedbackvraag: welke evaluatiemetrieken zijn voor jullie essentieel om de simulator als overtuigend te zien?
**Spreeknotities:**
Hou dit persoonlijk en kort; sluit af met concrete feedbackvraag. Timing: ~45 sec.

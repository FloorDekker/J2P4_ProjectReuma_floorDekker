# Reumatoïde Artritis
<p align="center">
  <img src="assets/DNA.png" alt="Dubbel strengs DNA" width="200" />
</p>

___

## Inleiding
Reumatoïde Artritis (RA) is een systemische auto immuunziekte die bij ongeveer 0,5–1 % van de bevolking voorkomt (Deane et al., 2017). De precieze oorzaak is nog onbekend, maar waarschijnlijk ontstaat RA door een combinatie van genetische aanleg, omgevingsfactoren (zoals roken) en een ontregeld immuunsysteem (Romão & Fonseca, 2021). Klinisch kenmerkt RA zich door synovitis, oftewel ontsteking van het gewrichtsslijmvlies, wat leidt tot gewrichtsschade. De diagnose wordt gesteld op basis van symptomen én de aanwezigheid van autoantistoffen zoals rheumatoid factor (RF) en ACPA (Deane et al., 2017). Hoewel RA niet kan worden genezen, kunnen medicijnen de symptomen vertragen en gewrichtsschade verminderen.
Het doel van dit onderzoek is om de genexpressie te analyseren in patiënten met en zonder RA, specifiek binnen pathway hsa05323 (Rheumatoid arthritis), om beter inzicht te krijgen in de processen die meespelen, zodat de diagnose en behandeling verbeterd kunnen worden.

## Methode
De RNA-seq-data van RA-patiënten en gezonde controles zijn geanalyseerd in R. Eerst werden de ruwe reads uitgelijnd op het humane referentiegenoom *(GRCh38)* met het `Rsubread-pakket`. Vervolgens werd een count matrix gegenereerd met `featureCounts`. Deze matrix werd ingelezen in `DESeq2` voor normalisatie en het identificeren van differentieel tot expressie gebrachte genen (DEGs). Genen met een aangepaste p-waarde < 0.05 en een log2-fold change > ±2 werden als significant beschouwd.
De significante genen zijn vervolgens gekoppeld aan KEGG-pathways met het `clusterProfiler-pakket`, met specifieke focus op *pathway hsa05323 (Rheumatoïde artritis)*. Daarnaast is een Gene Ontology (GO)-analyse uitgevoerd met `goseq` om betrokken biologische processen te identificeren. Visualisaties van de resultaten zijn gemaakt met `ggplot2` en `EnhancedVolcano`, en de pathway-activiteit werd in kaart gebracht met pathview.
Een overzicht van de analyseworkflow is opgenomen in het flowschema bijgevoegd in `data`. Daarnaast zijn scripts, resultaten en data (ruwe data, resultaten en metadata gescheiden) beschikbaar. 


## Resultaten
+- 200 woorden, inclusief correcte verwijzingen

## Conclusie
*+- 200 woorden, inclusief aanbevelingen en onderzoek in context
plaatsen*

`Leerdoelen die je moet beheersen (deze mag weg bij het inleveren)`

*(Schuin gaat over de inhoud
van je project* en *dikgedrukt over de competentie beheren):*
• *Je mapt reads met het Rsubread package in R
• Je bepaalt verschillen in genexpressie met het DESeq2 package in R
• Je bepaalt verschillen in KEGG pathways in R
• Je bepaalt verschillen in gene ontologies in R*
• **Je legt uit hoe je onderzoeksgegevens en scripts kan beheren
• Je voert een project uit waarbij je als data steward de projectgegevens beheert
• Je legt uit hoe je als data steward projectgegevens hebt beheerd**

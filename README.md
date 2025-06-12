# Reumatoïde Artritis
<p align="center">
  <img src="assets/DNA.png" alt="Dubbel strengs DNA" width="200" />
</p>

___

## Inleiding
Reumatoïde Artritis (RA) is een systemische auto immuunziekte die bij ongeveer 0,5–1 % van de bevolking voorkomt (Deane et al., 2017). De precieze oorzaak is nog onbekend, maar waarschijnlijk ontstaat RA door een combinatie van genetische aanleg, omgevingsfactoren (zoals roken) en een ontregeld immuunsysteem (Romão & Fonseca, 2021). Klinisch kenmerkt RA zich door synovitis, oftewel ontsteking van het gewrichtsslijmvlies, wat leidt tot gewrichtsschade. De diagnose wordt gesteld op basis van symptomen én de aanwezigheid van autoantistoffen zoals rheumatoid factor (RF) en ACPA (Deane et al., 2017). Hoewel RA niet kan worden genezen, kunnen medicijnen de symptomen vertragen en gewrichtsschade verminderen.
Het doel van dit onderzoek is om de genexpressie te analyseren in patiënten met en zonder RA, specifiek binnen pathway hsa05323 (Rheumatoid arthritis), om beter inzicht te krijgen in de processen die meespelen, zodat de diagnose en behandeling verbeterd kunnen worden.

## Methode
De RNA-seq-data van patiënten met *Reumatoïde Artritis (RA)* en gezonde controles zijn geanalyseerd in `R (versie 4.5.0)`. De ruwe sequentiegegevens werden eerst uitgelijnd op het humane referentiegenoom *(GRCh38)* met het pakket `Rsubread (v2.22.1)`. Het referentiegenoom is geïndexeerd met `buildindex()` en paired-end reads zijn uitgelijnd met `align()`. Vervolgens is met `featureCounts()` een gen-gebaseerde tellingsmatrix gemaakt op basis van een GTF-annotatiebestand van `Ensembl release 114`.
Deze matrix is geanalyseerd met `DESeq2 (v1.48.1)`, waarmee de gegevens zijn genormaliseerd en is bepaald welke genen significant anders tot expressie komen tussen de groepen (de zogenaamde differentieel tot expressie gebrachte genen, DEGs). Genen met een aangepaste p-waarde < 0.05 en een absolute log2-fold change > 2 zijn als significant beschouwd.
De gevonden DEGs zijn gekoppeld aan biologische processen via een *Gene Ontology (GO)-verrijkingsanalyse*, uitgevoerd met `goseq (v1.60.0)`. Hierbij is gecorrigeerd voor genlengtebias (een effect waarbij langere genen vaker als significant worden gedetecteerd) met behulp van `nullp()`. De verrijkte GO-termen zijn gebaseerd op `GO.db (v3.21.0)` en humane genannotaties uit `org.Hs.eg.db (v3.21.0)`.
Visualisaties van de resultaten zijn gemaakt met `ggplot2 (v3.5.2)` en `EnhancedVolcano (v1.26.0)`, en de pathway-activiteit is in kaart gebracht met `pathview (v1.48.0)`, met specifieke focus op *KEGG-pathway hsa05323 (Reumatoïde artritis)*.
Een overzicht van de methode is opgenomen in het bijgevoegde flowschema. De scripts, ruwe data, resultaten en metadata zijn gescheiden beschikbaar in de projectmap.


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

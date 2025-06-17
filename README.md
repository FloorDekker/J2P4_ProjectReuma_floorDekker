# Reumatoïde Artritis
<p align="center">
  <img src="assets/DNA.png" alt="Dubbel strengs DNA" width="200" />
</p>

___

## Inleiding
Reumatoïde Artritis (RA) is een systemische auto immuunziekte die bij ongeveer 0,5–1 % van de bevolking voorkomt (Deane et al., 2017). De precieze oorzaak is nog onbekend, maar waarschijnlijk ontstaat RA door een combinatie van genetische aanleg, omgevingsfactoren (zoals roken) en een ontregeld immuunsysteem (Scherer et al., 2020). Klinisch kenmerkt RA zich door synovitis, oftewel ontsteking van het gewrichtsslijmvlies, wat leidt tot gewrichtsschade. De diagnose wordt gesteld op basis van symptomen én de aanwezigheid van autoantistoffen zoals rheumatoid factor (RF) en ACPA (Deane et al., 2017). Hoewel RA niet kan worden genezen, kunnen medicijnen de symptomen vertragen en gewrichtsschade verminderen.
Het doel van dit onderzoek is om de genexpressie te analyseren in patiënten met en zonder RA, specifiek binnen pathway hsa05323 (Rheumatoid arthritis), om beter inzicht te krijgen in de processen die meespelen, zodat de diagnose en behandeling verbeterd kunnen worden.

## Methode
De RNA-seq-data van patiënten met *Reumatoïde Artritis (RA)* en gezonde controles zijn geanalyseerd in `R (versie 4.5.0)`. De ruwe sequentiegegevens werden eerst uitgelijnd op het humane referentiegenoom *(GRCh38)* met het pakket `Rsubread (v2.22.1)`. Het referentiegenoom is geïndexeerd met `buildindex()` en paired-end reads zijn uitgelijnd met `align()`. Vervolgens is met `featureCounts()` een gen-gebaseerde tellingsmatrix gemaakt op basis van een GTF-annotatiebestand van `Ensembl release 114`.
Deze matrix is geanalyseerd met `DESeq2 (v1.48.1)`, waarmee de gegevens zijn genormaliseerd en is bepaald welke genen significant anders tot expressie komen tussen de groepen (de zogenaamde differentieel tot expressie gebrachte genen, DEGs). Genen met een aangepaste p-waarde < 0.05 en een absolute log2-fold change > 2 zijn als significant beschouwd.
De gevonden DEGs zijn gekoppeld aan biologische processen via een *Gene Ontology (GO)-verrijkingsanalyse*, uitgevoerd met `goseq (v1.60.0)`. Hierbij is gecorrigeerd voor genlengtebias (een effect waarbij langere genen vaker als significant worden gedetecteerd) met behulp van `nullp()`. De verrijkte GO-termen zijn gebaseerd op `GO.db (v3.21.0)` en humane genannotaties uit `org.Hs.eg.db (v3.21.0)`.
Visualisaties van de resultaten zijn gemaakt met `ggplot2 (v3.5.2)` en `EnhancedVolcano (v1.26.0)`, en de pathway-activiteit is in kaart gebracht met `pathview (v1.48.0)`, met specifieke focus op *KEGG-pathway hsa05323 (Reumatoïde artritis)*.
Een overzicht van de methode is opgenomen in het bijgevoegde flowschema. De [ scripts ](https://github.com/FloorDekker/J2P4_ProjectReuma_floorDekker/blob/main/Script) , ruwe data, resultaten en metadata zijn gescheiden beschikbaar in de projectmap.


## Resultaten
De RNA-seq-analyse vond 4572 genen die anders tot expressie komen tussen RA-patiënten en gezonde controles. Hierbij is gebruik gemaakt van een statistische drempel (p-adj < 0,05) en een minimale verandering in genexpressie van vier keer hoger of lager. Van deze genen hadden 2085 genen een verhoogde expressie en 2487 een verlaagde bij RA. Voorbeelden van deze genen zijn SRGN, ZNF683 en BCL2A1 [ Volcano plot ](https://github.com/FloorDekker/J2P4_ProjectReuma_floorDekker/blob/main/Data/Vulcano.png) . Door eisen werden genen uitgesloten waarvan het verschil klein of toevallig is.
[ GO-analyse ](https://github.com/FloorDekker/J2P4_ProjectReuma_floorDekker/blob/main/Data/Rplot.png) onthulde immuun-gerelateerde processen zoals antigeenpresentatie en adaptieve immuniteit. De [ KEGG-pathway-mapping ](https://github.com/FloorDekker/J2P4_ProjectReuma_floorDekker/blob/main/Data/hsa05323.pathview.png) liet zien in het rood omcirkelde deel de activatie van de vroege ontstekingsproces zien; cellen presenteren antigenen aan CD4⁺ T-cellen, waarna deze cytokines (TNF-α, IL-6, IL-1β) produceren, met activatie van NF-κB en gewrichtsschade tot gevolg (Smolen et al., 2016).
Hoewel SRGN, ZNF683 en BCL2A1 niet expliciet in de KEGG-pathway zijn opgenomen, zijn ze functioneel relevant binnen deze stap. SRGN speelt een rol in cytokinesecretie door immuuncellen (Qian et al., 2024), ZNF683 beïnvloedt T-celactiviteit (Behr et al., 2020), en BCL2A1 helpt immuuncellen overleven tijdens ontsteking (Zhou et al., 2020).

## Conclusie
Met RNA-sequencing de genexpressie in RA-patiënten vergeleken met gezonde contro-les, specifiek gericht op genen binnen de RA-pathway. Er zijn 4572 genen gevonden met significant veranderde expressie, waaronder belangrijke immuun-gerelateerde genen zoals SRGN, ZNF683 en BCL2A1. De resultaten bevestigen dat verstoringen in immuunprocessen en ontstekingsroutes, zoals antigeenpresentatie en cytokineproductie, een centrale rol spelen in RA. Deze resultaten geven een beter beeld bij wat er op moleculair gebied speelt bij RA en deze zouden kunnen bijdragen aan diagnostice-ren van patiënten en de behandelingen. 
Voor vervolgonderzoek wordt aanbevolen om de rol van genen zoals SRGN, ZNF683 en BCL2A1 verder te onderzoeken, bijvoorbeeld in cellen of diermodellen. Daarnaast is het nuttig om genexpressiegegevens te combineren met klinische informatie, om beter te kunnen voorspellen hoe de ziekte zich ontwikkelt en hoe patiënten reageren op behandelingen. 

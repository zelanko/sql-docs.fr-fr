---
title: "Traiter manuellement les donn&#233;es (SSAS Tabulaire) | Microsoft Docs"
ms.custom: ""
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "analysis-services"
  - "analysis-services/multidimensional-tabular"
  - "analysis-services/data-mining"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "sql13.asvs.bidtoolset.datarefreshprogressdb.f1"
ms.assetid: 0918c04c-c1e6-45b4-acfa-96fa578e684b
caps.latest.revision: 18
author: "Minewiskan"
ms.author: "owend"
manager: "erikre"
caps.handback.revision: 18
---
# Traiter manuellement les donn&#233;es (SSAS Tabulaire)
  Cette rubrique décrit la procédure permettant de traiter manuellement des données d'espace de travail dans [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)].  
  
 Lorsque vous créez un modèle tabulaire qui utilise des données externes, vous pouvez actualiser manuellement les données à l'aide de la commande Traiter. Vous pouvez traiter une table unique, toutes les tables du modèle, ou une ou plusieurs partitions. Chaque fois que vous traitez des données, vous pouvez également être amené à recalculer les données.  Le traitement de données consiste à obtenir les données les plus récentes à partir des sources externes. Recalculer implique mettre à jour le résultat de toute formule qui utilise les données.  
  
 Sections de cette rubrique :  
  
-   [Traiter manuellement les données](#bkmk_mahually_process)  
  
-   [Progression du traitement des données](#bkmk_data_process_progress)  
  
##  <a name="bkmk_mahually_process"></a> Traiter manuellement les données  
  
#### Pour traiter des données pour une seule table ou toutes les tables d'un modèle  
  
1.  Dans le générateur de modèles, cliquez sur la table que vous souhaitez traiter.  
  
2.  Dans le menu **Modèle** , cliquez sur **Traiter**, puis sur **Traiter** ou **Traiter tout**.  
  
#### Pour traiter les données de toutes les tables qui utilisent la même connexion  
  
1.  Dans [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)], cliquez sur le menu **Modèle** , puis sur **Connexions existantes**.  
  
2.  Dans la boîte de dialogue **Connexions existantes** , sélectionnez une connexion, puis cliquez sur **Traiter**.  
  
#### Pour traiter des données pour une ou plusieurs partitions  
  
1.  Dans [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)], cliquez sur le menu **Modèle** , pointez sur **Traiter**, puis cliquez sur **Traiter les partitions**.  
  
2.  Dans la boîte de dialogue **Traiter les partitions** , dans la zone **Mode**, sélectionnez l'un des modes de traitement suivants :  
  
    |Mode|Description|  
    |----------|-----------------|  
    |**Traiter par défaut**|Détecte l'état de traitement d'un objet de partition et effectue le traitement nécessaire pour faire passer les objets de partition non traités ou traités partiellement dans un état de traitement complet. Les données des partitions et des tables vides sont chargées ; les hiérarchies, les colonnes calculées et les relations sont créées ou reconstruites.|  
    |**Traiter entièrement**|Traite un objet de partition et tous les objets qu'il contient. Lorsque la commande Traiter entièrement est exécutée pour un objet qui a déjà été traité, [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] supprime toutes les données de l'objet, puis traite l'objet. Ce type de traitement est obligatoire lorsqu'une modification structurelle a été apportée à un objet.|  
    |**Traiter les données**|Chargez les données dans une partition ou une table sans reconstruire les hiérarchies ou les relations ni recalculer les colonnes calculées et les mesures.|  
    |**Traiter l'effacement**|Supprime toutes les données d'une partition.|  
    |**Traiter l'ajout**|Mise à jour incrémentielle de la partition avec de nouvelles données.|  
  
3.  Dans la liste des partitions, sélectionnez les partitions à traiter, puis cliquez sur **OK**.  
  
##  <a name="bkmk_data_process_progress"></a> Progression du traitement des données  
 La boîte de dialogue **Progression du traitement des données** vous permet de surveiller le traitement des données que vous avez importées dans le modèle à partir d'une source externe. Pour accéder à cette boîte de dialogue, cliquez sur le menu **Modèle** , puis sur **Traiter les partitions**, **Traiter la table** ou **Traiter tout**.  
  
 **État**  
 Indique si l'opération de traitement a abouti ou non.  
  
 **Détails**  
 Répertorie les tables et les vues importées, le nombre des lignes importées, et fournit un lien vers un rapport concernant les éventuels problèmes.  
  
 **Arrêter l'actualisation**  
 Cliquez pour arrêter l'opération de traitement. Cette option est utile si l'opération prend trop de temps ou génère trop d'erreurs.  
  
## Voir aussi  
 [Traiter les données &#40;SSAS Tabulaire&#41;](../../analysis-services/tabular-models/process-data-ssas-tabular.md)   
 [Dépanner le traitement des données &#40;SSAS Tabulaire&#41;](../../analysis-services/troubleshoot-process-data-ssas-tabular.md)  
  
  
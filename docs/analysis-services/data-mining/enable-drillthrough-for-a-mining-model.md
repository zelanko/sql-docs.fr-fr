---
title: "Activer l&#39;extraction pour un mod&#232;le d&#39;exploration de donn&#233;es | Microsoft Docs"
ms.custom: ""
ms.date: "03/06/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "analysis-services"
  - "analysis-services/data-mining"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "exploration de données [Analysis Services], rubriques de procédures"
  - "extraction [Analysis Services]"
ms.assetid: 4fa44f60-ef9a-4b59-98c0-c0baf1195c8e
caps.latest.revision: 28
author: "Minewiskan"
ms.author: "owend"
manager: "jhubbard"
caps.handback.revision: 28
---
# Activer l&#39;extraction pour un mod&#232;le d&#39;exploration de donn&#233;es
  Si vous avez activé l'extraction pour un modèle d'exploration de données, lorsque vous parcourez le modèle, vous pouvez extraire des informations détaillées sur les cas utilisés pour créer le modèle. Pour consulter cette information, vous devez disposer des autorisations nécessaires et la structure doit déjà avoir été traitée.  
  
 **Autorisations** Pour qu’un utilisateur extraie les données d’un modèle ou d’une structure, il doit être membre d’un rôle qui a les autorisations [AllowDrillThrough](../../analysis-services/scripting/properties/allowdrillthrough-element-assl.md) pour le modèle ou la structure d’exploration de données. Les autorisations d'extraction sont définies séparément sur la structure et le modèle.  
  
-   Les autorisations d'extraction sur le modèle vous permettent d'extraire à partir du modèle, même si vous n'avez pas d'autorisations sur la structure.  
  
-   Les autorisations d’extraction sur la structure permettent en outre d’inclure des colonnes de structure dans les requêtes d’extraction à partir du modèle, à l’aide de la fonction [StructureColumn &#40;DMX&#41;](../../dmx/structurecolumn-dmx.md). Vous pouvez également interroger les scénarios d’apprentissage et de test dans la structure en utilisant la syntaxe SELECT… FROM \<structure>.CASES.  
  
 **Mise en cache de cas d’apprentissage** L’extraction consiste à récupérer des informations sur les cas d’apprentissage dans la structure d’exploration de données. Ces informations sont mises en cache lorsque la structure est traitée. Par conséquent, si vous choisissez d’effacer toutes les données mises en cache en remplaçant la propriété <xref:Microsoft.AnalysisServices.MiningStructureCacheMode> par **ClearAfterProcessing**, l’extraction ne fonctionne pas.  
  
> [!NOTE]  
>  Si les cas d’apprentissage n’ont pas été mis en cache, vous devez remplacer la propriété <xref:Microsoft.AnalysisServices.MiningStructureCacheMode> par **KeepTrainingCases**, puis retraiter le modèle avant de pouvoir consulter les données de cas.  
  
 Pour plus d’informations, consultez [Requêtes d’extraction &#40;exploration de données&#41;](../../analysis-services/data-mining/drillthrough-queries-data-mining.md).  
  
### Pour activer l'extraction sur un modèle d'exploration de données  
  
1.  Dans [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], sous l’onglet **Modèles d’exploration de données** du Concepteur d’exploration de données, cliquez avec le bouton droit sur le nom du modèle d’exploration de données pour lequel vous voulez activer l’extraction, puis sélectionnez **Propriétés**.  
  
2.  Dans les fenêtres **Propriétés**, cliquez sur **AllowDrillthrough** et sélectionnez **True**.  
  
3.  Sous l’onglet **Modèles d’exploration de données**, cliquez avec le bouton droit sur le modèle et sélectionnez **Traiter le modèle**.  
  
### Pour activer la mise en cache pour une structure d'exploration de données  
  
1.  Dans [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], sous l’onglet **Structure d’exploration de données** du Concepteur d’exploration de données, cliquez avec le bouton droit sur le nom de la structure d’exploration de données.  
  
2.  Ouvrez la fenêtre **Propriétés**.  
  
3.  Dans la fenêtre **Propriétés**, recherchez la propriété **CacheMode**, puis sélectionnez **KeepTrainingCases** dans la liste.  
  
4.  Dans le menu **Base de données**, sélectionnez **Traiter**.  
  
## Voir aussi  
 [Requêtes d’extraction &#40;exploration de données&#41;](../../analysis-services/data-mining/drillthrough-queries-data-mining.md)  
  
  
---
title: Boîte de dialogue de mise à jour incrémentielle (Analysis Services - données multidimensionnelles) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.process.incrementalupdate.f1
ms.assetid: d5a5ae27-44e7-4179-b9e2-efbf21d6c5f5
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 354ec6968698dc5b6a7bbca8ffcd33a34db4389d
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62730338"
---
# <a name="incremental-update-dialog-box-analysis-services---multidimensional-data"></a>Boîte de dialogue Mise à jour incrémentielle (Analysis Services - Données multidimensionnelles)
  Utilisez la boîte de dialogue **Mise à jour incrémentielle** dans [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] et [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] pour définir les paramètres utilisés pendant la mise à jour incrémentielle des groupes de mesures et des partitions. Pour afficher la boîte de dialogue **Mise à jour incrémentielle** , cliquez sur **Configurer** dans la colonne **Paramètres** de la grille **Liste d’objets** dans la boîte de dialogue **Traiter** .  
  
## <a name="options"></a>Options  
  
|Terme|Définition|  
|----------|----------------|  
|**Groupe de mesures**|Sélectionnez le groupe de mesures soumis à la mise à jour incrémentielle.<br /><br /> Remarque : Cette option est activée uniquement si vous sont mise à jour incrémentielle un cube. Si vous appliquez la mise à jour incrémentielle à un groupe de mesures ou à une partition, elle est désactivée.|  
|**Partition**|Sélectionnez la partition à mettre à jour.<br /><br /> Remarque : Cette option est activée uniquement si vous sont mise à jour incrémentielle un cube. Si vous appliquez la mise à jour incrémentielle à un groupe de mesures ou à une partition, elle est désactivée.|  
|**Table**|Met à jour l'objet d'une table.|  
|**Source de données ou une vue**|Sélectionnez la source ou la vue des données dans laquelle se trouve la table source.<br /><br /> Remarque : Cette option est activée uniquement si **Table** est sélectionné.|  
|**Nom et le schéma de table**|Sélectionnez la table source utilisée pour extraire les données pour la mise à jour incrémentielle du cube, du groupe de mesures ou de la partition.<br /><br /> Remarque : Cette option est activée uniquement si **Table** est sélectionné.|  
|**Requête**|Met à jour l'objet d'une requête.|  
|**Source de données**|Sélectionnez la source de données dans laquelle se trouvent les tables soumises à la requête.<br /><br /> Remarque : Cette option est activée uniquement si **requête** est sélectionné.|  
|**Texte de la requête**|Tapez le texte de la requête utilisée pour extraire les données pour la mise à jour incrémentielle du cube, du groupe de mesures ou de la partition.<br /><br /> Remarque : Cette option est activée uniquement si **requête** est sélectionné.|  
  
## <a name="see-also"></a>Voir aussi  
 [Concepteurs et boîtes de dialogue Analysis Services &#40;données multidimensionnelles&#41;](analysis-services-designers-and-dialog-boxes-multidimensional-data.md)   
 [Boîte de dialogue traiter &#40;Analysis Services - données multidimensionnelles&#41;](process-dialog-box-analysis-services-multidimensional-data.md)  
  
  

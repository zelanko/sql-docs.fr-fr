---
title: Boîte de dialogue mise à jour incrémentielle (Analysis Services-données multidimensionnelles) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.process.incrementalupdate.f1
ms.assetid: d5a5ae27-44e7-4179-b9e2-efbf21d6c5f5
author: minewiskan
ms.author: owend
ms.openlocfilehash: 6115a5123fd6e72cee0ebccaac5f539be8aebfbe
ms.sourcegitcommit: f0772f614482e0b3cde3609e178689ce62ca3a19
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84544161"
---
# <a name="incremental-update-dialog-box-analysis-services---multidimensional-data"></a>Boîte de dialogue Mise à jour incrémentielle (Analysis Services - Données multidimensionnelles)
  Utilisez la boîte de dialogue **Mise à jour incrémentielle** dans [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] et [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] pour définir les paramètres utilisés pendant la mise à jour incrémentielle des groupes de mesures et des partitions. Pour afficher la boîte de dialogue **Mise à jour incrémentielle** , cliquez sur **Configurer** dans la colonne **Paramètres** de la grille **Liste d’objets** dans la boîte de dialogue **Traiter** .  
  
## <a name="options"></a>Options  
  
|Terme|Définition|  
|----------|----------------|  
|**Groupe de mesures**|Sélectionnez le groupe de mesures soumis à la mise à jour incrémentielle.<br /><br /> Remarque : cette option est activée uniquement lorsque vous effectuez la mise à jour incrémentielle d’un cube. Si vous appliquez la mise à jour incrémentielle à un groupe de mesures ou à une partition, elle est désactivée.|  
|**Partition**|Sélectionnez la partition à mettre à jour.<br /><br /> Remarque : cette option est activée uniquement lorsque vous effectuez la mise à jour incrémentielle d’un cube. Si vous appliquez la mise à jour incrémentielle à un groupe de mesures ou à une partition, elle est désactivée.|  
|**Table**|Met à jour l'objet d'une table.|  
|**Source de données ou vue**|Sélectionnez la source ou la vue des données dans laquelle se trouve la table source.<br /><br /> Remarque : Cette option est active uniquement si **Table** est sélectionné.|  
|**Schéma et nom de la table**|Sélectionnez la table source utilisée pour extraire les données pour la mise à jour incrémentielle du cube, du groupe de mesures ou de la partition.<br /><br /> Remarque : Cette option est active uniquement si **Table** est sélectionné.|  
|**Requête**|Met à jour l'objet d'une requête.|  
|**Source de données**|Sélectionnez la source de données dans laquelle se trouvent les tables soumises à la requête.<br /><br /> Remarque : Cette option est active uniquement si **Requête** est sélectionné.|  
|**Texte de la requête**|Tapez le texte de la requête utilisée pour extraire les données pour la mise à jour incrémentielle du cube, du groupe de mesures ou de la partition.<br /><br /> Remarque : Cette option est active uniquement si **Requête** est sélectionné.|  
  
## <a name="see-also"></a>Voir aussi  
 [Analysis Services les concepteurs et les boîtes de dialogue &#40;les données multidimensionnelles&#41;](analysis-services-designers-and-dialog-boxes-multidimensional-data.md)   
 [Boîte de dialogue traiter &#40;Analysis Services-données multidimensionnelles&#41;](process-dialog-box-analysis-services-multidimensional-data.md)  
  
  

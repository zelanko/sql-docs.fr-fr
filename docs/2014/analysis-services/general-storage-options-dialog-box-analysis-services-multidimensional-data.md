---
title: Général (boîte de dialogue Options de stockage) (Analysis Services - données multidimensionnelles) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.cubeeditor.partitiondesigner.partitionstoragesettings.setstorageoptions.storage.f1
ms.assetid: ee1fac79-ae15-4c3c-9a98-33db04388817
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 251ecccbd7e28b4f15709d060ead8cbb61309fea
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62731880"
---
# <a name="general-storage-options-dialog-box-analysis-services---multidimensional-data"></a>Général (boîte de dialogue Options de stockage) (Analysis Services - Données multidimensionnelles)
  Utilisez l'onglet **Général** de la boîte de dialogue **Options de stockage** de [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] pour définir le mode de stockage et les paramètres de mise en cache proactive pour une dimension, un cube, un groupe de mesures ou une partition.  
  
> [!NOTE]  
>  Vous devez connaître les concepts de mode de stockage et de mise en cache proactive avant de modifier ces paramètres. Pour plus d’informations, consultez [Mise en cache proactive &#40;partitions&#41;](multidimensional-models-olap-logical-cube-objects/partitions-proactive-caching.md).  
  
## <a name="options"></a>Options  
  
|Terme|Définition|  
|----------|----------------|  
|**Mode de stockage**|Sélectionne le mode de stockage à utiliser pour l'objet.<br /><br /> **MOLAP**<br /> L'objet utilise le mode OLAP multidimensionnel (MOLAP).<br /><br /> **HOLAP**<br /> L'objet utilise le mode OLAP hybride (HOLAP).<br /><br /> **ROLAP**<br /> L'objet utilise le mode OLAP relationnel (ROLAP).|  
|**Activer la mise en cache proactive**|Active la mise en cache proactive.<br /><br /> Remarque : Si cette option n’est pas sélectionnée, toutes les options sauf **mode de stockage** sont désactivés.|  
|**Mettre à jour le cache lors de la modification des données**|Utilise la méthode de notification sélectionnée dans l'onglet **Notifications** pour mettre à jour l'image MOLAP de l'objet lorsqu'une notification est reçue. Pour plus d’informations sur l’onglet **Notifications** , consultez [Notifications &#40;Storage Options Dialog Box&#41; &#40;Analysis Services - Multidimensional Data&#41;](notifications-storage-options-dialog-analysis-services-multidimensional-data.md).<br /><br /> Remarque : Cette option est désactivée, sauf si **activer la mise en cache proactive** est sélectionné.|  
|**Intervalle de latence**|Définit les unités de temps et l'intervalle minimal pendant lequel l'objet est inactif avant que la mise en cache proactive commence à créer la nouvelle image MOLAP de l'objet.<br /><br /> Remarque : Cette option est désactivée, sauf si **mettre à jour le cache lorsque les données changent** est sélectionné.|  
|**Intervalle de latence**|Définit les unités de temps et l'intervalle maximal pendant lequel, après réception d'une notification pour l'objet, la mise en cache proactive commence à créer une nouvelle image MOLAP de l'objet, quelle que soit l'activité actuelle de l'objet. Les notifications reçues lorsque cet intervalle est écoulé n'annulent pas la création de l'image MOLAP déclenchée pendant l'intervalle.<br /><br /> Remarque : Cette option est désactivée, sauf si **mettre à jour le cache lorsque les données changent** est sélectionné. Notez également que cette option ne doit pas être définie si **mode de stockage** a la valeur **HOLAP**.|  
|**Supprimer le cache obsolète**|Spécifie la durée entre le début de la création d'une mémoire cache MOLAP et la suppression de la mémoire cache MOLAP existante.<br /><br /> Remarque : Cette option est désactivée, sauf si **activer la mise en cache proactive** est sélectionné. Notez également que cette option ne doit pas être définie si **mode de stockage** a la valeur HOLAP.|  
|**Latence**|Sélectionne les unités et l'intervalle de temps entre le début de la création d'une mémoire cache MOLAP et la suppression de la mémoire cache MOLAP existante.<br /><br /> Remarque : Cette option est désactivée, sauf si **supprimer le cache obsolète** est sélectionné. Notez également que cette option ne doit pas être définie si **mode de stockage** a la valeur **HOLAP**.|  
|**Mise à jour régulièrement le cache**|Met régulièrement à jour l'image MOLAP, quelle que soit la notification.<br /><br /> Remarque : Cette option est désactivée, sauf si **activer la mise en cache proactive** est sélectionné. Notez également que cette option ne doit pas être définie si **mode de stockage** a la valeur **HOLAP**.|  
|**L’intervalle de reconstruction**|Sélectionne les unités et l'intervalle de temps où, après la création d'une image MOLAP, [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] recommence le processus de l'image MOLAP de l'objet, quelle que soit la notification. Les notifications reçues lorsque cet intervalle est écoulé n'annulent pas la création de l'image MOLAP déclenchée pendant l'intervalle.<br /><br /> Remarque : Cette option est désactivée, sauf si **mettre à jour le cache périodiquement** est sélectionné. Notez également que cette option ne doit pas être définie si **mode de stockage** a la valeur **HOLAP**.|  
|**Mettre en ligne immédiatement**|Place immédiatement les objets en ligne. Si cette option est activée, les objets utilisent le stockage ROLAP sous-jacent pour résoudre les requêtes pendant la reconstruction de la mémoire cache MOLAP. Si elle n'est pas activée, les objets sont mis en ligne uniquement après que la mémoire cache MOLAP pour l'objet ne soit terminée.|  
|**Activer les agrégations ROLAP**|Utilise des vues matérialisées sur la source de données sous-jacente pour stocker des agrégations.<br /><br /> Remarque : Si la source de données sous-jacente ne prend pas en charge les vues matérialisées, une erreur se produit lors du traitement de l’objet.|  
|**Appliquer les paramètres aux dimensions**|Applique les paramètres de mode de stockage et de mise en mémoire cache proactive aux dimensions associées.|  
  
## <a name="see-also"></a>Voir aussi  
 [Boîte de dialogue Options de stockage &#40;Analysis Services - données multidimensionnelles&#41;](storage-options-dialog-box-analysis-services-multidimensional-data.md)   
 [Notifications &#40;boîte de dialogue Options de stockage&#41; &#40;Analysis Services - données multidimensionnelles&#41;](notifications-storage-options-dialog-analysis-services-multidimensional-data.md)  
  
  

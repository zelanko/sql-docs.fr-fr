---
title: Général (boîte de dialogue Options de stockage) (Analysis Services-données multidimensionnelles) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.cubeeditor.partitiondesigner.partitionstoragesettings.setstorageoptions.storage.f1
ms.assetid: ee1fac79-ae15-4c3c-9a98-33db04388817
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 3c7ddd5311232ae12b3eb9f66adc0cd1f5714b32
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "66081008"
---
# <a name="general-storage-options-dialog-box-analysis-services---multidimensional-data"></a>Général (boîte de dialogue Options de stockage) (Analysis Services - Données multidimensionnelles)
  Utilisez l'onglet **Général** de la boîte de dialogue **Options de stockage** de [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] pour définir le mode de stockage et les paramètres de mise en cache proactive pour une dimension, un cube, un groupe de mesures ou une partition.  
  
> [!NOTE]  
>  Vous devez connaître les concepts de mode de stockage et de mise en cache proactive avant de modifier ces paramètres. Pour plus d’informations, consultez [Mise en cache proactive &#40;partitions&#41;](multidimensional-models-olap-logical-cube-objects/partitions-proactive-caching.md).  
  
## <a name="options"></a>Options  
  
|Terme|Définition|  
|----------|----------------|  
|**Mode de stockage**|Sélectionne le mode de stockage à utiliser pour l'objet.<br /><br /> **MOLAP**<br /> L'objet utilise le mode OLAP multidimensionnel (MOLAP).<br /><br /> **HOLAP**<br /> L'objet utilise le mode OLAP hybride (HOLAP).<br /><br /> **ROLAP**<br /> L'objet utilise le mode OLAP relationnel (ROLAP).|  
|**Activer la mise en cache proactive**|Active la mise en cache proactive.<br /><br /> Remarque : si cette option n’est pas sélectionnée, toutes les options sont désactivées à l’exception de **Mode de stockage**.|  
|**Mettre à jour le cache en cas de modification des données**|Utilise la méthode de notification sélectionnée dans l'onglet **Notifications** pour mettre à jour l'image MOLAP de l'objet lorsqu'une notification est reçue. Pour plus d’informations sur l’onglet **Notifications** , consultez [Notifications &#40;Storage Options Dialog Box&#41; &#40;Analysis Services - Multidimensional Data&#41;](notifications-storage-options-dialog-analysis-services-multidimensional-data.md).<br /><br /> Remarque : cette option est désactivée, sauf si l’option **Activer la mise en cache proactive** est sélectionnée.|  
|**Intervalle de latence**|Définit les unités de temps et l'intervalle minimal pendant lequel l'objet est inactif avant que la mise en cache proactive commence à créer la nouvelle image MOLAP de l'objet.<br /><br /> Remarque : cette option est désactivée, sauf si l’option **Mettre à jour le cache en cas de modification des données** est sélectionnée.|  
|**Valeur de remplacement de l'intervalle de latence**|Définit les unités de temps et l'intervalle maximal pendant lequel, après réception d'une notification pour l'objet, la mise en cache proactive commence à créer une nouvelle image MOLAP de l'objet, quelle que soit l'activité actuelle de l'objet. Les notifications reçues lorsque cet intervalle est écoulé n'annulent pas la création de l'image MOLAP déclenchée pendant l'intervalle.<br /><br /> Remarque : cette option est désactivée, sauf si l’option **Mettre à jour le cache en cas de modification des données** est sélectionnée. Notez également que cette option ne doit pas être définie si le **mode de stockage** est défini sur **HOLAP**.|  
|**Supprimer le cache obsolète**|Spécifie la durée entre le début de la création d'une mémoire cache MOLAP et la suppression de la mémoire cache MOLAP existante.<br /><br /> Remarque : cette option est désactivée, sauf si l’option **Activer la mise en cache proactive** est sélectionnée. Notez également que cette option ne doit pas être définie si le **mode de stockage** est défini sur HOLAP.|  
|**Latence**|Sélectionne les unités et l'intervalle de temps entre le début de la création d'une mémoire cache MOLAP et la suppression de la mémoire cache MOLAP existante.<br /><br /> Remarque : cette option est désactivée, sauf si l’option **Supprimer le cache obsolète** est sélectionnée. Notez également que cette option ne doit pas être définie si le **mode de stockage** est défini sur **HOLAP**.|  
|**Mettre à jour régulièrement le cache**|Met régulièrement à jour l'image MOLAP, quelle que soit la notification.<br /><br /> Remarque : cette option est désactivée, sauf si l’option **Activer la mise en cache proactive** est sélectionnée. Notez également que cette option ne doit pas être définie si le **mode de stockage** est défini sur **HOLAP**.|  
|**Intervalle de reconstruction**|Sélectionne l’intervalle et les unités de temps pour la période qui, après la création d’une nouvelle image [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] MOLAP, redémarre le processus d’image MOLAP pour l’objet, quelle que soit la notification. Les notifications reçues lorsque cet intervalle est écoulé n'annulent pas la création de l'image MOLAP déclenchée pendant l'intervalle.<br /><br /> Remarque : cette option est désactivée, sauf si l’option **Mettre à jour régulièrement le cache** est sélectionnée. Notez également que cette option ne doit pas être définie si le **mode de stockage** est défini sur **HOLAP**.|  
|**Mettre en ligne immédiatement**|Place immédiatement les objets en ligne. Si cette option est activée, les objets utilisent le stockage ROLAP sous-jacent pour résoudre les requêtes pendant la reconstruction de la mémoire cache MOLAP. Si elle n'est pas activée, les objets sont mis en ligne uniquement après que la mémoire cache MOLAP pour l'objet ne soit terminée.|  
|**Activer les agrégations ROLAP**|Utilise des vues matérialisées sur la source de données sous-jacente pour stocker des agrégations.<br /><br /> Remarque : si la source de données sous-jacente ne prend pas en charge les vues matérialisées, une erreur se produit lors du traitement de l’objet.|  
|**Appliquer les paramètres aux dimensions**|Applique les paramètres de mode de stockage et de mise en mémoire cache proactive aux dimensions associées.|  
  
## <a name="see-also"></a>Voir aussi  
 [Boîte de dialogue Options de stockage &#40;Analysis Services-données multidimensionnelles&#41;](storage-options-dialog-box-analysis-services-multidimensional-data.md)   
 [Boîte de dialogue Options de stockage des &#40;de notification&#41; &#40;Analysis Services-données multidimensionnelles&#41;](notifications-storage-options-dialog-analysis-services-multidimensional-data.md)  
  
  

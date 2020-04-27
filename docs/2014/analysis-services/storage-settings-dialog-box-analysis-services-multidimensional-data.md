---
title: Boîte de dialogue Paramètres de stockage (Analysis Services-données multidimensionnelles) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.cubeeditor.partitiondesigner.partitionstoragesettings.f1
- sql12.asvs.cubeeditor.cubebuilder.measuregroupstoragesettings.f1
ms.assetid: 80c41c71-226c-45fe-b9cf-af824b592fe1
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: ecd796d2fb2bc37c4c2ad6d9fac00ef4258ec038
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/26/2020
ms.locfileid: "66068026"
---
# <a name="storage-settings-dialog-box-analysis-services---multidimensional-data"></a>Boîte de dialogue Paramètres de stockage (Analysis Services - Données multidimensionnelles)
  Utilisez la boîte de dialogue **Paramètres de stockage** dans [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] pour définir les paramètres de mise en cache proactive, de stockage et de notification d'une dimension, d'un cube, d'un groupe de mesures ou d'une partition. Vous pouvez afficher la boîte de dialogue **Paramètres de stockage** dans [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] en :  
  
-   Cliquez sur le bouton de sélection (**...**) `ProactiveCaching` pour la valeur de propriété d’une dimension, d’un cube, d’un groupe de mesures [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]ou d’une partition dans la fenêtre **Propriétés** de.  
  
-   développant un groupe de mesures dans l'onglet **Partitions** du **Concepteur de cube** et en cliquant sur **Paramètres de stockage** ;  
  
-   développant un groupe de mesures et en sélectionnant une partition dans la grille du groupe de mesures dans l'onglet **Partitions** du **Concepteur de cube** et en cliquant sur **Paramètres de stockage** ;  
  
-   développant un groupe de mesures et en sélectionnant une partition dans la grille du groupe de mesures dans l'onglet **Partitions** du **Concepteur de cube** et en cliquant sur **Paramètres de stockage** dans le volet **Barre d'outils** de l'onglet **Partitions** du **Concepteur de cube**.  
  
## <a name="options"></a>Options  
  
|Terme|Définition|Valeurs|  
|----------|----------------|------------|  
|**Paramètre standard**|Active le curseur **Paramètre standard** et utilise les paramètres prédéfinis pour le mode de stockage et la mise en cache proactive.||  
|**Paramètre standard**|Définissez l'un des paramètres prédéfinis suivants :<br /><br /> **ROLAP en temps réel**<br /><br /> Sélectionnez cette option pour utiliser les paramètres suivants de stockage et de mise en cache proactive :|Mode de stockage ROLAP<br /><br /> Active la mise en cache proactive<br /><br /> Supprime le cache obsolète avec une latence de 0 seconde<br /><br /> Met l'objet en ligne immédiatement|  
||**HOLAP en temps réel**<br /><br /> Sélectionnez cette option pour utiliser les paramètres suivants de stockage et de mise en cache proactive :|Mode de stockage HOLAP<br /><br /> Active la mise en cache proactive<br /><br /> Supprime le cache obsolète avec une latence de 0 seconde<br /><br /> Met à jour le cache lorsque les données changent avec une fréquence de 0 seconde et aucune fréquence de remplacement<br /><br /> Met l'objet en ligne immédiatement|  
||**MOLAP à faible latence**<br /><br /> Sélectionnez cette option pour utiliser les paramètres suivants de stockage et de mise en cache proactive :|Mode de stockage MOLAP<br /><br /> Active la mise en cache proactive<br /><br /> Supprime le cache obsolète avec une latence de 30 minutes<br /><br /> Met à jour le cache lorsque les données changent avec une fréquence de 10 secondes et une fréquence de remplacement de 10 minutes<br /><br /> Met l'objet en ligne immédiatement|  
||**MOLAP à latence moyenne**<br /><br /> Sélectionnez cette option pour utiliser les paramètres suivants de stockage et de mise en cache proactive :|Mode de stockage MOLAP<br /><br /> Active la mise en cache proactive<br /><br /> Supprime le cache obsolète avec une latence de 4 heures<br /><br /> Met à jour le cache lorsque les données changent avec une fréquence de 10 secondes et une fréquence de remplacement de 10 minutes<br /><br /> Met l'objet en ligne immédiatement|  
||**MOLAP automatique**<br /><br /> Sélectionnez cette option pour utiliser les paramètres suivants de stockage et de mise en cache proactive :|Mode de stockage MOLAP<br /><br /> Active la mise en cache proactive<br /><br /> Met à jour le cache lorsque les données changent avec une fréquence de 0 seconde et aucune fréquence de remplacement|  
||**MOLAP planifié**<br /><br /> Sélectionnez cette option pour utiliser les paramètres suivants de stockage et de mise en cache proactive :|Mode de stockage MOLAP<br /><br /> Activer la mise en cache proactive<br /><br /> Met périodiquement à jour la mémoire cache avec un intervalle de reconstruction égal à 1 jour|  
||**MOLAP**<br /><br /> Sélectionnez cette option pour utiliser les paramètres suivants de stockage et de mise en cache proactive :|Mode de stockage MOLAP|  
|**Paramètre personnalisé**|Sélectionnez cette option pour définir explicitement les options du mode de stockage, de mise en cache proactive et de notification.||  
|**Options**|Affiche la boîte de dialogue **Options de stockage** qui permet de définir explicitement les options du mode de stockage, de la mise en cache proactive et de notification. Pour plus d’informations sur la boîte de dialogue **Options de stockage**, consultez [Boîte de dialogue Options de stockage &#40;Analysis Services - Données multidimensionnelles&#41;](storage-options-dialog-box-analysis-services-multidimensional-data.md).||  
  
## <a name="see-also"></a>Voir aussi  
 [Analysis Services les concepteurs et les boîtes de dialogue &#40;les données multidimensionnelles&#41;](analysis-services-designers-and-dialog-boxes-multidimensional-data.md)   
 [Mise en cache proactive &#40;les partitions&#41;](multidimensional-models-olap-logical-cube-objects/partitions-proactive-caching.md)   
 [Stockage cube &#40;Analysis Services-données multidimensionnelles&#41;](multidimensional-models-olap-logical-cube-objects/cube-storage-analysis-services-multidimensional-data.md)  
  
  

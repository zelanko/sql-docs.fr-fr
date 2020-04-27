---
title: Notifications (boîte de dialogue Options de stockage) (Analysis Services-données multidimensionnelles) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.cubeeditor.partitiondesigner.partitionstoragesettings.setstorageoptions.notifications.f1
ms.assetid: 5675cdbf-bfaa-4b6e-b716-31b8e9da72b4
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 23845118c4c202db781fe325c4afc2402ceee271
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/26/2020
ms.locfileid: "66072201"
---
# <a name="notifications-storage-options-dialog-box-analysis-services---multidimensional-data"></a>Notifications (boîte de dialogue Options de stockage) (Analysis Services - Données multidimensionnelles)
  Utilisez l'onglet **Notifications** de la boîte de dialogue **Options de stockage** dans [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] pour définir la méthode de notification et les paramètres associés d'une dimension, d'un cube, d'un groupe de mesures ou d'une partition.  
  
> [!NOTE]  
>  Vous devez connaître les concepts de mode de stockage et de mise en cache proactive avant de modifier ces paramètres. Pour plus d’informations, consultez [Mise en cache proactive &#40;partitions&#41;](multidimensional-models-olap-logical-cube-objects/partitions-proactive-caching.md).  
  
## <a name="options"></a>Options  
  
|Terme|Définition|  
|----------|----------------|  
|**Mode de stockage**|Sélectionne le mode de stockage à utiliser pour l'objet.<br /><br /> **MOLAP**<br /> L'objet utilise le mode OLAP multidimensionnel (MOLAP).<br /><br /> **HOLAP**<br /> L'objet utilise le mode OLAP hybride (HOLAP).<br /><br /> **ROLAP**<br /> L'objet utilise le mode OLAP relationnel (ROLAP).|  
|**Activer la mise en cache proactive**|Active la mise en cache proactive.<br /><br /> Remarque : si cette option n’est pas sélectionnée, toutes les options sont désactivées à l’exception de **Mode de stockage**.|  
|**SQL Server**|Utilise un mécanisme de trace spécialisé [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] sur pour identifier les modifications apportées aux tables sous-jacentes de l’objet.|  
|**Spécifier les tables de suivi**|Définissez les tables sous-jacentes à suivre de l’objet, puis tapez la liste des tables délimitées par un point-virgule (;), ou cliquez sur le bouton avec des points de suspension (**...**) pour ouvrir la boîte de dialogue **Objets relationnels** et choisissez les tables à suivre. Pour plus d’informations, consultez [Boîte de dialogue Objets relationnels &#40;Analysis Services - Données multidimensionnelles&#41;](relational-objects-dialog-box-analysis-services-multidimensional-data.md).<br /><br /> Si vous ne sélectionnez pas cette option, [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] tente de déterminer les tables sous-jacentes à suivre de l'objet, si certaines conditions sont remplies. Pour plus d’informations sur ces conditions requises, consultez [Mise en cache proactive &#40;partitions&#41;](multidimensional-models-olap-logical-cube-objects/partitions-proactive-caching.md).|  
|**Client initié**|Sélectionnez la commande XML for Analysis (XMLA), `NotifyTableChange` pour identifier les modifications apportées aux tables sous-jacentes de l'objet. Cette option est généralement utilisée si vous envisagez d'utiliser un processus de notification client.|  
|**Spécifier les tables de suivi**|Sélectionnez cette option pour définir les tables sous-jacentes à suivre de l’objet, puis tapez la liste des tables délimitées par un point-virgule (;) ou cliquez sur le bouton avec des points de suspension (**...**) pour ouvrir la boîte de dialogue **Objets relationnels** et choisissez les tables à suivre. Pour plus d’informations, consultez [Boîte de dialogue Objets relationnels &#40;Analysis Services - Données multidimensionnelles&#41;](relational-objects-dialog-box-analysis-services-multidimensional-data.md).<br /><br /> Si vous ne sélectionnez pas cette option, [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] tente de déterminer les tables sous-jacentes à suivre de l'objet, si certaines conditions sont remplies. Pour plus d’informations sur ces conditions requises, consultez [Mise en cache proactive &#40;partitions&#41;](multidimensional-models-olap-logical-cube-objects/partitions-proactive-caching.md).|  
|**Interrogation planifiée**|Utilise un mécanisme d'interrogation pour identifier les modifications en exécutant une série de requêtes sur les tables sous-jacentes de l'objet.|  
|**Fréquence d’interrogation**|Définit la fréquence et l'unité de temps du délai qui doit s'écouler avant que [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] exécute les requêtes d'interrogation et les requêtes de traitement définies dans la grille d'interrogation.|  
|**Activer les mises à jour incrémentielles**|Met à jour de manière incrémentielle le cache MOLAP d'un objet en fonction du groupe de requêtes d'interrogation et de traitement définies pour identifier uniquement des données supplémentaires. Si vous sélectionnez cette option, la requête d'interrogation est associée à un identificateur de table dans la vue de source de données. La requête de traitement est utilisée ensuite pour comparer la valeur actuelle de la requête d'interrogation à la valeur stockée de la requête d'interrogation exécutée précédemment pour identifier les modifications.<br /><br /> Si vous ne sélectionnez pas cette option, le cache MOLAP est complètement mis à jour. La requête d'interrogation est utilisée pour identifier l'occurrence d'une modification, et aucune requête de traitement ou aucun identificateur de table n'est nécessaire.|  
|**Grille d'interrogation**|Contient les requêtes d'interrogation, les requêtes de traitement et les identificateurs de tables qu'utilise [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] pour interroger la source de données et identifier les modifications dans les tables sous-jacentes de l'objet. Cette grille comporte les colonnes suivantes :<br /><br /> **Requête d’interrogation**: tapez la requête singleton exécutée à la fréquence d’interrogation pour identifier les modifications de l’objet, ou cliquez sur le bouton de sélection (**...**) pour ouvrir la boîte de dialogue **créer une requête d’interrogation** et définir la requête singleton. Pour plus d’informations, consultez [Boîte de dialogue Créer la requête d’interrogation &#40;Analysis Services - Données multidimensionnelles&#41;](create-polling-query-dialog-box-analysis-services-multidimensional-data.md). Si vous avez sélectionné **Activer les mises à jour incrémentielles** , la requête d'interrogation doit retourner une valeur qui identifie le dernier enregistrement ajouté dans la table définie dans **Table**. Si vous n'avez pas sélectionné **Activer les mises à jour incrémentielles** , la requête d'interrogation doit retourner une valeur qui identifie le nombre d'enregistrements actuels dans la table.<br /><br /> **Traitement**de la requête : tapez la requête exécutée à la fréquence d’interrogation pour extraire les nouveaux enregistrements de la table identifiée dans la **table**, ou cliquez sur le bouton de sélection (**...**) pour ouvrir la boîte de dialogue **créer la requête de traitement** et définir la requête. Pour plus d’informations, consultez [Boîte de dialogue Créer la requête de traitement &#40;Analysis Services - Données multidimensionnelles&#41;](create-processing-query-dialog-box-analysis-services-multidimensional-data.md). La requête doit être paramétrable pour accepter deux paramètres : la valeur précédente retournée par la requête dans la **requête d’interrogation** et la valeur actuelle retournée par la requête dans la requête d' **interrogation**, qui peut être utilisée pour identifier et extraire uniquement les enregistrements qui ont été ajoutés au cours de la période d’interrogation. Notez que cette option n’est activée que si **Activer les mises à jour incrémentielles** est sélectionné.<br /><br /> **Table**: tapez l’identificateur de la table par rapport à laquelle la requête de la **requête d’interrogation** suit le dernier enregistrement, ou cliquez sur le bouton de sélection (**...**) pour ouvrir la boîte de dialogue **Rechercher une table** et sélectionner la table. Pour plus d’informations, consultez [Boîte de dialogue Rechercher une table &#40;Analysis Services - Données multidimensionnelles&#41;](find-table-dialog-box-analysis-services-multidimensional-data.md).|  
  
## <a name="see-also"></a>Voir aussi  
 [Boîte de dialogue Options de stockage &#40;Analysis Services-données multidimensionnelles&#41;](storage-options-dialog-box-analysis-services-multidimensional-data.md)  
  
  

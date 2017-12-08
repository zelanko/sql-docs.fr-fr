---
title: "Langage de script (TMSL) de modèle de commandes sous forme de tableau | Documents Microsoft"
ms.date: 05/30/2017
ms.prod: sql-non-specified
ms.prod_service: analysis-services
ms.service: 
ms.component: tabular-models
ms.reviewer: 
ms.suite: sql
ms.custom: 
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 4eb07192-6f53-4426-830a-d63a945dbcab
caps.latest.revision: "12"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 71b44ae1e5f8e5db2859bb4d3b2457c752de4dc6
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/17/2017
---
# <a name="tmsl-reference---commands"></a>Référence TMSL - commandes

[!INCLUDE[ssas-appliesto-sql2016-later-aas](../../includes/ssas-appliesto-sql2016-later-aas.md)]

  Vous pouvez exécuter des commandes sur un point de terminaison XMLA, formuler des définitions d’objet dans JSON à l’aide de l’écriture de scripts langage TMSL (Tabular Model), par rapport aux bases de données model tabulaire.   Consultez [définitions d’objets dans le tableau de modèle un langage de script &#40; TMSL &#41; ](../../analysis-services/tabular-models-scripting-language-objects/tmsl-reference-tabular-objects.md) pour obtenir la liste des objets utilisés avec les commandes suivantes.  
  
## <a name="object-operations"></a>Opérations de l’objet  
  
|||  
|-|-|  
|[Modifier la commande &#40; TMSL &#41;](../../analysis-services/tabular-models-scripting-language-commands/alter-command-tmsl.md)|Apportez les modifications d’inline à un objet sans avoir à spécifier la définition complète.|  
|[Créer une commande &#40; TMSL &#41;](../../analysis-services/tabular-models-scripting-language-commands/create-command-tmsl.md)|Crée un objet, y compris ses descendants.|  
|[La commande CreateOrReplace &#40; TMSL &#41;](../../analysis-services/tabular-models-scripting-language-commands/createorreplace-command-tmsl.md)|Créer ou remplacer des parties d’une définition d’objet. La définition complète doit être fournie.|  
|[Supprimer la commande &#40; TMSL &#41;](../../analysis-services/tabular-models-scripting-language-commands/delete-command-tmsl.md)|Supprimer un objet, y compris ses descendants.|  
  
## <a name="data-refresh-operations"></a>Opérations d’actualisation des données  
  
|||  
|-|-|  
|[Commande MergePartitions &#40; TMSL &#41;](../../analysis-services/tabular-models-scripting-language-commands/mergepartitions-command-tmsl.md)|Fusionner une partition cible dans une source et de suppression de la cible.|  
|[Actualiser les commandes &#40; TMSL &#41;](../../analysis-services/tabular-models-scripting-language-commands/refresh-command-tmsl.md)|Traiter une base de données, une table ou une partition.|  
  
## <a name="scripting"></a>Création de scripts  
  
|||  
|-|-|  
|[La commande Sequence &#40; TMSL &#41;](../../analysis-services/tabular-models-scripting-language-commands/sequence-command-tmsl.md)|Opérations du lot dans l’ordre ou en parallèle|  
  
## <a name="database-management-operations"></a>Opérations de gestion de base de données  
  
|||  
|-|-|  
|[Attacher une commande &#40; TMSL &#41;](../../analysis-services/tabular-models-scripting-language-commands/attach-command-tmsl.md)|Ajoute un fichier sur le serveur.|  
|[Détacher la commande &#40; TMSL &#41;](../../analysis-services/tabular-models-scripting-language-commands/detach-command-tmsl.md)|Supprime un fichier à partir des serveurs.|  
|[Commande de sauvegarde &#40; TMSL &#41;](../../analysis-services/tabular-models-scripting-language-commands/backup-command-tmsl.md)|Crée un fichier de sauvegarde de base de données.|  
|[Restaurer des commandes &#40; TMSL &#41;](../../analysis-services/tabular-models-scripting-language-commands/restore-command-tmsl.md)|Restaure la base de données sur le serveur.|  
|[Synchroniser les commandes &#40; TMSL &#41;](../../analysis-services/tabular-models-scripting-language-commands/synchronize-command-tmsl.md)|Synchronise une base de données Analysis Services avec une autre base de données existante.|  
  
## <a name="see-also"></a>Voir aussi  
 [Tabular Model Scripting Language &#40;TMSL&#41; Reference [Informations de référence sur TMSL &#40;Tabular Model Scripting Language&#41;]](../../analysis-services/tabular-model-scripting-language-tmsl-reference.md)   
 [Installer les fournisseurs de données Analysis Services &#40; AMO, ADOMD.NET, MSOLAP &#41;](../../analysis-services/instances/install-windows/install-analysis-services-data-providers-amo-adomd-net-msolap.md)   
 [Niveau de compatibilité pour les modèles tabulaires dans Analysis Services](../../analysis-services/tabular-models/compatibility-level-for-tabular-models-in-analysis-services.md)  
  
  

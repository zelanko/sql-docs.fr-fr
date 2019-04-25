---
title: Créer et gérer des Partitions dans la base de données d’espace de travail (SSAS tabulaire) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.bidtoolset.partitionmgr.f1
ms.assetid: 0b3027d6-652b-4eb3-a197-58b25df65218
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: dd519c9cafb1358f21af30d2c9ea0522e47768b7
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62757475"
---
# <a name="create-and-manage-partitions-in-the-workspace-database-ssas-tabular"></a>Créer et gérer des partitions dans la base de données de l'espace de travail (SSAS Tabulaire)
  Les partitions divisent une table en sections logiques. Chaque partition peut ensuite être traitée (actualisée) indépendamment ou parallèlement à d'autres partitions. Les partitions peuvent améliorer l'évolutivité et la gestion de bases de données volumineuses. Par défaut, chaque table possède une partition qui inclut toutes les colonnes. Les tâches de cette rubrique décrivent comment créer et gérer des partitions dans la base de données model de l’espace de travail à l’aide de la boîte de dialogue **Gestionnaire de partition** dans [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)]  
  
 Une fois que le modèle a été déployé sur une autre instance Analysis Services, les administrateurs de bases de données peuvent créer et gérer des partitions dans le modèle (déployé) à l'aide de [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]. Pour plus d’informations, consultez [Créer et gérer des partitions de modèles tabulaires &#40;SSAS Tabulaire&#41;](partitions-ssas-tabular.md).  
  
 Cette rubrique inclut les tâches suivantes :  
  
-   [Pour créer une nouvelle partition](#bkmk_create_new)  
  
-   [Pour copier une partition](#bkmk_copy)  
  
-   [Pour supprimer une partition](#bkmk_delete)  
  
> [!NOTE]  
>  Vous ne pouvez pas fusionner des partitions dans la base de données model de l'espace de travail à l'aide de la boîte de dialogue Gestionnaire de partitions. Les partitions peuvent être fusionnées dans un modèle déployé uniquement à l'aide de [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].  
  
## <a name="tasks"></a>Tâches  
 Pour créer et gérer des partitions, vous allez utiliser la boîte de dialogue **Gestionnaire de partition** . Pour consulter la boîte de dialogue **Gestionnaire de partition** , dans [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)], cliquez sur le menu **Table** , puis sur **Partitions**.  
  
###  <a name="bkmk_create_new"></a> Pour créer une nouvelle partition  
  
1.  Dans le générateur de modèles, sélectionnez la table pour laquelle vous souhaitez définir une partition.  
  
2.  Cliquez sur le menu **Table** , puis sur **Partitions**.  
  
3.  Dans **Gestionnaire de partition**, dans la zone de liste **Table** , vérifiez ou sélectionnez la table que vous voulez partitionner, puis cliquez sur **Nouveau**.  
  
4.  Dans **Nom de la partition**, tapez un nom pour la partition. Par défaut, le nom de la partition par défaut est numéroté de manière incrémentielle pour chaque nouvelle partition.  
  
5.  Vous pouvez sélectionner les lignes et les colonnes à inclure dans la partition à l'aide du mode Aperçu de la table ou d'une requête SQL créée avec le mode Éditeur de requête.  
  
     Pour utiliser le mode Aperçu de la table (valeur par défaut), cliquez sur le bouton **Aperçu de la table** en haut à droite dans la fenêtre d’aperçu. Sélectionnez les colonnes à inclure dans la partition en activant la case à cocher en regard du nom de la colonne. Pour filtrer des lignes, cliquez avec le bouton droit sur une valeur de cellule, puis cliquez sur **Filtrer par valeur de la cellule sélectionnée**.  
  
     Pour utiliser une instruction SQL, cliquez sur le bouton **Éditeur de requête** en haut à droite dans la fenêtre d’aperçu, puis tapez ou collez une instruction de requête SQL dans la fenêtre de requête. Pour valider votre instruction, cliquez sur **Valider**. Pour utiliser le concepteur de requêtes, cliquez sur **Conception**.  
  
###  <a name="bkmk_copy"></a> Pour copier une partition  
  
1.  Dans **Gestionnaire de partition**, dans la zone de liste **Table** , vérifiez ou sélectionnez la table qui contient la partition que vous souhaitez copier.  
  
2.  Dans la liste **Partitions** , sélectionnez la partition à copier, puis cliquez sur **Copier**.  
  
3.  Dans **Nom de la partition**, tapez un nouveau nom pour la partition.  
  
###  <a name="bkmk_delete"></a> Pour supprimer une partition  
  
1.  Dans **Gestionnaire de partition**, dans la zone de liste **Table** , vérifiez ou sélectionnez la table qui contient la partition à supprimer.  
  
2.  Dans la liste **Partitions** , sélectionnez la partition à supprimer, puis cliquez sur **Supprimer**.  
  
## <a name="see-also"></a>Voir aussi  
 [Partitions &#40;SSAS Tabulaire&#41;](partitions-ssas-tabular.md)   
 [Traiter les Partitions dans la base de données de l’espace de travail &#40;SSAS tabulaire&#41;](process-partitions-in-the-workspace-database-ssas-tabular.md)  
  
  

---
title: "Supprimer des colonnes dans une Structure d’exploration de données | Documents Microsoft"
ms.custom: 
ms.date: 03/13/2017
ms.prod: sql-non-specified
ms.prod_service: analysis-services
ms.service: 
ms.component: data-mining
ms.reviewer: 
ms.suite: sql
ms.technology:
- analysis-services
- analysis-services/data-mining
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- mining structures [Analysis Services], columns
- removing columns
- deleting columns
- columns [data mining], mining structure columns
ms.assetid: 41073ffe-9351-416b-9f0c-62634bc213f9
caps.latest.revision: "27"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: d7dc82033994b08f45283bf03bcae11d441c1b60
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/17/2017
---
# <a name="remove-columns-from-a-mining-structure"></a>Supprimer des colonnes d'une structure d'exploration de données
  Vous pouvez utiliser le Concepteur d'exploration de données pour supprimer des colonnes d'une structure d'exploration de données après que la structure a été créée. Les raisons de la suppression d'une colonne de structure d'exploration de données peuvent inclure les suivantes :  
  
-   La structure d'exploration de données contient plusieurs copies d'une colonne et vous souhaitez éviter l'utilisation de données en double dans un modèle.  
  
-   Les données doivent être protégées, mais l'extraction a été activée.  
  
-   Les données ne sont pas utilisées dans la modélisation et ne doivent pas être traitées.  
  
 La suppression d'une colonne de la structure d'exploration de données ne modifie pas la colonne de la vue de source de données ou dans les données externes ; seules les métadonnées sont supprimées. Toutefois, lorsque vous modifiez les colonnes utilisées dans une structure d'exploration de données, vous devez retraiter la structure et tous les modèles basés sur celle-ci.  
  
### <a name="to-remove-a-column-from-the-mining-structure"></a>Pour supprimer une colonne d'une structure d'exploration de données  
  
1.  Sélectionnez l’onglet **Structure d’exploration de données** dans le Concepteur d’exploration de données.  
  
2.  Développez l'arborescence de la structure d'exploration de données pour afficher toutes les colonnes.  
  
3.  Cliquez avec le bouton droit sur la colonne à supprimer, puis sélectionnez **Supprimer**.  
  
4.  Dans la boîte de dialogue **Supprimer les objets** , cliquez sur **OK**.  
  
## <a name="see-also"></a>Voir aussi  
 [Tâches de la structure d'exploration de données et procédures](../../analysis-services/data-mining/mining-structure-tasks-and-how-tos.md)  
  
  

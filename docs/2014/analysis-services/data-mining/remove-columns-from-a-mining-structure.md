---
title: Supprimer des colonnes dans une Structure d’exploration de données | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- mining structures [Analysis Services], columns
- removing columns
- deleting columns
- columns [data mining], mining structure columns
ms.assetid: 41073ffe-9351-416b-9f0c-62634bc213f9
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: ebc79ed1221b729cfac3fb3d34ed5d9683dc6875
ms.sourcegitcommit: f40fa47619512a9a9c3e3258fda3242c76c008e6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/23/2019
ms.locfileid: "66082959"
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
 [Tâches et procédures relatives aux structures d’exploration de données](mining-structure-tasks-and-how-tos.md)  
  
  

---
title: Ajouter des colonnes à une Structure d’exploration de données | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- mining structures [Analysis Services], columns
- columns [data mining], mining structure columns
- adding columns
ms.assetid: 3f879344-9f66-4178-851a-e8c5ccccf4cb
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 85a713bb9da24a67ebe8fdd097535c5a9d5ac98e
ms.sourcegitcommit: f40fa47619512a9a9c3e3258fda3242c76c008e6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/23/2019
ms.locfileid: "66086225"
---
# <a name="add-columns-to-a-mining-structure"></a>ajouter des colonnes à une structure d'exploration de données
  Utilisez le Concepteur d'exploration de données dans [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] pour ajouter des colonnes à une structure d'exploration de données après l'avoir définie dans l'Assistant Exploration de données. Vous pouvez ajouter n'importe quelle colonne qui existe dans la vue de source de données utilisée pour définir la structure d'exploration de données.  
  
> [!NOTE]  
>  Vous pouvez ajouter plusieurs copies de colonnes à une structure d'exploration de données ; toutefois, vous devez éviter d'utiliser plusieurs instances de la colonne dans le même modèle, afin d'éviter de fausses corrélations entre la source et la colonne dérivée.  
  
### <a name="to-add-a-column-to-a-mining-structure"></a>Pour ajouter une colonne à une structure d'exploration de données  
  
1.  Sélectionnez l’onglet **Structure d’exploration de données** dans le Concepteur d’exploration de données.  
  
2.  Cliquez avec le bouton droit de la souris et sélectionnez **Ajouter une colonne**.  
  
     La boîte de dialogue **Sélectionner une colonne** s’ouvre.  
  
3.  Sous **Table source**, sélectionnez la table de la vue de source de données qui contient la colonne.  
  
4.  Sous **Colonne source**, sélectionnez la colonne à ajouter à la structure d’exploration de données.  
  
5.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
> [!NOTE]  
>  Si vous ajoutez une colonne existante, une copie est incluse dans la structure et « 1 » est ajouté au nom. Vous pouvez modifier le nom de la colonne copiée pour qu’elle soit plus descriptive en tapant un nouveau nom dans la propriété **Name** de la colonne de structure d’exploration de données.  
  
## <a name="see-also"></a>Voir aussi  
 [Tâches et procédures relatives aux structures d’exploration de données](mining-structure-tasks-and-how-tos.md)  
  
  

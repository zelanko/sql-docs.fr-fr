---
title: Ajouter des colonnes à une Structure d’exploration de données | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
ms.topic: conceptual
helpviewer_keywords:
- mining structures [Analysis Services], columns
- columns [data mining], mining structure columns
- adding columns
ms.assetid: 3f879344-9f66-4178-851a-e8c5ccccf4cb
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 954159ba298b47c1a10a5e7baef1cff523dcc4b5
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48171249"
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
  
  

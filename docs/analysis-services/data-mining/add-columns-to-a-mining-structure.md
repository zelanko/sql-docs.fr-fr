---
title: "ajouter des colonnes &#224; une structure d&#39;exploration de donn&#233;es | Microsoft Docs"
ms.custom: ""
ms.date: "03/13/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "analysis-services"
  - "analysis-services/data-mining"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "structures d’exploration de données [Analysis Services], colonnes"
  - "colonnes [exploration de données], colonnes de structure d’exploration de données"
  - "ajout de colonnes"
ms.assetid: 3f879344-9f66-4178-851a-e8c5ccccf4cb
caps.latest.revision: 30
author: "Minewiskan"
ms.author: "owend"
manager: "jhubbard"
caps.handback.revision: 30
---
# ajouter des colonnes &#224; une structure d&#39;exploration de donn&#233;es
  Utilisez le Concepteur d'exploration de données dans [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] pour ajouter des colonnes à une structure d'exploration de données après l'avoir définie dans l'Assistant Exploration de données. Vous pouvez ajouter n'importe quelle colonne qui existe dans la vue de source de données utilisée pour définir la structure d'exploration de données.  
  
> [!NOTE]  
>  Vous pouvez ajouter plusieurs copies de colonnes à une structure d'exploration de données ; toutefois, vous devez éviter d'utiliser plusieurs instances de la colonne dans le même modèle, afin d'éviter de fausses corrélations entre la source et la colonne dérivée.  
  
### Pour ajouter une colonne à une structure d'exploration de données  
  
1.  Sélectionnez l’onglet **Structure d’exploration de données** dans le Concepteur d’exploration de données.  
  
2.  Cliquez avec le bouton droit de la souris et sélectionnez **Ajouter une colonne**.  
  
     La boîte de dialogue **Sélectionner une colonne** s’ouvre.  
  
3.  Sous **Table source**, sélectionnez la table de la vue de source de données qui contient la colonne.  
  
4.  Sous **Colonne source**, sélectionnez la colonne à ajouter à la structure d’exploration de données.  
  
5.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
> [!NOTE]  
>  Si vous ajoutez une colonne existante, une copie est incluse dans la structure et « 1 » est ajouté au nom. Vous pouvez modifier le nom de la colonne copiée pour qu’elle soit plus descriptive en tapant un nouveau nom dans la propriété **Name** de la colonne de structure d’exploration de données.  
  
## Voir aussi  
 [Tâches de la structure d'exploration de données et procédures](../../analysis-services/data-mining/mining-structure-tasks-and-how-tos.md)  
  
  
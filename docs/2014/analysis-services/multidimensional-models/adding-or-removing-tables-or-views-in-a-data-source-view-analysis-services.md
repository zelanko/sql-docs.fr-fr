---
title: Ajout ou suppression des Tables ou des vues dans un Data Source View (Analysis Services) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.dsvdesigner.tablespane.f1
helpviewer_keywords:
- deleting tables
- tables [Analysis Services]
- removing tables
- adding tables
- data source views [Analysis Services], tables
- tables [Analysis Services], data source views
ms.assetid: 98307d04-6548-4d7d-9244-2371dd165249
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: dc78ad1f8a1f49d1a42c5b2ded45a913cdd7e669
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48117951"
---
# <a name="adding-or-removing-tables-or-views-in-a-data-source-view-analysis-services"></a>Ajout ou suppression de tables ou de vues dans une vue de source de données (Analysis Services)
  Après avoir créé une vue de source de données (DSV) dans [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], vous pouvez la modifier dans le concepteur de vue de source de données en ajoutant ou en supprimant des tables et des colonnes, y compris les tables et les colonnes d'une autre source de données.  
  
 Pour ouvrir la vue DSV dans le concepteur de vue de source de données, double-cliquez sur la vue DSV dans l'Explorateur de solutions. Une fois que vous avez ouvert la vue DSV, vous pouvez utiliser la commande **Ajouter/supprimer des tables** dans la barre de boutons ou le menu pour modifier ou étendre la vue DSV. Vous pouvez également utiliser les objets du diagramme. Par exemple, vous pouvez sélectionner un objet puis utiliser la touche Suppr de votre clavier pour supprimer un objet.  
  
> [!WARNING]  
>  Soyez prudent lors de la suppression d'une table. La suppression d'une table supprime toutes les colonnes et relations associées de la vue DSV et invalide tous les objets liés à cette table.  
  
## <a name="selecting-tables-or-views-to-add-or-remove"></a>Sélection des tables ou vues à ajouter ou supprimer  
 Dans la boîte de dialogue **Ajouter/supprimer des tables** , vous pouvez déplacer des tables ou des vues entre les listes **Objets disponibles** et **Objets inclus** . La liste **Objets disponibles** inclut à l’origine les tables ou les vues de la source de données principale qui ne se trouvent pas encore dans la vue de source de données. Si la principales source de données prend en charge le `OPENROWSET` (fonction), vous pouvez également ajouter des tables ou vues à partir d’autres sources de données dans le projet ou la base de données.  
  
 L'ajout ou la suppression d'une table à la vue DSV ajoute ou supprime également la table au diagramme sélectionné dans cette vue DSV. Pour plus d’informations sur les diagrammes, consultez [Work with Diagrams in Data Source View Designer &#40;Analysis Services&#41;](work-with-diagrams-in-data-source-view-designer-analysis-services.md).  
  
 Une fois que vous avez placé une table dans la liste **Objets inclus** de la boîte de dialogue **Ajouter/supprimer des tables** , vous pouvez ajouter toutes les tables associées. Cette opération ajoute des tables en fonction des contraintes de clé étrangère dans la source de données, si de telles contraintes existent. Si les contraintes de clé étrangère n’existent pas, vous pouvez utiliser le `NameMatchingCriteria` propriété de la vue de source de données pour déterminer les relations en spécifiant un critère de correspondance des noms de colonne dans les tables pour générer des relations possibles. Si le `NameMatchingCriteria`propriété est spécifiée pour la vue de source de données, cliquez sur **ajouter des Tables associées** pour ajouter des tables à partir de la source de données qui ont des noms de colonne correspondants. Pour plus d’informations sur la configuration de la `NameMatchingCriteria` propriété, consultez [des vues de sources de données dans les modèles multidimensionnels](data-source-views-in-multidimensional-models.md).  
  
> [!NOTE]  
>  L'ajout ou la suppression d'objets dans une vue de source de données n'affecte pas la source de données sous-jacente.  
  
## <a name="see-also"></a>Voir aussi  
 [Vues de sources de données dans les modèles multidimensionnels](data-source-views-in-multidimensional-models.md)   
 [Utiliser des diagrammes dans le Concepteur de vue de Source de données &#40;Analysis Services&#41;](work-with-diagrams-in-data-source-view-designer-analysis-services.md)  
  
  

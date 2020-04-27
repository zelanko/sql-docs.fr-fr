---
title: Ajout ou suppression de tables ou de vues dans une vue de source de données (Analysis Services) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
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
ms.openlocfilehash: da7169cc95b768324e18f1ab5fd7b0a33615f99a
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/26/2020
ms.locfileid: "66077462"
---
# <a name="adding-or-removing-tables-or-views-in-a-data-source-view-analysis-services"></a>Ajout ou suppression de tables ou de vues dans une vue de source de données (Analysis Services)
  Après avoir créé une vue de source de données (DSV) dans [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], vous pouvez la modifier dans le concepteur de vue de source de données en ajoutant ou en supprimant des tables et des colonnes, y compris les tables et les colonnes d'une autre source de données.  
  
 Pour ouvrir la vue DSV dans le concepteur de vue de source de données, double-cliquez sur la vue DSV dans l'Explorateur de solutions. Une fois que vous avez ouvert la vue DSV, vous pouvez utiliser la commande **Ajouter/supprimer des tables** dans la barre de boutons ou le menu pour modifier ou étendre la vue DSV. Vous pouvez également utiliser les objets du diagramme. Par exemple, vous pouvez sélectionner un objet puis utiliser la touche Suppr de votre clavier pour supprimer un objet.  
  
> [!WARNING]  
>  Soyez prudent lors de la suppression d'une table. La suppression d'une table supprime toutes les colonnes et relations associées de la vue DSV et invalide tous les objets liés à cette table.  
  
## <a name="selecting-tables-or-views-to-add-or-remove"></a>Sélection des tables ou vues à ajouter ou supprimer  
 Dans la boîte de dialogue **Ajouter/supprimer des tables** , vous pouvez déplacer des tables ou des vues entre les listes **Objets disponibles** et **Objets inclus** . La liste **Objets disponibles** inclut à l’origine les tables ou les vues de la source de données principale qui ne se trouvent pas encore dans la vue de source de données. Si la source de données principale prend en charge la fonction `OPENROWSET`, vous pouvez également ajouter des tables ou des vues à partir d'autres sources de données dans le projet ou une base de données.  
  
 L'ajout ou la suppression d'une table à la vue DSV ajoute ou supprime également la table au diagramme sélectionné dans cette vue DSV. Pour plus d’informations sur les diagrammes, consultez [Utiliser des diagrammes dans un concepteur de vues de sources de données &#40;Analysis Services&#41;](work-with-diagrams-in-data-source-view-designer-analysis-services.md).  
  
 Une fois que vous avez placé une table dans la liste **Objets inclus** de la boîte de dialogue **Ajouter/supprimer des tables** , vous pouvez ajouter toutes les tables associées. Cette opération ajoute des tables en fonction des contraintes de clé étrangère dans la source de données, si de telles contraintes existent. Si aucune contrainte de clé étrangère n'existe, vous pouvez utiliser la propriété `NameMatchingCriteria` de la vue de source de données pour déterminer des relations en spécifiant un critère de correspondance des noms de colonnes dans les tables pour générer des relations possibles. Si la `NameMatchingCriteria`propriété est spécifiée pour la vue de source de données, cliquez sur **Ajouter des tables associées** pour ajouter des tables de la source de données qui ont des noms de colonnes correspondants. Pour plus d’informations sur la `NameMatchingCriteria` définition de la propriété, consultez [vues de sources de données dans les modèles multidimensionnels](data-source-views-in-multidimensional-models.md).  
  
> [!NOTE]  
>  L'ajout ou la suppression d'objets dans une vue de source de données n'affecte pas la source de données sous-jacente.  
  
## <a name="see-also"></a>Voir aussi  
 [Vues de sources de données dans les modèles multidimensionnels](data-source-views-in-multidimensional-models.md)   
 [Utiliser des diagrammes dans un concepteur de vues de sources de données &#40;Analysis Services&#41;](work-with-diagrams-in-data-source-view-designer-analysis-services.md)  
  
  

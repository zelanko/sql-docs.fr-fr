---
title: "Ajout ou suppression des Tables ou des vues dans les données de Source de vue (Analysis Services) | Documents Microsoft"
ms.custom: 
ms.date: 03/01/2017
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: 
ms.component: data-mining
ms.reviewer: 
ms.suite: pro-bi
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: sql13.asvs.dsvdesigner.tablespane.f1
helpviewer_keywords:
- deleting tables
- tables [Analysis Services]
- removing tables
- adding tables
- data source views [Analysis Services], tables
- tables [Analysis Services], data source views
ms.assetid: 98307d04-6548-4d7d-9244-2371dd165249
caps.latest.revision: "34"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: fe054e5e7378c7b779164961aaa46f1c4e6377d5
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/08/2018
---
# <a name="adding-or-removing-tables-or-views-in-a-data-source-view-analysis-services"></a>Ajout ou suppression de tables ou de vues dans une vue de source de données (Analysis Services)
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]Après avoir créé une vue de source de données (DSV) dans [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], vous pouvez la modifier dans le Concepteur de vue de Source de données en ajoutant ou supprimant des tables et colonnes, y compris les tables et les colonnes d’une autre source de données.  
  
 Pour ouvrir la vue DSV dans le concepteur de vue de source de données, double-cliquez sur la vue DSV dans l'Explorateur de solutions. Une fois que vous avez ouvert la vue DSV, vous pouvez utiliser la commande **Ajouter/supprimer des tables** dans la barre de boutons ou le menu pour modifier ou étendre la vue DSV. Vous pouvez également utiliser les objets du diagramme. Par exemple, vous pouvez sélectionner un objet puis utiliser la touche Suppr de votre clavier pour supprimer un objet.  
  
> [!WARNING]  
>  Soyez prudent lors de la suppression d'une table. La suppression d'une table supprime toutes les colonnes et relations associées de la vue DSV et invalide tous les objets liés à cette table.  
  
## <a name="selecting-tables-or-views-to-add-or-remove"></a>Sélection des tables ou vues à ajouter ou supprimer  
 Dans la boîte de dialogue **Ajouter/supprimer des tables** , vous pouvez déplacer des tables ou des vues entre les listes **Objets disponibles** et **Objets inclus** . La liste **Objets disponibles** inclut à l’origine les tables ou les vues de la source de données principale qui ne se trouvent pas encore dans la vue de source de données. Si la source de données principale prend en charge la fonction **OPENROWSET** , vous pouvez aussi ajouter des tables ou des vues d’autres sources de données dans le projet ou la base de données.  
  
 L'ajout ou la suppression d'une table à la vue DSV ajoute ou supprime également la table au diagramme sélectionné dans cette vue DSV. Pour plus d’informations sur les diagrammes, consultez [Utiliser des diagrammes dans un concepteur de vues de sources de données &#40;Analysis Services&#41;](../../analysis-services/multidimensional-models/work-with-diagrams-in-data-source-view-designer-analysis-services.md).  
  
 Une fois que vous avez placé une table dans la liste **Objets inclus** de la boîte de dialogue **Ajouter/supprimer des tables** , vous pouvez ajouter toutes les tables associées. Cette opération ajoute des tables en fonction des contraintes de clé étrangère dans la source de données, si de telles contraintes existent. S’il n’existe aucune contrainte de clé étrangère, vous pouvez utiliser la propriété **NameMatchingCriteria** de la vue de source de données pour déterminer des relations en spécifiant un critère de correspondance des noms de colonnes dans les tables pour générer des relations possibles. Si la propriété **NameMatchingCriteria**est spécifiée pour la vue de source de données, cliquez sur **Ajouter des tables associées** pour ajouter des tables de la source de données dont les noms de colonnes correspondent. Pour plus d’informations sur la définition de la propriété **NameMatchingCriteria** , consultez [Vues de sources de données dans les modèles multidimensionnels](../../analysis-services/multidimensional-models/data-source-views-in-multidimensional-models.md).  
  
> [!NOTE]  
>  L'ajout ou la suppression d'objets dans une vue de source de données n'affecte pas la source de données sous-jacente.  
  
## <a name="see-also"></a>Voir aussi  
 [Vues de sources de données dans les modèles multidimensionnels](../../analysis-services/multidimensional-models/data-source-views-in-multidimensional-models.md)   
 [Utiliser des diagrammes dans un concepteur de vues de sources de données &#40;Analysis Services&#41;](../../analysis-services/multidimensional-models/work-with-diagrams-in-data-source-view-designer-analysis-services.md)  
  
  

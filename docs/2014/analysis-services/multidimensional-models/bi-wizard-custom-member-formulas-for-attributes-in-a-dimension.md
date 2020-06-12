---
title: Définir des formules de membre personnalisées pour les attributs d’une dimension | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- Business Intelligence enhancements [Analysis Services], custom member formulas
- member formulas [Analysis Services]
- dimensions [Analysis Services], Business Intelligence enhancements
- custom member formulas [Analysis Services]
- CustomRollupColumn property
ms.assetid: c4467b08-ce59-4de7-a2d9-c22e246bdd52
author: minewiskan
ms.author: owend
ms.openlocfilehash: 112f8944bd20b2b6a464b0d84fb8ac1a0e89d976
ms.sourcegitcommit: f0772f614482e0b3cde3609e178689ce62ca3a19
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84544571"
---
# <a name="set-custom-member-formulas-for-attributes-in-a-dimension"></a>Définir des formules de membre personnalisées pour les attributs d’une dimension
  Ajoutez une formule de membre personnalisée à un cube ou à une dimension pour remplacer l'agrégation par défaut qui est associée à un membre de dimension par les résultats d'une expression MDX (Multidimensional Expressions). (Cette fonctionnalité affecte à la propriété `CustomRollupColumn` un attribut spécifié dans une dimension.)  
  
> [!NOTE]  
>  Les formules de membre personnalisées sont disponibles uniquement pour les dimensions basées sur des sources de données existantes. Pour les dimensions qui ont été créées sans source de données, vous devez exécuter l'Assistant Génération de schéma pour créer une vue de source de données avant d'ajouter une formule de membre personnalisée.  
  
 Pour ajouter une formule de membre personnalisée, utilisez l’Assistant Business Intelligence et sélectionnez l’option **Créer une formule de membre personnalisée** dans la page **Choisir des améliorations** . Cet Assistant vous guide ensuite dans la procédure à suivre pour sélectionner la dimension à laquelle vous voulez appliquer une formule de membre personnalisée et pour activer la formule de membre personnalisée.  
  
## <a name="selecting-a-dimension"></a>Sélection d'une dimension  
 Dans la première page **Créer une formule de membre personnalisée** de l’Assistant, vous spécifiez la dimension à laquelle vous voulez appliquer une formule de membre personnalisée. L'ajout de la formule de membre personnalisée à la dimension sélectionnée apportera des modifications à cette dimension. Ces modifications seront héritées par tous les cubes contenant la dimension sélectionnée.  
  
## <a name="enabling-a-custom-member-formula"></a>Activation d'une formule de membre personnalisée  
 Dans la deuxième page **Créer une formule de membre personnalisée** de l’Assistant, vous associez la colonne source contenant la formule de membre personnalisée à un ou plusieurs attributs de la dimension. Dans la colonne **Attribut** , cochez la case en regard de l’attribut à associer à la colonne de la formule de membre personnalisée. À chaque fois que vous sélectionnez un attribut, l’Assistant affiche la boîte de dialogue **Sélectionner une colonne** . Dans cette boîte de dialogue, cliquez sur la colonne de la table de dimension qui contient la formule. Si vous souhaitez modifier une sélection après avoir fermé la boîte de dialogue **Sélectionner une colonne** , cliquez sur la cellule **Colonne source** à modifier, puis cliquez sur les points de suspension (**...**) pour ouvrir à nouveau la boîte de dialogue **Sélectionner une colonne** .  
  
## <a name="see-also"></a>Voir aussi  
 [Utiliser l’Assistant Business Intelligence pour améliorer des dimensions](../use-the-business-intelligence-wizard-to-enhance-dimensions.md)  
  
  

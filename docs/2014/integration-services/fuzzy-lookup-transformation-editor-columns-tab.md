---
title: Éditeur de transformation de recherche floue (onglet colonnes) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.fuzzylookuptransformation.columns.f1
helpviewer_keywords:
- Fuzzy Lookup Transformation Editor
ms.assetid: aaf45327-79e9-4760-9b4d-546ace91b5b4
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: 063248c6b91aebf6198323487aa30ddd1c9cb6ec
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "66058328"
---
# <a name="fuzzy-lookup-transformation-editor-columns-tab"></a>Éditeur de transformation de recherche floue (onglet Colonnes)
  L'onglet **Colonnes** de la boîte de dialogue **Éditeur de transformation de recherche floue** vous permet de définir les propriétés des colonnes d'entrée et de sortie.  
  
 Pour en savoir plus sur la transformation de recherche floue, consultez [Fuzzy Lookup Transformation](data-flow/transformations/lookup-transformation.md).  
  
## <a name="options"></a>Options  
 **Colonnes d'entrée disponibles**  
 Faites glisser les colonnes d'entrée sur les colonnes de recherche afin de les y connecter. Ces colonnes doivent avoir le même type de données pris en charge. Sélectionnez une ligne de mappage et cliquez avec le bouton droit pour modifier les mappages dans la boîte de dialogue [Créer des relations](data-flow/transformations/create-relationships.md) .  
  
 **Nom**  
 Permet d'afficher les noms des colonnes d'entrée disponibles.  
  
 **Transfert direct**  
 Permet d'indiquer s'il convient d'inclure les colonnes d'entrée dans la sortie de la transformation.  
  
 **Colonnes de recherche disponibles**  
 Ces cases à cocher vous permettent de choisir les colonnes sur lesquelles les opérations de recherche floue doivent porter.  
  
 **colonne de recherche**  
 Permet de choisir les colonnes de recherche floue dans la liste des colonnes disponibles de la table de référence. Vos sélections se reflètent dans les sélections des cases à cocher tirées de la table **Colonnes de recherche disponibles** . En sélectionnant une colonne dans la table **Colonnes de recherche disponibles** , vous créez ainsi une colonne de sortie contenant la valeur de la colonne issue de la table de référence de chaque ligne retournée y correspondant.  
  
 **Alias de sortie**  
 Permet de saisir un alias pour la sortie de chaque colonne de recherche. La valeur par défaut correspond au nom de la colonne de recherche suivi d'une valeur d'index numérique. Vous pouvez cependant choisir tout autre nom descriptif s'il reste unique.  
  
## <a name="see-also"></a>Voir aussi  
 [Guide de référence des erreurs et des messages propres à Integration Services](../../2014/integration-services/integration-services-error-and-message-reference.md)   
 [Éditeur de transformation de recherche floue &#40;onglet de la table de référence&#41;](../../2014/integration-services/fuzzy-lookup-transformation-editor-reference-table-tab.md)   
 [Éditeur de transformation de recherche floue &#40;onglet Avancé&#41;](../../2014/integration-services/fuzzy-lookup-transformation-editor-advanced-tab.md)  
  
  

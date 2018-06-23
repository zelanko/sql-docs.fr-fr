---
title: Éditeur de Transformation de recherche de terme (onglet recherche de terme) | Documents Microsoft
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- integration-services
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- sql12.dts.designer.termlookup.termlookup.f1
helpviewer_keywords:
- Term Lookup Transformation Editor
ms.assetid: 245d3466-d51f-4073-978a-694a8d9dfaec
caps.latest.revision: 25
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.openlocfilehash: 0f00dba7a6b5c634c284161cd8c0af3e0e471375
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36044243"
---
# <a name="term-lookup-transformation-editor-term-lookup-tab"></a>Éditeur de transformation de recherche de terme (onglet Recherche de terme)
  L'onglet **Recherche de terme** de la boîte de dialogue **Éditeur de transformation de recherche de terme** permet de mapper une colonne d'entrée à une colonne de recherche dans une table de référence et de fournir un alias pour chaque colonne de sortie.  
  
 Pour en savoir plus sur la transformation de recherche de terme, consultez [Term Lookup Transformation](data-flow/transformations/lookup-transformation.md).  
  
## <a name="options"></a>Options  
 **Colonnes d'entrée disponibles**  
 À l'aide des cases à cocher, sélectionnez les colonnes d'entrées à transmettre telles quelles à la sortie. Faites glisser une colonne d'entrée vers la liste **Colonnes de référence disponibles** pour la mapper sur une colonne de recherche dans la table de référence. Les types de données prises en charge par les colonnes d'entrée et de recherche doivent correspondre et avoir pour valeur  DT_NTEXT ou DT_WSTR. Sélectionnez une ligne de mappage et cliquez avec le bouton droit de la souris pour modifier les mappages dans la boîte de dialogue [Créer des relations](data-flow/transformations/create-relationships.md) .  
  
 **Colonnes de référence disponibles**  
 Affiche les colonnes disponibles dans la table de référence. Choisissez la colonne qui contient la liste de termes correspondants.  
  
 **Colonne SQL directe**  
 Permet de sélectionner des colonnes dans la liste des colonnes d'entrée disponibles. Vos sélections se reflètent dans les sélections des cases à cocher de la table **Colonnes d'entrée disponibles** .  
  
 **Alias de colonne de sortie**  
 Permet de saisir un alias pour chaque colonne de sortie. La valeur par défaut correspond au nom de la colonne. Cependant, vous pouvez choisir un nom unique descriptif.  
  
 **Configurer la sortie d'erreur**  
 Utilisez la boîte de dialogue [Configurer l’affichage des erreurs](../../2014/integration-services/configure-error-output.md) pour spécifier les options de gestion des erreurs dans les lignes qui provoquent des erreurs.  
  
## <a name="see-also"></a>Voir aussi  
 [Integration Services Error and Message Reference](../../2014/integration-services/integration-services-error-and-message-reference.md)   
 [Éditeur de Transformation de recherche de terme &#40;onglet de la Table de référence&#41;](../../2014/integration-services/term-lookup-transformation-editor-reference-table-tab.md)   
 [Éditeur de Transformation de recherche de terme &#40;onglet Avancé&#41;](../../2014/integration-services/term-lookup-transformation-editor-advanced-tab.md)   
 [Transformation d'extraction de terme](data-flow/transformations/term-extraction-transformation.md)  
  
  
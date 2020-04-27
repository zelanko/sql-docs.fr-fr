---
title: Éditeur de transformation de recherche (page colonnes) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.lookuptransformation.columns.f1
helpviewer_keywords:
- Lookup Transformation Editor
ms.assetid: 690ffef5-fd59-4e95-a27d-4fcf0d6b1c0b
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: e1a32dcbcee6704cb4fecef7b58cbff8354b910a
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/26/2020
ms.locfileid: "66057897"
---
# <a name="lookup-transformation-editor-columns-page"></a>Éditeur de transformation de recherche (page Colonnes)
  Utilisez la page **Colonnes** de la boîte de dialogue **Éditeur de transformation de recherche** pour définir la jointure entre la table source et la table de référence, ainsi que pour sélectionner les colonnes de recherche dans la table de référence.  
  
 Pour en savoir plus sur la transformation de recherche, consultez [Lookup Transformation](data-flow/transformations/lookup-transformation.md).  
  
## <a name="options"></a>Options  
 **Colonnes d’entrée disponibles**  
 Affichez la liste des colonnes d'entrée disponibles. Les colonnes d'entrée représentent les colonnes dans le flux de données d'une source connectée. Les colonnes d'entrée et la colonne de recherche doivent avoir des types de données identiques.  
  
 Au moyen d'une opération glisser-déplacer, mappez les colonnes d'entrée disponibles aux colonnes de recherche.  
  
 Vous pouvez également mapper les colonnes d'entrée aux colonnes de recherche à l'aide du clavier. Pour ce faire, mettez en surbrillance une colonne dans la table **Colonnes d'entrée disponibles** , appuyez sur la touche de l'application, puis cliquez sur **Modifier les mappages**.  
  
 **Colonnes de recherche disponibles**  
 Affichez la liste des colonnes de recherche. Les colonnes de recherche représentent les colonnes de la table de référence dans lesquelles vous souhaitez rechercher des valeurs qui correspondent aux colonnes d'entrée.  
  
 Au moyen d'une opération glisser-déplacer, mappez les colonnes de recherche disponibles aux colonnes d'entrée.  
  
 Utilisez les cases à cocher pour sélectionner les colonnes de recherche de la table de référence sur lesquelles effectuer les opérations de recherche.  
  
 Vous pouvez également mapper les colonnes de recherche aux colonnes d'entrée à l'aide du clavier. Pour ce faire, mettez en surbrillance une colonne dans la table **Colonnes de recherche disponibles** , appuyez sur la touche de l'application, puis cliquez sur **Modifier les mappages**.  
  
 **colonne de recherche**  
 Affichez les colonnes de recherche sélectionnées. Les sélections se reflètent dans les sélections des cases à cocher de la table **Colonnes de recherche disponibles** .  
  
 **Opération de recherche**  
 Dans la liste, sélectionnez une opération de recherche à exécuter sur la colonne de recherche.  
  
 **Alias de sortie**  
 Permet de saisir un alias pour la sortie de chaque colonne de recherche. La valeur par défaut est le nom de la colonne de recherche. Toutefois, vous pouvez sélectionner n'importe quel nom descriptif unique.  
  
## <a name="see-also"></a>Voir aussi  
 [Éditeur de transformation de recherche &#40;page général&#41;](general-page-of-integration-services-designers-options.md)   
 [Éditeur de transformation de recherche &#40;page connexion&#41;](../../2014/integration-services/lookup-transformation-editor-connection-page.md)   
 [Éditeur de transformation de recherche &#40;&#41;de page avancé](../../2014/integration-services/lookup-transformation-editor-advanced-page.md)   
 [Éditeur de transformation de recherche &#40;page sortie d’erreur&#41;](../../2014/integration-services/lookup-transformation-editor-error-output-page.md)   
 [transformation de recherche floue](data-flow/transformations/fuzzy-lookup-transformation.md)  
  
  

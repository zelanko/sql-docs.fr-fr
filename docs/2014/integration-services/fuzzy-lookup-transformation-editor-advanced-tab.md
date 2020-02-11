---
title: Éditeur de transformation de recherche floue (onglet Avancé) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.fuzzylookuptransformation.advanced.f1
helpviewer_keywords:
- Fuzzy Lookup Transformation Editor
ms.assetid: 0a2919be-2ea7-4c06-82b8-0ffad5f0dd83
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: 26a7efa42215f1bc456cf4a4c47b3a71c62b94e7
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "66058351"
---
# <a name="fuzzy-lookup-transformation-editor-advanced-tab"></a>Éditeur de transformation de recherche floue (onglet Avancé)
  Utilisez l’onglet **Avancé** de la boîte de dialogue **Éditeur de transformation de recherche floue** pour définir les paramètres relatifs à une recherche floue.  
  
 Pour en savoir plus sur la transformation de recherche floue, consultez [Fuzzy Lookup Transformation](data-flow/transformations/lookup-transformation.md).  
  
## <a name="options"></a>Options  
 **Nombre maximal de correspondances à la sortie par recherche**  
 Indiquez le nombre maximal de correspondances que la transformation peut retourner pour chaque ligne d'entrée. La valeur par défaut est **1**.  
  
 **Seuil de similarité**  
 Définissez le seuil de similarité au niveau du composant à l'aide du curseur. Plus la valeur est proche de 1, plus la valeur de recherche doit être proche de la valeur source pour constituer une correspondance. Si vous augmentez le seuil, vous pouvez améliorer la vitesse de correspondance étant donné qu'un plus petit nombre d'enregistrements candidats doit être pris en compte.  
  
 **Délimiteurs de jetons**  
 Indiquez les séparateurs utilisés par la transformation pour marquer les valeurs de colonne.  
  
## <a name="see-also"></a>Voir aussi  
 [Guide de référence des erreurs et des messages propres à Integration Services](../../2014/integration-services/integration-services-error-and-message-reference.md)   
 [Éditeur de transformation de recherche floue &#40;onglet de la table de référence&#41;](../../2014/integration-services/fuzzy-lookup-transformation-editor-reference-table-tab.md)   
 [Éditeur de transformation de recherche floue &#40;onglet Colonnes&#41;](../../2014/integration-services/fuzzy-lookup-transformation-editor-columns-tab.md)  
  
  

---
title: Éditeur de transformation de regroupement probable (onglet Avancé) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.fuzzygroupingtransformation.advanced.f1
helpviewer_keywords:
- Fuzzy Grouping Transformation Editor
ms.assetid: dd820d75-b8a7-4515-aea4-3553ba5b442e
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: dcebe499eb80fbe01b9aa36a4e07785846eaf621
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/26/2020
ms.locfileid: "66058371"
---
# <a name="fuzzy-grouping-transformation-editor-advanced-tab"></a>Éditeur de transformation de regroupement probable (onglet Avancé).
  Utilisez l'onglet **Avancé** de la boîte de dialogue **Éditeur de transformation de regroupement probable** pour spécifier les colonnes d'entrée et de sortie, définir des seuils de similarité et des séparateurs.  
  
> [!NOTE]  
>  Les `Exhaustive` `MaxMemoryUsage` propriétés et de la transformation de regroupement approximatif ne sont pas disponibles dans l **'éditeur de transformation de regroupement probable**, mais elles peuvent être définies à l’aide de l' **éditeur avancé**. Pour plus d'informations sur ces propriétés, consultez la section Transformation de regroupement approximatif dans [Transformation Custom Properties](data-flow/transformations/transformation-custom-properties.md).  
  
 Pour en savoir plus sur la transformation de regroupement approximatif, consultez [Fuzzy Grouping Transformation](data-flow/transformations/fuzzy-grouping-transformation.md).  
  
## <a name="options"></a>Options  
 **Nom de la colonne clé d'entrée**  
 Spécifiez le nom d'une colonne de sortie qui contient l'identificateur unique de chaque ligne d'entée. La colonne `_key_in` a un nom qui identifie chaque ligne de manière unique.  
  
 **Nom de la colonne clé de sortie**  
 Spécifiez le nom d'une colonne de sortie qui contient l'identificateur unique de la ligne canonique d'un groupe de lignes dupliquées. La colonne `_key_out` correspond à la valeur `_key_in` de la ligne de données canonique.  
  
 **Nom de colonne du score de similarité**  
 Spécifiez un nom qui contient le score de similarité. Le score de similarité est une valeur comprise entre 0 et 1 qui indique le niveau de similarité avec la ligne canonique. Plus le score se rapproche de 1, plus la ligne correspond à la ligne canonique.  
  
 **Seuil de similarité**  
 Définissez le seuil de similarité au moyen du curseur. Plus le seuil est proche de 1, plus la similarité entre les lignes est grande pour se qualifier comme lignes dupliquées. L'augmentation du seuil peut accélérer les recherches du fait que moins de candidats doivent être évalués.  
  
 **Séparateurs de jetons**  
 La transformation fournit un ensemble de séparateurs par défaut pour marquer des données, mais vous devez ajouter ou supprimer des séparateurs en modifiant la liste en fonction des besoins.  
  
## <a name="see-also"></a>Voir aussi  
 [Integration Services de référence des erreurs et des messages](../../2014/integration-services/integration-services-error-and-message-reference.md)   
 [Identifier des lignes de données semblables à l'aide de la transformation de regroupement probable](data-flow/transformations/identify-similar-data-rows-by-using-the-fuzzy-grouping-transformation.md)  
  
  

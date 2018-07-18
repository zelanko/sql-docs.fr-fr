---
title: Éditeur de Transformation de regroupement probable (onglet Avancé) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- integration-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.fuzzygroupingtransformation.advanced.f1
helpviewer_keywords:
- Fuzzy Grouping Transformation Editor
ms.assetid: dd820d75-b8a7-4515-aea4-3553ba5b442e
caps.latest.revision: 28
author: douglaslms
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 7e8c12ad683e46838a88359170ea970f20c02828
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/02/2018
ms.locfileid: "37231519"
---
# <a name="fuzzy-grouping-transformation-editor-advanced-tab"></a>Éditeur de transformation de regroupement probable (onglet Avancé).
  Utilisez l'onglet **Avancé** de la boîte de dialogue **Éditeur de transformation de regroupement probable** pour spécifier les colonnes d'entrée et de sortie, définir des seuils de similarité et des séparateurs.  
  
> [!NOTE]  
>  Le `Exhaustive` et `MaxMemoryUsage` propriétés de la transformation de regroupement probable ne sont pas disponibles dans le **éditeur de Transformation de regroupement probable**, mais peut être définie à l’aide de la **éditeur avancé**. Pour plus d'informations sur ces propriétés, consultez la section Transformation de regroupement approximatif dans [Transformation Custom Properties](data-flow/transformations/transformation-custom-properties.md).  
  
 Pour en savoir plus sur la transformation de regroupement approximatif, consultez [Fuzzy Grouping Transformation](data-flow/transformations/fuzzy-grouping-transformation.md).  
  
## <a name="options"></a>Options  
 **Nom de la colonne clé d'entrée**  
 Spécifiez le nom d'une colonne de sortie qui contient l'identificateur unique de chaque ligne d'entée. Le `_key_in` colonne possède une valeur qui identifie de façon unique chaque ligne.  
  
 **Nom de la colonne clé de sortie**  
 Spécifiez le nom d'une colonne de sortie qui contient l'identificateur unique de la ligne canonique d'un groupe de lignes dupliquées. La colonne `_key_out` correspond à la valeur `_key_in` de la ligne de données canonique.  
  
 **Nom de colonne du score de similarité**  
 Spécifiez un nom qui contient le score de similarité. Le score de similarité est une valeur comprise entre 0 et 1 qui indique le niveau de similarité avec la ligne canonique. Plus le score se rapproche de 1, plus la ligne correspond à la ligne canonique.  
  
 **Seuil de similarité**  
 Définissez le seuil de similarité au moyen du curseur. Plus le seuil est proche de 1, plus la similarité entre les lignes est grande pour se qualifier comme lignes dupliquées. L'augmentation du seuil peut accélérer les recherches du fait que moins de candidats doivent être évalués.  
  
 **Séparateurs de jetons**  
 La transformation fournit un ensemble de séparateurs par défaut pour marquer des données, mais vous devez ajouter ou supprimer des séparateurs en modifiant la liste en fonction des besoins.  
  
## <a name="see-also"></a>Voir aussi  
 [Integration Services Error and Message Reference](../../2014/integration-services/integration-services-error-and-message-reference.md)   
 [Identifier des lignes de données semblables à l'aide de la transformation de regroupement probable](data-flow/transformations/identify-similar-data-rows-by-using-the-fuzzy-grouping-transformation.md)  
  
  

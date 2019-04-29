---
title: Éditeur de Transformation de regroupement probable (onglet colonnes) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.fuzzygroupingtransformation.columns.f1
helpviewer_keywords:
- Fuzzy Grouping Transformation Editor
ms.assetid: 24f4539f-2a9f-4acd-acc7-06228a07f7df
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: dc69475a26bde2045c06429462b5de306c4f932f
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62893244"
---
# <a name="fuzzy-grouping-transformation-editor-columns-tab"></a>Éditeur de transformation de regroupement approximatif (onglet Colonnes)
  L'onglet **Colonnes** de la boîte de dialogue **Éditeur de transformation de regroupement approximatif** permet de spécifier les colonnes utilisées pour regrouper les lignes comportant des doublons.  
  
 Pour en savoir plus sur la transformation de regroupement approximatif, consultez [Fuzzy Grouping Transformation](data-flow/transformations/fuzzy-grouping-transformation.md).  
  
## <a name="options"></a>Options  
 **Colonnes d'entrée disponibles**  
 Sélectionnez dans cette liste les colonnes d'entrée utilisées pour regrouper les lignes comportant des doublons.  
  
 **Nom**  
 Permet d'afficher le nom des colonnes d'entrée disponibles.  
  
 **Transfert direct**  
 Permet d'indiquer s'il est nécessaire d'inclure la colonne d'entrée dans la sortie de la transformation. Toutes les colonnes utilisées pour le regroupement sont automatiquement copiées dans la sortie. Vous pouvez inclure des colonnes supplémentaires en activant cette colonne.  
  
 **Colonne d'entrée**  
 Choisissez l’une des colonnes d’entrée précédemment sélectionnées dans la liste **Colonnes d’entrée disponibles** .  
  
 **Alias de sortie**  
 Entrez un nom descriptif pour la colonne de sortie correspondante. Par défaut, cette colonne porte le même nom que la colonne d'entrée.  
  
 **Grouper les alias de sortie**  
 Entrez un nom descriptif pour la colonne qui va contenir la valeur canonique des doublons groupés. Par défaut, cette colonne de sortie porte le nom de la colonne d'entrée suivi de la mention « _clean ».  
  
 **Type de correspondance**  
 Sélectionnez la correspondance floue ou exacte. Avec une correspondance approximative, les lignes sont considérées comme des doublons si elles sont suffisamment similaires dans toutes les colonnes. Si vous spécifiez une correspondance exacte pour certaines colonnes, seules les lignes contenant des valeurs identiques dans les colonnes associées à une correspondance exacte seront considérées comme des doublons probables. Par conséquent, si vous savez qu'une colonne ne contient aucune erreur ni incohérence, vous pouvez opter pour la correspondance exacte sur cette colonne afin d'accroître la précision de la correspondance approximative sur d'autres colonnes.  
  
 **Similarité minimale**  
 Définissez, à l'aide du curseur, le seuil de similarité au niveau de la jointure. Plus la valeur est proche de 1, plus la valeur de recherche doit être proche de la valeur source pour constituer une correspondance. Si vous augmentez le seuil, vous pouvez améliorer la vitesse de correspondance étant donné qu'un plus petit nombre d'enregistrements candidats doit être pris en compte.  
  
 **Alias de sortie de similarité**  
 Spécifiez le nom d'une nouvelle colonne de sortie qui contient le score de similarité de la jointure sélectionnée. Si vous ne définissez pas cette valeur, la colonne de sortie n'est pas créée.  
  
 **Chiffres**  
 Spécifiez l'importance des premiers et derniers chiffres en comparant les données de la colonne. Par exemple, si les premiers chiffres sont significatifs, « 123 Main Street » ne sera pas groupé avec « 456 Main Street ».  
  
|Value|Description|  
|-----------|-----------------|  
|**Aucun**|Les premiers et derniers chiffres ne sont pas significatifs.|  
|**Premiers**|Seuls les premiers chiffres sont significatifs.|  
|**Derniers**|Seuls les derniers chiffres sont significatifs.|  
|**LeadingAndTrailing**|Les premiers et derniers chiffres sont significatifs.|  
  
 **Indicateurs de comparaison**  
 Pour plus d’informations sur les options de comparaison de chaînes, consultez [Comparaison des données chaînes](data-flow/comparing-string-data.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Guide de référence des erreurs et des messages propres à Integration Services](../../2014/integration-services/integration-services-error-and-message-reference.md)   
 [Identifier des lignes de données semblables à l'aide de la transformation de regroupement probable](data-flow/transformations/identify-similar-data-rows-by-using-the-fuzzy-grouping-transformation.md)  
  
  

---
title: Créer des relations | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.createrelationships.f1
ms.assetid: 6ebd305f-ffd2-4a1d-b24c-e28c151b94f5
author: chugugrace
ms.author: chugu
ms.openlocfilehash: b752407b215cd87918aadc23ae0e6f9a14c098c9
ms.sourcegitcommit: 34278310b3e005d008cd2106a7b86fc6e736f661
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/26/2020
ms.locfileid: "85430846"
---
# <a name="create-relationships"></a>Créer des relations
  Utilisez la boîte de dialogue **Créer des relations** pour modifier les mappages entre les colonnes source et les colonnes de la table de recherche configurée dans l'Éditeur de transformation de recherche floue, l'Éditeur de transformation de recherche ou l'Éditeur de transformation de recherche de terme.  
  
> [!NOTE]  
>  La boîte de dialogue **Créer des relations** affiche uniquement les listes **Colonnes d’entrée** et **Colonne de recherche** quand elle est appelée à partir de l’Éditeur de transformation de recherche de terme.  
  
 Pour en savoir plus sur les transformations qui utilisent la boîte de dialogue **Créer des relations** , consultez [Fuzzy Lookup Transformation](lookup-transformation.md), [Lookup Transformation](lookup-transformation.md)et [Term Lookup Transformation](term-lookup-transformation.md).  
  
## <a name="options"></a>Options  
 **Colonne d'entrée**  
 Permet de sélectionner des colonnes dans la liste des colonnes d'entrée disponibles.  
  
 **colonne de recherche**  
 Sélectionnez dans la liste des colonnes de recherche disponibles.  
  
 **Type de mappage**  
 Sélectionnez la correspondance floue ou exacte.  
  
 Lorsque vous utilisez la correspondance floue, les lignes sont considérées correspondre à des doublons si elles sont suffisamment similaires dans toutes les colonnes ayant un type de correspondance floue. Pour optimiser les résultats de la correspondance floue, vous pouvez indiquer que des colonnes doivent utiliser la correspondance exacte au lieu de la correspondance floue. Si, par exemple, vous savez qu'une colonne ne contient pas d'erreur ou d'incohérence, vous pouvez définir la correspondance exacte sur la colonne pour que seules les lignes qui contiennent des valeurs identiques dans la colonne soient considérées comme des doublons possibles. Ceci améliore la précision de la correspondance floue dans les autres colonnes.  
  
 **Indicateurs de comparaison**  
 Pour plus d’informations sur les options de comparaison de chaînes, consultez [Comparaison des données chaînes](../comparing-string-data.md).  
  
 **Similarité minimale**  
 Définissez le seuil de similarité au niveau colonne en utilisant le curseur. Plus la valeur est proche de 1, plus la valeur de recherche doit ressembler à la valeur source pour qu'elle corresponde à une correspondance. L'augmentation du seuil peut accélérer les recherches du fait que moins de candidats doivent être évalués.  
  
 **Alias de sortie de similarité**  
 Définissez le nom d'une nouvelle colonne de sortie qui contient les scores de similarité de la colonne sélectionnée. Si vous ne définissez pas cette valeur, la colonne de sortie n'est pas créée.  
  
## <a name="see-also"></a>Voir aussi  
 [Guide de référence des erreurs et des messages propres à Integration Services](../../integration-services-error-and-message-reference.md)   
 [Éditeur de transformation de recherche floue &#40;onglet Colonnes&#41;](../../fuzzy-lookup-transformation-editor-columns-tab.md)   
 [Éditeur de transformation de recherche &#40;page Colonnes&#41;](../../lookup-transformation-editor-columns-page.md)   
 [Éditeur de transformation de recherche de terme &#40;onglet Recherche de terme&#41;](../../term-lookup-transformation-editor-term-lookup-tab.md)  
  
  

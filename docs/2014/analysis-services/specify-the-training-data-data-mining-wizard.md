---
title: Spécifier les données d’apprentissage (Assistant Exploration de données) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.dm.dmwizard.specifytrainingdata.f1
ms.assetid: cb04deeb-0f89-4bba-b3f1-efccada16825
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: c3bbeb708cdb0c2882b85d55081446b3dc12b56b
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/26/2020
ms.locfileid: "66068066"
---
# <a name="specify-the-training-data-data-mining-wizard"></a>Spécifier les données d'apprentissage (Assistant Exploration de données)
  Utilisez la page **Spécifier les données d’apprentissage** pour identifier les colonnes à inclure dans la structure d’exploration de données. Vous pouvez sélectionner des colonnes à inclure même dans la structure même si vous ne les utilisez pas dans tous les modèles. Par exemple, si vous souhaitez procéder à une extraction des colonnes à partir du modèle d'exploration de données, vous pouvez les inclure dans la structure mais pas dans le modèle.  
  
 Au moins une colonne clé est requise pour chaque table incluse dans la structure. La colonne que vous choisissez en tant que clé varie selon que la table est une table de cas ou une table imbriquée. Si la table est une table imbriquée, la clé est souvent la colonne prédictible également, pas la clé étrangère relationnelle. Pour en savoir plus sur les clés imbriquées, consultez [Tables imbriquées &#40;Analysis Services - Exploration de données&#41;](data-mining/nested-tables-analysis-services-data-mining.md).  
  
> [!NOTE]  
>  Les différents algorithmes d'exploration de données utilisent les clés différemment. Pour en savoir plus sur les différents types de clés, consultez [Types de contenu &#40;exploration de données&#41;](data-mining/content-types-data-mining.md).  
  
 **Pour plus d’informations :** [Structures d’exploration de données &#40;Analysis Services - Exploration de données&#41;](data-mining/mining-structures-analysis-services-data-mining.md), [Colonnes d’un modèle d’exploration de données](data-mining/mining-model-columns.md), [Assistant Exploration de données &#40;Analysis Services - Exploration de données&#41;](data-mining/data-mining-wizard-analysis-services-data-mining.md), [Créer une structure d’exploration de données relationnelle](data-mining/create-a-relational-mining-structure.md)  
  
## <a name="options"></a>Options  
 **Tables/Colonnes**  
 Affiche les tables et les colonnes sélectionnées dans la page précédente de l'Assistant.  
  
 **\<case à cocher>**  
 Sélectionnez les colonnes à inclure dans la structure d'exploration de données.  
  
 Si votre source de données inclut des tables imbriquées ou plusieurs vues, développez la liste de colonnes pour afficher les tables imbriquées.  
  
 **Clé**  
 Sélectionnez cette option pour utiliser la colonne en tant qu'identificateur unique des données.  
  
 Pour une table de cas, la clé est habituellement l'identificateur unique.  
  
 Pour une table imbriquée, la **Clé** indique l’identificateur d’une ligne dans le contexte du cas associé.  
  
 **Input**  
 Sélectionnez cette option pour utiliser la colonne dans la création des prévisions.  
  
> [!NOTE]  
>  Cette colonne est uniquement disponible lorsque vous créez un modèle d'exploration de données avec la structure d'exploration de données.  
  
 **Prédictible**  
 Sélectionnez cette option pour permettre à la table ou à la colonne d'être prédite en fonction d'une entrée supplémentaire ultérieure.  
  
 Si vous marquez également une table imbriquée comme prévisible, la totalité de la table imbriquée devient prévisible. Si aucune colonne de la table imbriquée n'est marquée comme colonne d'entrée ou colonne prédictible, la table imbriquée est visible dans la structure d'exploration de données, mais elle est ignorée dans le modèle.  
  
 **Remarque** Cette colonne est uniquement disponible quand vous créez un modèle d’exploration de données avec la structure d’exploration de données.  
  
 **Suggest**  
 Cliquez sur ce bouton pour ouvrir la boîte de dialogue **Suggérer des colonnes associées** , qui effectue l’analyse d’un échantillon de données pour identifier les colonnes d’entrée qui présentent la relation la plus forte avec la colonne **Prédictible** sélectionnée basée sur la méthode entropique. Cette analyse s'applique également aux colonnes de tables imbriquées ou aux structures d'exploration de données basées sur les sources OLAP.  
  
 **Remarque** Cette colonne est uniquement disponible quand vous créez un modèle d’exploration de données avec la structure d’exploration de données.  
  
## <a name="see-also"></a>Voir aussi  
 [Aide (F1) de l’Assistant Exploration de données &#40;Analysis Services-exploration de données&#41;](data-mining-wizard-f1-help-analysis-services-data-mining.md)   
 [Suggérer des colonnes associées &#40;l’Assistant Exploration de données&#41;](suggest-related-columns-data-mining-wizard.md)   
 [Spécifier les types de tables &#40;l’Assistant Exploration de données&#41;](specify-table-types-data-mining-wizard.md)   
 [Spécifiez le contenu et le type de données de la colonne &#40;l’Assistant Exploration de données&#41;](specify-the-column-s-content-and-data-type-data-mining-wizard.md)  
  
  

---
title: Enregistrer les données d’exploration de données boîte de dialogue de résultats de requête (vue prévision de modèle d’exploration de données) | Documents Microsoft
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- sql12.asvs.dm.savedataminingqueryresult.f1
helpviewer_keywords:
- Save Data Mining Query Result dialog box
ms.assetid: 112fb527-7466-4fd4-9cf1-75596135648f
caps.latest.revision: 16
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: 709c3364ac5b4d6bc159af4ec6db40663d21fcbf
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36041220"
---
# <a name="save-data-mining-query-result-dialog-box-mining-model-prediction-view"></a>Boîte de dialogue Enregistrer le résultat de la requête d'exploration de données (vue Prévision de modèle d'exploration de données)
  Utilisez la boîte de dialogue **Enregistrer le résultat de la requête d'exploration de données** pour enregistrer les résultats d'une requête d'exploration de données dans une nouvelle table.  
  
 La nouvelle table sera créée dans la base de données définie par la source de données.  
  
## <a name="options"></a>Options  
 **Source de données**  
 Sélectionnez une source de données dans le projet actuel. Si la source de données correcte n'existe pas, cliquez sur **Nouveau** pour en créer une.  
  
 **Nouveau**  
 Ouvre **l’Assistant Source de données**.  
  
 **Nom de la table**  
 Tapez un nom pour la nouvelle table.  
  
 **Remplacer si existe**  
 Sélectionnez cette option pour remplacer une table existante portant le même nom.  
  
 Remplacer la table existante est nécessaire si l'une des conditions suivantes est vraie :  
  
-   Vous avez ajouté des colonnes à la requête de prédiction.  
  
-   Vous avez modifié les noms ou les types de données de colonnes dans la requête de prédiction.  
  
-   Vous avez exécuté une instruction ALTER sur la table de destination.  
  
 Si plusieurs colonnes portent le même nom (par exemple, plusieurs colonnes dérivées peuvent porter le nom de colonne par défaut **Expression**), vous devez créer un alias pour chaque colonne ayant un nom dupliqué. Si les colonnes n'ont pas de noms uniques, une erreur est générée lorsque le concepteur tente d'enregistrer les résultats dans SQL Server, car les colonnes d'une table doivent porter des noms uniques.  
  
 **Ajouter à la vue de gestion dynamique**  
 (Facultatif) Sélectionnez une vue de source de données contenue dans le projet si vous souhaitez ajouter la table à une source de données existante.  
  
 Cette option est utile si vous voulez conserver toutes les tables associées pour un modèle, telles que les données d'apprentissage, les données sources de prédiction et les résultats de la requête, dans la même source de données.  
  
## <a name="see-also"></a>Voir aussi  
 [Générateur de requête de prédiction &#40;d’exploration de données&#41;](prediction-query-builder-data-mining.md)   
 [Interfaces de requête d’exploration de données](data-mining/data-mining-query-tools.md)   
 [Guide de référence des instructions DMX &#40;Data Mining Extensions&#41;](/sql/dmx/data-mining-extensions-dmx-statements)  
  
  

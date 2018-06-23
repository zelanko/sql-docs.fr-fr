---
title: Spécifier le mappage de la boîte de dialogue (graphique d’analyse de précision d’exploration de données) de colonne | Documents Microsoft
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
- sql12.dm.miningmodeleditor.accuracychart.coltotablecolmapping.f1
ms.assetid: 68e9e2d2-173f-4363-a515-fc60bfee3af0
caps.latest.revision: 14
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: 350b0f55f7ae4d445945905984f3e68a34d5c318
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36040959"
---
# <a name="specify-column-mapping-dialog-box-mining-accuracy-chart"></a>Boîte de dialogue Spécifier le mappage des colonnes (Graphique d'analyse de précision de l'exploration de données)
  Utilisez l’onglet **Spécifier le mappage des colonnes** pour sélectionner des tables d’une source de données externe et mapper les colonnes à un modèle d’exploration de données. Vous pouvez ensuite utiliser les données externes pour tester la précision d'un modèle d'exploration de données et afficher les résultats dans le graphique d'analyse de précision.  
  
 **Pour plus d’informations :** [Test et validation &#40;exploration de données&#41;](data-mining/testing-and-validation-data-mining.md)  
  
## <a name="options"></a>Options  
 **Structure d’exploration de données**  
 Affiche la structure d'exploration de données sélectionnée qui contient le modèle à tester.  
  
 **Sélectionnez la Structure**  
 Cliquez pour ouvrir la boîte de dialogue **Sélectionner la structure d’exploration de données** et sélectionner une structure d’exploration de données différente.  
  
 **Sélectionnez une ou plusieurs tables d’entrée**  
 Affiche les tables d'entrée sélectionnées utilisées pour générer le graphique de courbes d'élévation. Sélectionnez la table qui contient les données de test que vous utiliserez pour tester la précision des modèles.  
  
> [!NOTE]  
>  Si le volet ne contient aucune table, cliquez sur **Sélectionner la table de cas** pour ajouter des tables d’une vue de source de données.  
  
 **Supprimer la Table**  
 Supprime la table sélectionnée. Ce bouton est désactivé si aucune table n’a été sélectionnée ou si aucune table ne figure dans la liste **Sélectionner une ou plusieurs tables d’entrée** .  
  
 **Sélectionnez la Table de cas**  
 Cliquez pour ouvrir la boîte de dialogue **Sélectionner une table** , puis sélectionnez une vue de source de données.  
  
 **Remarque** Ce bouton s’affiche uniquement si aucune table de cas n’a été sélectionnée. Pour activer le bouton afin de pouvoir sélectionner une table de cas différente, effacez la liste en sélectionnant toutes les tables existantes, puis en cliquant sur **Supprimer la table**.  
  
 **Sélectionner la Table imbriquée**  
 Ouvre la boîte de dialogue **Sélectionner une table** . Ce bouton s'affiche uniquement si une table de cas a été sélectionnée. Si la structure d'exploration de données associée ne contient pas de table imbriquée, ce bouton est désactivé.  
  
 **Modifier la jointure**  
 Ouvre la boîte de dialogue **Spécifier la jointure imbriquée** . Ce bouton est activé uniquement si la table imbriquée est sélectionnée.  
  
## <a name="see-also"></a>Voir aussi  
 [Test et des tâches de Validation et des procédures &#40;d’exploration de données&#41;](data-mining/testing-and-validation-tasks-and-how-tos-data-mining.md)   
 [Concepteur graphique d’analyse de précision d’exploration de données &#40;d’exploration de données&#41;](mining-accuracy-chart-designer-data-mining.md)  
  
  
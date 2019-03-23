---
title: Exécuter l’éditeur de tâche SQL (Page ensemble de résultats) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.executesqltask.resultset.f1
helpviewer_keywords:
- Execute SQL Task Editor
ms.assetid: d27000c8-8d91-4e1c-b45e-bca9a3c12f6d
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: da5cfd11c00876a4d7f3d8c784715e79bd1c73ba
ms.sourcegitcommit: 5a8678bf85f65be590676745a7fe4fcbcc47e83d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/22/2019
ms.locfileid: "58378559"
---
# <a name="execute-sql-task-editor-result-set-page"></a>Éditeur de tâche d'exécution SQL (page Ensemble de résultats)
  Utilisez la page **Jeu de résultats** de la boîte de dialogue **Éditeur de tâche d’exécution de requêtes SQL** pour mapper le résultat de l’instruction SQL à des variables nouvelles ou existantes. Les options de cette boîte de dialogue sont désactivées si **ResultSet** dans la page Général est défini sur **Aucun**.  
  
 Pour plus d’informations sur cette tâche, consultez [Tache d’exécution de requêtes SQL](control-flow/execute-sql-task.md) et [Ensembles de résultats dans la tâche d’exécution SQL](../../2014/integration-services/result-sets-in-the-execute-sql-task.md).  
  
## <a name="options"></a>Options  
 **Nom de résultat**  
 Après avoir ajouté un ensemble de mappages d’un jeu de résultats en cliquant sur **Ajouter**, donnez un nom au résultat. Selon le type de jeu de résultats, vous devez utiliser des noms de résultats spécifiques.  
  
 Si le type de jeu de résultats est **Ligne unique**, le nom peut être celui d’une colonne retournée par la requête ou le numéro qui, dans la liste des colonnes, représente la position d’une colonne retournée par la requête.  
  
 Si le type de l'ensemble de résultats est **Ensemble de résultats complet** ou **XML**, vous devez utiliser 0 comme nom de jeu de résultats.  
  
 **Rubriques connexes :** [Ensembles de résultats dans la tâche d’exécution SQL](../../2014/integration-services/result-sets-in-the-execute-sql-task.md)  
  
 **Nom de la variable**  
 Mappez le jeu de résultats à une variable en sélectionnant celle-ci, ou cliquez sur \<**Nouvelle variable...**> pour ajouter une nouvelle variable via la boîte de dialogue **Ajouter une variable**.  
  
 **Ajouter**  
 Ajoute une correspondance de jeu de résultats.  
  
 **Supprimer**  
 Sélectionnez un mappage de jeu de résultats dans la liste, puis cliquez sur **Supprimer**.  
  
## <a name="see-also"></a>Voir aussi  
 [Guide de référence des erreurs et des messages propres à Integration Services](../../2014/integration-services/integration-services-error-and-message-reference.md)   
 [Éditeur de tâche SQL exécution &#40;Page Général&#41;](general-page-of-integration-services-designers-options.md)   
 [Éditeur de tâche SQL exécution &#40;Page mappage de paramètre&#41;](../../2014/integration-services/execute-sql-task-editor-parameter-mapping-page.md)   
 [Référence Transact-SQL &#40;moteur de base de données&#41;](/sql/t-sql/language-reference)  
  
  

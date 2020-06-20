---
title: Éditeur de tâche d’exécution SQL (page mappage de paramètre) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.executesqltask.parametermapping.f1
helpviewer_keywords:
- Execute SQL Task Editor
ms.assetid: 8ebe020a-7921-46b2-8823-398748f379b2
author: janinezhang
ms.author: janinez
ms.openlocfilehash: 93881c4e9b91e7ace4c250fbf90b8913484f2ce2
ms.sourcegitcommit: f71e523da72019de81a8bd5a0394a62f7f76ea20
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/17/2020
ms.locfileid: "84966759"
---
# <a name="execute-sql-task-editor-parameter-mapping-page"></a>Éditeur de tâche d'exécution de requête SQL (page Mappage de paramètre)
  Utilisez la page **Mappage de paramètre** de la boîte de dialogue **Éditeur de tâche d’exécution de requêtes SQL** pour associer des variables à des paramètres dans une instruction SQL.  
  
 Pour en savoir plus sur cette tâche, consultez [Tache d’exécution de requêtes SQL](control-flow/execute-sql-task.md) et [Paramètres et codes de retour dans la tâche d’exécution SQL](../../2014/integration-services/parameters-and-return-codes-in-the-execute-sql-task.md).  
  
## <a name="options"></a>Options  
 **Nom de la variable**  
 Après avoir ajouté un mappage de paramètre en cliquant sur **Ajouter**, sélectionnez un système ou une variable définie par l’utilisateur dans la liste ou cliquez \<**New variable...**> pour ajouter une nouvelle variable à l’aide de la boîte de dialogue **Ajouter une variable** .  
  
 **Rubriques connexes :** [Variables Integration Services &#40;SSIS&#41;](integration-services-ssis-variables.md)  
  
 **Sens**  
 Sélectionnez le sens du paramètre. Associez chaque variable à un paramètre d'entrée, un paramètre de sortie ou un code de retour.  
  
 **Type de données**  
 Sélectionnez le type de données du paramètre. La liste des types de données disponibles est propre au fournisseur sélectionné dans le gestionnaire de connexions utilisé par la tâche.  
  
 **Nom du paramètre**  
 Fournissez un nom de paramètre.  
  
 En fonction du type de gestionnaire de connexions que la tâche utilise, vous devez utiliser des nombres ou des noms de paramètres. Certains types de gestionnaires de connexions exigent que le premier caractère du nom de paramètre soit le signe \@, des noms spécifiques tels que \@Param1 ou des noms de colonnes comme noms de paramètres.  
  
 **Rubriques connexes :** [Paramètres et codes de retour dans la tâche d’exécution SQL](../../2014/integration-services/parameters-and-return-codes-in-the-execute-sql-task.md)  
  
 **Taille de paramètre**  
 Indiquez la taille des paramètres qui ont une longueur variable, par exemple les chaînes et champs binaires.  
  
 Ce paramètre garantit que le fournisseur alloue l'espace suffisant pour les valeurs de paramètre à longueur variable.  
  
 **Ajouter**  
 Cliquez pour ajouter une association de paramètre.  
  
 **Supprimer**  
 Sélectionnez une association de paramètre dans la liste et cliquez sur **Supprimer**.  
  
## <a name="see-also"></a>Voir aussi  
 [Integration Services de référence des erreurs et des messages](../../2014/integration-services/integration-services-error-and-message-reference.md)   
 [Éditeur de tâche d’exécution de SQL &#40;&#41;page général](general-page-of-integration-services-designers-options.md)   
 [Éditeur de tâche d’exécution de SQL &#40;page ensemble de résultats&#41;](../../2014/integration-services/execute-sql-task-editor-result-set-page.md)   
 [Référence Transact-SQL &#40;moteur de base de données&#41;](/sql/t-sql/language-reference)  
  
  

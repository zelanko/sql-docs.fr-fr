---
title: Exécutez l’éditeur de tâche SQL (Page mappage de paramètre) | Documents Microsoft
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- integration-services
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- sql12.dts.designer.executesqltask.parametermapping.f1
helpviewer_keywords:
- Execute SQL Task Editor
ms.assetid: 8ebe020a-7921-46b2-8823-398748f379b2
caps.latest.revision: 42
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.openlocfilehash: 863ae3b186cc60c4d2d2e04308dd81023f653f12
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36052441"
---
# <a name="execute-sql-task-editor-parameter-mapping-page"></a>Éditeur de tâche d'exécution de requête SQL (page Mappage de paramètre)
  Utilisez la page **Mappage de paramètre** de la boîte de dialogue **Éditeur de tâche d’exécution de requêtes SQL** pour associer des variables à des paramètres dans une instruction SQL.  
  
 Pour en savoir plus sur cette tâche, consultez [Tache d’exécution de requêtes SQL](control-flow/execute-sql-task.md) et [Paramètres et codes de retour dans la tâche d’exécution SQL](../../2014/integration-services/parameters-and-return-codes-in-the-execute-sql-task.md).  
  
## <a name="options"></a>Options  
 **Nom de la variable**  
 Après avoir ajouté un mappage de paramètre en cliquant sur **Ajouter**, sélectionnez une variable système ou une variable définie par l’utilisateur dans la liste, ou cliquez sur \<**Nouvelle variable...**> pour ajouter une nouvelle variable via la boîte de dialogue **Ajouter une variable**.  
  
 **Rubriques connexes :** [Variables Integration Services &#40;SSIS&#41;](integration-services-ssis-variables.md)  
  
 **Sens**  
 Sélectionnez le sens du paramètre. Associez chaque variable à un paramètre d'entrée, un paramètre de sortie ou un code de retour.  
  
 **Type de données**  
 Sélectionnez le type de données du paramètre. La liste des types de données disponibles est propre au fournisseur sélectionné dans le gestionnaire de connexions utilisé par la tâche.  
  
 **Nom du paramètre**  
 Fournissez un nom de paramètre.  
  
 En fonction du type de gestionnaire de connexions que la tâche utilise, vous devez utiliser des nombres ou des noms de paramètres. Avec certaines types de gestionnaires de connexions, le premier caractère du nom de paramètre doit être le signe @, des noms spécifiques tels que @Param1 doivent être utilisés ou les noms de colonnes doivent être utilisés comme noms de paramètres.  
  
 **Rubriques connexes :** [Paramètres et codes de retour dans la tâche d’exécution SQL](../../2014/integration-services/parameters-and-return-codes-in-the-execute-sql-task.md)  
  
 **Taille de paramètre**  
 Indiquez la taille des paramètres qui ont une longueur variable, par exemple les chaînes et champs binaires.  
  
 Ce paramètre garantit que le fournisseur alloue l'espace suffisant pour les valeurs de paramètre à longueur variable.  
  
 **Ajouter**  
 Cliquez pour ajouter une association de paramètre.  
  
 **Supprimer**  
 Sélectionnez une association de paramètre dans la liste et cliquez sur **Supprimer**.  
  
## <a name="see-also"></a>Voir aussi  
 [Integration Services Error and Message Reference](../../2014/integration-services/integration-services-error-and-message-reference.md)   
 [Éditeur de tâche SQL exécution &#40;Page Général&#41;](general-page-of-integration-services-designers-options.md)   
 [Éditeur de tâche SQL exécution &#40;Page de jeu de résultats&#41;](../../2014/integration-services/execute-sql-task-editor-result-set-page.md)   
 [Référence Transact-SQL &#40;moteur de base de données&#41;](/sql/t-sql/language-reference)  
  
  

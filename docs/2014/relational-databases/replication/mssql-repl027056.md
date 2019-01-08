---
title: MSSQL_REPL027056 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- MSSQL_REPL027056 error
ms.assetid: 92d62f3c-b8ae-482e-a348-2e9a8ee9786e
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: fd6f1d63b0de5e8ce0fda7ab4fbc727c70f67bbd
ms.sourcegitcommit: ceb7e1b9e29e02bb0c6ca400a36e0fa9cf010fca
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/03/2018
ms.locfileid: "52794371"
---
# <a name="mssqlrepl027056"></a>MSSQL_REPL027056
    
## <a name="message-details"></a>Détails du message  
  
|||  
|-|-|  
|Nom du produit|SQL Server|  
|ID d'événement|27056|  
|Source de l'événement|MSSQLSERVER|  
|Composant|[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]|  
|Nom symbolique||  
|Texte du message|Le processus de fusion n'a pas pu modifier l'historique de génération sur le '%1'. Lors de la résolution du problème, redémarrez la synchronisation avec un enregistrement d'historique détaillé et spécifiez un fichier de sortie dans lequel écrire.|  
  
## <a name="explanation"></a>Explication  
 Cette erreur résulte généralement d'une contention dans les tables système de réplication de fusion devenues trop volumineuses. Une longue période de rétention de publication est souvent à l'origine d'une croissance excessive des tables système car les métadonnées doivent être stockées dans ces tables jusqu'à la fin de la période de rétention.  
  
## <a name="user-action"></a>Action de l'utilisateur  
 **Pour résoudre ce problème :**  
  
1.  Diminuez la valeur des paramètres **-DownloadGenerationsPerBatch** et **- UploadGenerationsPerBatch** pour que l’Agent de fusion autorise la poursuite du traitement pendant que vous résolvez le problème à l’origine de l’erreur. Les paramètres des agents peuvent être spécifiés dans des profils d'agent et sur la ligne de commande. Pour plus d'informations, consultez :  
  
    -   [Utiliser des profils d’agent de réplication](agents/replication-agent-profiles.md)  
  
    -   [Afficher et modifier des paramètres d’invite de commandes d’un Agent de réplication &#40;SQL Server Management Studio&#41;](agents/view-and-modify-replication-agent-command-prompt-parameters.md)  
  
    -   [Replication Agent Executables Concepts](concepts/replication-agent-executables-concepts.md).  
  
2.  Spécifiez une période de rétention de publication la plus courte possible. Pour plus d’informations, voir [Subscription Expiration and Deactivation](subscription-expiration-and-deactivation.md).  
  
3.  Dans le cadre de la gestion d'une réplication de fusion, contrôlez de temps en temps le développement des tables système associées à cette réplication : **MSmerge_contents**, **MSmerge_genhistory**, et **MSmerge_tombstone**, **MSmerge_current_partition_mappings**, et **MSmerge_ past_partition_mappings**. Réindexez périodiquement ces tables. Pour plus d’informations, consultez [Réorganiser et reconstruire des index](../indexes/indexes.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Guide de référence des erreurs et des événements &#40;réplication&#41;](errors-and-events-reference-replication.md)  
  
  

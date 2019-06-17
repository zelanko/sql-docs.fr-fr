---
title: MSSQL_ENG014152 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- MSSQL_ENG014152 error
ms.assetid: 4215e2b1-cd30-441f-9671-9afc742adf6e
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: e14c0d724ba4832dfc0f67deec25308804b82f84
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "63191424"
---
# <a name="mssqleng014152"></a>MSSQL_ENG014152
    
## <a name="message-details"></a>Détails du message  
  
|||  
|-|-|  
|Nom du produit|SQL Server|  
|ID d'événement|14152|  
|Source de l'événement|MSSQLSERVER|  
|Composant|[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]|  
|Nom symbolique||  
|Texte du message|Réplication-%s : agent %s programmé pour réessayer. %s|  
  
## <a name="explanation"></a>Explication  
 L'agent de réplication spécifié a été programmé pour retenter l'opération demandée. Le processus continue à réessayer jusqu'à ce qu'il atteigne le nombre maximal de tentatives de reprise configuré pour l'étape du travail.  
  
 Une nouvelle tentative est effectuée généralement pour l'une des raisons suivantes :  
  
-   La valeur **QueryTimeout** est dépassée.  
  
-   La valeur **LoginTimeout** est dépassée.  
  
-   Le processus de réplication a été choisi comme victime du blocage.  
  
## <a name="user-action"></a>Action de l'utilisateur  
 Si ce message est occasionnel, aucune action de l'utilisateur n'est requise.  
  
 Utilisez [sp_help_jobstep](/sql/relational-databases/system-stored-procedures/sp-help-jobstep-transact-sql) pour afficher le paramétrage actuel du nombre maximal de tentatives défini pour l'étape **Exécution de l'Agent** pour l'agent de réplication spécifié. Vous pouvez utiliser le paramètre **@retry_attempts** de la procédure stockée [sp_update_jobstep](/sql/relational-databases/system-stored-procedures/sp-update-jobstep-transact-sql) pour ajuster le nombre de tentatives de reprise d'une étape de travail.  
  
 Si ce message est récurrent, résolvez le problème en fonction du message qui est à l'origine de la nouvelle tentative. Vérifiez si l'historique de l'agent contient des messages indiquant pourquoi la reprise a dû être planifiée. Dans certains cas, vous devrez peut-être activer une journalisation plus détaillée pour votre agent de réplication. Pour plus d'informations sur la configuration de la journalisation pour la réplication, consultez l'article [312292](https://support.microsoft.com/kb/312292)de la Base de connaissances Microsoft.  
  
## <a name="see-also"></a>Voir aussi  
 [Guide de référence des erreurs et des événements &#40;réplication&#41;](errors-and-events-reference-replication.md)  
  
  

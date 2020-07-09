---
title: MSSQL_ENG014152 | Microsoft Docs
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- MSSQL_ENG014152 error
ms.assetid: 4215e2b1-cd30-441f-9671-9afc742adf6e
author: MashaMSFT
ms.author: mathoma
monikerRange: =azuresqldb-mi-current||>=sql-server-2016||=sqlallproducts-allversions
ms.openlocfilehash: 4225be7df1ceee87e3faf61e322975cb2a7a5694
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85721843"
---
# <a name="mssql_eng014152"></a>MSSQL_ENG014152
[!INCLUDE [SQL Server SQL MI](../../includes/applies-to-version/sql-asdbmi.md)]
    
## <a name="message-details"></a>Détails du message  
  
|||  
|-|-|  
|Nom du produit|SQL Server|  
|ID de l’événement|14152|  
|Source de l’événement|MSSQLSERVER|  
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
  
 Utilisez [sp_help_jobstep](../../relational-databases/system-stored-procedures/sp-help-jobstep-transact-sql.md) pour afficher le paramétrage actuel du nombre maximal de tentatives défini pour l'étape **Exécution de l'Agent** pour l'agent de réplication spécifié. Vous pouvez utiliser le paramètre `@retry_attempts` de la procédure stockée [sp_update_jobstep](../../relational-databases/system-stored-procedures/sp-update-jobstep-transact-sql.md) pour ajuster le nombre de tentatives de reprise d’une étape de travail.  
  
 Si ce message est récurrent, résolvez le problème en fonction du message qui est à l'origine de la nouvelle tentative. Vérifiez si l'historique de l'agent contient des messages indiquant pourquoi la reprise a dû être planifiée. Dans certains cas, vous devrez peut-être activer une journalisation plus détaillée pour votre agent de réplication. Pour plus d'informations sur la configuration de la journalisation pour la réplication, consultez l'article [312292](https://support.microsoft.com/kb/312292)de la Base de connaissances Microsoft.  
  
## <a name="see-also"></a>Voir aussi  
 [Guide de référence des erreurs et des événements &#40;réplication&#41;](../../relational-databases/replication/errors-and-events-reference-replication.md)  
  
  

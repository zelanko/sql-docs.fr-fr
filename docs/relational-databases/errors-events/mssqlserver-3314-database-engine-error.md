---
title: MSSQLSERVER_3314 | Microsoft Docs
ms.custom: 
ms.date: 04/04/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: errors-events
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
helpviewer_keywords:
- 3314 (Database Engine error)
ms.assetid: f3a5ca6a-b502-4cab-b3b1-4bc753763fa9
caps.latest.revision: 
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 60748996df096813403b9377e14e7796fce120e5
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="mssqlserver3314"></a>MSSQLSERVER_3314
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  
## <a name="details"></a>Détails  
  
|||  
|-|-|  
|Nom du produit|SQL Server|  
|ID d'événement|3314|  
|Source de l'événement|MSSQLSERVER|  
|Composant|SQLEngine|  
|Nom symbolique|ERR_LOG_RID2|  
|Texte du message|Une erreur s'est produite sur l'enregistrement de journal % S_LSN en annulant une opération journalisée dans la base de données '%.*ls'. En général, l'erreur spécifique est déjà journalisée dans le service de journal d'événements Windows. Restaurez la base de données ou le fichier à partir d'une sauvegarde, ou réparez la base de données.|  
  
## <a name="explanation"></a>Explication  
Il s'agit d'une erreur de cumul pour la récupération d'une annulation. Cette erreur a placé la base de données dans l'état SUSPECT. Le groupe de fichiers primaire et éventuellement d'autres groupes de fichiers sont suspects et peut-être endommagés. La base de données ne peut pas être récupérée au démarrage de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] et n'est par conséquent pas disponible. Une action est requise de la part de l'utilisateur pour résoudre le problème.  
  
Notez que si cette erreur se produit pour **tempdb**, l'instance [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] s'arrête.  
  
## <a name="user-action"></a>Action de l'utilisateur  
Cette erreur peut être provoquée par une situation temporaire qui existait sur le système lors d'une tentative donnée de démarrer l'instance du serveur ou de récupérer une base de données. Cette erreur peut également être provoquée par un échec permanent qui se produit à chaque tentative de démarrage de la base de données. Pour plus d'informations sur la cause, examinez le journal des événements Windows pour rechercher une erreur précédente qui indique l'échec spécifique.  
  
Pour plus d'informations sur la cause de l'occurrence de l'erreur 3314, examinez le journal des événements Windows pour rechercher une erreur précédente qui indique l'échec spécifique. L'action utilisateur appropriée varie selon que les informations dans le Journal des événements Windows indiquent que l'erreur [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] a été provoquée par une condition transitoire ou un échec permanent. Pour plus d'informations sur les actions utilisateur requises pour le dépannage de l'erreur 3314, consultez la documentation en ligne de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
## <a name="see-also"></a>Voir aussi  
[ALTER DATABASE &#40;Transact-SQL&#41;](~/t-sql/statements/alter-database-transact-sql-set-options.md)  
[DBCC CHECKDB &#40;Transact-SQL&#41;](~/t-sql/database-console-commands/dbcc-checkdb-transact-sql.md)  
[Restaurations complètes de bases de données &#40;mode de récupération simple&#41;](~/relational-databases/backup-restore/complete-database-restores-simple-recovery-model.md)  
[MSSQLSERVER_824](~/relational-databases/errors-events/mssqlserver-824-database-engine-error.md)  
[sys.databases &#40;Transact-SQL&#41;](~/relational-databases/system-catalog-views/sys-databases-transact-sql.md)  
  

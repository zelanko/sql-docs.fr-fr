---
title: MSSQLSERVER_926 | Microsoft Docs
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- 926 (Database Engine error)
ms.assetid: 57e01668-883b-4be4-84a8-a111caaf0486
caps.latest.revision: 13
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 5078b002ef19d548bed73dac73cc8d960d967d99
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36142040"
---
# <a name="mssqlserver926"></a>MSSQLSERVER_926
    
## <a name="details"></a>Détails  
  
|||  
|-|-|  
|Nom du produit|SQL Server|  
|ID d'événement|926|  
|Source de l'événement|MSSQLSERVER|  
|Composant|SQLEngine|  
|Nom symbolique|DB_SUSPECT|  
|Texte du message|La base de données '%.*ls' ne peut pas être ouverte. Elle a été marquée SUSPECT lors de la récupération. Pour plus d’informations, consultez le journal des erreurs SQL Server.|  
  
## <a name="explanation"></a>Explication  
 La base de données est marquée comme étant suspecte, car le processus de récupération visant à amener la base de données dans un état transactionnel cohérent a échoué. Cela peut se produire durant les opérations suivantes :  
  
-   Démarrage d'une instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
-   Attachement d'une base de données.  
  
-   Utilisation de la base de données RESTORE ou de procédures RESTORE LOG.  
  
## <a name="user-action"></a>Action de l'utilisateur  
 Inspectez le journal des erreurs de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] et déterminez la cause de l'erreur. Si [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] a été redémarré depuis l'échec de la récupération, regardez dans les journaux des erreurs précédents de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] afin de voir pourquoi la récupération a échoué.  
  
 Si la récupération a échoué en raison d'une erreur d'E/S permanente, d'une page endommagée ou d'un autre problème matériel, résolvez le problème matériel sous-jacent et restaurez la base de données en utilisant une sauvegarde. Si aucune sauvegarde n'est disponible, utilisez les options de réparation de DBCC CHECKDB.  
  
 Si vous n'arrivez pas à résoudre ce problème, contactez votre fournisseur d'assistance principal. Fournissez-lui le journal des erreurs de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] afin qu'il puisse l'examiner.  
  
## <a name="see-also"></a>Voir aussi  
 [Sauvegarde et restauration des bases de données SQL Server](../backup-restore/back-up-and-restore-of-sql-server-databases.md)   
 [RESTORE &#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-transact-sql)   
 [Sys.sysdatabases &#40;Transact-SQL&#41;](/sql/relational-databases/system-compatibility-views/sys-sysdatabases-transact-sql)   
 [Attacher et détacher une base de données &#40;SQL Server&#41;](../../relational-databases/databases/database-detach-and-attach-sql-server.md)  
  
  

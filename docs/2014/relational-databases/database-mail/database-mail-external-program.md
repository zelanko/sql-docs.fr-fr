---
title: Programme externe de la messagerie de base de données | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- external programs [Database Mail]
- DatabaseMail90.exe
- Database Mail [SQL Server], external programs
ms.assetid: bc124164-eb6e-4b7f-bf66-98a3113d02f7
caps.latest.revision: 39
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: cc14bf4c5128cff5e836c894dbcd74aa8e7a5cc0
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/02/2018
ms.locfileid: "37233349"
---
# <a name="database-mail-external-program"></a>Programme externe de la messagerie de base de données
  L’exécutable externe de la messagerie de base de données est **DatabaseMail.exe**, situé dans le **répertoire MSSQL\Binn** de l’installation [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . La messagerie de base de données utilise l'activation Service Broker pour démarrer le programme externe lorsque des messages électroniques doivent être traités. La messagerie de base de données démarre une instance du programme externe. Le programme externe s'exécute dans le contexte de sécurité du compte de services pour [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 **Dans cette rubrique :**  
  
-   [Concepts du programme externe de la messagerie de base de données](#ComponentsAndConcepts)  
  
-   [Tâches liées à la configuration du programme externe de messagerie de base de données](#RelatedTasks)  
  
##  <a name="ComponentsAndConcepts"></a> Concepts du programme externe de la messagerie de base de données  
 Lorsque le programme externe démarre, il se connecte à [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] à l'aide de l'authentification Windows et débute le traitement des messages électroniques. S'il n'y a eu aucun message à envoyer pendant le délai d'attente spécifié, le programme est fermé. Vous pouvez configurer la durée du délai d'attente du programme avant qu'il ne soit fermé en utilisant soit l'Assistant Configuration de la messagerie de base de données, soit les procédures stockées de la messagerie de base de données. Pour plus d’informations, consultez [sysmail_configure_sp &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sysmail-configure-sp-transact-sql).  
  
 Le programme externe stocke les informations dans les tables système de la base de données **msdb** . Si le programme externe ne peut pas communiquer avec [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], il consigne des erreurs dans le journal des événements des applications Microsoft Windows. Une journalisation supplémentaire des messages est assurée si vous définissez le niveau de journalisation à **Commentaires** dans la boîte de dialogue **Configurer les paramètres du système** de l' **Assistant Configuration de la messagerie de base de données**.  
  
 Notez que, pour des raisons d'efficacité, le programme externe met en cache les informations de compte et de profil. Les changements de configuration des comptes et profils peuvent donc ne pas être pris en compte dans le programme externe avant quelques minutes.  
  
##  <a name="RelatedTasks"></a> Tâches liées à la configuration du programme externe de messagerie de base de données  
  
|Tâche de configuration|Lien de rubrique|  
|------------------------|----------------|  
|Spécifiez l'heure à laquelle le programme externe s'arrête.|[sysmail_configure_sp &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sysmail-configure-sp-transact-sql)|  
  
## <a name="see-also"></a>Voir aussi  
 [SQL Server Service Broker](../../database-engine/configure-windows/sql-server-service-broker.md)   
 [Journal et audits de la messagerie de base de données](database-mail-log-and-audits.md)   
 [Messagerie de base de données](database-mail.md)  
  
  

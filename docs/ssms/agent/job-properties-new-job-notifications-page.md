---
title: Propriétés du travail - Nouveau travail (page Notifications)
ms.custom: seo-lt-2019
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.technology: ssms
ms.topic: conceptual
f1_keywords:
- sql13.ag.job.notifications.f1
ms.assetid: ed393cbd-4496-4399-a177-e5baa92fb689
author: markingmyname
ms.author: maghan
ms.reviewer: ''
monikerRange: = azuresqldb-mi-current || >= sql-server-2016 || = sqlallproducts-allversions
ms.openlocfilehash: 2d1bc2ec3aef699e491fdac2036352fd986fec85
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85690602"
---
# <a name="job-properties---new-job-notifications-page"></a>Propriétés du travail - Nouveau travail (page Notifications)
[!INCLUDE [SQL Server SQL MI](../../includes/applies-to-version/sql-asdbmi.md)]

> [!IMPORTANT]  
> Dans [Azure SQL Database Managed Instance](https://docs.microsoft.com/azure/sql-database/sql-database-managed-instance), la plupart des fonctionnalités SQL Server Agent sont prises en charge. Pour plus d’informations, consultez [Différences T-SQL entre Azure SQL Database Managed Instance et SQL Server](https://docs.microsoft.com/azure/sql-database/sql-database-managed-instance-transact-sql-information#sql-server-agent).

Utilisez cette page pour définir des actions que [!INCLUDE[msCoName](../../includes/msconame_md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent devra exécuter une fois le travail terminé.  
  
## <a name="options"></a>Options  
**Messagerie électronique**  
Sélectionnez cette option pour envoyer un courrier électronique lorsque le travail se termine. Choisissez ensuite l’opérateur qu’il faut avertir et la condition qui va déclencher la notification : **Lors de la réussite du travail**, **Lors de l’échec du travail** ou **Lorsque le travail est terminé**.  
  
**Page**  
Sélectionnez cette option pour envoyer un courrier électronique à un opérateur via la radiomessagerie lorsque le travail se termine. Choisissez ensuite l’opérateur qu’il faut avertir et la condition qui va déclencher la notification : **Lors de la réussite du travail**, **Lors de l’échec du travail** ou **Lorsque le travail est terminé**.  
  
**Envoi réseau**  
Sélectionnez cette option pour avertir un opérateur de la fin du travail via l'envoi réseau. Choisissez ensuite l’opérateur qu’il faut avertir et la condition qui va déclencher la notification : **Lors de la réussite du travail**, **Lors de l’échec du travail** ou **Lorsque le travail est terminé**.  
  
**Écrire dans le journal des événements des applications Windows**  
Sélectionnez cette option pour écrire une entrée dans le journal des événements des applications lorsque le travail est terminé. Choisissez ensuite la condition qui va déclencher l’écriture de l’entrée : **Lors de la réussite du travail**, **Lors de l’échec du travail** ou **Lorsque le travail est terminé**.  
  
**Supprimer le travail automatiquement**  
Sélectionnez cette option pour supprimer le travail une fois celui-ci terminé. Choisissez ensuite la condition qui va déclencher la suppression du travail : **Lors de la réussite du travail**, **Lors de l’échec du travail** ou **Lorsque le travail est terminé**.  
  
## <a name="see-also"></a>Voir aussi  
[Implémenter des travaux](../../ssms/agent/implement-jobs.md)  
[Procédure : Configurer SQL Server Agent Mail pour utiliser Database Mail](https://msdn.microsoft.com/4b8b61bd-4bd1-43cd-b6e5-c6ed2e101dce)  
  

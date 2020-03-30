---
title: Résoudre les problèmes liés aux travaux multiserveurs qui utilisent des proxys
ms.custom: seo-lt-2019
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- proxies [SQL Server Agent], multiserver jobs
- jobs [SQL Server Agent], multiserver jobs using proxies
ms.assetid: fc579bd3-010c-4f72-8b5c-d0cc18a1f280
author: markingmyname
ms.author: maghan
ms.manager: jroth
ms.reviewer: ''
monikerRange: = azuresqldb-mi-current || >= sql-server-2016 || = sqlallproducts-allversions
ms.openlocfilehash: e3b579bb9154b59247b500c921850cae4e989d39
ms.sourcegitcommit: ff82f3260ff79ed860a7a58f54ff7f0594851e6b
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/29/2020
ms.locfileid: "75257855"
---
# <a name="troubleshoot-multiserver-jobs-that-use-proxies"></a>Résoudre les problèmes liés aux travaux multiserveurs qui utilisent des proxys
[!INCLUDE[appliesto-ss-asdbmi-xxxx-xxx-md](../../includes/appliesto-ss-asdbmi-xxxx-xxx-md.md)]

> [!IMPORTANT]  
> Dans [Azure SQL Database Managed Instance](https://docs.microsoft.com/azure/sql-database/sql-database-managed-instance), la plupart des fonctionnalités SQL Server Agent sont prises en charge. Pour plus d’informations, consultez [Différences T-SQL entre Azure SQL Database Managed Instance et SQL Server](https://docs.microsoft.com/azure/sql-database/sql-database-managed-instance-transact-sql-information#sql-server-agent).

Les travaux distribués dont les étapes sont associées à un proxy s'exécutent dans le contexte du compte proxy sur le serveur cible. Si les étapes de travail utilisant des comptes proxy échouent lors du téléchargement à partir du serveur maître, consultez la colonne **error_message** de la table **sysdownloadlist** dans la base de données **msdb** pour y rechercher les messages d’erreur suivants :  
  
-   « L'étape du travail nécessite un compte proxy, cependant la mise en correspondance de proxy est désactivée sur le serveur cible. »  
  
    Pour résoudre cette erreur, affectez la valeur **\SQLServerAgent\AllowDownloadedJobsToMatchProxyName** _\<n\>_ **\HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft SQL Server\MSSQL.** <n **\SQLServerAgent\AllowDownloadedJobsToMatchProxyName**. Par défaut, la valeur de cette sous-clé est **0** (**false**). La valeur de **MSSQL.** \<*n*> est le nom de l’instance, par exemple, **MSSQL.1** ou **MSSQL.3**.  
  
-   « Proxy introuvable. »  
  
    Un compte proxy sur le serveur cible doit porter le même nom que le compte proxy de serveur maître avec lequel l'étape du travail s'exécute.  
  
> [!CAUTION]  
> [!INCLUDE[ssNoteRegistry](../../includes/ssnoteregistry-md.md)]  
  
## <a name="see-also"></a>Voir aussi  
[Créer un environnement multi-serveur](../../ssms/agent/create-a-multiserver-environment.md)  
  

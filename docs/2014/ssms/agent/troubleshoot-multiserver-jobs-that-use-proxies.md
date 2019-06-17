---
title: Résoudre les problèmes liés aux travaux multiserveurs qui utilisent des proxys | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- proxies [SQL Server Agent], multiserver jobs
- jobs [SQL Server Agent], multiserver jobs using proxies
ms.assetid: fc579bd3-010c-4f72-8b5c-d0cc18a1f280
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 47e3c3991bd4732d542bf1ce79e83000e738ff77
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "63245422"
---
# <a name="troubleshoot-multiserver-jobs-that-use-proxies"></a>Résoudre les problèmes liés aux travaux multiserveurs qui utilisent des proxys
  Les travaux distribués dont les étapes sont associées à un proxy s'exécutent dans le contexte du compte proxy sur le serveur cible. Si les étapes de travail utilisant des comptes proxy échouent lors du téléchargement à partir du serveur maître, consultez la colonne **error_message** de la table **sysdownloadlist** dans la base de données **msdb** pour y rechercher les messages d’erreur suivants :  
  
-   « L'étape du travail nécessite un compte proxy, cependant la mise en correspondance de proxy est désactivée sur le serveur cible. »  
  
     Pour résoudre cette erreur, affectez la valeur **\SQLServerAgent\AllowDownloadedJobsToMatchProxyName** _\<n_> **\HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft SQL Server\MSSQL.** <n **\SQLServerAgent\AllowDownloadedJobsToMatchProxyName**. Par défaut, cette sous-clé est définie sur **0** (`false`). La valeur de **MSSQL.** \<*n*> est le nom de l’instance, par exemple, **MSSQL.1** ou **MSSQL.3**.  
  
-   « Proxy introuvable. »  
  
     Un compte proxy sur le serveur cible doit porter le même nom que le compte proxy de serveur maître avec lequel l'étape du travail s'exécute.  
  
> [!CAUTION]  
>  [!INCLUDE[ssNoteRegistry](../../includes/ssnoteregistry-md.md)]  
  
## <a name="see-also"></a>Voir aussi  
 [Créer un environnement multi-serveur](create-a-multiserver-environment.md)  
  
  

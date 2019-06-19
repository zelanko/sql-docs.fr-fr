---
title: Threads, fenêtre | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.technology: scripting
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- Threads Window [Transact-SQL]
ms.assetid: e153f619-0049-4162-9076-c24a454f3278
author: markingmyname
ms.author: maghan
manager: craigg
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 51d12d639cf1f5b34824f5442f9af026005a56c4
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "65821804"
---
# <a name="transact-sql-debugger---threads-window"></a>Débogueur Transact-SQL - Fenêtre Threads
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
  La fenêtre **Threads** affiche des informations sur le thread du [!INCLUDE[ssDE](../../includes/ssde-md.md)] utilisé par la session de l’éditeur de requête du [!INCLUDE[ssDE](../../includes/ssde-md.md)] en cours de débogage. Vous devez être en mode débogage pour afficher les informations sur le thread.  
  
## <a name="task-list"></a>Liste des tâches  
 **Pour accéder à la fenêtre Threads**  
  
-   Dans le menu **Déboguer** , cliquez sur **Fenêtres**, puis sur **Threads**.  
  
## <a name="columns"></a>Colonnes  
 **ID**  
 Numéro d'identification unique que le débogueur [!INCLUDE[tsql](../../includes/tsql-md.md)] attribue au thread. Vous pouvez obtenir des d'informations supplémentaires sur le thread en sélectionnant une ligne dans la vue de gestion dynamique sys.dm_os_threads.  
  
 Si vous n’êtes pas en mode Regroupement léger, sélectionnez la ligne dont la valeur dans os_thread_id correspond à la valeur dans la colonne **ID** . Si vous êtes en mode Regroupement léger, sélectionnez la ligne dont la valeur dans fiber_context_address correspond à la valeur dans la colonne **ID** .  
  
 **Name**  
 Affiche des informations sur la session du [!INCLUDE[ssDE](../../includes/ssde-md.md)] au format **nom_ordinateur/nom_instance [SPID]** .  
  
 **ComputerName**  
 Nom de l'ordinateur qui exécute l'instance du [!INCLUDE[ssDE](../../includes/ssde-md.md)] à laquelle la session de l'éditeur de requête est connectée.  
  
 **InstanceName**  
 Nom de l'instance du [!INCLUDE[ssDE](../../includes/ssde-md.md)] à laquelle la session de l'éditeur de requête est connectée.  
  
 **[SPID]**  
 ID de processus de session [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] qui identifie de façon unique cette session. Vous pouvez obtenir des informations supplémentaires sur la session en sélectionnant la ligne dans la vue sys.sysprocesses dont la valeur est la même dans la colonne spid.  
  
 **Emplacement**  
 Affiche le nom du fichier de script utilisé dans la session de l'éditeur de requête en cours de débogage.  
  
 **Priorité**  
 Le débogueur [!INCLUDE[tsql](../../includes/tsql-md.md)] ne prend pas en charge cette fonctionnalité.  
  
 **Suspendre**  
 Le débogueur [!INCLUDE[tsql](../../includes/tsql-md.md)] ne prend pas en charge cette fonctionnalité.  
  
## <a name="see-also"></a>Voir aussi  
 [Débogueur Transact-SQL](../../relational-databases/scripting/transact-sql-debugger.md)   
 [Informations du débogueur Transact-SQL](../../relational-databases/scripting/transact-sql-debugger-information.md)   
 [sys.dm_os_threads &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-os-threads-transact-sql.md)   
 [sys.sysprocesses &#40;Transact-SQL&#41;](../../relational-databases/system-compatibility-views/sys-sysprocesses-transact-sql.md)  

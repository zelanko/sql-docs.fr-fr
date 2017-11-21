---
title: MSSQLSERVER_9955 | Microsoft Docs
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
- 9955 (Database Engine error)
ms.assetid: 77f30570-7790-4747-b372-eac71c036e19
caps.latest.revision: 26
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.translationtype: Human Translation
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: 8c4d27af44152bb9b9816dbcdb0af7c75ea2f4db
ms.contentlocale: fr-fr
ms.lasthandoff: 06/22/2017

---
# <a name="mssqlserver9955"></a>MSSQLSERVER_9955
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  
## <a name="details"></a>Détails  
  
|||  
|-|-|  
|Nom du produit|SQL Server|  
|ID d'événement|9955|  
|Source de l'événement|MSSQLSERVER|  
|Composant|SQLEngine|  
|Nom symbolique|FTXT2_MSSEARCHACCESSDENY|  
|Texte du message|SQL Server n'a pas pu créer de canal nommé '%ls' pour communiquer avec le démon de filtre de texte intégral (erreur Windows : %d). Il existe déjà un canal nommé pour un processus hôte de démon de filtre, le système manque de ressources ou la recherche de numéro d'identification de sécurité (SID) du groupe de comptes du démon de filtre a échoué. Pour résoudre cette erreur, arrêtez les processus de démon de filtre de texte intégral en cours d'exécution et reconfigurez si nécessaire le compte de service du lanceur de démon de texte intégral.|  
  
## <a name="explanation"></a>Explication  
Ce message s'affiche parce que [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] n'a pas pu créer de canal nommé pour communiquer avec le démon de filtre de texte intégral. Il existe déjà un canal nommé pour un processus hôte de démon de filtre, le système manque de ressources ou la recherche de numéro d'identification de sécurité (SID) du groupe de comptes du démon de filtre a échoué.  
  
## <a name="user-action"></a>Action de l'utilisateur  
Pour résoudre cette erreur, arrêtez les processus de démon de filtre de texte intégral en cours d'exécution et reconfigurez si nécessaire le compte hôte du démon de texte intégral à l'aide du Gestionnaire de configuration SQL Server.  
  
## <a name="see-also"></a>Voir aussi  
[Gestionnaire de configuration SQL Server](~/relational-databases/sql-server-configuration-manager.md)  
[Définir le compte du service du Lanceur de démon de filtre de texte intégral](~/relational-databases/search/set-the-service-account-for-the-full-text-filter-daemon-launcher.md)  
[Recherche en texte intégral](~/relational-databases/search/full-text-search.md)  
  


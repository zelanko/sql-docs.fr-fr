---
title: MSSQLSERVER_9955 | Microsoft Docs
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 9955 (Database Engine error)
ms.assetid: 77f30570-7790-4747-b372-eac71c036e19
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: a092a7228f5ec70247e38cf39073d946de0e56ea
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48064039"
---
# <a name="mssqlserver9955"></a>MSSQLSERVER_9955
    
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
 [Gestionnaire de configuration SQL Server](../sql-server-configuration-manager.md)   
 [Définir le compte du service du Lanceur de démon de filtre de texte intégral](../search/set-the-service-account-for-the-full-text-filter-daemon-launcher.md)   
 [Recherche en texte intégral](../search/full-text-search.md)  
  
  

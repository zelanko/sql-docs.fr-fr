---
title: MSSQLSERVER_15517 | Microsoft Docs
ms.custom: ''
ms.date: 04/04/2017
ms.prod: sql
ms.prod_service: database-engine
ms.component: errors-events
ms.reviewer: ''
ms.suite: sql
ms.technology: supportability
ms.tgt_pltfrm: ''
ms.topic: language-reference
helpviewer_keywords:
- 15517 (Database Engine error)
ms.assetid: f94287f5-129f-4c52-9d34-62b996088001
caps.latest.revision: 5
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 8b08e71c58edf096a3ba07f12fdaa2972b1e3b32
ms.sourcegitcommit: f1caaa156db2b16e817e0a3884394e7b30fb642f
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
---
# <a name="mssqlserver15517"></a>MSSQLSERVER_15517
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  
## <a name="details"></a>Détails  
  
|||  
|-|-|  
|Nom du produit|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]|  
|ID d'événement|15517|  
|Source de l'événement|MSSQLSERVER|  
|Composant|SQLEngine|  
|Nom symbolique|SEC_CANNOTEXECUTEASUSER|  
|Texte du message|Exécution impossible en tant que principal de la base de données car le principal «*principal*» n’existe pas, ce type de principal n’autorise pas l’emprunt d’identité ou vous n’avez pas l’autorisation requise.|  
  
## <a name="user-action"></a>Action de l'utilisateur  
Utilisez le nom d'un principal existant ou obtenez l'autorisation IMPERSONATE sur ce principal.  
  
15517 peut également se produire après un attachement et une restauration de base de données par quelqu'un d'autre que le propriétaire d'origine de la base de données. Pour résoudre cette erreur, remplacez le db_owner par une connexion sur votre serveur, en exécutant la commande suivante :  
  
```  
ALTER AUTHORIZATION ON DATABASE:: DBName TO [NewLogin]  
```  
  
## <a name="see-also"></a> Voir aussi  
[OLTP en mémoire &#40;Optimisation en mémoire&#41;](~/relational-databases/in-memory-oltp/in-memory-oltp-in-memory-optimization.md)  
  

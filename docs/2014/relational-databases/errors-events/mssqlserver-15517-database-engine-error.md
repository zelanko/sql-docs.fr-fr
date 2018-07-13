---
title: MSSQLSERVER_15517 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: supportability
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- 15517 (Database Engine error)
ms.assetid: f94287f5-129f-4c52-9d34-62b996088001
caps.latest.revision: 5
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: ebbc87a299cb55658c7a8506fa4a63a2e2d1d215
ms.sourcegitcommit: f8ce92a2f935616339965d140e00298b1f8355d7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/03/2018
ms.locfileid: "37426468"
---
# <a name="mssqlserver15517"></a>MSSQLSERVER_15517
    
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
  
## <a name="see-also"></a>Voir aussi  
 [OLTP en mémoire &#40;Optimisation en mémoire&#41;](../in-memory-oltp/in-memory-oltp-in-memory-optimization.md)  
  
  

---
title: Catalog.Startup | Documents Microsoft
ms.custom:
- SQL2016_New_Updated
ms.date: 03/04/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: language-reference
ms.assetid: 271fd405-246a-4852-bfbe-f557241ce6ea
caps.latest.revision: 9
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: 3a8c89be0541be1861f45240b891d349019a8935
ms.contentlocale: fr-fr
ms.lasthandoff: 09/26/2017

---
# <a name="catalogstartup"></a>catalog.startup
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx_md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  Effectue la maintenance de l'état des opérations pour le catalogue SSISDB.  
  
 La procédure stockée résout l'état de tous les packages et cours d'exécution si et quand l'instance de serveur [!INCLUDE[ssIS](../../includes/ssis-md.md)] s'arrête.  
  
 Vous avez la possibilité de l’activation de la procédure stockée exécutée automatiquement chaque fois le [!INCLUDE[ssIS](../../includes/ssis-md.md)] instance de serveur est redémarrée, en sélectionnant le **l’exécution automatique d’activer des Services d’intégration de procédures stockées au démarrage de SQL Server** option dans le **créer un catalogue** boîte de dialogue.  
  
## <a name="syntax"></a>Syntaxe  
  
```tsql  
Catalog.startup  
```  
  
## <a name="return-code-value"></a>Valeur de Code de retour  
 0 (succès)  
  
## <a name="result-sets"></a>Jeux de résultats  
 Aucune  
  
## <a name="permissions"></a>Permissions  
 Cette procédure stockée requiert l'une des autorisations suivantes :  
  
-   Autorisations READ et MODIFY sur l'instance d'exécution, autorisations READ et EXECUTE sur le projet, et si applicable, autorisations READ sur l'environnement référencé  
  
-   L’appartenance à la **ssis_admin** rôle de base de données  
  
-   L’appartenance à la **sysadmin** rôle de serveur  
  
  

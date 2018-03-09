---
title: catalog.startup | Microsoft Docs
ms.custom: 
ms.date: 03/04/2017
ms.prod: sql-non-specified
ms.prod_service: integration-services
ms.service: 
ms.component: system-stored-procedures
ms.reviewer: 
ms.suite: sql
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: language-reference
ms.assetid: 271fd405-246a-4852-bfbe-f557241ce6ea
caps.latest.revision: 
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: f09c60f9f9a84e88a5198c49b1a7cbfcee16bc12
ms.sourcegitcommit: 9e6a029456f4a8daddb396bc45d7874a43a47b45
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/25/2018
---
# <a name="catalogstartup"></a>catalog.startup
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  Effectue la maintenance de l'état des opérations pour le catalogue SSISDB.  
  
 La procédure stockée résout l'état de tous les packages et cours d'exécution si et quand l'instance de serveur [!INCLUDE[ssIS](../../includes/ssis-md.md)] s'arrête.  
  
 Vous avez la possibilité d’exécuter automatiquement la procédure stockée chaque fois que l’instance de serveur [!INCLUDE[ssIS](../../includes/ssis-md.md)] est redémarrée ; sélectionnez l’option **Activer l’exécution automatique des procédures stockées Integration Services au démarrage de SQL Server** dans la boîte de dialogue **Créer un catalogue**.  
  
## <a name="syntax"></a>Syntaxe  
  
```sql  
catalog.startup  
```  
  
## <a name="return-code-value"></a>Valeur du code de retour  
 0 (succès)  
  
## <a name="result-sets"></a>Jeux de résultats  
 None  
  
## <a name="permissions"></a>Autorisations  
 Cette procédure stockée requiert l'une des autorisations suivantes :  
  
-   Autorisations READ et MODIFY sur l'instance d'exécution, autorisations READ et EXECUTE sur le projet, et si applicable, autorisations READ sur l'environnement référencé  
  
-   Appartenance au rôle de base de données **ssis_admin**  
  
-   Appartenance au rôle serveur **sysadmin**  
  
  

---
title: catalog.startup | Microsoft Docs
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: language-reference
ms.assetid: 271fd405-246a-4852-bfbe-f557241ce6ea
author: chugugrace
ms.author: chugu
ms.openlocfilehash: fdb3a128753ca5e6be23eadf1c0b4fb91e9654c4
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85674214"
---
# <a name="catalogstartup"></a>catalog.startup 

[!INCLUDE[ssis-appliesto](../../includes/ssis-appliesto-ssvrpluslinux-asdb-asdw-xxx.md)]


[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

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
  
  

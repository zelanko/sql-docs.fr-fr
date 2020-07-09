---
title: Configurer des paramètres de collecte de données (T-SQL)
ms.date: 06/03/2020
ms.prod: sql
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- data collection [SQL Server]
ms.assetid: 850905b6-35d2-4ed1-ab51-de64daa832b2
author: MashaMSFT
ms.author: mathoma
ms.custom: seo-lt-2019
ms.openlocfilehash: 47d18830d262bc817061aa3637cc3a4871accfd3
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85733892"
---
# <a name="configure-data-collection-parameters-transact-sql"></a>Configurer des paramètres de collecte de données (Transact-SQL)
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]
  Avant de créer un jeu d'éléments de collecte personnalisé, vous devez d'abord configurer des paramètres de collecte de données. Pour cela, vous devez vous servir des procédures stockées fournies avec le collecteur de données. L’utilisation de l'éditeur de requêtes dans [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] est nécessaire pour effectuer la procédure suivante.  
  
> [!NOTE]  
>  Vous ne configurez des paramètres de collecte de données qu'une seule fois. Lorsque la configuration est terminée, ces paramètres servent pour tous les jeux d'éléments de collecte supplémentaires que vous créez.  
  
### <a name="configure-data-collection-parameters"></a>Configurer des paramètres de collecte de données  
  
1.  Dans [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], connectez-vous à la base de données dans laquelle vous souhaitez créer un jeu d'éléments de collecte personnalisé.  
  
2.  Dans l'éditeur de requêtes, émettez les instructions suivantes.  

    ```sql  
    USE msdb;  
    EXEC sp_syscollector_set_warehouse_instance_name N'INSTANCE_NAME';-- where instance name is the name of the SQL Server instance  
    EXEC sp_syscollector_set_warehouse_database_name N'MDW';  
    EXEC sp_syscollector_set_cache_directory N'D:\tempdata';  
    ```  
  
## <a name="see-also"></a>Voir aussi  
 [Collecte de données](../../relational-databases/data-collection/data-collection.md)   
 [Procédures stockées du collecteur de données &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/data-collector-stored-procedures-transact-sql.md)  
  
  

---
title: Configurer des paramètres de collecte de données (T-SQL)
ms.custom: seo-lt-2019
ms.date: 03/04/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- data collection [SQL Server]
ms.assetid: 850905b6-35d2-4ed1-ab51-de64daa832b2
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: b7d8d45273fc9ac79a5dd65cfb168868e76f55cd
ms.sourcegitcommit: b2e81cb349eecacee91cd3766410ffb3677ad7e2
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/01/2020
ms.locfileid: "74056460"
---
# <a name="configure-data-collection-parameters-transact-sql"></a>Configurer des paramètres de collecte de données (Transact-SQL)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
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
  
  

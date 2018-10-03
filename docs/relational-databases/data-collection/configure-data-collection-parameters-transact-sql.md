---
title: Configurer des paramètres de collecte de données (Transact-SQL) | Microsoft Docs
ms.custom: ''
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
manager: craigg
ms.openlocfilehash: 98a599a60acd29ad99a515020da88c78faf21062
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47721687"
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
  
## <a name="see-also"></a> Voir aussi  
 [Collecte de données](../../relational-databases/data-collection/data-collection.md)   
 [Procédures stockées du collecteur de données &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/data-collector-stored-procedures-transact-sql.md)  
  
  

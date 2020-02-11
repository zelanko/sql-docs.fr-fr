---
title: Les fonctions définies par l’utilisateur ne sont pas autorisées dans system_function_schema | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- system functions [SQL Server]
- user-defined functions [SQL Server], system
ms.assetid: 3cb54053-ef65-4558-ae96-8686b6b22f4f
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 10813b7bc0a97f0ba8a81f3f48447142659cd596
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "66091330"
---
# <a name="user-defined-functions-are-not-allowed-in-system_function_schema"></a>Les fonctions définies par l'utilisateur ne sont pas autorisées dans system_function_schema
  Le conseiller de mise à niveau a détecté des fonctions définies par l’utilisateur qui sont détenues par l’utilisateur **system_function_schema**non documenté. Vous ne pouvez pas créer une fonction système définie par l'utilisateur en spécifiant cet utilisateur. Le nom d’utilisateur **system_function_schema** n’existe pas et l’ID d’utilisateur associé à ce nom (UID = 4) est réservé au schéma **sys** et est réservé à un usage interne uniquement.  
  
## <a name="component"></a>Composant  
 [!INCLUDE[ssDE](../../includes/ssde-md.md)]  
  
## <a name="description"></a>Description  
 Le stockage et l'accès des objets système ont été modifiés comme suit :  
  
-   Les objets système sont stockés dans la base de données de **ressources** en lecture seule et les mises à jour directes des objets système ne sont pas autorisées.  
  
     Les objets système apparaissent logiquement dans le schéma **sys** de chaque base de données. Il est donc toujours possible d'appeler des fonctions système à partir de n'importe quelle base de données en spécifiant un nom de fonction en une seule partie. Par exemple, l'instruction `SELECT * FROM fn_helpcollations()` peut être exécutée à partir de n'importe quelle base de données.  
  
-   L’utilisateur **system_function_schema** non documenté a été supprimé.  
  
-   L’ID d’utilisateur associé à **system_function_schema** (UID = 4) est réservé au schéma **sys** et est limité à un usage interne uniquement.  
  
 Ces modifications ont l'effet suivant sur les fonctions système définies par l'utilisateur :  
  
-   Les instructions DDL (Data Definition Language) qui référencent **system_function_schema** échouent. Par exemple, l’instruction `CREATE FUNCTION system`_`function` \_ `schema.fn` \_ `MySystemFunction` ... ne fonctionnera pas.  
  
-   Après la mise à [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]niveau vers, les objets existants appartenant à **system_function_schema** sont contenus uniquement dans le schéma **sys** de la base de données **Master** . Étant donné que les objets système ne peuvent pas être modifiés, ces fonctions ne peuvent jamais être modifiées ou supprimées de la base de données **Master** . En outre, il est impossible d'appeler ces fonctions à partir d'autres bases de données en spécifiant uniquement un nom de fonction en une seule partie.  
  
## <a name="corrective-action"></a>Action corrective  
 Avant de procéder à la mise à niveau, effectuez les tâches suivantes :  
  
1.  Modifiez la propriété des fonctions définies par l’utilisateur existantes en **dbo** à l’aide de la procédure stockée système **sp_changeobjectowner** .  
  
2.  Vous pouvez renommer la fonction de manière à ce que son nom ne comporte pas le préfixe 'fn_'. Cela évitera d'éventuels conflits de noms avec des fonctions système actuelles ou futures.  
  
3.  Ajoutez une copie des fonctions modifiées dans chaque base de données qui les utilise.  
  
4.  Remplacez les références à **system_function_schema** par **dbo** dans tous les scripts qui contiennent des instructions DDL de fonction définie par l’utilisateur.  
  
5.  Modifiez les scripts qui appellent ces fonctions pour utiliser le nom en deux parties dbo **.** _function_name_, ou le nom en trois parties _database_name_**.** dbo. *function_name*.  
  
 Pour plus d'informations, consultez les rubriques suivantes dans la documentation en ligne de SQL Server :  
  
-   « sp_changeobjectowner »  
  
-   « Séparation du schéma et de l'utilisateur »  
  
-   « Base de données Resource »  
  
## <a name="see-also"></a>Voir aussi  
 [Le conseiller de mise à niveau de SQL Server 2014 &#91;nouveau&#93;](sql-server-2014-upgrade-advisor.md)   
 [Problèmes de mise à niveau Moteur de base de données](../../../2014/sql-server/install/database-engine-upgrade-issues.md)   
 [Supprimer les instructions qui modifient les objets système](../../../2014/sql-server/install/remove-statements-that-modify-system-objects.md)   
 [Supprimer les instructions qui suppriment des objets système](../../../2014/sql-server/install/remove-statements-that-drop-system-objects.md)  
  
  

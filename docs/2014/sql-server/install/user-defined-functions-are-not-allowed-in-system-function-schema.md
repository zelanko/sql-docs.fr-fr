---
title: Fonctions définies par l’utilisateur ne sont pas autorisées dans system_function_schema | Microsoft Docs
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
ms.sourcegitcommit: f40fa47619512a9a9c3e3258fda3242c76c008e6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/23/2019
ms.locfileid: "66091330"
---
# <a name="user-defined-functions-are-not-allowed-in-systemfunctionschema"></a>Les fonctions définies par l'utilisateur ne sont pas autorisées dans system_function_schema
  Le Conseiller de mise à niveau a détecté des fonctions définies par l’utilisateur qui sont détenues par l’utilisateur non documenté **system_function_schema**. Vous ne pouvez pas créer une fonction système définie par l'utilisateur en spécifiant cet utilisateur. Le **system_function_schema** nom d’utilisateur n’existe pas, et l’ID d’utilisateur qui est associé à ce nom (UID = 4) est réservé pour le **sys** schéma et est limité à un usage interne uniquement.  
  
## <a name="component"></a>Composant  
 [!INCLUDE[ssDE](../../includes/ssde-md.md)]  
  
## <a name="description"></a>Description  
 Le stockage et l'accès des objets système ont été modifiés comme suit :  
  
-   Objets système sont stockés en lecture seule **ressources** de base de données et diriger les mises à jour des objets système ne sont pas autorisées.  
  
     Objets système apparaissent logiquement dans le **sys** schéma de chaque base de données. Il est donc toujours possible d'appeler des fonctions système à partir de n'importe quelle base de données en spécifiant un nom de fonction en une seule partie. Par exemple, l'instruction `SELECT * FROM fn_helpcollations()` peut être exécutée à partir de n'importe quelle base de données.  
  
-   L’utilisateur non documenté **system_function_schema** a été supprimé.  
  
-   L’utilisateur associé à un ID **system_function_schema** (UID = 4) est réservé pour le **sys** schéma et est limité à un usage interne uniquement.  
  
 Ces modifications ont l'effet suivant sur les fonctions système définies par l'utilisateur :  
  
-   Les instructions de langage de définition (DDL) de données qui font référence à **system_function_schema** échouera. Par exemple, l’instruction `CREATE FUNCTION system`_`function` \_ `schema.fn` \_ `MySystemFunction` ... ne réussira pas.  
  
-   Une fois que vous mettez à niveau vers [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)], les objets existants qui sont détenus par **system_function_schema** sont contenus uniquement dans le **sys** schéma de la **master** base de données. Étant donné que les objets système ne peut pas être modifiés, ces fonctions jamais peuvent être modifiées ou supprimées de la **master** base de données. En outre, il est impossible d'appeler ces fonctions à partir d'autres bases de données en spécifiant uniquement un nom de fonction en une seule partie.  
  
## <a name="corrective-action"></a>Action corrective  
 Avant de procéder à la mise à niveau, effectuez les tâches suivantes :  
  
1.  Modifier la propriété des fonctions définies par l’utilisateur existantes à **dbo** à l’aide de la **sp_changeobjectowner** procédure stockée système.  
  
2.  Vous pouvez renommer la fonction de manière à ce que son nom ne comporte pas le préfixe 'fn_'. Cela évitera d'éventuels conflits de noms avec des fonctions système actuelles ou futures.  
  
3.  Ajoutez une copie des fonctions modifiées dans chaque base de données qui les utilise.  
  
4.  Remplacez les références à **system_function_schema** avec **dbo** dans tous les scripts qui contiennent des instructions DDL de fonctions définies par l’utilisateur.  
  
5.  Modifiez les scripts qui appellent ces fonctions pour l’utilisation des dbo de nom en deux parties **.** _function_name_, ou le nom en trois parties _database_name_**.** dbo. *nom_fonction*.  
  
 Pour plus d'informations, consultez les rubriques suivantes dans la documentation en ligne de SQL Server :  
  
-   « sp_changeobjectowner »  
  
-   « Séparation du schéma et de l'utilisateur »  
  
-   « Base de données Resource »  
  
## <a name="see-also"></a>Voir aussi  
 [Conseiller de mise à niveau de SQL Server 2014 &#91;nouveau&#93;](sql-server-2014-upgrade-advisor.md)   
 [Problèmes de mise à niveau du moteur de base de données](../../../2014/sql-server/install/database-engine-upgrade-issues.md)   
 [Supprimer les instructions qui modifient les objets système](../../../2014/sql-server/install/remove-statements-that-modify-system-objects.md)   
 [Supprimer les instructions qui suppriment des objets système](../../../2014/sql-server/install/remove-statements-that-drop-system-objects.md)  
  
  

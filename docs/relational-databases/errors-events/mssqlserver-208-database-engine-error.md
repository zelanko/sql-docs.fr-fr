---
title: MSSQLSERVER_208 | Microsoft Docs
ms.custom: 
ms.date: 04/04/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: errors-events
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
helpviewer_keywords:
- 208 (Database Engine error)
ms.assetid: 4b1895f5-3197-4da1-af86-954c93507956
caps.latest.revision: 13
author: edmacauley
ms.author: edmaca
manager: cguyer
ms.workload: Inactive
ms.translationtype: Human Translation
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: 1d2936b044341cbd2ccaaf8955c351524ea83396
ms.contentlocale: fr-fr
ms.lasthandoff: 06/22/2017

---
# <a name="mssqlserver208"></a>MSSQLSERVER_208
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  
## <a name="details"></a>Détails  
  
|||  
|-|-|  
|Nom du produit|SQL Server|  
|ID d'événement|208|  
|Source de l'événement|MSSQLSERVER|  
|Composant|SQLEngine|  
|Nom symbolique|SQ_BADOBJECT|  
|Texte du message|Nom d'objet '%.*ls' non valide.|  
  
## <a name="explanation"></a>Explication  
L'objet spécifié reste introuvable.  
  
### <a name="possible-causes"></a>Causes possibles  
Cette erreur peut être causée par l'un des problèmes suivants :  
  
-   L'objet n'est pas correctement spécifié.  
  
-   L'objet n'existe pas dans la base de données actuelle ou dans la base de données spécifiée.  
  
-   L'objet existe, mais n'a pas pu être exposé à l'utilisateur. Par exemple, l'utilisateur n'a pas d'autorisations sur l'objet ou l'objet est créé dans une instruction EXECUTE, mais l'accès à cet objet s'effectue en dehors de la portée de l'instruction EXECUTE.  
  
## <a name="user-action"></a>Action de l'utilisateur  
Vérifiez les informations suivantes et corrigez l'instruction comme il convient.  
  
-   Le nom de l'objet est correctement orthographié.  
  
-   Le contexte de la base de données actuelle est correct. Si aucun nom de base de données n'est spécifié pour l'objet, celui-ci doit exister dans la base de données actuelle. Pour plus d’informations sur la définition du contexte de la base de données, consultez [USE &#40;Transact-SQL&#41;](~/t-sql/language-elements/use-transact-sql.md).  
  
-   L'objet existe dans les tables système. Pour vérifier s’il existe une table ou un autre objet étendu aux schémas, interrogez la vue de catalogue **sys.objects**. Si l'objet ne se trouve pas dans les tables système, cela signifie qu'il a été supprimé ou que l'utilisateur ne dispose pas d'autorisations pour afficher les métadonnées de l'objet. Pour plus d’informations sur les autorisations d’affichage des métadonnées d’objet, consultez [Configuration de la visibilité des métadonnées](~/relational-databases/security/metadata-visibility-configuration.md).  
  
-   L'objet est contenu dans le schéma par défaut de l'utilisateur. Si ce n’est pas le cas, l’objet doit être spécifié en respectant le format en deux parties *nom_schéma.nom_objet*. Notez que les fonctions scalaires doivent toujours être appelées à l'aide, au moins, du nom en deux parties.  
  
-   Respect de la casse du classement de base de données.  
  
    Lorsqu'une base de données utilise un classement respectant la casse, la casse du nom de l'objet doit être identique à celle qui est utilisée dans la base de données. Par exemple, quand un objet est spécifié en tant que **MyTable** dans une base de données avec un classement respectant la casse, les requêtes qui font référence à l’objet en tant que **mytable** ou **Mytable** retournent l’erreur 208, car les noms de l’objet ne correspondent pas.  
  
    Vous pouvez vérifier le classement de base de données en exécutant l'instruction suivante :  
  
    ```  
    SELECT collation_name FROM sys.databases WHERE name = 'database_name';  
    ```  
  
    L'abréviation CS dans le nom du classement indique que celui-ci respecte la casse. Par exemple, Latin1_General_CS_AS indique un classement qui respecte la casse et les accents. CI indique un classement qui ne respecte pas la casse.  
  
-   L'utilisateur a l'autorisation d'accéder à l'objet. Pour vérifier les autorisations de l’utilisateur sur l’objet, utilisez la fonction système **Has_Perms_By_Name**.  
  
## <a name="see-also"></a>Voir aussi  
[USE &#40;Transact-SQL&#41;](~/t-sql/language-elements/use-transact-sql.md)  
[Configuration de la visibilité des métadonnées](~/relational-databases/security/metadata-visibility-configuration.md)  
[HAS_PERMS_BY_NAME &#40;Transact-SQL&#41;](~/t-sql/functions/has-perms-by-name-transact-sql.md)  
  


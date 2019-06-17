---
title: Restrictions des fonctionnalités | Microsoft Docs
ms.custom: ''
ms.date: 01/09/2019
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
author: vainolo
ms.author: arib
manager: tomerw
monikerRange: '>= sql-server-ver15 || = sqlallproducts-allversions'
ms.openlocfilehash: 99a0a768334ab5335591fae69e4f18060fba9866
ms.sourcegitcommit: 561cee96844b82ade6cf543a228028ad5c310768
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2019
ms.locfileid: "66506917"
---
# <a name="feature-restrictions"></a>Restrictions liées aux fonctionnalités

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

Une source courante d’attaques SQL Server est liée aux applications web qui accèdent à la base de données où diverses formes d’attaques par injection SQL sont utilisées pour glaner des informations sur la base de données.  Dans l’idéal, le code d’application est développé afin de ne pas autoriser l’injection SQL.  Toutefois, dans les bases de code volumineuses qui incluent du code hérité et externe, on ne peut jamais être sûr que tous les cas ont été traités. Les injections SQL sont par conséquent une réalité contre laquelle nous devons nous protéger.  Les restrictions de fonctionnalités visent à empêcher que certaines formes d’injection SQL ne provoquent la fuite d’informations sur la base de données, même quand l’injection SQL réussit.

## <a name="enabling-feature-restrictions"></a>Activation des restrictions de fonctionnalités

L’activation des restrictions de fonctionnalités s’effectue à l’aide de la procédure stockée `sp_add_feature_restriction` comme suit :

```sql
EXEC sp_add_feature_restriction <feature>, <object_class>, <object_name>
```

Les fonctionnalités suivantes peuvent être restreintes :

| Fonctionnalité          | Description |
|------------------|-------------|
| N’ErrorMessages’ | En cas de restriction, toutes les données utilisateur dans le message d’erreur sont masquées. Consultez [Restriction des fonctionnalités de messages d’erreur](#error-messages-feature-restriction). |
| N’Waitfor’       | En cas de restriction, la commande retourne immédiatement sans délai. Consultez [Restriction de fonctionnalité WAITFOR](#waitfor-feature-restriction). |

La valeur de `object_class` peut être `N'User'` ou `N'Role'` pour indiquer si `object_name` est un nom d’utilisateur ou un nom de rôle dans la base de données.

L’exemple suivant entraîne le masquage de tous les messages d’erreur pour l’utilisateur `MyUser` :

```sql
EXEC sp_add_feature_restriction N'ErrorMessages', N'User', N'MyUser'
```

## <a name="disabling-feature-restrictions"></a>Désactivation des restrictions de fonctionnalités

La désactivation des restrictions de fonctionnalités s’effectue à l’aide de la procédure stockée `sp_drop_feature_restriction` comme suit :

```sql
EXEC sp_drop_feature_restriction <feature>, <object_class>, <object_name>
```

L’exemple suivant désactive le masquage des messages d’erreur pour l’utilisateur `MyUser` :

```sql
EXEC sp_drop_feature_restriction N'ErrorMessages', N'User', N'MyUser'
```

## <a name="viewing-feature-restrictions"></a>Affichage des restrictions de fonctionnalités

La vue `sys.sql_feature_restrictions` affiche toutes les restrictions de fonctionnalités actuellement définies sur la base de données. Pour obtenir des informations relatives au mode, consultez [sys.sql_feature_restrictions](../system-catalog-views/sys-sql-feature-restrictions.md).

## <a name="feature-restrictions"></a>Restrictions liées aux fonctionnalités

### <a name="error-messages-feature-restriction"></a>Restriction des fonctionnalités de messages erreur

Une méthode attaque par injection SQL courante consiste à injecter du code qui provoque une erreur.  En examinant le message d’erreur, un attaquant peut obtenir des informations sur le système, et ainsi déclencher d’autres attaques plus ciblées.  Cette attaque peut être particulièrement efficace quand l’application n’affiche pas les résultats d’une requête, mais affiche les messages d’erreur.

Considérez une application web ayant une requête du type :

```html
http://www.contoso.com/employee.php?id=1
```

Qui exécute la requête de base de données suivante :

```sql
SELECT Name FROM EMPLOYEES WHERE Id=$EmpId
```

Si la valeur passée en tant que paramètre `Id` à la requête d’application web est copiée pour remplacer $EmpId dans la requête de base de données, un attaquant pourrait effectuer la requête suivante :

```html
http://www.contoso.com/employee.php?id=1 AND CAST(DB_NAME() AS INT)=0
```

Et l’erreur suivante serait retournée, permettant à l’attaquant de connaître le nom de la base de données :

```sql
Conversion failed when converting the nvarchar value 'HR_Data' to data type int.
```

Après l’activation des restrictions de fonctionnalités de messages d’erreur pour l’utilisateur de l’application dans la base de données, le message d’erreur retourné est masqué afin qu’aucune information interne sur la base de données ne soit divulguée :

```sql
Conversion failed when converting the ****** value '******' to data type ******.
```

De même, l’attaquant pourrait effectuer la requête suivante :

```html
http://www.contoso.com/employee.php?id=1 AND CAST(Salary AS TINYINT)=0
```

Et l’erreur suivante serait retournée, permettant à l’attaquant de connaître le salaire de l’employé :

```sql
Arithmetic overflow error for data type tinyint, value = 140000.
```

Si vous utilisez la restriction des fonctionnalités de messages erreur, la base de données retournera :

```sql
Arithmetic overflow error for data type ******, value = ******.
```

### <a name="waitfor-feature-restriction"></a>Restriction de fonctionnalité WAITFOR

Une injection de code SQL aveugle se produit quand une application ne fournit pas à un attaquant les résultats de l’instruction SQL injectée ou un message d’erreur, mais que l’attaquant peut déduire des informations sur la base de données en créant une requête conditionnelle dans laquelle les deux branches conditionnelles nécessitent une durée d’exécution différente. En comparant le temps de réponse, l’attaquant peut savoir quelle branche a été exécutée et obtenir ainsi des informations sur le système. La variante la plus simple de cette attaque consiste à utiliser l’instruction `WAITFOR` pour introduire le délai.

Considérez une application web ayant une requête du type :

```html
http://www.contoso.com/employee.php?id=1
```

qui exécute la requête de base de données suivante :

```sql
SELECT Name FROM EMPLOYEES WHERE Id=$EmpId
```

Si la valeur passée en tant que paramètre `Id` aux requêtes d’application web est copiée pour remplacer $EmpId dans la requête de base de données, un attaquant peut effectuer la requête suivante :

```html
http://www.contoso.com/employee.php?id=1; IF SYSTEM_USER='sa' WAITFOR DELAY '00:00:05'
```

Et la requête prendrait cinq secondes supplémentaires si le compte `sa` était utilisé. Si vous utilisez la restriction de fonctionnalité `WAITFOR` dans la base de données, l’instruction `WAITFOR` est ignorée et aucune fuite d’information ne se produit suite à cette attaque.

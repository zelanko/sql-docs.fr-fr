---
title: DROP WORKLOAD GROUP (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2019
ms.prod: sql
ms.prod_service: sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- DROP_WORKLOAD_GROUP_TSQL
- DROP WORKLOAD GROUP
dev_langs:
- TSQL
helpviewer_keywords:
- DROP WORKLOAD GROUP statement
author: CarlRabeler
ms.author: carlrab
monikerRange: '>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azure-sqldw-latest||=azuresqldb-mi-current'
ms.openlocfilehash: 90622710b19ef3c2692cdcff62089cb7539fcf97
ms.sourcegitcommit: 66dbc3b740f4174f3364ba6b68bc8df1e941050f
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/05/2019
ms.locfileid: "73632808"
---
# <a name="drop-workload-group-transact-sql"></a>DROP WORKLOAD GROUP (Transact-SQL)

## <a name="click-a-product"></a>Cliquez sur un produit !

Dans la ligne suivante, cliquez sur le nom du produit qui vous intéresse. Le clic affiche un contenu différent ici dans cette page web, approprié pour le produit sur lequel vous cliquez.

::: moniker range=">=sql-server-2016||>=sql-server-linux-2017||=azuresqldb-mi-current||=sqlallproducts-allversions"

> |||||
> |---|---|---|---|
> |**\* _SQL Server \*_** &nbsp;|[Instance managée<br />SQL Database](drop-workload-group-transact-sql.md?view=azuresqldb-mi-current)|[SQL Data<br />Warehouse](drop-workload-group-transact-sql.md?view=azure-sqldw-latest)|

&nbsp;

## <a name="sql-server-and-sql-database-managed-instance"></a>SQL Server et instance managée SQL Database


  Supprime un groupe de charges de travail du gouverneur de ressources défini par l'utilisateur existant.  
  
 ![Icône Lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône Lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
DROP WORKLOAD GROUP group_name  
[;]  
```  
  
## <a name="arguments"></a>Arguments  
 *group_name*  
 Nom d'un groupe de charges de travail défini par l'utilisateur existant.  
  
## <a name="remarks"></a>Notes  
 L'instruction DROP WORKLOAD GROUP n'est pas autorisée sur les groupes interne ou par défaut du gouverneur de ressources.  
  
 Lorsque vous exécutez des instructions DDL, nous vous recommandons de connaître les états du gouverneur de ressources. Pour plus d’informations, consultez [Resource Governor](../../relational-databases/resource-governor/resource-governor.md).  
  
 Si un groupe de charges de travail contient des sessions actives, sa suppression ou son déplacement vers un pool de ressources différent échoue lorsque l'instruction ALTER RESOURCE GOVERNOR RECONFIGURE est appelée pour appliquer la modification. Pour éviter ce problème, vous pouvez suivre l'une des actions suivantes :  
  
-   Attendez la déconnexion de toutes les sessions du groupe affecté, puis réexécutez l'instruction ALTER RESOURCE GOVERNOR RECONFIGURE.  
  
-   Arrêtez explicitement les sessions du groupe affecté à l'aide de la commande KILL, puis réexécutez l'instruction ALTER RESOURCE GOVERNOR RECONFIGURE.  
  
-   Redémarrez le serveur. Au terme du processus de redémarrage, le groupe supprimé ne sera pas créé, et un groupe déplacé utilisera la nouvelle affectation de pool de ressources.  
  
-   Dans un scénario dans lequel vous publiez l'instruction DROP WORKLOAD GROUP mais décidez que vous ne souhaitez pas arrêter explicitement des sessions pour appliquer la modification, vous pouvez recréer le groupe en utilisant le nom qu'il portait avant l'émission de l'instruction DROP, puis déplacer le groupe dans le pool de ressources d'origine. Pour appliquer les modifications, exécutez l'instruction ALTER RESOURCE GOVERNOR RECONFIGURE.  
  
## <a name="permissions"></a>Autorisations

 Requiert l'autorisation CONTROL SERVER.  
  
## <a name="examples"></a>Exemples

 L'exemple suivant supprime le groupe de charges de travail nommé `adhoc`.  
  
```  
DROP WORKLOAD GROUP adhoc;  
GO  
ALTER RESOURCE GOVERNOR RECONFIGURE;  
GO  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Resource Governor](../../relational-databases/resource-governor/resource-governor.md)   
 [CREATE WORKLOAD GROUP &#40;Transact-SQL&#41;](../../t-sql/statements/create-workload-group-transact-sql.md)   
 [ALTER WORKLOAD GROUP &#40;Transact-SQL&#41;](../../t-sql/statements/alter-workload-group-transact-sql.md)   
 [CREATE RESOURCE POOL &#40;Transact-SQL&#41;](../../t-sql/statements/create-resource-pool-transact-sql.md)   
 [ALTER RESOURCE POOL &#40;Transact-SQL&#41;](../../t-sql/statements/alter-resource-pool-transact-sql.md)   
 [DROP RESOURCE POOL &#40;Transact-SQL&#41;](../../t-sql/statements/drop-resource-pool-transact-sql.md)   
 [ALTER RESOURCE GOVERNOR &#40;Transact-SQL&#41;](../../t-sql/statements/alter-resource-governor-transact-sql.md)  
  
::: moniker-end
::: moniker range="=azure-sqldw-latest||=sqlallproducts-allversions"

> ||||
> |---|---|---|
> |[SQL Server](drop-workload-group-transact-sql.md?view=sql-server-2017)||[Instance managée<br />SQL Database](drop-workload-group-transact-sql.md?view=azuresqldb-mi-current)||**_\* SQL Data<br />Warehouse \*_** &nbsp;||||

&nbsp;

## <a name="sql-data-warehouse-preview"></a>SQL Data Warehouse (préversion)

Supprime un groupe de charge de travail.  Une fois l’instruction exécutée, les paramètres sont activés.

 ![Icône Lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône Lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md).

## <a name="syntax"></a>Syntaxe

```
DROP WORKLOAD GROUP group_name  
```

## <a name="arguments"></a>Arguments

 *group_name*  
 Nom d'un groupe de charges de travail défini par l'utilisateur existant.

## <a name="remarks"></a>Notes

Un groupe de charge de travail ne peut pas être supprimé si des classifieurs ont été définis pour lui.  Vous devez supprimer les classifieurs existants avant de supprimer le groupe de charge de travail.  Si des requêtes actives utilisant des ressources du groupe de charge de travail sont supprimées, l’instruction de suppression du groupe de charge de travail est bloquée.

## <a name="examples"></a>Exemples

Utilisez l’exemple de code suivant pour déterminer quels classifieurs doivent être supprimés avant que le groupe de charge de travail puisse être supprimé.

```sql
SELECT c.name as classifier_name
      ,'DROP WORKLOAD CLASSIFIER '+c.name as drop_command
  FROM sys.workload_management_workload_classifiers c
  JOIN sys.workload_management_workload_groups g
    ON c.group_name = g.name
  WHERE g.name = 'wgXYZ' --change the filter to the workload being dropped
```

## <a name="permissions"></a>Autorisations

Requiert l’autorisation CONTROL DATABASE

## <a name="see-also"></a>Voir aussi
 [CREATE WORKLOAD GROUP &#40;Transact-SQL&#41;](../../t-sql/statements/create-workload-group-transact-sql.md)   
 
::: moniker-end

---
ms.openlocfilehash: 78b372942de6ec62823dddecd08fdb7221cbe7a8
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "68219687"
---


### <a name="index-stats-options"></a>Options de statistiques d’index

<!--
This includes/paragraph-content/ file was created when processing vsts sqlbuvsts01 2999014 (5589131).  genemi  2017-07-21

Initially used in:
- relational-databases/maintenance-plans/rebuild-index-task-maintenance-plan.md
- relational-databases/maintenance-plans/reorganize-index-task-maintenance-plan.md
-->


Dans les versions antérieures de Microsoft SQL Server, réorganiser ou reconstruire un index de grande taille pouvait occasionner un ralentissement du système. SQL Server 2016 a apporté des améliorations de performances majeures à ces opérations d’index.

En outre, dans les versions antérieures, la granularité du contrôle était moins perfectionnée. Il provoquait la réorganisation ou la reconstruction de certains index par le système, même lorsqu’ils n’étaient pas très fragmentés, ce qui était source de gaspillage. Les derniers contrôles de l’interface utilisateur (IU) du Plan de maintenance permettent d’exclure les index qui n’ont pas besoin d’être actualisés, selon des critères de statistiques d’index. Pour cela, les vues de gestion dynamique (DMV) suivantes de Transact-SQL sont utilisées en interne :


- [sys.dm_db_index_usage_stats](../../relational-databases/system-dynamic-management-views/sys-dm-db-index-usage-stats-transact-sql.md)
- [sys.dm_db_index_physical_stats](../../relational-databases/system-dynamic-management-views/sys-dm-db-index-physical-stats-transact-sql.md)


 **Type d'analyse**  
 Le système doit consommer des ressources pour collecter des statistiques d’index. Vous pouvez choisir entre consommer relativement plus ou moins de ressources, en fonction du degré de précision que vous estimez nécessaire pour les statistiques d’index. L’IU propose la liste suivante de niveaux de précision, parmi lesquels vous pouvez faire votre sélection :


- Rapide
- Échantillonné
- Détaillé


 **Optimiser l’index uniquement si :**  
 L’IU propose les filtres réglables suivants, qui évitent d’avoir à actualiser les index pour lesquels ce n’est pas encore absolument nécessaire :


- Fragmentation &gt; *(%)*
- Nombre de pages &gt;
- Utilisé au cours des *(derniers jours)*


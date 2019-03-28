---
title: Résoudre les problèmes de mémoire insuffisante | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: in-memory-oltp
ms.topic: conceptual
ms.assetid: f855e931-7502-44bd-8a8b-b8543645c7f4
author: CarlRabeler
ms.author: carlrab
manager: craigg
ms.openlocfilehash: 999f58014d661f2eb476cd195e11788b2a565937
ms.sourcegitcommit: c44014af4d3f821e5d7923c69e8b9fb27aeb1afd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/27/2019
ms.locfileid: "58527891"
---
# <a name="resolve-out-of-memory-issues"></a>Résoudre les problèmes de mémoire insuffisante
  [!INCLUDE[hek_1](../../includes/hek-1-md.md)] , l' [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Il est possible que la quantité de mémoire que vous avez installée et allouée pour [!INCLUDE[hek_2](../../includes/hek-2-md.md)] ne convienne plus à vos besoins croissants. Si c'est le cas, vous risquez de manquer de mémoire. Cette rubrique explique les procédures à mettre en œuvre en cas d'insuffisance de mémoire. Consultez [Analyse et dépannage de l’utilisation de mémoire](monitor-and-troubleshoot-memory-usage.md) pour des conseils pouvant vous aider à éviter de nombreuses situations d’épuisement de la mémoire.  
  
## <a name="covered-in-this-topic"></a>Thèmes abordés dans cette rubrique  
  
|Rubrique|Vue d'ensemble|  
|-----------|--------------|  
| [Résoudre les problèmes de restauration de base de données en cas d'insuffisance de mémoire](#resolve-database-restore-failures-due-to-oom) |Explique la procédure à suivre si vous recevez le message d’erreur « Échec de l’opération de restauration pour la base de données « *\<nom_base_de_données>*  » en raison d’une mémoire insuffisante dans le pool de ressources « *\<nom_pool_de_ressources>*  ». »|  
| [Résoudre les problèmes d'insuffisance de mémoire ayant un impact sur la charge de travail](#resolve-impact-of-low-memory-or-oom-conditions-on-the-workload)|Explique la procédure à suivre si vous constatez que les problèmes d'insuffisance de mémoire ont un effet négatif sur les performances.|  
| [Résoudre les échecs d'allocation de pages dus à une mémoire insuffisante alors qu'il y a suffisamment de mémoire à disposition](#resolve-page-allocation-failures-due-to-insufficient-memory-when-sufficient-memory-is-available) |Explique la procédure à suivre si vous recevez le message d’erreur « Interdiction des allocations de pages pour la base de données « *\<nom_base_de_données>*  » en raison d’une mémoire insuffisante dans le pool de ressources « *\<nom_pool_de_ressources>*  ». ... » lorsque la mémoire disponible est suffisante pour l’opération.|  
  
## <a name="resolve-database-restore-failures-due-to-oom"></a>Résoudre les problèmes de restauration de base de données en cas d'insuffisance de mémoire  
 Quand vous tentez de restaurer une base de données, le message d'erreur suivant peut s'afficher : « L’opération a échoué pour la base de données de restauration '*\<databaseName >*« en raison d’une mémoire insuffisante dans le pool de ressources'*\<Nom_pool_de_ressources >*'. » Avant de pouvoir restaurer correctement la base de données, vous devez résoudre le problème d'insuffisance de mémoire en augmentant la quantité de mémoire à disposition.  
  
 Pour résoudre un échec de récupération dû à une situation d'insuffisance de mémoire, augmentez la mémoire disponible à l'aide de tous les moyens à votre disposition afin de disposer temporairement d'une mémoire suffisante pour l'opération de récupération.  
  
-   Fermez temporairement les applications en cours d'exécution.   
    En fermant une ou plusieurs applications en cours d’exécution, comme Visual Studio, Internet Explorer, OneNote et autres, vous mettez à disposition de l’opération de restauration la quantité de mémoire qu’elles utilisaient. Vous pourrez les redémarrer à la fin de la restauration.  
  
-   Augmentez la valeur de MAX_MEMORY_PERCENT.   
    Cet extrait de code modifie la valeur de MAX_MEMORY_PERCENT pour le pool de ressources PoolHk à 70 % de la mémoire installée.  
  
    > [!IMPORTANT]  
    >  Si le serveur s'exécute sur une machine virtuelle sans être dédié, attribuez à MIN_MEMORY_PERCENT et à MAX_MEMORY_PERCENT la même valeur.   
    > Pour plus d'informations, consultez la rubrique [Meilleures pratiques : Utilisation d’OLTP en mémoire dans un environnement de machine virtuelle](../../database-engine/using-in-memory-oltp-in-a-vm-environment.md) pour plus d’informations.  
  
    ```sql  
  
    -- disable resource governor  
    ALTER RESOURCE GOVERNOR DISABLE  
  
    -- change the value of MAX_MEMORY_PERCENT  
    ALTER RESOURCE POOL PoolHk  
    WITH  
         ( MAX_MEMORY_PERCENT = 70 )  
    GO  
  
    -- reconfigure the Resource Governor  
    --    RECONFIGURE enables resource governor  
    ALTER RESOURCE GOVERNOR RECONFIGURE  
    GO  
  
    ```  
  
     Pour plus d’informations sur les valeurs maximales de MAX_MEMORY_PERCENT, consultez la section [pourcentage de mémoire disponible pour les tables mémoire optimisées et des index](bind-a-database-with-memory-optimized-tables-to-a-resource-pool.md#percent-of-memory-available-for-memory-optimized-tables-and-indexes)
  
-   Reconfigurezz **max server memory**.  
    Pour plus d’informations sur la configuration de **max server memory** see the topic [Optimisation des performances du serveur à l’aide des options de configuration de la mémoire](https://technet.microsoft.com/library/ms177455\(v=SQL.105\).aspx).  
  
## <a name="resolve-impact-of-low-memory-or-oom-conditions-on-the-workload"></a>Résoudre les problèmes d'insuffisance de mémoire ayant un impact sur la charge de travail  
 Évidemment, il est préférable de ne pas se trouver dans une situation d'insuffisance de mémoire. Une planification et une surveillance appropriées permettent souvent d'éviter ce type de problème. Néanmoins, même la meilleure des planifications ne suffit pas toujours pour anticiper ce qui va réellement se produire. Vous risquez donc d'être confronté à un problème d'insuffisance de mémoire à un moment ou un autre. Vous pouvez mettre fin à une situation d'insuffisance de mémoire en procédant aux deux étapes ci-dessous :  
  
1.  [Ouvrir une DAC (connexion administrateur dédiée) ](#open-a-dac-dedicated-administrator-connection) 
  
2.  [Prendre une mesure corrective](#take-corrective-action) 
  
### <a name="open-a-dac-dedicated-administrator-connection"></a>Ouvrir une connexion administrateur dédiée (DAC).  
 Microsoft SQL Server propose une connexion administrateur dédiée (DAC). Cette connexion DAC permet à un administrateur d’accéder à une instance active du moteur de base de données SQL Server afin de résoudre les problèmes sur le serveur, même si ce serveur ne répond pas aux autres connexions clientes. La connexion DAC est disponible via l'utilitaire `sqlcmd` et SQL Server Management Studio (SSMS).  
  
 Pour obtenir des conseils sur l'utilisation de `sqlcmd` et de DAC, consultez [Utilisation d'une connexion administrateur dédiée](../../database-engine/configure-windows/diagnostic-connection-for-database-administrators.md). Pour obtenir des conseils sur l’utilisation de DAC via SSMS, consultez [Comment : Utiliser la connexion administrateur dédiée avec SQL Server Management Studio](https://msdn.microsoft.com/library/ms178068.aspx).  
  
### <a name="take-corrective-action"></a>Prendre une mesure corrective  
 Pour résoudre une situation d'insuffisance de mémoire, vous devez libérer de la mémoire existante en réduisant son utilisation ou mettre plus de mémoire à la disposition de vos tables en mémoire.  
  
#### <a name="free-up-existing-memory"></a>Libérer de la mémoire existante  
  
##### <a name="delete-non-essential-memory-optimized-table-rows-and-wait-for-garbage-collection"></a>Supprimer les lignes non essentielles des tables mémoire optimisées et patienter jusqu'au prochain garbage collection  
 Vous pouvez supprimer les lignes non essentielles d'une table mémoire optimisée. Le garbage collector remet à disposition la mémoire utilisée par ces lignes. . Le moteur de l'OLTP en mémoire collecte les lignes à nettoyer de façon agressive. Cependant, une transaction longue peut empêcher cette opération de garbage collection. Par exemple, si une transaction s’exécute pendant 5 minutes, les versions de ligne créées par des opérations de mise à jour ou de suppression alors que la transaction était active ne peuvent pas être récupérées par le garbage collector.  
  
##### <a name="move-one-or-more-rows-to-a-disk-based-table"></a>Déplacer une ou plusieurs lignes dans une table sur disque  
 Les articles TechNet suivants donnent des conseils pour déplacer des lignes d'une table mémoire optimisée vers une table sur disque.  
  
-   [Partitionnement au niveau de l'application](https://technet.microsoft.com/library/dn296452\(v=sql.120\).aspx)  
  
-   [Modèle d'application pour partitionner des tables optimisées en mémoire](https://technet.microsoft.com/library/dn133171\(v=sql.120\).aspx)  
  
#### <a name="increase-available-memory"></a>Augmenter la mémoire disponible  
  
##### <a name="increase-value-of-maxmemorypercent-on-the-resource-pool"></a>Augmenter la valeur de MAX_MEMORY_PERCENT sur le pool de ressources  
 Si vous n'avez pas créé de pool de ressources nommé pour les tables en mémoire, vous devez le faire et lier les bases de données de l' [!INCLUDE[hek_2](../../includes/hek-2-md.md)] à ce pool. Consultez la rubrique [Lier une base de données avec des tables optimisées en mémoire à un pool de ressources](bind-a-database-with-memory-optimized-tables-to-a-resource-pool.md) pour obtenir des conseils sur la création et la liaison de vos bases de données [!INCLUDE[hek_2](../../includes/hek-2-md.md)] à un pool de ressources.  
  
 Si votre base de données de l' [!INCLUDE[hek_2](../../includes/hek-2-md.md)] est liée à un pool de ressources, vous pouvez éventuellement augmenter le pourcentage de la mémoire à laquelle le pool peut accéder. Consultez la sous-rubrique [Modifier MIN_MEMORY_PERCENT et MAX_MEMORY_PERCENT sur un pool existant](bind-a-database-with-memory-optimized-tables-to-a-resource-pool.md#change-min-memory-percent-and-max-memory-percent-on-an-existing-pool) pour obtenir des conseils sur la modification des valeurs MIN_MEMORY_PERCENT et MAX_MEMORY_PERCENT pour un pool de ressources.  
  
 Augmentez la valeur de MAX_MEMORY_PERCENT.   
Cet extrait de code modifie la valeur de MAX_MEMORY_PERCENT pour le pool de ressources PoolHk à 70 % de la mémoire installée.  
  
> [!IMPORTANT]  
>  Si le serveur s'exécute sur une machine virtuelle sans être dédié, attribuez à MIN_MEMORY_PERCENT et à MAX_MEMORY_PERCENT la même valeur.   
> Pour plus d'informations, consultez la rubrique [Meilleures pratiques : Utilisation d’OLTP en mémoire dans un environnement de machine virtuelle](../../database-engine/using-in-memory-oltp-in-a-vm-environment.md) pour plus d’informations.  
  
```sql  
  
-- disable resource governor  
ALTER RESOURCE GOVERNOR DISABLE  
  
-- change the value of MAX_MEMORY_PERCENT  
ALTER RESOURCE POOL PoolHk  
WITH  
     ( MAX_MEMORY_PERCENT = 70 )  
GO  
  
-- reconfigure the Resource Governor  
--    RECONFIGURE enables resource governor  
ALTER RESOURCE GOVERNOR RECONFIGURE  
GO  
  
```  
  
 Pour plus d’informations sur les valeurs maximales de MAX_MEMORY_PERCENT, consultez la section [Pourcentage de mémoire disponible pour les tables et index mémoire optimisés](bind-a-database-with-memory-optimized-tables-to-a-resource-pool.md#percent-of-memory-available-for-memory-optimized-tables-and-indexes).  
  
##### <a name="install-additional-memory"></a>Installer de la mémoire supplémentaire  
 En fin de compte, la meilleure solution, le cas échéant, consiste à installer de la mémoire physique supplémentaire. Si vous choisissez cette solution, souvenez-vous que vous pourrez sans doute augmenter également la valeur de MAX_MEMORY_PERCENT (consultez la sous-rubrique [Modifier MIN_MEMORY_PERCENT et MAX_MEMORY_PERCENT sur un pool existant](bind-a-database-with-memory-optimized-tables-to-a-resource-pool.md#change-min-memory-percent-and-max-memory-percent-on-an-existing-pool)) dans la mesure où [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] n’aura probablement pas besoin de davantage de mémoire. Cela vous permettra d’optimiser cette opération si la nouvelle mémoire installée n’est pas disponible dans son intégralité pour le pool de ressources.  
  
> [!IMPORTANT]  
>  Si le serveur s'exécute sur une machine virtuelle sans être dédié, attribuez à MIN_MEMORY_PERCENT et à MAX_MEMORY_PERCENT la même valeur.   
> Pour plus d'informations, consultez la rubrique [Meilleures pratiques : Utilisation d’OLTP en mémoire dans un environnement de machine virtuelle](../../database-engine/using-in-memory-oltp-in-a-vm-environment.md) pour plus d’informations.  
  
## <a name="resolve-page-allocation-failures-due-to-insufficient-memory-when-sufficient-memory-is-available"></a>Résoudre les échecs d'allocation de pages dus à une mémoire insuffisante alors qu'il y a suffisamment de mémoire à disposition  
 Si vous recevez le message d’erreur « interdiction des allocations de page pour la base de données '*\<databaseName >*« en raison d’une mémoire insuffisante dans le pool de ressources'*\<Nom_pool_de_ressources >*'. Consultez «<https://go.microsoft.com/fwlink/?LinkId=330673>» pour plus d’informations. » dans le journal des erreurs lorsque la mémoire physique disponible est suffisante pour allouer la page, il peut être dû à la désactivation de Resource Governor. Lorsque Resource Governor est désactivé, MEMORYBROKER_FOR_RESERVE induit une sollicitation de la mémoire artificielle.  
  
 Pour corriger le problème, vous devez activer Resource Governor.  
  
 Consultez [Activer Resource Governor](https://technet.microsoft.com/library/bb895149.aspx) pour obtenir des informations sur les limites et les restrictions, ainsi que sur l’activation de Resource Governor à l’aide de l’Explorateur d’objets, sur les propriétés de Resource Governor et sur Transact-SQL.  
  
## <a name="see-also"></a>Voir aussi  
 [Gestion de la mémoire pour l'OLTP en mémoire](../../database-engine/managing-memory-for-in-memory-oltp.md)   
 [Analyse et dépannage de l’utilisation de mémoire](monitor-and-troubleshoot-memory-usage.md)   
 [Lier une base de données avec des tables mémoire optimisées à un pool de ressources](bind-a-database-with-memory-optimized-tables-to-a-resource-pool.md)   
 [Meilleures pratiques : Utilisation d’OLTP en mémoire dans un environnement de machine virtuelle](../../database-engine/using-in-memory-oltp-in-a-vm-environment.md)  
  
  

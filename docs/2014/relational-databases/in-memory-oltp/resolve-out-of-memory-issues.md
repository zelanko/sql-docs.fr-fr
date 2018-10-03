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
ms.openlocfilehash: 4df9c58eb7832438253fc39bf6c68e8268ff2671
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48067404"
---
# <a name="resolve-out-of-memory-issues"></a>Résoudre les problèmes de mémoire insuffisante
  [!INCLUDE[hek_1](../../includes/hek-1-md.md)] , l' [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Il est possible que la quantité de mémoire que vous avez installée et allouée pour [!INCLUDE[hek_2](../../includes/hek-2-md.md)] ne convienne plus à vos besoins croissants. Si c'est le cas, vous risquez de manquer de mémoire. Cette rubrique explique les procédures à mettre en œuvre en cas d'insuffisance de mémoire. Consultez [Analyse et dépannage de l’utilisation de mémoire](monitor-and-troubleshoot-memory-usage.md) pour des conseils pouvant vous aider à éviter de nombreuses situations d’épuisement de la mémoire.  
  
## <a name="covered-in-this-topic"></a>Thèmes abordés dans cette rubrique  
  
|Rubrique|Vue d'ensemble|  
|-----------|--------------|  
|[Résoudre les problèmes de restauration de base de données en cas d'insuffisance de mémoire](resolve-out-of-memory-issues.md#bkmk_resolverecoveryfailures)|Explique la procédure à suivre si vous recevez le message d’erreur « Échec de l’opération de restauration pour la base de données « *\<nom_base_de_données>*  » en raison d’une mémoire insuffisante dans le pool de ressources « *\<nom_pool_de_ressources>*  » ».|  
|[Résoudre les problèmes d'insuffisance de mémoire ayant un impact sur la charge de travail](resolve-out-of-memory-issues.md#bkmk_recoverfromoom)|Explique la procédure à suivre si vous constatez que les problèmes d'insuffisance de mémoire ont un effet négatif sur les performances.|  
|[Résoudre les échecs d'allocation de pages dus à une mémoire insuffisante alors qu'il y a suffisamment de mémoire à disposition](resolve-out-of-memory-issues.md#bkmk_pageallocfailure)|Explique la procédure à suivre si vous recevez le message d’erreur « Interdiction des allocations de pages pour la base de données « *\<nom_base_de_données>*  » en raison d’une mémoire insuffisante dans le pool de ressources « *\<nom_pool_de_ressources>*  ». … » lorsque la mémoire disponible est suffisante pour l'opération.|  
  
##  <a name="bkmk_resolveRecoveryFailures"></a> Résoudre les problèmes de restauration de base de données en cas d'insuffisance de mémoire  
 Quand vous tentez de restaurer une base de données, il se peut que le message d’erreur suivant s’affiche : « Échec de l’opération de restauration pour la base de données « *\<nom_base_de_données>*  » en raison d’une mémoire insuffisante dans le pool de ressources « *\<nom_pool_de_ressources>*  » ». Avant de pouvoir restaurer correctement la base de données, vous devez résoudre le problème d'insuffisance de mémoire en augmentant la quantité de mémoire à disposition.  
  
 Pour résoudre un échec de récupération dû à une situation d'insuffisance de mémoire, augmentez la mémoire disponible à l'aide de tous les moyens à votre disposition afin de disposer temporairement d'une mémoire suffisante pour l'opération de récupération.  
  
-   Fermez temporairement les applications en cours d'exécution.   
    En fermant une ou plusieurs applications en cours d’exécution, comme Visual Studio, Internet Explorer, OneNote et autres, vous mettez à disposition de l’opération de restauration la quantité de mémoire qu’elles utilisaient. Vous pourrez les redémarrer à la fin de la restauration.  
  
-   Augmentez la valeur de MAX_MEMORY_PERCENT.   
    Cet extrait de code modifie la valeur de MAX_MEMORY_PERCENT pour le pool de ressources PoolHk à 70 % de la mémoire installée.  
  
    > [!IMPORTANT]  
    >  Si le serveur s'exécute sur une machine virtuelle sans être dédié, attribuez à MIN_MEMORY_PERCENT et à MAX_MEMORY_PERCENT la même valeur.   
    > Pour plus d’informations, consultez la rubrique [Meilleures pratiques : utilisation de l’OLTP en mémoire dans un environnement de machine virtuelle](../../database-engine/using-in-memory-oltp-in-a-vm-environment.md) .  
  
    ```tsql  
  
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
  
     Pour plus d’informations sur les valeurs maximales de MAX_MEMORY_PERCENT, consultez la section [Pourcentage de mémoire disponible pour les tables et index mémoire optimisés](bind-a-database-with-memory-optimized-tables-to-a-resource-pool.md#bkmk_PercentAvailable).  
  
-   Reconfigurezz **max server memory**.  
    Pour plus d’informations sur la configuration de **max server memory**, consultez la rubrique [Optimisation des performances du serveur à l’aide des options de configuration de la mémoire](http://technet.microsoft.com/library/ms177455\(v=SQL.105\).aspx).  
  
##  <a name="bkmk_recoverFromOOM"></a> Résoudre les problèmes d'insuffisance de mémoire ayant un impact sur la charge de travail  
 Évidemment, il est préférable de ne pas se trouver dans une situation d'insuffisance de mémoire. Une planification et une surveillance appropriées permettent souvent d'éviter ce type de problème. Néanmoins, même la meilleure des planifications ne suffit pas toujours pour anticiper ce qui va réellement se produire. Vous risquez donc d'être confronté à un problème d'insuffisance de mémoire à un moment ou un autre. Vous pouvez mettre fin à une situation d'insuffisance de mémoire en procédant aux deux étapes ci-dessous :  
  
1.  [Ouvrir une connexion administrateur dédiée (DAC).](resolve-out-of-memory-issues.md#bkmk_opendac)  
  
2.  [Prendre une mesure corrective](resolve-out-of-memory-issues.md#bkmk_takecorrectiveaction)  
  
###  <a name="bkmk_openDAC"></a> Ouvrir une connexion administrateur dédiée (DAC).  
 Microsoft SQL Server propose une connexion administrateur dédiée (DAC). Cette connexion DAC permet à un administrateur d'accéder à une instance active du moteur de base de données SQL Server afin de résoudre les problèmes sur le serveur, même si ce serveur ne répond pas aux autres connexions clientes. La connexion DAC est disponible via l'utilitaire `sqlcmd` et SQL Server Management Studio (SSMS).  
  
 Pour obtenir des conseils sur l'utilisation de `sqlcmd` et de DAC, consultez [Utilisation d'une connexion administrateur dédiée](../../database-engine/configure-windows/diagnostic-connection-for-database-administrators.md). Pour obtenir des conseils sur l'utilisation de DAC via SSMS, consultez [Procédure : utiliser la connexion administrateur dédiée avec SQL Server Management Studio](http://msdn.microsoft.com/library/ms178068.aspx).  
  
###  <a name="bkmk_takeCorrectiveAction"></a> Prendre une mesure corrective  
 Pour résoudre une situation d'insuffisance de mémoire, vous devez libérer de la mémoire existante en réduisant son utilisation ou mettre plus de mémoire à la disposition de vos tables en mémoire.  
  
#### <a name="free-up-existing-memory"></a>Libérer de la mémoire existante  
  
##### <a name="delete-non-essential-memory-optimized-table-rows-and-wait-for-garbage-collection"></a>Supprimer les lignes non essentielles des tables mémoire optimisées et patienter jusqu'au prochain garbage collection  
 Vous pouvez supprimer les lignes non essentielles d'une table mémoire optimisée. Le garbage collector remet à disposition la mémoire utilisée par ces lignes. . Le moteur de l'OLTP en mémoire collecte les lignes à nettoyer de façon agressive. Cependant, une transaction longue peut empêcher cette opération de garbage collection. Par exemple, si une transaction s'exécute pendant cinq minutes, les versions de ligne créées par des opérations de mise à jour ou de suppression alors que la transaction était active ne peuvent pas être récupérées par le garbage collector.  
  
##### <a name="move-one-or-more-rows-to-a-disk-based-table"></a>Déplacer une ou plusieurs lignes dans une table sur disque  
 Les articles TechNet suivants donnent des conseils pour déplacer des lignes d'une table mémoire optimisée vers une table sur disque.  
  
-   [Partitionnement au niveau de l'application](http://technet.microsoft.com/library/dn296452\(v=sql.120\).aspx)  
  
-   [Modèle d'application pour partitionner des tables mémoire optimisées](http://technet.microsoft.com/library/dn133171\(v=sql.120\).aspx)  
  
#### <a name="increase-available-memory"></a>Augmenter la mémoire disponible  
  
##### <a name="increase-value-of-maxmemorypercent-on-the-resource-pool"></a>Augmenter la valeur de MAX_MEMORY_PERCENT sur le pool de ressources  
 Si vous n'avez pas créé de pool de ressources nommé pour les tables en mémoire, vous devez le faire et lier les bases de données de l' [!INCLUDE[hek_2](../../includes/hek-2-md.md)] à ce pool. Consultez la rubrique [Lier une base de données avec des tables optimisées en mémoire à un pool de ressources](bind-a-database-with-memory-optimized-tables-to-a-resource-pool.md) pour obtenir des conseils sur la création et la liaison de vos bases de données [!INCLUDE[hek_2](../../includes/hek-2-md.md)] à un pool de ressources.  
  
 Si votre base de données de l' [!INCLUDE[hek_2](../../includes/hek-2-md.md)] est liée à un pool de ressources, vous pouvez éventuellement augmenter le pourcentage de la mémoire à laquelle le pool peut accéder. Consultez la sous-rubrique [Modifier MIN_MEMORY_PERCENT et MAX_MEMORY_PERCENT sur un pool existant](bind-a-database-with-memory-optimized-tables-to-a-resource-pool.md#bkmk_ChangeAllocation) pour obtenir des conseils sur la modification des valeurs MIN_MEMORY_PERCENT et MAX_MEMORY_PERCENT pour un pool de ressources.  
  
 Augmentez la valeur de MAX_MEMORY_PERCENT.   
Cet extrait de code modifie la valeur de MAX_MEMORY_PERCENT pour le pool de ressources PoolHk à 70 % de la mémoire installée.  
  
> [!IMPORTANT]  
>  Si le serveur s'exécute sur une machine virtuelle sans être dédié, attribuez à MIN_MEMORY_PERCENT et à MAX_MEMORY_PERCENT la même valeur.   
> Pour plus d’informations, consultez la rubrique [Meilleures pratiques : utilisation de l’OLTP en mémoire dans un environnement de machine virtuelle](../../database-engine/using-in-memory-oltp-in-a-vm-environment.md) .  
  
```tsql  
  
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
  
 Pour plus d’informations sur les valeurs maximales de MAX_MEMORY_PERCENT, consultez la section [Pourcentage de mémoire disponible pour les index et les tables optimisées en mémoire](bind-a-database-with-memory-optimized-tables-to-a-resource-pool.md#bkmk_PercentAvailable).  
  
##### <a name="install-additional-memory"></a>Installer de la mémoire supplémentaire  
 En fin de compte, la meilleure solution, le cas échéant, consiste à installer de la mémoire physique supplémentaire. Si vous choisissez cette solution, souvenez-vous que vous pourrez sans doute augmenter également la valeur de MAX_MEMORY_PERCENT (consultez la sous-rubrique [Modifier MIN_MEMORY_PERCENT et MAX_MEMORY_PERCENT sur un pool existant](bind-a-database-with-memory-optimized-tables-to-a-resource-pool.md#bkmk_ChangeAllocation)) dans la mesure où [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] n’aura probablement pas besoin de davantage de mémoire. Cela vous permettra d’optimiser cette opération si la nouvelle mémoire installée n’est pas disponible dans son intégralité pour le pool de ressources.  
  
> [!IMPORTANT]  
>  Si le serveur s'exécute sur une machine virtuelle sans être dédié, attribuez à MIN_MEMORY_PERCENT et à MAX_MEMORY_PERCENT la même valeur.   
> Pour plus d’informations, consultez la rubrique [Meilleures pratiques : utilisation de l’OLTP en mémoire dans un environnement de machine virtuelle](../../database-engine/using-in-memory-oltp-in-a-vm-environment.md) .  
  
##  <a name="bkmk_PageAllocFailure"></a> Résoudre les échecs d'allocation de pages dus à une mémoire insuffisante alors qu'il y a suffisamment de mémoire à disposition  
 Si vous recevez le message d’erreur « Interdiction des allocations de pages pour la base de données « *\<nom_base_de_données>*  » en raison d’une mémoire insuffisante dans le pool de ressources « *\<nom_pool_de_ressources>*  ». Consultez « http://go.microsoft.com/fwlink/?LinkId=330673» pour plus d’informations. » dans le journal des erreurs lorsque la mémoire physique disponible est suffisante pour allouer la page, il peut être dû à la désactivation de Resource Governor. Lorsque Resource Governor est désactivé, MEMORYBROKER_FOR_RESERVE induit une sollicitation de la mémoire artificielle.  
  
 Pour corriger le problème, vous devez activer Resource Governor.  
  
 Consultez [Activer Resource Governor](http://technet.microsoft.com/library/bb895149.aspx) pour obtenir des informations sur les limites et les restrictions, ainsi que sur l’activation de Resource Governor à l’aide de l’Explorateur d’objets, sur les propriétés de Resource Governor et sur Transact-SQL.  
  
## <a name="see-also"></a>Voir aussi  
 [Gestion de la mémoire pour l'OLTP en mémoire](../../database-engine/managing-memory-for-in-memory-oltp.md)   
 [Analyse et dépannage de l’utilisation de mémoire](monitor-and-troubleshoot-memory-usage.md)   
 [Lier une base de données avec des tables optimisées en mémoire à un pool de ressources](bind-a-database-with-memory-optimized-tables-to-a-resource-pool.md)   
 [Meilleures pratiques : utilisation de l’OLTP en mémoire dans un environnement de machine virtuelle](../../database-engine/using-in-memory-oltp-in-a-vm-environment.md)  
  
  

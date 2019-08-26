---
title: Utiliser une instance de cluster de basculement - SQL Server sur Linux
description: Cet article explique comment opérer une instance de cluster de basculement SQL Server sur Linux.
author: MikeRayMSFT
ms.author: mikeray
ms.reviewer: vanto
ms.date: 08/28/2017
ms.topic: conceptual
ms.prod: sql
ms.technology: linux
ms.assetid: ''
ms.openlocfilehash: a29d1d61b628126d03458fced964bde7c92b6d68
ms.sourcegitcommit: 71b9ebb511c68e0c9cb32a860a443803d2cb58f5
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/23/2019
ms.locfileid: "68032289"
---
# <a name="operate-failover-cluster-instance---sql-server-on-linux"></a>Utiliser une instance de cluster de basculement - SQL Server sur Linux

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-linuxonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-linuxonly.md)]

Cet article explique comment opérer une instance de cluster de basculement SQL Server sur Linux. Si vous n’avez pas créé d’instance de cluster de basculement SQL Server sur Linux, consultez [Configurer une instance de cluster de basculement - SQL Server sur Linux](sql-server-linux-shared-disk-cluster-configure.md). 

## <a name="failover"></a>Basculement

Le basculement pour les instances de cluster de basculement est similaire à un cluster de basculement Windows Server (WSFC). Si le nœud de cluster qui héberge l’instance de cluster de basculement subit une défaillance, l’instance de cluster de basculement doit automatiquement basculer vers un autre nœud. Contrairement à un WSFC, il n’existe aucun moyen de définir des propriétaires préférés. Par conséquent, Pacemaker sélectionne le nœud qui sera le nouvel hôte de l’instance de cluster de basculement.

Il peut arriver que vous souhaitiez basculer manuellement l’instance de cluster de basculement vers un autre nœud. Le processus n’est pas le même qu’avec les instances de cluster de basculement sur un WSFC. Sur un WSFC, vous basculez des ressources au niveau du rôle. Dans Pacemaker, vous choisissez une ressource à déplacer et en supposant que toutes les contraintes sont correctes, tout le reste sera également déplacé. 

Le mode de basculement dépend de la distribution Linux. Suivez les instructions pour votre distribution Linux.

- [RHEL ou Ubuntu](#-manual-failover-rhel-or-ubuntu)
- [SLES](#-manual-failover-sles)

## <a name = "#-manual-failover-rhel-or-ubuntu"></a> Basculement manuel (RHEL ou Ubuntu)

Pour effectuer un basculement manuel, sur les serveurs Red Hat Enterprise Linux (RHEL) ou Ubuntu exécutez les étapes suivantes.
1.  Émettez les commandes suivantes : 

   ```bash
   sudo pcs resource move <FCIResourceName> <NewHostNode> 
   ```

   \<FCIResourceName> est le nom de ressource Pacemaker de l’interface de cluster de basculement SQL Server.

   \<NewHostNode> est le nom du nœud de cluster sur lequel vous souhaitez héberger l’instance de cluster de basculement. 

   Vous n’obtiendrez pas d’accusé de réception.

2.  Pendant un basculement manuel, Pacemaker crée une contrainte d’emplacement sur la ressource qui a été choisie pour le déplacement manuel. Pour afficher cette contrainte, exécutez `sudo pcs constraint`.

3.  Une fois le basculement terminé, supprimez la contrainte en émettant `sudo pcs resource clear <FCIResourceName>`. 

\<FCIResourceName> est le nom de ressource Pacemaker de l’interface de cluster de basculement. 

## <a name = "#-manual-failover-sles"></a> Basculement manuel (SLES)


Dans SUSE Linux Enterprise Server (SLES), utilisez la commande `migrate` pour basculer manuellement une interface de cluster de basculement SQL Server. Par exemple :

```bash
crm resource migrate <FCIResourceName> <NewHostNode>
```

\<FCIResourceName> est le nom de la ressource de l’instance de cluster de basculement. 

\<NewHostNode> est le nom du nouvel hôte de destination. 


<!---

|Distribution |Topic 
|----- |-----
|**Red Hat Enterprise Linux with HA add-on** |[Configure](sql-server-linux-shared-disk-cluster-red-hat-7-configure.md)<br/>[Operate](sql-server-linux-shared-disk-cluster-red-hat-7-operate.md)
|**SUSE Linux Enterprise Server with HA add-on** |[Configure](sql-server-linux-shared-disk-cluster-sles-configure.md)

--->

## <a name="next-steps"></a>Next Steps

- [Configurer l’instance de cluster de basculement - SQL Server sur Linux](sql-server-linux-shared-disk-cluster-configure.md)

<!--Image references-->

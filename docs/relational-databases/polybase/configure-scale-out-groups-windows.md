---
title: Améliorer les groupes de scale-out PolyBase sur Windows | Microsoft Docs
ms.date: 09/24/2018
ms.prod: sql
ms.reviewer: ''
ms.custom: ''
ms.technology: polybase
ms.topic: tutorial
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: 3041a862639c8cbd71f2ad71378e980ec0b31fdc
ms.sourcegitcommit: 110e5e09ab3f301c530c3f6363013239febf0ce5
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/10/2018
ms.locfileid: "48905133"
---
# <a name="improve-polybase-scale-out-groups-on-windows"></a>Améliorer les groupes de scale-out PolyBase sur Windows

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

Cet article décrit comment configurer un [groupe de scale-out PolyBase](polybase-scale-out-groups.md) sur Windows. Ceci permet de créer un cluster d’instances de SQL Server pour traiter de grands volumes de jeux de données à partir de sources de données externes telles que Hadoop ou le stockage d’objets Blob Azure, sous forme de montée en puissance (scale-out) parallèle pour des performances de requête optimisées.

## <a name="prerequisites"></a>Conditions préalables requises
  
- Plusieurs machines dans le même domaine  
  
- Un compte d’utilisateur de domaine pour exécuter les services PolyBase  
  
## <a name="process-overview"></a>Vue d’ensemble du processus

Les étapes suivantes résument le processus de création d’un groupe de scale-out PolyBase. La section suivante fournit une présentation plus détaillée de chaque étape.
  
1. Installez la même version de SQL Server avec PolyBase sur N machines.
  
2. Sélectionnez une instance de SQL Server en tant que nœud principal. Un nœud principal peut uniquement être désigné sur une instance exécutant SQL Server Entreprise.
  
3. Ajoutez les autres instances SQL Server comme nœuds de calcul à l’aide de [sp_polybase_join_group](../../relational-databases/system-stored-procedures/polybase-stored-procedures-sp-polybase-join-group.md).

4. Surveillez les nœuds du groupe à l’aide de [sys.dm_exec_compute_nodes &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-exec-compute-nodes-transact-sql.md).

5. Facultatif. Supprimez un nœud de calcul à l’aide de [sp_polybase_leave_group &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/polybase-stored-procedures-sp-polybase-leave-group.md).

## <a name="example-walk-through"></a>Exemple de procédure

Cet exemple présente les étapes de configuration d’un groupe PolyBase à l’aide :  
  
1. de deux machines dans le domaine *PQTH4A* qui ont pour nom :  
  
   - PQTH4A-CMP01  
  
   - PQTH4A-CMP02  
  
2. d’un compte de domaine : *PQTH4A\PolybaseUser*  

## <a name="install-sql-server-with-polybase-on-all-machines"></a>Installer SQL Server avec PolyBase sur toutes les machines

1. Exécutez setup.exe.
  
2. Sur la page de sélection de fonctionnalités, sélectionnez **Service de requête PolyBase pour données externes**.
  
3. Dans la page Configuration du serveur, utilisez le **compte de domaine** PQTH4A\PolybaseUser pour le moteur PolyBase SQL Server et le service de mouvement de données PolyBase SQL Server.
  
4. Dans la page Configuration de PolyBase, sélectionnez l’option **Utiliser ce serveur SQL Server comme composant du groupe de scale-out PolyBase**. Elle ouvre le pare-feu pour autoriser les connexions entrantes aux services PolyBase.
  
5. Une fois l’installation terminée, exécutez **services.msc**. Vérifiez que SQL Server, le moteur PolyBase et le service de déplacement de données PolyBase sont en cours d’exécution.
  
   ![Services PolyBase](../../relational-databases/polybase/media/polybase-services.png "Services PolyBase")  
  
## <a name="select-one-sql-server-as-head-node"></a>Sélectionnez un serveur SQL Server comme nœud principal  
  
Une fois l’installation terminée, les deux machines peuvent fonctionner en tant que nœuds principaux d’un groupe PolyBase. Dans cet exemple, nous choisissons « MSSQLSERVER » sur PQTH4A-CMP01 en tant que nœud principal.
  
## <a name="add-other-sql-server-instances-as-compute-nodes"></a>Ajoutez d’autres instances SQL Server comme nœuds de calcul  
  
1. Connectez-vous à SQL Server sur PQTH4A-CMP02.
  
2. Exécutez la procédure stockée [sp_polybase_join_group](../../relational-databases/system-stored-procedures/polybase-stored-procedures-sp-polybase-join-group.md).

   ```sql
   -- Enter head node details:
   -- head node machine name, head node dms control channel port, head node sql server name  
    EXEC sp_polybase_join_group 'PQTH4A-CMP01', 16450, 'MSSQLSERVER';
   ```  

3. Exécutez services.msc sur le nœud de calcul (PQTH4A-CMP02).
  
4. Arrêtez le moteur PolyBase et redémarrez le service de déplacement des données PolyBase.
  
## <a name="optional-remove-a-compute-node"></a>Facultatif : supprimez un nœud de calcul  
  
1. Connectez-vous au nœud de calcul SQL Server (PQTH4A-CMP02).
  
2. Exécutez la procédure stockée sp_polybase_leave_group.
  
    ```sql  
    EXEC sp_polybase_leave_group;  
    ```  
  
3. Exécutez services.msc sur le nœud de calcul en cours de suppression (PQTH4A-CMP02).
  
4. Démarrez le moteur PolyBase. Redémarrez le service de déplacement de données PolyBase.
  
5. Vérifiez que le nœud a été supprimé en exécutant la DMV sys.dm_exec_compute_nodes sur PQTH4A-CMP01. À présent, PQTH4A-CMP02 fonctionne en tant que nœud principal autonome  
  
## <a name="next-steps"></a>Étapes suivantes  

Pour le dépannage, consultez [PolyBase troubleshooting with dynamic management views](http://msdn.microsoft.com/library/ce9078b7-a750-4f47-b23e-90b83b783d80).
  
Pour plus d’informations sur PolyBase, consultez [Vue d'ensemble de PolyBase](../../relational-databases/polybase/polybase-guide.md).

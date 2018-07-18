---
title: Configurer SQL Server pour utiliser Soft-NUMA (SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 07/12/2016
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- NUMA
- non-uniform memory access
ms.assetid: 1af22188-e08b-4c80-a27e-4ae6ed9ff969
caps.latest.revision: 38
author: CarlRabeler
ms.author: carlrab
manager: craigg
ms.openlocfilehash: 434e569b17fa70b6f6b3f4763e54e08e271dc99b
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/02/2018
ms.locfileid: "37279557"
---
# <a name="configure-sql-server-to-use-soft-numa-sql-server"></a>Configurer SQL Server pour utiliser soft-NUMA (SQL Server)
Les processeurs modernes disposent de nombreux noyaux par socket. Chaque socket est généralement représenté sous forme de nœud NUMA unique. Le moteur de base de données SQL Server partitionne plusieurs structures internes et threads de service de partitionnement par nœud NUMA. Avec les processeurs contenant 10 ou plusieurs noyaux par socket, à l’aide de logiciels NUMA (soft-NUMA) pour fractionner les nœuds NUMA matériels généralement augmente l’évolutivité et performances.   

> [!NOTE]
> Les processeurs ajoutés à chaud ne sont pas pris en charge par le soft-NUMA.
  
## <a name="automatic-soft-numa"></a>Soft-NUMA automatique

Nœuds soft-NUMA à partir de SQL Server 2014 Service Pack 2, chaque fois que le serveur de moteur de base de données détecte plus de 8 processeurs physiques au démarrage, sont créés automatiquement si l’indicateur de trace 8079 est activé en tant que paramètre de démarrage. Cœurs de processeurs multithreads ne sont pas prises en compte pour lors du décompte des processeurs physiques. Lorsque le nombre de processeurs physiques détectés est supérieur à 8 par socket, le service de moteur de base de données crée des nœuds soft-NUMA que dans l’idéal, contient 8 cœurs, chiffre peuvent varier de 5 ou jusqu'à 9 processeurs logiques par nœud. La taille du nœud matériel peut être limitée par un masque d'affinité de l’UC. Le nombre de nœuds NUMA ne dépasse jamais le nombre maximal de nœuds NUMA pris en charge.

Sans l’indicateur de trace, soft-NUMA est désactivée par défaut. Vous pouvez activer soft-NUMA à l’aide de l’indicateur de trace 8079. La modification de ce paramètre requiert le redémarrage du moteur de base de données pour s’appliquer.

La figure ci-dessous illustre le type d’informations concernant le soft-NUMA qui s’affiche dans le journal des erreurs SQL Server lorsque SQL Server détecte des nœuds NUMA matériels avec plus de 8 processeurs logiques et si l’indicateur de trace 8079 est activé.

![Soft-NUMA](./media/soft-numa-sql-server/soft-numa.PNG)

## <a name="manual-soft-numa"></a>Soft-NUMA manuel
  
Pour configurer [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] pour utiliser soft-NUMA manuellement, vous devez modifier le Registre pour ajouter un masque d’affinité de nœud configuration. Le masque soft-NUMA peut être établi comme entrée de Registre binaire, DWORD (hexadécimal ou décimal) ou QWORD (hexadécimal ou décimal). Pour configurer plus que les 32 premiers processeurs, utilisez des valeurs de Registre QWORD ou BINARY. (Les valeurs QWORD ne peuvent pas être utilisées avant [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)].) Vous devez redémarrer le [!INCLUDE[ssDE](../../includes/ssde-md.md)] pour configurer soft-NUMA.  
  
> [!TIP]  
>  Les UC sont numérotées à partir de 0.  
  
 [!INCLUDE[ssNoteRegistry](../../includes/ssnoteregistry-md.md)]  
  
 Prenons l'exemple suivant. Un ordinateur avec huit UC ne possède pas d'accès NUMA matériel. Trois nœuds soft-NUMA sont configurés. L'instance A du [!INCLUDE[ssDE](../../includes/ssde-md.md)] est configurée pour utiliser les UC de 0 à 3. Une deuxième instance du [!INCLUDE[ssDE](../../includes/ssde-md.md)] est installée et configurée pour utiliser les UC de 4 à 7. L'exemple peut être représenté visuellement de la façon suivante :  
  
 `CPUs          0  1  2  3  4  5  6  7`  
  
 `Soft-NUMA   <-N0--><-N1-><----N2---->`  
  
 `SQL Server  <instance A ><instance B>`  
  
 L'instance A, confrontée à des E/S importantes, possède maintenant deux threads d'E/S et un thread d'écriture différée, tandis que l'instance B, qui exécute des opérations nécessitant des ressources UC conséquentes, ne possède qu'un seul thread d'E/S et un seul thread d'écriture différée. Il est possible d'affecter des quantités de mémoire différentes aux instances, mais contrairement à l'accès NUMA matériel, elles reçoivent toutes deux la mémoire du même bloc mémoire du système d'exploitation et il n'existe pas d'affinité entre la mémoire et le processeur.  
  
 Le thread d'écriture différée est lié à la vue du système d'exploitation SQL des nœuds de mémoire NUMA physiques. Par conséquent, tout ce que le matériel présente sous la forme de nœuds NUMA physiques va correspondre au nombre de thread d'écriture différée qui sont créés. Pour plus d'informations, consultez [Fonctionnement : soft-NUMA, thread d'achèvement d'E/S, threads de travail d'écriture différée et nœuds de mémoire](http://blogs.msdn.com/b/psssql/archive/2010/04/02/how-it-works-soft-numa-i-o-completion-thread-lazy-writer-workers-and-memory-nodes.aspx).  
  
> [!NOTE]  
>  Les clés de Registre **NUMA logiciel** ne sont pas copiées quand vous mettez à niveau une instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
### <a name="set-the-cpu-affinity-mask"></a>Définir le masque d'affinité de l'UC  
  
1.  Exécutez l'instruction suivante sur l'instance A de façon à la configurer pour qu'elle utilise les UC 0, 1, 2 et 3 en définissant le masque d'affinité de l'UC :  
  
    ```  
    ALTER SERVER CONFIGURATION   
    SET PROCESS AFFINITY CPU=0 TO 3;  
    ```  
  
2.  Exécutez l'instruction suivante sur l'instance B de façon à la configurer pour qu'elle utilise les UC 4, 5, 6 et 7 en définissant le masque d'affinité de l'UC :  
  
    ```  
    ALTER SERVER CONFIGURATION   
    SET PROCESS AFFINITY CPU=4 TO 7;  
    ```  
  
### <a name="map-soft-numa-nodes-to-cpus"></a>Mapper les nœuds soft-NUMA aux UC  
  
-   À l'aide de l'Éditeur du Registre (regedit.exe), ajoutez les clés de Registre suivantes pour mapper le nœud soft-NUMA 0 aux UC 0 et 1, le nœud soft-NUMA 1 aux UC 2 et 3, et le nœud soft-NUMA 2 aux UC 4, 5, 6 et 7.  
  
     Dans l’exemple suivant, supposons que vous disposiez d’un serveur DL580 G9 doté de 4 sockets (avec 18 noyaux par socket), chaque socket se trouvant dans son propre groupe de processeurs (« K-Group »). Vous pouvez créer une configuration soft-NUMA qui se présente comme suit (6 noyaux par nœud, 3 nœuds par groupe, 4 groupes).  
  
    |Exemple pour un serveur [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] avec plusieurs « K-Groups »|Type|Nom de valeur|Données de valeur|  
    |------------------------------------------------------------------------|----------|----------------|----------------|  
    |HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft SQL Server\120\NodeConfiguration\Node0|DWORD|CPUMask|0x3F|  
    |HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft SQL Server\120\NodeConfiguration\Node0|DWORD|Grouper|0|  
    |HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft SQL Server\120\NodeConfiguration\Node1|DWORD|CPUMask|0x0fc0|  
    |HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft SQL Server\120\NodeConfiguration\Node1|DWORD|Grouper|0|  
    |HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft SQL Server\120\NodeConfiguration\Node2|DWORD|CPUMask|0x3f000|  
    |HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft SQL Server\120\NodeConfiguration\Node2|DWORD|Grouper|0|  
    |HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft SQL Server\120\NodeConfiguration\Node3|DWORD|CPUMask|0x3F|  
    |HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft SQL Server\120\NodeConfiguration\Node3|DWORD|Grouper| 1|  
    |HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft SQL Server\120\NodeConfiguration\Node4|DWORD|CPUMask|0x0fc0|  
    |HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft SQL Server\120\NodeConfiguration\Node4|DWORD|Grouper| 1|  
    |HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft SQL Server\120\NodeConfiguration\Node5|DWORD|CPUMask|0x3f000|  
    |HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft SQL Server\120\NodeConfiguration\Node5|DWORD|Grouper| 1|  
    |HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft SQL Server\120\NodeConfiguration\Node6|DWORD|CPUMask|0x3F|  
    |HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft SQL Server\120\NodeConfiguration\Node6|DWORD|Grouper|2|  
    |HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft SQL Server\120\NodeConfiguration\Node7|DWORD|CPUMask|0x0fc0|  
    |HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft SQL Server\120\NodeConfiguration\Node7|DWORD|Grouper|2|  
    |HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft SQL Server\120\NodeConfiguration\Node8|DWORD|CPUMask|0x3f000|  
    |HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft SQL Server\120\NodeConfiguration\Node8|DWORD|Grouper|2|  
    |HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft SQL Server\120\NodeConfiguration\Node9|DWORD|CPUMask|0x3F|  
    |HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft SQL Server\120\NodeConfiguration\Node9|DWORD|Grouper|3|  
    |HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft SQL Server\120\NodeConfiguration\Node10|DWORD|CPUMask|0x0fc0|  
    |HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft SQL Server\120\NodeConfiguration\Node10|DWORD|Grouper|3|  
    |HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft SQL Server\120\NodeConfiguration\Node11|DWORD|CPUMask|0x3f000|  
    |HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft SQL Server\120\NodeConfiguration\Node11|DWORD|Grouper|3|  
  
     Autres exemples :  
  
    |[!INCLUDE[ssSQL14](../../includes/sssql14-md.md)]|Type|Nom de valeur|Données de valeur|  
    |---------------------------|----------|----------------|----------------|  
    |HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft SQL Server\120\NodeConfiguration\Node0|DWORD|CPUMask|0x03|  
    |HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft SQL Server\120\NodeConfiguration\Node0|DWORD|Grouper|0|  
    |HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft SQL Server\120\NodeConfiguration\Node1|DWORD|CPUMask|0x0c|  
    |HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft SQL Server\120\NodeConfiguration\Node1|DWORD|Grouper|0|  
    |HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft SQL Server\120\NodeConfiguration\Node2|DWORD|CPUMask|0xf0|  
    |HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft SQL Server\120\NodeConfiguration\Node2|DWORD|Grouper|0|  
  
    > [!TIP]  
    >  Pour spécifier les UC 60 à 63, utilisez une valeur QWORD de F000000000000000 ou une valeur BINARY de 1111000000000000000000000000000000000000000000000000000000000000.  
  
    |[!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]|Type|Nom de valeur|Données de valeur|  
    |---------------------------|----------|----------------|----------------|  
    |HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft SQL Server\110\NodeConfiguration\Node0|DWORD|CPUMask|0x03|  
    |HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft SQL Server\110\NodeConfiguration\Node0|DWORD|Grouper|0|  
    |HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft SQL Server\110\NodeConfiguration\Node1|DWORD|CPUMask|0x0c|  
    |HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft SQL Server\110\NodeConfiguration\Node1|DWORD|Grouper|0|  
    |HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft SQL Server\110\NodeConfiguration\Node2|DWORD|CPUMask|0xf0|  
    |HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft SQL Server\110\NodeConfiguration\Node2|DWORD|Grouper|0|  
  
    |SQL Server 2008 R2|Type|Nom de valeur|Données de valeur|  
    |------------------------|----------|----------------|----------------|  
    |HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft SQL Server\100\NodeConfiguration\Node0|DWORD|CPUMask|0x03|  
    |HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft SQL Server\100\NodeConfiguration\Node0|DWORD|Grouper|0|  
    |HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft SQL Server\100\NodeConfiguration\Node1|DWORD|CPUMask|0x0c|  
    |HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft SQL Server\100\NodeConfiguration\Node1|DWORD|Grouper|0|  
    |HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft SQL Server\100\NodeConfiguration\Node2|DWORD|CPUMask|0xf0|  
    |HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft SQL Server\100\NodeConfiguration\Node2|DWORD|Grouper|0|  
  
    |SQL Server 2008|Type|Nom de valeur|Données de valeur|  
    |---------------------|----------|----------------|----------------|  
    |HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft SQL Server\100\NodeConfiguration\Node0|DWORD|CPUMask|0x03|  
    |HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft SQL Server\100\NodeConfiguration\Node1|DWORD|CPUMask|0x0c|  
    |HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft SQL Server\100\NodeConfiguration\Node2|DWORD|CPUMask|0xf0|  
  
    |SQL Server 2005|Type|Nom de valeur|Données de valeur|  
    |---------------------|----------|----------------|----------------|  
    |HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft SQL Server\90\NodeConfiguration\Node0|DWORD|CPUMask|0x03|  
    |HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft SQL Server\90\NodeConfiguration\Node1|DWORD|CPUMask|0x0c|  
    |HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft SQL Server\90\NodeConfiguration\Node2|DWORD|CPUMask|0xf0|  
  
## <a name="see-also"></a>Voir aussi  
 [Mapper les ports TCP/IP aux nœuds NUMA &#40;SQL Server&#41;](map-tcp-ip-ports-to-numa-nodes-sql-server.md)   
 [affinity mask (option de configuration de serveur)](affinity-mask-server-configuration-option.md)   
 [ALTER SERVER CONFIGURATION &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-server-configuration-transact-sql)  
  
  

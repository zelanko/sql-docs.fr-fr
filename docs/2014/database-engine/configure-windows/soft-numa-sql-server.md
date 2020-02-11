---
title: Configurer SQL Server pour utiliser soft-NUMA (SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 07/12/2016
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- NUMA
- non-uniform memory access
ms.assetid: 1af22188-e08b-4c80-a27e-4ae6ed9ff969
author: CarlRabeler
ms.author: carlrab
manager: craigg
ms.openlocfilehash: 6ad0e30c0db83daf7e0cae4f7353d1f0a96a96d9
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "62809031"
---
# <a name="configure-sql-server-to-use-soft-numa-sql-server"></a>Configurer SQL Server pour utiliser soft-NUMA (SQL Server)
Les processeurs modernes disposent de nombreux noyaux par socket. Chaque socket est généralement représenté sous forme de nœud NUMA unique. Le moteur de base de données SQL Server partitionne plusieurs structures internes et threads de service de partitionnement par nœud NUMA. Avec les processeurs contenant 10 cœurs ou plus par socket, l’utilisation du NUMA logiciel (soft-NUMA) pour fractionner les nœuds NUMA matériels augmente généralement l’évolutivité et les performances.   

> [!NOTE]
> Les processeurs ajoutés à chaud ne sont pas pris en charge par le soft-NUMA.
  
## <a name="automatic-soft-numa"></a>Soft-NUMA automatique
À compter de SQL Server 2014 Service Pack 2, chaque fois que le serveur du moteur de base de données détecte plus de 8 processeurs physiques au démarrage, les nœuds soft-NUMA sont créés automatiquement si l’indicateur de trace 8079 est activé en tant que paramètre de démarrage. Les cœurs de processeurs hyper-thread ne sont pas comptabilisés pour le comptage des processeurs physiques. Lorsque le nombre de processeurs physiques détectés est supérieur à 8 par socket, le service moteur de base de données crée des nœuds soft-NUMA qui contiennent idéalement 8 cœurs, mais peut aller jusqu’à 5 ou jusqu’à 9 processeurs logiques par nœud. La taille du nœud matériel peut être limitée par un masque d'affinité de l’UC. Le nombre de nœuds NUMA ne dépasse jamais le nombre maximal de nœuds NUMA pris en charge.

Sans l’indicateur de trace, soft-NUMA est désactivé par défaut. Vous pouvez activer soft-NUMA à l’aide de l’indicateur de trace 8079. La modification de ce paramètre requiert le redémarrage du moteur de base de données pour s’appliquer.

La figure ci-dessous illustre le type d’informations concernant le soft-NUMA que vous verrez dans le SQL Server journal des erreurs lorsque SQL Server détecte des nœuds NUMA matériels avec plus de 8 processeurs logiques et si l’indicateur de trace 8079 est activé.

![Soft-NUMA](./media/soft-numa-sql-server/soft-numa.PNG)

> [!NOTE]
> À partir de SQL Server 2016, ce comportement est contrôlé par le moteur et l’indicateur de trace 8079 n’a aucun effet.

## <a name="manual-soft-numa"></a>Soft-NUMA manuel
  
Pour configurer [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] de manière à utiliser soft-NUMA manuellement, vous devez modifier le registre pour ajouter un masque d’affinité de configuration des nœuds. Le masque soft-NUMA peut être établi comme entrée de Registre binaire, DWORD (hexadécimal ou décimal) ou QWORD (hexadécimal ou décimal). Pour configurer plus que les 32 premiers processeurs, utilisez des valeurs de Registre QWORD ou BINARY. (Les valeurs QWORD ne peuvent pas être [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]utilisées avant.) Vous devez redémarrer le [!INCLUDE[ssDE](../../includes/ssde-md.md)] pour configurer soft-NUMA.  
  
> [!TIP]  
>  Les UC sont numérotées à partir de 0.  
  
 [!INCLUDE[ssNoteRegistry](../../includes/ssnoteregistry-md.md)]  
  
 Considérez l'exemple suivant. Un ordinateur avec huit UC ne possède pas d'accès NUMA matériel. Trois nœuds soft-NUMA sont configurés. L'instance A du [!INCLUDE[ssDE](../../includes/ssde-md.md)] est configurée pour utiliser les UC de 0 à 3. Une deuxième instance du [!INCLUDE[ssDE](../../includes/ssde-md.md)] est installée et configurée pour utiliser les UC de 4 à 7. L'exemple peut être représenté visuellement de la façon suivante :  
  
 `CPUs          0  1  2  3  4  5  6  7`  
  
 `Soft-NUMA   <-N0--><-N1-><----N2---->`  
  
 `SQL Server  <instance A ><instance B>`  
  
 L'instance A, confrontée à des E/S importantes, possède maintenant deux threads d'E/S et un thread d'écriture différée, tandis que l'instance B, qui exécute des opérations nécessitant des ressources UC conséquentes, ne possède qu'un seul thread d'E/S et un seul thread d'écriture différée. Il est possible d'affecter des quantités de mémoire différentes aux instances, mais contrairement à l'accès NUMA matériel, elles reçoivent toutes deux la mémoire du même bloc mémoire du système d'exploitation et il n'existe pas d'affinité entre la mémoire et le processeur.  
  
 Le thread d'écriture différée est lié à la vue du système d'exploitation SQL des nœuds de mémoire NUMA physiques. Par conséquent, tout ce que le matériel présente sous la forme de nœuds NUMA physiques va correspondre au nombre de thread d'écriture différée qui sont créés. Pour plus d'informations, consultez [Fonctionnement : soft-NUMA, thread d'achèvement d'E/S, threads de travail d'écriture différée et nœuds de mémoire](https://blogs.msdn.com/b/psssql/archive/2010/04/02/how-it-works-soft-numa-i-o-completion-thread-lazy-writer-workers-and-memory-nodes.aspx).  
  
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
  
     Dans l’exemple suivant, supposons que vous disposiez d’un serveur DL580 G9 doté de 4 sockets (avec 18 noyaux par socket), chaque socket se trouvant dans son propre groupe de processeurs (« K-Group »). Vous pouvez créer une configuration soft-NUMA qui se présente comme suit (6 noyaux par nœud, 3 nœuds par groupe, 4 groupes).  
  
    |Exemple pour un serveur [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] avec plusieurs « K-Groups »|Type|Nom de la valeur|Données de valeur|  
    |------------------------------------------------------------------------|----------|----------------|----------------|  
    |HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft SQL Server\120\NodeConfiguration\Node0|DWORD|CPUMask|0x3F|  
    |HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft SQL Server\120\NodeConfiguration\Node0|DWORD|Group|0|  
    |HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft SQL Server\120\NodeConfiguration\Node1|DWORD|CPUMask|0x0fc0|  
    |HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft SQL Server\120\NodeConfiguration\Node1|DWORD|Group|0|  
    |HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft SQL Server\120\NodeConfiguration\Node2|DWORD|CPUMask|0x3f000|  
    |HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft SQL Server\120\NodeConfiguration\Node2|DWORD|Group|0|  
    |HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft SQL Server\120\NodeConfiguration\Node3|DWORD|CPUMask|0x3F|  
    |HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft SQL Server\120\NodeConfiguration\Node3|DWORD|Group|1|  
    |HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft SQL Server\120\NodeConfiguration\Node4|DWORD|CPUMask|0x0fc0|  
    |HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft SQL Server\120\NodeConfiguration\Node4|DWORD|Group|1|  
    |HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft SQL Server\120\NodeConfiguration\Node5|DWORD|CPUMask|0x3f000|  
    |HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft SQL Server\120\NodeConfiguration\Node5|DWORD|Group|1|  
    |HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft SQL Server\120\NodeConfiguration\Node6|DWORD|CPUMask|0x3F|  
    |HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft SQL Server\120\NodeConfiguration\Node6|DWORD|Group|2|  
    |HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft SQL Server\120\NodeConfiguration\Node7|DWORD|CPUMask|0x0fc0|  
    |HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft SQL Server\120\NodeConfiguration\Node7|DWORD|Group|2|  
    |HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft SQL Server\120\NodeConfiguration\Node8|DWORD|CPUMask|0x3f000|  
    |HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft SQL Server\120\NodeConfiguration\Node8|DWORD|Group|2|  
    |HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft SQL Server\120\NodeConfiguration\Node9|DWORD|CPUMask|0x3F|  
    |HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft SQL Server\120\NodeConfiguration\Node9|DWORD|Group|3|  
    |HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft SQL Server\120\NodeConfiguration\Node10|DWORD|CPUMask|0x0fc0|  
    |HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft SQL Server\120\NodeConfiguration\Node10|DWORD|Group|3|  
    |HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft SQL Server\120\NodeConfiguration\Node11|DWORD|CPUMask|0x3f000|  
    |HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft SQL Server\120\NodeConfiguration\Node11|DWORD|Group|3|  
  
     Autres exemples :  
  
    |[!INCLUDE[ssSQL14](../../includes/sssql14-md.md)]|Type|Nom de la valeur|Données de valeur|  
    |---------------------------|----------|----------------|----------------|  
    |HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft SQL Server\120\NodeConfiguration\Node0|DWORD|CPUMask|0x03|  
    |HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft SQL Server\120\NodeConfiguration\Node0|DWORD|Group|0|  
    |HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft SQL Server\120\NodeConfiguration\Node1|DWORD|CPUMask|0x0c|  
    |HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft SQL Server\120\NodeConfiguration\Node1|DWORD|Group|0|  
    |HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft SQL Server\120\NodeConfiguration\Node2|DWORD|CPUMask|0xf0|  
    |HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft SQL Server\120\NodeConfiguration\Node2|DWORD|Group|0|  
  
    > [!TIP]  
    >  Pour spécifier les UC 60 à 63, utilisez une valeur QWORD de F000000000000000 ou une valeur BINARY de 1111000000000000000000000000000000000000000000000000000000000000.  
  
    |[!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]|Type|Nom de la valeur|Données de valeur|  
    |---------------------------|----------|----------------|----------------|  
    |HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft SQL Server\110\NodeConfiguration\Node0|DWORD|CPUMask|0x03|  
    |HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft SQL Server\110\NodeConfiguration\Node0|DWORD|Group|0|  
    |HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft SQL Server\110\NodeConfiguration\Node1|DWORD|CPUMask|0x0c|  
    |HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft SQL Server\110\NodeConfiguration\Node1|DWORD|Group|0|  
    |HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft SQL Server\110\NodeConfiguration\Node2|DWORD|CPUMask|0xf0|  
    |HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft SQL Server\110\NodeConfiguration\Node2|DWORD|Group|0|  
  
    |SQL Server 2008 R2|Type|Nom de la valeur|Données de valeur|  
    |------------------------|----------|----------------|----------------|  
    |HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft SQL Server\100\NodeConfiguration\Node0|DWORD|CPUMask|0x03|  
    |HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft SQL Server\100\NodeConfiguration\Node0|DWORD|Group|0|  
    |HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft SQL Server\100\NodeConfiguration\Node1|DWORD|CPUMask|0x0c|  
    |HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft SQL Server\100\NodeConfiguration\Node1|DWORD|Group|0|  
    |HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft SQL Server\100\NodeConfiguration\Node2|DWORD|CPUMask|0xf0|  
    |HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft SQL Server\100\NodeConfiguration\Node2|DWORD|Group|0|  
  
    |SQL Server 2008|Type|Nom de la valeur|Données de valeur|  
    |---------------------|----------|----------------|----------------|  
    |HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft SQL Server\100\NodeConfiguration\Node0|DWORD|CPUMask|0x03|  
    |HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft SQL Server\100\NodeConfiguration\Node1|DWORD|CPUMask|0x0c|  
    |HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft SQL Server\100\NodeConfiguration\Node2|DWORD|CPUMask|0xf0|  
  
    |SQL Server 2005|Type|Nom de la valeur|Données de valeur|  
    |---------------------|----------|----------------|----------------|  
    |HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft SQL Server\90\NodeConfiguration\Node0|DWORD|CPUMask|0x03|  
    |HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft SQL Server\90\NodeConfiguration\Node1|DWORD|CPUMask|0x0c|  
    |HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft SQL Server\90\NodeConfiguration\Node2|DWORD|CPUMask|0xf0|  
  
## <a name="see-also"></a>Voir aussi  
 [Mapper les ports TCP/IP aux nœuds NUMA &#40;SQL Server&#41;](map-tcp-ip-ports-to-numa-nodes-sql-server.md)   
 [affinity mask (option de configuration de serveur)](affinity-mask-server-configuration-option.md)   
 [ALTER SERVER CONFIGURATION &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-server-configuration-transact-sql)  
  
  

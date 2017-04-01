---
title: "Soft-NUMA (SQL Server) | Microsoft Docs"
ms.custom: 
  - "SQL2016_New_Updated"
ms.date: "11/16/2016"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "database-engine"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "NUMA"
  - "soft-NUMA"
helpviewer_keywords: 
  - "NUMA"
  - "accès mémoire non uniforme"
  - "soft-NUMA"
ms.assetid: 1af22188-e08b-4c80-a27e-4ae6ed9ff969
caps.latest.revision: 53
author: "CarlRabeler"
ms.author: "carlrab"
manager: "jhubbard"
caps.handback.revision: 52
---
# Soft-NUMA (SQL Server)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx_md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Les processeurs modernes disposent de nombreux noyaux par socket. Chaque socket est généralement représenté sous forme de nœud NUMA unique. Le moteur de base de données SQL Server partitionne plusieurs structures internes et threads de service de partitionnement par nœud NUMA.  Pour les processeurs contenant 10 noyaux par socket ou plus, l’utilisation du NUMA logiciel pour fractionner les nœuds NUMA matériels augmente généralement l’évolutivité et les performances. Avant SQL Server 2014 SP2, le NUMA logiciel (soft-NUMA) nécessitait la modification du Registre pour ajouter un masque d’affinité de configuration des nœuds et était configuré par ordinateur plutôt que par instance.  Avec SQL Server 2014 SP2 et SQL Server 2016, le soft-NUMA est configuré automatiquement au niveau instance de base de données au démarrage du service SQL Server.  
  
> [!NOTE]  
>  Les processeurs ajoutés à chaud ne sont pas pris en charge par le soft-NUMA.  
  
## <a name="automatic-soft-numa"></a>Soft-NUMA automatique  
 Avec SQL Server 2016, chaque fois que le serveur de moteur de base de données détecte plus de huit cœurs physiques par socket ou nœud NUMA au démarrage, des nœuds NUMA logiciel sont créés automatiquement par défaut. Les cœurs des processeurs multithreads ne sont pas différenciés lors du décompte des cœurs physiques dans un nœud.  Quand le nombre de cœurs physiques détectés est supérieur à huit par socket, le service du moteur de base de données crée des nœuds NUMA logiciel contenant idéalement huit cœurs, ce chiffre pouvant varier de cinq à neuf cœurs logiques par nœud. La taille du nœud matériel peut être limitée par un masque d'affinité de l’UC. Consultez   
            [ALTER SERVER CONFIGURATION &amp;#40;Transact-SQL&amp;#41;](../../t-sql/statements/alter-server-configuration-transact-sql.md). Le nombre de nœuds NUMA ne dépasse jamais le nombre maximal de nœuds NUMA pris en charge.  
  
 Vous pouvez désactiver ou réactiver le soft-NUMA avec l’instruction [ALTER SERVER CONFIGURATION &#40;Transact-SQL&#41;](../../t-sql/statements/alter-server-configuration-transact-sql.md) et l’argument SET SOFTNUMA. La modification de ce paramètre requiert le redémarrage du moteur de base de données pour s’appliquer.  
  
 La figure ci-dessous présente le type d’informations concernant le NUMA logiciel que vous verrez dans le journal des erreurs de SQL Server quand SQL Server détecte des nœuds NUMA matériels avec plus de huit cœurs physiques dans chaque nœud ou socket.  


``2016-11-14 13:39:43.17 Server      SQL Server detected 2 sockets with 12 cores per socket and 24 logical processors per socket, 48 total logical processors; using 48 logical processors based on SQL Server licensing. This is an informational message; no user action is required.``  
  **``2016-11-14 13:39:43.35 Server      Automatic soft-NUMA was enabled because SQL Server has detected hardware NUMA nodes with greater than 8 physical cores.``**  
  ``2016-11-14 13:39:43.63 Server      Node configuration: node 0: CPU mask: 0x0000000000555555:0 Active CPU mask: 0x0000000000555555:0. This message provides a description of the NUMA configuration for this computer. This is an informational message only. No user action is required.``  
  ``2016-11-14 13:39:43.63 Server      Node configuration: node 1: CPU mask: 0x0000000000aaaaaa:0 Active CPU mask: 0x0000000000aaaaaa:0. This message provides a description of the NUMA configuration for this computer. This is an informational message only. No user action is required.``  
  ``2016-11-14 13:39:43.63 Server      Node configuration: node 2: CPU mask: 0x0000555555000000:0 Active CPU mask: 0x0000555555000000:0. This message provides a description of the NUMA configuration for this computer. This is an informational message only. No user action is required.``  
  ``2016-11-14 13:39:43.63 Server      Node configuration: node 3: CPU mask: 0x0000aaaaaa000000:0 Active CPU mask: 0x0000aaaaaa000000:0. This message provides a description of the NUMA configuration for this computer. This is an informational message only. No user action is required.``

  
## <a name="manual-soft-numa"></a>Soft-NUMA manuel  
 Vous pouvez configurer [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] manuellement pour utiliser le NUMA logiciel en désactivant le NUMA logiciel automatique et en modifiant le Registre pour ajouter un masque d’affinité de configuration des nœuds. Lorsque cette méthode est utilisée, le masque soft-NUMA peut être établi comme entrée de Registre binaire, DWORD (hexadécimal ou décimal) ou QWORD (hexadécimal ou décimal). Pour configurer plus que les 32 premiers processeurs, utilisez des valeurs de Registre QWORD ou BINARY. (Les valeurs QWORD ne peuvent pas être utilisées avant [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)].) Après avoir modifié le Registre, vous devez redémarrer le [!INCLUDE[ssDE](../../includes/ssde-md.md)] pour que la configuration NUMA logiciel prenne effet.  
  
> [!TIP] Les UC sont numérotées à partir de 0.  

> [!WARNING] [!INCLUDE[ssNoteRegistry](../../includes/ssnoteregistry-md.md)]  
  
 Prenons l'exemple suivant. Un ordinateur avec huit UC ne possède pas d'accès NUMA matériel. Trois nœuds soft-NUMA sont configurés.   
L'instance A du             [!INCLUDE[ssDE](../../includes/ssde-md.md)] est configurée pour utiliser les UC de 0 à 3. Une deuxième instance du [!INCLUDE[ssDE](../../includes/ssde-md.md)] est installée et configurée pour utiliser les UC de 4 à 7. L'exemple peut être représenté visuellement de la façon suivante :  
  
 `CPUs          0  1  2  3  4  5  6  7`  
  
 `Soft-NUMA   <-N0--><-N1-><----N2---->`  
  
 `SQL Server  <instance A ><instance B>`  
  
 L'instance A, confrontée à des E/S importantes, possède maintenant deux threads d'E/S et un thread d'écriture différée, tandis que l'instance B, qui exécute des opérations nécessitant des ressources UC conséquentes, ne possède qu'un seul thread d'E/S et un seul thread d'écriture différée. Il est possible d'affecter des quantités de mémoire différentes aux instances, mais contrairement à l'accès NUMA matériel, elles reçoivent toutes deux la mémoire du même bloc mémoire du système d'exploitation et il n'existe pas d'affinité entre la mémoire et le processeur.  
  
 Le thread d'écriture différée est lié à la vue du système d'exploitation SQL des nœuds de mémoire NUMA physiques. Par conséquent, tout ce que le matériel présente sous la forme de nœuds NUMA physiques va correspondre au nombre de thread d'écriture différée qui sont créés. Pour plus d'informations, consultez   
            [How It Works: Soft NUMA, I/O Completion Thread, Lazy Writer Workers and Memory Nodes (Fonctionnement : soft-NUMA, thread d’achèvement d’E/S, threads de travail d’écriture différée et nœuds de mémoire)](http://blogs.msdn.com/b/psssql/archive/2010/04/02/how-it-works-soft-numa-i-o-completion-thread-lazy-writer-workers-and-memory-nodes.aspx).  
  
> [!NOTE] Les clés de Registre **NUMA logiciel** ne sont pas copiées quand vous mettez à niveau une instance de [!INCLUDE[ssNoVersion] (../Token/ssNoVersion_md.md)].  
  
### <a name="set-the-cpu-affinity-mask"></a>Définir le masque d'affinité de l'UC  
 Exécutez l'instruction suivante sur l'instance A de façon à la configurer pour qu'elle utilise les UC 0, 1, 2 et 3 en définissant le masque d'affinité de l'UC :  
  
```  
ALTER SERVER CONFIGURATION   
SET PROCESS AFFINITY CPU=0 TO 3;  
```  
  
 Exécutez l'instruction suivante sur l'instance B de façon à la configurer pour qu'elle utilise les UC 4, 5, 6 et 7 en définissant le masque d'affinité de l'UC :  
  
```  
ALTER SERVER CONFIGURATION   
SET PROCESS AFFINITY CPU=4 TO 7;  
```  
  
### <a name="map-soft-numa-nodes-to-cpus"></a>Mapper les nœuds soft-NUMA aux UC  
 À l'aide de l'Éditeur du Registre (regedit.exe), ajoutez les clés de Registre suivantes pour mapper le nœud soft-NUMA 0 aux UC 0 et 1, le nœud soft-NUMA 1 aux UC 2 et 3, et le nœud soft-NUMA 2 aux UC 4, 5, 6 et 7.  
  
> [!TIP] Pour spécifier les UC 60 à 63, utilisez une valeur QWORD de F000000000000000 ou une valeur BINARY de 1111000000000000000000000000000000000000000000000000000000000000.  
  
 Dans l’exemple suivant, supposons que vous disposiez d’un serveur DL580 G9 doté de 4 sockets (avec 18 noyaux par socket), chaque socket se trouvant dans son propre groupe de processeurs (« K-Group »). Vous pouvez créer une configuration soft-NUMA qui se présente comme suit (6 noyaux par nœud, 3 nœuds par groupe, 4 groupes).  
  
|Exemple pour un serveur [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] avec plusieurs « K-Groups »|Type|Nom de valeur|Données de valeur|  
|-----------------------------------------------------------------------------------------------------------------|----------|----------------|----------------|  
|HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft SQL Server\130\NodeConfiguration\Node0|DWORD|CPUMask|0x3F|  
|HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft SQL Server\130\NodeConfiguration\Node0|DWORD|Grouper|0|  
|HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft SQL Server\130\NodeConfiguration\Node1|DWORD|CPUMask|0x0fc0|  
|HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft SQL Server\130\NodeConfiguration\Node1|DWORD|Grouper|0|  
|HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft SQL Server\130\NodeConfiguration\Node2|DWORD|CPUMask|0x3f000|  
|HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft SQL Server\130\NodeConfiguration\Node2|DWORD|Grouper|0|  
|HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft SQL Server\130\NodeConfiguration\Node3|DWORD|CPUMask|0x3F|  
|HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft SQL Server\130\NodeConfiguration\Node3|DWORD|Grouper|1|  
|HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft SQL Server\130\NodeConfiguration\Node4|DWORD|CPUMask|0x0fc0|  
|HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft SQL Server\130\NodeConfiguration\Node4|DWORD|Grouper|1|  
|HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft SQL Server\130\NodeConfiguration\Node5|DWORD|CPUMask|0x3f000|  
|HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft SQL Server\130\NodeConfiguration\Node5|DWORD|Grouper|1|  
|HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft SQL Server\130\NodeConfiguration\Node6|DWORD|CPUMask|0x3F|  
|HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft SQL Server\130\NodeConfiguration\Node6|DWORD|Grouper|2|  
|HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft SQL Server\130\NodeConfiguration\Node7|DWORD|CPUMask|0x0fc0|  
|HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft SQL Server\130\NodeConfiguration\Node7|DWORD|Grouper|2|  
|HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft SQL Server\130\NodeConfiguration\Node8|DWORD|CPUMask|0x3f000|  
|HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft SQL Server\130\NodeConfiguration\Node8|DWORD|Grouper|2|  
|HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft SQL Server\130\NodeConfiguration\Node9|DWORD|CPUMask|0x3F|  
|HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft SQL Server\130\NodeConfiguration\Node9|DWORD|Grouper|3|  
|HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft SQL Server\130\NodeConfiguration\Node10|DWORD|CPUMask|0x0fc0|  
|HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft SQL Server\130\NodeConfiguration\Node10|DWORD|Grouper|3|  
|HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft SQL Server\130\NodeConfiguration\Node11|DWORD|CPUMask|0x3f000|  
|HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft SQL Server\130\NodeConfiguration\Node11|DWORD|Grouper|3|  
  
## <a name="metadata"></a>Métadonnées  
 Vous pouvez utiliser les vues de gestion dynamique (DMV) suivantes pour afficher l’état actuel et la configuration du soft-NUMA.  
  
-   [sp_configure &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-configure-transact-sql.md): affiche la valeur actuelle (40 ou 41) pour SOFTNUMA  
  
-   [sys.dm_os_nodes &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-os-nodes-transact-sql.md) : la colonne node_state_desc pour chaque nœud NUMA indique si le nœud a été créé par soft-NUMA ou non.  
  
-   [Sys.dm_os_sys_info &#40 ; Transact-SQL &#41 ;](../../relational-databases/system-dynamic-management-views/sys-dm-os-sys-info-transact-sql.md) : les colonnes softnuma et softnuma_desc affichent les valeurs de configuration.  
  
> [!NOTE] Même si vous pouvez afficher la valeur d’exécution du soft-NUMA automatique avec [sp_configure &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-configure-transact-sql.md), vous ne pouvez pas modifier sa valeur avec **sp_configure**. Vous devez utiliser l’instruction [ALTER SERVER CONFIGURATION &#40;Transact-SQL&#41;](../../t-sql/statements/alter-server-configuration-transact-sql.md) avec l’argument SET SOFTNUMA.  
  
## <a name="see-also"></a>Voir aussi  
 [Mapper les ports TCP/IP aux nœuds NUMA &#40;SQL Server&#41;](../../database-engine/configure-windows/map-tcp-ip-ports-to-numa-nodes-sql-server.md)   
 [Masque d’affinité (option de configuration de serveur)](../../database-engine/configure-windows/affinity-mask-server-configuration-option.md)   
 [ALTER SERVER CONFIGURATION &#40;Transact-SQL&#41;](../../t-sql/statements/alter-server-configuration-transact-sql.md)  
  
  
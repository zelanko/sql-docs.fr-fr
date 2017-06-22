---
title: "Surveiller l’utilisation de la mémoire | Microsoft Docs"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- tuning databases [SQL Server], memory
- monitoring server performance [SQL Server], memory usage
- isolating memory [SQL Server]
- paging rate [SQL Server]
- memory [SQL Server], monitoring usage
- monitoring [SQL Server], memory usage
- low-memory conditions
- database monitoring [SQL Server], memory usage
- available memory [SQL Server]
- page faults [SQL Server]
- monitoring performance [SQL Server], memory usage
- server performance [SQL Server], memory
ms.assetid: 1aee3933-a11c-4b87-91b7-32f5ea38c87f
caps.latest.revision: 26
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: Human Translation
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: b69c5082567467771189cb7f9e781d850680bd34
ms.contentlocale: fr-fr
ms.lasthandoff: 06/22/2017

---
# <a name="monitor-memory-usage"></a>Surveiller l'utilisation de la mémoire
  Surveillez périodiquement une instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] pour vous assurer que l'utilisation de la mémoire reste dans des limites normales.  
  
 Pour surveiller l'état de la mémoire basse, utilisez les compteurs des objets suivants :  
  
-   **Mémoire : Octets disponibles**  
  
-   **Mémoire : Pages/s**  
  
 Le compteur **Octets disponibles** indique combien d'octets de mémoire sont actuellement disponibles pour les processus. Le compteur **Pages/s** indique le nombre de pages qui ont été extraites du disque en raison de défauts de page ou écrites sur le disque pour libérer de l’espace dans la plage de travail en raison de défauts de page.  
  
 Des valeurs faibles du compteur **Octets disponibles** peuvent indiquer un manque global de mémoire sur l'ordinateur ou bien qu'un programme ne libère pas la mémoire. Une valeur élevée du compteur **Pages/s** peut indiquer une pagination excessive. Surveillez le compteur **Mémoire : Défauts de page/s** pour vérifier que l’activité du disque n’est pas due à la pagination.  
  
 Un faible taux de pagination (et donc des défauts de page) est typique, même si l'ordinateur dispose de beaucoup de mémoire disponible. Le gestionnaire de mémoire virtuelle de Microsoft Windows soustrait des pages à [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] et à d'autres processus quand il réduit la taille des parties actives de ces processus. Son activité a tendance à provoquer des défauts de page. Pour déterminer si [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ou un autre processus provoque une pagination excessive, surveillez le compteur **Processus : Défauts de page/s** pour l’instance du processus [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
 Pour plus d'informations sur la résolution d'une pagination excessive, consultez la documentation du système d'exploitation Windows.  
  
## <a name="isolating-memory-used-by-sql-server"></a>Isolement de la mémoire utilisée par SQL Server  
 Par défaut, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] modifie dynamiquement ses besoins en mémoire en fonction des ressources système disponibles. Si [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] a besoin de plus de mémoire, il demande au système d'exploitation de déterminer si de la mémoire physique libre est disponible. Dans l'affirmative, il l'utilise. Si [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] n'a pas besoin de la mémoire qui lui est actuellement allouée, il la libère pour le système d'exploitation. Vous pouvez cependant ignorer cette option pour utiliser dynamiquement de la mémoire au moyen des options de configuration du serveur **minservermemory**et **maxservermemory** Pour plus d'informations, consultez [Options de mémoire du serveur](../../database-engine/configure-windows/server-memory-server-configuration-options.md).  
  
 Pour surveiller la mémoire utilisée par [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , examinez les compteurs de performances suivants :  
  
-   **Process: Working Set**  
  
-   **SQL Server: Buffer Manager: Buffer Cache Hit Ratio**  
  
-   **SQL Server: Buffer Manager: Database Pages**  
  
-   **SQL Server: Memory Manager: Total Server Memory (KB)**  
  
 Le compteur **WorkingSet** indique la quantité de mémoire utilisée par un processus. Si ce nombre est régulièrement inférieur à la quantité de mémoire définie par les options du serveur **min server memory** et **max server memory** , [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] est configuré pour utiliser trop de mémoire.  
  
 Le compteur **Buffer Cache Hit Ratio** est propre à une application. Cependant, une valeur supérieure ou égale à 90 % est souhaitable. Ajoutez de la mémoire jusqu'à ce que cette valeur soit régulièrement supérieure à 90 %. Une valeur supérieure à 90 pour cent indique que plus de 90 % de toutes les requêtes ont été satisfaites à partir de la mémoire cache.  
  
 Si la valeur du compteur **TotalServerMemory (KB)** est régulièrement élevée par rapport à la quantité de mémoire physique de l’ordinateur, cela peut indiquer que davantage de mémoire est nécessaire.  
  
## <a name="determining-current-memory-allocation"></a>Détermination de l'allocation de mémoire actuelle  
 La requête suivante retourne des informations sur la mémoire allouée actuellement.  
  
```  
SELECT  
(physical_memory_in_use_kb/1024) AS Memory_usedby_Sqlserver_MB,  
(locked_page_allocations_kb/1024) AS Locked_pages_used_Sqlserver_MB,  
(total_virtual_address_space_kb/1024) AS Total_VAS_in_MB,  
process_physical_memory_low,  
process_virtual_memory_low  
FROM sys.dm_os_process_memory;  
```  
  
  

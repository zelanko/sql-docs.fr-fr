---
title: "Configuration du stockage des tables optimisées en mémoire | Microsoft Docs"
ms.custom:
- SQL2016_New_Updated
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine-imoltp
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 6e005de0-3a77-4b91-b497-14cc0f9f6605
caps.latest.revision: 7
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
translationtype: Human Translation
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 0250c8370960dc17adf13c020c51bfc603b111c8
ms.lasthandoff: 04/11/2017

---
# <a name="configuring-storage-for-memory-optimized-tables"></a>Configuration du stockage des tables optimisées en mémoire
  Vous devez configurer des opérations d'entrée/sortie par seconde (IOPS) et la capacité de stockage.  
  
## <a name="storage-capacity"></a>Capacité de stockage  
 Utilisez les informations contenues dans [Estimer les besoins en mémoire des tables optimisées en mémoire](../../relational-databases/in-memory-oltp/estimate-memory-requirements-for-memory-optimized-tables.md) pour estimer la taille en mémoire des tables durables optimisées en mémoire de la base de données. Les index n'étant pas conservés pour les tables optimisées en mémoire, n'incluez pas la taille des index. Une fois que vous avez déterminé la taille, vous devez fournir l'espace disque correspondant à quatre fois la taille des tables durables en mémoire.  
  
## <a name="storage-iops"></a>E/S par seconde dédiées au stockage  
 [!INCLUDE[hek_2](../../includes/hek-2-md.md)] peut augmenter considérablement le débit de la charge de travail. Par conséquent, il est important de s'assurer que les E/S ne forment pas un goulet d'étranglement.  
  
-   Lorsque vous migrez des tables sur disque vers des tables optimisées en mémoire, vérifiez que le journal des transactions se trouve sur un support de stockage capable de prendre en charge le surcroît d'activité du journal des transactions. Par exemple, si votre support de stockage prend en charge des opérations du journal des transactions à 100 Mo/s et que les tables optimisées en mémoire offrent des performances cinq fois supérieures, le support de stockage du journal des transactions doit être en mesure de prendre en charge une amélioration des performances cinq fois supérieure, pour empêcher l'activité du journal des transactions de devenir un goulot d'étranglement des performances.  
  
-   Les tables optimisées en mémoire sont conservées dans des fichiers distribués sur un ou plusieurs conteneurs. Chaque conteneur doit généralement être mappé à son propre axe et est utilisé pour augmenter la capacité de stockage et améliorer les performances d’E/S par seconde (IOPS). Vous devez vous assurer que ces IOPS séquentielles du support de stockage peuvent prendre en charge une augmentation 3 fois supérieure dans le débit du journal des transactions.  
  
     Par exemple, si les tables optimisées en mémoire génèrent 500 Mo/sec d’activité dans le journal des transactions, le stockage pour ces tables doit prendre en charge 1,5 Go/sec d’IOPS. La nécessité de prendre en charge une triple augmentation du débit du journal des transactions s'explique par le fait que les paires de fichiers de données et delta sont d'abord écrites avec les données initiales, puis doivent être lues/réécrites dans le cadre d'une opération de fusion.  
  
     Le temps de récupération des tables optimisées en mémoire est un autre facteur entrant en compte dans l’estimation des IOPS pour le stockage. Les données des tables durables doivent être lues en mémoire avant qu'une base de données puisse être mise à la disposition des applications. Généralement, le chargement de données dans les tables optimisées en mémoire peut être effectué à la vitesse des opérations d’E/S par seconde (IOPS). Si le stockage total des tables durables, optimisées en mémoire, s'élève à 60 Go et que vous souhaitez pouvoir charger ces données en une minute, les IOPS du stockage doivent être définies à 1 Go/sec.  
  
-   Si vous avez un nombre d’axes pair, contrairement à SQL Server 2014, les fichiers de point de contrôle seront distribués uniformément entre tous les axes.  
  
## <a name="encryption"></a>Chiffrement  
 Dans [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)], le stockage des tables optimisées en mémoire est chiffré dans le cadre de l’activation de TDE (Transparent Data Encryption) sur la base de données. Pour plus d’informations, consultez [Transparent Data Encryption &#40;TDE&#41;](../../relational-databases/security/encryption/transparent-data-encryption-tde.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Création et gestion du stockage des objets optimisés en mémoire](../../relational-databases/in-memory-oltp/creating-and-managing-storage-for-memory-optimized-objects.md)  
  
  

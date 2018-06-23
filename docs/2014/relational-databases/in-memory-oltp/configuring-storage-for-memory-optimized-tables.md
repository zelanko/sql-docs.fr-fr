---
title: Configuration du stockage des tables optimisées en mémoire | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine-imoltp
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 6e005de0-3a77-4b91-b497-14cc0f9f6605
caps.latest.revision: 5
author: stevestein
ms.author: sstein
manager: jhubbard
ms.openlocfilehash: 4d13b8b46066eb6c2c8c855859fdab0114269700
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36038343"
---
# <a name="configuring-storage-for-memory-optimized-tables"></a>Configuration du stockage des tables optimisées en mémoire
  Vous devez configurer des opérations d'entrée/sortie par seconde (IOPS) et la capacité de stockage.  
  
## <a name="storage-capacity"></a>Capacité de stockage  
 Utilisez les informations contenues dans [Estimer les besoins en mémoire des tables optimisées en mémoire](memory-optimized-tables.md) pour estimer la taille en mémoire des tables durables optimisées en mémoire de la base de données. Les index n'étant pas conservés pour les tables mémoire optimisées, n'incluez pas la taille des index. Une fois que vous avez déterminé la taille, vous devez fournir l'espace disque correspondant à quatre fois la taille des tables durables en mémoire.  
  
## <a name="storage-performance"></a>Performances de stockage  
 [!INCLUDE[hek_2](../../includes/hek-2-md.md)] peut augmenter considérablement le débit de la charge de travail. Par conséquent, il est important de s'assurer que les E/S ne forment pas un goulet d'étranglement.  
  
-   Lorsque vous migrez des tables sur disque vers des tables mémoire optimisées, vérifiez que le journal des transactions se trouve sur un support de stockage capable de prendre en charge le surcroît d'activité du journal des transactions. Par exemple, si votre support de stockage prend en charge des opérations du journal des transactions à 100 Mo/s et que les tables mémoire optimisées offrent des performances cinq fois supérieures, le support de stockage du journal des transactions doit être en mesure de prendre en charge une amélioration des performances cinq fois supérieure, pour empêcher l'activité du journal des transactions de devenir un goulot d'étranglement des performances.  
  
-   Les tables mémoire optimisées sont conservées dans des fichiers distribués sur un ou plusieurs conteneurs. Chaque conteneur doit généralement être mappé à son propre axe, et est utilisé pour augmenter la capacité de stockage et améliorer les performances. Vous devez vous assurer que ces IOPS séquentielles du support de stockage peuvent prendre en charge une augmentation 3 fois supérieure dans le débit du journal des transactions.  
  
     Par exemple, si les tables optimisées en mémoire génèrent 500 Mo/sec d’activité dans le journal des transactions, le stockage des tables optimisées en mémoire doit prendre en charge 1,5 Go/sec. La nécessité de prendre en charge une fois 3 augmentation du débit du journal des transactions provient de l’observation que les paires de fichiers de données et delta sont d’abord écrites avec les données initiales et puis doivent être lues/réécrites dans le cadre d’une opération de fusion.  
  
     Le temps de récupération des tables mémoire optimisées est un autre facteur entrant en compte dans l'estimation du débit pour le stockage. Les données des tables durables doivent être lues en mémoire avant qu'une base de données puisse être mise à la disposition des applications. Généralement, le chargement de données dans les tables mémoire optimisées peut être effectué à la vitesse des opérations d’E/S par seconde (IOPS). Si le stockage total des tables durables, mémoire optimisées, s'élève à 60 Go et que vous souhaitez pouvoir charger ces données en une minute, les IOPS du stockage doivent être définies à 1 Go/sec.  
  
-   Si vous avez un nombre pair d'axes, vous devez créer deux fois le nombre de conteneurs, chaque paire étant mappée au même axe. Cela est nécessaire pour répartir les IOPS et le stockage. Pour plus d’informations, consultez [le mémoire optimisé groupe de fichiers](the-memory-optimized-filegroup.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Création et gestion du stockage des objets mémoire optimisés](creating-and-managing-storage-for-memory-optimized-objects.md)  
  
  
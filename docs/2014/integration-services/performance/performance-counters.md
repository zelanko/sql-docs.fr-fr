---
title: Compteurs de performances | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- logs [Integration Services], performance counters
- performance counters [Integration Services]
- data flow [Integration Services], performance
- counters [Integration Services]
- data flow engine [Integration Services]
ms.assetid: 11e17f4e-72ed-44d7-a71d-a68937a78e4c
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 70694b2814ab23ad13e29a1348e7bfb73d884fbc
ms.sourcegitcommit: 334cae1925fa5ac6c140e0b2c38c844c477e3ffb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/13/2018
ms.locfileid: "53367671"
---
# <a name="performance-counters"></a>Compteurs de performances
  [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] installe un ensemble de compteurs de performances qui vous permettent d’analyser les performances du moteur de flux de données. Par exemple, le compteur Mémoires tampon spoulées permet de déterminer si des tampons de données sont écrits temporairement sur le disque lors de l'exécution d'un package. Cette permutation diminue les performances et indique que la mémoire de l'ordinateur est insuffisante.  
  
> [!NOTE]  
>  Si vous installez [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] sur un ordinateur qui exécute [!INCLUDE[winxpsvr](../../includes/winxpsvr-md.md)], puis que vous mettez à niveau cet ordinateur vers [!INCLUDE[firstref_longhorn](../../includes/firstref-longhorn-md.md)], le processus de mise à niveau supprime les compteurs de performances de [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] de l’ordinateur. Pour restaurer les compteurs de performances de [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] sur l’ordinateur, exécutez l’installation de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] en mode réparation.  
  
 Le tableau suivant décrit les compteurs de performance.  
  
|Compteur de performances|Description|  
|-------------------------|-----------------|  
|Octets BLOB lus|Le nombre d'octets des données d'objet BLOB (Binary Large Object) que le moteur de flux de données a lu à partir de toutes les sources.|  
|Octets BLOB écrits|Le nombre d'octets des données BLOB que le moteur de flux de données a écrit sur toutes les destinations.|  
|Fichiers BLOB utilisés|Nombre de fichiers BLOB que le moteur de flux de données utilise actuellement pour la mise en file d'attente.|  
|Mémoire tampon|La quantité de mémoire en cours d'utilisation. Cela peut inclure à la fois la mémoire physique et la mémoire virtuelle. Quand ce nombre est supérieur à la quantité de mémoire physique, le compte **Mémoires tampon spoulées** augmente, ce qui indique une augmentation de l’échange de mémoire. L'augmentation de l'échange de mémoire ralentit les performances du moteur de flux de données.|  
|Tampons en cours d'utilisation|Nombre d'objets de mémoire tampon, de tous les types, que tous les composants de flux de données et le moteur de flux de données utilisent actuellement.|  
|Mémoires tampon spoulées|Nombre de mémoires tampon actuellement écrites sur le disque. Si le moteur de flux de données est à cours de mémoire physique, les mémoires tampons non utilisées actuellement sont écrites sur le disque puis rechargées en cas de besoin.|  
|Mémoire tampon plate|Le volume total de mémoire, en octets, que toutes les mémoires tampons plates utilisent. Les mémoires tampons plates sont des blocs de mémoire utilisés par un composant pour stocker des données. Une mémoire tampon plate est un grand bloc d'octets, auquel l'accès se fait octet par octet.|  
|Mémoires tampons plates en cours d'utilisation|Nombre de mémoires tampons plates que le moteur de flux de données utilise. Toutes les mémoires tampons plates sont des mémoires tampons privées.|  
|Mémoire tampon privée|Le volume total de mémoire utilisé par toutes les mémoires tampons privées. Une mémoire tampon n'est pas privée si le moteur de flux de données la crée pour prendre en charge le flux de données. Une mémoire tampon privée est une mémoire tampon qu'une transformation utilise seulement pour un travail temporaire. Par exemple, la transformation d'agrégation utilise des mémoires tampons privées pour son travail.|  
|Mémoires tampons privées en cours d'utilisation|Le nombre de mémoires tampons utilisées par les transformations.|  
|Lignes lues|Le nombre de lignes produites par une source. Le nombre n'inclut pas les lignes lues à partir des tables de références par la transformation de recherche.|  
|Lignes écrites|Le nombre de lignes offertes vers une destination. Le nombre ne reflète pas les lignes écrites vers la banque de données de destination.|  
  
 Vous utilisez le composant logiciel enfichable MMC (Microsoft Management Console) Performance pour créer un journal qui capture les compteurs de performances.  
  
 Pour plus d’informations sur l’amélioration des performances, consultez [Fonctionnalités de performances de flux de données](../data-flow/data-flow-performance-features.md).  
  
## <a name="obtain-performance-counter-statistics"></a>Obtenir des statistiques sur les compteurs de performance  
 Pour les projets [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] déployés sur le serveur [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)], vous pouvez obtenir des statistiques sur les compteurs de performances à l’aide de la fonction [dm_execution_performance_counters &#40;base de données SSISDB&#41;](/sql/integration-services/functions-dm-execution-performance-counters).  
  
 Dans l'exemple suivant, la fonction retourne des statistiques pour une exécution en cours ayant l'ID 34.  
  
```  
select * from [catalog].[dm_execution_performance_counters] (34)  
```  
  
 Dans l’exemple suivant, la fonction retourne des statistiques pour toutes les exécutions en cours sur le serveur [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] .  
  
```  
select * from [catalog].[dm_execution_performance_counters] (NULL)  
  
```  
  
> [!IMPORTANT]  
>  Si vous êtes membre du rôle de base de données `ssis_admin`, les statistiques de performance de toutes les exécutions en cours sont retournées.  Si vous n'êtes pas membre du rôle de base de données `ssis_admin`, les statistiques de performance des exécutions en cours pour lesquelles vous disposez d'autorisations de lecture, sont retournées.  
  
## <a name="related-content"></a>Contenu associé  
  
-   Outil : [SSIS Performance Visualization for Business Intelligence Development Studio (projet CodePlex)](https://go.microsoft.com/fwlink/?LinkId=146626), sur le site codeplex.com.  
  
-   Vidéo : [Mesure et présentation des performances de vos packages SSIS dans l’entreprise (Vidéo liée à SQL Server)](https://go.microsoft.com/fwlink/?LinkId=150497), sur le site msdn.microsoft.com.  
  
-   Article du Support technique : [Le compteur de performance SSIS n’est plus disponible dans l’Analyseur de performances après la mise à niveau vers Windows Server 2008](https://go.microsoft.com/fwlink/?LinkId=235319), sur le site support.microsoft.com.  
  
## <a name="see-also"></a>Voir aussi  
 [Exécution de projets et de packages](../packages/run-integration-services-ssis-packages.md)  
  
  

---
title: Garbage collection XTP de SQL Server | Microsoft Docs
description: Découvrez l’objet de performance Garbage collection XTP de SQL Server, qui contient les compteurs liés au garbage collector du moteur OLTP en mémoire.
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
ms.assetid: 64ae91e5-b420-44b4-af1a-f8bca83d7f41
author: julieMSFT
ms.author: jrasnick
ms.openlocfilehash: 8575295948b5560f25dc0e967fa419699587af7b
ms.sourcegitcommit: 9470c4d1fc8d2d9d08525c4f811282999d765e6e
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/17/2020
ms.locfileid: "86457961"
---
# <a name="sql-server-xtp-garbage-collection"></a>Garbage collection XTP de SQL Server
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  L’objet de performance Garbage collection XTP de SQL Server contient les compteurs liés au garbage collector du moteur OLTP en mémoire.  
  
 Ce tableau décrit les compteurs **Garbage collection XTP de SQL Server** .  
  
|Compteur|Description|  
|-------------|-----------------|  
|**Nouvelles tentatives d'analyse d'angles inutilisés par seconde (sortie GC)**|Nombre de tentatives d'analyse dues à des conflits d'écriture lors des nettoyages d'angles inutilisés indiqué par le garbage collector (en moyenne), par seconde. Il s'agit d'un compteur de très bas niveau, non destiné au client.|  
|**Éléments de travail de GC principal par seconde**|Nombre d'éléments de travail traités par le thread GC principal.|  
|**Élément de travail de GC parallèle par seconde**|Nombre de fois qu'un thread parallèle a exécuté un élément de travail GC.|  
|**Lignes traitées par seconde**|Nombre de lignes traitées par le garbage collector (en moyenne), par seconde.|  
|**Lignes traitées par seconde (d'abord dans le compartiment, puis supprimées)**|Nombre de lignes traitées par le garbage collector qui étaient initialement dans le compartiment de hachage correspondant, et qui ont pu ensuite être supprimées immédiatement (en moyenne), par seconde.|  
|**Lignes traitées par seconde (d'abord dans le compartiment)**|Nombre de lignes traitées par le garbage collector qui étaient initialement dans le compartiment de hachage correspondant (en moyenne), par seconde.|  
|**Lignes traitées par seconde (marquées pour la dissociation)**|Nombre de lignes traitées par le garbage collector qui étaient déjà marquées pour la dissociation (en moyenne), par seconde.|  
|**Lignes traitées par seconde (pas de nettoyage requis)**|Nombre de lignes traitées par le garbage collector qui ne nécessitent pas de nettoyage d'angle inutilisé (en moyenne), par seconde.|  
|**Lignes expirées lors des nettoyages, supprimées par seconde**|Nombre de lignes expirées supprimées lors des nettoyages d'angles inutilisés (en moyenne), par seconde.|  
|**Lignes expirées lors des nettoyages, touchées par seconde**|Nombre de lignes expirées touchées lors des nettoyages d'angles inutilisés (en moyenne), par seconde.|  
|**Lignes expirant touchées lors des nettoyages, par seconde**|Nombre de lignes expirant touchées lors des nettoyages d'angles inutilisés (en moyenne), par seconde.|  
|**Lignes touchées lors des nettoyages, par seconde**|Nombre de lignes touchées lors des nettoyages d'angles inutilisés (en moyenne), par seconde.|  
|**Analyses de nettoyage démarrées par seconde**|Nombre d'analyses de nettoyage d'angles inutilisés démarrées (en moyenne), par seconde.|  
  
## <a name="see-also"></a>Voir aussi  
 [SQL Server XTP &#40;OLTP en mémoire&#41;, compteurs de performances](../../relational-databases/performance-monitor/sql-server-xtp-in-memory-oltp-performance-counters.md)  
  
  

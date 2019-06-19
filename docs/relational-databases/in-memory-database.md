---
title: Base de données en mémoire | Microsoft Docs
ms.date: 05/22/2019
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- in-memory database
- feature, in-memory database
- in-memory
ms.assetid: 11f8017e-5bc3-4bab-8060-c16282cfbac1
author: briancarrig
ms.author: brcarrig
manager: amitban
ms.openlocfilehash: e4e0e6622a2a313b85dfa00df8c88044486f75f5
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "65994997"
---
# <a name="in-memory-database"></a>Base de données en mémoire

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

« Base de données en mémoire » est un terme général désignant les fonctionnalités dans SQL Server qui tirent parti des technologies en mémoire. Cette page sera mise à jour au fil du développement de nouvelles fonctionnalités en mémoire.

## <a name="hybrid-buffer-pool"></a>Pool de mémoires tampons hybride

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

Le [pool de mémoires tampons hybride](../database-engine/configure-windows/hybrid-buffer-pool.md) permet au moteur de base de données d’accéder directement aux pages de données dans les fichiers de base de données stockés sur des appareils à mémoire persistante (PMEM).

## <a name="memory-optimized-tempdb-metadata"></a>Métadonnées tempdb à mémoire optimisée

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

[!INCLUDE[sql-server-2019](../includes/sssqlv15-md.md)] introduit une nouvelle fonctionnalité, les [métadonnées tempdb à mémoire optimisée](./databases/tempdb-database.md#memory-optimized-tempdb-metadata), qui supprime efficacement certains goulots de contention et déverrouille un nouveau niveau de scalabilité pour les charges de travail de base de données tempdb lourdes.

## <a name="in-memory-oltp"></a>OLTP en mémoire

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

[OLTP en mémoire](./in-memory-oltp/in-memory-oltp-in-memory-optimization.md) est la technologie de premier plan disponible dans [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] et [!INCLUDE[ssSDS](../includes/sssds-md.md)] pour optimiser les performances du traitement transactionnel, de l’ingestion et du chargement des données, et des scénarios de données temporaires.

**S’applique à  :** [!INCLUDE[ssSQL14](../includes/sssql14-md.md)] à [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].

## <a name="persistent-memory-support-for-linux"></a>Prise en charge de la mémoire persistante pour Linux

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-linuxonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-linuxonly.md)]

[!INCLUDE[sqlv15](../includes/sssqlv15-md.md)] ajoute la prise en charge des appareils à mémoire persistante (PMEM) pour Linux, fournissant une mise en compatibilité complète des fichiers de données et de journaux de transactions placés dans la [mémoire persistante](../linux/sql-server-linux-configure-pmem.md).

**S’applique à  :** [!INCLUDE[sqlv15](../includes/sssqlv15-md.md)] à [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].

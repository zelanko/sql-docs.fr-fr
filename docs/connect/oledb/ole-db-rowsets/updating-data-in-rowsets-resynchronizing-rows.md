---
title: Resynchronisation des lignes | Documents Microsoft
description: Resynchronisation des lignes à l’aide du pilote OLE DB pour SQL Server
ms.custom: ''
ms.date: 03/26/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- synchronization [OLE DB]
- IRowsetResynch interface
- resynchronizing rows
- data updates [SQL Server], OLE DB
author: pmasl
ms.author: Pedro.Lopes
manager: craigg
ms.openlocfilehash: aab5c457d7cfb0755ef15ac995b67f4e33cb791b
ms.sourcegitcommit: f16003fd1ca28b5e06d5700e730f681720006816
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/11/2018
ms.locfileid: "35306238"
---
# <a name="updating-data-in-rowsets---resynchronizing-rows"></a>Mise à jour des données dans les ensembles de lignes - resynchronisation des lignes
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  Le pilote OLE DB pour SQL Server prend en charge **IRowsetResynch** sur [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] curseur pris en charge les ensembles de lignes uniquement. **IRowsetResynch** n’est pas disponible à la demande. Le consommateur doit demander l'interface avant d'ouvrir l'ensemble de lignes.  
  
## <a name="see-also"></a>Voir aussi  
 [Mise à jour des données dans les ensembles de lignes](../../oledb/ole-db-rowsets/updating-data-in-rowsets.md)  
  
  

---
title: Création d’ensembles de lignes avec ICommand::Execute | Documents Microsoft
description: Création d’ensembles de lignes avec ICommand::Execute
ms.custom: ''
ms.date: 03/26/2018
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: ''
ms.component: ole-db-rowsets
ms.reviewer: ''
ms.suite: sql
ms.technology:
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- rowsets [OLE DB], creating
- OLE DB Driver for SQL Server, rowsets
- OLE DB rowsets, creating
- Execute method
author: pmasl
ms.author: Pedro.Lopes
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: c6768c8b5e09dbce8b0177368d9ff8b2c63b74fa
ms.sourcegitcommit: 9f4330a4b067deea396b8567747a6771f35e6eee
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/30/2018
---
# <a name="creating-rowsets-with-icommandexecute"></a>Création d'ensembles de lignes avec ICommand::Execute
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  Pour les ensembles de lignes créés à l’aide de la **ICommand::Execute** méthode, les propriétés que vous souhaitez dans l’ensemble de lignes résultant peut limiter le texte de la commande. Cela est particulièrement important pour les consommateurs qui prennent en charge un texte de commande dynamique.  
  
 Le pilote OLE DB pour SQL Server ne peut pas utiliser [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] curseurs pour prendre en charge les résultats de plusieurs ensembles de lignes générés par de nombreuses commandes. Lorsqu'un consommateur demande un ensemble de lignes qui requiert la prise en charge de curseurs [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], une erreur se produit si le texte de commande génère plusieurs ensembles de lignes comme résultat. Pour plus d’informations, consultez [commandes générant plusieurs ensembles de lignes résultats](../../oledb/ole-db-commands/commands-generating-multiple-rowset-results.md).  
  
 Défilement pilote OLE DB pour les ensembles de lignes de SQL Server sont pris en charge par [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] les curseurs. [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] impose des limitations aux curseurs qui sont sensibles aux modifications effectuées par d'autres utilisateurs de la base de données. En particulier, dans certains curseurs, les lignes ne peuvent pas être triées ; en outre, toute tentative de création d'un ensemble de lignes à l'aide d'une commande qui contient une clause SQL ORDER BY peut échouer. Pour plus d’informations, consultez [ensembles de lignes et curseurs SQL Server](../../oledb/ole-db-rowsets/rowsets-and-sql-server-cursors.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Ensembles de lignes](../../oledb/ole-db-rowsets/rowsets.md)  
  
  

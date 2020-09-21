---
title: ICommand (pilote OLE DB) | Microsoft Docs
description: En savoir plus sur le comportement de la méthode ICommand::Execute spécifique à OLE DB Driver pour SQL Server.
ms.custom: ''
ms.date: 06/14/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: connectivity
ms.topic: reference
helpviewer_keywords:
- ICommand [OLE DB Driver for SQL Server]
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: bf787628804f3597fa724c0ab6313a450e365d58
ms.sourcegitcommit: c95f3ef5734dec753de09e07752a5d15884125e2
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/25/2020
ms.locfileid: "88861899"
---
# <a name="icommand-ole-db"></a>ICommand (OLE DB)
[!INCLUDE [SQL Server](../../../includes/applies-to-version/sql-asdb-asdbmi-asa-pdw.md)]

[!INCLUDE[Driver_OLEDB_Download](../../../includes/driver_oledb_download.md)]

  Cet article décrit le comportement OLE DB spécifique à OLE DB Driver pour SQL Server.  
  
## <a name="icommandexecute"></a>ICommand::Execute  
 L'insertion de données dont la taille est supérieure à celle d'une colonne provoque généralement une erreur. Toutefois, il existe des cas où S_OK est retourné et `dwStatus` est défini sur DBSTATUS_S_TRUNCATED. Voici quelques scénarios où cela se produit généralement :

- Lors de l’insertion de données avec des paramètres  
- Où la colonne n’est pas suffisamment grande pour contenir les données  
- Lorsque `ICommandWithParameters::SetParameterInfo` n’a pas été appelé  
  
## <a name="see-also"></a>Voir aussi  
 [Interfaces &#40;OLE DB&#41;](../../oledb/ole-db-interfaces/oledb-driver-for-sql-server-ole-db-interfaces.md)
  
  

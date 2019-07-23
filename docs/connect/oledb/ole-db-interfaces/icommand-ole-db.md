---
title: ICommand (OLE DB) | Microsoft Docs
description: ICommand, interface (OLE DB)
ms.custom: ''
ms.date: 06/14/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: connectivity
ms.topic: reference
helpviewer_keywords:
- ICommand [OLE DB Driver for SQL Server]
author: pmasl
ms.author: pelopes
ms.openlocfilehash: 722536a086abf280cacded3ecd2cd0d450a417ae
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "67994492"
---
# <a name="icommand-ole-db"></a>ICommand (OLE DB)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

[!INCLUDE[Driver_OLEDB_Download](../../../includes/driver_oledb_download.md)]

  Cet article décrit OLE DB comportement propre à OLE DB pilote pour SQL Server.  
  
## <a name="icommandexecute"></a>ICommand::Execute  
 L'insertion de données dont la taille est supérieure à celle d'une colonne provoque généralement une erreur. Toutefois, il existe des cas où S_OK sera retourné, mais *dwStatus* aura la valeur DBSTATUS_S_TRUNCATED. Ceci se produit généralement lors de l’insertion de données avec des paramètres, quand la colonne n’est pas assez large pour contenir les données et que **ICommandWithParameters::SetParameterInfo** n’a pas été appelé.  
  
## <a name="see-also"></a>Voir aussi  
 [Interfaces &#40;OLE DB&#41;](../../oledb/ole-db-interfaces/oledb-driver-for-sql-server-ole-db-interfaces.md)
  
  

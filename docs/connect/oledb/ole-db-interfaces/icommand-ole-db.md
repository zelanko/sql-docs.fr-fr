---
title: ICommand (OLE DB) | Documents Microsoft
description: Interface ICommand (OLE DB)
ms.custom: ''
ms.date: 03/26/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: ''
ms.component: ole-db-interfaces
ms.reviewer: ''
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- ICommand [OLE DB Driver for SQL Server]
author: pmasl
ms.author: Pedro.Lopes
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 7db2582c204d99b809f72e1ce367f0c5f006fb15
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
---
# <a name="icommand-ole-db"></a>ICommand (OLE DB)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  Cet article décrit le comportement OLE DB qui est spécifique au pilote OLE DB pour SQL Server.  
  
## <a name="icommandexecute"></a>ICommand::Execute  
 L'insertion de données dont la taille est supérieure à celle d'une colonne provoque généralement une erreur. Toutefois, il existe des cas où S_OK sera retourné, mais *dwStatus* aura la valeur DBSTATUS_S_TRUNCATED. Il se produit généralement lors de l’insertion de données avec des paramètres, où la colonne n’est pas suffisamment grande pour contenir les données, et **ICommandWithParameters::SetParameterInfo** n’a pas été appelée.  
  
## <a name="see-also"></a>Voir aussi  
 [Interfaces & #40 ; OLE DB & #41 ;](../../oledb/ole-db-interfaces/oledb-driver-for-sql-server-ole-db-interfaces.md)
  
  

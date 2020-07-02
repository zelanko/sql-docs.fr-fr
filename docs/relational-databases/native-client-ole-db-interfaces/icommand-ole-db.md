---
title: ICommand (OLE DB) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- ICommand [SQL Server Native Client]
ms.assetid: 5e24b3a0-0658-44fc-b653-f4c52f9eb328
author: markingmyname
ms.author: maghan
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: e04f91926d9855031626a1ecb7097b30c68e8d58
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85785437"
---
# <a name="icommand-ole-db"></a>ICommand (OLE DB)
[!INCLUDE[SQL Server Azure SQL Database Synapse Analytics PDW ](../../includes/applies-to-version/sql-asdb-asdbmi-asdw-pdw.md)]

  Cette rubrique présente le comportement OLE DB qui est spécifique à [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client.  
  
## <a name="icommandexecute"></a>ICommand::Execute  
 L'insertion de données dont la taille est supérieure à celle d'une colonne provoque généralement une erreur. Toutefois, il existe des cas où S_OK sera retourné, mais *dwStatus* aura la valeur DBSTATUS_S_TRUNCATED. Cette situation se produit généralement lors de l'insertion de données avec des paramètres, lorsque la colonne n'est pas assez large pour contenir les données et que **ICommandWithParameters::SetParameterInfo** n'a pas été appelé.  
  
## <a name="see-also"></a>Voir aussi  
 [Interfaces &#40;OLE DB&#41;](https://msdn.microsoft.com/library/34c33364-8538-45db-ae41-5654481cda93)  
  
  

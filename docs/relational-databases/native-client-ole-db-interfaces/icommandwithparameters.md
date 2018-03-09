---
title: ICommandWithParameters | Documents Microsoft
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: 
ms.component: native-client-ole-db-interfaces
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 66644c70-def7-46d8-8c47-b883292a0288
caps.latest.revision: "6"
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 04f369ba934f768ddd94754406b4ce0915e3018b
ms.sourcegitcommit: a0aa5e611a0e6ebb74ac1e2f613e8916dc7a7617
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/24/2018
---
# <a name="icommandwithparameters"></a>ICommandWithParameters
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

  Améliorations apportées au début du moteur de base de données avec [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] autoriser ICommandWithParameters::GetParameterInfo obtenir des descriptions plus exactes des résultats attendus. Ces résultats plus précis peuvent différer des valeurs retournées par CommandWithParameters::GetParameterInfo dans les versions précédentes de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Pour plus d'informations, consultez [Metadata Discovery](../../relational-databases/native-client/features/metadata-discovery.md).  
  
 Également depuis la [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)], lors de l’appel d’ICommandWithParameters::SetParameterInfo, la valeur passée à la *pwszName* paramètre doit être un identificateur valide. Pour plus d'informations, consultez [Database Identifiers](../../relational-databases/databases/database-identifiers.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Interfaces &#40; OLE DB &#41;](http://msdn.microsoft.com/library/34c33364-8538-45db-ae41-5654481cda93)  
  
  

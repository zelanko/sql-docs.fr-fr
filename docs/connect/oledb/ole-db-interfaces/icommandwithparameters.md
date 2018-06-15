---
title: ICommandWithParameters | Documents Microsoft
description: Interface ICommandWithParameters
ms.custom: ''
ms.date: 03/26/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: reference
author: pmasl
ms.author: Pedro.Lopes
manager: craigg
ms.openlocfilehash: 647c161b2a12ae530edfe610b7d3cbac3b745e50
ms.sourcegitcommit: f16003fd1ca28b5e06d5700e730f681720006816
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/11/2018
ms.locfileid: "35305093"
---
# <a name="icommandwithparameters"></a>ICommandWithParameters
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  Améliorations apportées au début du moteur de base de données avec [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)] autoriser ICommandWithParameters::GetParameterInfo obtenir des descriptions plus exactes des résultats attendus. Ces résultats plus précis peuvent différer des valeurs retournées par CommandWithParameters::GetParameterInfo dans les versions précédentes de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. Pour plus d’informations, consultez [de découverte des métadonnées](../../oledb/features/metadata-discovery.md).  
  
 Également depuis la [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)], lors de l’appel d’ICommandWithParameters::SetParameterInfo, la valeur passée à la *pwszName* paramètre doit être un identificateur valide. Pour plus d'informations, consultez [Database Identifiers](../../../relational-databases/databases/database-identifiers.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Interfaces &#40;OLE DB&#41;](../../oledb/ole-db-interfaces/oledb-driver-for-sql-server-ole-db-interfaces.md) 
  
  

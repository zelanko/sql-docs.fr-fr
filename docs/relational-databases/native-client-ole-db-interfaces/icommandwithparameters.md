---
title: ICommandWithParameters | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.suite: sql
ms.technology: native-client
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: 66644c70-def7-46d8-8c47-b883292a0288
caps.latest.revision: 6
author: MightyPen
ms.author: genemi
manager: craigg
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017'
ms.openlocfilehash: 08acaa9ef4d1dae0a1cd104b4703edb8a0836437
ms.sourcegitcommit: 4cd008a77f456b35204989bbdd31db352716bbe6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/06/2018
ms.locfileid: "39555449"
---
# <a name="icommandwithparameters"></a>ICommandWithParameters
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

  Améliorations apportées au début du moteur de base de données avec [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] autoriser ICommandWithParameters::GetParameterInfo obtenir des descriptions plus exactes des résultats attendus. Ces résultats plus exacts peuvent différer des valeurs retournées par CommandWithParameters::GetParameterInfo dans les versions précédentes de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Pour plus d’informations, consultez [Découverte des métadonnées](../../relational-databases/native-client/features/metadata-discovery.md).  
  
 Depuis [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)], lors de l’appel d’ICommandWithParameters::SetParameterInfo, la valeur passée au paramètre *pwszName* doit être un identificateur valide. Pour plus d'informations, consultez [Database Identifiers](../../relational-databases/databases/database-identifiers.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Interfaces &#40;OLE DB&#41;](http://msdn.microsoft.com/library/34c33364-8538-45db-ae41-5654481cda93)  
  
  

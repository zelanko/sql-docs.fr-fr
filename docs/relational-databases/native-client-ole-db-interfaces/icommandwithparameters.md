---
title: ICommandWithParameters | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
ms.assetid: 66644c70-def7-46d8-8c47-b883292a0288
author: markingmyname
ms.author: maghan
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: d8510b5a9713ee58611678df1bae2885a69c5d79
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85785423"
---
# <a name="icommandwithparameters"></a>ICommandWithParameters
[!INCLUDE[SQL Server Azure SQL Database Synapse Analytics PDW ](../../includes/applies-to-version/sql-asdb-asdbmi-asdw-pdw.md)]

  Les améliorations apportées au moteur de base de données à compter de [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] permettent à ICommandWithParameters::GetParameterInfo d'obtenir des descriptions plus exactes des résultats attendus. Ces résultats plus exacts peuvent différer des valeurs retournées par CommandWithParameters::GetParameterInfo dans les versions précédentes de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Pour plus d’informations, consultez [Découverte des métadonnées](../../relational-databases/native-client/features/metadata-discovery.md).  
  
 Depuis [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)], lors de l’appel d’ICommandWithParameters::SetParameterInfo, la valeur passée au paramètre *pwszName* doit être un identificateur valide. Pour plus d'informations, consultez [Database Identifiers](../../relational-databases/databases/database-identifiers.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Interfaces &#40;OLE DB&#41;](https://msdn.microsoft.com/library/34c33364-8538-45db-ae41-5654481cda93)  
  
  

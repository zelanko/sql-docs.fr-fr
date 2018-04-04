---
title: Découverte des métadonnées | Documents Microsoft
description: Découverte des métadonnées dans le pilote OLE DB pour SQL Server
ms.custom: ''
ms.date: 03/26/2018
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: ''
ms.component: oledb|features
ms.reviewer: ''
ms.suite: sql
ms.technology:
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
author: pmasl
ms.author: Pedro.Lopes
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 5990632392ec4656af7f655fcbd1b19b29346066
ms.sourcegitcommit: 9f4330a4b067deea396b8567747a6771f35e6eee
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/30/2018
---
# <a name="metadata-discovery"></a>Découverte des métadonnées
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  L’amélioration de découverte des métadonnées dans [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)] permet le pilote OLE DB pour les applications SQL Server pour vous assurer que la colonne ou des métadonnées de paramètre retournées par l’exécution d’une requête sont identique à ou compatibles avec le format de métadonnées que vous avez spécifié avant exécution de la requête. Vous recevrez une erreur si les métadonnées retournées après l'exécution de la requête ne sont pas compatibles avec le format des métadonnées que vous avez spécifié avant l'exécution de la requête.  
  
 Bcp et les interfaces IBCPSession et IBCPSession2, vous pouvez maintenant spécifier un retardée en lecture (découverte des métadonnées retardée) pour éviter la découverte des métadonnées pour les opérations de requête. Cela améliore la performance et élimine les échecs de découverte des métadonnées.  
  
 Si vous développez une application à l’aide du pilote OLE DB pour SQL Server, mais vous connecter à une version de serveur antérieure à [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)], fonctionnalité correspond à la version du serveur de découverte des métadonnées.  
  
## <a name="remarks"></a>Notes   
 Les fonctions membres OLE DB suivantes ont été améliorées dans [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)] pour fournir une fonctionnalité améliorée de découverte des métadonnées :  
  
-   IColumnsInfo::GetColumnInfo  
  
-   IColumnsRowset::GetColumnsRowset  
  
-   ICommandWithParameters::GetParameterInfo (consultez [ICommandWithParameters](../../oledb/ole-db-interfaces/icommandwithparameters.md) pour plus d’informations)  
  
 Vous verrez également une amélioration des performances lors de la spécification de format de métadonnées à l’aide de IBCPSession::BCPSetBulkMode  
  
 La détection améliorée des métadonnées dans le pilote OLE DB pour SQL Server est possible grâce à l’ajout de deux procédures stockées dans [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)]:  
  
-   sp_describe_first_result_set  
  
-   sp_describe_undeclared_parameters  
  
## <a name="see-also"></a>Voir aussi  
 [Pilote de base de données OLE pour les fonctionnalités SQL Server](../../oledb/features/oledb-driver-for-sql-server-features.md)  
  
  

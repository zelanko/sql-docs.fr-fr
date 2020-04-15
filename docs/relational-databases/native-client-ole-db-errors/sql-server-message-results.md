---
title: Résultats des messages SQL Server | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- SQL Server Native Client OLE DB provider, errors
- errors [OLE DB], SQL Server message results
- OLE DB error handling, SQL Server message results
ms.assetid: 6663c6f9-def1-4d9e-845b-2085e5efc401
author: markingmyname
ms.author: maghan
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 577b609fd2f878e6c97010cac004e0b10b3a4e4e
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81300965"
---
# <a name="sql-server-message-results"></a>Résultats des messages SQL Server
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  Les [!INCLUDE[tsql](../../includes/tsql-md.md)] relevés suivants [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ne génèrent pas de rames de fournisseurs de DB OLE de clients autochtones ou un décompte des lignes touchées lorsqu’elles sont exécutées :  
  
-   PRINT  
  
-   RAISERROR avec une gravité égale ou inférieure à 10  
  
-   DBCC  
  
-   SET SHOWPLAN  
  
-   SET STATISTICS  
  
 Ces instructions retournent un ou plusieurs messages d'information ou entraînent le renvoi par [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] de messages d'information au lieu de résultats sous forme d'ensemble de lignes ou de nombre. Lors de l’exécution réussie, le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] fournisseur de DB OLE de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] client autochtone retourne S_OK, et les messages sont disponibles pour le consommateur fournisseur de DB OLE de client autochtone.  
  
 Le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] fournisseur de DB OLE de client autochtone retourne S_OK et dispose d’un ou de plusieurs messages d’information disponibles à la suite de l’exécution de nombreuses [!INCLUDE[tsql](../../includes/tsql-md.md)] déclarations ou de l’exécution par le consommateur d’une [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] fonction de membre du fournisseur de DB OLE de client autochtone.  
  
 Le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] fournisseur de fournisseur native Client OLE DB qui permet une spécification dynamique du texte de requête doit vérifier les interfaces d’erreur après l’exécution de chaque fonction membre, quelle que soit la valeur du code de retour, la présence ou l’absence d’une référence d’interface **IRowset** ou **IMultipleResults** retournée, ou un décompte des lignes touchées.  
  
## <a name="see-also"></a>Voir aussi  
 [Erreurs](../../relational-databases/native-client-ole-db-errors/errors.md)  
  
  

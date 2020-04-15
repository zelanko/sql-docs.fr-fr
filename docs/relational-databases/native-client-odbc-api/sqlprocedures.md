---
title: SQLProcedures ( france) Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
apitype: DLLExport
helpviewer_keywords:
- SQLProcedures function
ms.assetid: ec41f017-f5e0-40ef-913a-65d206068631
author: markingmyname
ms.author: maghan
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 14ff76504c9a36657be60ba4855cf252474071d7
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81302368"
---
# <a name="sqlprocedures"></a>SQLProcedures
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  Toutes les procédures stockées [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] retournent une valeur. **SQLProcedures signale** SQL_PT_FUNCTION pour la colonne de l’ensemble de résultats PROCEDURE_TYPE.  
  
 **SQLProcedures** renvoie SQL_SUCCESS des valeurs existent ou non pour les paramètres *CatalogName, SchemaName* ou *ProcName.* **SQLFetch** retourne SQL_NO_DATA lorsque des valeurs non valides sont utilisées dans ces paramètres.  
  
 **SQLProcedures** peut être exécuté sur un curseur serveur statique. Une tentative d’exécuter **SQLProcedures** sur un curseur updatable (dynamique ou keyset) reviendra SQL_SUCCESS_WITH_INFO, ce qui indique que le type de curseur a été modifié.  
  
 **SQLProcedures renvoie** des informations sur toutes les procédures dont les noms correspondent *à ProcName* et peuvent être exécutés par l’utilisateur actuel, ou pour lesquels l’utilisateur actuel a obtenu l’autorisation VIEW DEFINITION.  
  
## <a name="see-also"></a>Voir aussi  
 [Fonction SQLProcedures](https://go.microsoft.com/fwlink/?LinkId=59364)   
 [Détails de l’implémentation d’API ODBC](../../relational-databases/native-client-odbc-api/odbc-api-implementation-details.md)  
  
  

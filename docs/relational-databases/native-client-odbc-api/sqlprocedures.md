---
title: SQLProcedures | Documents Microsoft
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.suite: sql
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apitype: DLLExport
helpviewer_keywords:
- SQLProcedures function
ms.assetid: ec41f017-f5e0-40ef-913a-65d206068631
caps.latest.revision: 35
author: MightyPen
ms.author: genemi
manager: craigg
monikerRange: '>= aps-pdw-2016 || = azuresqldb-current || = azure-sqldw-latest || >= sql-server-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: 95eced372cab2e6eb0807958f4fa871feaa4bf19
ms.sourcegitcommit: a78fa85609a82e905de9db8b75d2e83257831ad9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/18/2018
ms.locfileid: "35697490"
---
# <a name="sqlprocedures"></a>SQLProcedures
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

  Toutes les procédures stockées [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] retournent une valeur. **SQLProcedures** sql_pt_function pour le jeu de résultats PROCEDURE_TYPE de colonne.  
  
 **SQLProcedures** retourne SQL_SUCCESS qu’il existe des valeurs ou non *CatalogName, SchemaName* ou *ProcName* paramètres. **SQLFetch** retourne SQL_NO_DATA lorsque des valeurs non valides sont utilisées dans ces paramètres.  
  
 **SQLProcedures** peut être exécutée sur un curseur côté serveur statique. Toute tentative d’exécution **SQLProcedures** sur un curseur de mettre à jour (dynamique ou jeu de clés) retourne SQL_SUCCESS_WITH_INFO, indiquant que le type de curseur a été modifié.  
  
 **SQLProcedures** retourne des informations sur toutes les procédures dont les noms correspondent *ProcName* et peut être exécutée par l’utilisateur actuel, ou pour lequel l’utilisateur actuel a reçu l’autorisation VIEW DEFINITION.  
  
## <a name="see-also"></a>Voir aussi  
 [SQLProcedures, fonction](http://go.microsoft.com/fwlink/?LinkId=59364)   
 [Détails de l’implémentation d’API ODBC](../../relational-databases/native-client-odbc-api/odbc-api-implementation-details.md)  
  
  

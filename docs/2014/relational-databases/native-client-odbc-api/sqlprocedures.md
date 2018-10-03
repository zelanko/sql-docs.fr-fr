---
title: SQLProcedures | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
topic_type:
- apiref
helpviewer_keywords:
- SQLProcedures function
ms.assetid: ec41f017-f5e0-40ef-913a-65d206068631
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: feb5cd9df428ec09441ae1ebe0ff1cb051660754
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48203989"
---
# <a name="sqlprocedures"></a>SQLProcedures
  Toutes les procédures stockées [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] retournent une valeur. **SQLProcedures** sql_pt_function pour le jeu de résultats PROCEDURE_TYPE de colonne.  
  
 **SQLProcedures** retourne SQL_SUCCESS qu’il existe des valeurs ou non *CatalogName, SchemaName* ou *ProcName* paramètres. **SQLFetch** retourne SQL_NO_DATA lorsque des valeurs non valides sont utilisées dans ces paramètres.  
  
 **SQLProcedures** peut être exécutée sur un curseur côté serveur statique. Une tentative d’exécution **SQLProcedures** sur un curseur modifiable (dynamique ou jeu de clés) retourne SQL_SUCCESS_WITH_INFO, indiquant que le type de curseur a été modifié.  
  
 **SQLProcedures** retourne des informations sur toutes les procédures dont les noms correspondent *ProcName* et peut être exécutée par l’utilisateur actuel, ou pour lequel l’utilisateur actuel a reçu l’autorisation VIEW DEFINITION.  
  
## <a name="see-also"></a>Voir aussi  
 [SQLProcedures, fonction](http://go.microsoft.com/fwlink/?LinkId=59364)   
 [Détails de l’implémentation d’API ODBC](odbc-api-implementation-details.md)  
  
  

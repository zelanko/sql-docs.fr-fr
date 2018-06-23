---
title: SQLProcedures | Documents Microsoft
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
topic_type:
- apiref
helpviewer_keywords:
- SQLProcedures function
ms.assetid: ec41f017-f5e0-40ef-913a-65d206068631
caps.latest.revision: 34
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 26c59b042ba861684402a4b79ce7cb1b5d77e53a
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36043589"
---
# <a name="sqlprocedures"></a>SQLProcedures
  Toutes les procédures stockées [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] retournent une valeur. **SQLProcedures** sql_pt_function pour le jeu de résultats PROCEDURE_TYPE de colonne.  
  
 **SQLProcedures** retourne SQL_SUCCESS qu’il existe des valeurs ou non *CatalogName, SchemaName* ou *ProcName* paramètres. **SQLFetch** retourne SQL_NO_DATA lorsque des valeurs non valides sont utilisées dans ces paramètres.  
  
 **SQLProcedures** peut être exécutée sur un curseur côté serveur statique. Toute tentative d’exécution **SQLProcedures** sur un curseur de mettre à jour (dynamique ou jeu de clés) retourne SQL_SUCCESS_WITH_INFO, indiquant que le type de curseur a été modifié.  
  
 **SQLProcedures** retourne des informations sur toutes les procédures dont les noms correspondent *ProcName* et peut être exécutée par l’utilisateur actuel, ou pour lequel l’utilisateur actuel a reçu l’autorisation VIEW DEFINITION.  
  
## <a name="see-also"></a>Voir aussi  
 [SQLProcedures, fonction](http://go.microsoft.com/fwlink/?LinkId=59364)   
 [Détails de l’implémentation d’API ODBC](odbc-api-implementation-details.md)  
  
  
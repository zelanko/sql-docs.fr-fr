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
ms.openlocfilehash: b0001f1d6e45e855b884028a595a2b61263c2e58
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/26/2020
ms.locfileid: "63046677"
---
# <a name="sqlprocedures"></a>SQLProcedures
  Toutes les procédures stockées [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] retournent une valeur. Les rapports **SQLProcedures** SQL_PT_FUNCTION pour la colonne de l’ensemble de résultats PROCEDURE_TYPE.  
  
 **SQLProcedures** retourne SQL_SUCCESS si des valeurs existent pour les paramètres *nomcatalogue, SchemaName* ou *procname* . **SQLFetch** retourne SQL_NO_DATA lorsque des valeurs non valides sont utilisées dans ces paramètres.  
  
 Les **SQLProcedures** peuvent être exécutés sur un curseur côté serveur statique. Une tentative d’exécution de **SQLProcedures** sur un curseur pouvant être mis à jour (dynamique ou de jeu de clés) retourne SQL_SUCCESS_WITH_INFO, ce qui indique que le type de curseur a été modifié.  
  
 **SQLProcedures** retourne des informations sur les procédures dont les noms correspondent à *procname* et peuvent être exécutés par l’utilisateur actuel, ou pour lesquels l’utilisateur actuel a reçu l’autorisation View definition.  
  
## <a name="see-also"></a>Voir aussi  
 [SQLProcedures (fonction)](https://go.microsoft.com/fwlink/?LinkId=59364)   
 [Détails de l’implémentation d’API ODBC](odbc-api-implementation-details.md)  
  
  

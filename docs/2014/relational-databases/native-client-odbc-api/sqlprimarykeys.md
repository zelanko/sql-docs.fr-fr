---
title: SQLPrimaryKeys | Documents Microsoft
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
- SQLPrimaryKeys function
ms.assetid: bc61cd5b-d2f4-4f87-abc7-743cf9ea772d
caps.latest.revision: 37
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: cb0dc440025730c278206a751a5ce741b69b0f6e
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36040880"
---
# <a name="sqlprimarykeys"></a>SQLPrimaryKeys
  Une table peut contenir une ou plusieurs colonnes qui peuvent servir d’identificateurs de ligne unique, et les tables créées sans une contrainte PRIMARY KEY retournent un résultat vide SQLPrimaryKeys la valeur. La fonction ODBC [SQLSpecialColumns](sqlspecialcolumns.md) candidats identificateurs pour les tables sans clés primaires de lignes.  
  
 SQLPrimaryKeys retourne SQL_SUCCESS qu’il existe des valeurs ou non *CatalogName*, *SchemaName*, ou *TableName* paramètres. SQLFetch retourne SQL_NO_DATA lorsque des valeurs non valides sont utilisées dans ces paramètres.  
  
 SQLPrimaryKeys peut être exécutée sur un curseur côté serveur statique. Toute tentative d’exécution SQLPrimaryKeys sur un curseur de mettre à jour (dynamique ou jeu de clés) retourne SQL_SUCCESS_WITH_INFO, indiquant que le type de curseur a été modifié.  
  
 Le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] pilote ODBC Native Client prend en charge les informations de rapport pour les tables des serveurs liés en acceptant un nom en deux parties pour le *CatalogName* paramètre : *nom_serveur_lié.Nom_Catalogue*.  
  
## <a name="sqlprimarykeys-and-table-valued-parameters"></a>SQLPrimaryKeys et paramètres table  
 Si l’attribut d’instruction SQL_SOPT_SS_NAME_SCOPE a la valeur SQL_SS_NAME_SCOPE_TABLE_TYPE, plutôt que sa valeur par défaut SQL_SS_NAME_SCOPE_TABLE, SQLPrimaryKeys retourne des informations sur les colonnes clés primaires des types de table. Pour plus d’informations sur SQL_SOPT_SS_NAME_SCOPE, consultez [SQLSetStmtAttr](sqlsetstmtattr.md).  
  
 Pour plus d’informations sur les paramètres table, consultez [paramètres table &#40;ODBC&#41;](../native-client-odbc-table-valued-parameters/table-valued-parameters-odbc.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Fonction SQLPrimaryKeys](http://go.microsoft.com/fwlink/?LinkId=59361)   
 [Détails de l’implémentation d’API ODBC](odbc-api-implementation-details.md)  
  
  
---
title: SQLPrimaryKeys | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
topic_type:
- apiref
helpviewer_keywords:
- SQLPrimaryKeys function
ms.assetid: bc61cd5b-d2f4-4f87-abc7-743cf9ea772d
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: a12392f9e70fec2fae3b7790b43f12779b8868b5
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63046676"
---
# <a name="sqlprimarykeys"></a>SQLPrimaryKeys
  Une table peut contenir une ou plusieurs colonnes pouvant servir d’identificateurs de lignes uniques, et les tables créées sans une contrainte PRIMARY KEY retournent un résultat vide à SQLPrimaryKeys. La fonction ODBC [SQLSpecialColumns](sqlspecialcolumns.md) candidats identificateurs pour les tables sans clés primaires de lignes.  
  
 SQLPrimaryKeys retourne SQL_SUCCESS qu’il existe des valeurs ou non *CatalogName*, *SchemaName*, ou *TableName* paramètres. SQLFetch retourne SQL_NO_DATA lorsque des valeurs non valides sont utilisées dans ces paramètres.  
  
 SQLPrimaryKeys peut être exécutée sur un curseur côté serveur statique. Une tentative d’exécution SQLPrimaryKeys sur un curseur modifiable (dynamique ou jeu de clés) retourne SQL_SUCCESS_WITH_INFO, indiquant que le type de curseur a été modifié.  
  
 Le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] pilote ODBC Native Client prend en charge des informations de rapport pour les tables des serveurs liés en acceptant un nom en deux parties pour le *CatalogName* paramètre : *Nom_serveur_lié.Nom_Catalogue*.  
  
## <a name="sqlprimarykeys-and-table-valued-parameters"></a>SQLPrimaryKeys et paramètres table  
 Si l’attribut d’instruction SQL_SOPT_SS_NAME_SCOPE a la valeur SQL_SS_NAME_SCOPE_TABLE_TYPE, plutôt que sa valeur par défaut SQL_SS_NAME_SCOPE_TABLE, SQLPrimaryKeys retourne des informations sur les colonnes clés primaires des types de tables. Pour plus d'informations sur SQL_SOPT_SS_NAME_SCOPE, consultez [SQLSetStmtAttr](sqlsetstmtattr.md).  
  
 Pour plus d’informations sur les paramètres table, consultez [paramètres table &#40;ODBC&#41;](../native-client-odbc-table-valued-parameters/table-valued-parameters-odbc.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Fonction SQLPrimaryKeys](https://go.microsoft.com/fwlink/?LinkId=59361)   
 [Détails de l’implémentation d’API ODBC](odbc-api-implementation-details.md)  
  
  

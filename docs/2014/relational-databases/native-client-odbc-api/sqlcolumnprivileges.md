---
title: SQLColumnPrivileges | Documents Microsoft
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
- SQLColumnPrivileges function
ms.assetid: c78acd4e-8668-4abc-9bc9-6ad381965863
caps.latest.revision: 33
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: c13c432b43be893cdc0612fe9ed54fc7b612b213
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36044507"
---
# <a name="sqlcolumnprivileges"></a>SQLColumnPrivileges
  **SQLColumnPrivileges** retourne SQL_SUCCESS qu’il existe des valeurs ou non le*CatalogName*, *SchemaName*, *TableName*, ou  *Nom de colonne* paramètres. **SQLFetch** retourne SQL_NO_DATA lorsque des valeurs non valides sont utilisées dans ces paramètres.  
  
 **SQLColumnPrivileges** peut être exécutée sur un curseur côté serveur statique. Toute tentative d’exécution **SQLColumnPrivileges** sur un curseur de mettre à jour (dynamique ou jeu de clés) retourne SQL_SUCCESS_WITH_INFO, indiquant que le type de curseur a été modifié.  
  
 Le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] pilote ODBC Native Client prend en charge les informations de rapport pour les tables des serveurs liés en acceptant un nom en deux parties pour le *CatalogName* paramètre : *nom_serveur_lié.Nom_Catalogue*.  
  
## <a name="see-also"></a>Voir aussi  
 [SQLColumnPrivileges, fonction](http://go.microsoft.com/fwlink/?LinkId=59335)   
 [Détails de l’implémentation d’API ODBC](odbc-api-implementation-details.md)  
  
  
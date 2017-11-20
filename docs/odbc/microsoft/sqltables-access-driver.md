---
title: SQLTables (pilote Access) | Documents Microsoft
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: microsoft
ms.reviewer: 
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- SQLTables function [ODBC], Access Driver
- Access driver [ODBC], SQLTables
ms.assetid: 94423cf9-341a-4db6-bb10-8f5448df7fc3
caps.latest.revision: 6
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 4f6ca61bf3bc72e5640271e1eaed55cd10664d04
ms.contentlocale: fr-fr
ms.lasthandoff: 09/09/2017

---
# <a name="sqltables-access-driver"></a>SQLTables (pilote Access)
> [!NOTE]  
>  Cette rubrique fournit des informations spécifiques au pilote Access. Pour obtenir des informations générales sur cette fonction, consultez la rubrique appropriée sous [référence de l’API ODBC](../../odbc/reference/syntax/odbc-api-reference.md).  
  
|Argument|Commentaires|  
|--------------|--------------|  
|*szTableOwner*|Le seul argument valide pour *szTableOwner* a la valeur NULL, car aucun des pilotes prend en charge les noms de propriétaire. Avec *szTableOwner* la valeur NULL, toutes les tables sont retournées. NULL est retourné dans la colonne TABLE_OWNER.|  
|*szTableQualifier*|Dans la colonne TABLE_QUALIFIER, **SQLTables** retourne le chemin d’accès à un fichier de base de données.|  
|*SzTableType*|Lorsque le pilote Microsoft Access est utilisé, « TABLE système » est pris en charge pour *szTableType* pour les tables système, « SYNONYME » est pris en charge pour les tables attachées, et « Vue » est pris en charge pour le retour à la ligne des requêtes.|  
  
## <a name="see-also"></a>Voir aussi  
 [SQLTables, fonction](../../odbc/reference/syntax/sqltables-function.md)


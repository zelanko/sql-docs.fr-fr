---
title: SQLTransact (pilote Access) | Documents Microsoft
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: microsoft
ms.reviewer: 
ms.suite: sql
ms.technology: drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Access driver [ODBC], SQLTransact
- SQLTransact function [ODBC], Access Driver
ms.assetid: 892b79c7-9e20-4d1f-bc60-d4b25694ca25
caps.latest.revision: "6"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 041bd1a56db21dda374a8bd279c890e187f04beb
ms.sourcegitcommit: 7f8aebc72e7d0c8cff3990865c9f1316996a67d5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/20/2017
---
# <a name="sqltransact-access-driver"></a>SQLTransact (pilote Access)
> [!NOTE]  
>  Cette rubrique fournit des informations spécifiques au pilote Access. Pour obtenir des informations générales sur cette fonction, consultez la rubrique appropriée sous [référence de l’API ODBC](../../odbc/reference/syntax/odbc-api-reference.md).  
  
 Lorsque le pilote Microsoft Access est utilisé, SQL_COMMIT et SQL_ROLLBACK sont pris en charge pour le *fType* argument dans un appel à **SQLTransact**.  
  
 Si une défaillance se produit pendant le processus de validation, la base de données concernée peut être réparé à l’aide de l’option de base de données dans le programme d’installation du pilote Microsoft Access, ou via l’utilisation du mot clé REPAIR_DB dans le **SQLConfigDataSource** (fonction).

---
title: SQLPrimaryKeys (le pilote ODBC Visual FoxPro) | Documents Microsoft
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
- SQLPrimaryKeys function [ODBC], Visual FoxPro ODBC Driver
ms.assetid: 8dbe2903-efdc-45e0-a079-9e357c5fd81b
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 8906d8672c44eaf6a2e8cc6fbfc63189a4dcbda2
ms.contentlocale: fr-fr
ms.lasthandoff: 09/09/2017

---
# <a name="sqlprimarykeys-visual-foxpro-odbc-driver"></a>SQLPrimaryKeys (le pilote ODBC Visual FoxPro)
> [!NOTE]  
>  Cette rubrique contient des informations spécifiques au pilote ODBC Visual FoxPro. Pour obtenir des informations générales sur cette fonction, consultez la rubrique appropriée sous [référence de l’API ODBC](../../odbc/reference/syntax/odbc-api-reference.md).  
  
 Prise en charge : complet  
  
 Conformité d’API ODBC : Niveau 2  
  
 Retourne les noms de colonnes qui composent la clé primaire pour une table. L’implémentation du pilote ODBC Visual FoxPro de **SQLPrimaryKeys** se comporte comme suit :  
  
-   Ignore le *szTableOwner* et *cbTableOwner* arguments.  
  
-   S’applique uniquement aux sources de données qui sont [bases de données](../../odbc/microsoft/visual-foxpro-terminology.md). Le pilote retourne l’erreur « Pilote ne prend pas en charge cette fonction » si la source de données est un répertoire de [libre tables](../../odbc/microsoft/visual-foxpro-terminology.md).  
  
 Pour plus d’informations, consultez [SQLPrimaryKeys](../../odbc/reference/syntax/sqlprimarykeys-function.md) dans les *de référence du programmeur ODBC*.


---
title: SQLAllocConnect (le pilote ODBC Visual FoxPro) | Documents Microsoft
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
- SQLAllocConnect function [ODBC], Visual FoxPro ODBC Driver
ms.assetid: 70d48b12-def5-475c-b8e1-654a55fdfe0f
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 5614b69fddd5b5430f15e8266bef6872d4294f4e
ms.contentlocale: fr-fr
ms.lasthandoff: 09/09/2017

---
# <a name="sqlallocconnect-visual-foxpro-odbc-driver"></a>SQLAllocConnect (le pilote ODBC Visual FoxPro)
> [!NOTE]  
>  Cette rubrique contient des informations spécifiques au pilote ODBC Visual FoxPro. Pour obtenir des informations générales sur cette fonction, consultez la rubrique appropriée sous [référence de l’API ODBC](../../odbc/reference/syntax/odbc-api-reference.md).  
  
 Prise en charge : complet  
  
 Conformité d’API ODBC : Niveau principal  
  
 Alloue de la mémoire pour un handle de connexion, *pas*, dans l’environnement identifié par *henv*. Le Gestionnaire de pilotes traite cet appel et appelle du pilote **SQLAllocConnect** chaque fois que [SQLConnect](../../odbc/microsoft/sqlconnect-visual-foxpro-odbc-driver.md), **SQLBrowseConnect**, ou [SQLDriverConnect](../../odbc/microsoft/sqldriverconnect-visual-foxpro-odbc-driver.md) est appelée.  
  
 Pour plus d’informations, consultez [SQLAllocConnect](../../odbc/reference/syntax/sqlallocconnect-function.md) dans les *de référence du programmeur ODBC*.


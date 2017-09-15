---
title: SQLGetStmtOption (le pilote ODBC Visual FoxPro) | Documents Microsoft
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- SQLGetStmtOption function [ODBC], Visual FoxPro ODBC Driver
ms.assetid: 984a8b1d-f12c-420c-8be4-f555114c764b
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 601dd559d7bf13d1a12d032d8431a8c3fe0287d4
ms.contentlocale: fr-fr
ms.lasthandoff: 09/09/2017

---
# <a name="sqlgetstmtoption-visual-foxpro-odbc-driver"></a>SQLGetStmtOption (le pilote ODBC Visual FoxPro)
> [!NOTE]  
>  Cette rubrique contient des informations spécifiques au pilote ODBC Visual FoxPro. Pour obtenir des informations générales sur cette fonction, consultez la rubrique appropriée sous [référence de l’API ODBC](../../odbc/reference/syntax/odbc-api-reference.md).  
  
 Prise en charge : complet  
  
 Compatibilité d’API ODBC : Un niveau  
  
 Retourne le paramètre actuel d’une option de l’instruction.  
  
|*FOption*|Valeur renvoyée|  
|---------------|-------------|  
|SQL_GET_BOOKMARK|valeur d’entier 32 bits qui est le signet pour le numéro d’enregistrement en cours|  
|SQL_ROW_NUMBER|valeur d’entier 32 bits spécifiant la position de la ligne actuelle dans le résultat|  
|SQL_TRANSLATE_DLL|Erreur : « Driver non compatibles avec »|  
  
 Le pilote ODBC Visual FoxPro ne contient aucune traduction DLL.  
  
 Pour plus d’informations, consultez [SQLGetStmtOption](../../odbc/reference/syntax/sqlgetstmtoption-function.md) dans les *de référence du programmeur ODBC*.

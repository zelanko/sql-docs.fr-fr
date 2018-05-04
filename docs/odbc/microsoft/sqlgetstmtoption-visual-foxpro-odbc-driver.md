---
title: SQLGetStmtOption (le pilote ODBC Visual FoxPro) | Documents Microsoft
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: odbc
ms.reviewer: ''
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- SQLGetStmtOption function [ODBC], Visual FoxPro ODBC Driver
ms.assetid: 984a8b1d-f12c-420c-8be4-f555114c764b
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 6cb9e9178d7b90afaaa5cd324f79459a14a2dcc6
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
---
# <a name="sqlgetstmtoption-visual-foxpro-odbc-driver"></a>SQLGetStmtOption (le pilote ODBC Visual FoxPro)
> [!NOTE]  
>  Cette rubrique contient des informations spécifiques au pilote ODBC Visual FoxPro. Pour obtenir des informations générales sur cette fonction, consultez la rubrique appropriée sous [référence de l’API ODBC](../../odbc/reference/syntax/odbc-api-reference.md).  
  
 Prise en charge : complet  
  
 Compatibilité d’API ODBC : Un niveau  
  
 Retourne le paramètre actuel d’une option de l’instruction.  
  
|*fOption*|Valeur renvoyée|  
|---------------|-------------|  
|SQL_GET_BOOKMARK|valeur d’entier 32 bits qui est le signet pour le numéro d’enregistrement en cours|  
|SQL_ROW_NUMBER|valeur d’entier 32 bits spécifiant la position de la ligne actuelle dans le résultat|  
|SQL_TRANSLATE_DLL|Erreur : « Driver non compatibles avec »|  
  
 Le pilote ODBC Visual FoxPro ne contient aucune traduction DLL.  
  
 Pour plus d’informations, consultez [SQLGetStmtOption](../../odbc/reference/syntax/sqlgetstmtoption-function.md) dans les *de référence du programmeur ODBC*.

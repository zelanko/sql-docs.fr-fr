---
title: SQLGetStmtOption (Visual FoxPro ODBC Driver) Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SQLGetStmtOption function [ODBC], Visual FoxPro ODBC Driver
ms.assetid: 984a8b1d-f12c-420c-8be4-f555114c764b
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 2624783f7bd55903f5741c62190626e455a9096d
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81295139"
---
# <a name="sqlgetstmtoption-visual-foxpro-odbc-driver"></a>SQLGetStmtOption (pilote ODBC Visual FoxPro)
> [!NOTE]  
>  Ce sujet contient des informations visuelles spécifiques à FoxPro ODBC Driver. Pour plus d’informations générales sur cette fonction, voir le sujet approprié sous [ODBC API Référence](../../odbc/reference/syntax/odbc-api-reference.md).  
  
 Soutien: Complet  
  
 Conformité API ODBC : Niveau 1  
  
 Retourne le paramètre actuel d’une option d’instruction.  
  
|*FOption (FOption)*|Retours|  
|---------------|-------------|  
|SQL_GET_BOOKMARK|Valeur integer 32 bits qui est le signet du nombre record actuel|  
|SQL_ROW_NUMBER|32 bits integer spécifiant la position de la ligne actuelle dans l’ensemble de résultats|  
|SQL_TRANSLATE_DLL|Erreur: "Driver pas capable"|  
  
 Le visual FoxPro ODBC Driver n’a pas de DLL de traduction.  
  
 Pour plus d’informations, voir [SQLGetStmtOption](../../odbc/reference/syntax/sqlgetstmtoption-function.md) dans la *référence du programmeur ODBC*.

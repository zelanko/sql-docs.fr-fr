---
description: SQLGetStmtOption (pilote ODBC Visual FoxPro)
title: SQLGetStmtOption (pilote ODBC Visual FoxPro) | Microsoft Docs
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
ms.openlocfilehash: e57456ca05e39c12b83da80cd19c34f482c3d8df
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/17/2020
ms.locfileid: "88340085"
---
# <a name="sqlgetstmtoption-visual-foxpro-odbc-driver"></a>SQLGetStmtOption (pilote ODBC Visual FoxPro)
> [!NOTE]  
>  Cette rubrique contient des informations spécifiques au pilote ODBC Visual FoxPro. Pour obtenir des informations générales sur cette fonction, consultez la rubrique appropriée sous référence de l' [API ODBC](../../odbc/reference/syntax/odbc-api-reference.md).  
  
 Prise en charge : complète  
  
 Conformité de l’API ODBC : niveau 1  
  
 Retourne le paramètre actuel d’une option d’instruction.  
  
|*FOption*|Retours|  
|---------------|-------------|  
|SQL_GET_BOOKMARK|valeur entière 32 bits qui est le signet du numéro d’enregistrement actif|  
|SQL_ROW_NUMBER|entier 32 bits spécifiant la position de la ligne actuelle dans le jeu de résultats|  
|SQL_TRANSLATE_DLL|Erreur : « pilote non conforme »|  
  
 Le pilote ODBC Visual FoxPro n’a pas de dll de traduction.  
  
 Pour plus d’informations, consultez [SQLGetStmtOption](../../odbc/reference/syntax/sqlgetstmtoption-function.md) dans le *Guide de référence du programmeur ODBC*.

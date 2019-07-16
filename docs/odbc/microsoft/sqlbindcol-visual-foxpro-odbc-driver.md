---
title: SQLBindCol (pilote ODBC de Visual FoxPro) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SQLBindCol function [ODBC], Visual FoxPro ODBC Driver
ms.assetid: 984d6605-39ba-4d33-ac94-22625bfa6107
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 706677b71d1243baac0ca576bb3087d50abb6796
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "68098293"
---
# <a name="sqlbindcol-visual-foxpro-odbc-driver"></a>SQLBindCol (pilote ODBC Visual FoxPro)
> [!NOTE]  
>  Cette rubrique contient des informations spécifiques au pilote ODBC Visual FoxPro. Pour obtenir des informations générales sur cette fonction, consultez la rubrique appropriée sous [ODBC API Reference](../../odbc/reference/syntax/odbc-api-reference.md).  
  
 Prise en charge : Complète  
  
 Conformité d’API ODBC : Niveau principal  
  
 Affecte l’espace de stockage pour une colonne de résultats et spécifie le type du résultat. Lorsque [SQLFetch](../../odbc/microsoft/sqlfetch-visual-foxpro-odbc-driver.md) ou [SQLExtendedFetch](../../odbc/microsoft/sqlextendedfetch-visual-foxpro-odbc-driver.md) est appelée, le pilote place les données pour toutes les colonnes liées aux emplacements attribué. Consultez [SQLGetTypeInfo](../../odbc/microsoft/sqlgettypeinfo-visual-foxpro-odbc-driver.md) pour le mappage entre les types de données ODBC et Visual FoxPro.  
  
 Pour plus d’informations, consultez [SQLBindCol](../../odbc/reference/syntax/sqlbindcol-function.md) dans le *de référence du programmeur ODBC*.

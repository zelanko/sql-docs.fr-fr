---
title: SQLSpecialColumns (le pilote ODBC Visual FoxPro) | Documents Microsoft
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: odbc
ms.reviewer: 
ms.suite: sql
ms.technology: drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: SQLSpecialColumns function [ODBC], Visual FoxPro ODBC Driver
ms.assetid: b72a978d-6a60-475a-b7d9-c424d77bbe30
caps.latest.revision: "5"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 82e56af804ee91dd2231e8bf6baa141bd9f94115
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/21/2017
---
# <a name="sqlspecialcolumns-visual-foxpro-odbc-driver"></a>SQLSpecialColumns (le pilote ODBC Visual FoxPro)
> [!NOTE]  
>  Cette rubrique contient des informations spécifiques au pilote ODBC Visual FoxPro. Pour obtenir des informations générales sur cette fonction, consultez la rubrique appropriée sous [référence de l’API ODBC](../../odbc/reference/syntax/odbc-api-reference.md).  
  
 Prise en charge : complet  
  
 Conformité d’API ODBC : Niveau 1  
  
 Récupère le jeu optimal de colonnes qui identifie de façon unique une ligne dans la table.  
  
 Le pilote ODBC Visual FoxPro retourne les colonnes qui composent la clé primaire sur la table FoxPro. (Consultez [SQLPrimaryKeys](../../odbc/microsoft/sqlprimarykeys-visual-foxpro-odbc-driver.md).) Si elle est appelée avec *fColType* ne défini sur SQL_ROWVER, aucune colonne n’est retournée. **SQLSpecialColumns** fonctionne uniquement pour les sources de données qui sont [bases de données](../../odbc/microsoft/visual-foxpro-terminology.md).  
  
 Pour plus d’informations, consultez [SQLSpecialColumns](../../odbc/reference/syntax/sqlspecialcolumns-function.md) dans les *de référence du programmeur ODBC*.

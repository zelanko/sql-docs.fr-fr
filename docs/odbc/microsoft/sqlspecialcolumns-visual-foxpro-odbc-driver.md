---
title: SQLSpecialColumns (Visual FoxPro ODBC Driver) Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SQLSpecialColumns function [ODBC], Visual FoxPro ODBC Driver
ms.assetid: b72a978d-6a60-475a-b7d9-c424d77bbe30
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 96b439674c8bda3494b4cefd0c1118602b537cd0
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81299379"
---
# <a name="sqlspecialcolumns-visual-foxpro-odbc-driver"></a>SQLSpecialColumns (pilote ODBC Visual FoxPro)
> [!NOTE]  
>  Ce sujet contient des informations visuelles spécifiques à FoxPro ODBC Driver. Pour plus d’informations générales sur cette fonction, voir le sujet approprié sous [ODBC API Référence](../../odbc/reference/syntax/odbc-api-reference.md).  
  
 Soutien: Complet  
  
 Conformité API ODBC: Niveau 1  
  
 Récupère l’ensemble optimal de colonnes qui identifie uniquement une ligne dans la table.  
  
 Le visual FoxPro ODBC Driver retourne les colonnes qui composent la clé principale sur la table FoxPro. (Voir [SQLPrimaryKeys](../../odbc/microsoft/sqlprimarykeys-visual-foxpro-odbc-driver.md).) Si appelé avec *fColType* réglé pour SQL_ROWVER, aucune colonne n’est retournée. **SQLSpecialColumns** ne fonctionne que pour les sources de données qui sont [des bases de données.](../../odbc/microsoft/visual-foxpro-terminology.md)  
  
 Pour plus d’informations, voir [SQLSpecialColumns](../../odbc/reference/syntax/sqlspecialcolumns-function.md) dans la *référence du programmeur ODBC*.

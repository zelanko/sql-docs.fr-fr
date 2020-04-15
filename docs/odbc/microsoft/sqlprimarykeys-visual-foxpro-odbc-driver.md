---
title: SQLPrimaryKeys (Visual FoxPro ODBC Driver) Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SQLPrimaryKeys function [ODBC], Visual FoxPro ODBC Driver
ms.assetid: 8dbe2903-efdc-45e0-a079-9e357c5fd81b
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 83631d22bd07017c4eba8f6af171443ab8c76d9c
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81301544"
---
# <a name="sqlprimarykeys-visual-foxpro-odbc-driver"></a>SQLPrimaryKeys (pilote ODBC Visual FoxPro)
> [!NOTE]  
>  Ce sujet contient des informations visuelles spécifiques à FoxPro ODBC Driver. Pour plus d’informations générales sur cette fonction, voir le sujet approprié sous [ODBC API Référence](../../odbc/reference/syntax/odbc-api-reference.md).  
  
 Soutien: Complet  
  
 Conformité API ODBC: Niveau 2  
  
 Retourne les noms de colonne qui composent la clé principale pour une table. La mise en œuvre visual foxPro ODBC Driver de **SQLPrimaryKeys** se comporte comme suit :  
  
-   Ignore les arguments *szTableOwner* et *cbTableOwner.*  
  
-   Fonctionne uniquement pour les sources de données qui sont [des bases de données](../../odbc/microsoft/visual-foxpro-terminology.md). Le conducteur retourne l’erreur "Driver ne prend pas en charge cette fonction" si la source de données est un répertoire de [tables gratuites](../../odbc/microsoft/visual-foxpro-terminology.md).  
  
 Pour plus d’informations, voir [SQLPrimaryKeys](../../odbc/reference/syntax/sqlprimarykeys-function.md) dans la *référence du programmeur ODBC*.

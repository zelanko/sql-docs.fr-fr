---
title: SQLPrimaryKeys (pilote ODBC de Visual FoxPro) | Microsoft Docs
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
author: MightyPen
ms.author: genemi
ms.openlocfilehash: e85e60cde86c9483e69a8c43de14ef64eb914119
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "68030702"
---
# <a name="sqlprimarykeys-visual-foxpro-odbc-driver"></a>SQLPrimaryKeys (pilote ODBC Visual FoxPro)
> [!NOTE]  
>  Cette rubrique contient des informations spécifiques au pilote ODBC Visual FoxPro. Pour obtenir des informations générales sur cette fonction, consultez la rubrique appropriée sous [ODBC API Reference](../../odbc/reference/syntax/odbc-api-reference.md).  
  
 Prise en charge : Complète  
  
 Conformité d’API ODBC : Niveau 2  
  
 Retourne les noms de colonnes qui composent la clé primaire pour une table. L’implémentation pilote ODBC Visual FoxPro de **SQLPrimaryKeys** se comporte comme suit :  
  
-   Ignore le *szTableOwner* et *cbTableOwner* arguments.  
  
-   S’applique uniquement aux sources de données qui sont [bases de données](../../odbc/microsoft/visual-foxpro-terminology.md). Le pilote retourne l’erreur « Pilote ne prend pas en charge cette fonction » si la source de données est un répertoire de [gratuit tables](../../odbc/microsoft/visual-foxpro-terminology.md).  
  
 Pour plus d’informations, consultez [SQLPrimaryKeys](../../odbc/reference/syntax/sqlprimarykeys-function.md) dans le *de référence du programmeur ODBC*.

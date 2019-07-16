---
title: À l’aide de chaînes de connexion | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- connection strings [ODBC]
- connecting to data source [ODBC], Visual FoxPro
- Visual FoxPro data source [ODBC], connecting
ms.assetid: 57634960-47e9-49bf-95c1-6e3702ac8166
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 496fe10fbf49f4d712127e2e4122c50fa20ba2be
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "68044586"
---
# <a name="using-connection-strings"></a>Utilisation des chaînes de connexion
Vous pouvez utiliser une chaîne de connexion pour se connecter à une source de données Visual FoxPro.  
  
 Par exemple, pour vous connecter à la source de données TasTrade et que vous remplacez que le paramètre actuel du exclusifs associé à la source de données, vous utiliseriez la chaîne :  
  
```  
DSN=TasTrade;Exclusive=Yes  
```  
  
 Pour obtenir la liste des mots clés des attributs et des valeurs que vous pouvez inclure dans la chaîne de connexion, consultez [SQLDriverConnect](../../odbc/microsoft/sqldriverconnect-visual-foxpro-odbc-driver.md).  
  
 Pour obtenir une explication complète de la syntaxe de chaîne de connexion, consultez [SQLBrowseConnect](../../odbc/reference/syntax/sqlbrowseconnect-function.md) dans le *de référence du programmeur ODBC*.

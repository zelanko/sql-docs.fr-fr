---
title: Utilisation des chaînes de connexion | Microsoft Docs
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 9083414503606720a40d372ed883a140953dc415
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/27/2020
ms.locfileid: "81307590"
---
# <a name="using-connection-strings"></a>Utilisation des chaînes de connexion
Vous pouvez utiliser une chaîne de connexion pour vous connecter à une source de données Visual FoxPro.  
  
 Par exemple, pour vous connecter à la source de données TasTrade et remplacer la valeur actuelle de l’option exclusive associée à la source de données, vous devez utiliser la chaîne :  
  
```  
DSN=TasTrade;Exclusive=Yes  
```  
  
 Pour obtenir la liste des mots clés d’attribut et des valeurs que vous pouvez inclure dans la chaîne de connexion, consultez [SQLDriverConnect](../../odbc/microsoft/sqldriverconnect-visual-foxpro-odbc-driver.md).  
  
 Pour obtenir une explication complète de la syntaxe de la chaîne de connexion, consultez [SQLBrowseConnect](../../odbc/reference/syntax/sqlbrowseconnect-function.md) dans le *Guide de référence du programmeur ODBC*.

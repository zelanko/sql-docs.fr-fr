---
title: Utilisation des chaînes de connexion (fr) Microsoft Docs
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
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81307590"
---
# <a name="using-connection-strings"></a>Utilisation des chaînes de connexion
Vous pouvez utiliser une chaîne de connexion pour vous connecter à une source de données Visual FoxPro.  
  
 Par exemple, pour vous connecter à la source de données TasTrade et passer outre au paramètre actuel d’Exclusivité associé à la source de données, vous utiliseriez la chaîne :  
  
```  
DSN=TasTrade;Exclusive=Yes  
```  
  
 Pour une liste des mots clés et valeurs d’attribut que vous pouvez inclure dans la chaîne de connexion, voir [SQLDriverConnect](../../odbc/microsoft/sqldriverconnect-visual-foxpro-odbc-driver.md).  
  
 Pour une explication complète de la syntaxe de chaîne de connexion, voir [SQLBrowseConnect](../../odbc/reference/syntax/sqlbrowseconnect-function.md) dans la *référence du programmeur ODBC*.

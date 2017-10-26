---
title: SQLExecDirect (le pilote ODBC Visual FoxPro) | Documents Microsoft
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- SQLExecDirect function [ODBC], Visual FoxPro ODBC Driver
ms.assetid: 5004060f-8510-4018-87a4-d41789e69d3e
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 3edf8a3bd785d3440af3347d457dd5078e289638
ms.contentlocale: fr-fr
ms.lasthandoff: 09/09/2017

---
# <a name="sqlexecdirect-visual-foxpro-odbc-driver"></a>SQLExecDirect (le pilote ODBC Visual FoxPro)
> [!NOTE]  
>  Cette rubrique contient des informations spécifiques au pilote ODBC Visual FoxPro. Pour obtenir des informations générales sur cette fonction, consultez la rubrique appropriée sous [référence de l’API ODBC](../../odbc/reference/syntax/odbc-api-reference.md).  
  
 Prise en charge : complet  
  
 Conformité d’API ODBC : Niveau principal  
  
 Exécute un nouveau [pouvant être préparée instruction SQL](../../odbc/microsoft/visual-foxpro-terminology.md). Le pilote ODBC Visual FoxPro utilise les valeurs actuelles des variables de marqueur de paramètre, si tous les paramètres existent dans l’instruction.  
  
 Pour créer une commande batch pour envoyer plusieurs instructions SQL à la fois, utilisez un point-virgule ( ;) pour séparer chaque instruction SQL dans le lot.  
  
 Si votre table, vue ou les noms de champs contiennent des espaces, placez les noms à l’arrière devis marques. Par exemple, si votre base de données contient une table nommée My Table et le champ My Field, placez chaque élément de l’identificateur comme suit :  
  
```  
SELECT `My Table`.`Field1`, `My Table`.`Field2` FROM `My Table`  
```  
  
 Pour plus d’informations, consultez [SQLExecDirect](../../odbc/reference/syntax/sqlexecdirect-function.md) dans les *de référence du programmeur ODBC*.


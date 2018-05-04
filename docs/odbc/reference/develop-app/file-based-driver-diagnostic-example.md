---
title: Exemple de Diagnostic basé sur le fichier de pilote | Documents Microsoft
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: odbc
ms.reviewer: ''
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- file-based driver diagnostic [ODBC]
- diagnostic information [ODBC], examples
- error messages [ODBC], diagnostic messages
ms.assetid: 0575fccd-4641-478d-a3cc-5a764e35bae2
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 2b1b05e575530b09f2f17fa707d73d2ae86b9141
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
---
# <a name="file-based-driver-diagnostic-example"></a>Exemple de Diagnostic basé sur le fichier de pilote
Un pilote de fichier agit comme un pilote ODBC et comme une source de données. Il peut ainsi générer des erreurs et avertissements à la fois en tant que composant dans une connexion ODBC et comme une source de données. Comme il est également le composant qui s’interface avec le Gestionnaire de pilotes, il met en forme et retourne les arguments de **SQLGetDiagRec**.  
  
 Par exemple, si un pilote Microsoft® pour dBASE ne peut pas allouer suffisamment de mémoire, il peut retourner les valeurs suivantes à partir de **SQLGetDiagRec**:  
  
```  
SQLSTATE:         "HY001"  
Native Error:      42052  
Diagnostic Msg:   "[Microsoft][ODBC dBASE Driver]Unable to allocate sufficient memory."  
```  
  
 Parce que cette erreur n’est pas liée à la source de données, le pilote ajouté uniquement les préfixes pour le message de diagnostic pour le fournisseur ([Microsoft]) et le pilote ([ODBC pilote dBASE]).  
  
 Si le pilote n’a pas pu trouver le fichier Employee.dbf, elle peut retourner les valeurs suivantes à partir de **SQLGetDiagRec**:  
  
```  
SQLSTATE:         "42S02"  
Native Error:      -1305  
Diagnostic Msg:   "[Microsoft][ODBC dBASE Driver][dBASE]No such table or object"  
```  
  
 Étant donné que cette erreur a été liée à la source de données, le pilote ajouté le format de fichier de la source de données ([dBASE]) en tant que préfixe pour le message de diagnostic. Étant donné que le pilote a été également le composant à la source de données, il ajouté préfixes pour le fournisseur ([Microsoft]) et le pilote ([ODBC pilote dBASE]).

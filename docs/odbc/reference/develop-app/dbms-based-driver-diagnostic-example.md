---
title: Exemple de Diagnostic de pilote de SGBD | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- DBMS-based driver diagnostic [ODBC]
- diagnostic information [ODBC], examples
- error messages [ODBC], diagnostic messages
ms.assetid: a80d54b0-43ff-4dfd-b6cb-f4694a5ed765
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 0485ecf720cb84580c17c77b31fc6816de2e679a
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "62641038"
---
# <a name="dbms-based-driver-diagnostic-example"></a>Exemple de diagnostic d’un pilote de SGBD
Un pilote de SGBD envoie des demandes à un SGBD et retourne des informations à l’application via le Gestionnaire de pilotes. Étant donné que le pilote est le composant qui sert d’interface avec le Gestionnaire de pilotes, il met en forme et retourne les arguments pour **SQLGetDiagRec**.  
  
 Par exemple, si, à l’aide des Services/SQL, un pilote Microsoft pour Oracle Rdb a rencontré un nom de curseur non valide, elle peut retourner les valeurs suivantes à partir de **SQLGetDiagRec**:  
  
```  
SQLSTATE:         "34000"  
Native Error:      0  
Diagnostic Msg:   "[Microsoft][ODBC Rdb Driver]Invalid cursor name: EMPLOYEE_CURSOR."  
```  
  
 Étant donné que l’erreur s’est produite dans le pilote, il ajouté préfixes pour le message de diagnostic pour le fournisseur ([Microsoft]) et le (pilote [ODBC Rdb]).  
  
 Si le SGBD ne peut pas trouver la table EMPLOYEE, le pilote peut mettre en forme et retourner les valeurs suivantes à partir de **SQLGetDiagRec**:  
  
```  
SQLSTATE:         "42S02"  
Native Error:      -1  
Diagnostic Msg:   "[Microsoft][ODBC Rdb Driver][Rdb] %SQL-F-RELNOTDEF, Table EMPLOYEE "  
                  "is not defined in schema."  
```  
  
 Étant donné que l’erreur s’est produite dans la source de données, le pilote ajouté un préfixe de l’identificateur de source de données ([Rdb]) pour le message de diagnostic. Étant donné que le pilote a été le composant connectée à la source de données, il ajouté préfixes pour son fournisseur ([Microsoft]) et l’identificateur ([ODBC Rdb pilote]) pour le message de diagnostic.

---
title: Exemple de diagnostic de conducteur basé sur DBMS (fr) Microsoft Docs
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 117f43548d2b57233dea6f7423e6bad67b6233b0
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81304350"
---
# <a name="dbms-based-driver-diagnostic-example"></a>Exemple de diagnostic d’un pilote de SGBD
Un chauffeur basé sur DBMS envoie des demandes à un DBMS et renvoie des informations à l’application par l’intermédiaire du gestionnaire de conducteur. Parce que le conducteur est le composant qui s’interface avec le Driver Manager, il formate et renvoie les arguments pour **SQLGetDiagRec**.  
  
 Par exemple, si, à l’aide de SQL/Services, un pilote Microsoft pour Oracle Rdb a rencontré un nom de curseur invalide, il pourrait retourner les valeurs suivantes de **SQLGetDiagRec**:  
  
```  
SQLSTATE:         "34000"  
Native Error:      0  
Diagnostic Msg:   "[Microsoft][ODBC Rdb Driver]Invalid cursor name: EMPLOYEE_CURSOR."  
```  
  
 Parce que l’erreur s’est produite dans le conducteur, il a ajouté des préfixes au message diagnostique pour le fournisseur ([Microsoft]) et le conducteur ([ODBC Rdb Driver]).  
  
 Si le DBMS n’a pas pu trouver la table EMPLOYEE, le conducteur pourrait formater et retourner les valeurs suivantes de **SQLGetDiagRec**:  
  
```  
SQLSTATE:         "42S02"  
Native Error:      -1  
Diagnostic Msg:   "[Microsoft][ODBC Rdb Driver][Rdb] %SQL-F-RELNOTDEF, Table EMPLOYEE "  
                  "is not defined in schema."  
```  
  
 Étant donné que l’erreur s’est produite dans la source de données, le conducteur a ajouté un préfixe pour l’identifiant source de données ([Rdb]) au message diagnostique. Étant donné que le pilote était le composant qui s’est associé à la source de données, il a ajouté des préfixes pour son fournisseur ([Microsoft]) et son identifiant ([ODBC Rdb Driver]) au message diagnostique.

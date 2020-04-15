---
title: Exemple de diagnostic de pilote basé sur les fichiers (en anglais seulement) Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- file-based driver diagnostic [ODBC]
- diagnostic information [ODBC], examples
- error messages [ODBC], diagnostic messages
ms.assetid: 0575fccd-4641-478d-a3cc-5a764e35bae2
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 6f09e4f4758b6276836b08f02b24fb31dd1fadc7
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81305637"
---
# <a name="file-based-driver-diagnostic-example"></a>Exemple de diagnostic d’un pilote basé sur des fichiers
Un conducteur basé sur des fichiers agit à la fois comme conducteur oDBC et comme source de données. Il peut donc générer des erreurs et des avertissements à la fois en tant que composant dans une connexion ODBC et comme source de données. Parce que c’est aussi le composant qui s’interface avec le Driver Manager, il formate et renvoie les arguments pour **SQLGetDiagRec**.  
  
 Par exemple, si un pilote Microsoft® pour dBASE ne pouvait pas allouer suffisamment de mémoire, il pourrait retourner les valeurs suivantes de **SQLGetDiagRec**:  
  
```  
SQLSTATE:         "HY001"  
Native Error:      42052  
Diagnostic Msg:   "[Microsoft][ODBC dBASE Driver]Unable to allocate sufficient memory."  
```  
  
 Étant donné que cette erreur n’était pas liée à la source de données, le conducteur n’a ajouté que des préfixes au message diagnostique pour le fournisseur ([Microsoft]) et le pilote ([ODBC dBASE Driver]).  
  
 Si le conducteur n’a pas pu trouver le fichier Employee.dbf, il pourrait retourner les valeurs suivantes de **SQLGetDiagRec**:  
  
```  
SQLSTATE:         "42S02"  
Native Error:      -1305  
Diagnostic Msg:   "[Microsoft][ODBC dBASE Driver][dBASE]No such table or object"  
```  
  
 Étant donné que cette erreur était liée à la source de données, le conducteur a ajouté le format de fichier de la source de données ([dBASE]) comme préfixe au message diagnostique. Étant donné que le pilote était aussi le composant qui s’est associé à la source de données, il a ajouté des préfixes pour le fournisseur ([Microsoft]) et le pilote ([ODBC dBASE Driver]).

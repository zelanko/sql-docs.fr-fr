---
title: Exemple de diagnostic de pilote basé sur des fichiers | Microsoft Docs
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
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 23234a490f664c4be0811152b2b77ae7c0b73761
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "68069831"
---
# <a name="file-based-driver-diagnostic-example"></a>Exemple de diagnostic d’un pilote basé sur des fichiers
Un pilote basé sur des fichiers agit à la fois comme un pilote ODBC et comme source de données. Il peut donc générer des erreurs et des avertissements en tant que composant dans une connexion ODBC et en tant que source de données. Comme il s’agit également du composant qui interagit avec le gestionnaire de pilotes, il met en forme et retourne les arguments pour **SQLGetDiagRec**.  
  
 Par exemple, si un pilote Microsoft® pour dBASE n’a pas pu allouer suffisamment de mémoire, il peut renvoyer les valeurs suivantes à partir de **SQLGetDiagRec**:  
  
```  
SQLSTATE:         "HY001"  
Native Error:      42052  
Diagnostic Msg:   "[Microsoft][ODBC dBASE Driver]Unable to allocate sufficient memory."  
```  
  
 Étant donné que cette erreur n’est pas liée à la source de données, le pilote n’a ajouté que des préfixes au message de diagnostic pour le fournisseur ([Microsoft]) et le pilote ([pilote ODBC dBASE]).  
  
 Si le pilote n’a pas pu trouver le fichier Employee. DBF, il peut retourner les valeurs suivantes à partir de **SQLGetDiagRec**:  
  
```  
SQLSTATE:         "42S02"  
Native Error:      -1305  
Diagnostic Msg:   "[Microsoft][ODBC dBASE Driver][dBASE]No such table or object"  
```  
  
 Étant donné que cette erreur est liée à la source de données, le pilote a ajouté le format de fichier de la source de données ([dBASE]) en tant que préfixe au message de diagnostic. Étant donné que le pilote était également le composant qui a été associé à la source de données, il a ajouté des préfixes pour le fournisseur ([Microsoft]) et le pilote ([pilote ODBC dBASE]).

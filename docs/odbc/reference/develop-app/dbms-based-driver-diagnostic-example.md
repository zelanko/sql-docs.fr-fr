---
description: Exemple de diagnostic d’un pilote de SGBD
title: Exemple de diagnostic de pilote basé sur SGBD | Microsoft Docs
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
ms.openlocfilehash: 5425afb18a5582a840966798ea7a7209dba7e1e6
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/17/2020
ms.locfileid: "88424741"
---
# <a name="dbms-based-driver-diagnostic-example"></a>Exemple de diagnostic d’un pilote de SGBD
Un pilote basé sur un SGBD envoie des demandes à un SGBD et renvoie des informations à l’application via le gestionnaire de pilotes. Étant donné que le pilote est le composant qui s’interface avec le gestionnaire de pilotes, il met en forme et retourne les arguments pour **SQLGetDiagRec**.  
  
 Par exemple, si, à l’aide de SQL/services, un pilote Microsoft pour la RDB Oracle a rencontré un nom de curseur non valide, il peut retourner les valeurs suivantes à partir de **SQLGetDiagRec**:  
  
```  
SQLSTATE:         "34000"  
Native Error:      0  
Diagnostic Msg:   "[Microsoft][ODBC Rdb Driver]Invalid cursor name: EMPLOYEE_CURSOR."  
```  
  
 Étant donné que l’erreur s’est produite dans le pilote, elle a ajouté des préfixes au message de diagnostic pour le fournisseur ([Microsoft]) et le pilote ([pilote ODBC RDB]).  
  
 Si le SGBD n’a pas trouvé la table EMPLOYee, le pilote peut formater et retourner les valeurs suivantes à partir de **SQLGetDiagRec**:  
  
```  
SQLSTATE:         "42S02"  
Native Error:      -1  
Diagnostic Msg:   "[Microsoft][ODBC Rdb Driver][Rdb] %SQL-F-RELNOTDEF, Table EMPLOYEE "  
                  "is not defined in schema."  
```  
  
 Étant donné que l’erreur s’est produite dans la source de données, le pilote a ajouté un préfixe pour l’identificateur de source de données ([RDB]) au message de diagnostic. Étant donné que le pilote était le composant qui a été associé à la source de données, il a ajouté des préfixes pour son fournisseur ([Microsoft]) et son identificateur ([pilote ODBC RDB]) au message de diagnostic.

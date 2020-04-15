---
title: Paramètres de l’énoncé (en anglais) Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- statement parameters [ODBC]
ms.assetid: 58d5b166-2578-4699-a560-1f1e6d86c49a
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 02327ff4bb6a1ac3ac57fbf7d3c6b09b70c11534
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81306820"
---
# <a name="statement-parameters"></a>Paramètres des instructions
Un *paramètre* est une variable dans un communiqué SQL. Supposons, par exemple, qu’une table De pièces porte des colonnes nommées PartID, Description et Prix. Pour ajouter une pièce sans paramètres, il faudrait construire une déclaration SQL comme :  
  
```  
INSERT INTO Parts (PartID, Description, Price) VALUES (2100, 'Drive shaft', 50.00)  
```  
  
 Bien que cette déclaration insère une nouvelle commande, il n’est pas une bonne solution pour une application d’entrée de commande parce que les valeurs à insérer ne peuvent pas être codées dans l’application. Une alternative consiste à construire la déclaration SQL au moment de l’exécution, en utilisant les valeurs à insérer. Ce n’est pas non plus une bonne solution, en raison de la complexité de la construction d’énoncés au moment de l’exécution. La meilleure solution est de remplacer les éléments de la clause **VALUES** par des points d’interrogation (?), ou *des marqueurs de paramètres*:  
  
```  
INSERT INTO Parts (PartID, Description, Price) VALUES (?, ?, ?)  
```  
  
 Les marqueurs de paramètres sont ensuite liés à des variables d'applications. Pour ajouter une nouvelle ligne, l’application n’a qu’à définir les valeurs des variables et exécuter l’instruction. Le pilote extrait ensuite les valeurs actuelles des variables et les envoie à la source de données. Si l’instruction est exécutée plusieurs fois, l’application peut rendre le processus encore plus efficace en préparant l’instruction.  
  
 La déclaration qui vient d’être affichée peut être codée en dur dans une application d’entrée de commande pour insérer une nouvelle ligne. Cependant, les marqueurs de paramètres ne se limitent pas aux applications verticales. Pour toute application, ils soulagent la difficulté de construire des relevés SQL au moment de l’exécution en évitant les conversions vers et depuis le texte. Par exemple, la pièce d’identité qui vient d’être montrée est très probablement stockée dans l’application sous forme d’intégrage. Si l’énoncé SQL est construit sans marqueurs de paramètres, l’application doit convertir l’ID de pièce en texte et la source de données doit la convertir en un intégrant. En utilisant un marqueur de paramètres, l’application peut envoyer la pièce d’identité au conducteur comme un intégreur, qui peut généralement l’envoyer à la source de données comme un intégreur. Cela permet d’économiser deux conversions. Pour les valeurs de données longues, c’est très important, car les formes de texte de ces valeurs dépassent souvent la longueur autorisée d’une déclaration SQL.  
  
 Les paramètres ne sont valables qu’à certains endroits dans les relevés SQL. Par exemple, ils ne sont pas autorisés dans la liste de sélection (la liste des colonnes à retourner par une instruction **SELECT),** et ils ne sont pas autorisés en tant qu’opérandes d’un opérateur binaire comme le signe égal (MD), car il serait impossible de déterminer le type de paramètre. En général, les paramètres ne sont valables que dans les relevés de type de manipulation de données (DML), et non dans les énoncés de définition des données (DDL). Pour plus d’informations, voir [Marqueurs paramètres](../../../odbc/reference/appendixes/parameter-markers.md) à l’annexe C: SQL Grammar.  
  
 Lorsque la déclaration SQL invoque une procédure, les paramètres désignés peuvent être utilisés. Les paramètres désignés sont identifiés par leurs noms, et non par leur position dans la déclaration de la SQL. Ils peuvent être liés par un appel à **SQLBindParameter**, mais le paramètre est identifié par le champ SQL_DESC_NAME de l’IPD (descripteur paramètre de mise en œuvre), et non par *l’argument de ParameterNumber* de **SQLBindParameter**. Ils peuvent également être liés en appelant **SQLSetDescField** ou **SQLSetDescRec**. Pour plus d’informations sur les paramètres nommés, voir [Paramètres de liaison par nom (Paramètres nommés)](../../../odbc/reference/develop-app/binding-parameters-by-name-named-parameters.md), plus tard dans cette section. Pour plus d’informations sur les descripteurs, voir [Descriptors](../../../odbc/reference/develop-app/descriptors.md).  
  
 Cette section contient les rubriques suivantes :  
  
-   [Liaison de paramètres](../../../odbc/reference/develop-app/binding-parameters-odbc.md)  
  
-   [Définition de valeurs de paramètres](../../../odbc/reference/develop-app/setting-parameter-values.md)  
  
-   [Envoi de données de type Long](../../../odbc/reference/develop-app/sending-long-data.md)  
  
-   [Récupération des paramètres de sortie par SQLGetData](../../../odbc/reference/develop-app/retrieving-output-parameters-using-sqlgetdata.md)  
  
-   [Paramètres de procédure](../../../odbc/reference/develop-app/procedure-parameters.md)  
  
-   [Tableaux de valeurs de paramètre](../../../odbc/reference/develop-app/arrays-of-parameter-values.md)

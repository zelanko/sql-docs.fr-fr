---
description: Paramètres des instructions
title: Paramètres d’instruction | Microsoft Docs
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
ms.openlocfilehash: 7400367d4b237d2d0e22c6363d1559eb89506d7d
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/17/2020
ms.locfileid: "88482892"
---
# <a name="statement-parameters"></a>Paramètres des instructions
Un *paramètre* est une variable dans une instruction SQL. Par exemple, supposons qu’une table de composants possède des colonnes nommées PartId, description et Price. Pour ajouter un composant sans paramètres, vous devez construire une instruction SQL telle que :  
  
```  
INSERT INTO Parts (PartID, Description, Price) VALUES (2100, 'Drive shaft', 50.00)  
```  
  
 Bien que cette instruction insère une nouvelle commande, il ne s’agit pas d’une bonne solution pour une application de saisie de commandes, car les valeurs à insérer ne peuvent pas être codées en dur dans l’application. Une alternative consiste à construire l’instruction SQL au moment de l’exécution, en utilisant les valeurs à insérer. Il ne s’agit pas non plus d’une bonne solution, en raison de la complexité de la construction d’instructions au moment de l’exécution. La meilleure solution consiste à remplacer les éléments de la clause **values** par des points d’interrogation ( ?) ou des *marqueurs de paramètres*:  
  
```  
INSERT INTO Parts (PartID, Description, Price) VALUES (?, ?, ?)  
```  
  
 Les marqueurs de paramètres sont ensuite liés à des variables d'applications. Pour ajouter une nouvelle ligne, l’application a uniquement défini les valeurs des variables et exécute l’instruction. Le pilote extrait ensuite les valeurs actuelles des variables et les envoie à la source de données. Si l’instruction est exécutée plusieurs fois, l’application peut rendre le processus encore plus efficace en préparant l’instruction.  
  
 L’instruction indiquée peut être codée en dur dans une application d’entrée de commande pour insérer une nouvelle ligne. Toutefois, les marqueurs de paramètres ne sont pas limités aux applications verticales. Pour toute application, ils facilitent la construction d’instructions SQL au moment de l’exécution en évitant les conversions vers et à partir du texte. Par exemple, l’ID de la partie que vous venez de voir est probablement stocké dans l’application sous la forme d’un entier. Si l’instruction SQL est construite sans marqueurs de paramètres, l’application doit convertir l’ID de composant en texte et la source de données doit la reconvertir en entier. À l’aide d’un marqueur de paramètre, l’application peut envoyer l’ID du composant au pilote en tant qu’entier, ce qui peut généralement l’envoyer à la source de données sous la forme d’un entier. Cela permet d’économiser deux conversions. Pour les valeurs de données longues, c’est très important, car les formes textuelles de ces valeurs dépassent fréquemment la longueur autorisée d’une instruction SQL.  
  
 Les paramètres sont valides uniquement à certains endroits dans les instructions SQL. Par exemple, elles ne sont pas autorisées dans la liste de sélection (la liste des colonnes à retourner par une instruction **Select** ), et ne sont pas autorisées comme les deux opérandes d’un opérateur binaire tel que le signe égal (=), car il est impossible de déterminer le type de paramètre. En règle générale, les paramètres sont valides uniquement dans les instructions DML (Data Manipulation Language), et non dans les instructions DDL (Data Definition Language). Pour plus d’informations, consultez [marqueurs de paramètres](../../../odbc/reference/appendixes/parameter-markers.md) dans l’annexe C : grammaire SQL.  
  
 Lorsque l’instruction SQL appelle une procédure, des paramètres nommés peuvent être utilisés. Les paramètres nommés sont identifiés par leurs noms, et non par leur position dans l’instruction SQL. Ils peuvent être liés par un appel à **SQLBindParameter**, mais le paramètre est identifié par le champ SQL_DESC_NAME de la IPD (descripteur de paramètre d’implémentation) et non par l’argument *ParameterNumber* de **SQLBindParameter**. Elles peuvent également être liées en appelant **SQLSetDescField** ou **SQLSetDescRec**. Pour plus d’informations sur les paramètres nommés, consultez [liaison de paramètres par nom (paramètres nommés)](../../../odbc/reference/develop-app/binding-parameters-by-name-named-parameters.md), plus loin dans cette section. Pour plus d’informations sur les descripteurs, consultez [descripteurs](../../../odbc/reference/develop-app/descriptors.md).  
  
 Cette section contient les rubriques suivantes :  
  
-   [Liaison de paramètres](../../../odbc/reference/develop-app/binding-parameters-odbc.md)  
  
-   [Définition de valeurs de paramètres](../../../odbc/reference/develop-app/setting-parameter-values.md)  
  
-   [Envoi de données de type Long](../../../odbc/reference/develop-app/sending-long-data.md)  
  
-   [Récupération des paramètres de sortie par SQLGetData](../../../odbc/reference/develop-app/retrieving-output-parameters-using-sqlgetdata.md)  
  
-   [Paramètres de procédure](../../../odbc/reference/develop-app/procedure-parameters.md)  
  
-   [Tableaux de valeurs de paramètre](../../../odbc/reference/develop-app/arrays-of-parameter-values.md)

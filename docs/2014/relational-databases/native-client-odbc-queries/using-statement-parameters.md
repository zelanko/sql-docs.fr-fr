---
title: À l’aide des paramètres d’instruction | Documents Microsoft
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- SQL Server Native Client ODBC driver, parameters
- parameters [SQL Server Native Client], ODBC
- ODBC, parameters
- statements [ODBC], parameters
- parameter markers [ODBC]
- SQL Server Native Client ODBC driver, statements
- ODBC applications, statements
ms.assetid: 2427d886-ec6c-49d7-b0b6-0d998b64cdb9
caps.latest.revision: 32
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 8c359db9f39f659ac497adcf3bc6e343e1dd6796
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36155035"
---
# <a name="using-statement-parameters"></a>Utilisation de paramètres d'instruction
  Un paramètre est une variable dans une instruction SQL qui peut permettre à une application ODBC d'effectuer les actions suivantes :  
  
-   fournir de manière efficace des valeurs pour les colonnes d'une table ;  
  
-   améliorer l'interaction de l'utilisateur lors de la construction de critères de requête ;  
  
-   Gérer les **texte**, **ntext**, et **image** données et [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-types de données C spécifiques.  
  
 Par exemple, un **parties** table possède des colonnes nommées **PartID**, **Description**, et **prix**. L'ajout d'un article sans paramètres requiert la construction d'une instruction SQL telle que :  
  
```  
INSERT INTO Parts (PartID, Description, Price) VALUES (2100, 'Drive shaft', 50.00)  
```  
  
 Bien que cette instruction soit acceptable pour insérer une ligne avec un jeu connu de valeurs, elle est maladroite lorsqu'une application doit insérer plusieurs lignes. Pour résoudre ce problème, ODBC laisse une application remplacer toute valeur de données dans une instruction SQL par un fabricant de paramètre. Cela est dénoté par un point d'interrogation (?). Dans l'exemple suivant, trois valeurs de données sont remplacées par des marqueurs de paramètres :  
  
```  
INSERT INTO Parts (PartID, Description, Price) VALUES (?, ?, ?)  
```  
  
 Les marqueurs de paramètres sont ensuite liés à des variables d'applications. Pour insérer une nouvelle ligne, l'application doit uniquement définir les valeurs des variables et exécuter l'instruction. Le pilote extrait ensuite les valeurs actuelles des variables et les envoie à la source de données. Si l'instruction est exécutée plusieurs fois, l'application peut rendre le processus encore plus efficace en préparant l'instruction.  
  
 Chaque marqueur de paramètre est référencé par son nombre ordinal assigné aux paramètres de gauche à droite. Le marqueur de paramètre situé le plus à gauche dans une instruction SQL a la valeur ordinale 1 ; le suivant a la valeur ordinale 2, et ainsi de suite.  
  
## <a name="in-this-section"></a>Dans cette section  
  
-   [Paramètres de liaison](using-statement-parameters-binding-parameters.md)  
  
## <a name="see-also"></a>Voir aussi  
 [L’exécution de requêtes &#40;ODBC&#41;](executing-queries-odbc.md)  
  
  
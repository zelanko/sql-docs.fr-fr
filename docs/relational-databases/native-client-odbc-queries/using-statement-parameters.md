---
title: Utilisation des paramètres de l’énoncé ( Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
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
author: markingmyname
ms.author: maghan
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 74cd70bcd9107d68551dc3f82eb1e01f76a549b4
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81297895"
---
# <a name="using-statement-parameters"></a>Utilisation de paramètres d'instruction
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  Un paramètre est une variable dans une instruction SQL qui peut permettre à une application ODBC d'effectuer les actions suivantes :  
  
-   fournir de manière efficace des valeurs pour les colonnes d'une table ;  
  
-   améliorer l'interaction de l'utilisateur lors de la construction de critères de requête ;  
  
-   Gérer le **texte,** **le ntext**, et les données **d’image** et [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]les types spécifiques de données C.  
  
 Par exemple, un tableau **De pièces** a des colonnes nommées **PartID**, **Description**, et **Prix**. L'ajout d'un article sans paramètres requiert la construction d'une instruction SQL telle que :  
  
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
  
-   [Liaison de paramètres](../../relational-databases/native-client-odbc-queries/using-statement-parameters-binding-parameters.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Exécution des requêtes &#40;&#41;ODBC](../../relational-databases/native-client-odbc-queries/executing-queries-odbc.md)  
  
  

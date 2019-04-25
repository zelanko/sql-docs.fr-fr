---
title: Handles de descripteur | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- application parameter descriptor [ODBC]
- automatically allocated descriptors [ODBC]
- implementation row descriptor [ODBC]
- descriptor handles [ODBC]
- handles [ODBC], descriptor
- implementation parameter descriptor [ODBC]
- apd [ODBC]
- ard [ODBC]
- explicitly allocated descriptors [ODBC]
- ipd [ODBC]
- ird [ODBC]
- application row descriptor [ODBC]
ms.assetid: 7741035c-f3e7-4c89-901e-fe528392f67d
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 3aa085cc0a098f557ca7a8cbddcd787a178b79d0
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62760767"
---
# <a name="descriptor-handles"></a>Handles de descripteur
Un *descripteur* est une collection de métadonnées qui décrivent les paramètres d’une instruction SQL ou les colonnes d’un jeu de résultats, comme indiqué par l’application ou le pilote (également connu sous le *implémentation*). Par conséquent, un descripteur peut remplir un des quatre rôles :  
  
-   **Descripteur de paramètre d’application (APD).** Contient des informations sur les tampons d’application liées aux paramètres dans une instruction SQL, telles que leurs adresses, les longueurs et les types de données C.  
  
-   **Descripteur de paramètre d’implémentation (IPD).** Contient des informations sur les paramètres dans une instruction SQL, telles que leurs types de données SQL, les longueurs et possibilité de valeur null.  
  
-   **Descripteur de ligne d’application (ARD).** Contient des informations sur les mémoires tampon d’application liées aux colonnes dans un jeu de résultats, telles que leurs adresses, les longueurs et les types de données C.  
  
-   **Descripteur de ligne d’implémentation (IRD).** Contient des informations sur les colonnes dans un jeu de résultats, telles que leurs types de données SQL, les longueurs et possibilité de valeur null.  
  
 Les descripteurs de quatre (une en remplissant chaque rôle) sont alloués automatiquement lorsqu’une instruction est allouée. Ils sont appelés *alloué automatiquement descripteurs* et sont toujours associées à cette instruction. Les applications peuvent également allouer des descripteurs avec **SQLAllocHandle**. Ils sont appelés *explicitement alloué descripteurs*. Ils sont alloués sur une connexion et peuvent être associés à une ou plusieurs instructions sur cette connexion pour remplir le rôle d’un APD ou d’ARD sur ces instructions.  
  
 La plupart des opérations dans ODBC peuvent être effectuées sans utilisation explicite de descripteurs par l’application. Toutefois, les descripteurs fournissent un raccourci commode pour certaines opérations. Par exemple, qu'une application souhaite insérer des données à partir de deux ensembles différents de mémoires tampons. Pour utiliser le premier jeu de mémoires tampons, il appelle à plusieurs reprises **SQLBindParameter** pour les lier aux paramètres dans un **insérer** instruction, puis exécutez l’instruction. Pour utiliser le deuxième jeu de mémoires tampons, il serait Répétez ce processus. Il peut également définir des liaisons pour le premier jeu de mémoires tampons dans un descripteur et le deuxième jeu de mémoires tampons dans un autre descripteur. Pour basculer entre les ensembles de liaisons, l’application appelle simplement **SQLSetStmtAttr** et associer le descripteur correct à l’instruction en tant que le descripteur APD.  
  
 Pour plus d’informations sur les descripteurs, consultez [Types de descripteurs](../../../odbc/reference/develop-app/types-of-descriptors.md).

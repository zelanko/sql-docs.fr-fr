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
ms.openlocfilehash: 24e3d4c87f3bc461a339a6cb635d64f20dc73e20
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "68106165"
---
# <a name="descriptor-handles"></a>Handles de descripteur
Un *descripteur* est une collection de métadonnées qui décrit les paramètres d’une instruction SQL ou les colonnes d’un jeu de résultats, comme le montre l’application ou le pilote (également appelée *implémentation*). Par conséquent, un descripteur peut remplir l’un des quatre rôles suivants :  
  
-   **Descripteur de paramètre d’application (APD).** Contient des informations sur les mémoires tampons d’application liées aux paramètres dans une instruction SQL, telles que leurs adresses, leurs longueurs et leurs types de données C.  
  
-   **Descripteur de paramètre d’implémentation (IPD).** Contient des informations sur les paramètres dans une instruction SQL, telles que les types de données SQL, les longueurs et les valeurs NULL.  
  
-   **Descripteur de ligne d’application (ARD).** Contient des informations sur les mémoires tampons d’application liées aux colonnes dans un jeu de résultats, telles que leurs adresses, leurs longueurs et leurs types de données C.  
  
-   **Descripteur de ligne d’implémentation (IRD).** Contient des informations sur les colonnes d’un jeu de résultats, telles que leurs types de données SQL, leurs longueurs et leurs valeurs NULL.  
  
 Quatre descripteurs (un remplissant chaque rôle) sont alloués automatiquement lors de l’allocation d’une instruction. Celles-ci sont appelées *descripteurs alloués automatiquement* et sont toujours associées à cette instruction. Les applications peuvent également allouer des descripteurs avec **SQLAllocHandle**. Ils sont appelés *descripteurs explicitement alloués*. Elles sont allouées sur une connexion et peuvent être associées à une ou plusieurs instructions sur cette connexion pour assumer le rôle d’un APD ou d’un ARD sur ces instructions.  
  
 La plupart des opérations dans ODBC peuvent être effectuées sans utilisation explicite des descripteurs par l’application. Toutefois, les descripteurs fournissent un raccourci pratique pour certaines opérations. Par exemple, supposons qu’une application souhaite insérer des données à partir de deux ensembles différents de mémoires tampons. Pour utiliser le premier ensemble de mémoires tampons, il doit appeler **SQLBindParameter** à plusieurs reprises pour les lier aux paramètres dans une instruction **Insert** , puis exécuter l’instruction. Pour utiliser le deuxième ensemble de mémoires tampons, il répète ce processus. Elle peut également définir des liaisons au premier jeu de mémoires tampons dans un descripteur et au deuxième ensemble de mémoires tampons dans un autre descripteur. Pour basculer entre les jeux de liaisons, l’application appelle simplement **SQLSetStmtAttr** et associe le descripteur correct à l’instruction en tant que APD.  
  
 Pour plus d’informations sur les descripteurs, consultez [types de descripteurs](../../../odbc/reference/develop-app/types-of-descriptors.md).

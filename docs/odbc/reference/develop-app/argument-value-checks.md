---
title: Vérifications de la valeur argument | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- diagnostic information [ODBC], driver manager error checking
- argument value checks [ODBC]
- driver manager [ODBC], error checking
ms.assetid: 37a65f8b-83aa-456c-b7cf-500404abb38a
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 013c8f80a672ed691e7519b318206c406171cfbc
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "68077114"
---
# <a name="argument-value-checks"></a>Vérifications de la valeur des arguments
Le Gestionnaire de pilotes vérifie les types suivants d’arguments. Sauf indication contraire, le Gestionnaire de pilotes retourne SQL_ERROR des erreurs dans les valeurs d’argument.  
  
-   Handles d’environnement, de connexion et d’instruction ne peut généralement être des pointeurs null. Le Gestionnaire de pilotes retourne SQL_INVALID_HANDLE lorsqu’il détecte un handle null.  
  
-   Requis comme des arguments de pointeur, *OutputHandlePtr* dans **SQLAllocHandle** et *CursorName* dans **SQLSetCursorName**, ne peut pas être pointeurs NULL.  
  
-   Indicateurs d’option qui ne prennent pas en charge les valeurs spécifiques au pilote doivent être une valeur autorisée. Par exemple, *opération* dans **SQLSetPos** doit être SQL_POSITION, SQL_REFRESH, SQL_UPDATE, SQL_DELETE ou SQL_ADD.  
  
-   Indicateurs d’option doivent être pris en charge dans la version d’ODBC pris en charge par le pilote. Par exemple, *InfoType* dans **SQLGetInfo** ne peut pas être SQL_ASYNC_MODE (introduite dans ODBC 3.0) lors de l’appel d’un pilote ODBC 2.0.  
  
-   Numéros de colonne et de paramètre doivent être supérieur à 0 ou supérieur ou égal à 0, selon la fonction. Le pilote doit vérifier la limite supérieure de ces valeurs d’argument selon le jeu de résultats actuel ou l’instruction SQL.  
  
-   Arguments de longueur / d’indicateur et des arguments de longueur de mémoire tampon de données doivent contenir des valeurs appropriées. Par exemple, l’argument qui spécifie la longueur d’un nom de table dans **SQLColumns** (*NameLength3*) doit être SQL_NTS ou une valeur supérieure à 0 ; *BufferLength* dans **SQLDescribeCol** doit être supérieur ou égal à 0. Le pilote peut également devez vérifier ces arguments. Par exemple, il peut vérifier que *NameLength3* est inférieure ou égale à la longueur maximale d’un nom de table dans la source de données.

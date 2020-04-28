---
title: Vérifications de la valeur d’argument | Microsoft Docs
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 6c6e4de16c4a1a80be893acbc7a1993b375f2fee
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/27/2020
ms.locfileid: "81298820"
---
# <a name="argument-value-checks"></a>Vérifications de la valeur des arguments
Le gestionnaire de pilotes vérifie les types d’arguments suivants. Sauf indication contraire, le gestionnaire de pilotes retourne SQL_ERROR pour les erreurs dans les valeurs d’argument.  
  
-   Les handles d’environnement, de connexion et d’instruction ne peuvent généralement pas être des pointeurs null. Le gestionnaire de pilotes retourne SQL_INVALID_HANDLE lorsqu’il trouve un handle null.  
  
-   Les arguments de pointeur requis, tels que *OutputHandlePtr* dans **SQLAllocHandle** et *CursorName* dans **SQLSetCursorName**, ne peuvent pas être des pointeurs null.  
  
-   Les indicateurs d’option qui ne prennent pas en charge les valeurs spécifiques au pilote doivent être une valeur légale. Par exemple, l' *opération* dans **SQLSetPos** doit être SQL_POSITION, SQL_REFRESH, SQL_UPDATE, SQL_DELETE ou SQL_ADD.  
  
-   Les indicateurs d’option doivent être pris en charge dans la version de ODBC prise en charge par le pilote. Par exemple, l' *infotype* dans **SQLGetInfo** ne peut pas être SQL_ASYNC_MODE (introduit dans ODBC 3,0) lors de l’appel d’un pilote ODBC 2,0.  
  
-   Les numéros de colonnes et de paramètres doivent être supérieurs à 0 ou supérieurs ou égaux à 0, en fonction de la fonction. Le pilote doit vérifier la limite supérieure de ces valeurs d’argument en fonction du jeu de résultats ou de l’instruction SQL en cours.  
  
-   Les arguments longueur/indicateur et longueur de la mémoire tampon des données doivent contenir des valeurs appropriées. Par exemple, l’argument qui spécifie la longueur d’un nom de table dans **SQLColumns** (*NameLength3*) doit être SQL_NTS ou une valeur supérieure à 0 ; *BufferLength* dans **SQLDescribeCol** doit être supérieur ou égal à 0. Le pilote peut également avoir besoin de vérifier ces arguments. Par exemple, il peut vérifier que *NameLength3* est inférieur ou égal à la longueur maximale d’un nom de table dans la source de données.

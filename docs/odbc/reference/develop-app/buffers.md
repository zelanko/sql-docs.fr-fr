---
title: Mémoires tampons | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- input buffers [ODBC]
- length/indicator buffers [ODBC]
- output buffers [ODBC]
- buffers [ODBC], about buffers
- application buffers [ODBC]
- buffers [ODBC]
ms.assetid: 42c5226c-cb40-4d1e-809f-2ea50ce6bd55
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 0c49e83e12463665f86f8cc15dc595e6ba2c506f
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/27/2020
ms.locfileid: "81306284"
---
# <a name="buffers"></a>Mémoires tampons
Une mémoire tampon est une partie de la mémoire d’application utilisée pour passer des données entre l’application et le pilote. Par exemple, les mémoires tampons d’application peuvent être associées à des colonnes de jeu de résultats, ou *liées à* celles-ci, avec **SQLBindCol**. À mesure que chaque ligne est extraite, les données sont retournées pour chaque colonne dans ces mémoires tampons. Les *mémoires tampons d’entrée* sont utilisées pour transmettre les données de l’application au pilote ; les *mémoires tampons de sortie* sont utilisées pour retourner les données du pilote à l’application.  
  
> [!NOTE]  
>  Si une fonction ODBC retourne SQL_ERROR, le contenu de tous les arguments de sortie de cette fonction n’est pas défini.  
  
 Cette discussion s’intéresse principalement aux mémoires tampons de type indéterminé. Les adresses de ces mémoires tampons apparaissent en tant qu’arguments de type SQLPOINTER, tels que l’argument *TargetValuePtr* dans **SQLBindCol**. Toutefois, certains des éléments abordés ici, tels que les arguments utilisés avec les tampons, s’appliquent également aux arguments utilisés pour passer des chaînes au pilote, tel que l’argument *TableName* dans **SQLTables**.  
  
 Ces mémoires tampons sont généralement des paires. Les *tampons de données* sont utilisés pour passer les données elles-mêmes, tandis que les *tampons de longueur/d’indicateur* sont utilisés pour transmettre la longueur des données dans la mémoire tampon de données ou une valeur spéciale telle que SQL_NULL_DATA, ce qui indique que les données sont null. La longueur des données dans une mémoire tampon de données est différente de la longueur de la mémoire tampon de données elle-même. L’illustration suivante montre la relation entre la mémoire tampon de données et la mémoire tampon de longueur/d’indicateur.  
  
 ![Mémoire tampon des données et longueur&#47;tampon de l’indicateur](../../../odbc/reference/develop-app/media/pr09.gif "pr09")  
  
 Une mémoire tampon de longueur/indicateur est requise chaque fois que le tampon de données contient des données de longueur variable, telles que des données de type caractère ou binaire. Si la mémoire tampon de données contient des données de longueur fixe, telles qu’un entier ou une structure de date, une mémoire tampon de longueur/indicateur est nécessaire uniquement pour passer des valeurs d’indicateur, car la longueur des données est déjà connue. Si une application utilise une mémoire tampon de longueur/d’indicateur avec des données de longueur fixe, le pilote ignore toutes les longueurs qui lui sont passées.  
  
 La longueur de la mémoire tampon de données et des données qu’elle contient est mesurée en octets, par opposition aux caractères. Cette distinction n’est pas importante pour les programmes qui utilisent des chaînes ANSI, car les longueurs en octets et les caractères sont les mêmes.  
  
 Lorsque le tampon de données représente un champ de descripteur, un champ ou un attribut de diagnostic défini par le pilote, l’application doit indiquer au gestionnaire de pilotes la nature de l’argument de fonction qui indique la valeur du champ ou de l’attribut. Pour ce faire, l’application définit l’argument de longueur dans tout appel de fonction qui définit le champ ou l’attribut sur l’une des valeurs suivantes. (Il en est de même pour les fonctions qui récupèrent les valeurs du champ ou de l’attribut, à l’exception du fait que l’argument pointe vers les valeurs que la fonction de paramètre se trouve dans l’argument lui-même.)  
  
-   Si l’argument de fonction qui indique la valeur du champ ou de l’attribut est un pointeur vers une chaîne de caractères, l’argument de *longueur* est la longueur de la chaîne ou SQL_NTS.  
  
-   Si l’argument de fonction qui indique la valeur du champ ou de l’attribut est un pointeur vers une mémoire tampon binaire, l’application place le résultat de la macro SQL_LEN_BINARY_ATTR (*longueur*) dans l’argument de *longueur* . Cela place une valeur négative dans l’argument de *longueur* .  
  
-   Si l’argument de fonction qui indique la valeur du champ ou de l’attribut est un pointeur vers une valeur autre qu’une chaîne de caractères ou une chaîne binaire, l’argument de *longueur* doit avoir la valeur SQL_IS_POINTER.  
  
-   Si l’argument de fonction qui indique la valeur du champ ou de l’attribut contient une valeur de longueur fixe, l’argument de *longueur* est SQL_IS_INTEGER, SQL_IS_UINTEGER, SQL_IS_SMALLINT ou SQL_ISI_USMALLINT, selon le cas.  
  
 Cette section contient les rubriques suivantes :  
  
-   [Mémoires tampons différées](../../../odbc/reference/develop-app/deferred-buffers.md)  
  
-   [Allocation et libération de mémoires tampons](../../../odbc/reference/develop-app/allocating-and-freeing-buffers.md)  
  
-   [Utilisation des tampons de données](../../../odbc/reference/develop-app/using-data-buffers.md)

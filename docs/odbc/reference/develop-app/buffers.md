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
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 306632f544f144aa4b21e150543c2d4ca5a37d0e
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63008015"
---
# <a name="buffers"></a>Mémoires tampons
Une mémoire tampon est tout bloc de mémoire de l’application utilisée pour passer des données entre l’application et le pilote. Par exemple, mémoires tampons d’application peuvent être associées, ou *lié,* avec les colonnes du jeu de résultats **SQLBindCol**. Comme chaque ligne est extraite, les données sont retournées pour chaque colonne dans ces mémoires tampons. *Entrée de mémoires tampons* sont utilisés pour passer des données à partir de l’application au pilote ; *mémoires tampons de sortie* sont utilisées pour retourner des données à partir du pilote à l’application.  
  
> [!NOTE]  
>  Si une fonction ODBC retourne SQL_ERROR, le contenu de tous les arguments sortie à cette fonction n’est pas défini.  
  
 Cette discussion s’occupe principalement avec les mémoires tampons de type indéterminé. Les adresses de ces mémoires tampons apparaissent en tant qu’arguments de type SQLPOINTER, telles que la *TargetValuePtr* argument dans **SQLBindCol**. Toutefois, certains des éléments abordées ici, telles que les arguments utilisés avec les mémoires tampons, s’appliquent également aux arguments utilisés pour passer des chaînes au pilote, telles que la *TableName* argument dans **SQLTables**.  
  
 Ces mémoires tampons sont généralement fournis par paires. *Mémoires tampons de données* sont utilisée pour transmettre les données proprement dites, alors que *mémoires tampon de longueur / d’indicateur* sont utilisés pour passer la longueur des données dans le tampon de données ou une valeur spécifique telle que de SQL_NULL_DATA, ce qui indique que les données sont NULL. La longueur des données dans un tampon de données est différente de la longueur de la mémoire tampon de données elle-même. L’illustration suivante montre la relation entre la mémoire tampon de données et de la mémoire tampon de longueur / d’indicateur.  
  
 ![Mémoire tampon de données et longueur&#47;tampon d’indicateur](../../../odbc/reference/develop-app/media/pr09.gif "pr09")  
  
 Une mémoire tampon de longueur / d’indicateur est nécessaire chaque fois que le tampon de données contient des données de longueur variable, comme binaire ou caractère. Si la mémoire tampon de données contient des données de longueur fixe, comme une structure entier ou une date, une mémoire tampon de longueur / d’indicateur est nécessaire uniquement pour passer des valeurs d’indicateur, car la longueur des données est déjà connue. Si une application utilise une mémoire tampon de longueur / d’indicateur avec les données de longueur fixe, le pilote ignore les longueurs passés qu’il contient.  
  
 La longueur de la mémoire tampon de données et les données qu’il contient est mesurée en octets, par opposition aux caractères. Cette distinction est sans importance pour les programmes qui utilisent des chaînes ANSI, car les longueurs en octets et les caractères sont les mêmes.  
  
 Lorsque le tampon de données représente un champ de descripteur définis par le pilote, un champ de diagnostic ou un attribut, l’application doit indiquer la nature de l’argument de fonction qui indique la valeur du champ ou d’un attribut pour le Gestionnaire de pilotes. L’application effectue cela en définissant l’argument de longueur dans n’importe quel appel de fonction qui définit le champ ou un attribut à une des valeurs suivantes. (Le même est vrai pour les fonctions qui récupèrent les valeurs du champ ou de l’attribut, hormis le fait que l’argument pointe vers les valeurs pour la fonction de paramètre dans l’argument lui-même.)  
  
-   Si l’argument de fonction qui indique la valeur du champ ou l’attribut est un pointeur vers une chaîne de caractères, le *longueur* argument est la longueur de la chaîne ou le SQL_NTS.  
  
-   Si l’argument de fonction qui indique la valeur du champ ou l’attribut est un pointeur vers une mémoire tampon binaire, l’application place le résultat de la SQL_LEN_BINARY_ATTR (*longueur*) (macro) dans le *longueur* argument. Cela place une valeur négative dans le *longueur* argument.  
  
-   Si l’argument de fonction qui indique la valeur du champ ou l’attribut est un pointeur vers une valeur autre qu’une chaîne de caractères ou une chaîne binaire, le *longueur* argument doit avoir la valeur SQL_IS_POINTER.  
  
-   Si l’argument de fonction qui indique la valeur du champ ou d’un attribut contient une valeur de longueur fixe, le *longueur* argument est SQL_IS_INTEGER, SQL_IS_UINTEGER, SQL_IS_SMALLINT ou SQL_ISI_USMALLINT, comme il convient.  
  
 Cette section contient les rubriques suivantes.  
  
-   [Mémoires tampons différées](../../../odbc/reference/develop-app/deferred-buffers.md)  
  
-   [Allocation et libération de mémoires tampons](../../../odbc/reference/develop-app/allocating-and-freeing-buffers.md)  
  
-   [Utilisation des tampons de données](../../../odbc/reference/develop-app/using-data-buffers.md)

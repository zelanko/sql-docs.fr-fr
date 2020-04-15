---
title: Tampons Microsoft Docs
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
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81306284"
---
# <a name="buffers"></a>Mémoires tampons
Un tampon est n’importe quelle mémoire d’application utilisée pour passer des données entre l’application et le pilote. Par exemple, les tampons d’application peuvent être associés ou *liés à des* colonnes définies de résultat avec **SQLBindCol**. Au fur et à mesure que chaque rangée est récupérée, les données sont retournées pour chaque colonne dans ces tampons. *Les tampons d’entrée* sont utilisés pour transmettre les données de l’application au conducteur; *les tampons* de sortie sont utilisés pour renvoyer les données du conducteur à l’application.  
  
> [!NOTE]  
>  Si une fonction ODBC renvoie SQL_ERROR, le contenu de tout argument de sortie à cette fonction n’est pas défini.  
  
 Cette discussion porte principalement sur des tampons de type indéterminé. Les adresses de ces tampons apparaissent comme des arguments de type SQLPOINTER, comme l’argument *TargetValuePtr* dans **SQLBindCol**. Cependant, certains des éléments abordés ici, comme les arguments utilisés avec les tampons, s’appliquent également aux arguments utilisés pour passer des ficelles au conducteur, comme *l’argument De TableName* dans **SQLTables**.  
  
 Ces tampons viennent généralement par paires. *Les tampons de données* sont utilisés pour transmettre les données elles-mêmes, tandis que les tampons de *longueur/indicateur* sont utilisés pour passer la longueur des données dans le tampon de données ou une valeur spéciale telle que SQL_NULL_DATA, ce qui indique que les données sont NULL. La longueur des données dans un tampon de données est différente de la longueur du tampon de données lui-même. L’illustration suivante montre la relation entre le tampon de données et le tampon longueur/indicateur.  
  
 ![Tampon de données et longueur&#47;tampon indicateur](../../../odbc/reference/develop-app/media/pr09.gif "pr09")  
  
 Un tampon de longueur/indicateur est requis chaque fois que le tampon de données contient des données à durée variable, telles que les données de caractère ou binaires. Si le tampon de données contient des données à durée fixe, telles qu’une structure d’intégrateur ou de date, un tampon de longueur/indicateur n’est nécessaire que pour dépasser les valeurs des indicateurs parce que la longueur des données est déjà connue. Si une application utilise un tampon de longueur/indicateur avec des données à durée fixe, le conducteur ignore les longueurs qui y sont passées.  
  
 La longueur du tampon de données et des données qu’il contient est mesurée en octets, par opposition aux caractères. Cette distinction n’est pas importante pour les programmes qui utilisent des chaînes ANSI parce que les longueurs dans les octets et les personnages sont les mêmes.  
  
 Lorsque le tampon de données représente un champ descripteur, un champ de diagnostic ou un attribut défini par le conducteur, l’application doit indiquer au gestionnaire de conducteur la nature de l’argument de fonction qui indique la valeur du champ ou de l’attribut. L’application le fait en définissant l’argument de longueur dans n’importe quel appel de fonction qui définit le champ ou l’attribut à l’une des valeurs suivantes. (Il en va de même pour les fonctions qui récupèrent les valeurs du champ ou de l’attribut, à l’exception que l’argument indique les valeurs que pour la fonction de réglage sont dans l’argument lui-même.)  
  
-   Si l’argument de fonction qui indique la valeur du champ ou de l’attribut est un pointeur à une chaîne de caractère, l’argument de *longueur* est la longueur de la chaîne ou SQL_NTS.  
  
-   Si l’argument de fonction qui indique la valeur pour le champ ou l’attribut est un pointeur à un tampon binaire, l’application place le résultat de la SQL_LEN_BINARY_ATTR(*longueur)* macro dans l’argument *de longueur.* Cela place une valeur négative dans l’argument *de longueur.*  
  
-   Si l’argument de fonction qui indique la valeur pour le champ ou l’attribut est un pointeur à une valeur autre qu’une chaîne de caractère ou une chaîne binaire, l’argument *de longueur* devrait avoir la valeur SQL_IS_POINTER.  
  
-   Si l’argument de fonction qui indique la valeur du champ ou de l’attribut contient une valeur fixe, l’argument *de longueur* est SQL_IS_INTEGER, SQL_IS_UINTEGER, SQL_IS_SMALLINT ou SQL_ISI_USMALLINT, le cas échéant.  
  
 Cette section contient les rubriques suivantes :  
  
-   [Mémoires tampons différées](../../../odbc/reference/develop-app/deferred-buffers.md)  
  
-   [Allocation et libération de mémoires tampons](../../../odbc/reference/develop-app/allocating-and-freeing-buffers.md)  
  
-   [Utilisation des tampons de données](../../../odbc/reference/develop-app/using-data-buffers.md)

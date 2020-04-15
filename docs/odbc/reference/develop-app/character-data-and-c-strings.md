---
title: Données de caractère et chaînes C (fr) Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- data buffers [ODBC], length
- data buffers [ODBC], character data
- buffers [ODBC], C strings
- buffers [ODBC], character data
- character data and buffers [ODBC]
- length of data buffers [ODBC]
- data buffers [ODBC], C strings
- buffers [ODBC], length
- C strings and buffers [ODBC]
ms.assetid: 3a141cb4-229d-4027-9349-615cb2995e36
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 7bb25022d4e0c0559f2a8f77b89a4ba26aeba33a
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81307489"
---
# <a name="character-data-and-c-strings"></a>Données caractères et chaînes C
Les paramètres d’entrée qui se réfèrent à des données de caractère à longueur variable (tels que les noms de colonnes, les paramètres dynamiques et les valeurs d’attribut de chaîne) ont un paramètre de longueur associé. Si l’application met fin aux cordes avec le caractère nul, comme c’est typique dans C, elle fournit comme argument soit la longueur des octets de la chaîne (sans compter le null-terminateur) ou SQL_NTS (Null-Ended String). Un argument de longueur non négatif spécifie la longueur réelle de la chaîne associée. L’argument de longueur peut être de 0 pour spécifier une chaîne de longueur zéro, qui est distincte d’une valeur NULL. La valeur négative SQL_NTS ordonne au conducteur de déterminer la longueur de la chaîne en localisant le caractère de résiliation nulle.  
  
 Lorsque les données de caractère sont retournées du conducteur à l’application, le conducteur doit toujours les interrompre. Cela donne à l’application le choix de gérer les données comme une chaîne ou un tableau de caractère. Si le tampon d’application n’est pas assez grand pour retourner toutes les données de caractère, le conducteur les tronque à la longueur octet du tampon moins le nombre d’octets requis par le caractère de non-résiliation, termine les données tronquées, et les stocke dans le tampon. Par conséquent, les applications doivent toujours allouer de l’espace supplémentaire pour le caractère de résiliation nulle dans les tampons utilisés pour récupérer les données de caractère. Par exemple, un tampon de 51 byte est nécessaire pour récupérer 50 caractères de données.  
  
 L’application et le conducteur doivent faire l’objet d’une attention particulière lors de l’envoi ou de la récupération de données de caractères longs dans les pièces avec **SQLPutData** ou **SQLGetData**. Si les données sont transmises sous forme d’une série de chaînes non résiliées, les caractères de terminaison nulle sur ces cordes doivent être dépouillés avant que les données puissent être remontées.  
  
 Un certain nombre de programmeurs ODBC ont des données de caractère confuses et des chaînes C. Que cela s’est produit est un artefact d’utiliser la langue C lors de la définition des fonctions ODBC. Si un conducteur ou une application ODBC utilise un autre langage - rappelez-vous que l’ODBC est indépendant de la langue - cette confusion est moins susceptible de se produire.  
  
 Lorsque les chaînes C sont utilisées pour conserver des données de caractère, le caractère de résiliation nulle n’est pas considéré comme faisant partie des données et n’est pas compté dans le cadre de sa longueur d’entrée. Par exemple, les données de caractère "ABC" peuvent être tenues sous le nom de chaîne C "ABC'0" ou le tableau de caractères 'A', 'B', 'C'. La longueur d’ordite des données est 3, qu’elle soit traitée ou non comme une chaîne ou un tableau de caractère.  
  
 Bien que les applications et les pilotes utilisent généralement des chaînes C (des tableaux de caractères annulés) pour conserver des données de caractère, il n’est pas nécessaire de le faire. Dans C, les données de caractère peuvent également être traitées comme un tableau de caractères (sans interruption nulle) et sa longueur d’ente passée séparément dans le tampon longueur/indicateur.  
  
 Étant donné que les données de caractère peuvent être conservées dans un tableau non-null-ended et sa longueur d’byte passé séparément, il est possible d’intégrer des caractères nuls dans les données de caractère. Cependant, le comportement des fonctions ODBC dans ce cas est indéfini et il est spécifique au conducteur si un pilote gère cela correctement. Ainsi, les applications interopérables doivent toujours traiter les données de caractère qui peuvent contenir des caractères nuls intégrés comme données binaires.

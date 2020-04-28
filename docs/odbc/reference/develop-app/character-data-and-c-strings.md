---
title: Données caractères et chaînes C | Microsoft Docs
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
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/27/2020
ms.locfileid: "81307489"
---
# <a name="character-data-and-c-strings"></a>Données caractères et chaînes C
Les paramètres d’entrée qui font référence à des données de caractères de longueur variable (tels que les noms de colonnes, les paramètres dynamiques et les valeurs d’attribut de chaîne) ont un paramètre de longueur associé. Si l’application termine les chaînes avec le caractère null, comme c’est généralement le cas dans C, elle fournit comme argument la longueur en octets de la chaîne (sans le terminateur null) ou la SQL_NTS (chaîne terminée par le caractère null). Un argument de longueur non négative spécifie la longueur réelle de la chaîne associée. L’argument de longueur peut être 0 pour spécifier une chaîne de longueur nulle, ce qui est différent d’une valeur NULL. La valeur négative SQL_NTS indique au pilote de déterminer la longueur de la chaîne en localisant le caractère de fin null.  
  
 Quand des données de type caractère sont retournées du pilote à l’application, le pilote doit toujours l’arrêter. Cela permet à l’application de choisir s’il faut gérer les données sous forme de chaîne ou de tableau de caractères. Si la mémoire tampon de l’application n’est pas assez grande pour retourner toutes les données de type caractère, le pilote la tronque à la longueur en octets de la mémoire tampon moins le nombre d’octets requis par le caractère de fin null, termine les données tronquées et les stocke dans la mémoire tampon. Par conséquent, les applications doivent toujours allouer de l’espace supplémentaire pour le caractère de fin null dans les mémoires tampons utilisées pour récupérer les données de caractères. Par exemple, une mémoire tampon de 51 octets est nécessaire pour récupérer 50 caractères de données.  
  
 Une attention particulière doit être prise par l’application et le pilote lors de l’envoi ou de la récupération de données à caractères longs en parties avec **SQLPutData** ou **SQLGetData**. Si les données sont transmises sous la forme d’une série de chaînes terminées par le caractère null, les caractères de fin null sur ces chaînes doivent être supprimés pour que les données puissent être réassemblées.  
  
 Un certain nombre de programmeurs ODBC ont des données de caractères et des chaînes C confuses. Ce qui s’est produit est un artefact de l’utilisation du langage C lors de la définition des fonctions ODBC. Si une application ou un pilote ODBC utilise une autre langue, n’oubliez pas qu’ODBC est indépendant de la langue. cette confusion est moins susceptible de se produire.  
  
 Lorsque les chaînes C sont utilisées pour contenir des données de type caractère, le caractère de fin null n’est pas considéré comme faisant partie des données et n’est pas compté dans le cadre de sa longueur d’octet. Par exemple, les données caractères « ABC » peuvent être conservées en tant que chaîne C « ABC\0 » ou tableau de caractères {« A », « B », « C »}. La longueur en octets des données est 3, qu’elles soient ou non traitées comme une chaîne ou un tableau de caractères.  
  
 Bien que les applications et les pilotes utilisent couramment des chaînes C (tableaux de caractères se terminant par null) pour contenir des données de type caractère, il n’est pas nécessaire de le faire. En C, les données de caractères peuvent également être traitées en tant que tableau de caractères (sans fin null) et sa longueur d’octet est passée séparément dans la mémoire tampon de longueur/d’indicateur.  
  
 Étant donné que les données caractères peuvent être conservées dans un tableau non-terminé par le caractère null et que leur longueur d’octet est passée séparément, il est possible d’incorporer des caractères null dans les données de type caractère. Toutefois, le comportement des fonctions ODBC dans ce cas n’est pas défini et il est spécifique au pilote, qu’un pilote gère correctement ce problème. Ainsi, les applications interopérables doivent toujours gérer les données de type caractère qui peuvent contenir des caractères null incorporés comme données binaires.

---
title: Caractères de données et chaînes C | Microsoft Docs
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
author: MightyPen
ms.author: genemi
ms.openlocfilehash: ed99ab72e3d5112588a0b1c93df34b01aff7acdd
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "68044920"
---
# <a name="character-data-and-c-strings"></a>Données caractères et chaînes C
Les paramètres d’entrée qui font référence aux données de caractères de longueur variable (par exemple, les noms de colonnes, paramètres dynamiques et les valeurs d’attribut de chaîne) disposent d’un paramètre de longueur. Si l’application termine par le caractère null, comme cela est courant en C, les chaînes, il fournit en tant qu’argument soit la longueur en octets de la chaîne (sans la marque de fin null) ou SQL_NTS (String Null-Terminated). Un argument de longueur non négative spécifie la longueur réelle de la chaîne associée. L’argument de longueur peut être 0 pour spécifier une chaîne de longueur nulle, ce qui est différente d’une valeur NULL. La valeur négative SQL_NTS dirige le pilote pour déterminer la longueur de la chaîne en recherchant le caractère de fin de la valeur null.  
  
 Lorsque les données de caractère sont renvoyées à partir du pilote à l’application, le pilote doit toujours null-arrêtez-la. Cela donne la possibilité de gérer les données comme une chaîne ou un tableau de caractères à l’application. Si la mémoire tampon d’application n’est pas assez grande pour retourner toutes les données de caractère, le pilote tronque à la longueur d’octet de la mémoire tampon moins le nombre d’octets requis par le caractère null de terminaison, les données tronquées sont terminées par null et le stocke dans le mémoire tampon. Par conséquent, les applications doivent toujours allouer un espace supplémentaire pour le caractère de fin de la valeur null dans les mémoires tampons utilisées pour récupérer des données caractères. Par exemple, une mémoire tampon 51-octets est nécessaire pour récupérer les 50 caractères de données.  
  
 Une attention particulière doit être prise par l’application et le pilote lors de l’envoi ou de récupération la durée pendant laquelle les données de caractères dans des parties avec **SQLPutData** ou **SQLGetData**. Si les données sont transmises en tant que série de chaînes se terminant par null, les caractères de caractère nul de terminaison sur ces chaînes doivent être supprimés avant que les données peuvent être réassemblées.  
  
 Un nombre de programmeurs ODBC ont confondu des données de caractères et chaînes C. Cet événement est un artefact de l’utilisation du langage C lors de la définition de fonctions ODBC. Si un pilote ODBC ou une application utilise une autre langue - n’oubliez pas que ODBC est indépendant du langage, cette confusion est moins susceptible de survenir.  
  
 Lorsque les chaînes C servent à stocker des données de type caractère, le caractère null de terminaison n’est pas considéré comme faisant partie des données et n’est pas compté dans le cadre de sa longueur en octets. Par exemple, le données de caractères « ABC » peut être maintenu en tant que la chaîne C « ABC\0 » ou le tableau de caractères {« A », « B », « C »}. La longueur d’octet des données est 3, si elle est traitée comme une chaîne ou un tableau de caractères.  
  
 Bien que les applications et pilotes utilisent couramment chaînes C (se terminant par null les tableaux de caractères) pour contenir les données de type caractère, il n’est pas nécessaire pour ce faire. En C, les données de caractères peuvent également être traitées comme un tableau de caractères (sans le caractère nul de terminaison) et sa longueur en octets passé séparément dans la mémoire tampon de longueur / d’indicateur.  
  
 Étant donné que les données caractères peuvent être conservées dans un tableau non nul et sa longueur en octets passé séparément, il est possible d’incorporer des caractères null dans les données de type caractère. Toutefois, le comportement de fonctions ODBC dans ce cas n’est pas défini, et il est spécifique au pilote si un pilote gère cela correctement. Par conséquent, les applications interopérables doivent gérer les données de caractères qui peuvent contenir des caractères null incorporés en tant que données binaires.

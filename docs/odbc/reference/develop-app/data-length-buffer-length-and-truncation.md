---
title: Longueur des données, longueur de la mémoire tampon et troncation | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- data buffers [ODBC], length
- data length [ODBC]
- truncating data [ODBC]
- length of data buffers [ODBC]
- buffers [ODBC], length
ms.assetid: 2825c6e7-b9ff-42fe-84fc-7fb39728ac5d
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: b2e7b8d1e60cd83594509c2ab5cbc24e04546eca
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/27/2020
ms.locfileid: "81305227"
---
# <a name="data-length-buffer-length-and-truncation"></a>Longueur des données, longueur de la mémoire tampon et troncation
La *longueur des données* est la longueur en octets des données, car elles sont stockées dans la mémoire tampon de données de l’application, et non dans la mesure où elles sont stockées dans la source de données. Cette distinction est importante, car les données sont souvent stockées dans des types différents dans la mémoire tampon de données que dans la source de données. Ainsi, pour les données envoyées à la source de données, il s’agit de la longueur d’octet des données avant la conversion vers le type de la source de données. Pour les données récupérées à partir de la source de données, il s’agit de la longueur d’octet des données après la conversion en type de tampon de données et avant la fin de la troncation.  
  
 Pour les données de longueur fixe, telles qu’un entier ou une structure de date, la longueur en octets des données est toujours la taille du type de données. En général, les applications allouent une mémoire tampon de données qui correspond à la taille du type de données. Si l’application alloue une mémoire tampon plus petite, les conséquences ne sont pas définies car le pilote part du principe que la mémoire tampon de données est la taille du type de données et ne tronque pas les données pour les adapter à une plus petite mémoire tampon. Si l’application alloue une mémoire tampon plus grande, l’espace supplémentaire n’est jamais utilisé.  
  
 Pour les données de longueur variable, telles que les données de type caractère ou binaire, il est important de reconnaître que la longueur en octets des données est différente de la longueur d’octet de la mémoire tampon et, souvent, de celles-ci. La relation de ces deux longueurs est décrite dans la section [mémoires tampons](../../../odbc/reference/develop-app/buffers.md) . Si la longueur d’octet des données est supérieure à la longueur d’octet de la mémoire tampon, le pilote tronque les données extraites jusqu’à la longueur en octets de la mémoire tampon et retourne SQL_SUCCESS_WITH_INFO avec SQLSTATE 01004 (données tronquées). Toutefois, la longueur de l’octet retourné correspond à la longueur des données non tronquées.  
  
 Supposons, par exemple, qu’une application alloue 50 octets pour une mémoire tampon de données binaires. Si le pilote comporte 10 octets de données binaires à retourner, il retourne ces 10 octets dans la mémoire tampon. La longueur en octets des données est de 10, et la longueur d’octet de la mémoire tampon est de 50. Si le pilote a 60 octets de données binaires à retourner, il tronque les données à 50 octets, retourne ces octets dans la mémoire tampon et retourne SQL_SUCCESS_WITH_INFO. La longueur en octets des données est 60 (longueur avant troncation), et la longueur d’octet de la mémoire tampon est toujours de 50.  
  
 Un enregistrement de diagnostic est créé pour chaque colonne tronquée. Étant donné qu’il faut du temps au pilote pour créer ces enregistrements et pour que l’application puisse les traiter, la troncation peut dégrader les performances. En règle générale, une application peut éviter ce problème en allouant suffisamment de mémoires tampons, bien que cela ne soit pas possible lors de l’utilisation de données de type long. Lorsque la troncation de données se produit, l’application peut parfois allouer une mémoire tampon plus importante et récupérer les données. Cela n’est pas vrai dans tous les cas. Si la troncation se produit lors de l’obtention de données avec des appels à **SQLGetData**, l’application n’a pas besoin d’appeler **SQLGetData** pour les données qui ont déjà été retournées ; Pour plus d’informations, consultez [obtention de données de type long](../../../odbc/reference/develop-app/getting-long-data.md).

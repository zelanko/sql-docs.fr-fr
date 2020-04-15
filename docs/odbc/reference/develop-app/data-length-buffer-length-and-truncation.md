---
title: Longueur de données, longueur tampon et truncation Microsoft Docs
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
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81305227"
---
# <a name="data-length-buffer-length-and-truncation"></a>Longueur des données, longueur de la mémoire tampon et troncation
La *longueur des données* est la longueur d’entrée des données car elles seraient stockées dans le tampon de données de l’application, et non dans la mesure où elles sont stockées dans la source de données. Cette distinction est importante parce que les données sont souvent stockées dans différents types dans le tampon de données que dans la source de données. Donc, pour les données envoyées à la source de données, c’est la longueur d’entrée des données avant la conversion au type de la source de données. Pour les données récupérées à partir de la source de données, il s’agit de la longueur d’entrée des données après la conversion au type du tampon de données et avant toute troncation.  
  
 Pour les données à durée fixe, telles qu’un intégrant ou une structure de date, la longueur des données est toujours la taille du type de données. En général, les applications allouent un tampon de données qui est la taille du type de données. Si l’application alloue un tampon plus petit, les conséquences ne sont pas définies parce que le conducteur suppose que le tampon de données est la taille du type de données et ne tronque pas les données pour s’adapter à un tampon plus petit. Si l’application alloue un tampon plus grand, l’espace supplémentaire n’est jamais utilisé.  
  
 Pour les données à durée variable, telles que les données de caractère ou binaires, il est important de reconnaître que la longueur des byte des données est séparée et souvent différente de la longueur des bytes du tampon. La relation de ces deux longueurs est décrite dans la section [Tampons.](../../../odbc/reference/develop-app/buffers.md) Si la longueur des bytes des données est supérieure à la longueur des bytes du tampon, le conducteur tronque les données récupérées jusqu’à la longueur des byte du tampon et retourne SQL_SUCCESS_WITH_INFO avec SQLSTATE 01004 (Données tronquées). Cependant, la longueur d’entrée retournée est la longueur des données fausses.  
  
 Par exemple, supposons qu’une application alloue 50 octets pour un tampon de données binaires. Si le conducteur a 10 octets de données binaires à retourner, il retourne ces 10 octets dans le tampon. La longueur d’entrée des données est de 10, et la longueur d’entrée du tampon est de 50. Si le conducteur a 60 octets de données binaires à retourner, il tronque les données à 50 octets, retourne ces octets dans le tampon, et retourne SQL_SUCCESS_WITH_INFO. La longueur d’en-avant des données est de 60 (la longueur avant la troncation), et la longueur d’entrée du tampon est encore de 50.  
  
 Un enregistrement diagnostique est créé pour chaque colonne qui est tronquée. Parce qu’il faut du temps pour que le conducteur crée ces enregistrements et que l’application les traite, la troncation peut dégrader les performances. Habituellement, une application peut éviter ce problème en allouant suffisamment de tampons, bien que cela puisse ne pas être possible lorsque vous travaillez avec de longues données. Lorsque la troncation de données se produit, l’application peut parfois allouer un tampon plus grand et réfélérer les données; ce n’est pas vrai dans tous les cas. Si la troncation se produit lors de l’obtention de données avec des appels à **SQLGetData**, l’application n’a pas besoin d’appeler **SQLGetData** pour les données qui ont déjà été retournées; pour plus d’informations, voir [Getting Long Data](../../../odbc/reference/develop-app/getting-long-data.md).

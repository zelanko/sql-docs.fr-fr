---
title: Longueur des données, la longueur de la mémoire tampon et troncation | Microsoft Docs
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
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 8586157237db1158587e3c39f1320b78d8251fb5
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "68081469"
---
# <a name="data-length-buffer-length-and-truncation"></a>Longueur des données, longueur de la mémoire tampon et troncation
Le *longueur des données* est la longueur en octets des données tel qu’il est stocké dans la mémoire tampon de données de l’application, pas lorsqu’elles sont stockées dans la source de données. Cette distinction est importante, car les données sont souvent stockées dans différents types dans la mémoire tampon de données que dans la source de données. Par conséquent, pour les données envoyées à la source de données, c’est la longueur en octets des données avant la conversion en type de la source de données. Pour les données récupérées à partir de la source de données, il s’agit la longueur d’octet des données après la conversion vers le type de données de la mémoire tampon et avant toute troncation est effectuée.  
  
 Pour les données de longueur fixe, comme un entier ou une structure de date, la longueur d’octet des données est toujours la taille du type de données. En règle générale, les applications allouer un tampon de données qui est la taille du type de données. Si l’application alloue une mémoire tampon plus petits, les conséquences sont indéfinis, car le pilote part du principe que le tampon de données est la taille du type de données et ne tronque pas les données pour tenir dans une mémoire tampon plus petits. Si l’application alloue une mémoire tampon plus importante, l’espace supplémentaire n’est jamais utilisé.  
  
 Pour les données de longueur variable, telles que binaire ou caractère, il est important de reconnaître que la longueur d’octet des données est souvent différent à la longueur d’octet de la mémoire tampon et séparé. La relation de ces deux longueurs est décrite dans le [tampons](../../../odbc/reference/develop-app/buffers.md) section. Si la longueur d’octet des données est supérieure à la longueur d’octet de la mémoire tampon, le pilote tronque les données extraites à la longueur d’octet de la mémoire tampon et retourne SQL_SUCCESS_WITH_INFO avec SQLSTATE 01004 (données tronquées). Toutefois, la longueur d’octet retournée est la longueur des données non tronquées.  
  
 Par exemple, qu'une application alloue 50 octets pour une mémoire tampon de données binaires. Si le pilote a 10 octets de données binaires à retourner, elle retourne ces 10 octets dans la mémoire tampon. La longueur d’octet des données est 10, et la longueur d’octet de la mémoire tampon est 50. Si le pilote a 60 octets de données binaires à retourner, elle tronque les données à 50 octets retourne ces octets dans la mémoire tampon et retourne SQL_SUCCESS_WITH_INFO. La longueur d’octet des données est 60 (la longueur avant la troncation), et la longueur d’octet de la mémoire tampon est toujours 50.  
  
 Un enregistrement de diagnostic est créé pour chaque colonne est tronqué. Prenant un certain temps pour le pilote créer ces enregistrements et de l’application pour les traiter, une troncation peut dégrader les performances. En règle générale, une application peut éviter ce problème en allouant des mémoires tampons suffisamment grands, bien que cela est peut-être pas possible lorsque vous travaillez avec des données de type long. En cas de troncation de données, l’application peut parfois allouer une mémoire tampon plus importante et récupérer à nouveau les données ; Cela n’est pas vrai dans tous les cas. Si une troncation se produit lors de l’obtention des données avec les appels à **SQLGetData**, l’application ne doive pas appeler **SQLGetData** pour les données qui ont déjà été retournées ; pour plus d’informations, consultez [mise en route Données de type long](../../../odbc/reference/develop-app/getting-long-data.md).

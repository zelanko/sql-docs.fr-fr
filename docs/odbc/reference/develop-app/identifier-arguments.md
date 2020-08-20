---
description: Arguments d’identificateur
title: Arguments des identificateurs | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- identifier arguments [ODBC]
- catalog functions [ODBC], arguments
- arguments in catalog functions [ODBC], identifier
ms.assetid: b9de003f-cb49-4dec-b528-14a5b8ff12bd
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 24efb295c9c27dbfc5edc2b1d7a46d6ca166e2c9
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/17/2020
ms.locfileid: "88461450"
---
# <a name="identifier-arguments"></a>Arguments d’identificateur
Si une chaîne dans un argument d’identificateur est entre guillemets, le pilote supprime les espaces de début et de fin et traite littéralement la chaîne entre guillemets. Si la chaîne n’est pas entre guillemets, le pilote supprime les espaces à droite et plie la chaîne en majuscules. La définition d’un argument d’identificateur sur un pointeur null retourne SQL_ERROR et SQLSTATE HY009 (utilisation non valide du pointeur null), à moins que l’argument ne soit un nom de catalogue et que les catalogues ne soient pas pris en charge.  
  
 Ces arguments sont traités comme des arguments d’identificateur si l’attribut d’instruction SQL_ATTR_METADATA_ID est défini sur SQL_TRUE. Dans ce cas, le trait de soulignement (_) et le signe de pourcentage (%) sera traité comme le caractère réel, et non comme un caractère de modèle de recherche. Ces arguments sont traités comme un argument ordinaire ou un argument de modèle, selon l’argument, si cet attribut a la valeur SQL_FALSE.  
  
 Bien que les identificateurs contenant des caractères spéciaux doivent être entre guillemets dans les instructions SQL, ils ne doivent pas être placés entre guillemets lorsqu’ils sont passés en tant qu’arguments de fonction de catalogue, car les guillemets passés aux fonctions de catalogue sont interprétés littéralement. Par exemple, supposons que le caractère d’identificateur guillemet (qui est spécifique au pilote et retourné via **SQLGetInfo**) soit un guillemet double ("). Le premier appel à **SQLTables** retourne un jeu de résultats contenant des informations sur la table Accounts payable, tandis que le deuxième appel retourne des informations sur la table « Accounts payable », ce qui n’est probablement pas ce qui était prévu.  
  
```  
SQLTables(hstmt1, NULL, 0, NULL, 0, "Accounts Payable", SQL_NTS, NULL, 0);  
SQLTables(hstmt2, NULL, 0, NULL, 0, "\"Accounts Payable\"", SQL_NTS, NULL, 0);  
```  
  
 Les identificateurs entre guillemets sont utilisés pour distinguer un vrai nom de colonne d’une pseudo-colonne du même nom, par exemple ROWID dans Oracle. Si « ROWID » est passé dans un argument d’une fonction de catalogue, la fonction fonctionnera avec la pseudo-colonne ROWID, si elle existe. Si la pseudo-colonne n’existe pas, la fonction fonctionne avec la colonne « ROWID ». Si ROWID est transmis dans un argument d’une fonction de catalogue, la fonction utilisera la colonne ROWID.  
  
 Pour plus d’informations sur les identificateurs entre guillemets, consultez [identificateurs entre guillemets](../../../odbc/reference/develop-app/quoted-identifiers.md).

---
title: Lors de la récupération des informations avec SQLGetTypeInfo types | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SQL data types [ODBC], identifiers
- SQLGetTypeInfo function [ODBC], retrieving data type information
- retrieving data type information [ODBC]
- type identifiers [ODBC], SQL
- identifiers [ODBC], SQL type
- SQL type identifiers [ODBC]
ms.assetid: d4f8b152-ab9e-4d05-a720-d10a08a6df81
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: c69113e4bb5457cb997f832179e5c1aab2841d82
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "63199092"
---
# <a name="retrieving-data-type-information-with-sqlgettypeinfo"></a>Récupération des informations sur les types de données avec SQLGetTypeInfo
Étant donné que les mappages de types de données SQL sous-jacente aux identificateurs de type ODBC sont approximatifs, ODBC fournit une fonction (**SQLGetTypeInfo**) via lequel un pilote peut complètement décrivent chaque type de données SQL dans la source de données. Cette fonction retourne un jeu de résultats, chaque ligne qui décrit les caractéristiques d’un type de données unique, telles que nom ou identificateur de type, précision, échelle, possibilité de valeur null.  
  
 Ces informations sont généralement utilisées par les applications génériques qui lui permet de créer et modifier des tables. Ce applications appellent **SQLGetTypeInfo** pour récupérer les informations de type de données et puis de les présenter tout ou partie de celui-ci à l’utilisateur. De telles applications doivent être conscient de deux choses :  
  
-   Plusieurs types de données SQL peut mapper à un identificateur de type unique, ce qui peut rendre difficile de déterminer le type de données à utiliser. Pour résoudre ce problème, le jeu de résultats est tout d’abord classé par identificateur de type et ensuite par proximité à la définition de l’identificateur de type. En outre, les types de données source de données sont prioritaires sur les types de données définis par l’utilisateur. Par exemple, supposons qu’une source de données définit les types de données entier et compteur pour être identiques, à ceci près que le compteur est à incrémentation automatique. Supposons également que le type défini par l’utilisateur WHOLENUM est un synonyme d’entier. Chacun de ces types est mappé à SQL_INTEGER. Dans le **SQLGetTypeInfo** jeu de résultats, entier s’affiche tout d’abord, suivie de WHOLENUM et ensuite de compteur. WHOLENUM apparaît après entier, car il est défini par l’utilisateur, mais avant de compteur, car il plus étroitement correspond à la définition de la SQL_INTEGER type identificateur.  
  
-   ODBC ne définit pas de noms de types de données pour une utilisation dans **CREATE TABLE** et **ALTER TABLE** instructions. Au lieu de cela, l’application doit utiliser le nom retourné dans la colonne TYPE_NAME du jeu de résultats retourné par **SQLGetTypeInfo**. La raison en est que bien que la plupart des SQL ne varie pas beaucoup dans le SGBD, les noms de types de données varient considérablement. Plutôt que de forcer les pilotes pour analyser les instructions SQL et remplacez les noms de types de données standard avec des noms de types de données propres au SGBD, ODBC requiert des applications à utiliser les noms propres au SGBD en premier lieu.  
  
 Notez que **SQLGetTypeInfo** ne décrit pas nécessairement tous les types de données une application peut rencontrer. En particulier, les jeux de résultats peuvent contenir des types de données pas directement pris en charge par la source de données. Par exemple, les types de données des colonnes de jeux de résultats retournés par les fonctions de catalogue sont définies par ODBC, et ces types de données ne peuvent pas être pris en charge par la source de données. Pour déterminer les caractéristiques des types de données dans un jeu de résultats, une application appelle **SQLColAttribute**.

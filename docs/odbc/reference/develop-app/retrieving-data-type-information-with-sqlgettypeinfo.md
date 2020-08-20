---
description: Récupération des informations sur les types de données avec SQLGetTypeInfo
title: Récupération d’informations sur les types de données avec SQLGetTypeInfo | Microsoft Docs
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: d7135a6d149646c43eb93218d2ce8952930748c6
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/17/2020
ms.locfileid: "88476521"
---
# <a name="retrieving-data-type-information-with-sqlgettypeinfo"></a>Récupération des informations sur les types de données avec SQLGetTypeInfo
Étant donné que les mappages des types de données SQL sous-jacents aux identificateurs de type ODBC sont approximatifs, ODBC fournit une fonction (**SQLGetTypeInfo**) par le biais de laquelle un pilote peut décrire complètement chaque type de données SQL dans la source de données. Cette fonction retourne un jeu de résultats, chaque ligne qui décrit les caractéristiques d’un type de données unique, telles que le nom, l’identificateur de type, la précision, l’échelle et la possibilité de valeur null.  
  
 Ces informations sont généralement utilisées par les applications génériques qui permettent à l’utilisateur de créer et de modifier des tables. De telles applications appellent **SQLGetTypeInfo** pour récupérer les informations sur le type de données et en présenter une partie ou la totalité à l’utilisateur. De telles applications doivent être conscientes de deux choses :  
  
-   Plusieurs types de données SQL peuvent être mappés à un seul identificateur de type, ce qui peut compliquer la détermination du type de données à utiliser. Pour résoudre ce cas, le jeu de résultats est ordonné en premier par l’identificateur de type et le second par proximité à la définition de l’identificateur de type. En outre, les types de données définis par la source de données ont la priorité sur les types de données définis par l’utilisateur. Par exemple, supposons qu’une source de données définit l’entier et les types de données de compteur pour être identiques, sauf que le compteur est auto-incrémenté. Supposons également que le type défini par l’utilisateur WHOLENUM est un synonyme de INTEGER. Chacun de ces types est mappé à SQL_INTEGER. Dans le jeu de résultats **SQLGetTypeInfo** , l’entier apparaît en premier, suivi de WHOLENUM, puis Counter. WHOLENUM apparaît après un entier, car il est défini par l’utilisateur, mais avant le compteur, car il correspond plus précisément à la définition de l’identificateur de type SQL_INTEGER.  
  
-   ODBC ne définit pas les noms de types de données à utiliser dans les instructions **Create table** et **ALTER TABLE** . Au lieu de cela, l’application doit utiliser le nom retourné dans la colonne TYPE_NAME du jeu de résultats retourné par **SQLGetTypeInfo**. Cela est dû au fait que, bien que la plupart des données SQL ne varient pas énormément entre les SGBD, les noms des types de données varient considérablement. Plutôt que de forcer les pilotes à analyser les instructions SQL et à remplacer les noms de types de données standard par des noms de types de données propres au SGBD, ODBC exige que les applications utilisent les noms propres au SGBD en premier lieu.  
  
 Notez que **SQLGetTypeInfo** ne décrit pas nécessairement tous les types de données qu’une application peut rencontrer. En particulier, les jeux de résultats peuvent contenir des types de données non directement pris en charge par la source de données. Par exemple, les types de données des colonnes des jeux de résultats retournés par les fonctions de catalogue sont définis par ODBC et ces types de données peuvent ne pas être pris en charge par la source de données. Pour déterminer les caractéristiques des types de données dans un jeu de résultats, une application appelle **SQLColAttribute**.

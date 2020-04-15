---
title: Récupérer les informations de type de données avec SQLGetTypeInfo (fr) Microsoft Docs
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
ms.openlocfilehash: 4ec2bbba824eaf3d74133cf9754eca2593c9fb79
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81300059"
---
# <a name="retrieving-data-type-information-with-sqlgettypeinfo"></a>Récupération des informations sur les types de données avec SQLGetTypeInfo
Étant donné que les cartographies des types de données SQL sous-jacentes aux identificateurs de type ODBC sont approximatives, ODBC fournit une fonction (**SQLGetTypeInfo**) par laquelle un conducteur peut décrire complètement chaque type de données SQL dans la source de données. Cette fonction renvoie un ensemble de résultats, dont chaque ligne décrit les caractéristiques d’un seul type de données, telles que le nom, l’identifiant de type, la précision, l’échelle et l’annulation.  
  
 Ces informations sont généralement utilisées par des applications génériques qui permettent à l’utilisateur de créer et de modifier des tables. Ces applications appellent **SQLGetTypeInfo** pour récupérer les informations de type de données et ensuite présenter une partie ou la totalité de celui-ci à l’utilisateur. Ces applications doivent être au courant de deux choses :  
  
-   Plus d’un type de données SQL peut cartographier un seul type d’identifiant, ce qui peut rendre difficile la déterminer quel type de données utiliser. Pour résoudre ce problème, l’ensemble de résultat est commandé d’abord par identifiant de type et ensuite par proximité de la définition de l’identifiant de type. En outre, les types de données définies par les sources de données ont préséance sur les types de données définis par l’utilisateur. Supposons, par exemple, qu’une source de données définit les types de données INTEGER et COUNTER comme les mêmes, sauf que COUNTER est auto-incrémentation. Supposons également que le type DÉFINI par l’utilisateur WHOLENUM est synonyme d’INTEGER. Chacun de ces types de cartes pour SQL_INTEGER. Dans l’ensemble de résultats **SQLGetTypeInfo,** INTEGER apparaît d’abord, suivi par WHOLENUM, puis COUNTER. WHOLENUM apparaît après INTEGER parce qu’il est défini par l’utilisateur, mais avant COUNTER parce qu’il correspond plus étroitement à la définition de l’identificateur de type SQL_INTEGER.  
  
-   ODBC ne définit pas les noms de type de données pour une utilisation dans les relevés **CREATE TABLE** et **ALTER TABLE.** Au lieu de cela, l’application devrait utiliser le nom retourné dans la colonne TYPE_NAME de l’ensemble de résultat retourné par **SQLGetTypeInfo**. La raison en est que, bien que la plupart des SQL ne varient pas beaucoup d’un million d’euros, les noms de type de données varient énormément. Plutôt que de forcer les conducteurs à analyser les relevés SQL et à remplacer les noms de type de données standard par des noms de type de données spécifiques au DBMS, ODBC exige des applications qu’elles utilisent les noms spécifiques au DBMS en premier lieu.  
  
 Notez que **SQLGetTypeInfo** ne décrit pas nécessairement tous les types de données qu’une application peut rencontrer. En particulier, les ensembles de résultats peuvent contenir des types de données qui ne sont pas directement pris en charge par la source de données. Par exemple, les types de données des colonnes dans les ensembles de résultats retournés par les fonctions de catalogue sont définis par ODBC et ces types de données peuvent ne pas être pris en charge par la source de données. Pour déterminer les caractéristiques des types de données dans un ensemble de résultats, une application appelle **SQLColAttribute**.

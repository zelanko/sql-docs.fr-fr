---
title: Handles d’instruction | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- statement handles [ODBC]
- handles [ODBC], statement
ms.assetid: 65d6d78b-a8c8-489a-9dad-f8d127a44882
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 1be90fe10d10a0b087d1c9724fed249805eb4dba
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/27/2020
ms.locfileid: "81299675"
---
# <a name="statement-handles"></a>Handles d’instruction
Une *instruction* est plus facilement considérée comme une instruction SQL, telle que **Select \* from employee**. Toutefois, une instruction est plus qu’une simple instruction SQL. elle se compose de toutes les informations associées à cette instruction SQL, telles que les jeux de résultats créés par l’instruction et les paramètres utilisés dans l’exécution de l’instruction. Une instruction n’a même pas besoin d’une instruction SQL définie par l’application. Par exemple, lorsqu’une fonction de catalogue telle que **SQLTables** est exécutée sur une instruction, elle exécute une instruction SQL prédéfinie qui retourne une liste de noms de tables.  
  
 Chaque instruction est identifiée par un descripteur d’instruction. Une instruction est associée à une seule connexion, et il peut y avoir plusieurs instructions sur cette connexion. Certains pilotes limitent le nombre d’instructions actives qu’ils prennent en charge ; l’option SQL_MAX_CONCURRENT_ACTIVITIES dans **SQLGetInfo** spécifie le nombre d’instructions actives prises en charge par un pilote sur une seule connexion. Une instruction est définie comme *active* si elle a des résultats en attente, où les résultats sont soit un jeu de résultats, soit le nombre de lignes affectées par une instruction **Insert**, **Update**ou **Delete** , ou les données sont envoyées avec plusieurs appels à **SQLPutData**.  
  
 Dans un morceau de code qui implémente ODBC (le gestionnaire de pilotes ou un pilote), le descripteur d’instruction identifie une structure qui contient des informations d’instruction, telles que :  
  
-   État de l’instruction  
  
-   Diagnostics au niveau de l’instruction en cours  
  
-   Adresses des variables d’application liées aux paramètres de l’instruction et aux colonnes de l’ensemble de résultats  
  
-   Paramètres actuels de chaque attribut d’instruction  
  
 Les descripteurs d’instruction sont utilisés dans la plupart des fonctions ODBC. En particulier, elles sont utilisées dans les fonctions pour lier des paramètres et des colonnes de jeu de résultats (**SQLBindParameter** et **SQLBindCol**), préparer et exécuter des instructions (**SQLPrepare**, **SQLExecute**et **SQLExecDirect**), récupérer des métadonnées (**SQLColAttribute** et **SQLDescribeCol**), extraire des résultats (**SQLFetch**) et récupérer les Diagnostics (**SQLGetDiagField** et **SQLGetDiagRec**). Ils sont également utilisés dans les fonctions de catalogue (**SQLColumns**, **SQLTables**, etc.) et un certain nombre d’autres fonctions.  
  
 Les descripteurs d’instruction sont alloués avec **SQLAllocHandle** et libérés avec **SQLFreeHandle**.

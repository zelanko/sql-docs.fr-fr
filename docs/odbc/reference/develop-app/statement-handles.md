---
title: Descripteurs d’instruction | Microsoft Docs
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
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 6f249bb13ece6382e96dfe953b1d3c1d96c7bf65
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63149004"
---
# <a name="statement-handles"></a>Handles d’instruction
Un *instruction* est plus facilement considérée comme une instruction SQL, tel que **sélectionnez \* à partir d’un employé**. Toutefois, une instruction est plus qu’une instruction SQL : il se compose de toutes les informations associées à cette instruction SQL, tels que des jeux de résultats créés par l’instruction et les paramètres utilisés dans l’exécution de l’instruction. Une instruction n’a même pas besoin d’avoir une instruction SQL définie par l’application. Par exemple, quand une fonction de catalogue comme **SQLTables** est exécutée sur une instruction, il s’exécute une instruction SQL prédéfinie qui retourne une liste de noms de table.  
  
 Chaque instruction est identifiée par un descripteur d’instruction. Une instruction est associée à une connexion unique, et il peut y avoir plusieurs instructions sur cette connexion. Certains pilotes de limitent le nombre d’instructions actives, qu'elles prennent en charge ; option le SQL_MAX_CONCURRENT_ACTIVITIES **SQLGetInfo** Spécifie le nombre d’instructions actif un pilote prend en charge sur une seule connexion. Une instruction est définie comme étant *active* si elle contient des résultats en attente, où des résultats sont un jeu de résultats ou le nombre de lignes affectées par une **insérer**, **mise à jour**, ou **Supprimer** instruction ou les données sont envoyées avec plusieurs appels à **SQLPutData**.  
  
 Au sein d’un morceau de code qui implémente ODBC (le Gestionnaire de pilotes ou un pilote), le descripteur d’instruction identifie une structure qui contient des informations sur l’instruction, telles que :  
  
-   État de l’instruction  
  
-   Les diagnostics au niveau de l’instruction actuelles  
  
-   Les adresses de variables d’application liés aux paramètres de l’instruction et les colonnes de jeu de résultats  
  
-   Les paramètres actuels de chaque attribut d’instruction  
  
 Descripteurs d’instruction sont utilisés dans la plupart des fonctions ODBC. En particulier, ils sont utilisés dans les fonctions pour lier les paramètres et les colonnes de jeu de résultats (**SQLBindParameter** et **SQLBindCol**), préparer et exécuter des instructions (**SQLPrepare** **SQLExecute**, et **SQLExecDirect**), de récupérer les métadonnées (**SQLColAttribute** et **SQLDescribeCol**), fetch résultats (**SQLFetch**) et récupérer les diagnostics (**SQLGetDiagField** et **SQLGetDiagRec**). Ils sont également utilisés dans les fonctions de catalogue (**SQLColumns**, **SQLTables**, et ainsi de suite) et un nombre d’autres fonctions.  
  
 Descripteurs d’instruction sont allouées avec **SQLAllocHandle** et libéré avec **SQLFreeHandle**.

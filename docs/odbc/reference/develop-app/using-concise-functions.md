---
title: Utilisation de fonctions concises | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- concise functions [ODBC]
- functions [ODBC], concise functions
- descriptors [ODBC], concise functions
ms.assetid: 31ac070f-8c59-4fd5-bd5a-466bb27dbca0
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 63313e3dfaec8dbcd91f3bb084bbaab46da40c6e
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/27/2020
ms.locfileid: "81306780"
---
# <a name="using-concise-functions"></a>Utilisation de fonctions concises
Certaines fonctions ODBC bénéficient d’un accès implicite aux descripteurs. Les rédacteurs d’applications peuvent les trouver plus facilement que l’appel de **SQLSetDescField** ou **SQLGetDescField**. Ces fonctions sont appelées fonctions *concises* , car elles exécutent un certain nombre de fonctions, notamment la définition ou l’obtention de champs de descripteur. Certaines fonctions concises permettent à une application de définir ou d’extraire plusieurs champs de descripteur associés dans un appel de fonction unique.  
  
 Des fonctions concises peuvent être appelées sans récupérer au préalable un handle de descripteur à utiliser comme argument. Ces fonctions fonctionnent avec les champs de descripteur associés au descripteur d’instruction sur lequel elles sont appelées.  
  
 Les fonctions concises **SQLBindCol** et **SQLBindParameter** lient une colonne ou un paramètre en définissant les champs de descripteur qui correspondent à leurs arguments. Chacune de ces fonctions effectue plus de tâches que de définir simplement des descripteurs. **SQLBindCol** et **SQLBindParameter** fournissent une spécification complète de la liaison d’une colonne de données ou d’un paramètre dynamique. Toutefois, une application peut modifier des détails individuels d’une liaison en appelant **SQLSetDescField** ou **SQLSetDescRec** et peut lier complètement une colonne ou un paramètre en effectuant une série d’appels appropriés à ces fonctions.  
  
 Les fonctions concise **SQLColAttribute**, **SQLDescribeCol**, **SQLDescribeParam**, **SQLNumParams**et **SQLNumResultCols** récupèrent des valeurs dans les champs de descripteur.  
  
 **SQLSetDescRec** et **SQLGetDescRec** sont des fonctions concises qui, avec un appel, définissent ou obtiennent plusieurs champs de descripteur qui affectent le type de données et le stockage des données de colonne ou de paramètre. **SQLSetDescRec** est un moyen efficace de modifier la liaison de données de colonnes ou de paramètres en une seule étape.  
  
 **SQLSetStmtAttr** et **SQLGetStmtAttr** servent de fonctions concises dans certains cas. (Voir [champs de descripteur](../../../odbc/reference/develop-app/descriptor-fields.md).)

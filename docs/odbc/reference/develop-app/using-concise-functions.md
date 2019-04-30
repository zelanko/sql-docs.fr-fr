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
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 1d70d3ca60a046a355549260406edba261f805e4
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63312481"
---
# <a name="using-concise-functions"></a>Utilisation de fonctions concises
Certaines fonctions ODBC accéder implicite pour les descripteurs. Créateurs d’applications peuvent les trouver plus pratique que l’appel **SQLSetDescField** ou **SQLGetDescField**. Ces fonctions sont appelées *concis* fonctionne car ils effectuent un nombre de fonctions, y compris de définir ou obtenir les champs de descripteur. Certaines fonctions concises permettent une application de définir ou extraire plusieurs champs de descripteur associés dans un seul appel de fonction.  
  
 Fonctions concises peuvent être appelées sans récupérer préalablement un handle de descripteur pour une utilisation en tant qu’argument. Ces fonctions fonctionnent avec les champs de descripteur associés au handle d’instruction qu’elles sont appelées sur.  
  
 Les fonctions concises **SQLBindCol** et **SQLBindParameter** lier une colonne ou un paramètre en définissant les champs de descripteur qui correspondent à leurs arguments. Chacune de ces fonctions effectue des tâches plus que de simplement définir les descripteurs. **SQLBindCol** et **SQLBindParameter** fournissent une spécification complète de la liaison d’une colonne de données ou d’un paramètre dynamique. Une application peut, toutefois, modifier les détails individuels d’une liaison en appelant **SQLSetDescField** ou **SQLSetDescRec** et peut lier complètement une colonne ou un paramètre, en effectuant une série d’appels appropriés à Ces fonctions.  
  
 Les fonctions concises **SQLColAttribute**, **SQLDescribeCol**, **SQLDescribeParam**, **SQLNumParams**, et  **SQLNumResultCols** récupérer des valeurs dans les champs de descripteur.  
  
 **SQLSetDescRec** et **SQLGetDescRec** sont des fonctions concises qui, avec un seul appel, définir ou obtenir plusieurs champs de descripteur qui affectent le type de données et le stockage de données de colonne ou du paramètre. **SQLSetDescRec** est un moyen efficace de changer la liaison de données de colonne ou du paramètre en une seule étape.  
  
 **SQLSetStmtAttr** et **SQLGetStmtAttr** servir de fonctions concises dans certains cas. (Consultez [champs de descripteur](../../../odbc/reference/develop-app/descriptor-fields.md).)

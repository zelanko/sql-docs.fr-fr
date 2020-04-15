---
title: Utilisation de fonctions concises (fr) Microsoft Docs
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
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81306780"
---
# <a name="using-concise-functions"></a>Utilisation de fonctions concises
Certaines fonctions ODBC ont un accès implicite aux descripteurs. Les auteurs d’applications peuvent les trouver plus pratiques que d’appeler **SQLSetDescField** ou **SQLGetDescField**. Ces fonctions sont appelées fonctions *concises* parce qu’elles remplissent un certain nombre de fonctions, y compris le réglage ou l’obtention de champs descripteurs. Certaines fonctions concises permettent à un ensemble d’applications ou de récupérer plusieurs champs descripteur connexes dans un seul appel de fonction.  
  
 Les fonctions concises peuvent être appelées sans d’abord récupérer une poignée descripteur pour une utilisation comme argument. Ces fonctions fonctionnent avec les champs descripteur associés à la poignée de déclaration sur laquelle ils sont appelés.  
  
 Les fonctions concises **SQLBindCol** et **SQLBindParameter** lient une colonne ou un paramètre en définissant les champs descripteur qui correspondent à leurs arguments. Chacune de ces fonctions effectue plus de tâches que de simplement définir des descripteurs. **SQLBindCol** et **SQLBindParameter** fournissent une spécification complète de la liaison d’une colonne de données ou d’un paramètre dynamique. Une application peut cependant modifier les détails individuels d’une liaison en appelant **SQLSetDescField** ou **SQLSetDescRec** et peut complètement lier une colonne ou un paramètre en effectuant une série d’appels appropriés à ces fonctions.  
  
 Les fonctions concises **SQLColAttribute**, **SQLDescribeCol**, **SQLDescribeParam**, **SQLNumParams**, et **SQLNumResultCols** récupérer des valeurs dans les champs descripteur.  
  
 **SQLSetDescRec** et **SQLGetDescRec** sont des fonctions concises qui, avec un seul appel, définissent ou obtiennent plusieurs champs descripteur qui affectent le type de données et le stockage des données de colonne ou de paramètre. **SQLSetDescRec** est un moyen efficace de modifier la liaison des données de colonne ou de paramètre en une seule étape.  
  
 **SQLSetStmtAttr** et **SQLGetStmtAttr** servent de fonctions concises dans certains cas. (Voir [Descriptor Fields](../../../odbc/reference/develop-app/descriptor-fields.md).)

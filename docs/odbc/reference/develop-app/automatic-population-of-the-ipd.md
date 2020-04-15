---
title: Population automatique de l’IPD (fr) Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- automatically populating ipd [ODBC]
- descriptors [ODBC], automatically populating ipd
- descriptors [ODBC], allocating and freeing
- ipd [ODBC]
- allocating and freeing descriptors [ODBC]
ms.assetid: 1184a7d8-d557-4140-843b-6633ae6deacc
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 1998ea1992ee7f14d87d01e348d955b017166088
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81285069"
---
# <a name="automatic-population-of-the-ipd"></a>Remplissage automatique de l’IPD
Certains conducteurs sont capables de définir les champs de l’IPD après qu’une requête paramétrée a été préparée. Les champs descripteur sont automatiquement peuplés d’informations sur le paramètre, y compris le type de données, la précision, l’échelle et d’autres caractéristiques. Cela équivaut à soutenir **SQLDescribeParam**. Ces informations peuvent être particulièrement précieuses pour une application lorsqu’elle n’a pas d’autre moyen de les découvrir, par exemple lorsqu’une requête ad hoc est effectuée avec des paramètres que l’application ne connaît pas.  
  
 Une demande détermine si le conducteur prend en charge la population automatique en appelant **SQLGetConnectAttr** avec un *attribut* de SQL_ATTR_AUTO_IPD. Si SQL_TRUE est retournée, le conducteur le prend en charge et l’application peut l’activer en définissant l’attribut SQL_ATTR_ENABLE_AUTO_IPD’énoncé à SQL_TRUE.  
  
 Lorsque la population automatique est soutenue et activée, le conducteur peuple les champs de l’IPD après qu’une déclaration SQL contenant des marqueurs de paramètres a été préparée par un appel à **SQLPrepare**. Une application peut récupérer ces informations en appelant **SQLGetDescField** ou **SQLGetDescRec**, ou **SQLDescribeParam**. L’application peut utiliser les informations pour lier le tampon d’application le plus approprié pour un paramètre ou pour spécifier une conversion de données pour elle.  
  
 La population automatique de l’IPD peut entraîner une pénalité de performance. Une application peut l’éteindre en réinitialisant l’attribut de l’SQL_ATTR_ENABLE_AUTO_IPD déclaration à SQL_FALSE (la valeur par défaut).

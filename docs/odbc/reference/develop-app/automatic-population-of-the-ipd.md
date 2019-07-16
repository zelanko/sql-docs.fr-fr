---
title: Remplissage automatique de l’IPD | Microsoft Docs
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
author: MightyPen
ms.author: genemi
ms.openlocfilehash: c1591843667ef01c6c88f5dfafb734f044679b2d
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "67909829"
---
# <a name="automatic-population-of-the-ipd"></a>Remplissage automatique de l’IPD
Certains pilotes sont capables de définition des champs de l’IPD après la préparation d’une requête paramétrable. Les champs de descripteur sont automatiquement remplies avec des informations sur le paramètre, y compris le type de données, précision, échelle et d’autres caractéristiques. Cela équivaut à la prise en charge **SQLDescribeParam**. Ces informations peuvent être particulièrement utiles pour une application lorsqu’il n’a aucun autre moyen de le découvrir, par exemple quand une requête ad hoc est effectuée avec les paramètres de l’application ne connaît pas.  
  
 Une application détermine si le pilote prend en charge le remplissage automatique en appelant **SQLGetConnectAttr** avec un *attribut* de SQL_ATTR_AUTO_IPD. Si SQL_TRUE est retourné, le pilote prend en charge et l’application peut l’activer en affectant à l’attribut d’instruction SQL_ATTR_ENABLE_AUTO_IPD SQL_TRUE.  
  
 Quand le remplissage automatique est pris en charge et activé, le pilote renseigne les champs de l’IPD après une instruction SQL contenant des marqueurs de paramètres a été préparée par un appel à **SQLPrepare**. Une application peut récupérer ces informations en appelant **SQLGetDescField** ou **SQLGetDescRec**, ou **SQLDescribeParam**. L’application peut utiliser les informations pour lier la mémoire tampon d’application plus approprié pour un paramètre ou pour spécifier une conversion de données pour celui-ci.  
  
 Remplissage automatique de l’IPD risque de produire une altération des performances. Une application peut désactiver en réinitialisant l’attribut d’instruction SQL_ATTR_ENABLE_AUTO_IPD aux SQL_FALSE (la valeur par défaut).

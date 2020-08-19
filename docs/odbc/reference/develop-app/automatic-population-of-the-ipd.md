---
description: Remplissage automatique de l’IPD
title: Remplissage automatique de la IPD | Microsoft Docs
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
ms.openlocfilehash: 73c0456f1c78ccc19f1ff55a1ab288baedae2e14
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/17/2020
ms.locfileid: "88476881"
---
# <a name="automatic-population-of-the-ipd"></a>Remplissage automatique de l’IPD
Certains pilotes sont en mesure de définir les champs de l’IPD après la préparation d’une requête paramétrable. Les champs de descripteur sont renseignés automatiquement avec des informations sur le paramètre, notamment le type de données, la précision, l’échelle et d’autres caractéristiques. Cela équivaut à la prise en charge de **SQLDescribeParam**. Ces informations peuvent être particulièrement utiles pour une application quand elle n’a pas d’autre moyen de la découvrir, par exemple lorsqu’une requête ad hoc est exécutée avec des paramètres que l’application ne connaît pas.  
  
 Une application détermine si le pilote prend en charge le remplissage automatique en appelant **SQLGetConnectAttr** avec un *attribut* de SQL_ATTR_AUTO_IPD. Si SQL_TRUE est retourné, le pilote le prend en charge et l’application peut l’activer en affectant à l’attribut d’instruction SQL_ATTR_ENABLE_AUTO_IPD la valeur SQL_TRUE.  
  
 Lorsque le remplissage automatique est pris en charge et activé, le pilote remplit les champs de l’IPD après qu’une instruction SQL contenant des marqueurs de paramètres a été préparée par un appel à **SQLPrepare**. Une application peut récupérer ces informations en appelant **SQLGetDescField** ou **SQLGetDescRec**, ou **SQLDescribeParam**. L’application peut utiliser les informations pour lier la mémoire tampon d’application la plus appropriée à un paramètre ou pour spécifier une conversion de données pour celle-ci.  
  
 Le remplissage automatique de l’IPD peut entraîner une baisse des performances. Une application peut la désactiver en réinitialisant l’attribut d’instruction SQL_ATTR_ENABLE_AUTO_IPD sur SQL_FALSE (valeur par défaut).

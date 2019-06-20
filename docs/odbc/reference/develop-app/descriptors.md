---
title: Descripteurs | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- descriptors [ODBC]
- descriptors [ODBC], about descriptors
- descriptor handles [ODBC]
- handles [ODBC], descriptor
ms.assetid: ef2cbb93-cd00-40f8-b1d2-5f5723a991aa
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: d50ce0c2023e187d63d08aa862398d18dc188fd1
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "62744230"
---
# <a name="descriptors"></a>Descripteurs
Un handle de descripteur fait référence à une structure de données qui conserve des informations sur les colonnes ou les paramètres dynamiques.  
  
 Fonctions ODBC qui opèrent sur des données de colonnes et de paramètres implicitement définir et récupérer des champs de descripteur. Par exemple, lorsque **SQLBindCol** est appelée pour lier des données de colonne, il définit les champs de descripteur qui décrivent complètement la liaison. Lorsque **SQLColAttribute** est appelée pour décrire les données de la colonne, elle retourne des données stockées dans les champs de descripteur.  
  
 Une application appelant les fonctions ODBC pas concerner les lui-même avec descripteurs. Aucune opération de base de données ne nécessite que l’application accéder directement aux descripteurs. Toutefois, pour certaines applications, l’accès direct aux descripteurs simplifie de nombreuses opérations. Par exemple diriger les accès aux descripteurs de permet de relier les données de la colonne, qui peuvent être plus efficaces que l’appel **SQLBindCol** à nouveau.  
  
> [!NOTE]  
>  La représentation physique du descripteur n’est pas définie. Applications obtenir un accès direct à un descripteur uniquement en manipulant des ses champs en appelant les fonctions ODBC avec le handle du descripteur.  
  
 Cette section contient les rubriques suivantes.  
  
-   [Types de descripteurs](../../../odbc/reference/develop-app/types-of-descriptors.md)  
  
-   [Champs de descripteur](../../../odbc/reference/develop-app/descriptor-fields.md)  
  
-   [Allocation et libération de descripteurs](../../../odbc/reference/develop-app/allocating-and-freeing-descriptors.md)  
  
-   [Obtention et définition des champs de descripteur](../../../odbc/reference/develop-app/getting-and-setting-descriptor-fields.md)

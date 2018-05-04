---
title: Descripteurs | Documents Microsoft
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: odbc
ms.reviewer: ''
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- descriptors [ODBC]
- descriptors [ODBC], about descriptors
- descriptor handles [ODBC]
- handles [ODBC], descriptor
ms.assetid: ef2cbb93-cd00-40f8-b1d2-5f5723a991aa
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: df7ca68c54f6d86162ed22a942b65792f13089e2
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
---
# <a name="descriptors"></a>Descripteurs
Un handle de descripteur fait référence à une structure de données qui conserve des informations sur des colonnes ou des paramètres dynamiques.  
  
 Fonctions ODBC qui opèrent sur des données de colonnes et de paramètres implicitement définir et récupérer des champs de descripteur. Par exemple, lorsque **SQLBindCol** est appelée pour lier les données de la colonne, il définit les champs de descripteur qui décrivent complètement la liaison. Lorsque **SQLColAttribute** est appelée pour décrire les données de la colonne, elle retourne des données stockées dans les champs de descripteur.  
  
 Une application appelant les fonctions ODBC pas concerner les lui-même avec des descripteurs. Aucune opération de base de données ne requiert que l’application accéder directement aux descripteurs. Toutefois, pour certaines applications, l’accès direct aux descripteurs simplifie de nombreuses opérations. Par exemple, indiquer à l’accès aux descripteurs de permet de lier de nouveau les données de colonne, qui peuvent être plus efficaces que l’appel **SQLBindCol** à nouveau.  
  
> [!NOTE]  
>  La représentation physique du descripteur n’est pas définie. Applications obtenir un accès direct à un descripteur uniquement par la manipulation de ses champs en appelant les fonctions ODBC avec le handle du descripteur.  
  
 Cette section contient les rubriques suivantes.  
  
-   [Types de descripteurs](../../../odbc/reference/develop-app/types-of-descriptors.md)  
  
-   [Champs de descripteur](../../../odbc/reference/develop-app/descriptor-fields.md)  
  
-   [Allocation et libération de descripteurs](../../../odbc/reference/develop-app/allocating-and-freeing-descriptors.md)  
  
-   [Obtention et définition des champs de descripteur](../../../odbc/reference/develop-app/getting-and-setting-descriptor-fields.md)

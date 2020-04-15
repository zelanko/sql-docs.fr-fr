---
title: Descripteurs - France Microsoft Docs
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: ca8299daae744fb9398ed6ffc99c838ce8edff48
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81305900"
---
# <a name="descriptors"></a>Descripteurs
Une poignée descripteur se réfère à une structure de données qui contient des informations sur les colonnes ou les paramètres dynamiques.  
  
 Fonctions ODBC fonctions qui fonctionnent sur les données de colonne et de paramètres implicitement définir et récupérer les champs descripteur. Par exemple, lorsque **SQLBindCol** est appelé à lier les données de colonne, il définit des champs descripteur qui décrivent complètement la liaison. Lorsque **SQLColAttribute** est appelé pour décrire les données de colonne, il renvoie les données stockées dans les champs descripteur.  
  
 Une application appelant les fonctions ODBC n’a pas besoin de se préoccuper des descripteurs. Aucune opération de base de données n’exige que l’application ait un accès direct aux descripteurs. Cependant, pour certaines applications, l’accès direct aux descripteurs rationalise de nombreuses opérations. Par exemple, l’accès direct aux descripteurs fournit un moyen de rebind données de colonne, qui peuvent être plus efficaces que d’appeler **SQLBindCol** à nouveau.  
  
> [!NOTE]  
>  La représentation physique du descripteur n’est pas définie. Les applications n’ont un accès direct à un descripteur qu’en manipulant ses champs en appelant les fonctions ODBC avec la poignée descripteur.  
  
 Cette section contient les rubriques suivantes :  
  
-   [Types de descripteurs](../../../odbc/reference/develop-app/types-of-descriptors.md)  
  
-   [Champs de descripteur](../../../odbc/reference/develop-app/descriptor-fields.md)  
  
-   [Allocation et libération de descripteurs](../../../odbc/reference/develop-app/allocating-and-freeing-descriptors.md)  
  
-   [Obtention et définition des champs de descripteur](../../../odbc/reference/develop-app/getting-and-setting-descriptor-fields.md)

---
title: Configuration du curseur | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- scrollable cursors [ODBC]
- cursors [ODBC], scrollable
- cursors [ODBC], creating
ms.assetid: b80afb0e-ef2f-408f-86f5-a392edd99a56
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 805d8076c853513d86f9a3a92d9342d1224226c9
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/27/2020
ms.locfileid: "81299799"
---
# <a name="setting-up-the-cursor"></a>Configuration du curseur
L’application peut spécifier le type de curseur avant d’exécuter une instruction qui crée un jeu de résultats. Pour ce faire, il utilise l’attribut d’instruction SQL_ATTR_CURSOR_TYPE. Si l’application ne spécifie pas explicitement un type, un curseur avant uniquement sera utilisé. Pour obtenir un curseur mixte, une application spécifie un curseur piloté par jeu de clés, mais déclare une taille de jeu de clés inférieure à la taille du jeu de résultats.  
  
 Pour les curseurs de jeu de clés et les curseurs mixtes, l’application peut également spécifier la taille du jeu de clés. Pour ce faire, il utilise l’attribut d’instruction SQL_ATTR_KEYSET_SIZE. Si la taille du keyset est définie sur 0, ce qui correspond à la valeur par défaut, la taille du jeu de clés est définie sur la taille du jeu de résultats et un curseur piloté par jeu de clés est utilisé. La taille du jeu de clés peut être modifiée après l’ouverture du curseur.  
  
 L’application peut également définir la taille de l’ensemble de lignes ; Pour plus d’informations, consultez [utilisation de curseurs de bloc](../../../odbc/reference/develop-app/using-block-cursors.md), plus haut dans cette section.

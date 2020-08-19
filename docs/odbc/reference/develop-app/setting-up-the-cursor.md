---
description: Configuration du curseur
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
ms.openlocfilehash: 307245dc403167f5bd857005f084ed22498d3ee8
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/17/2020
ms.locfileid: "88424581"
---
# <a name="setting-up-the-cursor"></a>Configuration du curseur
L’application peut spécifier le type de curseur avant d’exécuter une instruction qui crée un jeu de résultats. Pour ce faire, il utilise l’attribut d’instruction SQL_ATTR_CURSOR_TYPE. Si l’application ne spécifie pas explicitement un type, un curseur avant uniquement sera utilisé. Pour obtenir un curseur mixte, une application spécifie un curseur piloté par jeu de clés, mais déclare une taille de jeu de clés inférieure à la taille du jeu de résultats.  
  
 Pour les curseurs de jeu de clés et les curseurs mixtes, l’application peut également spécifier la taille du jeu de clés. Pour ce faire, il utilise l’attribut d’instruction SQL_ATTR_KEYSET_SIZE. Si la taille du keyset est définie sur 0, ce qui correspond à la valeur par défaut, la taille du jeu de clés est définie sur la taille du jeu de résultats et un curseur piloté par jeu de clés est utilisé. La taille du jeu de clés peut être modifiée après l’ouverture du curseur.  
  
 L’application peut également définir la taille de l’ensemble de lignes ; Pour plus d’informations, consultez [utilisation de curseurs de bloc](../../../odbc/reference/develop-app/using-block-cursors.md), plus haut dans cette section.

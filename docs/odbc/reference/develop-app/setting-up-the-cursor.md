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
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 59ade343f282933e05619996b119bc08e2dfb2ab
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62445911"
---
# <a name="setting-up-the-cursor"></a>Configuration du curseur
L’application peut spécifier le type de curseur avant que l’exécution d’une instruction qui crée un résultat défini. Il le fait avec l’attribut d’instruction SQL_ATTR_CURSOR_TYPE. Si l’application ne spécifie pas explicitement un type, un curseur avant uniquement est utilisé. Pour obtenir un curseur mixte, une application spécifie un curseur keyset mais déclare une curseur de taille inférieure à la taille du jeu de résultats.  
  
 Pour les curseurs pilotés par jeu de clés et mixtes, l’application peut également spécifier la taille du jeu de clés. Il le fait avec l’attribut d’instruction SQL_ATTR_KEYSET_SIZE. Si la taille de jeu de clés est définie sur 0, ce qui est la valeur par défaut, la taille de jeu de clés est définie sur la taille du jeu de résultats et un curseur keyset est utilisé. La taille de jeu de clés peut être modifiée une fois que le curseur a été ouvert.  
  
 L’application peut également définir la taille de l’ensemble de lignes ; Pour plus d’informations, consultez [à l’aide des curseurs de bloc](../../../odbc/reference/develop-app/using-block-cursors.md), plus haut dans cette section.

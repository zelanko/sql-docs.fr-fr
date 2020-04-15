---
title: Mise en place du curseur Microsoft Docs
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
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81299799"
---
# <a name="setting-up-the-cursor"></a>Configuration du curseur
L’application peut spécifier le type de curseur avant d’exécuter une déclaration qui crée un ensemble de résultats. Il le fait avec l’attribut SQL_ATTR_CURSOR_TYPE déclaration. Si l’application ne spécifie pas explicitement un type, un curseur avant-seulement sera utilisé. Pour obtenir un curseur mixte, une application spécifie un curseur à clé, mais déclare une taille de jeu de clés inférieure à la taille de l’ensemble de résultats.  
  
 Pour les curseurs mixtes et à jeu de clés, l’application peut également spécifier la taille du jeu de clés. Il le fait avec l’attribut SQL_ATTR_KEYSET_SIZE déclaration. Si la taille du jeu de clés est réglée à 0, ce qui est la valeur par défaut, la taille du jeu de clés est réglée à la taille de l’ensemble de résultats et un curseur piloté par un jeu de clés est utilisé. La taille du jeu de clés peut être modifiée après l’ouverture du curseur.  
  
 L’application peut également définir la taille de l’acart; pour plus d’informations, voir [Using Block Cursors](../../../odbc/reference/develop-app/using-block-cursors.md), plus tôt dans cette section.

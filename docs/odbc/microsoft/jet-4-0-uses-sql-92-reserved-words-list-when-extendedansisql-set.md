---
title: Jet 4.0 utilise SQL-92 Liste de mots réservés lorsqu’il est ExtendedAnsiSQL_Set Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- extendedANSISQL [ODBC], reserved words
ms.assetid: 7645187e-7777-4c07-9686-0a80d5c5834d
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 6988e0da1ecb881e0f6e88e35b66f1a6284f9b7a
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81299959"
---
# <a name="jet-40-uses-sql-92-reserved-words-list-when-extendedansisql_set"></a>Jet 4.0 utilise la liste de mots de réservés de SQL-92 avec ExtendedAnsiSQL_Set
Lorsque le drapeau ExtendedAnsiSQL est allumé, Jet 4.0 utilise la liste de mots réservés SQL-92. Essayer d’utiliser un mot réservé SQL-92 comme nom d’objet non cité se traduira par une erreur de syntaxe. Lorsque le drapeau ExtendedAnsiSQL est éteint, les nouveaux mots réservés peuvent être utilisés comme noms d’objets comme avant.

---
title: Jet 4,0 utilise la liste de mots réservés SQL-92 quand ExtendedAnsiSQL_Set | Microsoft Docs
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
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/27/2020
ms.locfileid: "81299959"
---
# <a name="jet-40-uses-sql-92-reserved-words-list-when-extendedansisql_set"></a>Jet 4.0 utilise la liste de mots de réservés de SQL-92 avec ExtendedAnsiSQL_Set
Lorsque l’indicateur ExtendedAnsiSQL est activé, Jet 4,0 utilise la liste de mots réservés SQL-92. Si vous tentez d’utiliser un mot réservé SQL-92 comme nom d’objet sans guillemets, une erreur de syntaxe se produit. Lorsque l’indicateur ExtendedAnsiSQL est désactivé, les nouveaux mots réservés peuvent être utilisés comme noms d’objet comme avant.

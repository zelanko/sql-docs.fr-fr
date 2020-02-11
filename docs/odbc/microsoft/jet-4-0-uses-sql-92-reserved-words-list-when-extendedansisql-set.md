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
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 93d23216db950ed861449061f3e35e5e88a637fb
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "68058796"
---
# <a name="jet-40-uses-sql-92-reserved-words-list-when-extendedansisql_set"></a>Jet 4.0 utilise la liste de mots de réservés de SQL-92 avec ExtendedAnsiSQL_Set
Lorsque l’indicateur ExtendedAnsiSQL est activé, Jet 4,0 utilise la liste de mots réservés SQL-92. Si vous tentez d’utiliser un mot réservé SQL-92 comme nom d’objet sans guillemets, une erreur de syntaxe se produit. Lorsque l’indicateur ExtendedAnsiSQL est désactivé, les nouveaux mots réservés peuvent être utilisés comme noms d’objet comme avant.

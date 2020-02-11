---
title: Limitations des mots réservés | Microsoft Docs
ms.custom: ''
ms.date: 05/01/2018
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- ODBC desktop database drivers [ODBC]
- desktop database drivers [ODBC]
ms.assetid: ed42f083-c9e8-4ee4-9d64-d879bf955c78
author: MightyPen
ms.author: genemi
ms.openlocfilehash: c884d8594c3c4511bed0e24f9b3dd43092176b4e
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "67988027"
---
# <a name="reserved-keyword-limitations"></a>Limitations des mots clés réservés

Évitez d’utiliser des mots clés réservés ODBC comme identificateurs dans vos tables SQL ou objets connexes. Si un cas impair se produit lorsque vous devez utiliser un mot clé réservé comme identificateur, vous devez entourer l’identificateur d’une paire de *battements* ('). Un autre nom *pour la* sauvegarde est un *guillemet*.

La limitation du mot clé réservé s’applique également à toute forme abrégée des mots clés réservés.

Une liste des mots clés réservés ODBC est disponible à l’adresse suivante :

- [Mots clés réservés ODBC](https://docs.microsoft.com/sql/odbc/reference/appendixes/reserved-keywords).

- Dans le *Guide de référence du programmeur ODBC*, consultez l' [annexe C : grammaire SQL](https://docs.microsoft.com/sql/odbc/reference/appendixes/appendix-c-sql-grammar).


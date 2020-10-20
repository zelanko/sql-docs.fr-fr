---
description: Limitations des mots clés réservés
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 15033816b953df764126853ada353452f00650d6
ms.sourcegitcommit: cfa04a73b26312bf18d8f6296891679166e2754d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/19/2020
ms.locfileid: "92196173"
---
# <a name="reserved-keyword-limitations"></a>Limitations des mots clés réservés

Évitez d’utiliser des mots clés réservés ODBC comme identificateurs dans vos tables SQL ou objets connexes. Si un cas impair se produit lorsque vous devez utiliser un mot clé réservé comme identificateur, vous devez entourer l’identificateur d’une paire de *battements* ('). Un autre nom *pour la* sauvegarde est un *guillemet*.

La limitation du mot clé réservé s’applique également à toute forme abrégée des mots clés réservés.

Une liste des mots clés réservés ODBC est disponible à l’adresse suivante :

- [Mots clés réservés ODBC](../reference/appendixes/reserved-keywords.md).

- Dans le *Guide de référence du programmeur ODBC*, consultez l' [annexe C : grammaire SQL](../reference/appendixes/appendix-c-sql-grammar.md).
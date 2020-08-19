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
ms.openlocfilehash: 07917cbe056b38be42e4697fcef52935bae3efe3
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/17/2020
ms.locfileid: "88449291"
---
# <a name="reserved-keyword-limitations"></a>Limitations des mots clés réservés

Évitez d’utiliser des mots clés réservés ODBC comme identificateurs dans vos tables SQL ou objets connexes. Si un cas impair se produit lorsque vous devez utiliser un mot clé réservé comme identificateur, vous devez entourer l’identificateur d’une paire de *battements* ('). Un autre nom *pour la* sauvegarde est un *guillemet*.

La limitation du mot clé réservé s’applique également à toute forme abrégée des mots clés réservés.

Une liste des mots clés réservés ODBC est disponible à l’adresse suivante :

- [Mots clés réservés ODBC](https://docs.microsoft.com/sql/odbc/reference/appendixes/reserved-keywords).

- Dans le *Guide de référence du programmeur ODBC*, consultez l' [annexe C : grammaire SQL](https://docs.microsoft.com/sql/odbc/reference/appendixes/appendix-c-sql-grammar).


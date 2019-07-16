---
title: CREATE INDEX, instruction-Limitations | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- CREATE INDEX statement limitations [ODBC]
- ODBC SQL grammar, CREATE INDEX statement limitations
ms.assetid: 832dcda1-e452-48e6-8adb-7fb33c4fb4ff
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 0ddb695d996cdd40b7fde4087799e5c1ec84224c
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "68081933"
---
# <a name="create-index-statement-limitations"></a>CREATE INDEX, instruction - limitations
L’instruction CREATE INDEX n’est pas pris en charge pour les pilotes Microsoft Excel ou texte.  
  
 Un index peut être défini sur un maximum de 10 colonnes. Si plus de 10 colonnes sont incluses dans une instruction CREATE INDEX, l’index n’est pas reconnue et la table est traitée comme si aucun index ont été créés.  
  
 Le pilote dBASE ne peut pas créer un index sur une colonne logique.  
  
 Lorsque le pilote dBASE est utilisé, les temps de réponse sur les fichiers volumineux peuvent être améliorées en créant un index .mdx (ou .ndx) sur la colonne (champ) spécifié dans les clauses WHERE d’une instruction SELECT. Index .mdx existants seront automatiquement appliquées pour =, >, \<, > =, = < et entre les opérateurs dans une clause WHERE et les prédicats LIKE, ainsi que dans les prédicats de jointure.  
  
 Lorsque le pilote dBASE est utilisé, l’index créé par une instruction CREATE UNIQUE INDEX n’est pas réellement non unique, et les valeurs en double peuvent être insérées dans la colonne indexée. Qu’un seul enregistrement à partir d’un jeu avec des valeurs de clés identiques peut être ajouté à l’index.  
  
 Lorsque le pilote Paradox est utilisé, un index unique doit être défini sur un sous-ensemble contigu de colonnes dans une table, y compris la première colonne. Une table ne peut pas être mis à jour par le pilote Paradox si un index unique n’est pas défini sur la table, ou si le pilote Paradox est utilisé sans l’implémentation du moteur de base de données Borland.

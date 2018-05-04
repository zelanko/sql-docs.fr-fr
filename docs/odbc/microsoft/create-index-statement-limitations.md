---
title: CRÉER INDEX instruction Limitations | Documents Microsoft
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: odbc
ms.reviewer: ''
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- CREATE INDEX statement limitations [ODBC]
- ODBC SQL grammar, CREATE INDEX statement limitations
ms.assetid: 832dcda1-e452-48e6-8adb-7fb33c4fb4ff
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: d473a0fce55688dfa00fd916c5eab15bd4ad44e2
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
---
# <a name="create-index-statement-limitations"></a>CRÉER INDEX instruction Limitations
L’instruction CREATE INDEX n’est pas prise en charge pour les pilotes Microsoft Excel ou texte.  
  
 Un index peut être défini sur un maximum de 10 colonnes. Si plus de 10 colonnes sont inclus dans une instruction CREATE INDEX, l’index n’est pas reconnue et la table est traitée comme si aucun index ont été créés.  
  
 Le pilote dBASE ne peut pas créer un index sur une colonne logique.  
  
 Lorsque le pilote dBASE est utilisé, le temps de réponse sur des fichiers volumineux peuvent être amélioré en créant un index .mdx (ou .ndx) sur la colonne (champ) spécifié dans les clauses WHERE d’une instruction SELECT. Index .mdx existants sont automatiquement appliquées pour =, >, \<, > =, = < et entre les opérateurs dans une clause WHERE et les prédicats LIKE, ainsi que dans les prédicats de jointure.  
  
 Lorsque le pilote dBASE est utilisé, l’index créé par une instruction CREATE UNIQUE INDEX n’est pas réellement non unique, et des valeurs en double peuvent être insérées dans la colonne indexée. Qu’un seul enregistrement d’un ensemble de valeurs clés identiques peut être ajouté à l’index.  
  
 Lorsque le pilote Paradox est utilisé, un index unique doit être défini sur un sous-ensemble contigu de colonnes dans une table, y compris la première colonne. Une table ne peut pas être mis à jour par le pilote Paradox si un index unique n’est pas défini sur la table ou le pilote Paradox est utilisée sans l’implémentation du moteur de base de données Borland.

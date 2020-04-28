---
title: Limitations de l’instruction CREATe INDEX | Microsoft Docs
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 053287d5087b377429221c31dd4e6b20f24248e5
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/27/2020
ms.locfileid: "81280880"
---
# <a name="create-index-statement-limitations"></a>CREATE INDEX, instruction - limitations
L’instruction CREATe INDEX n’est pas prise en charge pour Microsoft Excel ou les pilotes texte.  
  
 Un index peut être défini sur un maximum de 10 colonnes. Si plus de 10 colonnes sont incluses dans une instruction CREATe INDEX, l’index n’est pas reconnu et la table est traitée comme si aucun index n’avait été créé.  
  
 Le pilote dBASE ne peut pas créer d’index sur une colonne logique.  
  
 Lorsque le pilote dBASE est utilisé, vous pouvez améliorer le temps de réponse des fichiers volumineux en générant un index. MDX (ou. ndx) sur la colonne (champ) spécifiée dans les clauses WHERE d’une instruction SELECT. Les index. MDX existants seront automatiquement appliqués pour les opérateurs =, > \<,, >=, =< et between dans une clause WHERE, ainsi que pour les prédicats LIKE et dans les prédicats de jointure.  
  
 Lorsque le pilote dBASE est utilisé, l’index créé par une instruction CREATe UNIQUE INDEX est en fait non unique et des valeurs dupliquées peuvent être insérées dans la colonne indexée. Un seul enregistrement d’un ensemble avec des valeurs de clé identiques peut être ajouté à l’index.  
  
 Lorsque le pilote Paradox est utilisé, un index unique doit être défini sur un sous-ensemble contigu des colonnes d’une table, y compris la première colonne. Une table ne peut pas être mise à jour par le pilote Paradox si un index unique n’est pas défini sur la table ou lorsque le pilote Paradox est utilisé sans l’implémentation du Moteur de base de données Borland.

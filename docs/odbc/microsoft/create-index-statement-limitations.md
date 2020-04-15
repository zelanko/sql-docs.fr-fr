---
title: Limites de relevés INDEX CREATE (fr) Microsoft Docs
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
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81280880"
---
# <a name="create-index-statement-limitations"></a>CREATE INDEX, instruction - limitations
La déclaration CREATE INDEX n’est pas prise en charge pour les pilotes Microsoft Excel ou Text.  
  
 Un index peut être défini sur un maximum de 10 colonnes. Si plus de 10 colonnes sont incluses dans un relevé CREATE INDEX, l’index ne sera pas reconnu et le tableau sera traité comme si aucun index n’avait été créé.  
  
 Le pilote dBASE ne peut pas créer un index sur une colonne LOGICAL.  
  
 Lorsque le pilote dBASE est utilisé, le temps de réponse sur les fichiers volumineux peut être amélioré en construisant un index .mdx (ou .ndx) sur la colonne (champ) spécifié dans les clauses WHERE d’une déclaration SELECT. Les indices .mdx existants seront automatiquement appliqués \<pour les indices .mdx existants, >, >,<, et les opérateurs BETWEEN dans une clause WHERE, et LIKE se prédice, ainsi que dans les prédicats de jointure.  
  
 Lorsque le pilote dBASE est utilisé, l’index créé par une instruction INDEX UNIQUE CREATE est en fait non unique, et les valeurs en double peuvent être insérées dans la colonne indexée. Un seul enregistrement d’un ensemble avec des valeurs clés identiques peut être ajouté à l’indice.  
  
 Lorsque le pilote Paradox est utilisé, un index unique doit être défini sur un sous-ensemble contigu des colonnes dans un tableau, y compris la première colonne. Un tableau ne peut pas être mis à jour par le pilote Paradox si un index unique n’est pas défini sur la table ou lorsque le pilote Paradox est utilisé sans la mise en œuvre du moteur de base de données Borland.

---
title: Limitations de déclaration DE SUPPRESSION (en anglais) Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- DELETE statement limitations [ODBC]
- ODBC SQL grammar, DELETE statement limitations
ms.assetid: 084761fe-e65b-4f38-ba4f-69884b2a7700
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 365b54ab8c0678253e184b397f1f71e39aed3b9b
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81303530"
---
# <a name="delete-statement-limitations"></a>DELETE, instruction - limitations
La déclaration DELETE n’est pas prise en charge pour le pilote Microsoft Excel ou Text. Notez que la déclaration INSERT est prise en charge pour le pilote de texte.  
  
 Le pilote dBASE ne prend pas en charge l’emballage d’une table pour supprimer les valeurs « supprimées ».  
  
 Pour que le pilote Paradox supprime une ligne d’une table, la table doit avoir un index unique (clé primaire paradoxal).

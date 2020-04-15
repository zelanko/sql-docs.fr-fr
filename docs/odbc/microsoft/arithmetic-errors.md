---
title: Erreurs arithmétiques (fr) Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- arithmetic errors [ODBC]
- desktop database drivers [ODBC], arithmetic errors
ms.assetid: 1c47bfac-7455-4487-b673-6b47d2a2d756
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: ab1b472540d1978a6e7a06d94da7542cc641e999
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81299899"
---
# <a name="arithmetic-errors"></a>Erreurs arithmétiques
Le conducteur de l’ODBC évalue la clause WHERE dans une déclaration SELECT au fur et à mesure qu’elle récupère chaque rangée. Si une ligne contient une valeur qui provoque une erreur arithmétique, comme le débordement par division par zéro ou numérique, le pilote renvoie toutes les lignes, mais renvoie des erreurs pour les colonnes avec des erreurs arithmétiques. Lors de l’insertion ou de la mise à jour, cependant, le pilote ODBC cesse d’insérer ou de mettre à jour des données lorsque la première erreur arithmétique est rencontrée.

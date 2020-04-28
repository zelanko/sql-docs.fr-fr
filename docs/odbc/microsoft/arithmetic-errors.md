---
title: Erreurs arithmétiques | Microsoft Docs
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
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/27/2020
ms.locfileid: "81299899"
---
# <a name="arithmetic-errors"></a>Erreurs arithmétiques
Le pilote ODBC évalue la clause WHERE dans une instruction SELECT lors de l’extraction de chaque ligne. Si une ligne contient une valeur qui provoque une erreur arithmétique, telle qu’une division par zéro ou un dépassement de capacité numérique, le pilote retourne toutes les lignes, mais retourne des erreurs pour les colonnes avec des erreurs arithmétiques. Toutefois, lors de l’insertion ou de la mise à jour, le pilote ODBC arrête d’insérer ou de mettre à jour des données lorsque la première erreur arithmétique se produit.

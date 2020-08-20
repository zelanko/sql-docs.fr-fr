---
description: Erreurs arithmétiques
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
ms.openlocfilehash: 3e2fa142b43f1e96693390f777c90ea6f10705f6
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/17/2020
ms.locfileid: "88500402"
---
# <a name="arithmetic-errors"></a>Erreurs arithmétiques
Le pilote ODBC évalue la clause WHERE dans une instruction SELECT lors de l’extraction de chaque ligne. Si une ligne contient une valeur qui provoque une erreur arithmétique, telle qu’une division par zéro ou un dépassement de capacité numérique, le pilote retourne toutes les lignes, mais retourne des erreurs pour les colonnes avec des erreurs arithmétiques. Toutefois, lors de l’insertion ou de la mise à jour, le pilote ODBC arrête d’insérer ou de mettre à jour des données lorsque la première erreur arithmétique se produit.

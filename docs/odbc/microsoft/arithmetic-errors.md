---
title: Les erreurs arithmétiques | Microsoft Docs
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
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: c0d957d6091dc5fa29ee8a0b707c0e7fe7dfc7c8
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "63302042"
---
# <a name="arithmetic-errors"></a>Erreurs arithmétiques
Le pilote ODBC évalue la clause WHERE dans une instruction SELECT comme il lit chaque ligne. Si une ligne contient une valeur qui provoque une erreur arithmétique, telle que de dépassement de capacité numérique ou de division par zéro, le pilote retourne toutes les lignes, mais retourne des erreurs pour les colonnes avec des erreurs arithmétiques. Lorsque vous insérez ou la mise à jour, toutefois, le pilote ODBC s’arrête insertion ou la mise à jour des données lors de la première erreur arithmétique est rencontrée.

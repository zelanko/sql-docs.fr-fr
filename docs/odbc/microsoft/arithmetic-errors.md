---
title: Les erreurs arithmétiques | Documents Microsoft
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
- arithmetic errors [ODBC]
- desktop database drivers [ODBC], arithmetic errors
ms.assetid: 1c47bfac-7455-4487-b673-6b47d2a2d756
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: f63a3c7dd14301fc77a2b4ec1565744ac5015d93
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
---
# <a name="arithmetic-errors"></a>Erreurs arithmétiques
Le pilote ODBC évalue la clause WHERE dans une instruction SELECT, il extrait chaque ligne. Si une ligne contient une valeur qui entraîne une erreur arithmétique, telles que de dépassement de capacité numérique ou de division par zéro, le pilote retourne toutes les lignes, mais renvoie des erreurs pour les colonnes avec des erreurs arithmétiques. Lors de l’insertion ou de mise à jour, toutefois, le pilote ODBC arrête insertion ou mise à jour des données lors de la première erreur arithmétique est rencontrée.

---
title: Création et l’ouverture de Tables (pilote du fichier texte) | Documents Microsoft
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
- text file driver [ODBC], creating and opening tables
ms.assetid: e6a07dda-a665-4f5b-a8d6-9ff479700513
caps.latest.revision: 6
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 2693e65aa00628066915ee3dd4b00304eed3fa94
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
---
# <a name="creating-and-opening-tables-text-file-driver"></a>Création et l’ouverture de Tables (pilote du fichier texte)
Lorsque le pilote de texte est utilisé, une nouvelle table est créée en utilisant le format spécifié dans le fichier Odbcinst.ini. Si non spécifié, les tables sont créées dans le format CSVDELIMITED. Par défaut, par défaut des colonnes de type INTEGER à 11 caractères et les colonnes de type FLOAT par défaut 22 caractères. Les colonnes DATE utilisent le format AAAA-MM-JJ. Colonnes CHAR et LONGCHAR sont la largeur spécifiée dans l’instruction CREATE.

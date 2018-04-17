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
ms.topic: article
helpviewer_keywords:
- text file driver [ODBC], creating and opening tables
ms.assetid: e6a07dda-a665-4f5b-a8d6-9ff479700513
caps.latest.revision: 6
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 374a234f7c0f9eecc119e36d7dd4305a32745786
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
---
# <a name="creating-and-opening-tables-text-file-driver"></a>Création et l’ouverture de Tables (pilote du fichier texte)
Lorsque le pilote de texte est utilisé, une nouvelle table est créée en utilisant le format spécifié dans le fichier Odbcinst.ini. Si non spécifié, les tables sont créées dans le format CSVDELIMITED. Par défaut, par défaut des colonnes de type INTEGER à 11 caractères et les colonnes de type FLOAT par défaut 22 caractères. Les colonnes DATE utilisent le format AAAA-MM-JJ. Colonnes CHAR et LONGCHAR sont la largeur spécifiée dans l’instruction CREATE.

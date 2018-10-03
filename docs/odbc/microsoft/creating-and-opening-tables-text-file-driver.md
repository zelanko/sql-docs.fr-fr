---
title: Création et ouverture de Tables (pilote de fichier texte) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- text file driver [ODBC], creating and opening tables
ms.assetid: e6a07dda-a665-4f5b-a8d6-9ff479700513
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: ce901e6a8639c8a2caea6e55cbaa18fedb56f4a7
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47769097"
---
# <a name="creating-and-opening-tables-text-file-driver"></a>Création et ouverture de tables (pilote de fichier texte)
Lorsque le pilote de texte est utilisé, une nouvelle table est créée à l’aide du format spécifié dans le fichier Odbcinst.ini. Si non spécifié, les tables sont créées dans le format CSVDELIMITED. Par défaut, les colonnes d’entiers par défaut à 11 caractères et FLOAT colonnes par défaut 22 caractères. Colonnes DATE utilisent le format AAAA-MM-JJ. Colonnes CHAR et LONGCHAR sont la largeur spécifiée dans l’instruction CREATE.

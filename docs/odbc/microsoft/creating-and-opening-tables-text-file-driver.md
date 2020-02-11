---
title: Création et ouverture de tables (pilote de fichier texte) | Microsoft Docs
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
ms.openlocfilehash: b36c02d772682088a799cfca66f5bbf3e169a67f
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "68096542"
---
# <a name="creating-and-opening-tables-text-file-driver"></a>Création et ouverture de tables (pilote de fichier texte)
Lorsque le pilote de texte est utilisé, une nouvelle table est créée à l’aide du format spécifié dans le fichier Odbcinst. ini. S’il n’est pas spécifié, les tables sont créées au format CSVDELIMITED. Par défaut, les colonnes de type entier ont une valeur par défaut de 11 caractères et les colonnes de type FLOAT sur 22 caractères. Les colonnes de DATE utilisent le format AAAA-MM-JJ. Les colonnes CHAR et LONGCHAR sont la largeur spécifiée dans l’instruction CREATe.

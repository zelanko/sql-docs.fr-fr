---
description: Création et ouverture de tables (pilote de fichier texte)
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: c64f74270e8c2bbf4645f72406113e88948d0da9
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/17/2020
ms.locfileid: "88340965"
---
# <a name="creating-and-opening-tables-text-file-driver"></a>Création et ouverture de tables (pilote de fichier texte)
Lorsque le pilote de texte est utilisé, une nouvelle table est créée à l’aide du format spécifié dans Odbcinst.ini. S’il n’est pas spécifié, les tables sont créées au format CSVDELIMITED. Par défaut, les colonnes de type entier ont une valeur par défaut de 11 caractères et les colonnes de type FLOAT sur 22 caractères. Les colonnes de DATE utilisent le format AAAA-MM-JJ. Les colonnes CHAR et LONGCHAR sont la largeur spécifiée dans l’instruction CREATe.

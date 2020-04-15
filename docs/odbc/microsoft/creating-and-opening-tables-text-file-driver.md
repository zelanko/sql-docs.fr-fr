---
title: Tables de création et d’ouverture (Text File Driver) Microsoft Docs
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
ms.openlocfilehash: ae13312299f131d1957557db28bbe4db0bf7b4c7
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81280919"
---
# <a name="creating-and-opening-tables-text-file-driver"></a>Création et ouverture de tables (pilote de fichier texte)
Lorsque le pilote de texte est utilisé, une nouvelle table est créée en utilisant le format spécifié dans Odbcinst.ini. S’ils ne sont pas spécifiés, les tableaux sont créés en format CSVDELIMITED. Par défaut, les colonnes INTEGER par défaut à 11 caractères et colonnes FLOAT par défaut à 22 caractères. Les colonnes DATE utilisent le format YYYY-MM-DD. Les colonnes CHAR et LONGCHAR sont la largeur spécifiée dans l’instruction CREATE.

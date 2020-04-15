---
title: Source de données par défaut (fr) Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- data sources [ODBC], connection functions
- connecting to data source [ODBC], default data source
- functions [ODBC], data source or driver connections
- data sources [ODBC], default
- default data source [ODBC]
- connecting to data source [ODBC], functions
- connecting to driver [ODBC], default data source
- connecting to driver [ODBC], functions
- connection functions [ODBC]
- ODBC drivers [ODBC], connection functions
ms.assetid: dd473cc6-f051-4aa0-ab14-3dd1b37fe99e
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 978362b7dfe92d1333f83be684f6326cf25dd69b
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81305990"
---
# <a name="default-data-source"></a>Source de données par défaut
Le conducteur peut sélectionner une source de données, appelée source de données par défaut, dans certains cas où l’application ne spécifie pas explicitement :  
  
-   Dans un appel à **SQLConnect** où l’argument *ServerName* est une chaîne de zéro longueur, un pointeur nul, ou DEFAULT.  
  
-   Dans un appel à **SQLDriverConnect** où *InConnectionString* spécifie **DSN**-DEFAULT ou spécifie avec le mot clé **DSN** une source de données qui n’est pas contenue dans les informations du système.  
  
 Il est défini par le conducteur comment la source de données par défaut est spécifiée. Cela peut impliquer une action administrative et peut dépendre de l’utilisateur.

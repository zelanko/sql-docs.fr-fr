---
title: Source de données par défaut | Microsoft Docs
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
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 8fb016ac7597617b119834e20ffd9e12bd648dc0
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "68076852"
---
# <a name="default-data-source"></a>Source de données par défaut
Le pilote peut sélectionner une source de données, appelée source de données par défaut, dans certains cas où l’application n’en spécifie pas explicitement une :  
  
-   Dans un appel à **SQLConnect** où l’argument *ServerName* est une chaîne de longueur nulle, un pointeur null ou default.  
  
-   Dans un appel à **SQLDriverConnect** , où *InConnectionString* spécifie **DSN**= default ou spécifie avec le mot clé **DSN** une source de données qui n’est pas contenue dans les informations système.  
  
 C’est la façon dont la source de données par défaut est spécifiée par le pilote. Cela peut impliquer une action administrative et peut dépendre de l’utilisateur.

---
title: Valeur par défaut de la Source de données | Microsoft Docs
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
manager: craigg
ms.openlocfilehash: 909f9b3e7c8087add8eb66ca2f5c15253026304c
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63267652"
---
# <a name="default-data-source"></a>Source de données par défaut
Le pilote peut sélectionner une source de données, appelée la source de données par défaut, dans certains cas où l’application ne spécifie pas explicitement une :  
  
-   Dans un appel à **SQLConnect** où le *nom_serveur* argument est une chaîne de longueur nulle, un pointeur null ou par défaut.  
  
-   Dans un appel à **SQLDriverConnect** où *InConnectionString* soit spécifie **DSN**= valeur par défaut ou spécifie avec le **DSN** mot clé un source de données qui n’est pas contenue dans les informations système.  
  
 Elle est définie par le pilote comment la source de données par défaut est spécifiée. Cela peut impliquer l’action administrative et peut dépendre de l’utilisateur.

---
title: Limitations d’instruction DELETE | Documents Microsoft
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
- DELETE statement limitations [ODBC]
- ODBC SQL grammar, DELETE statement limitations
ms.assetid: 084761fe-e65b-4f38-ba4f-69884b2a7700
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 45386d8278e968b55fba5881dfe9b914bc23f454
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
---
# <a name="delete-statement-limitations"></a>SUPPRIMER les Limitations de l’instruction
L’instruction DELETE n’est pas prise en charge pour le pilote Microsoft Excel ou texte. Notez que l’instruction INSERT est pris en charge pour le pilote de texte.  
  
 Le pilote dBASE ne prend pas en charge la compression d’une table pour supprimer les valeurs de « supprimé ».  
  
 Pour le pilote Paradox supprimer une ligne d’une table, la table doit avoir un index unique (clé primaire).

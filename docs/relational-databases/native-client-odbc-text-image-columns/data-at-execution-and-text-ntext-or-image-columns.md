---
title: Data-at-Execution et colonnes Text, ntext ou Image | Documents Microsoft
ms.custom: 
ms.date: 03/06/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: 
ms.component: native-client-odbc-text-image-columns
ms.reviewer: 
ms.suite: sql
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- text columns [ODBC]
- SQL Server Native Client ODBC driver, image columns
- SQL Server Native Client ODBC driver, text columns
- data types [ODBC], image
- data types [ODBC], text
- columns [ODBC]
- ODBC data types, image columns
- ODBC data types, text columns
- data-at-execution
- ODBC data-at-execution
- image columns [ODBC]
ms.assetid: 67ffb1a6-f38d-4712-ba64-96bdd41ec2b2
caps.latest.revision: 
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: ec54f186ac60d970d5e3848d5abafd4d6cd636c5
ms.sourcegitcommit: 9e6a029456f4a8daddb396bc45d7874a43a47b45
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/25/2018
---
# <a name="data-at-execution-and-text-ntext-or-image-columns"></a>Données en cours d'exécution et colonnes text, ntext ou image
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

  Les données en cours d'exécution sont une fonctionnalité ODBC qui permet aux applications d'utiliser des quantités de données extrêmement importantes sur les colonnes dépendantes ou les paramètres. Lors de la récupération de très grande **texte**, **ntext**, ou **image** colonnes, une application peut-être pas simplement allouer une immense mémoire tampon, lier la colonne dans la mémoire tampon et extraire la ligne. Lors de la mise à jour très volumineux **texte**, **ntext**, ou **image** colonnes, l’application ne peut pas être en mesure d’allouer simplement une immense mémoire tampon, lier à un marqueur de paramètre dans une instruction SQL, puis exécutez l’instruction. Dans ce cas, l’application doit utiliser [SQLGetData](../../relational-databases/native-client-odbc-api/sqlgetdata.md) ou [SQLPutData](../../relational-databases/native-client-odbc-api/sqlputdata.md) avec ses options de data-at-execution.  
  
## <a name="see-also"></a>Voir aussi  
 [Gestion des colonnes texte et image](../../relational-databases/native-client-odbc-text-image-columns/managing-text-and-image-columns.md)  
  
  

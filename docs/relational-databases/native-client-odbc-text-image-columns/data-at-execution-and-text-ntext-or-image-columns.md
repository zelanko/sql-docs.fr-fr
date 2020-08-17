---
description: Données en cours d'exécution et colonnes text, ntext ou image
title: Données en cours d’exécution et Text, ntext, image
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
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
author: markingmyname
ms.author: maghan
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 9f0faef2097287e026023afe30c379a2f08f3d82
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/17/2020
ms.locfileid: "88381835"
---
# <a name="data-at-execution-and-text-ntext-or-image-columns"></a>Données en cours d'exécution et colonnes text, ntext ou image
[!INCLUDE[SQL Server Azure SQL Database Synapse Analytics PDW ](../../includes/applies-to-version/sql-asdb-asdbmi-asa-pdw.md)]

  Les données en cours d'exécution sont une fonctionnalité ODBC qui permet aux applications d'utiliser des quantités de données extrêmement importantes sur les colonnes dépendantes ou les paramètres. Lorsque vous récupérez des colonnes **Text**, **ntext**ou **image** très volumineuses, il est possible qu’une application ne soit pas en mesure d’allouer une mémoire tampon volumineuse, de lier la colonne dans la mémoire tampon et d’extraire la ligne. Lors de la mise à jour de colonnes **Text**, **ntext**ou **image** de très grande taille, l’application peut ne pas être en mesure d’allouer simplement une mémoire tampon volumineuse, de la lier à un marqueur de paramètre dans une instruction SQL, puis d’exécuter l’instruction. Dans ce cas, l’application doit utiliser [SQLGetData](../../relational-databases/native-client-odbc-api/sqlgetdata.md) ou [SQLPutData](../../relational-databases/native-client-odbc-api/sqlputdata.md) avec ses options de données en cours d’exécution.  
  
## <a name="see-also"></a>Voir aussi  
 [Gestion des colonnes texte et image](../../relational-databases/native-client-odbc-text-image-columns/managing-text-and-image-columns.md)  
  
  

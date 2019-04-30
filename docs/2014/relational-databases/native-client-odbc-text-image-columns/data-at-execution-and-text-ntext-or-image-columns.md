---
title: Data-at-Execution et colonnes Text, ntext ou Image | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
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
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 7e7c57cf6444e5833b6deee0dcae36d71b7a6430
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63195130"
---
# <a name="data-at-execution-and-text-ntext-or-image-columns"></a>Données en cours d'exécution et colonnes text, ntext ou image
  Les données en cours d'exécution sont une fonctionnalité ODBC qui permet aux applications d'utiliser des quantités de données extrêmement importantes sur les colonnes dépendantes ou les paramètres. Lors de la récupération de très grandes **texte**, **ntext**, ou **image** colonnes, une application ne peut pas pouvoir pour simplement allouer une immense mémoire tampon, lier la colonne dans la mémoire tampon et l’extraction la ligne. Lors de la mise à jour très volumineux **texte**, **ntext**, ou **image** colonnes, l’application ne peut pas être en mesure de simplement allouer une immense mémoire tampon, lier à un marqueur de paramètre dans SQL instruction, puis exécutez l’instruction. Dans ce cas, l’application doit utiliser [SQLGetData](../native-client-odbc-api/sqlgetdata.md) ou [SQLPutData](../native-client-odbc-api/sqlputdata.md) avec ses options data-at-execution.  
  
## <a name="see-also"></a>Voir aussi  
 [Gestion des colonnes texte et image](managing-text-and-image-columns.md)  
  
  

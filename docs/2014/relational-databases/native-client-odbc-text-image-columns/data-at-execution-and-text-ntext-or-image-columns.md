---
title: Données en cours d’exécution et colonnes text, ntext ou image | Microsoft Docs
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
author: rothja
ms.author: jroth
ms.openlocfilehash: 404fade34862fe4705ec440eef7f466a9073250b
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/18/2020
ms.locfileid: "85039300"
---
# <a name="data-at-execution-and-text-ntext-or-image-columns"></a>Données en cours d'exécution et colonnes text, ntext ou image
  Les données en cours d'exécution sont une fonctionnalité ODBC qui permet aux applications d'utiliser des quantités de données extrêmement importantes sur les colonnes dépendantes ou les paramètres. Lorsque vous récupérez des colonnes **Text**, **ntext**ou **image** très volumineuses, il est possible qu’une application ne soit pas en mesure d’allouer une mémoire tampon volumineuse, de lier la colonne dans la mémoire tampon et d’extraire la ligne. Lors de la mise à jour de colonnes **Text**, **ntext**ou **image** de très grande taille, l’application peut ne pas être en mesure d’allouer simplement une mémoire tampon volumineuse, de la lier à un marqueur de paramètre dans une instruction SQL, puis d’exécuter l’instruction. Dans ce cas, l’application doit utiliser [SQLGetData](../native-client-odbc-api/sqlgetdata.md) ou [SQLPutData](../native-client-odbc-api/sqlputdata.md) avec ses options de données en cours d’exécution.  
  
## <a name="see-also"></a>Voir aussi  
 [Gestion des colonnes texte et image](managing-text-and-image-columns.md)  
  
  

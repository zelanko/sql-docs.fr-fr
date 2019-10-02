---
title: Copie en bloc de données text et image | Microsoft Docs
ms.custom: ''
ms.date: 03/03/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- bulk copy [ODBC], text data
- SQL Server Native Client ODBC driver, bulk copy
- bulk copy [ODBC], image data
- ODBC, bulk copy operations
ms.assetid: 87155bfa-3a73-4158-9d4d-cb7435dac201
author: markingmyname
ms.author: maghan
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 5243c862e07ad8b4f5a0b3b33ea292cecc1cb0a9
ms.sourcegitcommit: 8732161f26a93de3aa1fb13495e8a6a71519c155
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2019
ms.locfileid: "71707900"
---
# <a name="bulk-copying-text-and-image-data"></a>Copie en bloc de données Text et Image
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

  Les valeurs **Text**, **ntext**et **image** volumineuses sont copiées en bloc à l’aide de la fonction [bcp_moretext](../../relational-databases/native-client-odbc-extensions-bulk-copy-functions/bcp-moretext.md) . Vous codez [bcp_bind](../../relational-databases/native-client-odbc-extensions-bulk-copy-functions/bcp-bind.md) pour la colonne **Text**, **ntext**ou **image** avec un pointeur *pData* défini sur null, indiquant que les données seront fournies avec **bcp_moretext**. Il est important de spécifier la longueur exacte des données fournies pour chaque colonne **Text**, **ntext**ou **image** dans chaque ligne copiée en bloc. Si la longueur des données d’une colonne est différente de la longueur de colonne spécifiée dans [bcp_bind](../../relational-databases/native-client-odbc-extensions-bulk-copy-functions/bcp-bind.md), utilisez [bcp_collen](../../relational-databases/native-client-odbc-extensions-bulk-copy-functions/bcp-collen.md) pour définir la longueur à la valeur appropriée. Un [bcp_sendrow](../../relational-databases/native-client-odbc-extensions-bulk-copy-functions/bcp-sendrow.md) envoie toutes les données non**textuelles**, non**ntext**et non-**image** . vous appelez ensuite **bcp_moretext** pour envoyer les données **Text**, **ntext**ou **image** dans des unités distinctes. Les fonctions de copie en bloc déterminent que toutes les données ont été envoyées pour la colonne **Text**, **ntext**ou **image** actuelle lorsque la somme des longueurs des données envoyées via **bcp_moretext** est égale à la longueur spécifiée dans la dernière **bcp_collen** ou **bcp_bind**.  
  
 **bcp_moretext** n’a aucun paramètre pour identifier une colonne. Lorsqu’il existe plusieurs colonnes **Text**, **ntext**ou **image** dans une ligne, **bcp_moretext** opère sur les colonnes **Text**, **ntext**ou **image** en commençant par la colonne ayant le nombre ordinal le plus petit et en procédant à la colonne avec le numéro ordinal le plus élevé. **bcp_moretext** passe d’une colonne à la suivante lorsque la somme des longueurs de données envoyées est égale à la longueur spécifiée dans le dernier **bcp_collen** ou **bcp_bind** pour la colonne actuelle.  
  
## <a name="see-also"></a>Voir aussi  
 [Exécution d’opérations &#40;de copie en bloc ODBC&#41;](../../relational-databases/native-client-odbc-bulk-copy-operations/performing-bulk-copy-operations-odbc.md)  
  
  

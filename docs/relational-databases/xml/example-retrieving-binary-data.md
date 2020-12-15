---
title: 'Exemple : Récupération de données binaires | Microsoft Docs'
description: Affichez un exemple de requête SQL qui extrait des données binaires à l’aide des options RAW et BINARY BASE64 avec la clause FOR XML.
ms.custom: ''
ms.date: 04/03/2020
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: xml
ms.topic: conceptual
helpviewer_keywords:
- RAW mode, retrieving binary data example
ms.assetid: 5cea5d49-58ac-403a-a933-c4fd91de400b
author: RothJa
ms.author: jroth
ms.openlocfilehash: fedec9e351b9c8910db0bee51c1e2c5dc8569655
ms.sourcegitcommit: 1a544cf4dd2720b124c3697d1e62ae7741db757c
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/14/2020
ms.locfileid: "97402977"
---
# <a name="example-retrieving-binary-data"></a>Exemple : Extraction de données binaires

[!INCLUDE [SQL Server Azure SQL Database](../../includes/applies-to-version/sql-asdb.md)]

La requête ci-dessous retourne la photo du produit stockée dans une colonne de type **varbinary(max)** . L'option `BINARY BASE64` est spécifiée dans la requête pour retourner les données binaires au format encodé en base64.

## <a name="example"></a>Exemple

```sql
USE AdventureWorks2012;
GO
SELECT ProductPhotoID, ThumbNailPhoto
FROM Production.ProductPhoto
WHERE ProductPhotoID=1
FOR XML RAW, BINARY BASE64 ;
GO
```

Voici le résultat attendu :

```console
<row ProductModelID="1" ThumbNailPhoto="base64 encoded binary data"/>
```

## <a name="see-also"></a>Voir aussi

[Utiliser le mode RAW avec FOR XML](../../relational-databases/xml/use-raw-mode-with-for-xml.md)

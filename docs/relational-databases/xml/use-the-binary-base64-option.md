---
title: Utiliser l’option BINARY BASE64 | Microsoft Docs
description: Découvrez comment utiliser l’option BINARY BASE64 dans une requête SQL pour retourner des données binaires au format d’encodage base64.
ms.custom: ''
ms.date: 04/03/2020
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: xml
ms.topic: conceptual
helpviewer_keywords:
- AUTO FOR XML mode, BINARY BASE64 option
ms.assetid: 86a7bb85-7f83-412a-b775-d2c379702fe9
author: RothJa
ms.author: jroth
ms.openlocfilehash: 03ada0a70977968914cd00c14c279921a0652a2c
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85738389"
---
# <a name="use-the-binary-base64-option"></a>Utiliser l'option BINARY BASE64

[!INCLUDE [SQL Server Azure SQL Database](../../includes/applies-to-version/sql-asdb.md)]

Si l'option BINARY BASE64 est spécifiée dans la requête, les données binaires sont renvoyées dans un format encodé en base 64.

Si l’option BINARY BASE64 n’est pas spécifiée dans la requête, par défaut, le mode AUTO prend en charge l’encodage URL des données binaires. Une référence à une URL relative vers la racine virtuelle de la base de données est retournée. Cette référence concerne la base de données où la requête a été exécutée. La référence retournée peut être utilisée pour accéder aux données binaires réelles lors les opérations ultérieures. Cet accès est obtenu à l’aide de la requête de dbobject ISAPI de SQLXML. La requête doit fournir suffisamment d’informations pour identifier l’image. Ces informations peuvent inclure les colonnes de la clé primaire.

## <a name="column-alias"></a>Alias de colonne

N’utilisez pas d’alias pour une colonne binaire quand vous interrogez une vue et que vous utilisez le mode FOR XML AUTO. Si vous utilisez un alias, l’alias est retourné dans l’encodage URL des données binaires. Dans les opérations suivantes, l’alias ne signifie rien. Dans les opérations suivantes, l’alias qui ne signifie rien et l’encodage URL ne peuvent pas être utilisés pour extraire l’image.

### <a name="cast-to-a-blob"></a>Cast en objet blob

Dans une requête SELECT, le cast d’une colonne en objet blob transforme la colonne en une entité temporaire. Étant temporaire, l’objet blob perd son nom de table et son nom de colonne associés. Ce cast fait que les requêtes exprimées en mode AUTO génèrent une erreur, car le système ne sait pas où placer cette valeur dans la hiérarchie XML.

Par exemple, considérons la table suivante avec sa seule ligne.

```sql
CREATE TABLE MyTable (Col1 int PRIMARY KEY, Col2 binary)
INSERT INTO MyTable VALUES (1, 0x7);
```

La requête suivante produit une erreur en raison du cast en objet blob :

```sql
SELECT Col1,
CAST(Col2 as image) as Col2
FROM MyTable
FOR XML AUTO;
```

La solution consiste à ajouter l'option BINARY BASE64 dans la clause FOR XML. Si vous supprimez le cast, la requête produit les bons résultats.

```sql
SELECT Col1,
CAST(Col2 as image) as Col2
FROM MyTable
FOR XML AUTO, BINARY BASE64;
```

Voici le bon résultat attendu :

```console
<MyTable Col1="1" Col2="Bw==" />
```

## <a name="see-also"></a>Voir aussi

[Utiliser le mode AUTO avec FOR XML](../../relational-databases/xml/use-auto-mode-with-for-xml.md)

---
title: Données binaires et à valeurs élevées SQL Server
description: Décrit comment utiliser les données à valeurs élevées dans SQL Server.
ms.date: 08/15/2019
ms.assetid: e00827b3-7511-4b2d-91d7-851ca86cc6b5
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.topic: conceptual
author: v-kaywon
ms.author: v-kaywon
ms.reviewer: rothja
ms.openlocfilehash: 0a38d90a810f9ca3ee376562eaabf6e713267b27
ms.sourcegitcommit: 9c993112842dfffe7176decd79a885dbb192a927
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 10/16/2019
ms.locfileid: "72452053"
---
# <a name="sql-server-binary-and-large-value-data"></a>Données binaires et à valeurs élevées SQL Server

![Download-DownArrow-Circled](../../../ssdt/media/download.png)[Télécharger ADO.NET](../../sql-connection-libraries.md#anchor-20-drivers-relational-access)

SQL Server fournit le spécificateur de `max`, qui étend la capacité de stockage des types de données `varchar`, `nvarchar`et `varbinary`. `varchar(max)`, `nvarchar(max)` et `varbinary(max)` sont désignés par le terme générique de types de données de valeur élevée. Les types de données de valeur élevée permettent de stocker jusqu’à 2^31-1 octets de données.  
  
SQL Server 2008 introduit l’attribut FILESTREAM, qui n’est pas un type de données, mais plutôt un attribut qui peut être défini sur une colonne, ce qui permet de stocker les données de grande valeur sur le système de fichiers plutôt que dans la base de données.  
  
## <a name="in-this-section"></a>Contenu de cette section  
[Modification de données à valeurs élevées (max) dans ADO.NET](modify-large-value-max-data.md)  
Décrit comment utiliser les types de données de valeur élevée.  
  
[Données FILESTREAM](filestream-data.md)  
Décrit comment utiliser des données de valeur élevée stockées dans SQL Server 2008 avec l’attribut FILESTREAM.  
  
## <a name="next-steps"></a>Étapes suivantes
- [Types de données SQL Server et ADO.NET](sql-server-data-types.md)
- [Opérations de données SQL Server dans ADO.NET](sql-server-data-operations.md)

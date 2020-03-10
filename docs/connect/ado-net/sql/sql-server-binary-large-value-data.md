---
title: Données binaires et à valeurs élevées SQL Server
description: Décrit comment utiliser les données à valeurs élevées dans SQL Server.
ms.date: 08/15/2019
ms.assetid: e00827b3-7511-4b2d-91d7-851ca86cc6b5
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.topic: conceptual
author: rothja
ms.author: jroth
ms.reviewer: v-kaywon
ms.openlocfilehash: 4ed8ccbadb27008fb15d9d117d55b5a4d332a8f6
ms.sourcegitcommit: 610e49c3e1fa97056611a85e31e06ab30fd866b1
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/07/2020
ms.locfileid: "78896626"
---
# <a name="sql-server-binary-and-large-value-data"></a>Données binaires et à valeurs élevées SQL Server

[!INCLUDE[Driver_ADONET_Download](../../../includes/driver_adonet_download.md)]

SQL Server fournit le spécificateur `max`, qui étend la capacité de stockage des types de données `varchar`, `nvarchar` et `varbinary`. `varchar(max)`, `nvarchar(max)` et `varbinary(max)` sont désignés par le terme générique de *types de données de valeur élevée*. Les types de données de valeur élevée permettent de stocker jusqu’à 2^31-1 octets de données.  
  
SQL Server 2008 introduit l’attribut FILESTREAM, qui n’est pas un type de données, mais plutôt un attribut qui peut être défini sur une colonne, et permet de stocker des données de grande valeur sur le système de fichiers plutôt que dans la base de données.  
  
## <a name="in-this-section"></a>Contenu de cette section  
[Modification de données à valeurs élevées (max) dans ADO.NET](modify-large-value-max-data.md)  
Décrit comment utiliser les types de données de valeur volumineux.  
  
[Données FILESTREAM](filestream-data.md)  
Décrit comment utiliser les données de valeur élevée stockées dans SQL Server 2008 avec l’attribut FILESTREAM.  
  
## <a name="next-steps"></a>Étapes suivantes
- [Types de données SQL Server et ADO.NET](sql-server-data-types.md)
- [Opérations de données SQL Server dans ADO.NET](sql-server-data-operations.md)

---
title: Extraction et modification de données
description: Dans .NET Framework, le Fournisseur de données Microsoft SqlClient pour SQL Server sert de pont entre une application et une source de données pour lire et mettre à jour des données.
ms.date: 11/13/2020
ms.assetid: 722e7f87-3691-46c6-87e8-7d159722d675
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.topic: conceptual
author: David-Engel
ms.author: v-daenge
ms.reviewer: v-chmalh
ms.openlocfilehash: cbe61aafd8dcd1681230c355187a65a231535e00
ms.sourcegitcommit: 192f6a99e19e66f0f817fdb1977f564b2aaa133b
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/25/2020
ms.locfileid: "96126389"
---
# <a name="retrieving-and-modifying-data-in-adonet"></a>Extraction et modification de données dans ADO.NET

[!INCLUDE[appliesto-netfx-netcore-netst-md](../../includes/appliesto-netfx-netcore-netst-md.md)]

[!INCLUDE[Driver_ADONET_Download](../../includes/driver_adonet_download.md)]

Une fonction principale de toute application de base de données consiste à se connecter à une source de données et extraire les données qu'elle contient. Le fournisseur de données SqlClient fait office de passerelle entre une application et une source de données, ce qui vous permet d'exécuter des commandes et d'extraire des données à l'aide d'un **DataReader** ou d'un **DataAdapter**. Une fonction clé de toute application de base de données est la capacité à mettre à jour les données stockées dans la base de données. Dans le Fournisseur de données Microsoft SqlClient pour SQL Server, la mise à jour de données implique l’utilisation des objets **DataAdapter** et <xref:System.Data.DataSet> et **Command** ; cela peut également impliquer l’utilisation de transactions.

## <a name="in-this-section"></a>Dans cette section

[Connexion à une source de données](connecting-to-data-source.md) décrit comment établir une connexion à une source de données et comment utiliser les événements de connexion.

[Chaîne de connexion](connection-strings.md) contient des rubriques qui décrivent divers aspects de l'utilisation de chaînes de connexion, y compris des mots clés de chaîne de connexion, des informations de sécurité, ainsi que de leur stockage et de leur extraction.

[Regroupement de connexions](connection-pooling.md) Décrit le regroupement de connexions pour le Fournisseur de données Microsoft SqlClient pour SQL Server.

## <a name="see-also"></a>Voir aussi

- [Mappages de types de données dans ADO.NET](data-type-mappings-ado-net.md)
- [SQL Server et ADO.NET](./sql/index.md)

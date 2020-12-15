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
ms.openlocfilehash: d6e4d6c298c632c446e1671b5d9adabaa19e0776
ms.sourcegitcommit: c127c0752e84cccd38a7e23ac74c0362a40f952e
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/07/2020
ms.locfileid: "96761487"
---
# <a name="retrieving-and-modifying-data-in-adonet"></a>Extraction et modification de données dans ADO.NET

[!INCLUDE[appliesto-netfx-netcore-netst-md](../../includes/appliesto-netfx-netcore-netst-md.md)]

[!INCLUDE[Driver_ADONET_Download](../../includes/driver_adonet_download.md)]

Une fonction principale de toute application de base de données consiste à se connecter à une source de données et extraire les données qu'elle contient. Le fournisseur de données SqlClient fait office de passerelle entre une application et une source de données, ce qui vous permet d'exécuter des commandes et d'extraire des données à l'aide d'un **DataReader** ou d'un **DataAdapter**. Une fonction clé de toute application de base de données est la capacité à mettre à jour les données stockées dans la base de données. Dans le Fournisseur de données Microsoft SqlClient pour SQL Server, la mise à jour de données implique l’utilisation des objets **DataAdapter** et <xref:System.Data.DataSet> et **Command** ; cela peut également impliquer l’utilisation de transactions.

## <a name="in-this-section"></a>Dans cette section

[Connexion à une source de données](connecting-to-data-source.md)  
Décrit comment établir une connexion à une source de données et comment travailler avec des événements de connexion.

[Chaînes de connexion](connection-strings.md)  
Contient des rubriques qui décrivent divers aspects de l'utilisation de chaînes de connexion, y compris des mots clés de chaîne de connexion, des informations de sécurité, ainsi que de leur stockage et leur extraction.

[Regroupement de connexions](connection-pooling.md)  
Décrit le regroupement de connexions pour le Fournisseur de données Microsoft SqlClient pour SQL Server.

[Commandes et paramètres](commands-parameters.md)  
Contient des rubriques qui décrivent comment créer des commandes et des générateurs de commande, configurer des paramètres et exécuter des commandes pour extraire et modifier des données.

[DataAdapters et DataReaders](dataadapters-datareaders.md)  
Contient des rubriques qui décrivent les objets DataReader et DataAdapter, les paramètres, la gestion des événements DataAdapter et l'exécution d'opérations par lots.

## <a name="see-also"></a>Voir aussi

- [Mappages des types de données dans ADO.NET](data-type-mappings-ado-net.md)
- [SQL Server et ADO.NET](./sql/index.md)
- [Microsoft ADO.NET pour SQL Server](microsoft-ado-net-sql-server.md)

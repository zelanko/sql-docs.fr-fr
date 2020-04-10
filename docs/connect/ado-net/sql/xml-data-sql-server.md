---
title: Données XML dans SQL Server
description: Décrit comment utiliser des données XML extraites de SQL Server.
ms.date: 08/15/2019
ms.assetid: 9849d319-f518-4e3d-a7cd-f8fdcaaa1d4d
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.topic: conceptual
author: David-Engel
ms.author: v-daenge
ms.reviewer: v-kaywon
ms.openlocfilehash: e2d181ce82cfa9d71f2902e3a50e50ed80f0c465
ms.sourcegitcommit: fe5c45a492e19a320a1a36b037704bf132dffd51
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/08/2020
ms.locfileid: "80918248"
---
# <a name="xml-data-in-sql-server"></a>Données XML dans SQL Server

[!INCLUDE[Driver_ADONET_Download](../../../includes/driver_adonet_download.md)]

SQL Server expose la fonctionnalité de SQLXML à l'intérieur de .NET. Les développeurs peuvent écrire des applications qui accèdent aux données XML à partir d’une instance SQL Server, importer les données dans l’environnement .NET, traitent les données puis renvoient les données mises à jour à SQL Server. Les données XML peuvent être utilisées de plusieurs manières dans SQL Server, notamment pour le stockage de données et comme valeurs de paramètre pour l’extraction de données. La classe **SqlXml** dans .NET fournit la prise en charge côté client pour travailler avec des données stockées dans une colonne XML dans SQL Server. Pour plus d’informations, Consultez « Classes gérées SQLXML » dans la Documentation en ligne de SQL Server.  
  
## <a name="in-this-section"></a>Contenu de cette section  
[Valeurs des colonnes XML SQL](sql-xml-column-values.md)  
Montre comment extraire et utiliser des données XML extraites de SQL Server.  
  
[Spécification de valeurs XML comme paramètres](specify-xml-values-parameters.md)  
Montre comment passer des données XML en tant que paramètre à une commande.  
  
## <a name="next-steps"></a>Étapes suivantes
- [SQL Server et ADO.NET](index.md)

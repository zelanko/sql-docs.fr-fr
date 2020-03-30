---
title: Données XML dans SQL Server
description: Décrit comment utiliser des données XML extraites de SQL Server.
ms.date: 08/15/2019
ms.assetid: 9849d319-f518-4e3d-a7cd-f8fdcaaa1d4d
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.topic: conceptual
author: rothja
ms.author: jroth
ms.reviewer: v-kaywon
ms.openlocfilehash: 039efb5e3e2826fd4c337d2dbdced29295f05fdb
ms.sourcegitcommit: ff82f3260ff79ed860a7a58f54ff7f0594851e6b
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/29/2020
ms.locfileid: "78895873"
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

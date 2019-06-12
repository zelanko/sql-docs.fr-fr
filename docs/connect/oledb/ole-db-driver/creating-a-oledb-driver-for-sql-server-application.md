---
title: Création d’une application de pilote OLE DB pour SQL Server | Microsoft Docs
description: Création d’une application de pilote OLE DB pour SQL Server
ms.custom: ''
ms.date: 06/14/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: connectivity
ms.topic: reference
helpviewer_keywords:
- OLE DB Driver for SQL Server, application creation
- applications [OLE DB Driver for SQL Server]
- OLE DB, creating applications
author: pmasl
ms.author: pelopes
manager: jroth
ms.openlocfilehash: c36ec6878f7ef981e72a64121c98c930e6481104
ms.sourcegitcommit: ad2e98972a0e739c0fd2038ef4a030265f0ee788
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 06/07/2019
ms.locfileid: "66769204"
---
# <a name="creating-an-ole-db-driver-for-sql-server-application"></a>Création d’une application de pilote OLE DB pour SQL Server
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

[!INCLUDE[Driver_OLEDB_Download](../../../includes/driver_oledb_download.md)]

  Création d’un pilote OLE DB pour l’application de SQL Server implique ces étapes :  
  
1.  Établissement d'une connexion à une source de données.  
  
2.  Exécution d'une commande.  
  
3.  Traitement des résultats.  
  
> [!NOTE]  
>  Lorsque c'est possible, utilisez l'authentification Windows. Si l'authentification Windows n'est pas disponible, invitez les utilisateurs à entrer leurs informations d'identification au moment de l'exécution. Évitez de stocker ces informations dans un fichier. Si vous devez rendre les informations d’identification persistantes, chiffrez-les avec [l’API de chiffrement Win32 cryptoAPI](https://go.microsoft.com/fwlink/?LinkId=9504).  
  
## <a name="in-this-section"></a>Dans cette section  
  
-   [Établissement d’une connexion à une source de données](../../oledb/ole-db-driver/establishing-a-connection-to-a-data-source.md)  
  
-   [Exécution d’une commande](../../oledb/ole-db-driver/executing-a-command.md)  
  
-   [Traitement des résultats](../../oledb/ole-db-driver/processing-results.md)  
  
-   [Présentation des propriétés OLE DB](../../oledb/ole-db-driver/about-ole-db-properties.md)  
  
-   [Utilisation de la clause OUTPUT avec OLE DB dans OLE DB Driver pour SQL Server](../../oledb/ole-db-driver/using-the-output-clause-with-ole-db-in-oledb-driver-for-sql-server.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Programmation OLE DB Driver pour SQL Server](../../oledb/ole-db/oledb-driver-for-sql-server-programming.md)  
  
  

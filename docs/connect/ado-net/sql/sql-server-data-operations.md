---
title: Opérations de données SQL Server dans ADO.NET
description: Décrit comment utiliser des données dans SQL Server. Contient des sections sur les opérations de copie en bloc, MARS, les opérations asynchrones et les paramètres table.
ms.date: 08/15/2019
ms.assetid: b864ebc9-ed8e-4059-85fd-36d9198f5521
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.topic: conceptual
author: rothja
ms.author: jroth
ms.reviewer: v-kaywon
ms.openlocfilehash: 3f435e44ef6fb7fb7ff777e2b5361482fcde9a98
ms.sourcegitcommit: b78f7ab9281f570b87f96991ebd9a095812cc546
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/31/2020
ms.locfileid: "75251115"
---
# <a name="sql-server-data-operations-in-adonet"></a>Opérations de données SQL Server dans ADO.NET

![Download-DownArrow-Circled](../../../ssdt/media/download.png)[Télécharger ADO.NET](../../sql-connection-libraries.md#anchor-20-drivers-relational-access)

Cette section décrit les fonctionnalités SQL Server spécifiques au fournisseur de données Microsoft SqlClient pour SQL Server (<xref:Microsoft.Data.SqlClient>).  
  
## <a name="in-this-section"></a>Contenu de cette section  
[Opérations de copie en bloc dans SQL Server](bulk-copy-operations-sql-server.md)  
Décrit la fonctionnalité de copie en bloc pour le fournisseur de données .NET pour SQL Server.  
  
[MARS (Multiple Active Result Sets)](multiple-active-result-sets-mars.md)  
Décrit comment avoir plusieurs instances <xref:Microsoft.Data.SqlClient.SqlDataReader> ouvertes sur une connexion lorsque chaque instance de <xref:Microsoft.Data.SqlClient.SqlDataReader> est démarrée à partir d’une commande distincte.  
  
[Opérations asynchrones](asynchronous-operations.md)  
Décrit comment effectuer des opérations de base de données asynchrones à l’aide d’une API modélisée d’après le modèle asynchrone utilisé par le .NET Framework.  
  
[Paramètres table](table-valued-parameters.md)  
Décrit comment utiliser les paramètres table qui ont été introduits dans SQL Server 2008.  
  
## <a name="next-steps"></a>Étapes suivantes
- [SQL Server et ADO.NET](index.md)

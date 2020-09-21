---
title: Ensembles de lignes (pilote OLE DB)
description: En savoir plus sur les interfaces qui prennent en charge un contrôle serveur consommateur en créant un ensemble de lignes dans une session dans OLE DB Driver pour SQL Server. Pour plus d’informations, consultez les articles de cette section.
ms.custom: ''
ms.date: 06/14/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: connectivity
ms.topic: reference
helpviewer_keywords:
- rowsets [OLE DB], about rowsets
- OLE DB Driver for SQL Server, rowsets
- OLE DB rowsets
- OLE DB rowsets, about rowsets
- rowsets [OLE DB]
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 55100932092abeb81da7fa1c156ccb5a61fc193c
ms.sourcegitcommit: c95f3ef5734dec753de09e07752a5d15884125e2
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/25/2020
ms.locfileid: "88859944"
---
# <a name="rowsets"></a>Ensembles de lignes
[!INCLUDE [SQL Server](../../../includes/applies-to-version/sql-asdb-asdbmi-asa-pdw.md)]

[!INCLUDE[Driver_OLEDB_Download](../../../includes/driver_oledb_download.md)]

  Un ensemble de lignes est un jeu de lignes contenant des colonnes de données. Les ensembles de lignes sont des objets centraux qui permettent à tous les fournisseurs de données OLE DB d'exposer les données des jeux de résultats sous forme tabulaire.  
  
 Après avoir créé une session en utilisant la méthode **IDBCreateSession::CreateSession**, le consommateur peut utiliser l’interface **IOpenRowset** ou **IDBCreateCommand** dans la session pour créer un ensemble de lignes. OLE DB Driver pour SQL Server prend en charge ces deux interfaces. Ces deux méthodes sont décrites ici.  
  
-   Créer un ensemble de lignes en appelant la méthode **IOpenRowset::OpenRowset**.  
  
     Cette solution est équivalente à la création d'un ensemble de lignes sur une même table. Cette méthode ouvre et retourne un ensemble de lignes qui inclut toutes les lignes d'une même table de base. L’un des arguments transmis à **OpenRowset** est un ID qui identifie la table à partir de laquelle créer l’ensemble de lignes.  
  
-   Créer un objet de commande en appelant la méthode **IDBCreateCommand::CreateCommand**.  
  
     L'objet de commande exécute les commandes que le fournisseur prend en charge. Avec le pilote OLE DB pour SQL Server, le consommateur peut spécifier une instruction [!INCLUDE[tsql](../../../includes/tsql-md.md)], telle qu’une instruction SELECT ou l’appel d’une procédure stockée. Les étapes de la création d'un ensemble de lignes en utilisant un objet de commande sont les suivantes :  
  
    1.  Le consommateur appelle la méthode **IDBCreateCommand::CreateCommand** dans la session pour obtenir un objet de commande qui demande l’interface **ICommandText** dans l’objet de commande. Cette interface **ICommandText** définit et récupère le texte de la commande. Le consommateur remplit la commande de texte en appelant la méthode **ICommandText::SetCommandText**.  
  
    2.  L’utilisateur appelle la méthode **ICommand::Execute** dans la commande. L'objet de l'ensemble de lignes créé lors de l'exécution de la commande contient le jeu de résultats de la commande.  
  
 Le consommateur peut utiliser l’interface **ICommandProperties** pour obtenir ou définir les propriétés de l’ensemble de lignes retourné par la commande exécutée par les interfaces **ICommand::Execute**. Les propriétés les plus communément demandées sont les interfaces que l'ensemble de lignes doit prendre en charge. En plus des interfaces, le consommateur peut demander les propriétés qui modifient le comportement de l'ensemble de lignes ou de l'interface.  
  
 Les consommateurs libèrent les ensembles de lignes avec la méthode **IRowset::Release**. La libération d'un ensemble de lignes entraîne celle des handles de ligne détenus par le consommateur sur cet ensemble de lignes. La libération d'un ensemble de lignes ne libère pas les accesseurs. Si vous avez une interface **IAccessor**, il lui reste à être libérée.  
  
## <a name="in-this-section"></a>Dans cette section  
  
-   [Création d’un ensemble de lignes avec IOpenRowset](../../oledb/ole-db-rowsets/creating-a-rowset-with-iopenrowset.md)  
  
-   [Création d’ensembles de lignes avec ICommand::Execute](../../oledb/ole-db-rowsets/creating-rowsets-with-icommand-execute.md)  
  
-   [Propriétés et comportements des ensembles de lignes](../../oledb/ole-db-rowsets/rowset-properties-and-behaviors.md)  
  
-   [Ensembles de lignes et curseurs SQL Server](../../oledb/ole-db-rowsets/rowsets-and-sql-server-cursors.md)  
  
-   [Récupération de lignes](../../oledb/ole-db-rowsets/fetching-rows.md)  
  
-   [Récupération d’une ligne unique avec IRow](../../oledb/ole-db-rowsets/fetching-a-single-row-with-irow.md)  
  
-   [Signets](../../oledb/ole-db-rowsets/bookmarks.md)  
  
-   [Mise à jour des données dans les ensembles de lignes](../../oledb/ole-db-rowsets/updating-data-in-rowsets.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Programmation OLE DB Driver pour SQL Server](../../oledb/ole-db/oledb-driver-for-sql-server-programming.md)  
  
  

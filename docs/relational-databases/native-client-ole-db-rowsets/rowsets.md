---
title: Ensembles de lignes | Microsoft Docs
description: Permet à tous les fournisseurs de données d’exposer les données du jeu de résultats sous forme de tableau. Dans OLE DB, utilisez la fonctionnalité d’ensemble de lignes, un ensemble de lignes qui contient des colonnes de données.
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- rowsets [OLE DB], about rowsets
- SQL Server Native Client OLE DB provider, rowsets
- OLE DB rowsets
- OLE DB rowsets, about rowsets
- rowsets [OLE DB]
ms.assetid: 5e7b3cbe-3670-4e18-8172-2226e0b6b142
author: markingmyname
ms.author: maghan
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 203b5114b79214b37ae719d34dfb5b23e9cb4352
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85724787"
---
# <a name="rowsets"></a>Ensembles de lignes
[!INCLUDE[SQL Server Azure SQL Database Synapse Analytics PDW ](../../includes/applies-to-version/sql-asdb-asdbmi-asdw-pdw.md)]

  Un ensemble de lignes est un jeu de lignes contenant des colonnes de données. Les ensembles de lignes sont des objets centraux qui permettent à tous les fournisseurs de données OLE DB d'exposer les données des jeux de résultats sous forme tabulaire.  
  
 Après avoir créé une session en utilisant la méthode **IDBCreateSession::CreateSession**, le consommateur peut utiliser l’interface **IOpenRowset** ou **IDBCreateCommand** dans la session pour créer un ensemble de lignes. Le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] fournisseur OLE DB Native Client prend en charge ces deux interfaces. Ces deux méthodes sont décrites ici.  
  
-   Créer un ensemble de lignes en appelant la méthode **IOpenRowset::OpenRowset**.  
  
     Cette solution est équivalente à la création d'un ensemble de lignes sur une même table. Cette méthode ouvre et retourne un ensemble de lignes qui inclut toutes les lignes d'une même table de base. L’un des arguments transmis à **OpenRowset** est un ID qui identifie la table à partir de laquelle créer l’ensemble de lignes.  
  
-   Créer un objet de commande en appelant la méthode **IDBCreateCommand::CreateCommand**.  
  
     L'objet de commande exécute les commandes que le fournisseur prend en charge. Avec le fournisseur OLE DB [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client, le consommateur peut spécifier une instruction [!INCLUDE[tsql](../../includes/tsql-md.md)], telle qu'une instruction SELECT ou l'appel d'une procédure stockée. Les étapes de la création d'un ensemble de lignes en utilisant un objet de commande sont les suivantes :  
  
    1.  Le consommateur appelle la méthode **IDBCreateCommand::CreateCommand** dans la session pour obtenir un objet de commande qui demande l’interface **ICommandText** dans l’objet de commande. Cette interface **ICommandText** définit et récupère le texte de la commande. Le consommateur remplit la commande de texte en appelant la méthode **ICommandText::SetCommandText**.  
  
    2.  L’utilisateur appelle la méthode **ICommand::Execute** dans la commande. L'objet de l'ensemble de lignes créé lors de l'exécution de la commande contient le jeu de résultats de la commande.  
  
 Le consommateur peut utiliser l’interface **ICommandProperties** pour obtenir ou définir les propriétés de l’ensemble de lignes retourné par la commande exécutée par les interfaces **ICommand::Execute**. Les propriétés les plus communément demandées sont les interfaces que l'ensemble de lignes doit prendre en charge. En plus des interfaces, le consommateur peut demander les propriétés qui modifient le comportement de l'ensemble de lignes ou de l'interface.  
  
 Les consommateurs libèrent les ensembles de lignes avec la méthode **IRowset::Release**. La libération d'un ensemble de lignes entraîne celle des handles de ligne détenus par le consommateur sur cet ensemble de lignes. La libération d'un ensemble de lignes ne libère pas les accesseurs. Si vous avez une interface **IAccessor**, il lui reste à être libérée.  
  
## <a name="in-this-section"></a>Dans cette section  
  
-   [Création d'un ensemble de lignes avec IOpenRowset](../../relational-databases/native-client-ole-db-rowsets/creating-a-rowset-with-iopenrowset.md)  
  
-   [Création d'ensembles de lignes avec ICommand::Execute](../../relational-databases/native-client-ole-db-rowsets/creating-rowsets-with-icommand-execute.md)  
  
-   [Propriétés et comportements de l'ensemble de lignes](../../relational-databases/native-client-ole-db-rowsets/rowset-properties-and-behaviors.md)  
  
-   [Ensembles de lignes et curseurs SQL Server](../../relational-databases/native-client-ole-db-rowsets/rowsets-and-sql-server-cursors.md)  
  
-   [Extraction de lignes](../../relational-databases/native-client-ole-db-rowsets/fetching-rows.md)  
  
-   [Extraction d'une ligne unique avec IRow](../../relational-databases/native-client-ole-db-rowsets/fetching-a-single-row-with-irow.md)  
  
-   [Signets](../../relational-databases/native-client-ole-db-rowsets/bookmarks.md)  
  
-   [Mise à jour des données dans les ensembles de lignes](../../relational-databases/native-client-ole-db-rowsets/updating-data-in-rowsets.md)  
  
## <a name="see-also"></a>Voir aussi  
 [SQL Server Native Client &#40;OLE DB&#41;](../../relational-databases/native-client/ole-db/sql-server-native-client-ole-db.md)  
  
  

---
title: Paramètres table (fournisseur Native Client OLE DB)
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- OLE DB, table-valued parameters
- table-valued parameters (OLE DB)
ms.assetid: 4298b73d-615b-4d28-9843-03b4d5fc489e
author: markingmyname
ms.author: maghan
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 40fe9932ca65af3087b8bcccc569adc2e0451952
ms.sourcegitcommit: 75f767c7b1ead31f33a870fddab6bef52f99906b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/28/2020
ms.locfileid: "87331870"
---
# <a name="table-valued-parameters--in-sql-server-native-client-ole-db"></a>Paramètres table en SQL Server Native Client (OLE DB)
[!INCLUDE[SQL Server Azure SQL Database Synapse Analytics PDW ](../../includes/applies-to-version/sql-asdb-asdbmi-asa-pdw.md)]

  Cette section décrit la prise en charge des paramètres table dans le fournisseur OLE DB [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client. Pour plus d’informations sur la vue d’ensemble, consultez [paramètres Table &#40;SQL Server Native Client&#41;](../../relational-databases/native-client/features/table-valued-parameters-sql-server-native-client.md). Pour obtenir un exemple, consultez [Utiliser les paramètres table &#40;OLE DB&#41;](../../relational-databases/native-client-ole-db-how-to/use-table-valued-parameters-ole-db.md).  
  
## <a name="remarks"></a>Notes  
 Vous pouvez actuellement envoyer des données à lignes multiples au serveur en tant que paramètres à une procédure, avec des jeux de paramètres (le paramètre DBPARAMS dans **ICommand::Execute**). Avec des jeux de paramètres, chaque élément du jeu doit être envoyé dans une demande d'appel de procédure distante séparée au serveur. Les paramètres table fournissent des fonctionnalités semblables, mais l'intégration avec le serveur est meilleure. Cela réduit le nombre de demandes d'appel de procédure distante et autorise des opérations basées sur des jeux sur le serveur.  
  
 Les paramètres de valeur de table sont pris en charge dans le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] fournisseur OLE DB Native Client en tant qu’objets d' **ensemble de lignes** OLE DB. Tout objet d' **ensemble de lignes** peut être fourni par le consommateur (autrement dit, l’application cliente à l’aide du [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] fournisseur OLE DB Native Client) comme espace réservé pour les paramètres table. Les paramètres table sont traités comme tout autre type de paramètre [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Le fournisseur OLE DB [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client fournit des interfaces de création, de découverte, de spécification, de liaison et de schéma.  
  
## <a name="in-this-section"></a>Dans cette section  
  
-   [Création d'un ensemble de lignes de paramètre table](../../relational-databases/native-client-ole-db-table-valued-parameters/table-valued-parameter-rowset-creation.md)  
  
-   [Découverte du type de paramètre table](../../relational-databases/native-client-ole-db-table-valued-parameters/table-valued-parameter-type-discovery.md)  
  
-   [Exécution de commandes contenant des paramètres table](../../relational-databases/native-client-ole-db-table-valued-parameters/executing-commands-containing-table-valued-parameters.md)  
  
-   [Insertion de données dans des paramètres table](../../relational-databases/native-client-ole-db-table-valued-parameters/inserting-data-into-table-valued-parameters.md)  
  
-   [Ensembles de lignes de schéma modifiés pour les paramètres table OLE DB](../../relational-databases/native-client-ole-db-table-valued-parameters/schema-rowsets-changed-for-ole-db-table-valued-parameters.md)  
  
-   [Prise en charge du type de paramètre table OLE DB](../../relational-databases/native-client-ole-db-table-valued-parameters/ole-db-table-valued-parameter-type-support.md)  
  
-   [Prise en charge des types de paramètre table OLE DB &#40;méthodes&#41;](../../relational-databases/native-client-ole-db-table-valued-parameters/ole-db-table-valued-parameter-type-support-methods.md)  
  
-   [Prise en charge des types de paramètre table OLE DB &#40;propriétés&#41;](../../relational-databases/native-client-ole-db-table-valued-parameters/ole-db-table-valued-parameter-type-support-properties.md)  
  
## <a name="see-also"></a>Voir aussi  
 [SQL Server Native Client &#40;OLE DB&#41;](../../relational-databases/native-client/ole-db/sql-server-native-client-ole-db.md)   
 [Utiliser les paramètres table &#40;OLE DB&#41;](../../relational-databases/native-client-ole-db-how-to/use-table-valued-parameters-ole-db.md)  
  
  

---
title: Paramètres table (OLE DB) | Microsoft Docs
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
author: MightyPen
ms.author: genemi
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 67991d5bd50b9612b8f3eaff01d37eef581b22f5
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "73761638"
---
# <a name="table-valued-parameters-ole-db"></a>Paramètres table (OLE DB)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  Cette section décrit la prise en charge des paramètres table dans le fournisseur OLE DB [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client. Pour plus d’informations sur la vue d’ensemble, consultez [paramètres Table &#40;SQL Server Native Client&#41;](../../relational-databases/native-client/features/table-valued-parameters-sql-server-native-client.md). Pour obtenir un exemple, consultez [utiliser des paramètres Table &#40;OLE DB&#41;](../../relational-databases/native-client-ole-db-how-to/use-table-valued-parameters-ole-db.md).  
  
## <a name="remarks"></a>Notes  
 Vous pouvez actuellement envoyer des données à lignes multiples au serveur en tant que paramètres à une procédure, avec des jeux de paramètres (le paramètre DBPARAMS dans **ICommand::Execute**). Avec des jeux de paramètres, chaque élément du jeu doit être envoyé dans une demande d'appel de procédure distante séparée au serveur. Les paramètres table fournissent des fonctionnalités semblables, mais l'intégration avec le serveur est meilleure. Cela réduit le nombre de demandes d'appel de procédure distante et autorise des opérations basées sur des jeux sur le serveur.  
  
 Les paramètres de valeur de table sont [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] pris en charge dans le fournisseur OLE DB Native Client en tant qu’objets d' **ensemble de lignes** OLE DB. Tout objet d' **ensemble de lignes** peut être fourni par le consommateur (autrement dit, l' [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] application cliente à l’aide du fournisseur OLE DB Native Client) comme espace réservé pour les paramètres table. Les paramètres table sont traités comme tout autre type de paramètre [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Le fournisseur OLE DB [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client fournit des interfaces de création, de découverte, de spécification, de liaison et de schéma.  
  
## <a name="in-this-section"></a>Dans cette section  
  
-   [Création d'un ensemble de lignes de paramètre table](../../relational-databases/native-client-ole-db-table-valued-parameters/table-valued-parameter-rowset-creation.md)  
  
-   [Découverte du type de paramètre table](../../relational-databases/native-client-ole-db-table-valued-parameters/table-valued-parameter-type-discovery.md)  
  
-   [Exécution de commandes contenant des paramètres table](../../relational-databases/native-client-ole-db-table-valued-parameters/executing-commands-containing-table-valued-parameters.md)  
  
-   [Insertion de données dans des paramètres table](../../relational-databases/native-client-ole-db-table-valued-parameters/inserting-data-into-table-valued-parameters.md)  
  
-   [Ensembles de lignes de schéma modifiés pour les paramètres table OLE DB](../../relational-databases/native-client-ole-db-table-valued-parameters/schema-rowsets-changed-for-ole-db-table-valued-parameters.md)  
  
-   [Prise en charge du type de paramètre table OLE DB](../../relational-databases/native-client-ole-db-table-valued-parameters/ole-db-table-valued-parameter-type-support.md)  
  
-   [OLE DB type de paramètre table prend en charge les méthodes de &#40;&#41;](../../relational-databases/native-client-ole-db-table-valued-parameters/ole-db-table-valued-parameter-type-support-methods.md)  
  
-   [OLE DB type de paramètre table prend en charge les propriétés de &#40;&#41;](../../relational-databases/native-client-ole-db-table-valued-parameters/ole-db-table-valued-parameter-type-support-properties.md)  
  
## <a name="see-also"></a>Voir aussi  
 [SQL Server Native Client &#40;OLE DB&#41;](../../relational-databases/native-client/ole-db/sql-server-native-client-ole-db.md)   
 [Utiliser les paramètres table &#40;OLE DB&#41;](../../relational-databases/native-client-ole-db-how-to/use-table-valued-parameters-ole-db.md)  
  
  

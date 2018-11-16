---
title: Détection de Type de paramètre table | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- table-valued parameters, type discovery
ms.assetid: f55818c2-ebb5-4cf6-8c0c-0da41f592560
author: MightyPen
ms.author: genemi
manager: craigg
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: fd093ed5352fc303642a2d20d2cab9a0829522ae
ms.sourcegitcommit: 1a5448747ccb2e13e8f3d9f04012ba5ae04bb0a3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/12/2018
ms.locfileid: "51558486"
---
# <a name="table-valued-parameter-type-discovery"></a>Découverte du type de paramètre table
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

  Le consommateur, autrement dit, l’application cliente utilisant la [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] fournisseur Native Client OLE DB — peut découvrir le type de chaque paramètre de commande si le texte de commande a été donné au fournisseur OLE DB. Une fois le type d’un paramètre table connu, le consommateur peut découvrir les informations de métadonnées de chacune des colonnes du paramètre table.  
  
 Les informations de type des paramètres de procédure sont pris en charge par ICommandWithParameters::GetParameterInfo pour la plupart des types de paramètres. Depuis [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)], avec l’introduction des types définis par l’utilisateur et du type de données **xml**, la méthode GetParameterInfo n’est plus suffisante, car il n’est pas possible de fournir des informations sur les types définis par l’utilisateur (nom, schéma et catalogue) par le biais de ICommandWithParameters. Une nouvelle interface, ISSCommandWithParameters, a été définie pour fournir des informations de type étendu.  
  
 Pour les paramètres table, vous utilisez également l’interface ISSCommandWithParameters pour découvrir des informations détaillées. Le client appelle ISSCommandWithParameters::GetParameterInfo après avoir préparé l’objet de commande. Pour les paramètres table, le membre *wType* de la structure DBPARAMINFO est défini sur DBTYPE_TABLE par le fournisseur. Le champ *ulParamSize* de la structure DBPARAMINFO a la valeur ~0.  
  
 Le consommateur peut ensuite demander des propriétés supplémentaires (nom de catalogue de type de paramètre table, nom de schéma de type de paramètre table, nom de type de paramètre table, ordre de tri et les colonnes par défaut) à l’aide de ISSCommandWithParameters :: GetParameterProperties.  
  
 Une fois le nom du type connu, pour récupérer les informations de chaque colonne, le consommateur doit appeler IOpenRowset::OpenRowsetor ou obtenir l’ensemble de lignes DBSCHEMA_TABLE_TYPE_COLUMNS en spécifiant le nom du type de paramètre table comme nom de table.  
  
## <a name="see-also"></a>Voir aussi  
 [Paramètres table &#40;OLE DB&#41;](../../relational-databases/native-client-ole-db-table-valued-parameters/table-valued-parameters-ole-db.md)   
 [Utiliser les paramètres table &#40;OLE DB&#41;](../../relational-databases/native-client-ole-db-how-to/use-table-valued-parameters-ole-db.md)  
  
  

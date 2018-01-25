---
title: "Détection de Type de paramètre table | Documents Microsoft"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: 
ms.component: native-client-ole-db-table-valued-parameters
ms.reviewer: 
ms.suite: sql
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords: table-valued parameters, type discovery
ms.assetid: f55818c2-ebb5-4cf6-8c0c-0da41f592560
caps.latest.revision: "20"
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 8cb2c68a50c97ca1e51dea778c81c5b9d5c60737
ms.sourcegitcommit: 9e6a029456f4a8daddb396bc45d7874a43a47b45
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/25/2018
---
# <a name="table-valued-parameter-type-discovery"></a>Découverte du type de paramètre table
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

  Le consommateur, autrement dit, l’application cliente utilisant la [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] fournisseur Native Client OLE DB, peut découvrir le type de chaque paramètre de commande si le texte de commande a été donné au fournisseur OLE DB. Une fois le type d’un paramètre table connu, le consommateur peut découvrir les informations de métadonnées de chacune des colonnes du paramètre table incluse.  
  
 Les informations de type des paramètres de procédure sont pris en charge par ICommandWithParameters::GetParameterInfo pour la plupart des types de paramètre. À partir de [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)], avec l’introduction des types définis par l’utilisateur et le **xml** type de données, la méthode GetParameterInfo était insuffisante à cette fin, car il n’était pas possible de fournir des informations de type défini par l’utilisateur (nom, schéma et catalogue) par le biais ICommandWithParameters. Une nouvelle interface, ISSCommandWithParameters, a été définie pour fournir des informations de type étendu.  
  
 Pour les paramètres table, vous utilisez également l’interface ISSCommandWithParameters pour découvrir des informations détaillées. Le client appelle ISSCommandWithParameters::GetParameterInfo après avoir préparé l’objet de commande. Pour les paramètres table, le *wType* membre de la structure DBPARAMINFO est défini sur DBTYPE_TABLE par le fournisseur. Le *ulParamSize* champ de la structure DBPARAMINFO a la valeur ~ 0.  
  
 Le consommateur peut ensuite demander des propriétés supplémentaires (nom de catalogue de type de paramètre table, nom de schéma de type de paramètre table, nom de type de paramètre table, colonne de classement et les colonnes par défaut) à l’aide de ISSCommandWithParamters::GetParameterProperties.  
  
 Une fois le nom de type est connu, pour récupérer les informations de colonne que le consommateur doit appeler soit IOpenRowset::OpenRowsetor obtenir l’ensemble de lignes DBSCHEMA_TABLE_TYPE_COLUMNS en spécifiant le nom de type de paramètre table comme nom de table.  
  
## <a name="see-also"></a>Voir aussi  
 [Table-Valued paramètres &#40; OLE DB &#41;](../../relational-databases/native-client-ole-db-table-valued-parameters/table-valued-parameters-ole-db.md)   
 [Utilisez la Table-Valued paramètres &#40; OLE DB &#41;](../../relational-databases/native-client-ole-db-how-to/use-table-valued-parameters-ole-db.md)  
  
  

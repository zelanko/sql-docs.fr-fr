---
title: Détection de Type de paramètre table | Microsoft Docs
description: Table-Valued paramètre découverte du type à l’aide de OLE DB Driver pour SQL Server
ms.custom: ''
ms.date: 06/14/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: connectivity
ms.topic: reference
helpviewer_keywords:
- table-valued parameters, type discovery
author: pmasl
ms.author: pelopes
manager: craigg
ms.openlocfilehash: 8e4da9d25a5d23e81e1d5dd44becd17e26263338
ms.sourcegitcommit: 1a5448747ccb2e13e8f3d9f04012ba5ae04bb0a3
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 11/12/2018
ms.locfileid: "51558316"
---
# <a name="table-valued-parameter-type-discovery"></a>Découverte du type de paramètre table
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

[!INCLUDE[Driver_OLEDB_Download](../../../includes/driver_oledb_download.md)]

  Le consommateur, autrement dit, l’application cliente utilisant le pilote OLE DB pour SQL Server, peut découvrir le type de chaque paramètre de commande si le texte de la commande a été donné au fournisseur OLE DB. Une fois le type d’un paramètre table connu, le consommateur peut découvrir les informations de métadonnées de chacune des colonnes du paramètre table.  
  
 Les informations de type des paramètres de procédure sont pris en charge par ICommandWithParameters::GetParameterInfo pour la plupart des types de paramètres. Depuis [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)], avec l’introduction des types définis par l’utilisateur et du type de données **xml**, la méthode GetParameterInfo n’est plus suffisante, car il n’est pas possible de fournir des informations sur les types définis par l’utilisateur (nom, schéma et catalogue) par le biais de ICommandWithParameters. Une nouvelle interface, ISSCommandWithParameters, a été définie pour fournir des informations de type étendu.  
  
 Pour les paramètres table, vous utilisez également l’interface ISSCommandWithParameters pour découvrir des informations détaillées. Le client appelle ISSCommandWithParameters::GetParameterInfo après avoir préparé l’objet de commande. Pour les paramètres table, le membre *wType* de la structure DBPARAMINFO est défini sur DBTYPE_TABLE par le fournisseur. Le champ *ulParamSize* de la structure DBPARAMINFO a la valeur ~0.  
  
 Le consommateur peut ensuite demander des propriétés supplémentaires (nom de catalogue, nom de schéma et nom du type de paramètre table, tri des colonnes et colonnes par défaut) avec ISSCommandWithParameters::GetParameterProperties.  
  
 Une fois le nom du type connu, pour récupérer les informations de chaque colonne, le consommateur doit appeler IOpenRowset::OpenRowsetor ou obtenir l’ensemble de lignes DBSCHEMA_TABLE_TYPE_COLUMNS en spécifiant le nom du type de paramètre table comme nom de table.  
  
## <a name="see-also"></a> Voir aussi  
 [Paramètres table &#40;OLE DB&#41;](../../oledb/ole-db-table-valued-parameters/table-valued-parameters-ole-db.md)   
 [Utiliser les paramètres table &#40;OLE DB&#41;](../../oledb/ole-db-how-to/use-table-valued-parameters-ole-db.md)  
  
  

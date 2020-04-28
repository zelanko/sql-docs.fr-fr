---
title: Découverte du type de paramètre table | Microsoft Docs
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
author: markingmyname
ms.author: maghan
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 71e22c7945edb2014fc5c14ffcb5644fcc96a846
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/27/2020
ms.locfileid: "81301222"
---
# <a name="table-valued-parameter-type-discovery"></a>Découverte du type de paramètre table
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  Le consommateur, c’est-à-dire l’application cliente utilisant le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] fournisseur de OLE DB Native Client, peut découvrir le type de chaque paramètre de commande si le texte de la commande a été donné au fournisseur OLE DB. Une fois le type d’un paramètre table connu, le consommateur peut découvrir les informations de métadonnées de chacune des colonnes du paramètre table.  
  
 Les informations de type des paramètres de procédure sont prises en charge par ICommandWithParameters::GetParameterInfo pour la plupart des types de paramètres. Depuis [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)], avec l’introduction des types définis par l’utilisateur et du type de données **xml**, la méthode GetParameterInfo n’est plus suffisante, car il n’est pas possible de fournir des informations sur les types définis par l’utilisateur (nom, schéma et catalogue) par le biais de ICommandWithParameters. Une nouvelle interface, ISSCommandWithParameters, a été définie pour fournir des informations étendues sur les types.  
  
 Pour les paramètres table, l'interface ISSCommandWithParameters est également utilisée pour découvrir des informations détaillées. Le client appelle ISSCommandWithParameters::GetParameterInfo après la préparation de l’objet de commande. Pour les paramètres table, le membre *wType* de la structure DBPARAMINFO est défini sur DBTYPE_TABLE par le fournisseur. Le champ *ulParamSize* de la structure DBPARAMINFO a la valeur ~0.  
  
 Le consommateur peut ensuite demander des propriétés supplémentaires (nom de catalogue, nom de schéma et nom du type de paramètre table, tri des colonnes et colonnes par défaut) avec ISSCommandWithParameters::GetParameterProperties.  
  
 Une fois le nom du type connu, pour récupérer les informations de chaque colonne, le consommateur doit appeler IOpenRowset::OpenRowsetor ou obtenir l’ensemble de lignes DBSCHEMA_TABLE_TYPE_COLUMNS en spécifiant le nom du type de paramètre table comme nom de table.  
  
## <a name="see-also"></a>Voir aussi  
 [Paramètres table &#40;OLE DB&#41;](../../relational-databases/native-client-ole-db-table-valued-parameters/table-valued-parameters-ole-db.md)   
 [Utiliser les paramètres table &#40;OLE DB&#41;](../../relational-databases/native-client-ole-db-how-to/use-table-valued-parameters-ole-db.md)  
  
  

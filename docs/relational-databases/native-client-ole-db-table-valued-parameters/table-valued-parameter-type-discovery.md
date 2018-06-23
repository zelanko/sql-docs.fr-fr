---
title: Détection de Type de paramètre table | Documents Microsoft
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- table-valued parameters, type discovery
ms.assetid: f55818c2-ebb5-4cf6-8c0c-0da41f592560
caps.latest.revision: 20
author: MightyPen
ms.author: genemi
manager: craigg
monikerRange: '>= aps-pdw-2016 || = azuresqldb-current || = azure-sqldw-latest || >= sql-server-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: 3fbc4e5f1ca395eb79539e8d670743bdf015b168
ms.sourcegitcommit: a78fa85609a82e905de9db8b75d2e83257831ad9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/18/2018
ms.locfileid: "35698660"
---
# <a name="table-valued-parameter-type-discovery"></a>Découverte du type de paramètre table
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

  Le consommateur, autrement dit, l’application cliente utilisant la [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] fournisseur Native Client OLE DB, peut découvrir le type de chaque paramètre de commande si le texte de commande a été donné au fournisseur OLE DB. Une fois le type d’un paramètre table connu, le consommateur peut découvrir les informations de métadonnées de chacune des colonnes du paramètre table incluse.  
  
 Les informations de type des paramètres de procédure sont pris en charge par ICommandWithParameters::GetParameterInfo pour la plupart des types de paramètre. À partir de [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)], avec l’introduction des types définis par l’utilisateur et le **xml** type de données, la méthode GetParameterInfo était insuffisante à cette fin, car il n’était pas possible de fournir le type défini par l’utilisateur informations (nom, schéma et catalogue) par le biais ICommandWithParameters. Une nouvelle interface, ISSCommandWithParameters, a été définie pour fournir des informations de type étendu.  
  
 Pour les paramètres table, vous utilisez également l’interface ISSCommandWithParameters pour découvrir des informations détaillées. Le client appelle ISSCommandWithParameters::GetParameterInfo après avoir préparé l’objet de commande. Pour les paramètres table, le *wType* membre de la structure DBPARAMINFO est défini sur DBTYPE_TABLE par le fournisseur. Le *ulParamSize* champ de la structure DBPARAMINFO a la valeur ~ 0.  
  
 Le consommateur peut ensuite demander des propriétés supplémentaires (nom de catalogue de type de paramètre table, nom de schéma de type de paramètre table, nom de type de paramètre table, colonne de classement et les colonnes par défaut) à l’aide de ISSCommandWithParamters :: GetParameterProperties.  
  
 Une fois le nom de type est connu, pour récupérer les informations de colonne que le consommateur doit appeler soit IOpenRowset::OpenRowsetor obtenir l’ensemble de lignes DBSCHEMA_TABLE_TYPE_COLUMNS en spécifiant le nom de type de paramètre table comme nom de table.  
  
## <a name="see-also"></a>Voir aussi  
 [Paramètres table &#40;OLE DB&#41;](../../relational-databases/native-client-ole-db-table-valued-parameters/table-valued-parameters-ole-db.md)   
 [Utiliser des paramètres table &#40;OLE DB&#41;](../../relational-databases/native-client-ole-db-how-to/use-table-valued-parameters-ole-db.md)  
  
  

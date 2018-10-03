---
title: Détection de Type de paramètre table | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- database-engine
- docset-sql-devref
ms.topic: reference
helpviewer_keywords:
- table-valued parameters, type discovery
ms.assetid: f55818c2-ebb5-4cf6-8c0c-0da41f592560
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 66f2be8633c7070e2458d5c1e1258fe3bcb9f949
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48146719"
---
# <a name="table-valued-parameter-type-discovery"></a>Découverte du type de paramètre table
  Le consommateur, autrement dit, l’application cliente utilisant la [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] fournisseur Native Client OLE DB — peut découvrir le type de chaque paramètre de commande si le texte de commande a été donné au fournisseur OLE DB. Une fois le type d’un paramètre table connu, le consommateur peut découvrir les informations de métadonnées de chacune des colonnes du paramètre table.  
  
 Les informations de type des paramètres de procédure sont pris en charge par ICommandWithParameters::GetParameterInfo pour la plupart des types de paramètres. À partir de [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)], avec l’introduction des types définis par l’utilisateur et le `xml` type de données, la méthode GetParameterInfo n’était pas suffisante à cet effet, car il n’était pas possible de fournir des informations de type défini par l’utilisateur (nom, schéma, et catalogue) par le biais ICommandWithParameters. Une nouvelle interface, ISSCommandWithParameters, a été définie pour fournir des informations de type étendu.  
  
 Pour les paramètres table, vous utilisez également l’interface ISSCommandWithParameters pour découvrir des informations détaillées. Le client appelle ISSCommandWithParameters::GetParameterInfo après avoir préparé l’objet de commande. Pour les paramètres table, le *wType* membre de la structure DBPARAMINFO est défini sur DBTYPE_TABLE par le fournisseur. Le champ *ulParamSize* de la structure DBPARAMINFO a la valeur ~0.  
  
 Le consommateur peut ensuite demander des propriétés supplémentaires (nom de catalogue du type de paramètre table, nom de schéma du type de paramètre table et nom du type de paramètre table, tri des colonnes et colonnes par défaut) à l’aide de ISSCommandWithParamters::GetParameterProperties.  
  
 Une fois le nom du type connu, pour récupérer les informations de chaque colonne, le consommateur doit appeler IOpenRowset::OpenRowsetor ou obtenir l’ensemble de lignes DBSCHEMA_TABLE_TYPE_COLUMNS en spécifiant le nom du type de paramètre table comme nom de table.  
  
## <a name="see-also"></a>Voir aussi  
 [Paramètres table &#40;OLE DB&#41;](../../relational-databases/native-client-ole-db-table-valued-parameters/table-valued-parameters-ole-db.md)   
 [Utiliser les paramètres table &#40;OLE DB&#41;](../../relational-databases/native-client-ole-db-how-to/use-table-valued-parameters-ole-db.md)  
  
  

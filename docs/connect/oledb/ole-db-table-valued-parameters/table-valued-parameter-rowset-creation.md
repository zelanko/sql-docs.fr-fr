---
title: Création d’un ensemble de lignes de paramètre table | Microsoft Docs
description: Création d’un ensemble de lignes de paramètre table statique et dynamique
ms.custom: ''
ms.date: 06/14/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: connectivity
ms.topic: reference
helpviewer_keywords:
- table-valued parameters, rowset creation
author: pmasl
ms.author: pelopes
ms.openlocfilehash: c771d8bde657b464b29a109dadd7a4d6fa33fbdb
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "67994107"
---
# <a name="table-valued-parameter-rowset-creation"></a>Création d'un ensemble de lignes de paramètre table
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

[!INCLUDE[Driver_OLEDB_Download](../../../includes/driver_oledb_download.md)]

  Bien que les consommateurs puissent fournir n'importe quel objet d'ensemble de lignes pour les paramètres table, les objets d'ensemble de lignes communs sont implémentés dans des banques de données principales, ce qui limite leurs performances. C’est pourquoi le pilote OLE DB pour SQL Server permet aux consommateurs de créer un objet d’ensemble de lignes spécialisé par-dessus les données en mémoire. Cet objet d'ensemble de lignes spécial stocké en mémoire est un nouvel objet COM appelé un ensemble de lignes de paramètre table. Il fournit des fonctionnalités similaires aux jeux de paramètres.  
  
 Les objets d'ensemble de lignes de paramètre table sont créés explicitement par le consommateur pour les paramètres d'entrée via plusieurs interfaces de niveau session. Il existe une instance d’un objet d’ensemble de lignes de paramètre table par paramètre table. Le consommateur peut créer les objets d'ensemble de lignes de paramètre table soit en fournissant des informations de métadonnées qui sont déjà connues (scénario statique), soit en révélant ces informations par le biais des interfaces du fournisseur (scénario dynamique). Les sections qui suivent décrivent ces deux scénarios :  
  
## <a name="static-scenario"></a>Scénario statique  
 Lorsque les informations de type sont connues, le consommateur utilise ITableDefinitionWithConstraints:: CreateTableWithConstraints pour instancier un objet d’ensemble de lignes de paramètre table qui correspond à un paramètre table.  
  
 Le champ *GUID* (paramètre*pTableID* ) contient le GUID spécial (CLSID_ROWSET_TVP). Le membre *pwszName* contient le nom du type de paramètre table que le consommateur souhaite instancier. Le champ *eKind* sera défini sur DBKIND_GUID_NAME. Ce nom est nécessaire lorsque l’instruction est une instruction SQL ad hoc. Le nom est facultatif s’il s’agit d’un appel de procédure.  
  
 Pour l’agrégation, le consommateur passe le paramètre *pUnkOuter* avec le contrôle IUnknown.  
  
 Les propriétés des objets d’ensemble de lignes de paramètre table sont en lecture seule. Le consommateur n’est donc pas supposé définir une quelconque propriété dans *rgPropertySets*.  
  
 Pour le membre *rgPropertySets* de chaque structure DBCOLUMNDESC, le consommateur peut spécifier des propriétés supplémentaires pour chaque colonne. Ces propriétés appartiennent au jeu de propriétés DBPROPSET_SQLSERVERCOLUMN. Elles vous permettent de spécifier les paramètres calculés et les paramètres par défaut de chaque colonne. Elles prennent également en charge les propriétés de colonnes existantes, telles que la possibilité de valeur Null et l'identité.  
  
 Pour récupérer les informations correspondantes d’un objet d’ensemble de lignes de paramètre table, le consommateur utilise IRowsetInfo::GetProperties.  
  
 Pour récupérer les informations sur l’État null, unique, calculé et mis à jour de chaque colonne, le consommateur peut utiliser IColumnsRowset:: GetColumnsRowset ou IColumnsInfo:: GetColumnInfo. Ces méthodes fournissent des informations détaillées sur chaque colonne de l'ensemble de lignes du paramètre table.  
  
 Le consommateur spécifie le type de chaque colonne du paramètre table. Ceci est identique à la spécification de colonnes lors de la création d’une table dans [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. Le consommateur obtient un objet d’ensemble de lignes de paramètre table à partir du pilote OLE DB pour SQL Server via le paramètre de sortie *ppRowset* .  
  
## <a name="dynamic-scenario"></a>Scénario Dynamique  
 Lorsque le consommateur n’a pas d’informations de type, il doit utiliser IOpenRowset:: OpenRowset pour instancier des objets d’ensemble de lignes de paramètre table. Tout ce que le consommateur doit fournir au fournisseur est le nom du type.  
  
 Dans ce scénario, le fournisseur obtient les informations de type d'un objet d'ensemble de lignes de paramètre table à partir du serveur au nom du consommateur.  
  
 Les paramètres *pTableID* et *pUnkOuter* doivent être définis comme dans le scénario statique. Le pilote OLE DB pour SQL Server obtient ensuite les informations de type (informations et contraintes de colonne) du serveur et retourne un objet d’ensemble de lignes de paramètre table par le biais du paramètre *ppRowset*. Cette opération nécessite une communication avec le serveur, et par conséquent, ne fonctionne pas aussi bien que le scénario statique. Le scénario dynamique fonctionne uniquement avec des appels de procédure paramétrables.  
  
## <a name="see-also"></a>Voir aussi  
 [Paramètres table &#40;OLE DB&#41;](../../oledb/ole-db-table-valued-parameters/table-valued-parameters-ole-db.md)   
 [Utiliser les paramètres table &#40;OLE DB&#41;](../../oledb/ole-db-how-to/use-table-valued-parameters-ole-db.md)  
  
  

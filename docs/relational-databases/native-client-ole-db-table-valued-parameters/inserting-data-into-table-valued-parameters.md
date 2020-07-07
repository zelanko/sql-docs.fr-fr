---
title: Insertion de données dans des paramètres table | Microsoft Docs
description: Découvrez les deux modèles pris en charge par le fournisseur SQL Server Native Client OLE DB pour que le consommateur spécifie des données pour les lignes de paramètres table.
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- table-valued parameters, inserting data into
ms.assetid: 9c1a3234-4675-40d3-b473-8df06208f880
author: markingmyname
ms.author: maghan
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 739f2e04b77197e0189f34651bcaac045d7a4c7e
ms.sourcegitcommit: f3321ed29d6d8725ba6378d207277a57cb5fe8c2
ms.contentlocale: fr-FR
ms.lasthandoff: 07/06/2020
ms.locfileid: "86013064"
---
# <a name="inserting-data-into-table-valued-parameters"></a>Insertion de données dans des paramètres table
[!INCLUDE[SQL Server Azure SQL Database Synapse Analytics PDW ](../../includes/applies-to-version/sql-asdb-asdbmi-asa-pdw.md)]

  Le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] fournisseur de OLE DB Native Client prend en charge deux modèles pour que le consommateur spécifie des données pour les lignes de paramètres table : un modèle d’émission et un modèle d’extraction. Pour obtenir un exemple illustrant le modèle de tirage (pull) des données, consultez [Exemples de programmation de données SQL Server](https://msftdpprodsamples.codeplex.com/).  
  
> [!NOTE]  
>  Une colonne de paramètre table doit avoir, soit des valeurs non définies par défaut, soit des valeurs définies par défaut dans toutes les lignes. Il n'est pas possible d'avoir des valeurs par défaut dans certaines lignes et pas d'autres. Par conséquent, dans les liaisons de paramètres table, les seules valeurs d'état autorisées pour les données de colonnes d'ensembles de lignes de paramètres table sont DBSTATUS_S_ISNULL et DBSTATUS_S_OK. DBSTATUS_S_DEFAULT provoque un échec et la valeur d'état liée est définie à DBSTATUS_E_BADSTATUS.  
  
## <a name="push-model-loads-all-table-valued-paremeter-data-in-memory"></a>Modèle d'émission des données (charge toutes les données de paramètres table en mémoire)  
 Le modèle d’envoi (push) des données est semblable à l’utilisation des jeux de paramètres (c’est-à-dire le paramètre DBPARAMS dans ICommand::Execute). Le modèle d’envoi des données est utilisé uniquement si les objets d’ensembles de lignes de paramètres table sont utilisés sans implémentation personnalisée des interfaces IRowset. Le modèle d'émission des données est recommandé lorsque le nombre de lignes de l'ensemble de lignes de paramètres table est faible et qu'il ne risque pas d'entraîner une sollicitation excessive de la mémoire dans l'application. Il est plus simple que le modèle d'extraction des données, car les seules fonctionnalités qu'il requiert de la part de l'application du consommateur sont celles communes aux applications OLE DB classiques.  
  
 Le consommateur est censé fournir toutes les données de paramètres table au fournisseur avant d'exécuter une commande. Pour fournir les données, le consommateur remplit un objet d'ensemble de lignes de paramètres table pour chaque paramètre table. L'objet d'ensemble de lignes de paramètres table expose les opérations d'insertion, de définition et de suppression de l'ensemble de lignes, qui permettent au consommateur de manipuler les données de paramètres table. Le fournisseur extrait les données de cet objet d'ensemble de lignes de paramètres table au moment de l'exécution.  
  
 Lorsqu'un objet d'ensemble de lignes de paramètres table est fourni au consommateur, ce dernier peut le traiter comme un objet d'ensemble de lignes. Le consommateur peut obtenir les informations de type de chaque colonne (type, longueur maximale, précision et échelle) en utilisant la méthode d'interface IColumnsInfo::GetColumnInfo ou IColumnsRowset::GetColumnsRowset. Le consommateur crée ensuite un accesseur pour spécifier les liaisons des données. L'étape suivante consiste à insérer des lignes de données dans l'ensemble de lignes de paramètres table. Pour ce faire, vous pouvez utiliser IRowsetChange::InsertRow. Cela est aussi possible via IRowsetChange::SetData ou IRowsetChange::DeleteRows sur l'objet d'ensemble de lignes de paramètres table si vous devez manipuler les données. Les objets d'ensembles de lignes de paramètres table ont un décompte de références, à l'instar des objets de flux.  
  
 Si vous utilisez IColumnsRowset::GetColumnsRowset, il y aura des appels ultérieurs aux méthodes IRowset::GetNextRows, IRowset::GetData et IRowset::ReleaseRows sur l’objet d’ensemble de lignes de la colonne résultante.  
  
 Une fois que le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] fournisseur de OLE DB Native Client commence à exécuter la commande, les valeurs de paramètre table sont extraites de cet objet d’ensemble de lignes de paramètre table et envoyées au serveur.  
  
 Le modèle d'émission des données requiert un travail minimal de la part du consommateur ; toutefois, il utilise plus de mémoire que le modèle d'extraction des données, car toutes les données de paramètres table doivent être en mémoire au moment de l'exécution.  
  
## <a name="pull-model-obtaining-table-valued-parameter-data-on-demand-from-the-consumer"></a>Modèle d'extraction des données (obtention de données de paramètres table sur demande, de la part du consommateur)  
 Le modèle d'extraction des données est utile pour deux scénarios :  
  
-   flux de lignes ;  
  
-   utilisation d'un ensemble de lignes d'un autre fournisseur comme valeur de paramètre table.  
  
 Dans le modèle d'extraction des données, le consommateur fournit des données au fournisseur à la demande. Utilisez cette approche si votre application comporte de nombreuses insertions de données et si les données d'ensembles de lignes de paramètres table en mémoire peuvent entraîner une sollicitation excessive de la mémoire. Si plusieurs fournisseurs OLE DB sont utilisés, le modèle d'extraction des données du consommateur permet à ce dernier de fournir n'importe quel objet d'ensemble de lignes en tant que valeur de paramètre table.  
  
 Pour utiliser le modèle d'extraction des données, les consommateurs doivent fournir leur propre implémentation d'un objet d'ensemble de lignes. Lors de l'utilisation du modèle d'extraction des données avec les ensembles de lignes de paramètres table (CLSID_ROWSET_TVP), le consommateur doit agréger l'objet d'ensemble de lignes de paramètres table que le fournisseur expose via la méthode ITableDefinitionWithConstraints::CreateTableWithConstraints ou IOpenRowset::OpenRowset. L'objet du consommateur est uniquement supposé substituer l'implémentation de l'interface IRowset. Vous devez substituer les fonctions suivantes :  
  
-   IRowset::GetNextRows  
  
-   IRowset::AddRefRows  
  
-   IRowset::GetData  
  
-   IRowset::ReleaseRows  
  
-   IRowset::RestartPosition  
  
 Le fournisseur OLE DB de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client lit une ou plusieurs lignes à la fois à partir de l'objet d'ensemble de lignes du consommateur afin de prendre en charge l'accès en continu dans les paramètres table. Par exemple, l'utilisateur peut disposer des données d'ensembles de lignes de paramètres table sur disque (et non en mémoire) et peut implémenter les fonctionnalités de lecture des données à partir du disque lorsque cela est requis par le fournisseur OLE DB de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client.  
  
 Le consommateur communique son format de données au [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] fournisseur OLE DB Native Client à l’aide de IAccessor :: CreateAccessor sur l’objet d’ensemble de lignes de paramètre table. Lors de la lecture des données à partir de la mémoire tampon du consommateur, le fournisseur s'assure que toutes les colonnes accessibles en écriture et non définies par défaut sont disponibles à travers au moins un handle d'accesseur, et utilise les handles correspondants pour lire les données des colonnes. Pour éviter toute ambiguïté, il doit exister une correspondance unique entre une colonne d’ensemble de lignes de paramètres table et une liaison. Les liaisons en double à la même colonne génèrent une erreur. Par ailleurs, chaque accesseur est supposé avoir le membre *iOrdinal* de DBBindings en séquence. Il y a autant d’appels à IRowset::GetData que d’accesseurs par ligne. En outre, l’ordre des appels est basé sur l’ordre de la valeur *iOrdinal*, du plus petit au plus grand.  
  
 Le fournisseur est supposé implémenter la plupart des interfaces exposées par l'objet d'ensemble de lignes de paramètres table. Le consommateur implémente un objet d’ensemble de lignes avec des interfaces minimales (IRowset). Avec une agrégation indifférenciée, les interfaces d'objets d'ensembles de lignes obligatoires restantes sont implémentées par l'objet d'ensemble de lignes de paramètres table.  
  
 Pour tout autre objet d'ensemble de lignes, par exemple les objets d'ensembles de lignes obtenus pour n'importe quel fournisseur OLE DB, l'ensemble de lignes fourni par le consommateur doit implémenter toutes les interfaces d'objets d'ensembles de lignes obligatoires conformément à la spécification OLE DB.  
  
 Au moment de l'exécution, le fournisseur OLE DB de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client rappelle l'objet d'ensemble de lignes pour extraire les lignes et lire les données de colonne.  
  
## <a name="see-also"></a>Voir aussi  
 [Paramètres table &#40;OLE DB&#41;](../../relational-databases/native-client-ole-db-table-valued-parameters/table-valued-parameters-ole-db.md)   
 [Utiliser les paramètres table &#40;OLE DB&#41;](../../relational-databases/native-client-ole-db-how-to/use-table-valued-parameters-ole-db.md)  
  
  

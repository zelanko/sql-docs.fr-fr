---
title: Objets BLOB et OLE | Microsoft Docs
description: Objets BLOB et OLE
ms.custom: ''
ms.date: 06/14/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.component: oledb|ole-db-blobs
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- BLOBs, OLE objects
- BLOBs
- storage object [OLE DB]
- OLE DB Driver for SQL Server, BLOBs
- large data, OLE objects
author: pmasl
ms.author: pelopes
manager: craigg
ms.openlocfilehash: 52c1793b315e89770efaae9cedca7b4da730c71c
ms.sourcegitcommit: 182b8f68bfb345e9e69547b6d507840ec8ddfd8b
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 08/27/2018
ms.locfileid: "43034947"
---
# <a name="blobs-and-ole-objects"></a>Objets BLOB et OLE
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

[!INCLUDE[Driver_OLEDB_Download](../../../includes/driver_oledb_download.md)]

  Le pilote OLE DB pour SQL Server expose l’interface **ISequentialStream** pour prendre en charge l’accès des consommateurs aux types de données [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] **ntext**, **text**, **image**, **varchar(max)**, **nvarchar(max)**, **varbinary(max)** et XML comme objets BLOB. La méthode **Read** sur **ISequentialStream** permet au consommateur de récupérer un grand nombre de données en blocs maniables.  
  
 Pour obtenir un exemple illustrant cette fonctionnalité, consultez [définir les données volumineuses &#40;OLE DB&#41;](../../oledb/ole-db-how-to/set-large-data-ole-db.md).  
  
 Le pilote OLE DB pour SQL Server peut utiliser une interface **IStorage** implémentée par le consommateur quand celui-ci fournit le pointeur d’interface dans un accesseur lié pour la modification des données.  
  
 Pour les types de données avec des valeurs volumineuses, le pilote OLE DB pour SQL Server vérifie les hypothèses sur la taille du type dans les interfaces **IRowset** et DDL. Les colonnes avec les types de données **varchar**, **nvarchar** et **varbinary**, et définies avec une taille maximale illimitée, sont représentées en tant que ISLONG dans les ensembles de lignes du schéma et les interfaces qui retournent les types de données des colonnes.  
  
 Le pilote OLE DB pour SQL Server expose les types **varchar(max)**, **varbinary(max)** et **nvarchar(max)** respectivement comme DBTYPE_STR, DBTYPE_BYTES et DBTYPE_WSTR.  
  
 Pour utiliser ces types, une application dispose des options suivantes :  
  
-   Lier comme type (DBTYPE_STR, DBTYPE_BYTES, DBTYPE_WSTR). Si la mémoire tampon n’est pas assez grande, une troncation est effectuée, exactement comme pour ces types dans les précédentes versions (bien que de plus grandes valeurs soient maintenant disponibles).  
  
-   Lier comme type et spécifier également DBTYPE_BYREF.  
  
-   Lier comme DBTYPE_IUNKNOWN et utiliser la diffusion en continu.  
  
 En cas de liaison à DBTYPE_IUNKNOWN, la fonctionnalité de flux ISequentialStream est utilisée. Le pilote OLE DB pour SQL Server prend en charge la liaison des paramètres de sortie en tant que DBTYPE_IUNKNOWN pour les types de données de valeur élevée. Il s’agit pour prendre en charge les scénarios où une procédure stockée retourne ces types de données en tant que valeurs de retour, qui seront restitués au client en tant que DBTYPE_IUNKNOWN.  
  
## <a name="storage-object-limitations"></a>Limitations des objets de stockage  
  
-   Le pilote OLE DB pour SQL Server peut prendre en charge uniquement un objet de stockage ouvert unique. Les tentatives d’ouverture de plusieurs objets de stockage (pour obtenir une référence sur plusieurs pointeurs d’interface **ISequentialStream**) retournent DBSTATUS_E_CANTCREATE.  
  
-   Dans le pilote OLE DB pour SQL Server, la valeur par défaut de la propriété en lecture seule de DBPROP_BLOCKINGSTORAGEOBJECTS est VARIANT_TRUE. Cela signifie que si un objet de stockage est actif, certaines méthodes (autres que celles sur les objets de stockage) échouent avec E_UNEXPECTED.  
  
-   Le pilote OLE DB pour SQL Server doit avoir connaissance de la longueur des données présentées par un objet de stockage implémenté par le consommateur quand l’accesseur de ligne qui référence l’objet de stockage est créé. Le consommateur doit lier un indicateur de longueur dans la structure DBBINDING utilisée pour la création de l'accesseur.  
  
-   Si une ligne contient plusieurs valeurs de données volumineuses et que DBPROP_ACCESSORDER n’est pas DBPROPVAL_AO_RANDOM, le consommateur doit utiliser un ensemble de lignes pris en charge par le curseur du pilote OLE DB pour SQL Server pour extraire les données de ligne ou traiter toutes les valeurs de données volumineuses avant d’extraire d’autres valeurs de ligne. Si DBPROP_ACCESSORDER a pour valeur DBPROPVAL_AO_RANDOM, le pilote OLE DB pour SQL Server met en cache tous les types de données XML comme objets BLOB pour en permettre l’accès dans n’importe quel ordre.  
  
## <a name="in-this-section"></a>Dans cette section  
  
-   [Obtention de données volumineuses](../../oledb/ole-db-blobs/getting-large-data.md)  
  
-   [Définition de données volumineuses](../../oledb/ole-db-blobs/setting-large-data.md)  
  
-   [Prise en charge de la diffusion en continu pour les paramètres de sortie BLOB](../../oledb/ole-db-blobs/streaming-support-for-blob-output-parameters.md)  
  
## <a name="see-also"></a> Voir aussi  
 [Programmation du pilote OLE DB pour SQL Server](../../oledb/ole-db/oledb-driver-for-sql-server-programming.md)        
 [Utilisation de types de valeur élevée](../../oledb/features/using-large-value-types.md)  
  
  

---
title: Objets BLOB et OLE | Microsoft Docs
ms.custom: ''
ms.date: 03/16/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- BLOBs, OLE objects
- BLOBs
- storage object [OLE DB]
- SQL Server Native Client OLE DB provider, BLOBs
- large data, OLE objects
ms.assetid: 767fa2f6-9cd2-436f-add5-e760bed29a58
author: MightyPen
ms.author: genemi
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: b4e284d2086684af232c17b59675b834b26f497b
ms.sourcegitcommit: 856e42f7d5125d094fa84390bc43048808276b57
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/07/2019
ms.locfileid: "73790631"
---
# <a name="blobs-and-ole-objects"></a>Objets BLOB et OLE
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  Le fournisseur [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB expose l’interface **ISequentialStream** pour prendre en charge l’accès des consommateurs à [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] **ntext**, **Text**, **image**, **varchar (max)** , **nvarchar (max)** , **varbinary (max)** , et les types de données XML en tant qu’objets BLOB (Binary Large Object). La méthode **Read** sur **ISequentialStream** permet au consommateur de récupérer un grand nombre de données en blocs maniables.  
  
 Pour obtenir un exemple illustrant cette fonctionnalité, consultez [définir des &#40;OLE DB&#41;de données volumineuses](../../relational-databases/native-client-ole-db-how-to/set-large-data-ole-db.md).  
  
 Le fournisseur [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB peut utiliser une interface **IStorage** implémentée par le consommateur lorsque le consommateur fournit le pointeur d’interface dans un accesseur lié à la modification des données.  
  
 Pour les types de données de valeur élevée, le fournisseur [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB vérifie les hypothèses de taille de type dans les interfaces **IRowset** et DDL. Les colonnes avec des types de données **varchar**, **nvarchar**et **varbinary** dont la taille maximale est définie sur illimité sont représentées en tant que IsLong via les ensembles de lignes de schéma et les interfaces qui retournent des types de données de colonne.  
  
 Le fournisseur [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB expose les types **varchar (max)** , **varbinary (max)** et **nvarchar (max)** en tant que DBTYPE_STR, DBTYPE_BYTES et DBTYPE_WSTR respectivement.  
  
 Pour travailler avec ces types une application possède les options suivantes :  
  
-   Lier comme type (DBTYPE_STR, DBTYPE_BYTES, DBTYPE_WSTR). Si la mémoire tampon n'est pas assez grande il s'ensuit une troncation, exactement comme pour ces types dans les précédentes versions (bien que de plus grandes valeurs soient maintenant disponibles).  
  
-   Lier comme type et spécifier également DBTYPE_BYREF.  
  
-   Lier comme DBTYPE_IUNKNOWN et utiliser la diffusion en continu.  
  
 En cas de liaison à DBTYPE_IUNKNOWN, la fonctionnalité de flux ISequentialStream est utilisée. Le fournisseur [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB prend en charge la liaison des paramètres de sortie comme DBTYPE_IUNKNOWN pour les types de données de valeur élevée afin de faciliter les scénarios dans lesquels une procédure stockée retourne ces types de données comme valeurs de retour qui seront exposées comme DBTYPE_IUNKNOWN au client.  
  
## <a name="storage-object-limitations"></a>Limitations des objets de stockage  
  
-   Le fournisseur [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB ne peut prendre en charge qu’un seul objet de stockage ouvert. Les tentatives d’ouverture de plusieurs objets de stockage (pour obtenir une référence sur plusieurs pointeurs d’interface **ISequentialStream**) retournent DBSTATUS_E_CANTCREATE.  
  
-   Dans le fournisseur de OLE DB Native Client [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], la valeur par défaut de la propriété en lecture seule DBPROP_BLOCKINGSTORAGEOBJECTS est VARIANT_TRUE. Cela signifie que si un objet de stockage est actif, certaines méthodes (autres que celles sur les objets de stockage) échouent avec E_UNEXPECTED.  
  
-   La longueur des données présentées par un objet de stockage implémenté par le consommateur doit être connue du fournisseur [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB lorsque l’accesseur de ligne qui fait référence à l’objet de stockage est créé. Le consommateur doit lier un indicateur de longueur dans la structure DBBINDING utilisée pour la création de l'accesseur.  
  
-   Si une ligne contient plus d’une valeur de données volumineuse et que DBPROP_ACCESSORDER n’est pas DBPROPVAL_AO_RANDOM, le consommateur doit utiliser un ensemble de lignes pris en charge par le curseur [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB fournisseur pour récupérer des données de ligne ou traiter toutes les valeurs de données volumineuses avant récupération des autres valeurs de ligne. Si DBPROP_ACCESSORDER est DBPROPVAL_AO_RANDOM, le fournisseur [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB met en cache tous les types de données XML en tant qu’objets BLOB (Binary Large Object) afin qu’ils soient accessibles dans n’importe quel ordre.  
  
## <a name="in-this-section"></a>Dans cette section  
  
-   [Obtention de données volumineuses](../../relational-databases/native-client-ole-db-blobs/getting-large-data.md)  
  
-   [Définition de données volumineuses](../../relational-databases/native-client-ole-db-blobs/setting-large-data.md)  
  
-   [Prise en charge de la diffusion en continu pour les paramètres de sortie BLOB](../../relational-databases/native-client-ole-db-blobs/streaming-support-for-blob-output-parameters.md)  
  
## <a name="see-also"></a>Voir aussi  
 [SQL Server Native Client &#40;OLE DB&#41; ](../../relational-databases/native-client/ole-db/sql-server-native-client-ole-db.md)   
 [Utilisation de types de valeur élevée](../../relational-databases/native-client/features/using-large-value-types.md)  
  
  

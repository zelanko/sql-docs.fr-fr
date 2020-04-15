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
author: markingmyname
ms.author: maghan
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: d0cb9751940489513f939ab8ee52728c6b75e925
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81297649"
---
# <a name="blobs-and-ole-objects"></a>Objets BLOB et OLE
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  Le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] fournisseur Native Client OLE DB expose **l’interface ISequentialStream** pour soutenir l’accès des [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] consommateurs à **ntext**, **texte**, **image**, **varchar(max)**, **nvarchar(max)**, **varbinary(max)**, et xml types de données comme des objets binaires grands (BLO). La méthode **Read** sur **ISequentialStream** permet au consommateur de récupérer un grand nombre de données en blocs maniables.  
  
 Pour obtenir un exemple illustrant cette fonctionnalité, consultez [Définir des données volumineuses &#40;OLE DB&#41;](../../relational-databases/native-client-ole-db-how-to/set-large-data-ole-db.md).  
  
 Le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] fournisseur native Client OLE DB peut utiliser une interface **IStorage** mise en œuvre par le consommateur lorsque le consommateur fournit le pointeur d’interface dans un accesseur destiné à la modification des données.  
  
 Pour les types de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] données de grande valeur, le fournisseur native Client OLE DB vérifie les hypothèses de taille de type dans les interfaces **IRowset** et DDL. Les colonnes avec **varchar,** **nvarchar**, et les types de données **varbinaires** avec la taille maximale réglée à illimitée seront représentés comme ISLONG par les rangs de schémas et les interfaces retour des types de données de colonne.  
  
 Le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] fournisseur native De DB OLE de client expose les types **varchar(max),** **varbinaire(max)** et **nvarchar(max)** comme DBTYPE_STR, DBTYPE_BYTES et DBTYPE_WSTR respectivement.  
  
 Pour travailler avec ces types une application possède les options suivantes :  
  
-   Lier comme type (DBTYPE_STR, DBTYPE_BYTES, DBTYPE_WSTR). Si la mémoire tampon n'est pas assez grande il s'ensuit une troncation, exactement comme pour ces types dans les précédentes versions (bien que de plus grandes valeurs soient maintenant disponibles).  
  
-   Lier comme type et spécifier également DBTYPE_BYREF.  
  
-   Lier comme DBTYPE_IUNKNOWN et utiliser la diffusion en continu.  
  
 En cas de liaison à DBTYPE_IUNKNOWN, la fonctionnalité de flux ISequentialStream est utilisée. Le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] fournisseur native Client OLE DB prend en charge les paramètres de sortie contraignants comme DBTYPE_IUNKNOWN pour les types de données de grande valeur afin de faciliter les scénarios où une procédure stockée renvoie ces types de données comme des valeurs de retour qui seront exposées comme DBTYPE_IUNKNOWN au client.  
  
## <a name="storage-object-limitations"></a>Limitations des objets de stockage  
  
-   Le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] fournisseur native Client OLE DB ne peut prendre en charge qu’un seul objet de stockage ouvert. Les tentatives d’ouverture de plusieurs objets de stockage (pour obtenir une référence sur plusieurs pointeurs d’interface **ISequentialStream**) retournent DBSTATUS_E_CANTCREATE.  
  
-   Dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] le fournisseur native De DB OLE de client, la valeur par défaut de la propriété de lecture-seulement de DBPROP_BLOCKINGSTORAGEOBJECTS est VARIANT_TRUE. Cela signifie que si un objet de stockage est actif, certaines méthodes (autres que celles sur les objets de stockage) échouent avec E_UNEXPECTED.  
  
-   La longueur des données présentées par un objet de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] stockage mis en œuvre par le consommateur doit être rendue compte du fournisseur de DB OLE native client lorsque l’accesseur de ligne qui fait référence à l’objet de stockage est créé. Le consommateur doit lier un indicateur de longueur dans la structure DBBINDING utilisée pour la création de l'accesseur.  
  
-   Si une ligne contient plus d’une valeur de données importante et DBPROP_ACCESSORDER n’est [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] pas DBPROPVAL_AO_RANDOM, le consommateur doit soit utiliser un ensemble de ligne supporté par le curseur du fournisseur OLE DB pour récupérer les données de la ligne ou traiter toutes les grandes valeurs de données avant de récupérer d’autres valeurs de ligne. Si DBPROP_ACCESSORDER est DBPROPVAL_AO_RANDOM, le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] fournisseur Native Client OLE DB cache tous les types de données xml comme de grands objets binaires (BLOB) afin qu’ils puissent être consultés dans n’importe quel ordre.  
  
## <a name="in-this-section"></a>Dans cette section  
  
-   [Obtention de données volumineuses](../../relational-databases/native-client-ole-db-blobs/getting-large-data.md)  
  
-   [Définition de données volumineuses](../../relational-databases/native-client-ole-db-blobs/setting-large-data.md)  
  
-   [Prise en charge de la diffusion en continu pour les paramètres de sortie BLOB](../../relational-databases/native-client-ole-db-blobs/streaming-support-for-blob-output-parameters.md)  
  
## <a name="see-also"></a>Voir aussi  
 [SQL Server Native Client &#40;OLE DB&#41;](../../relational-databases/native-client/ole-db/sql-server-native-client-ole-db.md)   
 [Utilisation de types de valeur élevée](../../relational-databases/native-client/features/using-large-value-types.md)  
  
  

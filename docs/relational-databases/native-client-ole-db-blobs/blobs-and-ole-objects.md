---
title: Objets BLOB et OLE | Microsoft Docs
ms.custom: ''
ms.date: 03/16/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.suite: sql
ms.technology: native-client
ms.tgt_pltfrm: ''
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
manager: craigg
monikerRange: '>= aps-pdw-2016 || = azuresqldb-current || = azure-sqldw-latest || >= sql-server-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: 80629d81a9212801e65e272f5790b0cc57a11103
ms.sourcegitcommit: f8ce92a2f935616339965d140e00298b1f8355d7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/03/2018
ms.locfileid: "37428738"
---
# <a name="blobs-and-ole-objects"></a>Objets BLOB et OLE
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

  Le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] fournisseur de OLE DB Native Client expose la **ISequentialStream** interface pour prendre en charge d’accès du consommateur à [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] **ntext**, **texte**, **image**, **varchar (max)**, **nvarchar (max)**, **varbinary (max)**, et les types de données xml comme objets (objets BLOB ). Le **en lecture** méthode sur **ISequentialStream** permet au consommateur de récupérer le volume de données en segments gérables.  
  
 Pour obtenir un exemple illustrant cette fonctionnalité, consultez [définir les données volumineuses &#40;OLE DB&#41;](../../relational-databases/native-client-ole-db-how-to/set-large-data-ole-db.md).  
  
 Le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] fournisseur de OLE DB Native Client peut utiliser un objet implémenté par le consommateur **IStorage** interface lorsque le consommateur fournit le pointeur d’interface dans un accesseur lié pour la modification des données.  
  
 Pour les types de données de valeur élevée, le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] fournisseur de OLE DB Native Client vérifie les hypothèses de taille de type dans **IRowset** et interfaces DDL. Colonnes avec **varchar**, **nvarchar**, et **varbinary** des types de données avec une taille maximale illimitée sont représentées comme ISLONG via les ensembles de lignes de schéma et les interfaces retour des types de données de colonne.  
  
 Le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] fournisseur de OLE DB Native Client expose la **varchar (max)**, **varbinary (max)** et **nvarchar (max)** types en tant que DBTYPE_STR, DBTYPE_BYTES et DBTYPE_ WSTR respectivement.  
  
 Pour travailler avec ces types une application possède les options suivantes :  
  
-   Lier comme type (DBTYPE_STR, DBTYPE_BYTES, DBTYPE_WSTR). Si la mémoire tampon n'est pas assez grande il s'ensuit une troncation, exactement comme pour ces types dans les précédentes versions (bien que de plus grandes valeurs soient maintenant disponibles).  
  
-   Lier comme type et spécifier également DBTYPE_BYREF.  
  
-   Lier comme DBTYPE_IUNKNOWN et utiliser la diffusion en continu.  
  
 En cas de liaison à DBTYPE_IUNKNOWN, la fonctionnalité de flux ISequentialStream est utilisée. Le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Client fournisseur OLE DB natif prend en charge la liaison des paramètres de sortie en tant que DBTYPE_IUNKNOWN pour les types de données de valeur élevée afin de simplifier les scénarios où une procédure stockée retourne ces données types comme valeurs de retour qui seront exposées en tant que DBTYPE_IUNKNOWN pour le client.  
  
## <a name="storage-object-limitations"></a>Limitations des objets de stockage  
  
-   Le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Client fournisseur OLE DB Native peut prendre en charge uniquement un objet de stockage ouvert unique. Tente d’ouvrir plusieurs objets de stockage (pour obtenir une référence sur plusieurs **ISequentialStream** pointeur d’interface) retournent DBSTATUS_E_CANTCREATE.  
  
-   Dans le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] fournisseur OLE DB Native Client, la valeur par défaut de la propriété en lecture seule de DBPROP_BLOCKINGSTORAGEOBJECTS est VARIANT_TRUE. Cela signifie que si un objet de stockage est actif, certaines méthodes (autres que celles sur les objets de stockage) échouent avec E_UNEXPECTED.  
  
-   La longueur des données présentées par un objet de stockage implémenté par le consommateur doit avoir connaissance de la [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] fournisseur Native Client OLE DB lors de la création de l’accesseur de ligne qui fait référence à l’objet de stockage. Le consommateur doit lier un indicateur de longueur dans la structure DBBINDING utilisée pour la création de l'accesseur.  
  
-   Si une ligne contient plus d’une valeur unique de données volumineux et que DBPROP_ACCESSORDER n’est pas DBPROPVAL_AO_RANDOM, le consommateur doit utiliser un [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB fournisseur pris en charge de curseur ensemble de lignes à récupérer des données de ligne ou traiter les données de toutes les grandes valeurs avant récupération des autres valeurs de ligne. Si DBPROP_ACCESSORDER a pour valeur DBPROPVAL_AO_RANDOM, le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Client fournisseur OLE DB natif met en cache tous les types de données xml en tant qu’objets binaires volumineux (BLOB) afin qu’il est accessible dans n’importe quel ordre.  
  
## <a name="in-this-section"></a>Dans cette section  
  
-   [Obtention de données volumineuses](../../relational-databases/native-client-ole-db-blobs/getting-large-data.md)  
  
-   [Définition de données volumineuses](../../relational-databases/native-client-ole-db-blobs/setting-large-data.md)  
  
-   [Prise en charge de la diffusion en continu pour les paramètres de sortie BLOB](../../relational-databases/native-client-ole-db-blobs/streaming-support-for-blob-output-parameters.md)  
  
## <a name="see-also"></a>Voir aussi  
 [SQL Server Native Client &#40;OLE DB&#41;](../../relational-databases/native-client/ole-db/sql-server-native-client-ole-db.md)   
 [Utilisation de types de valeur élevée](../../relational-databases/native-client/features/using-large-value-types.md)  
  
  

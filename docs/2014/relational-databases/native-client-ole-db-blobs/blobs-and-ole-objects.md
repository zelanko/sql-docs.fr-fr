---
title: Objets BLOB et OLE | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
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
manager: craigg
ms.openlocfilehash: e459682da63bac8359fa8310233c234e456f4e5b
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/26/2020
ms.locfileid: "63195214"
---
# <a name="blobs-and-ole-objects"></a>Objets BLOB et OLE
  Le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] fournisseur OLE DB Native Client expose l’interface **ISequentialStream** pour prendre en charge l' [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] accès des consommateurs aux types de données **ntext**, **Text**, **image**, **varchar (max)**, **nvarchar (max)**, **varbinary (max)** et XML en tant qu’objets BLOB (Binary Large Object). La méthode **Read** sur **ISequentialStream** permet au consommateur de récupérer un grand nombre de données en blocs maniables.  
  
 Pour obtenir un exemple illustrant cette fonctionnalité, consultez [Définir des données volumineuses &#40;OLE DB&#41;](../native-client-ole-db-how-to/set-large-data-ole-db.md).  
  
 Le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] fournisseur de OLE DB Native Client peut utiliser une interface **IStorage** implémentée par le consommateur lorsque le consommateur fournit le pointeur d’interface dans un accesseur lié pour la modification des données.  
  
 Pour les types de données de valeur [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] élevée, le fournisseur de OLE DB Native Client vérifie les hypothèses de taille de type dans les interfaces **IRowset** et DDL. Les colonnes avec des types de données **varchar**, **nvarchar**et **varbinary** dont la taille maximale est définie sur illimité sont représentées en tant que IsLong via les ensembles de lignes de schéma et les interfaces qui retournent des types de données de colonne.  
  
 Le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] fournisseur OLE DB Native Client expose les types **varchar (max)**, **varbinary (max)** et **nvarchar (max)** comme DBTYPE_STR, DBTYPE_BYTES et DBTYPE_WSTR respectivement.  
  
 Pour travailler avec ces types une application possède les options suivantes :  
  
-   Lier comme type (DBTYPE_STR, DBTYPE_BYTES, DBTYPE_WSTR). Si la mémoire tampon n'est pas assez grande il s'ensuit une troncation, exactement comme pour ces types dans les précédentes versions (bien que de plus grandes valeurs soient maintenant disponibles).  
  
-   Lier comme type et spécifier également DBTYPE_BYREF.  
  
-   Lier comme DBTYPE_IUNKNOWN et utiliser la diffusion en continu.  
  
 En cas de liaison à DBTYPE_IUNKNOWN, la fonctionnalité de flux ISequentialStream est utilisée. Le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] fournisseur OLE DB Native Client prend en charge la liaison des paramètres de sortie comme DBTYPE_IUNKNOWN pour les types de données de valeur élevée afin de faciliter les scénarios dans lesquels une procédure stockée retourne ces types de données comme valeurs de retour qui seront exposées comme DBTYPE_IUNKNOWN au client.  
  
## <a name="storage-object-limitations"></a>Limitations des objets de stockage  
  
-   Le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] fournisseur de OLE DB Native Client ne peut prendre en charge qu’un seul objet de stockage ouvert. Les tentatives d’ouverture de plusieurs objets de stockage (pour obtenir une référence sur plusieurs pointeurs d’interface **ISequentialStream**) retournent DBSTATUS_E_CANTCREATE.  
  
-   Dans le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] fournisseur de OLE DB Native Client, la valeur par défaut de la propriété DBPROP_BLOCKINGSTORAGEOBJECTS en lecture seule est VARIANT_TRUE. Cela signifie que si un objet de stockage est actif, certaines méthodes (autres que celles sur les objets de stockage) échouent avec E_UNEXPECTED.  
  
-   La longueur des données présentées par un objet de stockage implémenté par le consommateur doit être connue du [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] fournisseur OLE DB Native Client lorsque l’accesseur de ligne qui fait référence à l’objet de stockage est créé. Le consommateur doit lier un indicateur de longueur dans la structure DBBINDING utilisée pour la création de l'accesseur.  
  
-   Si une ligne contient plus d’une valeur de données volumineuse et que DBPROP_ACCESSORDER n’est pas DBPROPVAL_AO_RANDOM, le consommateur doit utiliser [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] un ensemble de lignes pris en charge par le curseur du fournisseur Native Client OLE DB pour récupérer des données de ligne ou traiter toutes les valeurs de données volumineuses avant de récupérer d’autres valeurs de ligne. Si DBPROP_ACCESSORDER est DBPROPVAL_AO_RANDOM, le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] fournisseur de OLE DB Native Client met en cache tous les types de données XML en tant qu’objets BLOB (Binary Large Object) afin qu’ils soient accessibles dans n’importe quel ordre.  
  
## <a name="in-this-section"></a>Dans cette section  
  
-   [Obtention de données volumineuses](getting-large-data.md)  
  
-   [Définition de données volumineuses](setting-large-data.md)  
  
-   [Prise en charge de la diffusion en continu pour les paramètres de sortie BLOB](streaming-support-for-blob-output-parameters.md)  
  
## <a name="see-also"></a>Voir aussi  
 [SQL Server Native Client &#40;OLE DB&#41;](../native-client/ole-db/sql-server-native-client-ole-db.md)   
 [Utilisation de types de valeur élevée](../native-client/features/using-large-value-types.md)  
  
  

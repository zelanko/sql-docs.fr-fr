---
title: IRowsetFastLoad::InsertRow (OLE DB) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
apiname:
- IRowsetFastLoad::InsertRow (OLE DB)
apitype: COM
helpviewer_keywords:
- InsertRow method
ms.assetid: 594d3461-34d2-41e7-8ad4-bd2753601ab6
author: MightyPen
ms.author: genemi
manager: craigg
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: a29b8f3dd01a39079f1eec86410ba5bc2ddcc738
ms.sourcegitcommit: 9c6a37175296144464ffea815f371c024fce7032
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/15/2018
ms.locfileid: "51667849"
---
# <a name="irowsetfastloadinsertrow-ole-db"></a>IRowsetFastLoad::InsertRow (OLE DB)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

  Ajoute une ligne à l'ensemble de lignes de copie en bloc. Pour obtenir des exemples, consultez [en bloc copie de données en bloc avec IRowsetFastLoad &#40;OLE DB&#41; ](../../relational-databases/native-client-ole-db-how-to/bulk-copy-data-using-irowsetfastload-ole-db.md) et [envoyer les données BLOB à SQL SERVER à l’aide de IROWSETFASTLOAD et ISEQUENTIALSTREAM &#40;OLE DB&#41;](../../relational-databases/native-client-ole-db-how-to/send-blob-data-to-sql-server-using-irowsetfastload-and-isequentialstream-ole-db.md).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
HRESULT InsertRow(  
      HACCESSOR hAccessor,  
      void* pData);  
```  
  
## <a name="arguments"></a>Arguments  
 *hAccessor*[in]  
 Handle de l'accesseur définissant les données de ligne pour la copie en bloc. L'accesseur référencé est un accesseur de ligne, liant la mémoire dont le consommateur est propriétaire et qui contient les valeurs des données.  
  
 *pData*[in]  
 Pointeur vers la mémoire dont le consommateur est propriétaire et qui contient les valeurs des données. Pour plus d'informations, consultez [Structures DBBINDING](https://go.microsoft.com/fwlink/?LinkId=65955).  
  
## <a name="return-code-values"></a>Valeurs des codes de retour  
 Cette méthode signale les erreurs en attribuant à la propriété Nombre de l'objet Err global l'une des valeurs du tableau suivant.  
 S_OK Les valeurs d'état liées de toutes les colonnes ont la valeur DBSTATUS_S_OK ou DBSTATUS_S_NULL.  
  
 E_FAIL  
 Une erreur s'est produite. Les informations sur l'erreur sont disponibles depuis les interfaces d'erreur de l'ensemble de lignes.  
  
 E_INVALIDARG  
 L'argument *pData* a été défini sur un pointeur NULL.  
  
 E_OUTOFMEMORY  
 SQLNCLI11 ne pouvait pas allouer la mémoire suffisante pour compléter la demande.  
  
 E_UNEXPECTED  
 La méthode a été appelée sur un ensemble de lignes de copie en bloc précédemment invalidé par la méthode [IRowsetFastLoad::Commit](../../relational-databases/native-client-ole-db-interfaces/irowsetfastload-commit-ole-db.md) .  
  
 DB_E_BADACCESSORHANDLE  
 L'argument *hAccessor* fourni par le consommateur n'était pas valide.  
  
 DB_E_BADACCESSORTYPE  
 L'accesseur spécifié n'était pas un accesseur de ligne ou ne spécifiait pas une mémoire dont le consommateur était propriétaire.  
  
## <a name="remarks"></a>Notes  
 Une erreur lors de la conversion des données du consommateur en type de données [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] pour une colonne provoque un retour E_FAIL du fournisseur OLE DB [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client. Les données peuvent être transmises à [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] sur n'importe quelle méthode **InsertRow** ou uniquement sur la méthode **Commit** . L'application du consommateur peut appeler la méthode **InsertRow** plusieurs fois avec des données erronées avant de recevoir le message qu'une erreur de conversion de type de données s'est produite. Comme la méthode **Commit** garantit que toutes les données sont spécifiées correctement par le consommateur, celui-ci peut utiliser la méthode **Commit** de façon appropriée pour valider les données comme nécessaire.  
  
 Les ensembles de lignes de la copie en bloc du fournisseur OLE DB [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client sont en écriture seule. Le fournisseur OLE DB [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client n'expose aucune méthode qui autorise l'interrogation de l'ensemble de lignes par le consommateur. Pour terminer le traitement, le consommateur peut libérer sa référence sur l’interface [IRowsetFastLoad](../../relational-databases/native-client-ole-db-interfaces/irowsetfastload-ole-db.md) sans appeler la méthode **Commit**. Il n'existe pas d'utilitaires permettant d'accéder à une ligne insérée par le consommateur dans l'ensemble de lignes et de modifier ses valeurs, ou de la supprimer individuellement de l'ensemble de lignes.  
  
 Les lignes copiées en bloc sont mises en forme sur le serveur pour [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Le format de ligne est affecté par les options qui ont pu être définies pour la connexion ou la session, telles que ANSI_PADDING. Cette option est activée par défaut pour toute connexion établie à travers le fournisseur OLE DB [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client.  
  
## <a name="see-also"></a>Voir aussi  
 [IRowsetFastLoad &#40;OLE DB&#41;](../../relational-databases/native-client-ole-db-interfaces/irowsetfastload-ole-db.md)  
  
  

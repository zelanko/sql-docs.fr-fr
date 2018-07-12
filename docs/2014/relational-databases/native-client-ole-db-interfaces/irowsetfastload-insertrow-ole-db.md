---
title: IRowsetFastLoad::InsertRow (OLE DB) | Microsoft Docs
ms.custom: ''
ms.date: 03/09/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: native-client
ms.tgt_pltfrm: ''
ms.topic: reference
api_name:
- IRowsetFastLoad::InsertRow (OLE DB)
topic_type:
- apiref
helpviewer_keywords:
- InsertRow method
ms.assetid: 594d3461-34d2-41e7-8ad4-bd2753601ab6
caps.latest.revision: 36
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 7eb8d5612ef4c4ab4b8bee88e81a75133f9b8ede
ms.sourcegitcommit: f8ce92a2f935616339965d140e00298b1f8355d7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/03/2018
ms.locfileid: "37430838"
---
# <a name="irowsetfastloadinsertrow-ole-db"></a>IRowsetFastLoad::InsertRow (OLE DB)
  Ajoute une ligne à l'ensemble de lignes de copie en bloc. Pour obtenir des exemples, consultez [en bloc copie de données en bloc avec IRowsetFastLoad &#40;OLE DB&#41; ](../native-client-ole-db-how-to/bulk-copy-data-using-irowsetfastload-ole-db.md) et [envoyer les données BLOB à SQL SERVER à l’aide de IROWSETFASTLOAD et ISEQUENTIALSTREAM &#40;OLE DB&#41;](../native-client-ole-db-how-to/send-blob-data-to-sql-server-using-irowsetfastload-and-isequentialstream-ole-db.md).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
HRESULT InsertRow(  
HACCESSOR  
hAccessor  
,  
void*  
pData  
);  
  
```  
  
## <a name="arguments"></a>Arguments  
 *hAccessor*[in]  
 Handle de l'accesseur définissant les données de ligne pour la copie en bloc. L'accesseur référencé est un accesseur de ligne, liant la mémoire dont le consommateur est propriétaire et qui contient les valeurs des données.  
  
 *pData*[in]  
 Pointeur vers la mémoire dont le consommateur est propriétaire et qui contient les valeurs des données. Pour plus d'informations, consultez [Structures DBBINDING](http://go.microsoft.com/fwlink/?LinkId=65955).  
  
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
 La méthode a été appelée sur un ensemble de lignes de copie en bloc précédemment invalidé par la [IRowsetFastLoad::Commit](irowsetfastload-commit-ole-db.md) (méthode).  
  
 DB_E_BADACCESSORHANDLE  
 L'argument *hAccessor* fourni par le consommateur n'était pas valide.  
  
 DB_E_BADACCESSORTYPE  
 L'accesseur spécifié n'était pas un accesseur de ligne ou ne spécifiait pas une mémoire dont le consommateur était propriétaire.  
  
## <a name="remarks"></a>Notes  
 Une erreur de conversion de données du consommateur la [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] type de données pour une colonne provoque un retour E_FAIL du [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Client fournisseur OLE DB natif. Données peuvent être transmises à [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] sur n’importe quel **InsertRow** méthode ou uniquement sur **valider** (méthode). L'application du consommateur peut appeler la méthode **InsertRow** plusieurs fois avec des données erronées avant de recevoir le message qu'une erreur de conversion de type de données s'est produite. Comme la méthode **Commit** garantit que toutes les données sont spécifiées correctement par le consommateur, celui-ci peut utiliser la méthode **Commit** de façon appropriée pour valider les données comme nécessaire.  
  
 Le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ensembles de lignes OLE DB Native Client fournisseur en bloc copie sont en écriture seule. Le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Client fournisseur OLE DB natif n’expose aucune méthode qui autorise l’interrogation de consommateur de l’ensemble de lignes. Pour terminer le traitement, le consommateur peut libérer sa référence sur le [IRowsetFastLoad](irowsetfastload-ole-db.md) interface sans appeler le **valider** (méthode). Il n'existe pas d'utilitaires permettant d'accéder à une ligne insérée par le consommateur dans l'ensemble de lignes et de modifier ses valeurs, ou de la supprimer individuellement de l'ensemble de lignes.  
  
 Les lignes copiées en bloc sont mises en forme sur le serveur pour [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Le format de ligne est affecté par les options qui ont pu être définies pour la connexion ou la session, telles que ANSI_PADDING. Cette option est définie sur par défaut pour toute connexion établie via la [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Client fournisseur OLE DB natif.  
  
## <a name="see-also"></a>Voir aussi  
 [IRowsetFastLoad &#40;OLE DB&#41;](irowsetfastload-ole-db.md)  
  
  

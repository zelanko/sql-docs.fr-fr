---
title: IRowsetFastLoad::Commit (pilote OLE DB) | Microsoft Docs
description: IRowsetFastLoad::Commit (OLE DB)
ms.custom: ''
ms.date: 06/14/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: connectivity
ms.topic: reference
apiname:
- IRowsetFastLoad::Commit (OLE DB)
apitype: COM
helpviewer_keywords:
- Commit method
author: pmasl
ms.author: pelopes
ms.openlocfilehash: 6c932947a77d2170dd1e92c47c19f5ff3959cba9
ms.sourcegitcommit: 216f377451e53874718ae1645a2611cdb198808a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/28/2020
ms.locfileid: "87244449"
---
# <a name="irowsetfastloadcommit-ole-db"></a>IRowsetFastLoad::Commit (OLE DB)
[!INCLUDE [SQL Server](../../../includes/applies-to-version/sql-asdb-asdbmi-asa-pdw.md)]

[!INCLUDE[Driver_OLEDB_Download](../../../includes/driver_oledb_download.md)]

  Marque la fin d'un lot de lignes insérées et écrit les lignes dans la table [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] . Pour obtenir des exemples, consultez [Copier des données en bloc avec IRowsetFastLoad &#40;OLE DB&#41;](../../oledb/ole-db-how-to/bulk-copy-data-using-irowsetfastload-ole-db.md) et [Envoyer des données BLOB vers SQL Server en utilisant IROWSETFASTLOAD et ISEQUENTIALSTREAM &#40;OLE DB&#41;](../../oledb/ole-db-how-to/send-blob-data-to-sql-server-using-irowsetfastload-and-isequentialstream-ole-db.md).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
HRESULT Commit(  
      BOOL fDone);  
```  
  
## <a name="arguments"></a>Arguments  
 *fDone*[in]  
 Si FALSE, l'ensemble de lignes conserve la validation et peut être utilisé par le consommateur pour l'insertion de ligne supplémentaire. Si TRUE, l'ensemble de lignes perd la validation et aucune insertion supplémentaire ne peut être effectuée par le consommateur.  
  
## <a name="return-code-values"></a>Codet de retour  
 S_OK  
 La méthode a réussi et toutes les données insérées ont été écrites dans la table [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].  
  
 E_FAIL  
 Une erreur spécifique au fournisseur s'est produite. Extrayez les informations sur l'erreur pour le texte d'erreur spécifique à partir du fournisseur.  
  
 E_UNEXPECTED  
 La méthode a été appelée sur un ensemble de lignes de copie en bloc précédemment invalidé par la méthode **IRowsetFastLoad::Commit**.  
  
## <a name="remarks"></a>Notes  
 Un ensemble de lignes de copie en bloc d’OLE DB Driver pour SQL Server se comporte comme un ensemble de lignes en mode de mise à jour retardée. Quand l’utilisateur insère des données de ligne dans l’ensemble de lignes, les lignes insérées sont traitées de la même façon que les insertions en attente sur un ensemble de lignes prenant en charge **IRowsetUpdate**.  
  
 Le consommateur doit appeler la méthode **Commit** sur l’ensemble de lignes de copie en bloc pour écrire les lignes insérées dans la table [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], de la même façon que la méthode **IRowsetUpdate::Update** est utilisée pour soumettre des lignes en attente à une instance de SQL Server.  
  
 Si le consommateur libère sa référence sur l’ensemble de lignes de copie en bloc sans appeler la méthode **Commit**, toutes les lignes insérées non écrites précédemment sont perdues.  
  
 Le consommateur peut insérer des lignes par lot en appelant la méthode **Commit** avec l’argument *fDone* défini sur FALSE. Quand *fDone* est défini sur TRUE, l’ensemble de lignes devient non valide. Un ensemble de lignes de copie en bloc non valide prend en charge seulement l’interface **ISupportErrorInfo** et la méthode **IRowsetFastLoad::Release**.  
  
## <a name="see-also"></a>Voir aussi  
 [IRowsetFastLoad &#40;OLE DB&#41;](../../oledb/ole-db-interfaces/irowsetfastload-ole-db.md)  
  
  

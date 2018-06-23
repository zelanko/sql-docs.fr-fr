---
title: IRowsetFastLoad::Commit (OLE DB) | Documents Microsoft
ms.custom: ''
ms.date: 03/09/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
api_name:
- IRowsetFastLoad::Commit (OLE DB)
topic_type:
- apiref
helpviewer_keywords:
- Commit method
ms.assetid: 19de9128-b91a-4626-847f-af721edaa24e
caps.latest.revision: 34
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 553f3aaaceae23944ae9b2d0be7d8129a22c0dd1
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36052172"
---
# <a name="irowsetfastloadcommit-ole-db"></a>IRowsetFastLoad::Commit (OLE DB)
  Marque la fin d'un lot de lignes insérées et écrit les lignes dans la table [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Pour obtenir des exemples, consultez [en bloc copie de données en bloc avec IRowsetFastLoad &#40;OLE DB&#41; ](irowsetfastload-ole-db.md) et [envoyer les données BLOB à SQL SERVER à l’aide de IROWSETFASTLOAD et ISEQUENTIALSTREAM &#40;OLE DB&#41;](../native-client-ole-db-how-to/send-blob-data-to-sql-server-using-irowsetfastload-and-isequentialstream-ole-db.md).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
HRESULT Commit(  
BOOL   
fDone  
);  
  
```  
  
## <a name="arguments"></a>Arguments  
 *fDone*[in]  
 Si FALSE, l'ensemble de lignes conserve la validation et peut être utilisé par le consommateur pour l'insertion de ligne supplémentaire. Si TRUE, l'ensemble de lignes perd la validation et aucune insertion supplémentaire ne peut être effectuée par le consommateur.  
  
## <a name="return-code-values"></a>Valeurs des codes de retour  
 Cette méthode signale les erreurs en attribuant à la propriété Nombre de l'objet Err global l'une des valeurs du tableau suivant.  
 La méthode a réussi et toutes les données insérées ont été écrites dans la table [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 E_FAIL  
 Une erreur spécifique au fournisseur s'est produite. Extrayez les informations sur l'erreur pour le texte d'erreur spécifique à partir du fournisseur.  
  
 E_UNEXPECTED  
 La méthode a été appelée sur un ensemble de lignes de copie en bloc précédemment invalidé par le **IRowsetFastLoad::Commit** (méthode).  
  
## <a name="remarks"></a>Notes  
 A [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ensemble de lignes OLE DB Native Client fournisseur bulk copy se comporte comme un ensemble de lignes en mode de mise à jour différée. Comme l’utilisateur insère des données de ligne via l’ensemble de lignes, les lignes insérées sont traitées de la même manière qu’insertions en attente sur un ensemble de lignes prenant en charge **IRowsetUpdate**.  
  
 Le consommateur doit appeler le **valider** méthode sur l’ensemble de lignes de copie en bloc pour écrire des lignes insérées dans la [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] table dans la même façon que les **IRowsetUpdate::Update** méthode est utilisée pour envoyer des lignes en attente à un instance de SQL Server.  
  
 Si le consommateur libère sa référence à l’ensemble de lignes de copie en bloc sans appeler le **valider** méthode insérée de toutes les lignes non écrites précédemment sont perdues.  
  
 Le consommateur peut traiter par lot des lignes insérées en appelant le **valider** méthode avec la *fDone* argument a la valeur FALSE. Lorsque *fDone*est définie sur TRUE, l’ensemble de lignes devient non valide. Un ensemble de lignes de copie en bloc non valide prend uniquement en charge la **ISupportErrorInfo** interface et **IRowsetFastLoad::Release** (méthode).  
  
## <a name="see-also"></a>Voir aussi  
 [IRowsetFastLoad &#40;OLE DB&#41;](irowsetfastload-ole-db.md)  
  
  
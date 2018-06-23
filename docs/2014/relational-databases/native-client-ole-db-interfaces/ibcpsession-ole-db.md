---
title: IBCPSession (OLE DB) | Documents Microsoft
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
topic_type:
- apiref
helpviewer_keywords:
- IBCPSession interface
ms.assetid: 00d0311f-8b71-4ad6-824d-0e89119347a3
caps.latest.revision: 27
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 7ccd40edb997ae3e45fd705a8a6543c8f3895b6f
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36143881"
---
# <a name="ibcpsession-ole-db"></a>IBCPSession (OLE DB)
  Le **IBCPSession** interface expose la prise en charge de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] les opérations de copie en bloc basées sur le fichier. Le **IBCPSession** interface est exposée dans les [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] fournisseur OLE DB Native Client sous le même niveau que Sessions. Dans le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Client fournisseur OLE DB natif, les objets de source de données sont des fabriques pour les objets de Session, et les opérations de copie en bloc sont spécifiées dans la propriété de connexion SSPROP_ENABLEBULKCOPY. De plus, la propriété SSPROP_ENABLEFASTLOAD doit avoir la valeur vrai.  
  
 L'appel de la méthode **IDBCreateSession::CreateSession** provoquera alors la création d'un objet **BulkCopySession** . Toutes les méthodes de copie en bloc basées sur des fichiers exposées par le biais de l'objet **IBCPSession** peuvent ensuite être appelées avec des signatures presque semblables sur l'interface **IBCPSession** de cet objet **IBCPSession** .  
  
> [!NOTE]  
>  Le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] fournisseur de OLE DB Native Client prend en charge les opérations de copie en bloc basées sur mémoire par le biais du [IRowsetFastLoad](irowsetfastload-ole-db.md) interface.  
  
 Pour plus d’informations sur l’utilisation de la [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] fournisseur OLE DB Native Client pour les opérations de copie en bloc, consultez [effectuant des opérations de copie en bloc](../native-client/features/performing-bulk-copy-operations.md).  
  
 Pour obtenir un exemple montrant comment utiliser les **IBCPSession** l’interface, consultez [IBCPSession::BCPDone &#40;OLE DB&#41;](ibcpsession-bcpdone-ole-db.md).  
  
## <a name="in-this-section"></a>Dans cette section  
  
|Méthode|Description|  
|------------|-----------------|  
|[IBCPSession::BCPColFmt &#40;OLE DB&#41;](ibcpsession-bcpcolfmt-ole-db.md)|Crée une liaison entre des variables de programme et des colonnes [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].|  
|[IBCPSession::BCPColumns &#40;OLE DB&#41;](ibcpsession-bcpcolumns-ole-db.md)|Définit le nombre de champs qui doivent être liés aux colonnes dans une table [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].|  
|[IBCPSession::BCPControl &#40;OLE DB&#41;](ibcpsession-bcpcontrol-ole-db.md)|Définit les options pour une opération de copie en bloc.|  
|[IBCPSession::BCPDone &#40;OLE DB&#41;](ibcpsession-bcpdone-ole-db.md)|Valide les lignes restantes à envoyer à [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].|  
|[IBCPSession::BCPExec &#40;OLE DB&#41;](ibcpsession-bcpexec-ole-db.md)|Effectue l'opération de copie en bloc.|  
|[IBCPSession::BCPInit &#40;OLE DB&#41;](ibcpsession-bcpinit-ole-db.md)|Initialise la structure de copie en bloc, effectue une vérification des erreurs, vérifie que les données et les noms de fichiers de format sont corrects, puis les ouvre.|  
|[IBCPSession::BCPReadFmt &#40;OLE DB&#41;](ibcpsession-bcpreadfmt-ole-db.md)|Lit les informations de format pour chaque colonne à partir du fichier de format.|  
|[IBCPSession::BCPWriteFmt &#40;OLE DB&#41;](ibcpsession-bcpwritefmt-ole-db.md)|Écrit les informations de format pour chaque colonne dans le fichier de format.|  
  
## <a name="see-also"></a>Voir aussi  
 [Interfaces &#40;OLE DB&#41;](../../database-engine/dev-guide/interfaces-ole-db.md)  
  
  
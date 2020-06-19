---
title: IBCPSession (OLE DB) | Microsoft Docs
ms.custom: ''
ms.date: 03/09/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
topic_type:
- apiref
helpviewer_keywords:
- IBCPSession interface
ms.assetid: 00d0311f-8b71-4ad6-824d-0e89119347a3
author: rothja
ms.author: jroth
ms.openlocfilehash: 3c6e0323a38fb6af9d242cca9c4aa9135ee99f37
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/18/2020
ms.locfileid: "85047955"
---
# <a name="ibcpsession-ole-db"></a>IBCPSession (OLE DB)
  L’interface **IBCPSession** expose la prise en charge des opérations de copie en bloc basées sur des fichiers [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. L'interface **IBCPSession** est exposée dans le fournisseur OLE DB [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client sous le même niveau que Sessions. Dans le fournisseur OLE DB [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client, les objets sources de données sont des fabriques pour les objets Session et les opérations de copie en bloc sont spécifiées dans la propriété de connexion SSPROP_ENABLEBULKCOPY. De plus, la propriété SSPROP_ENABLEFASTLOAD doit avoir la valeur vrai.  
  
 L'appel de la méthode **IDBCreateSession::CreateSession** provoquera alors la création d'un objet **BulkCopySession** . Toutes les méthodes de copie en bloc basées sur des fichiers exposées par le biais de l'objet **IBCPSession** peuvent ensuite être appelées avec des signatures presque semblables sur l'interface **IBCPSession** de cet objet **IBCPSession** .  
  
> [!NOTE]  
>  Le fournisseur OLE DB [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client prend en charge les opérations de copie en bloc basées sur mémoire par le biais de l'interface [IRowsetFastLoad](irowsetfastload-ole-db.md) .  
  
 Pour plus d’informations sur l’utilisation du [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] fournisseur de OLE DB Native Client pour les opérations de copie en bloc, consultez [exécution d’opérations de copie en bloc](../native-client/features/performing-bulk-copy-operations.md).  
  
 Pour obtenir un exemple qui indique comment utiliser l'interface **IBCPSession**, consultez [IBCPSession::BCPDone &#40;OLE DB&#41;](ibcpsession-bcpdone-ole-db.md).  
  
## <a name="in-this-section"></a>Dans cette section  
  
|Méthode|Description|  
|------------|-----------------|  
|[IBCPSession::BCPColFmt &#40;OLE DB&#41;](ibcpsession-bcpcolfmt-ole-db.md)|Crée une liaison entre des variables de programme et des colonnes [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .|  
|[IBCPSession::BCPColumns &#40;OLE DB&#41;](ibcpsession-bcpcolumns-ole-db.md)|Définit le nombre de champs qui doivent être liés aux colonnes dans une table [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .|  
|[IBCPSession::BCPControl &#40;OLE DB&#41;](ibcpsession-bcpcontrol-ole-db.md)|Définit les options pour une opération de copie en bloc.|  
|[IBCPSession::BCPDone &#40;OLE DB&#41;](ibcpsession-bcpdone-ole-db.md)|Valide les lignes restantes à envoyer à [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].|  
|[IBCPSession::BCPExec &#40;OLE DB&#41;](ibcpsession-bcpexec-ole-db.md)|Effectue l'opération de copie en bloc.|  
|[IBCPSession::BCPInit &#40;OLE DB&#41;](ibcpsession-bcpinit-ole-db.md)|Initialise la structure de copie en bloc, effectue une vérification des erreurs, vérifie que les données et les noms de fichiers de format sont corrects, puis les ouvre.|  
|[IBCPSession::BCPReadFmt &#40;OLE DB&#41;](ibcpsession-bcpreadfmt-ole-db.md)|Lit les informations de format pour chaque colonne à partir du fichier de format.|  
|[IBCPSession::BCPWriteFmt &#40;OLE DB&#41;](ibcpsession-bcpwritefmt-ole-db.md)|Écrit les informations de format pour chaque colonne dans le fichier de format.|  
  
## <a name="see-also"></a>Voir aussi  
 [Interfaces &#40;OLE DB&#41;](../../database-engine/dev-guide/interfaces-ole-db.md)  
  
  

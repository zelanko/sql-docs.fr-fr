---
title: IBCPSession (OLE DB) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
apitype: COM
helpviewer_keywords:
- IBCPSession interface
ms.assetid: 00d0311f-8b71-4ad6-824d-0e89119347a3
author: MightyPen
ms.author: genemi
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: f3ea8d1e52ba5fc4d34f5bee1c728ff7ca3db2d7
ms.sourcegitcommit: 856e42f7d5125d094fa84390bc43048808276b57
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/07/2019
ms.locfileid: "73789580"
---
# <a name="ibcpsession-ole-db"></a>IBCPSession (OLE DB)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  L'interface **IBCPSession** expose la prise en charge des opérations de copie en bloc basées sur des fichiers [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . L'interface **IBCPSession** est exposée dans le fournisseur OLE DB [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client sous le même niveau que Sessions. Dans le fournisseur OLE DB [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client, les objets sources de données sont des fabriques pour les objets Session et les opérations de copie en bloc sont spécifiées dans la propriété de connexion SSPROP_ENABLEBULKCOPY. De plus, la propriété SSPROP_ENABLEFASTLOAD doit avoir la valeur vrai.  
  
 L'appel de la méthode **IDBCreateSession::CreateSession** provoquera alors la création d'un objet **BulkCopySession** . Toutes les méthodes de copie en bloc basées sur des fichiers exposées par le biais de l'objet **IBCPSession** peuvent ensuite être appelées avec des signatures presque semblables sur l'interface **IBCPSession** de cet objet **IBCPSession** .  
  
> [!NOTE]  
>  Le fournisseur OLE DB [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client prend en charge les opérations de copie en bloc basées sur mémoire par le biais de l'interface [IRowsetFastLoad](../../relational-databases/native-client-ole-db-interfaces/irowsetfastload-ole-db.md) .  
  
 Pour plus d’informations sur l’utilisation du fournisseur [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB pour les opérations de copie en bloc, consultez [exécution d’opérations de copie en bloc](../../relational-databases/native-client/features/performing-bulk-copy-operations.md).  
  
 Pour obtenir un exemple illustrant l’utilisation de l’interface **IBCPSession** , consultez [IBCPSession : &#40;:&#41;BCPDone OLE DB](../../relational-databases/native-client-ole-db-interfaces/ibcpsession-bcpdone-ole-db.md).  
  
## <a name="in-this-section"></a>Dans cette section  
  
|Méthode|Description|  
|------------|-----------------|  
|[IBCPSession :: BCPColFmt &#40;OLE DB&#41;](../../relational-databases/native-client-ole-db-interfaces/ibcpsession-bcpcolfmt-ole-db.md)|Crée une liaison entre des variables de programme et des colonnes [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .|  
|[IBCPSession :: BCPColumns &#40;OLE DB&#41;](../../relational-databases/native-client-ole-db-interfaces/ibcpsession-bcpcolumns-ole-db.md)|Définit le nombre de champs qui doivent être liés aux colonnes dans une table [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .|  
|[IBCPSession :: BCPControl &#40;OLE DB&#41;](../../relational-databases/native-client-ole-db-interfaces/ibcpsession-bcpcontrol-ole-db.md)|Définit les options pour une opération de copie en bloc.|  
|[IBCPSession :: BCPDone &#40;OLE DB&#41;](../../relational-databases/native-client-ole-db-interfaces/ibcpsession-bcpdone-ole-db.md)|Valide les lignes restantes à envoyer à [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].|  
|[IBCPSession :: BCPExec &#40;OLE DB&#41;](../../relational-databases/native-client-ole-db-interfaces/ibcpsession-bcpexec-ole-db.md)|Effectue l'opération de copie en bloc.|  
|[IBCPSession :: BCPInit &#40;OLE DB&#41;](../../relational-databases/native-client-ole-db-interfaces/ibcpsession-bcpinit-ole-db.md)|Initialise la structure de copie en bloc, effectue une vérification des erreurs, vérifie que les données et les noms de fichiers de format sont corrects, puis les ouvre.|  
|[IBCPSession::BCPReadFmt &#40;OLE DB&#41;](../../relational-databases/native-client-ole-db-interfaces/ibcpsession-bcpreadfmt-ole-db.md)|Lit les informations de format pour chaque colonne à partir du fichier de format.|  
|[IBCPSession::BCPWriteFmt &#40;OLE DB&#41;](../../relational-databases/native-client-ole-db-interfaces/ibcpsession-bcpwritefmt-ole-db.md)|Écrit les informations de format pour chaque colonne dans le fichier de format.|  
  
## <a name="see-also"></a>Voir aussi  
 [Interfaces &#40;OLE DB&#41;](https://msdn.microsoft.com/library/34c33364-8538-45db-ae41-5654481cda93)  
  
  

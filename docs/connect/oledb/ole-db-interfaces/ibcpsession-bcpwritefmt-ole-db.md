---
title: IBCPSession::BCPWriteFmt (pilote OLE DB) | Microsoft Docs
description: Utilisation d’IBCPSession::BCPWriteFmt pour enregistrer les fichiers de format dans un format xml ou texte (OLE DB)
ms.custom: ''
ms.date: 06/14/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: connectivity
ms.topic: reference
apiname:
- IBCPSession::BCPWriteFmt (OLE DB)
apitype: COM
helpviewer_keywords:
- BCPWriteFmt method
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 2e758d5bb93238cf2fd006486b61df065c14ac3c
ms.sourcegitcommit: c7f40918dc3ecdb0ed2ef5c237a3996cb4cd268d
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/05/2020
ms.locfileid: "91726936"
---
# <a name="ibcpsessionbcpwritefmt-ole-db"></a>IBCPSession::BCPWriteFmt (OLE DB)
[!INCLUDE [SQL Server](../../../includes/applies-to-version/sql-asdb-asdbmi-asa-pdw.md)]

[!INCLUDE[Driver_OLEDB_Download](../../../includes/driver_oledb_download.md)]

  Écrit les informations de format pour chaque colonne dans le fichier de format.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
HRESULT BCPWriteFmt(   
      const wchar_t *pwszFormatFile);  
```  
  
## <a name="remarks"></a>Notes  
 Le fichier de format spécifie le format de données d'un fichier de données créé par le biais d'une copie en bloc. Les appels aux méthodes [IBCPSession::BCPColumns](../../oledb/ole-db-interfaces/ibcpsession-bcpcolumns-ole-db.md) et [IBCPSession::BCPColFmt](../../oledb/ole-db-interfaces/ibcpsession-bcpcolfmt-ole-db.md) définissent le format du fichier de données. La méthode **BCPWriteFmt** enregistre cette définition dans le fichier référencé par l'argument pwszFormatFile.  
  
 La méthode **BCPWriteFmt** peut enregistrer les fichiers de format dans un format XML ou texte. Vous devez l’indiquer au moyen de l’option de contrôle BCP_OPTION_XML avec la méthode [IBCPSession::BCPControl](../../oledb/ole-db-interfaces/ibcpsession-bcpcontrol-ole-db.md).  
  
 Pour charger un fichier de format enregistré, utilisez la méthode [IBCPSession::BCPReadFmt](../../oledb/ole-db-interfaces/ibcpsession-bcpreadfmt-ole-db.md).  
  
## <a name="arguments"></a>Arguments  
 *pwszFormatFile*[in]  
 Chemin d'accès et nom du fichier contenant les valeurs de format du fichier de données.  
  
## <a name="return-code-values"></a>Codet de retour  
 S_OK  
 S_OK  
  
 E_FAIL  
 Une erreur spécifique au fournisseur s’est produite. Pour obtenir des informations détaillées, utilisez l’interface [ISQLServerErrorInfo](./isqlservererrorinfo-geterrorinfo-ole-db.md?view=sql-server-ver15).  
  
 E_OUTOFMEMORY  
 Erreur de mémoire insuffisante.  
  
 E_UNEXPECTED  
 L'appel à la méthode était inattendu. Par exemple, la méthode [IBCPSession::BCPInit](../../oledb/ole-db-interfaces/ibcpsession-bcpinit-ole-db.md) n’a pas été appelée avant d’appeler cette méthode.  
  
## <a name="see-also"></a>Voir aussi  
 [IBCPSession &#40;OLE DB&#41;](../../oledb/ole-db-interfaces/ibcpsession-ole-db.md)   
 [Exécution d'opérations de copie en bloc](../../oledb/features/performing-bulk-copy-operations.md) 
  

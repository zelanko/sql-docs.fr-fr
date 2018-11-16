---
title: IBCPSession::BCPReadFmt (OLE DB) | Microsoft Docs
description: À l’aide de IBCPSession::BCPReadFmt pour lire les données à partir d’un fichier de format (OLE DB)
ms.custom: ''
ms.date: 06/14/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: connectivity
ms.topic: reference
apiname:
- IBCPSession::BCPReadFmt (OLE DB)
apitype: COM
helpviewer_keywords:
- BCPReadFmt method
author: pmasl
ms.author: pelopes
manager: craigg
ms.openlocfilehash: 451b2b52f44af44176ab5470992d30e24df70582
ms.sourcegitcommit: 63b4f62c13ccdc2c097570fe8ed07263b4dc4df0
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 11/13/2018
ms.locfileid: "51600269"
---
# <a name="ibcpsessionbcpreadfmt-ole-db"></a>IBCPSession::BCPReadFmt (OLE DB)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

[!INCLUDE[Driver_OLEDB_Download](../../../includes/driver_oledb_download.md)]

  Lit les informations de format pour chaque colonne à partir du fichier de format.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
HRESULT BCPReadFmt(   
      const wchar_t *pwszFormatFile);  
```  
  
## <a name="remarks"></a>Notes   
 La méthode **BCPReadFmt** est utilisée pour lire les données d'un fichier de format qui spécifie le format des données dans le fichier de données. Cette méthode est capable de détecter la version correcte du fichier de format. Elle peut détecter automatiquement si le fichier de format est au format xml ou dans un ancien format et qu'il se comporte en conséquence. Les versions de fichiers de format pris en charge par le pilote OLE DB pour SQL Server BCP sont 6.0 ou version ultérieure.  
  
 Après avoir lu les valeurs de format, la méthode **BCPReadFmt** effectue les appels appropriés aux méthodes [IBCPSession::BCPColumns](../../oledb/ole-db-interfaces/ibcpsession-bcpcolumns-ole-db.md) et [IBCPSession::BCPColFmt](../../oledb/ole-db-interfaces/ibcpsession-bcpcolfmt-ole-db.md). L'utilisateur n'a pas besoin d'analyser un fichier de format et d'effectuer ces appels.  
  
 Pour enregistrer un fichier de format, appelez la méthode [IBCPSession::BCPWriteFmt](../../oledb/ole-db-interfaces/ibcpsession-bcpwritefmt-ole-db.md) . Les appels à la méthode **BCPReadFmt** peuvent référencer des formats enregistrés. L'utilitaire**bcp**peut également enregistrer des formats de données définis par l'utilisateur dans des fichiers qui peuvent être référencés par la méthode **BCPReadFmt** .  
  
 Le **BCP_OPTION_DELAYREADFMT** valeur de la *eOption* paramètre de [IBCPSession::BCPControl](../../oledb/ole-db-interfaces/ibcpsession-bcpcontrol-ole-db.md) modifie le comportement de IBCPSession::BCPReadFmt.  
  
## <a name="arguments"></a>Arguments  
 *pwszFormatFile*[in]  
 Chemin d'accès et nom du fichier contenant les valeurs de format du fichier de données.  
  
## <a name="return-code-values"></a>Valeurs des codes de retour  
 Cette méthode signale les erreurs en attribuant à la propriété Nombre de l'objet Err global l'une des valeurs du tableau suivant.  
 S_OK  
  
 E_FAIL  
 Une erreur spécifique au fournisseur s'est produite. Pour obtenir des informations détaillées, utilisez l'interface [ISQLServerErrorInfo](https://msdn.microsoft.com/library/a8323b5c-686a-4235-a8d2-bda43617b3a1) .  
  
 E_OUTOFMEMORY  
 Erreur de mémoire insuffisante.  
  
 E_UNEXPECTED  
 L'appel à la méthode était inattendu. Par exemple, la méthode [IBCPSession::BCPInit](../../oledb/ole-db-interfaces/ibcpsession-bcpinit-ole-db.md) n’a pas été appelée avant d’appeler cette méthode.  
  
## <a name="see-also"></a> Voir aussi  
 [IBCPSession &#40;OLE DB&#41;](../../oledb/ole-db-interfaces/ibcpsession-ole-db.md)   
 [Exécution d'opérations de copie en bloc](../../oledb/features/performing-bulk-copy-operations.md)  
  
  

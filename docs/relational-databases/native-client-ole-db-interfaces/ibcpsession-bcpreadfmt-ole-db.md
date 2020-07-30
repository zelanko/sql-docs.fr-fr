---
title: 'IBCPSession :: BCPReadFmt (fournisseur Native Client OLE DB) | Microsoft Docs'
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
apiname:
- IBCPSession::BCPReadFmt (OLE DB)
apitype: COM
helpviewer_keywords:
- BCPReadFmt method
ms.assetid: e2a12050-94e4-48a3-8a48-b780d646f116
author: markingmyname
ms.author: maghan
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: fda3b39b227b959c28268d47ced774821ad7041b
ms.sourcegitcommit: 216f377451e53874718ae1645a2611cdb198808a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/28/2020
ms.locfileid: "87247738"
---
# <a name="ibcpsessionbcpreadfmt-native-client-ole-db-provider"></a>IBCPSession :: BCPReadFmt (fournisseur Native Client OLE DB)
[!INCLUDE[SQL Server Azure SQL Database Synapse Analytics PDW ](../../includes/applies-to-version/sql-asdb-asdbmi-asa-pdw.md)]

  Lit les informations de format pour chaque colonne à partir du fichier de format.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
HRESULT BCPReadFmt(   
      const wchar_t *pwszFormatFile);  
```  
  
## <a name="remarks"></a>Notes  
 La méthode **BCPReadFmt** est utilisée pour lire les données d'un fichier de format qui spécifie le format des données dans le fichier de données. Cette méthode est capable de détecter la version correcte du fichier de format. Elle peut détecter automatiquement si le fichier de format est au format xml ou dans un ancien format et qu'il se comporte en conséquence. Les fichiers de format versions 6.0 et supérieures sont prises en charge par l'utilitaire de copie en bloc (BCP) du fournisseur OLE DB [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client.  
  
 Après avoir lu les valeurs de format, la méthode **BCPReadFmt** effectue les appels appropriés aux méthodes [IBCPSession::BCPColumns](../../relational-databases/native-client-ole-db-interfaces/ibcpsession-bcpcolumns-ole-db.md) et [IBCPSession::BCPColFmt](../../relational-databases/native-client-ole-db-interfaces/ibcpsession-bcpcolfmt-ole-db.md). L'utilisateur n'a pas besoin d'analyser un fichier de format et d'effectuer ces appels.  
  
 Pour enregistrer un fichier de format, appelez la méthode [IBCPSession::BCPWriteFmt](../../relational-databases/native-client-ole-db-interfaces/ibcpsession-bcpwritefmt-ole-db.md). Les appels à la méthode **BCPReadFmt** peuvent référencer des formats enregistrés. L'utilitaire**bcp**peut également enregistrer des formats de données définis par l'utilisateur dans des fichiers qui peuvent être référencés par la méthode **BCPReadFmt** .  
  
 La valeur **BCP_OPTION_DELAYREADFMT** du paramètre *eOption* de [IBCPSession::BCPControl](../../relational-databases/native-client-ole-db-interfaces/ibcpsession-bcpcontrol-ole-db.md) modifie le comportement de IBCPSession::BCPReadFmt.  
  
## <a name="arguments"></a>Arguments  
 *pwszFormatFile*[in]  
 Chemin d'accès et nom du fichier contenant les valeurs de format du fichier de données.  
  
## <a name="return-code-values"></a>Codet de retour  
 S_OK  
 S_OK  
  
 E_FAIL  
 Une erreur spécifique au fournisseur s’est produite. Pour obtenir des informations détaillées, utilisez l’interface [ISQLServerErrorInfo](https://msdn.microsoft.com/library/a8323b5c-686a-4235-a8d2-bda43617b3a1).  
  
 E_OUTOFMEMORY  
 Erreur de mémoire insuffisante.  
  
 E_UNEXPECTED  
 L'appel à la méthode était inattendu. Par exemple, la méthode [IBCPSession::BCPInit](../../relational-databases/native-client-ole-db-interfaces/ibcpsession-bcpinit-ole-db.md) n’a pas été appelée avant d’appeler cette méthode.  
  
## <a name="see-also"></a>Voir aussi  
 [IBCPSession &#40;OLE DB&#41;](../../relational-databases/native-client-ole-db-interfaces/ibcpsession-ole-db.md)   
 [Exécution d'opérations de copie en bloc](../../relational-databases/native-client/features/performing-bulk-copy-operations.md)  
  
  

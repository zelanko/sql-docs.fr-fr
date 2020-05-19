---
title: IBCPSession::BCPWriteFmt (OLE DB) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
api_name:
- IBCPSession::BCPWriteFmt (OLE DB)
topic_type:
- apiref
helpviewer_keywords:
- BCPWriteFmt method
ms.assetid: add50425-2ed6-411a-a391-4ce63c364892
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: a547548f84af88ea3790658618570aeed8ce8112
ms.sourcegitcommit: b72c9fc9436c44c6a21fd96223c73bf94706c06b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/01/2020
ms.locfileid: "82695140"
---
# <a name="ibcpsessionbcpwritefmt-ole-db"></a>IBCPSession::BCPWriteFmt (OLE DB)
  Écrit les informations de format pour chaque colonne dans le fichier de format.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
HRESULT BCPWriteFmt(   
const wchar_t *pwszFormatFile);  
```  
  
## <a name="remarks"></a>Notes  
 Le fichier de format spécifie le format de données d'un fichier de données créé par le biais d'une copie en bloc. Les appels aux méthodes [IBCPSession::BCPColumns](ibcpsession-bcpcolumns-ole-db.md) et [IBCPSession::BCPColFmt](ibcpsession-bcpcolfmt-ole-db.md) définissent le format du fichier de données. La méthode **BCPWriteFmt** enregistre cette définition dans le fichier référencé par l'argument pwszFormatFile.  
  
 La méthode **BCPWriteFmt** peut enregistrer les fichiers de format dans un format XML ou texte. Vous devez l’indiquer au moyen de l’option de contrôle BCP_OPTION_XML avec la méthode [IBCPSession::BCPControl](ibcpsession-bcpcontrol-ole-db.md).  
  
 Pour charger un fichier de format enregistré, utilisez la méthode [IBCPSession::BCPReadFmt](ibcpsession-bcpreadfmt-ole-db.md).  
  
## <a name="arguments"></a>Arguments  
 *pwszFormatFile*[in]  
 Chemin d'accès et nom du fichier contenant les valeurs de format du fichier de données.  
  
## <a name="return-code-values"></a>Codet de retour  
 S_OK  
 S_OK  
  
 E_FAIL  
 Une erreur spécifique au fournisseur s’est produite ; Pour plus d’informations, utilisez l’interface [ISQLServerErrorInfo](../../database-engine/dev-guide/isqlservererrorinfo-ole-db.md) .  
  
 E_OUTOFMEMORY  
 Erreur de mémoire insuffisante.  
  
 E_UNEXPECTED  
 L'appel à la méthode était inattendu. Par exemple, la méthode [IBCPSession::BCPInit](ibcpsession-bcpinit-ole-db.md) n’a pas été appelée avant d’appeler cette méthode.  
  
## <a name="see-also"></a>Voir aussi  
 [IBCPSession &#40;OLE DB&#41;](ibcpsession-ole-db.md)   
 [Exécution d'opérations de copie en bloc](../native-client/features/performing-bulk-copy-operations.md)  
  
  

---
title: bcp_sendrow | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
api_name:
- bcp_sendrow
api_location:
- sqlncli11.dll
topic_type:
- apiref
helpviewer_keywords:
- bcp_sendrow function
ms.assetid: ddbdb4bd-ad4e-4bf1-9a75-656aa26ce10a
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 3e8ef7aa7a4354f5a3fbc334504512b2ee8d131b
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "62688828"
---
# <a name="bcp_sendrow"></a>bcp_sendrow
  Envoie une ligne de données à partir de variables de programme à [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
RETCODE bcp_sendrow (  
    HDBC   
hdbc  
);  
  
```  
  
## <a name="arguments"></a>Arguments  
 *hdbc*  
 Handle de connexion ODBC compatible avec la copie en bloc.  
  
## <a name="returns"></a>Retours  
 SUCCEED ou FAIL.  
  
## <a name="remarks"></a>Notes  
 La fonction **bcp_sendrow** génère une ligne à partir de variables de programme et l'envoie à [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 Avant d'appeler **bcp_sendrow**, vous devez effectuer des appels à [bcp_bind](bcp-bind.md) pour spécifier les variables de programme qui contiennent des données de ligne.  
  
 Si **bcp_bind** est appelé en spécifiant un type de données long de longueur variable (par exemple, un paramètre *eDataType* SQLTEXT et un paramètre *pData* nonNULL), **bcp_sendrow** envoie la valeur de données entière, comme pour tout autre type de données. Toutefois, si **bcp_bind** possède un paramètre *pData* NULL, **bcp_sendrow** redonne le contrôle à l'application immédiatement après que tous les colonnes avec des données spécifiées ont été envoyées à [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. L'application peut ensuite appeler [bcp_moretext](bcp-moretext.md) à plusieurs reprises pour envoyer les données longues de longueur variable à [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], segment par segment. Pour plus d'informations, consultez [bcp_moretext](bcp-moretext.md).  
  
 Lorsque **bcp_sendrow** est utilisé pour copier en bloc des lignes à partir de variables de programme dans des tables [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , les lignes sont validées uniquement lorsque l'utilisateur appelle [bcp_batch](bcp-batch.md) ou [bcp_done](bcp-done.md). L'utilisateur peut choisir d'appeler **bcp_batch** une fois chaque *n* lignes ou lors de creux entre deux périodes de données entrantes. Si **bcp_batch** n'est jamais appelé, les lignes sont validées lorsque **bcp_done** est appelé.  
  
 Pour plus d’informations sur la modification avec rupture dans la copie [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]en bloc à compter de, consultez [exécution d’opérations de copie en bloc &#40;ODBC&#41;](../native-client-odbc-bulk-copy-operations/performing-bulk-copy-operations-odbc.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Bulk Copy Functions](sql-server-driver-extensions-bulk-copy-functions.md)  
  
  

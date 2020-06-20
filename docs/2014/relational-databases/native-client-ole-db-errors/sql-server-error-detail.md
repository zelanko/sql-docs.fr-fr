---
title: Détail des erreurs SQL Server | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- SQL Server Native Client OLE DB provider, errors
- errors [OLE DB], error details
- IErrorRecords interface
- IErrorInfo interface
- OLE DB error handling, error details
- ISQLServerErrorInfo interface
ms.assetid: 51500ee3-3d78-47ec-b90f-ebfc55642e06
author: rothja
ms.author: jroth
ms.openlocfilehash: 4c03cf62dd274f9bcca213d33fb8969b26c9d980
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/18/2020
ms.locfileid: "85043521"
---
# <a name="sql-server-error-detail"></a>Détail des erreurs SQL Server
  Le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] fournisseur de OLE DB Native Client définit l’interface d’erreur spécifique au fournisseur [ISQLServerErrorInfo](../../database-engine/dev-guide/isqlservererrorinfo-ole-db.md). L'interface retourne davantage de détails sur une erreur [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] et s'avère utile en cas d'échec de l'exécution d'une commande ou d'opérations d'ensemble de lignes.  
  
 Vous pouvez accéder à l’interface **ISQLServerErrorInfo** de deux manières.  
  
 Le consommateur peut appeler **IErrorRecords::GetCustomerErrorObject** pour obtenir un pointeur **ISQLServerErrorInfo**, comme illustré dans l’exemple de code suivant. (Il n’est pas nécessaire d’obtenir **ISQLErrorInfo**). **ISQLErrorInfo** et **ISQLServerErrorInfo** sont tous deux des objets d’erreur OLE DB personnalisés, **ISQLServerErrorInfo** étant l’interface à utiliser pour obtenir des informations sur les erreurs de serveur, notamment des détails sur le nom de la procédure et les numéros de ligne.  
  
```  
// Get the SQL Server custom error object.  
if(FAILED(hr=pIErrorRecords->GetCustomErrorObject(  
   nRec, IID_ISQLServerErrorInfo,  
   (IUnknown**)&pISQLServerErrorErrorInfo)))  
```  
  
 L’autre méthode permettant d’obtenir un pointeur **ISQLServerErrorInfo** consiste à appeler la méthode **QueryInterface** sur un pointeur **ISQLErrorInfo** qui a déjà été obtenu. Notez que comme **ISQLServerErrorInfo** contient un surensemble des informations disponibles auprès de **ISQLErrorInfo**, il est logique d’accéder directement à **ISQLServerErrorInfo** via **GetCustomerErrorObject**.  
  
 L’interface **ISQLServerErrorInfo** expose une fonction membre, [ISQLServerErrorInfo::GetErrorInfo](../native-client-ole-db-interfaces/isqlservererrorinfo-geterrorinfo-ole-db.md). La fonction retourne un pointeur à une structure SSERRORINFO et un pointeur à une mémoire tampon de chaîne. Les deux pointeurs référencent la mémoire que le consommateur doit libérer avec méthode **IMalloc::Free**.  
  
 Les membres de la structure SSERRORINFO sont interprétés par le consommateur comme suit.  
  
|Membre|Description|  
|------------|-----------------|  
|*pwszMessage*|Message d'erreur [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Identique à la chaîne retournée dans **IErrorInfo::GetDescription**.|  
|*pwszServer*|Nom de l'instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] pour la session.|  
|*pwszProcedure*|S'il y a lieu, nom de la procédure d'où provient l'erreur. Sinon, une chaîne vide.|  
|*lNative*|Numéro d'erreur natif [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Identique à la valeur retournée dans le paramètre *plNativeError* de **ISQLErrorInfo::GetSQLInfo**.|  
|*bState*|État d'un message d'erreur [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].|  
|*bClass*|Gravité d'un message d'erreur [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].|  
|*wLineNumber*|S'il y a lieu, numéro de ligne d'une procédure stockée sur laquelle s'est produite l'erreur.|  
  
## <a name="see-also"></a>Voir aussi  
 [Sont](errors.md)   
 [RAISERROR &#40;Transact-SQL&#41;](/sql/t-sql/language-elements/raiserror-transact-sql)  
  
  

---
title: Détail de l’erreur SQL Server | Documents Microsoft
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- SQL Server Native Client OLE DB provider, errors
- errors [OLE DB], error details
- IErrorRecords interface
- IErrorInfo interface
- OLE DB error handling, error details
- ISQLServerErrorInfo interface
ms.assetid: 51500ee3-3d78-47ec-b90f-ebfc55642e06
caps.latest.revision: 27
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: cbbf2365603998edabe58a01de840f2969a8c263
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36142031"
---
# <a name="sql-server-error-detail"></a>Détail des erreurs SQL Server
  Le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] fournisseur de OLE DB Native Client définit l’interface d’erreur spécifique au fournisseur [ISQLServerErrorInfo](../../database-engine/dev-guide/isqlservererrorinfo-ole-db.md). L'interface retourne davantage de détails sur une erreur [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] et s'avère utile en cas d'échec de l'exécution d'une commande ou d'opérations d'ensemble de lignes.  
  
 Il existe deux façons d’obtenir l’accès à **ISQLServerErrorInfo** interface.  
  
 Le consommateur peut appeler **IErrorRecords::GetCustomerErrorObject** pour obtenir un **ISQLServerErrorInfo** pointeur, comme indiqué dans l’exemple de code suivant. (Il est inutile d’obtenir **ISQLErrorInfo.**) Les deux **ISQLErrorInfo** et **ISQLServerErrorInfo** sont des objets d’erreur OLE DB personnalisés, **ISQLServerErrorInfo** en cours de l’interface à utiliser pour obtenir des informations de erreurs de serveur, notamment des détails sur les numéros de ligne et de nom de procédure.  
  
```  
// Get the SQL Server custom error object.  
if(FAILED(hr=pIErrorRecords->GetCustomErrorObject(  
   nRec, IID_ISQLServerErrorInfo,  
   (IUnknown**)&pISQLServerErrorErrorInfo)))  
```  
  
 Une autre méthode pour obtenir un **ISQLServerErrorInfo** pointeur consiste à appeler la **QueryInterface** méthode sur une déjà obtenu **ISQLErrorInfo** pointeur. Notez que puisque **ISQLServerErrorInfo** contient un surensemble des informations disponibles à partir de **ISQLErrorInfo**, il est judicieux d’accéder directement à **ISQLServerErrorInfo**via **GetCustomerErrorObject**.  
  
 Le **ISQLServerErrorInfo** interface expose une fonction membre, [ISQLServerErrorInfo::GetErrorInfo](../native-client-ole-db-interfaces/isqlservererrorinfo-geterrorinfo-ole-db.md). La fonction retourne un pointeur à une structure SSERRORINFO et un pointeur à une mémoire tampon de chaîne. Les deux pointeurs font référence mémoire, le consommateur doit libérer à l’aide de la **IMalloc::Free** (méthode).  
  
 Les membres de la structure SSERRORINFO sont interprétés par le consommateur comme suit.  
  
|Membre|Description|  
|------------|-----------------|  
|*pwszMessage*|Message d'erreur [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Identique à la chaîne retournée dans **IErrorInfo::GetDescription**.|  
|*pwszServer*|Nom de l'instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] pour la session.|  
|*pwszProcedure*|S'il y a lieu, nom de la procédure d'où provient l'erreur. Sinon, une chaîne vide.|  
|*lNative*|Numéro d'erreur natif [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Identique à la valeur retournée dans le *plNativeError* paramètre de **ISQLErrorInfo::GetSQLInfo**.|  
|*bState*|État d'un message d'erreur [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].|  
|*bClass*|Gravité d'un message d'erreur [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].|  
|*wLineNumber*|S'il y a lieu, numéro de ligne d'une procédure stockée sur laquelle s'est produite l'erreur.|  
  
## <a name="see-also"></a>Voir aussi  
 [Erreurs](errors.md)   
 [RAISERROR &#40;Transact-SQL&#41;](/sql/t-sql/language-elements/raiserror-transact-sql)  
  
  

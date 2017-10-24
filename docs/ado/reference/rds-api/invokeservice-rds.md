---
title: InvokeService (RDS) | Documents Microsoft
ms.prod: sql-non-specified
ms.technology:
- drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
apitype: COM
helpviewer_keywords:
- InvokeService [RDS]
ms.assetid: ad45c676-ec7e-4a3a-9a6b-a54f75eb3012
caps.latest.revision: 11
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 20e7b09600a0ec96b089322a1bd4d55e75eb9acf
ms.contentlocale: fr-fr
ms.lasthandoff: 09/09/2017

---
# <a name="invokeservice-rds"></a>InvokeService (RDS)
Retourne un pointeur vers l’interface demandée sur une version plus performante de l’objet.  
  
> [!IMPORTANT]
>  À compter de Windows 8 et Windows Server 2012, les composants de serveur Services Bureau à distance ne sont plus inclus dans le système d’exploitation Windows (consultez Windows 8 et [Cookbook de compatibilité de Windows Server 2012](https://www.microsoft.com/en-us/download/details.aspx?id=27416) pour plus de détails). Composants du client Bureau à distance seront supprimées dans une future version de Windows. Évitez d'utiliser cette fonctionnalité dans de nouveaux travaux de développement, et prévoyez de modifier les applications qui utilisent actuellement cette fonctionnalité. La migration vers les applications qui utilisent des services Bureau à distance [Service de données WCF](http://go.microsoft.com/fwlink/?LinkId=199565).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
object.InvokeService(REFID riid, IUknown* punkNotSoFunctionalInterface, IUknown** ppunkMoreFunctionalInterface) As HRESULT  
```  
  
#### <a name="parameters"></a>Paramètres  
 *riid*  
  
 [in] Identificateur de l’interface demandée.  
  
 *punkNotSoFunctionalInterface*  
  
 [in] L’objet source moins performant.  
  
 *ppunkMoreFunctionalInterface*  
  
 [out] L’adresse de la variable pointeur qui reçoit le pointeur d’interface demandé dans *riid*. Lors d’un retour, le *ppunkMoreFunctionalInterface* paramètre contient le pointeur d’interface demandé à l’objet. Si l’objet ne prend pas en charge l’interface spécifiée dans *riid*, *ppunkMoreFunctionalInterface* a la valeur NULL.  
  
## <a name="return-value"></a>Valeur retournée  
 Une valeur HRESULT qui indique si l’appel à la **InvokeService** méthode a réussi.  
  
## <a name="remarks"></a>Notes  
 L’implémentation du moteur de curseur RDS de **InvokeService** prend l’ensemble de lignes d’entrée (ou de plusieurs objets de résultats), remplit le moteur de curseur à partir de l’ensemble de lignes d’entrée, puis retourne un pointeur sur lui-même.  
  
## <a name="applies-to"></a>S'applique à  
 [Interface IRDSService (RDS)](../../../ado/reference/rds-api/irdsservice-interface-rds.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Méthodes des services Bureau à distance](../../../ado/reference/rds-api/rds-methods.md)




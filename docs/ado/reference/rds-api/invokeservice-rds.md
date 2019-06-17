---
title: InvokeService (RDS) | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
helpviewer_keywords:
- InvokeService [RDS]
ms.assetid: ad45c676-ec7e-4a3a-9a6b-a54f75eb3012
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: d7d0c205b5045f4cd743776894f62fbc4f0750cc
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "66712645"
---
# <a name="invokeservice-rds"></a>InvokeService (RDS)
Retourne un pointeur vers l’interface demandée sur une version plus performante de l’objet.  
  
> [!IMPORTANT]
>  Depuis Windows 8 et Windows Server 2012, composants de serveur Services Bureau à distance ne sont plus inclus dans le système d’exploitation Windows (voir Windows 8 et [Guide de compatibilité de Windows Server 2012](https://www.microsoft.com/download/details.aspx?id=27416) pour plus de détails). Composants du client RDS seront supprimées dans une future version de Windows. Évitez d'utiliser cette fonctionnalité dans de nouveaux travaux de développement, et prévoyez de modifier les applications qui utilisent actuellement cette fonctionnalité. Les applications qui utilisent des services Bureau à distance doivent migrer vers [Service de données WCF](https://go.microsoft.com/fwlink/?LinkId=199565).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
object.InvokeService(REFID riid, IUknown* punkNotSoFunctionalInterface, IUknown** ppunkMoreFunctionalInterface) As HRESULT  
```  
  
#### <a name="parameters"></a>Paramètres  
 *riid*  
  
 [in] L’identificateur de l’interface demandée.  
  
 *punkNotSoFunctionalInterface*  
  
 [in] L’objet source moins performant.  
  
 *ppunkMoreFunctionalInterface*  
  
 [out] L’adresse de la variable pointeur qui reçoit le pointeur d’interface demandé dans *riid*. En cas de renvoi, le *ppunkMoreFunctionalInterface* paramètre contient le pointeur d’interface demandé à l’objet. Si l’objet ne prend pas en charge l’interface spécifiée dans *riid*, *ppunkMoreFunctionalInterface* est définie sur NULL.  
  
## <a name="return-value"></a>Valeur de retour  
 Une valeur HRESULT qui indique si l’appel à la **InvokeService** méthode a réussi.  
  
## <a name="remarks"></a>Notes  
 L’implémentation du moteur de curseur RDS de **InvokeService** prend l’ensemble de lignes d’entrée (ou plusieurs objets de résultats), remplit le moteur de curseur à partir de l’ensemble de lignes d’entrée et renvoie un pointeur sur lui-même.  
  
## <a name="applies-to"></a>S'applique à  
 [IRDSService, interface (RDS)](../../../ado/reference/rds-api/irdsservice-interface-rds.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Méthodes RDS](../../../ado/reference/rds-api/rds-methods.md)



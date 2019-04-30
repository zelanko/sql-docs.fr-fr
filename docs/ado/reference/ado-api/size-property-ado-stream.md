---
title: Size, propriété (ADO Stream) | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- _Stream::Size
helpviewer_keywords:
- Size property [ADO Stream]
ms.assetid: a487c241-d953-4c31-ae7e-6358d5cf6733
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: d35af0315460af8b110c7af38934e5d196a5c895
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63192795"
---
# <a name="size-property-ado-stream"></a>Size, propriété (objet Stream ADO)
Indique la taille du flux en nombre d’octets.  
  
## <a name="return-values"></a>Valeurs de retour  
 Retourne un **Long** valeur qui spécifie la taille du flux en nombre d’octets. La valeur par défaut est la taille de flux, ou -1 si la taille du flux de données n’est pas connue.  
  
## <a name="remarks"></a>Notes  
 **Taille** peut être utilisé uniquement avec open [Stream](../../../ado/reference/ado-api/stream-object-ado.md) objets.  
  
> [!NOTE]
>  N’importe quel nombre de bits peut être stocké dans un **Stream** objet, limitée uniquement par les ressources système. Si le **Stream** contient plus de bits que peut être représenté par un **Long** valeur, **taille** est tronqué et par conséquent ne représentent pas avec précision la longueur de la **Stream**.  
  
## <a name="applies-to"></a>S'applique à  
 [Stream, objet (ADO)](../../../ado/reference/ado-api/stream-object-ado.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Size, propriété (paramètre ADO)](../../../ado/reference/ado-api/size-property-ado-parameter.md)

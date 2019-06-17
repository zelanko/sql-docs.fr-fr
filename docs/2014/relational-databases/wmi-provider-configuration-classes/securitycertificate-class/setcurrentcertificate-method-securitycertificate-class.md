---
title: Setcurrentcertificate, méthode (classe SecurityCertificate) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: wmi
ms.topic: reference
api_name:
- SetCurrentCertificate Method (SecurityCertificate Class)
api_location:
- sqlmgmproviderxpsp2up.mof
topic_type:
- apiref
helpviewer_keywords:
- SetCurrentCertificate method
ms.assetid: 04b1a76a-932d-4824-8506-e346afe7554e
author: CarlRabeler
ms.author: carlrab
manager: craigg
ms.openlocfilehash: 32af70857eac43a99257444081c1bcbdc842a2e5
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "63270642"
---
# <a name="setcurrentcertificate-method-securitycertificate-class"></a>Méthode SetCurrentCertificate (classe SecurityCertificate)
  Définit le certificat de sécurité actuel.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
object  
.SetCurrentCertificate(  
SHA , SQLInstance  
)  
  
```  
  
## <a name="parts"></a>Éléments  
 *object*  
 Un securitycertificate [classe SecurityCertificate]-class.md) objet qui représente un certificat de sécurité.  
  
#### <a name="parameters"></a>Paramètres  
  
|Paramètre|Description|  
|---------------|-----------------|  
|*SHA*|Valeur de chaîne qui spécifie l'empreinte numérique de l'algorithme de hachage sécurisé (SHA) pour le certificat de sécurité requis.|  
|*SQLInstance*|Valeur de chaîne qui spécifie l'instance pour laquelle le certificat est requis.|  
  
## <a name="property-valuereturn-value"></a>Valeur de propriété/valeur de retour  
 Valeur uint32 égale à 0 si le service a été correctement modifié, égale à 1 si la demande n'est pas prise en charge ou égale à tout autre nombre pour indiquer une erreur.  
  
## <a name="remarks"></a>Notes  
  
## <a name="see-also"></a>Voir aussi  
 [Configuration des bibliothèques réseau et des protocoles réseau du serveur](https://msdn.microsoft.com/library/ms177485\(v=sql.100\).aspx)  
  
  

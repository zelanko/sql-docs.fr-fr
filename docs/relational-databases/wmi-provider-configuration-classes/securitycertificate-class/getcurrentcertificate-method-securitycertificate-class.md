---
title: Getcurrentcertificate, méthode (classe SecurityCertificate) | Microsoft Docs
ms.custom: ''
ms.date: 03/03/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology:
- database-engine
ms.topic: reference
apiname:
- GetCurrentCertificate Method (SecurityCertificate Class)
apilocation:
- sqlmgmproviderxpsp2up.mof
apitype: MOFDef
helpviewer_keywords:
- GetCurrentCertificate method
ms.assetid: 987a2671-1801-45c4-93e6-29f883c58720
author: CarlRabeler
ms.author: carlrab
manager: craigg
ms.openlocfilehash: c0415981ff65d6ec996de2089d52548a63bb8f71
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47621577"
---
# <a name="getcurrentcertificate-method-securitycertificate-class"></a>Méthode GetCurrentCertificate (classe SecurityCertificate)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]
  Obtient le certificat de sécurité actuel.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
object.GetCurrentCertificate(SHA , SQLInstance)  
```  
  
## <a name="parts"></a>Éléments  
 *object*  
 Objet de [classe SecurityCertificate](../../../relational-databases/wmi-provider-configuration-classes/securitycertificate-class/securitycertificate-class.md) qui représente un certificat de sécurité.  
  
#### <a name="parameters"></a>Paramètres  
  
|Paramètre|Description|  
|---------------|-----------------|  
|*SHA*|Valeur de chaîne (paramètre de sortie) qui spécifie l'empreinte numérique SHA du certificat de sécurité actuel une fois la méthode terminée.|  
|*SQLInstance*|Valeur de chaîne qui spécifie l'instance pour laquelle le certificat est requis.|  
  
## <a name="property-valuereturn-value"></a>Valeur de propriété/valeur de retour  
 Valeur **uint32** , égale à 0 si le service a été correctement modifié, égale à 1 si la demande n'est pas prise en charge ou égale à tout autre nombre pour indiquer une erreur.  
  
## <a name="remarks"></a>Notes  
  
## <a name="see-also"></a>Voir aussi  
 [Configuration des bibliothèques réseau et des protocoles réseau du serveur](http://msdn.microsoft.com/library/ms177485\(v=sql.100\).aspx)  
  
  

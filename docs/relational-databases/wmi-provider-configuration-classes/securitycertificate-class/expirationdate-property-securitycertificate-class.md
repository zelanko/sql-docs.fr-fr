---
title: Propriété ExpirationDate (SecurityCertificate)
ms.custom: seo-lt-2019
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: wmi
ms.topic: reference
apiname:
- ExpirationDate Property (SecurityCertificate Class)
apilocation:
- sqlmgmproviderxpsp2up.mof
apitype: MOFDef
helpviewer_keywords:
- ExpirationDate property
ms.assetid: b7fbb9e9-85c1-475b-8e49-7c82fb3740aa
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 757de27d6d697a27011cba529c730e26a8fb1a4d
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85755390"
---
# <a name="expirationdate-property-securitycertificate-class"></a>Propriété ExpirationDate (classe SecurityCertificate)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../../includes/applies-to-version/sqlserver.md)]
  Obtient la date à laquelle le certificat de sécurité n'est plus en vigueur.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
object.ExpirationDate [= value]  
```  
  
## <a name="parts"></a>Éléments  
 *object*  
 Objet de [classe SecurityCertificate](../../../relational-databases/wmi-provider-configuration-classes/securitycertificate-class/securitycertificate-class.md) qui représente un certificat de sécurité.  
  
## <a name="property-valuereturn-value"></a>Valeur de propriété/valeur de retour  
 Valeur **UInt32** qui spécifie la date d’expiration du certificat de sécurité.  
  
## <a name="remarks"></a>Remarques  
  
## <a name="see-also"></a>Voir aussi  
 [Configuration des bibliothèques réseau et des protocoles réseau du serveur](https://msdn.microsoft.com/library/ms177485\(v=sql.100\).aspx)  
  
  

---
title: ExpirationDate, propriété (classe SecurityCertificate) | Microsoft Docs
ms.custom: ''
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
manager: craigg
ms.openlocfilehash: cf2b4cd081eb36d74438851094284b6e98d55ba8
ms.sourcegitcommit: 9c6a37175296144464ffea815f371c024fce7032
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/15/2018
ms.locfileid: "51656153"
---
# <a name="expirationdate-property-securitycertificate-class"></a>Propriété ExpirationDate (classe SecurityCertificate)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]
  Obtient la date à laquelle le certificat de sécurité n'est plus en vigueur.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
object.ExpirationDate [= value]  
```  
  
## <a name="parts"></a>Éléments  
 *object*  
 Objet de [classe SecurityCertificate](../../../relational-databases/wmi-provider-configuration-classes/securitycertificate-class/securitycertificate-class.md) qui représente un certificat de sécurité.  
  
## <a name="property-valuereturn-value"></a>Valeur de propriété/valeur de retour  
 Un **uint32** valeur qui spécifie la date d’expiration du certificat de sécurité.  
  
## <a name="remarks"></a>Notes  
  
## <a name="see-also"></a>Voir aussi  
 [Configuration des bibliothèques réseau et des protocoles réseau du serveur](https://msdn.microsoft.com/library/ms177485\(v=sql.100\).aspx)  
  
  

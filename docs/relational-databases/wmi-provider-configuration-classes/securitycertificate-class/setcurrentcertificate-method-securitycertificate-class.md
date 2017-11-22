---
title: "Méthode SetCurrentCertificate (classe SecurityCertificate) | Documents Microsoft"
ms.custom: 
ms.date: 03/03/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: wmi
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: reference
apiname: SetCurrentCertificate Method (SecurityCertificate Class)
apilocation: sqlmgmproviderxpsp2up.mof
apitype: MOFDef
helpviewer_keywords: SetCurrentCertificate method
ms.assetid: 04b1a76a-932d-4824-8506-e346afe7554e
caps.latest.revision: "33"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 06d9742dab834e88673db63df18417793e26c1ce
ms.sourcegitcommit: 66bef6981f613b454db465e190b489031c4fb8d3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/17/2017
---
# <a name="setcurrentcertificate-method-securitycertificate-class"></a>Méthode SetCurrentCertificate (classe SecurityCertificate)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]Définit le certificat de sécurité actuel.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
object.SetCurrentCertificate(SHA , SQLInstance)  
```  
  
## <a name="parts"></a>Éléments  
 *objet*  
 Objet de [classe SecurityCertificate](../../../relational-databases/wmi-provider-configuration-classes/securitycertificate-class/securitycertificate-class.md) qui représente un certificat de sécurité.  
  
#### <a name="parameters"></a>Paramètres  
  
|Paramètre| Description|  
|---------------|-----------------|  
|*SHA*|Valeur de chaîne qui spécifie l'empreinte numérique de l'algorithme de hachage sécurisé (SHA) pour le certificat de sécurité requis.|  
|*SQLInstance*|Valeur de chaîne qui spécifie l'instance pour laquelle le certificat est requis.|  
  
## <a name="property-valuereturn-value"></a>Valeur de propriété/valeur de retour  
 Valeur uint32 égale à 0 si le service a été correctement modifié, égale à 1 si la demande n'est pas prise en charge ou égale à tout autre nombre pour indiquer une erreur.  
  
## <a name="remarks"></a>Notes  
  
## <a name="see-also"></a>Voir aussi  
 [Configuration des bibliothèques réseau et des protocoles réseau du serveur](http://msdn.microsoft.com/library/ms177485\(v=sql.100\).aspx)  
  
  

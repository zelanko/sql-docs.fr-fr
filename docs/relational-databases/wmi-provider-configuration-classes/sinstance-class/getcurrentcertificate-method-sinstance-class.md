---
description: Méthode GetCurrentCertificate (classe SInstance)
title: Méthode GetCurrentCertificate, (SInstance)
ms.custom: seo-lt-2019
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: wmi
ms.topic: reference
apiname:
- GetCurrentCertificate Method (SInstance Class)
apilocation:
- sqlmgmproviderxpsp2up.mof
apitype: MOFDef
helpviewer_keywords:
- GetCurrentCertificate method
ms.assetid: 9d2b72df-cb21-414a-abef-917f13d4de62
author: markingmyname
ms.author: maghan
ms.openlocfilehash: 7c36d3c9bbaef0b37a42695315762cada6b9b12d
ms.sourcegitcommit: dd36d1cbe32cd5a65c6638e8f252b0bd8145e165
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/08/2020
ms.locfileid: "89520836"
---
# <a name="getcurrentcertificate-method-sinstance-class"></a>Méthode GetCurrentCertificate (classe SInstance)
[!INCLUDE [SQL Server](../../../includes/applies-to-version/sqlserver.md)]
  Obtient le certificat de sécurité actuel.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
object.GetCurrentCertificate(SHA)  
```  
  
## <a name="parts"></a>Éléments  
 *object*  
 Objet de [classe SInstance](../../../relational-databases/wmi-provider-configuration-classes/sinstance-class/sinstance-class.md) qui représente les paramètres du serveur sur une instance de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].  
  
#### <a name="parameters"></a>Paramètres  
  
|Paramètre|Description|  
|---------------|-----------------|  
|*SHA*|Valeur d'objet de chaîne (paramètre de sortie) qui spécifie le certificat de sécurité actuel une fois la méthode terminée.|  
  
## <a name="property-valuereturn-value"></a>Valeur de propriété/valeur de retour  
 Valeur **uint32** , égale à 0 si le service a été correctement modifié, égale à 1 si la demande n'est pas prise en charge ou égale à tout autre nombre pour indiquer une erreur.  
  
## <a name="remarks"></a>Notes  
  
## <a name="see-also"></a>Voir aussi  
 [Configuration des bibliothèques réseau et des protocoles réseau du serveur](https://msdn.microsoft.com/library/ms177485\(v=sql.100\).aspx)  
  
  

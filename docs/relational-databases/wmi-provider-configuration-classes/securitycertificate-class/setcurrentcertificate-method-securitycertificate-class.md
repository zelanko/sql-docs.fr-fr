---
description: Méthode SetCurrentCertificate (classe SecurityCertificate)
title: Méthode SetCurrentCertificate (SecurityCertificate)
ms.custom: seo-lt-2019
ms.date: 03/03/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: wmi
ms.topic: reference
apiname:
- SetCurrentCertificate Method (SecurityCertificate Class)
apilocation:
- sqlmgmproviderxpsp2up.mof
apitype: MOFDef
helpviewer_keywords:
- SetCurrentCertificate method
ms.assetid: 04b1a76a-932d-4824-8506-e346afe7554e
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 001d9ccdff7db054760f1c7ae10bbce19269f694
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/17/2020
ms.locfileid: "88427281"
---
# <a name="setcurrentcertificate-method-securitycertificate-class"></a>Méthode SetCurrentCertificate (classe SecurityCertificate)
[!INCLUDE [SQL Server](../../../includes/applies-to-version/sqlserver.md)]
  Définit le certificat de sécurité actuel.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
object.SetCurrentCertificate(SHA , SQLInstance)  
```  
  
## <a name="parts"></a>Éléments  
 *object*  
 Objet de [classe SecurityCertificate](../../../relational-databases/wmi-provider-configuration-classes/securitycertificate-class/securitycertificate-class.md) qui représente un certificat de sécurité.  
  
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
  
  

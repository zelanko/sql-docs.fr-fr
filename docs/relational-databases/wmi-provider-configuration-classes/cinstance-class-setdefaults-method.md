---
description: CInstance, classe (méthode SetDefaults)
title: Méthode SetDefaults (CInstance)
ms.custom: seo-lt-2019
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: wmi
ms.topic: reference
apiname:
- SetDefaults Method (CInstance Class)
apilocation:
- sqlmgmproviderxpsp2up.mof
apitype: MOFDef
helpviewer_keywords:
- SetDefaults method
ms.assetid: ed9e99c2-3e28-4ee8-bc20-61ca05984973
author: markingmyname
ms.author: maghan
ms.openlocfilehash: 2a99b8bbc94bf8e62cd8125e01327a4691a296cb
ms.sourcegitcommit: dd36d1cbe32cd5a65c6638e8f252b0bd8145e165
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/08/2020
ms.locfileid: "89545311"
---
# <a name="cinstance-class---setdefaults-method"></a>CInstance, classe (méthode SetDefaults)
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]
  Définit toutes les valeurs par défaut pour l’instance du [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] client avec l’option permettant de remplacer les données existantes.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
object.SetDefaults(OverwriteAll)  
```  
  
## <a name="parts"></a>Éléments  
 *object*  
 Objet de [classe CInstance](../../relational-databases/wmi-provider-configuration-classes/cinstance-class.md) qui représente une instance du client [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
#### <a name="parameters"></a>Paramètres  
  
|Paramètre|Description|  
|---------------|-----------------|  
|*OverwriteAll*|Valeur booléenne qui spécifie s’il faut remplacer les valeurs existantes sur l’instance du [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] client : **true** pour remplacer les données existantes, ou **false** si les données existantes ne doivent pas être remplacées.|  
  
## <a name="property-valuereturn-value"></a>Valeur de propriété/valeur de retour  
 Valeur **uint32** , égale à 0 si le service a été correctement modifié, égale à 1 si la demande n'est pas prise en charge ou égale à tout autre nombre pour indiquer une erreur.  
  
## <a name="remarks"></a>Notes  
  
## <a name="see-also"></a>Voir aussi  
 [Configurer des protocoles clients](https://technet.microsoft.com/library/ms181035.aspx)  
  
  

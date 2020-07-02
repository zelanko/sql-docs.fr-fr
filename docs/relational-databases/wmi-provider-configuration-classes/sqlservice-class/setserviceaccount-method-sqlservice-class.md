---
title: Méthode SetServiceAccount, (SqlService)
ms.custom: seo-lt-2019
ms.date: 03/03/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: wmi
ms.topic: reference
apiname:
- SetServiceAccount Method (SqlService Class)
apilocation:
- sqlmgmproviderxpsp2up.mof
apitype: MOFDef
helpviewer_keywords:
- SetServiceAccount method
ms.assetid: d5782892-e9d8-4d48-92af-b3afe9610f84
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 5892c9b080604af2e46a96685f4667e4d12dcfe1
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85784715"
---
# <a name="setserviceaccount-method-sqlservice-class"></a>Méthode SetServiceAccount (classe SqlService)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../../includes/applies-to-version/sqlserver.md)]
  Tente de modifier le nom d'utilisateur et le mot de passe sous lesquels l'instance du service s'exécute.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
object.SetServiceAccount(ServiceStartName , ServiceStartPassword)  
```  
  
## <a name="parts"></a>Éléments  
 *object*  
 Objet de [classe SqlService](../../../relational-databases/wmi-provider-configuration-classes/sqlservice-class/sqlservice-class.md) qui représente le service.  
  
#### <a name="parameters"></a>Paramètres  
 *ServiceStartName*  
 Valeur de chaîne qui spécifie le nom de compte sous lequel le service s'exécute. En fonction du type de service, le nom de compte peut se présenter sous la forme DomainName\Username. Lorsqu'il s'exécute, le processus du service sera connecté à l'aide de l'une des deux formes suivantes :  
  
-   si le compte appartient au domaine intégré, \Username peut être spécifié ;  
  
-   Si NULL est spécifié, le service est connecté en tant que compte **LocalSystem** .  
  
 Pour les pilotes au niveau du noyau ou du système, *StartName* contient le nom d’objet du pilote, \FileSystem\Rdr ou \Driver\Xns, que le système d’e/s utilise pour charger le pilote de périphérique. Si la valeur NULL est spécifiée, le pilote s'exécute avec un nom d'objet par défaut créé par le système d'E/S en fonction du nom du service, par exemple DWDOM\Admin.  
  
 *ServiceStartPassword*  
 Valeur de chaîne qui spécifie le mot de passe pour le nom de compte dans le paramètre *StartName* . Spécifiez NULL si vous ne modifiez pas le mot de passe. Spécifiez une chaîne vide si le service ne possède pas de mot de passe.  
  
## <a name="property-valuereturn-value"></a>Valeur de propriété/valeur de retour  
 Valeur **uint32** égale à 0 si le service a été correctement modifié ou égale à 1 si la demande n'est pas prise en charge. Tout autre nombre indique une erreur.  
  
## <a name="remarks"></a>Remarques  
  
## <a name="see-also"></a>Voir aussi  
 [Démarrage et arrêt des services](https://technet.microsoft.com/library/ms174886\(v=sql.105\).aspx)  
  
  

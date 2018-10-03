---
title: SetServiceAccount, méthode (classe SqlService) | Microsoft Docs
ms.custom: ''
ms.date: 03/03/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology:
- database-engine
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
manager: craigg
ms.openlocfilehash: 27985e94766a76efa755d05e81bce3ccb59ed6c6
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47664328"
---
# <a name="setserviceaccount-method-sqlservice-class"></a>Méthode SetServiceAccount (classe SqlService)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]
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
  
-   Si NULL est spécifié, le service s’être connecté en tant que le **LocalSystem** compte.  
  
 Pour les pilotes du noyau ou au niveau du système, *StartName* contient le nom d’objet de pilote, \FileSystem\Rdr ou \Driver\Xns, que le système d’e/s utilise pour charger le pilote de périphérique. Si la valeur NULL est spécifiée, le pilote s'exécute avec un nom d'objet par défaut créé par le système d'E/S en fonction du nom du service, par exemple DWDOM\Admin.  
  
 *ServiceStartPassword*  
 Valeur de chaîne qui spécifie le mot de passe pour le nom du compte dans le *StartName* paramètre. Spécifiez NULL si vous ne modifiez pas le mot de passe. Spécifiez une chaîne vide si le service ne possède pas de mot de passe.  
  
## <a name="property-valuereturn-value"></a>Valeur de propriété/valeur de retour  
 Valeur **uint32** égale à 0 si le service a été correctement modifié ou égale à 1 si la demande n'est pas prise en charge. Tout autre nombre indique une erreur.  
  
## <a name="remarks"></a>Notes  
  
## <a name="see-also"></a>Voir aussi  
 [Démarrage et arrêt des Services](http://technet.microsoft.com/library/ms174886\(v=sql.105\).aspx)  
  
  

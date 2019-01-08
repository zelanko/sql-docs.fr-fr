---
title: Fonction LocalDBGetInstances | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: reference
api_name:
- LocalDBGetInstances
api_location:
- sqluserinstance.dll
topic_type:
- apiref
ms.assetid: f95a9980-8bc0-426c-8aa1-e2660b6784cf
author: CarlRabeler
ms.author: carlrab
manager: craigg
ms.openlocfilehash: 92aa65bd2d3aad71f2467efaa7a09f75f20d8f63
ms.sourcegitcommit: ceb7e1b9e29e02bb0c6ca400a36e0fa9cf010fca
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/03/2018
ms.locfileid: "52795031"
---
# <a name="localdbgetinstances-function"></a>Fonction LocalDBGetInstances
  Retourne toutes les instances de SQL Server Express LocalDB avec la version donnée.  
  
 **Fichier d'en-tête :** sqlncli.h  
  
## <a name="syntax"></a>Syntaxe  
  
```  
#define MAX_LOCALDB_INSTANCE_NAME_LENGTH 128typedef WCHAR TLocalDBInstanceName[MAX_LOCALDB_INSTANCE_NAME_LENGTH + 1];typedef TLocalDBInstanceName* PTLocalDBInstanceName;  
HRESULT LocalDBGetInstances(  
           PTLocalDBInstanceName pInstanceNames,  
           LPDWORD lpdwNumberOfInstances  
);  
```  
  
## <a name="parameters"></a>Paramètres  
 *pInstanceNames*  
 [Sortie] Lorsque cette fonction est retournée, contient les noms des deux nommé et instances de base de données locale sur le poste de travail par défaut.  
  
 *lpdwNumberOfInstances*  
 [Entrée/sortie] En entrée, contient le nombre d'emplacements de noms d'instances dans la mémoire tampon de *pInstanceNames* . Lors de la sortie, contient le nombre d’instances de LocalDB sur la station de travail de l’utilisateur.  
  
## <a name="returns"></a>Valeur renvoyée  
 Cette méthode signale les erreurs en attribuant à la propriété Nombre de l'objet Err global l'une des valeurs du tableau suivant.  
 La fonction a réussi.  
  
 [LOCALDB_ERROR_NOT_INSTALLED](../express-localdb-error-messages/localdb-error-not-installed.md)  
 SQL Server Express LocalDB n'est pas installé sur l'ordinateur.  
  
 [LOCALDB_ERROR_INVALID_PARAMETER](../express-localdb-error-messages/localdb-error-invalid-parameter.md)  
 Un ou plusieurs paramètres d'entrée spécifiés ne sont pas valides.  
  
 [LOCALDB_ERROR_INSUFFICIENT_BUFFER](../express-localdb-error-messages/localdb-error-insufficient-buffer.md)  
 Le tampon d'entrée est trop court, et la troncation n'a pas été demandée.  
  
 [LOCALDB_ERROR_INSTANCE_FOLDER_PATH_TOO_LONG](../express-localdb-error-messages/localdb-error-instance-folder-path-too-long.md)  
 Le chemin d'accès où l'instance doit être stockée est plus long que MAX_PATH.  
  
 [LOCALDB_ERROR_CANNOT_ACCESS_INSTANCE_REGISTRY](../express-localdb-error-messages/localdb-error-cannot-access-instance-registry.md)  
 Un Registre d'instance n'est pas accessible.  
  
 [LOCALDB_ERROR_INSTANCE_CONFIGURATION_CORRUPT](../express-localdb-error-messages/localdb-error-instance-configuration-corrupt.md)  
 Une configuration d'instance est endommagée.  
  
 [LOCALDB_ERROR_INTERNAL_ERROR](../express-localdb-error-messages/localdb-error-internal-error.md)  
 Une erreur inattendue s'est produite. Pour plus d'informations, consultez le journal des événements.  
  
## <a name="remarks"></a>Notes  
 Pour un exemple de code qui utilise l'API LocalDB, consultez [SQL Server Express LocalDB Reference](../sql-server-express-localdb-reference.md).  
  
## <a name="see-also"></a>Voir aussi  
 [En-tête et informations de version de la base de données locale SQL Server Express](sql-server-express-localdb-header-and-version-information.md)  
  
  

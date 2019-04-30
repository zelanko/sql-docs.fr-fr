---
title: Fonction LocalDBCreateInstance | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: reference
api_name:
- LocalDBCreateInstance
api_location:
- sqluserinstance.dll
topic_type:
- apiref
ms.assetid: 3eebb485-8a53-4a79-82a9-57b8de9f8e84
author: CarlRabeler
ms.author: carlrab
manager: craigg
ms.openlocfilehash: d5e46c3d8a8a6836dbc0252177e45e86115abb07
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63128799"
---
# <a name="localdbcreateinstance-function"></a>Fonction LocalDBCreateInstance
  Crée une instance SQL Server Express LocalDB.  
  
 **Fichier d'en-tête :** sqlncli.h  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT LocalDBCreateInstance(  
           PCWSTR wszVersion,  
           PCWSTR pInstanceName,   
           DWORD dwFlags   
);  
```  
  
## <a name="parameters"></a>Paramètres  
 *wszVersion*  
 [Entrée] Version de LocalDB, par exemple 11.0 ou 11.0.1094.2.  
  
 *pInstanceName*  
 [Entrée] Nom de l'instance de LocalDB à créer.  
  
 *dwFlags*  
 [Entrée] Réservé à un usage ultérieur. Actuellement doit avoir la valeur 0.  
  
## <a name="returns"></a>Valeur renvoyée  
 Cette méthode signale les erreurs en attribuant à la propriété Nombre de l'objet Err global l'une des valeurs du tableau suivant.  
 La fonction a réussi.  
  
 [LOCALDB_ERROR_NOT_INSTALLED](../express-localdb-error-messages/localdb-error-not-installed.md)  
 SQL Server Express LocalDB n'est pas installé sur l'ordinateur.  
  
 [LOCALDB_ERROR_INVALID_PARAMETER](../express-localdb-error-messages/localdb-error-invalid-parameter.md)  
 Un ou plusieurs paramètres d'entrée spécifiés ne sont pas valides.  
  
 [LOCALDB_ERROR_INVALID_INSTANCE_NAME](../express-localdb-error-messages/localdb-error-invalid-instance-name.md)  
 Le nom d'instance spécifié n'est pas valide.  
  
 [LOCALDB_ERROR_INSTANCE_FOLDER_PATH_TOO_LONG](../express-localdb-error-messages/localdb-error-instance-folder-path-too-long.md)  
 Le chemin d'accès où l'instance doit être stockée est plus long que MAX_PATH.  
  
 [LOCALDB_ERROR_INSTANCE_EXISTS_WITH_LOWER_VERSION](../express-localdb-error-messages/localdb-error-instance-exists-with-lower-version.md)  
 L'instance spécifiée existe déjà mais sa version est inférieure à celle demandée.  
  
 [LOCALDB_ERROR_UNKNOWN_VERSION](../express-localdb-error-messages/localdb-error-unknown-version.md)  
 La version spécifiée n'est pas disponible.  
  
 [LOCALDB_ERROR_VERSION_REQUESTED_NOT_INSTALLED](../express-localdb-error-messages/localdb-error-version-requested-not-installed.md)  
 Le niveau de correctif de logiciel spécifié n'est pas installé.  
  
 [LOCALDB_ERROR_CANNOT_CREATE_INSTANCE_FOLDER](../express-localdb-error-messages/localdb-error-cannot-create-instance-folder.md)  
 Impossible de créer un dossier sous %userprofile%.  
  
 [LOCALDB_ERROR_CANNOT_GET_USER_PROFILE_FOLDER](../express-localdb-error-messages/localdb-error-cannot-get-user-profile-folder.md)  
 Impossible de récupérer un dossier du profil utilisateur.  
  
 [LOCALDB_ERROR_CANNOT_ACCESS_INSTANCE_FOLDER](../express-localdb-error-messages/localdb-error-cannot-access-instance-folder.md)  
 Un dossier d'instance n'est pas accessible.  
  
 [LOCALDB_ERROR_CANNOT_ACCESS_INSTANCE_REGISTRY](../express-localdb-error-messages/localdb-error-cannot-access-instance-registry.md)  
 Un Registre d'instance n'est pas accessible.  
  
 [LOCALDB_ERROR_CANNOT_MODIFY_INSTANCE_REGISTRY](../express-localdb-error-messages/localdb-error-cannot-modify-instance-registry.md)  
 Impossible de modifier un Registre d'instance.  
  
 [LOCALDB_ERROR_SQL_SERVER_STARTUP_FAILED](../express-localdb-error-messages/localdb-error-sql-server-startup-failed.md)  
 Un processus SQL Server est démarré, mais le démarrage de SQL Server a échoué.  
  
 [LOCALDB_ERROR_INSTANCE_CONFIGURATION_CORRUPT](../express-localdb-error-messages/localdb-error-instance-configuration-corrupt.md)  
 Une configuration d'instance est endommagée.  
  
 [LOCALDB_ERROR_INTERNAL_ERROR](../express-localdb-error-messages/localdb-error-internal-error.md)  
 Une erreur inattendue s'est produite. Pour plus d'informations, consultez le journal des événements.  
  
## <a name="remarks"></a>Notes  
 Si une instance de LocalDB entièrement fonctionnelle portant le nom spécifié existe déjà et sa version est supérieure ou égale à la version demandée, le résultat est S_OK.  
  
 Dans les cas où une instance existante est endommagée, les appels suivants à la méthode d'API `LocalDBCreateInstance` échouent. Les instances endommagées doivent être corrigées manuellement ou être explicitement supprimées avant de pouvoir être réutilisées.  
  
 Pour un exemple de code qui utilise l'API LocalDB, consultez [SQL Server Express LocalDB Reference](../sql-server-express-localdb-reference.md).  
  
## <a name="see-also"></a>Voir aussi  
 [En-tête et informations de version de la base de données locale SQL Server Express](sql-server-express-localdb-header-and-version-information.md)  
  
  

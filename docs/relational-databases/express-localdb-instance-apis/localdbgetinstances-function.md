---
description: Fonction LocalDBGetInstances
title: LocalDBGetInstances fonction) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: ''
ms.topic: reference
apiname:
- LocalDBGetInstances
apilocation:
- sqluserinstance.dll
apitype: DLLExport
ms.assetid: f95a9980-8bc0-426c-8aa1-e2660b6784cf
author: markingmyname
ms.author: maghan
ms.openlocfilehash: b35bb809ebd1dfd9dd3d0a4c836b3ff7439ce3ec
ms.sourcegitcommit: dd36d1cbe32cd5a65c6638e8f252b0bd8145e165
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/08/2020
ms.locfileid: "89544079"
---
# <a name="localdbgetinstances-function"></a>Fonction LocalDBGetInstances
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]
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
 Sortie Lorsque cette fonction est retournée, contient les noms des instances de base de données locale nommées et par défaut sur la station de travail de l’utilisateur.  
  
 *lpdwNumberOfInstances*  
 [Entrée/sortie] En entrée, contient le nombre d'emplacements de noms d'instances dans la mémoire tampon de *pInstanceNames* . En sortie, contient le nombre d’instances de base de données locale trouvées sur la station de travail de l’utilisateur.  
  
## <a name="returns"></a>Retours  
 S_OK  
 La fonction a réussi.  
  
 [LOCALDB_ERROR_NOT_INSTALLED](../../relational-databases/express-localdb-error-messages/localdb-error-not-installed.md)  
 SQL Server Express LocalDB n'est pas installé sur l'ordinateur.  
  
 [LOCALDB_ERROR_INVALID_PARAMETER](../../relational-databases/express-localdb-error-messages/localdb-error-invalid-parameter.md)  
 Un ou plusieurs paramètres d'entrée spécifiés ne sont pas valides.  
  
 [LOCALDB_ERROR_INSUFFICIENT_BUFFER](../../relational-databases/express-localdb-error-messages/localdb-error-insufficient-buffer.md)  
 Le tampon d'entrée est trop court, et la troncation n'a pas été demandée.  
  
 [LOCALDB_ERROR_INSTANCE_FOLDER_PATH_TOO_LONG](../../relational-databases/express-localdb-error-messages/localdb-error-instance-folder-path-too-long.md)  
 Le chemin d'accès où l'instance doit être stockée est plus long que MAX_PATH.  
  
 [LOCALDB_ERROR_CANNOT_ACCESS_INSTANCE_REGISTRY](../../relational-databases/express-localdb-error-messages/localdb-error-cannot-access-instance-registry.md)  
 Un Registre d'instance n'est pas accessible.  
  
 [LOCALDB_ERROR_INSTANCE_CONFIGURATION_CORRUPT](../../relational-databases/express-localdb-error-messages/localdb-error-instance-configuration-corrupt.md)  
 Une configuration d'instance est endommagée.  
  
 [LOCALDB_ERROR_INTERNAL_ERROR](../../relational-databases/express-localdb-error-messages/localdb-error-internal-error.md)  
 Une erreur inattendue s’est produite. Pour plus d'informations, consultez le journal des événements.  
  
## <a name="remarks"></a>Notes  
 Pour un exemple de code qui utilise l'API LocalDB, consultez [SQL Server Express LocalDB Reference](../../relational-databases/sql-server-express-localdb-reference.md).  
  
## <a name="see-also"></a>Voir aussi  
 [En-tête et informations de version SQL Server Express LocalDB](../../relational-databases/express-localdb-instance-apis/sql-server-express-localdb-header-and-version-information.md)  
  
  
